# Main Avionics System for a TEKNOFEST Rocket Project

## Overview

This repository contains an **incomplete main avionics system schematic** originally designed in **EasyEDA** for a **TEKNOFEST rocket project**.

The avionics system was intended to act as the **central electronic control and data-handling unit** of the rocket. It was designed to combine multiple subsystems into one board, including:

- flight sensing
- orientation estimation
- altitude/pressure measurement
- GPS positioning
- long-range telemetry
- onboard data logging
- battery/power regulation
- relay outputs
- audible buzzer indication

Unfortunately, the full project was **postponed before completion**, so this design remained unfinished. Even though the work is incomplete, I still wanted to publish it because it may be useful as a reference for others working on **rocket avionics**, **embedded telemetry systems**, or **sensor integration projects**.

This repository is shared mainly for:

- documentation purposes
- learning/reference
- future continuation or redesign
- open sharing of partial engineering work

---

## Project Status

**Status:** Incomplete / Archived / Shared as Reference

This schematic was created as a **main avionics concept** for a rocket system, but the project was interrupted before final validation, PCB review, firmware completion, and integrated testing.

That means:

- the design may contain unfinished sections
- some subsystems may not be fully verified
- the board should **not** be considered flight-ready
- the repository is shared in its current state for transparency and possible reuse

---

## What Can Be Seen in the Schematic

Based on the current EasyEDA schematic, the system appears to include the following major blocks.

---

## 1. Inertial Measurement / Orientation Sensor

### **BNO055**
The schematic includes a **BNO055** sensor block.

The BNO055 is commonly used for:

- orientation estimation
- fused motion sensing
- acceleration, gyroscope, and magnetometer data
- attitude-related calculations

In a rocket avionics context, this type of sensor can be useful for:

- tracking orientation during ascent
- motion analysis
- tilt estimation
- post-flight analysis

The schematic shows the BNO055 connected through what appears to be an **I2C interface**, along with pull-up and level-shifting support between logic voltage domains.

---

## 2. Pressure / Altitude Sensor

### **BMP390**
A **BMP390** barometric pressure sensor block is also present.

This sensor is typically used for:

- pressure measurement
- relative altitude estimation
- vertical profile analysis
- flight event support such as ascent/descent interpretation

In rocket avionics, a barometric sensor is especially important for:

- estimating altitude trends
- detecting ascent and descent phases
- supporting recovery logic when combined with other data sources

The presence of this sensor suggests the board was intended to gather atmospheric/altitude data during flight.

---

## 3. Main Controller

### **Arduino Mega / ATmega2560-based section**
The schematic includes a large microcontroller block labeled **Arduino Mega**, which strongly suggests an **ATmega2560-based controller architecture**.

This controller likely served as the main brain of the avionics system, responsible for:

- reading sensor data
- handling telemetry
- logging flight data
- processing GPS input
- controlling relays and buzzer outputs
- managing communication between different modules

Using a Mega-class controller makes sense in a prototype or development-focused avionics system because it offers:

- many GPIO pins
- multiple UART/I2C/SPI interfaces
- easy firmware development
- compatibility with many common modules

---

## 4. GPS Module

### **NEO-6M**
The schematic includes a **NEO-6M** GPS block.

This module would have been used for:

- obtaining geographic coordinates
- time synchronization
- recovery support
- position tracking during ground tests or post-flight localization

In many rocket projects, GPS data is helpful for:

- payload tracking
- landing area estimation
- telemetry transmission of location data
- post-flight search and recovery

---

## 5. Long-Range Telemetry

### **SX1262 LoRa**
A block labeled **SX1262 LoRa** is present in the schematic.

This suggests the avionics system was intended to support **long-range wireless telemetry**, likely for sending selected flight data to a ground station.

Potential telemetry use cases include:

- altitude data
- orientation/IMU data
- GPS coordinates
- flight state information
- system health or battery data

LoRa is commonly chosen for this kind of project because it offers:

- long-range communication
- relatively low power consumption
- robust telemetry capability for low-bandwidth sensor data

---

## 6. Onboard Data Logging

### **SD Card Module**
The design includes an **SD card module** section.

This would allow the avionics system to store:

- sensor logs
- pressure/altitude data
- IMU/orientation data
- timestamps
- GPS records
- event markers
- debug information

Onboard logging is a critical feature in rocket avionics because even if live telemetry is lost, the stored data can still be analyzed after recovery.

---

## 7. Power System

