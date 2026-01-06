# DDD system stands for driver drowsiness detection system

## 📌 Project Description
This project is a **Smart Goggles-based Alert System** using an **IR Sensor**, **Arduino UNO**, **motor**, and **buzzer**.  
It is designed to detect obstacles using an IR sensor and trigger a motor and buzzer alert through a **BD140 transistor** circuit.

The project is useful for:
- Assistive technology
- Safety alert systems
- Basic robotics and electronics learning

---

## 🧰 Components Required
| Component | Quantity |
|---------|----------|
| Arduino UNO | 1 |
| Goggles | 1 |
| IR Sensor Module | 1 |
| BD140 Transistor | 1 |
| 1kΩ Resistor | 1 |
| Buzzer | 1 |
| DC Motor | 1 |
| Wheels | 2 |
| Jumper Wires | As required |
| Breadboard | 1 |
| USB Cable | 1 |

---

## 🔌 Circuit Connections

### IR Sensor Connections
| IR Sensor Pin | Arduino UNO Pin |
|--------------|-----------------|
| VCC | 5V |
| GND | GND |
| OUT | D2 |

---

### Buzzer Connections
| Buzzer Pin | Connection |
|------------|------------|
| Positive (+) | D8 (via 1kΩ resistor) |
| Negative (-) | GND |

---

### Motor Connections (Using BD140 Transistor)
| BD140 Pin | Connection |
|----------|------------|
| Base | Arduino D9 (via 1kΩ resistor) |
| Collector | Motor Negative |
| Emitter | GND |
| Motor Positive | 5V |

---

## ⚙️ Working Principle
1. The **IR sensor** continuously checks for obstacles.
2. When an object is detected:
   - The **buzzer** turns ON
   - The **motor** starts rotating
3. The **BD140 transistor** works as a switch to safely control the motor.
4. The system is mounted on **goggles** for wearable obstacle detection.

---

## 🧑‍💻 Arduino Code provided in zip file above

📦 Attached ZIP File

The attached ZIP file contains:

Arduino source code

Circuit diagram

Project report

Components list

🚀 How to Upload Code

1. Open Arduino IDE


2. Connect Arduino UNO via USB


3. Select:

Board: Arduino UNO

Port: COM / USB Port



4. Open anti-sleep-alarm.ino


5. Click Upload




---

✅ Applications

Drowsiness detection systems

Beginner Arduino projects



---

👨‍🎓 Author

Gautam Kumar


---

📜 License

This project is open-source and free to use for educational purposes.
