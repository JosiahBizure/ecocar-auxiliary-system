# EcoCAR Mobility Challenge – Auxiliary Controller

## 1. Overview

### Purpose and Function
This subsystem is designed to control and monitor non-propulsion systems in a hybrid-electric vehicle, such as wipers, lighting, windshield fluid delivery, telemetry, and system health indicators. It supports safety, usability, and compliance with competition standards while operating on a microcontroller-based platform (Raspberry Pi Pico).

### Design Philosophy
The design emphasizes modularity, state-driven logic, and real-time responsiveness using interrupt-based event handling. Each module is isolated with well-defined responsibilities and communicates through digital GPIO lines, with minimal resource contention.

## 2. Project Status
- [x] High-level module breakdown and responsibilities defined
- [ ] GPIO and sensor pinout finalized
- [ ] ISR design and debouncing strategy implementation
- [ ] Integration and test with physical components
- [ ] Telemetry display or logging mechanism selected

## 3. Subsystems & Modules

### Wipers Module
- **Input**: Wiper switch (analog or digital)
- **Output**: PWM signal to motor
- **Visual Feedback**: Green (active), blinking red (error)
- **Notes**: May support variable-speed mode using analog input and timer logic.

### Lights Module
- **Input**: Selector switches for headlights, turn signals, brake pedal, hazard
- **Output**: All major exterior lights
- **Visual Feedback**: Color-coded indicator scheme (blue, white, yellow, red)
- **Notes**: Will handle blinking via timers or ISRs.

### Windshield Fluid Module
- **Input**: Spray button, fluid level sensor
- **Output**: Pump activation signal
- **Visual Feedback**: Blue (spraying), red (low fluid)
- **Notes**: Debounced input; spray auto-timeout planned.

### Telemetry Module
- **Input**: Hall effect sensor
- **Output**: Vehicle speed data
- **Visual Feedback**: Green (active), blinking red (sensor fail)
- **Notes**: May transmit speed data to display or logging system.

### Power Monitor Module
- **Input**: Analog voltage/current sensors
- **Output**: System power state, subsystem cutoff triggers
- **Visual Feedback**: Green (OK), blinking red (fault)
- **Notes**: ADC sampling loop with threshold logic

### Visual Flags Module
- **Input**: Status signals from all subsystems
- **Output**: LEDs to indicate system health/status
- **Notes**: Acts as central feedback hub for driver/operator.

## 4. Future Plans
- Determine communication method: purely GPIO or add serial/I2C for future expansion.
- Consider watchdog timers for module fault detection.
- Expand compatibility with EcoCAR telemetry and diagnostics systems.

## 5. Role and Contributions
- Spearheading initial system decomposition and logic architecture.
- Identifying I/O needs, event-driven logic, and state management strategies.
- Will implement and validate each subsystem in C, with possible ARM inline assembly for time-critical routines.

---

> This document will be expanded with schematics, testing results, and hardware details as implementation proceeds.
