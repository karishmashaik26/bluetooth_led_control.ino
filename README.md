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

## 📁 CODE

#include <Wire.h>
#include <SoftwareSerial.h>

#define TxD 3
#define RxD 2

#define LED1 13
#define LED2 12
#define LED3 11
#define LED4 10
#define LED5 9
#define LED6 8

SoftwareSerial bluetoothSerial(TxD, RxD);
char c;

void setup() {
  pinMode(LED1, OUTPUT);
  pinMode(LED2, OUTPUT);
  pinMode(LED3, OUTPUT);
  pinMode(LED4, OUTPUT);
  pinMode(LED5, OUTPUT);
  pinMode(LED6, OUTPUT);
  
  bluetoothSerial.begin(9600);
  Serial.begin(9600);
}

void loop() {
  if (bluetoothSerial.available() > 0) {
    c = bluetoothSerial.read();
  }

  Serial.print(c);

  if (c == 'F' || c == 'B') {
    digitalWrite(LED1, HIGH);
    digitalWrite(LED2, HIGH);
  }

  if (c == 'L') {
    digitalWrite(LED1, HIGH);
    digitalWrite(LED2, LOW);
  }

  if (c == 'R') {
    digitalWrite(LED1, LOW);
    digitalWrite(LED2, HIGH);
  }

  if (c == 'H') {
    digitalWrite(LED3, HIGH);
    digitalWrite(LED4, HIGH);
  }

  if (c == 'K') {
    digitalWrite(LED3, LOW);
    digitalWrite(LED4, LOW);
  }

  if (c == 'M') {
    digitalWrite(LED5, HIGH);
    digitalWrite(LED6, HIGH);
  }

  if (c == 'N') {
    digitalWrite(LED5, LOW);
    digitalWrite(LED6, LOW);
  }

  if (c == 'S') {
    digitalWrite(LED1, LOW);
    digitalWrite(LED2, LOW);
    digitalWrite(LED3, LOW);
    digitalWrite(LED4, LOW);
    digitalWrite(LED5, LOW);
    digitalWrite(LED6, LOW);
  }
}


---

## 💡 Use Cases

- Bluetooth-controlled car/robot
- Signal simulation
- Smart home or vehicle dashboards

---
