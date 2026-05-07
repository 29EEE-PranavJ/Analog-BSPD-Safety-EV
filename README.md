# Analog-BSPD-Safety-EV

## 🛑 Brake System Plausibility Device (BSPD)

A hardware-based safety system designed for electric race vehicles to detect unsafe simultaneous acceleration and braking conditions.

This project implements a fully analog Brake System Plausibility Device (BSPD) using comparators, logic circuits, SR latch memory, and transistor-based shutdown mechanisms. The system is simulated in LTspice and implemented on PCB for real-world EV safety applications.

---

## 🔷 Overview

The Brake System Plausibility Device (BSPD) is a critical safety subsystem used in electric race vehicles such as Formula Student EVs.

The system continuously monitors:

- Motor current (acceleration indication)
- Brake pressure signal

If the driver attempts to accelerate while braking simultaneously, the BSPD interprets this as an implausible and unsafe condition.

The system immediately:

- Detects the fault
- Latches the condition
- Sends a shutdown signal to the motor controller

This prevents unintended acceleration and ensures fail-safe vehicle operation.

---

## 🎯 Objective

- Design a fail-safe hardware safety system
- Detect simultaneous braking and acceleration
- Ensure rapid motor shutdown during unsafe conditions
- Eliminate dependency on microcontrollers
- Achieve reliable low-latency protection
- Implement a real-world EV safety architecture

---

## ⚙️ Key Features

- Real-time analog signal monitoring
- Hardware-only implementation
- Comparator-based threshold detection
- Boolean logic fault evaluation
- SR latch-based fault retention
- RC timing and debounce circuits
- Transistor-driven shutdown output
- LTspice simulation validation
- PCB implementation support

---

## ⚡ Working Principle

The BSPD compares two primary inputs continuously:

### Inputs

| Signal | Purpose |
|---|---|
| Current Sensor Signal | Detects acceleration/current draw |
| Brake Pressure Signal | Detects braking action |

---

## 🚨 Fault Detection Logic

### Unsafe Condition

```text
Brake Applied = TRUE
AND
Motor Current > Threshold
```

If both conditions occur simultaneously:

```text
→ Fault Detected
→ SR Latch Triggered
→ Shutdown Signal Activated
```

---

## 🔒 Latching Behaviour

Once the fault is triggered:

- The SR latch stores the fault condition
- Shutdown remains active
- System cannot automatically recover

A manual/system reset is required to restore operation.

This ensures:
- fail-safe persistence
- prevention of intermittent unsafe states
- compliance with EV safety requirements

---

## 🧠 Software Used & Roles

| Software | Role |
|---|---|
| LTspice | Circuit simulation and validation |
| LTspice | Comparator threshold tuning |
| LTspice | RC timing analysis |
| PCB Design Tools (KiCad / Eagle) | PCB layout and routing |
| PCB Design Tools | Real-world hardware realization |

---

## 🏗️ System Architecture

### Core Components

- Current Sensor Interface
- Brake Signal Conditioning
- Analog Comparators
- Logic Gate Network
- SR Latch
- RC Delay Circuit
- Transistor Switching Stage
- Shutdown Output Driver

---

## 🔄 System Behaviour

### ✅ Normal Driving Condition

```text
Brake = OFF
Current = Normal
→ Output = ENABLED
```

---

### ✅ Braking Only

```text
Brake = ON
Current = Low
→ Output = ENABLED
```

---

### 🚨 Fault Condition

```text
Brake = ON
Current = High
→ Output = DISABLED
```

Motor shutdown is immediately triggered.

---

### 🔒 Post Fault State

```text
Fault Stored in SR Latch
→ System Locked
→ Manual Reset Required
```

---

## 📊 Functional Logic Flow

```text
Current Sensor ─┐
                ├── Comparator Logic ── AND Logic ── SR Latch ── Shutdown Signal
Brake Sensor ───┘
```

---

## 🔍 Observations

- Comparator thresholds strongly affect system reliability
- Signal noise may create false triggering conditions
- RC filtering improves stability
- Debounce circuits reduce transient faults
- SR latch ensures persistent fault retention
- Analog implementation provides extremely fast response

---

## 🧪 Simulation Results

### LTspice Validation

- Successful detection of implausible conditions
- Correct comparator switching observed
- Stable SR latch operation verified
- Reliable shutdown signal generation achieved
- RC delay behavior validated
- Transistor switching response confirmed

---

## 📈 Results

| Feature | Result |
|---|---|
| Fault Detection | Successful |
| Shutdown Response | Reliable |
| SR Latch Stability | Verified |
| Comparator Operation | Stable |
| PCB Validation | Successful |
| Real-Time Response | Achieved |

---

## 🚀 Applications

### Formula Student Electric Vehicles
Mandatory EV safety subsystem implementation.

### Electric Vehicle Safety Systems
Motor shutdown and safety interlocks.

### Industrial Motor Protection
Protection against unsafe operating conditions.

### Autonomous Systems
Fail-safe emergency shutdown systems.

### Safety-Critical Electronics
Hardware-level protection architectures.

---

## 🧩 Key Concepts Used

- Analog Comparators
- Boolean Logic
- AND Gate Logic
- SR Latch
- RC Delay Circuits
- Signal Conditioning
- Transistor Switching
- Hardware Fault Detection
- Safety-Critical System Design

---

## 🔮 Future Scope

- Microcontroller integration for diagnostics
- CAN communication support
- Real-time fault logging
- Adaptive threshold calibration
- Advanced analog filtering
- Vehicle Control Unit (VCU) integration
- Redundant safety layers
- FPGA-based safety architecture
- Automotive-grade hardware optimization

---

## 👨‍💻 Project Domain

- Electric Vehicles
- Automotive Safety Systems
- Analog Electronics
- Embedded Hardware
- Circuit Design
- Power Electronics
- Safety-Critical Engineering

---

## 🏛️ Platform & Implementation

### Simulation
- LTspice

### Hardware
- PCB-Based Analog Circuit

### Deployment Target
- Formula Student Electric Vehicle

---

## ⭐ Final Perspective

This project demonstrates how pure hardware logic can still outperform software-dependent systems in safety-critical environments.

Instead of relying entirely on firmware or controllers:

> the protection mechanism exists directly in hardware.

That means:
- faster response
- higher reliability
- lower failure probability
- deterministic safety behavior

This is the kind of engineering mindset used in real automotive safety systems:
- simple
- robust
- fail-safe
- physically reliable
---
## 👨‍💻 Authors

- **Pranav J**
- **Tharun S**
- **Midhun P**
