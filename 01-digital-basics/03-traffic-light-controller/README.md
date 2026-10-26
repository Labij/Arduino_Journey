# Experiment 03: 3-Phase Intersection Traffic Light Controller

### Overview
This project simulates an autonomous 3-phase municipal traffic signal controller using an Arduino Uno (Type-C). It expands upon single and dual-LED blinking to manage three coordinated digital outputs running in a deterministic sequential loop.

---

### Demonstrations
- 🎥 **Video Build & Walkthrough (YouTube):** [https://youtu.be/zT5aJJqgpsA?si=NXj5CZMcpyKl-Xd7]
- ⚡ **Interactive Simulation (Wokwi):** [Run Traffic Light on Wokwi](https://wokwi.com/projects/478825906885076993)

---

### State Sequence & Timing Specification

| State | Phase | Active Pin | Duration | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **State 1** | **STOP** | Digital Pin 8 (Red) | 5000 ms (5s) | Halts incoming traffic at intersection |
| **State 2** | **GO** | Digital Pin 4 (Green) | 4000 ms (4s) | Allows vehicle flow |
| **State 3** | **CLEAR / CAUTION** | Digital Pin 7 (Yellow) | 2000 ms (2s) | Warning buffer to clear the junction |

> **Safety Logic Note:** The transition sequence strictly follows `Red → Green → Yellow → Red`. Yellow serves as the mandatory transition between high-speed green flow and a red stop state to prevent collision hazards.

---

### Circuit Architecture

- **Microcontroller:** Arduino Uno (Type-C)
- **Outputs:**
  - **Red LED:** Digital Pin 8 → Resistor → Anode (+)
  - **Yellow LED:** Digital Pin 7 → Resistor → Anode (+)
  - **Green LED:** Digital Pin 4 → Resistor → Anode (+)
- **Ground Return:** All three LED cathodes (-) tie directly into the breadboard's common negative (`-`) bus, which routes to an Arduino **GND** terminal.

---

### Source Code

```cpp
/*
  Experiment 03: 3-Phase Traffic Light Controller
  Microcontroller: Arduino Uno (Type-C)
*/

const int redpin = 8;
const int yellowpin = 7;
const int greenpin = 4;

void setup() {
  pinMode(redpin, OUTPUT);
  pinMode(yellowpin, OUTPUT);
  pinMode(greenpin, OUTPUT);
}

void loop() {
  // Phase 1: RED (Stop)
  digitalWrite(redpin, HIGH);
  delay(5000);
  digitalWrite(redpin, LOW);

  // Phase 2: GREEN (Go)
  digitalWrite(greenpin, HIGH);
  delay(4000);
  digitalWrite(greenpin, LOW);

  // Phase 3: YELLOW (Caution / Clear)
  digitalWrite(yellowpin, HIGH);
  delay(2000);
  digitalWrite(yellowpin, LOW);

  // Loop automatically cycles back to Phase 1
}
