# bluetooth_led_control.ino
# 🔦 Bluetooth LED Control System – Arduino + HC-05

This Arduino project lets you control multiple LEDs via Bluetooth using an Android terminal or custom mobile app. Great for robot direction indication, signal systems, and smart cars.

---

## 🧰 Components Required

- Arduino UNO  
- HC-05 Bluetooth module  
- 6x LEDs  
- Jumper wires, Breadboard  
- Bluetooth terminal app (like Serial Bluetooth Terminal on Android)

---

## 🔌 Pin Configuration

| Arduino Pin | Component Description |
|-------------|------------------------|
| D13         | LED1 – Left Motor     |
| D12         | LED2 – Right Motor    |
| D11         | LED3 – Headlight L    |
| D10         | LED4 – Headlight R    |
| D9          | LED5 – Left Signal    |
| D8          | LED6 – Right Signal   |
| D2          | Bluetooth RxD         |
| D3          | Bluetooth TxD         |

---

## 📲 Commands & LED Actions

| Bluetooth Input | Action                      | LEDs ON         |
|------------------|-----------------------------|------------------|
| `F`              | Move Forward                | LED1, LED2       |
| `B`              | Move Backward               | LED1, LED2       |
| `L`              | Turn Left                   | LED1             |
| `R`              | Turn Right                  | LED2             |
| `H`              | Headlights ON               | LED3, LED4       |
| `K`              | Headlights OFF              | -                |
| `M`              | Indicators ON               | LED5, LED6       |
| `N`              | Indicators OFF              | -                |
| `S`              | Stop (All LEDs OFF)         | -                |

---

## 📁 Project Files

- `code/bluetooth_led_control.ino` – Main Arduino sketch

---

## 💡 Use Cases

- Bluetooth-controlled car/robot
- Signal simulation
- Smart home or vehicle dashboards

---
