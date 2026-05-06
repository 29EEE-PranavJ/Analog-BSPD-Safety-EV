# Analog-BSPD-Safety-EV

🛑 Brake System Plausibility Device (BSPD)

🔷 Overview
The Brake System Plausibility Device (BSPD) is a critical safety system used in electric race vehicles (like Formula Student cars) to detect implausible conditions between throttle input and braking.If the system detects that the driver is accelerating while braking, it interprets this as a fault condition and shuts down the motor power, preventing unsafe acceleration.
This project implements a hardware-based BSPD using analog and digital circuit design, simulated in LTspice and realized on PCB.

🎯 Objective
Design a fail-safe hardware system to detect implausible acceleration conditions
Ensure instant motor shutdown during unsafe states
Implement logic using pure circuit design (no microcontroller dependency)
Achieve reliable, low-latency response suitable for real-world EV safety

⚙️ Key Features
Real-time monitoring of:
Motor current (acceleration proxy)
Brake pressure signal
Hardware-based fault detection logic
SR latch memory for fault retention
RC delay circuit for debounce and timing control
Transistor-based output switching for shutdown signal
Fully simulated in LTspice and implemented via PCB

⚡ Working Principle
The BSPD continuously compares two main inputs:

Current Sensor Signal → Indicates acceleration
Brake Pressure Signal → Indicates braking
Fault Condition:
If current > threshold AND brake applied simultaneously,
→ System detects implausible condition
Action:
Output logic triggers
SR latch locks the fault
Shutdown signal is sent to motor controller

Even if the fault disappears, the system remains latched until reset (ensures safety).

🧠 Software Used & Roles
LTspice
Circuit design and simulation
Validation of comparator thresholds
Timing analysis (RC delay behavior)
PCB Design Tool (e.g., KiCad / Eagle)
Circuit layout and routing
Real-world implementation

🔄 System Behaviour
Normal Condition:
Brake = OFF, Current = Normal
→ Output = ENABLED
Braking Only:
Brake = ON, Current = Low
→ Output = ENABLED
Fault Condition:
Brake = ON + Current = High
→ Output = DISABLED (shutdown triggered)
Post Fault:
System remains locked (latched)
→ Requires manual/system reset

🔍 Observations
Comparator thresholds are critical for accurate detection
Noise in signals can cause false triggering, requiring filtering
RC delay improves stability but introduces slight latency
SR latch ensures fail-safe persistence, preventing intermittent faults

🚀 Applications
Formula Student Electric Vehicles
Electric Vehicle Safety Systems
Industrial Motor Protection
Autonomous System Safety Interlocks

📊 Results
Successful detection of implausible conditions in simulation
Reliable shutdown response observed
Stable latch behavior verified
PCB implementation validated core functionality

🔮 Future Scope
Integration with microcontroller for diagnostics/logging
Adaptive thresholding using sensor calibration
Reduction of noise via advanced filtering techniques
Integration into Vehicle Control Unit (VCU)
Redundant safety layers for higher reliability

🧩 Key Concepts Used
Analog Comparators
Boolean Logic (AND operation)
SR Latch (Memory Element)
RC Time Delay Circuits
Transistor Switching
Signal Conditioning
Safety-Critical System Design
