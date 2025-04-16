# VINEGUARD-Node
VINEGUARD Node Firmware
# 🌿 VINEGUARD™ Node v0.1

**LoRa-based precision agriculture sensor node for vineyards and smart farming applications.**  
This firmware reads environmental + soil data, transmits it via LoRa, and enters deep sleep to conserve power.

---

## 🚀 Features

- 📡 Sends real-time data via LoRa (915 MHz)
- 🌡️ Reads temperature, humidity, pressure (BME280)
- 🌱 Measures soil moisture via capacitive sensor
- 🔋 Ultra-low power design with deep sleep between cycles
- 🧠 Easily expandable: pH sensors, NPK, SD logging, or Wi-Fi cloud sync

---

## 🧰 Hardware Requirements

| Component                      | Example Model                       | Notes                                   |
|-------------------------------|-------------------------------------|-----------------------------------------|
| ESP32 LoRa Board              | Heltec WiFi LoRa 32 (V2)            | SX1276-based radio at 915 MHz           |
| Environmental Sensor          | Adafruit BME280                     | I2C - temp, humidity, pressure           |
| Soil Moisture Sensor          | Capacitive analog soil sensor       | Connected to analog pin 34              |
| Power                         | LiPo battery + solar panel          | Optional: USB for dev/testing           |
| Optional Expansion            | Atlas pH / DFRobot NPK sensors      | Placeholder-ready in firmware           |

---

## 🔌 Wiring Diagram

| Sensor           | ESP32 Pin       |
|------------------|------------------|
| BME280 SDA       | GPIO 21 (SDA)    |
| BME280 SCL       | GPIO 22 (SCL)    |
| BME280 VCC       | 3.3V             |
| BME280 GND       | GND              |
| Soil Sensor OUT  | GPIO 34 (ADC)    |
| Soil Sensor VCC  | 3.3V / 5V        |
| Soil Sensor GND  | GND              |
| LoRa SPI         | Board default SPI|
| LoRa SS          | GPIO 18          |
| LoRa RST         | GPIO 14          |
| LoRa DIO0        | GPIO 26          |

🖼️ Wiring diagram image available in `docs/wiring.png`  
(coming soon)

---

## 💻 Project Structure

```bash
VINEGUARD-Node/
├── src/
│   └── main.cpp              # Sensor + LoRa firmware
├── include/
│   ├── LoRaSender.h          # (Coming soon)
│   └── LoRaReceiver.h        # (Coming soon)
├── docs/
│   └── wiring.png            # Wiring diagram image
├── platformio.ini            # PlatformIO board & lib config
├── README.md
