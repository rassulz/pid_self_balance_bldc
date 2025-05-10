# pid_self_balance_bldc

---

## ⚙️ Hardware Components

- **Controller:** Arduino Uno (ATmega328P @ 16 MHz)  
- **IMU:** MPU-6050 (3-axis gyro ±250 °/s, accel ±2 g)  
- **Motors:** 2× BLDC, 12 V, 300 W max, 3000 RPM  
- **ESCs:** 2× 20 A brushless speed controllers (PWM input 0.9–2.1 ms)  
- **Power:** 12 V, 20 A Li-Ion battery pack  
- **Chassis:** 3D-printed PETG frame (Fusion 360 file included)  
- **Bearings & Mounts:** 8 mm ball bearings, mounting hardware  

---

## 🛠️ Software Components

- **Arduino Sketch** (`PID_SELF_BALANCE_BLDC.ino`)  
  - I²C driver for MPU-6050 (Wire.h)  
  - Complementary filter for tilt estimation  
  - PID_v1 library for control loop  
  - PWM output with Servo.h / analogWrite for ESC signals  
  - Serial logging for real-time debug

- **Simulink Model** (`balancing_model.slx`)  
  - Simscape Electrical inverter + BLDC motor  
  - Hall-sensor decoding and gating  
  - Discrete PID block replicating Arduino logic  
  - Powergui in discrete mode (5 µs step)

- **MATLAB Script** (`self_balance_pid.m`)  
  - Linearized inverted-pendulum state-space model  
  - Discretized at 200 Hz  
  - PID simulation with tilt-angle and control-effort plots

- **Fusion 360 Model** (`chassis.f3d`)  
  - Printable frame with landing legs  
  - Mount points for Arduino, IMU, ESCs, battery, and motors

---

## 🚀 Getting Started

### Prerequisites

- **Hardware:**  
  - Arduino Uno + USB cable  
  - MPU-6050 breakout board  
  - 2× BLDC motors + 2× 20 A ESCs  
  - 12 V/20 A battery  
  - 3D-printed chassis (print with PETG / PLA)

- **Software:**  
  - Arduino IDE  
  - MATLAB & Simulink (Simscape Electrical)  
  - Fusion 360 (or any STEP/IGES viewer)

### Installation

1. **Clone the repository**
   ```bash
   https://github.com/rassulz/pid_self_balance_bldc
