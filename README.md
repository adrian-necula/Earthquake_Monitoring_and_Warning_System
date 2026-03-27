# Earthquake Monitoring and Warning System

This repository contains the software implementation and logic design for an automated earthquake detection and warning system. It was developed in C for AVR microcontrollers as part of the **Microprocessor Architecture 2 (AMP2)** course at ETTI, UNSTPB.

## 🌍 About the Project
The system processes data from a vibration sensor (accelerometer) to determine the severity of seismic activity. To prevent false alarms, it features a custom Finite State Machine (FSM) that requires critical vibrations to persist for a specific duration (3 seconds) before triggering the main alarm.

## ⚙️ System Architecture
The digital logic is divided into three main modules:
* **Combinational Logic Circuit (CLC):** Analyzes the raw sensor input (Low, Medium, High vibrations) and determines the immediate alert level using bitwise operations and masking.
* **Sequential Logic Circuit (CLS):** Acts as the timer/memory. It tracks how long a high-vibration state persists to filter out accidental shocks.
* **Sequential Process (FSM):** The master state machine that transitions between states: *Monitoring ➡️ Warning ➡️ Persistence Counting ➡️ Active Alarm ➡️ Reset*.

## 🚨 Alerts & Outputs
Based on the FSM state, the system provides real-time visual and acoustic feedback:
* 🟢 **Normal/Low Vibration:** Green LED ON.
* 🟡 **Medium Vibration (Warning):** Yellow LED ON.
* 🔴 **High Vibration (Critical):** Red LED blinking + Buzzer ON (activates *only* after 3 seconds of continuous severe vibration).

## 💻 Development & Testing
* **Language:** C
* **Tools:** CodeVisionAVR and AVR Studio.
* **Testing:** The system was rigorously tested using I/O simulation (manipulating `PIND` registers for simulated sensor input and observing `PORTB` outputs for LED/Buzzer response).

## 📂 Repository Structure
* 📄 `Tema_suplimentara_422E_Necula_Adrian.pdf`: The complete project documentation in Romanian (Theoretical foundations, Truth tables, FSM logic, full C code, and Testing results).
* 🖼️ `Graf_PS.png`: The visual representation of the Finite State Machine (FSM) transitions.
