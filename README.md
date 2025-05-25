# Line Follower Robot

This is a simple line follower robot project that uses:
- **Two DC motors**
- **QTR-8RC reflectance sensor array**
- **TB6612FNG motor driver**
- **4 x 3.7V batteries (14.8V total)**
- **Arduino Uno/Nano**

## Features
- Follows black line on white surface using PID control
- Adjustable motor speed and tuning
- Basic calibration routine for QTR-8RC

---

## Hardware Used

| Component              | Quantity |
|------------------------|----------|
| Arduino Uno/Nano       | 1        |
| QTR-8RC Sensor Array   | 1        |
| TB6612FNG Motor Driver | 1        |
| DC Gear Motors         | 2        |
| Wheels                 | 2        |
| 3.7V Li-ion Batteries  | 4        |
| Battery Holder (4S)    | 1        |
| Chassis                | 1        |
| Jumper Wires           | -        |

---

## Wiring

### QTR-8RC to Arduino
| QTR-8RC Pin | Arduino Pin |
|------------|-------------|
| VCC        | 5V          |
| GND        | GND         |
| OUT0–OUT7  | D2–D9 (or any 8 digital pins) |
| LEDON      | 5V (or controlled via digital pin) |

### TB6612FNG to Arduino
| TB6612FNG Pin | Arduino Pin | Description         |
|---------------|-------------|---------------------|
| AIN1          | D10         | Motor A control     |
| AIN2          | D11         | Motor A control     |
| BIN1          | D12         | Motor B control     |
| BIN2          | D13         | Motor B control     |
| PWMA          | D5 (PWM)    | Speed for Motor A   |
| PWMB          | D6 (PWM)    | Speed for Motor B   |
| STBY          | 5V or D8    | Standby, set HIGH   |
| VM            | Battery +   | Motor power (14.8V) |
| GND           | Battery -   | Ground              |
| VCC           | 5V          | Logic power         |

---

## Software

### Arduino Libraries Required
- `QTRSensors` by Pololu  
  Install via Library Manager or from: https://github.com/pololu/qtr-sensors-arduino

### Arduino Code Outline
- Calibrate QTR sensors on startup
- Use `readLine()` to get position
- Apply a PID algorithm to calculate correction
- Adjust motor speeds accordingly
