# Experiment 02: Dual-LED Emergency Strobe Controller

### Overview
Building upon single-output blinking, this experiment controls two independent digital GPIO channels (Pins 12 and 13) to create a high-urgency emergency vehicle ("wig-wag" / double-burst) strobe pattern using Red and Blue LEDs.

---

### Demonstrations
- 🎥 **Video Walkthrough (YouTube):** [I WILL PASTE MY LINK OF YOUTUBE HERE SOON!]
- ⚡ **Interactive Simulation (Wokwi):** [Run Strobe Simulation on Wokwi](https://wokwi.com/projects/478237007197260801)

---

### Circuit Design & Architecture

Rather than wiring separate ground lines back to the board, this circuit implements a **Common Ground Rail** approach standard in industrial wiring:

1. **Red LED Channel (Pin 12):**
   - Arduino **Digital Pin 12** connects to a current-limiting resistor.
   - The resistor connects to the **Anode (+)** of the Red LED.
   - The **Cathode (-)** of the Red LED connects to the breadboard's negative power rail (`-`).

2. **Blue LED Channel (Pin 13):**
   - Arduino **Digital Pin 13** connects to a second current-limiting resistor.
   - The resistor connects to the **Anode (+)** of the Blue LED.
   - The **Cathode (-)** of the Blue LED connects to the same negative power rail (`-`).

3. **Common Ground Return:**
   - A single return jumper wire connects the breadboard's negative power rail directly back to an Arduino **GND** pin, completing both circuits.

---

### Source Code

```cpp
/*
  Experiment 02: Dual-LED Emergency Strobe (Wig-Wag Double Flash)
  Target: Arduino Uno (Type-C)
  Channels: Pin 12 (Red), Pin 13 (Blue)
*/

const int redLedPin = 12;
const int blueLedPin = 13;

void setup() {
  pinMode(redLedPin, OUTPUT);
  pinMode(blueLedPin, OUTPUT);
}

void loop() {
  // === PHASE 1: RED STROBE (Double Burst) ===
  digitalWrite(redLedPin, HIGH);
  delay(80);
  digitalWrite(redLedPin, LOW);
  delay(80);

  digitalWrite(redLedPin, HIGH);
  delay(80);
  digitalWrite(redLedPin, LOW);
  delay(80);

  // === PHASE 2: BLUE STROBE (Double Burst) ===
  digitalWrite(blueLedPin, HIGH);
  delay(80);
  digitalWrite(blueLedPin, LOW);
  delay(80);

  digitalWrite(blueLedPin, HIGH);
  delay(80);
  digitalWrite(blueLedPin, LOW);
  delay(80);
}
