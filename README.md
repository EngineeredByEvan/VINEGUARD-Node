# 🌿 VINEGUARD Node v0.1

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
```
---

## 🔋 Power-Saving Details

- Uses `esp_deep_sleep_start()` for ultra low-power sleep between reads.
- Wake time controlled by `SLEEP_MINUTES` constant.
- Ideal for battery + solar operation.

---

## 📦 Libraries Used

- [Adafruit BME280](https://registry.platformio.org/libraries/adafruit/Adafruit%20BME280%20Library)
- [Adafruit Unified Sensor](https://registry.platformio.org/libraries/adafruit/Adafruit%20Unified%20Sensor)
- [LoRa by Sandeep Mistry](https://github.com/sandeepmistry/arduino-LoRa)

---

## 🛣️ Roadmap

- ✅ BME280 + Soil sensor + LoRa transmission
- ✅ Deep sleep support
- ⏳ Add SD card buffering (for offline scenarios)
- ⏳ Transmit as JSON (structured payloads)
- ⏳ Integrate with Firebase / MQTT / REST cloud endpoint
- ⏳ Auto-calibration features + OTA update support
- ⏳ Dashboard frontend for vineyard customers 🌐

---

## 📄 License & Disclaimer

MIT License © 2024 **Evan White**

> This is a pre-production prototype intended for educational and research purposes.  

