# Experiment 04: Pushbutton LED Control (My First Input!)

### Overview
Up until now, my Arduino was basically blind and deaf—it could turn LEDs on, but it didn't know I was there. For this project, I finally added a "sense" to the microcontroller by wiring up a tactile pushbutton.

---

### Demonstrations
- 🎥 **Bench Video (YouTube):** [PASTE_YOUR_UNLISTED_YOUTUBE_LINK_HERE]
- ⚡ **Wokwi Simulation:** [Run my circuit on Wokwi](https://wokwi.com/projects/479421757507749889)

---

### The Struggle: Understanding Pull-Up Resistors
I'm going to be honest, learning how a button actually works in electronics was super confusing at first. 

I originally thought: *"Why can't I just connect the button to 5V and the pin?"* 
I learned that if a pin is left floating (touching nothing), it acts like an antenna and picks up random static electricity, making the Arduino read random 1s and 0s. 

To fix this, we need a **Pull-Up Resistor** to act like a gentle spring, holding the pin at 5V when nobody is pressing the button. The coolest part? I didn't even have to wire a resistor on my breadboard because the Arduino chip has them built inside! I just had to type `pinMode(buttonPin, INPUT_PULLUP);`.

---

### How I Wired It

- **The Output:** 
  - Red LED on **Pin 12** (with a series resistor to Ground).
- **The Input (The Button):**
  - Leg A of the button connected to **Pin 2**.
  - Leg B (diagonal to Leg A) connected directly to **Ground**. 

### The Code

```cpp
/*
  Experiment 04: Pushbutton LED
  Learning how to use digitalRead() and internal pull-up resistors!
*/

const int buttonPin = 2;  
const int ledPin = 12;    

void setup() {
  pinMode(ledPin, OUTPUT);
  // This turns on the secret resistor inside the Arduino chip!
  pinMode(buttonPin, INPUT_PULLUP);
}

void loop() {
  int buttonState = digitalRead(buttonPin);

  // Because of the pull-up resistor, 0V (LOW) means it's touching Ground (PRESSED)
  if (buttonState == LOW) {
    digitalWrite(ledPin, HIGH);  
  } else {
    digitalWrite(ledPin, LOW);   
  }
}
