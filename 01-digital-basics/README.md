# 01. Digital Basics

This module covers fundamental microcontroller GPIO (General Purpose Input/Output) concepts: driving loads, managing logic voltage levels (5V / 0V), software timing modulation, and protecting circuits using series resistors.

### 📋 Completed Experiments

1. **[01-external-led-blink](./01-external-led-blink/)**
   - **Concepts:** `pinMode(OUTPUT)`, `digitalWrite()`, series current protection, adapting resistor values under real-world constraints.
   - **Hardware:** Arduino Pin 12, 10kΩ resistor, Red LED.

2. **[02-emergency-strobe-controller](./02-emergency-strobe-controller/)**
   - **Concepts:** Dual-channel GPIO coordination, non-blocking sequence logic, breadboard common ground rail architecture, emergency vehicle strobe pattern.
   - **Hardware:** Arduino Pins 12 & 13, Dual Series Resistors, Red & Blue LEDs.

---

### 🧠 Core Concepts Mastered
- **GPIO Direction:** Configuring pins as low-impedance `OUTPUT` sources.
- **Current Protection:** Series resistance prevents short-circuit conditions and component failure.
- **Common Ground (GND) Bus:** Tying multiple cathode return paths together on the breadboard's ground rail before routing back to the Arduino.
- **Timing Modulation:** Changing device behavior entirely in software without altering a single wire.