### **Battery Circuit**
The schematic includes a dedicated **battery circuit** block.

Although the project is incomplete and the exact final power architecture may not be fully validated, the visible schematic indicates that the design intended to include:

- battery input handling
- regulated power rails
- power distribution for both 5V and 3.3V domains
- support circuitry for stable system operation

Different modules in the schematic appear to use both **5V** and **3.3V**, which is normal for mixed embedded systems.

---

## 8. Power Regulation and Supply Sections

### **Power Supply**
A dedicated **power supply** section is visible, along with regulators and decoupling components.

From the schematic labeling, the design appears to support multiple voltage rails such as:

- **5V**
- **3.3V**
- possibly battery/raw input domains

This is important because:

- some modules operate at 5V logic
- others operate at 3.3V logic
- sensors and radio devices often require clean, stable supply rails

The presence of separate regulation and support circuitry suggests the board was planned as a more integrated avionics platform rather than a simple wiring prototype.

---

## 9. Logic-Level Translation

### **Level shifting (5V <-> 3.3V)**
The schematic explicitly includes a **level-shifting** block between **5V and 3.3V** logic.

This is an important design detail because the system combines modules that likely do not all share the same logic level. Proper level translation helps protect devices and improves communication reliability.

This is particularly relevant for buses such as:

- I2C
- SPI
- digital control signals

---

## 10. I2C Support and Expansion

### **I2C pull-ups and STEMMA QT headers**
The schematic includes:

- **I2C pull-up and shift circuitry**
- **STEMMA QT headers**

This suggests the board was designed with modularity and expandability in mind. The use of STEMMA QT/Qwiic-style connectors is especially useful during prototyping because it makes sensor testing and module replacement easier.

This indicates that part of the avionics workflow may have included:

- quick sensor swaps
- easier bench testing
- simpler prototyping of I2C peripherals

---

## 11. Relay Outputs

### **Relays**
The schematic includes a **relay section**.

These relay outputs may have been intended for switching or controlling external circuits. In a rocket electronics context, relay-style outputs could be explored for:

- isolated switching
- subsystem activation
- external payload control
- test bench actuation

Since the project was not completed, the exact final role of these relays in the flight architecture was not fully finalized.

---

## 12. Audible Feedback

### **Buzzer Circuit**
A **buzzer circuit** is present in the design.

This could be used for:

- startup indication
- status tones
- fault indication
- continuity-style alerts
- debugging during bench tests

A buzzer is especially useful in field electronics because it provides immediate feedback without requiring serial monitoring or a connected display.

---

## 13. Status Indication

### **ON LED**
The schematic also includes an **ON LED** block.

This likely serves as a basic power/status indicator to show that the board is energized and operating.

---

## System Intent

From the visible blocks in the schematic, the overall intended system architecture appears to be:

1. **Read sensor data**
   - BNO055 for motion/orientation
   - BMP390 for pressure/altitude
   - GPS for position/time

2. **Process data in the main controller**
   - central logic handled by the Arduino Mega / ATmega2560-based section

3. **Transmit selected telemetry**
   - via SX1262 LoRa

4. **Store data onboard**
   - via SD card

5. **Manage outputs and alerts**
   - relay section
   - buzzer
   - LEDs

6. **Power all modules safely**
   - battery input
   - regulators
   - 5V / 3.3V distribution
   - level shifting where needed

In short, this was intended to be a **single integrated avionics motherboard** for a rocket project prototype.

---

## Important Notes

This repository is shared as an **unfinished engineering work**. Please keep the following in mind:

- This is **not a final flight-certified design**
- The schematic may contain incomplete or untested sections
- Pin mappings, regulator choices, and interfaces may still require review
- Electrical validation and PCB checks may still be necessary
- Firmware for the full system is not guaranteed to be complete
- Anyone reusing this work should verify everything independently

If you want to build on top of this project, it is strongly recommended to perform:

- full schematic review
- ERC/DRC checks
- component validation
- signal integrity review
- power budget calculation
- ground and noise analysis
- hardware-in-the-loop testing
- environmental and vibration considerations for flight use

---

## Why This Repository Is Public

I decided to publish this project even though it was left unfinished.

The original goal was to develop a **main avionics system for a TEKNOFEST rocket project**, but due to various circumstances the project was postponed before this design could be fully completed.

Instead of leaving the work unused, I wanted to share it because:

- it may help someone starting a similar avionics design
- it documents part of the development process
- incomplete projects can still be valuable references
- open engineering work can inspire better future desing

