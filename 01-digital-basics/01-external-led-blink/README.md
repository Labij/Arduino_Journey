# Experiment 01: External LED Blink Circuit

### Overview
This project demonstrates the design, simulation, and physical implementation of an external LED blink circuit controlled by an Arduino Uno (Type-C) microcontroller.

---

### Demonstration
- 🎥 **Video Walkthrough (YouTube):** [PASTE_YOUR_UNLISTED_YOUTUBE_LINK_HERE]
- ⚡ **Interactive Simulation (Wokwi):** [Run Circuit Simulation on Wokwi](https://wokwi.com/projects/478141441634345985)

---

### Circuit Wiring Specifications

- **Microcontroller:** Arduino Uno (Type-C clone, CH340 USB)
- **Digital Output Pin:** Pin 12
- **Current Limiting Resistor:** 10kΩ (Brown – Black – Orange – Gold)
  > **Note:** Standard tutorials recommend 220Ω to 330Ω. Due to kit component availability, a 10kΩ resistor was deployed. At 5V, this limits forward current safely to ~0.3mA. The circuit functions reliably with an eye-friendly, non-blinding LED output while fully protecting the microcontroller GPIO pin.

#### Physical Breadboard Map:
- **Pin 12** → Breadboard Row 28 (Column J)
- **10kΩ Resistor:** Row 28 (Column H) → Row 22 (Column H)
- **LED Anode (+ Long Leg):** Row 22 (Column F)
- **LED Cathode (- Short Leg):** Row 21 (Column F)
- **Ground Connection:** Breadboard Row 21 (Column G) → Arduino **GND**

---

### Source Code

```cpp
/*
  Experiment 01: External LED Blink
  Target: Arduino Uno (Type-C)
  Signal Pin: Digital Pin 12
*/

const int ledPin = 12;

void setup() {
  // Configure digital pin 12 as an output
  pinMode(ledPin, OUTPUT);
}

void loop() {
  digitalWrite(ledPin, HIGH); // Turn LED ON (5V)
  delay(500);                 // Wait 500 milliseconds (0.5s)
  
  digitalWrite(ledPin, LOW);  // Turn LED OFF (0V)
  delay(500);                 // Wait 500 milliseconds
}
