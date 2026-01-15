# 🎸 Arduino Digital Guitar

A **standalone Arduino-based digital guitar** that uses **motion (MPU6050)** to detect strumming, **touch sensors** to select chords, and a **DFPlayer Mini** module to play guitar sounds.  
No wireless communication is used — everything runs on a single Arduino.

---

## 📌 Features
- 🎸 Strum detection using **MPU6050 accelerometer**
- ✋ **Touch sensors** for chord selection
- 🔊 **DFPlayer Mini** for audio playback
- 🧠 Automatic MPU6050 freeze detection and re-initialization
- ⚡ Low-latency and smooth response

---

## 🧰 Components Required
- Arduino Uno / Nano
- MPU6050 (Accelerometer & Gyroscope)
- DFPlayer Mini MP3 Module
- Micro SD Card (formatted FAT32)
- 3 × Touch Sensors
- **1 kΩ Resistor (required)**
- Speaker (4Ω–8Ω)
- Jumper wires
- Breadboard / PCB
- Power supply

---

## 🔌 Pin Connections

### Touch Sensors
| Touch Sensor | Arduino Pin |
|-------------|-------------|
| Touch 1 | D2 |
| Touch 2 | D3 |
| Touch 3 | D4 |

### MPU6050 (I2C)
| MPU6050 Pin | Arduino Pin |
|------------|-------------|
| VCC | 5V |
| GND | GND |
| SDA | A4 |
| SCL | A5 |

### DFPlayer Mini (IMPORTANT)
| DFPlayer Pin | Arduino Pin |
|-------------|-------------|
| RX | D10 **via 1 kΩ resistor** |
| TX | D11 |
| VCC | 5V |
| GND | GND |
| SPK+ / SPK- | Speaker |

⚠️ **Important Note:**  
Always place a **1 kΩ resistor between Arduino TX (D10) and DFPlayer RX**.  
This protects the DFPlayer and ensures **stable serial communication**.

---

## 💾 SD Card Setup
1. Format the SD card as **FAT32**
2. Copy audio files and name them as: 0001.mp3   → Chord 1
                                      0002.mp3   → Chord 2
                                      0003.mp3   → Chord 3
  3. Insert the SD card into the DFPlayer Mini

---

## ▶️ How It Works
1. Touch sensors select the active chord
2. MPU6050 detects a strumming motion
3. The selected chord sound is played through DFPlayer Mini
4. Small movements are ignored to prevent false triggering

---

## 📚 Libraries Used
Install these libraries using **Arduino Library Manager**:
- `I2Cdev`
- `MPU6050`
- `DFRobotDFPlayerMini`
- `Wire`
- `SoftwareSerial`

---

## ⚙️ Configuration
- **Strum Threshold** can be adjusted:
```cpp
const int STRUM_THRESHOLD = 2000;] 
   •	Volume control: dfPlayer.volume(25); // Range: 0–30
