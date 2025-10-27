# Smart Biodigester Monitor - ESP32 Firmware

ESP32 firmware for multi-sensor biodigester monitoring with real-time data transmission.

## Overview

Production-ready firmware for monitoring biogas fermenters with comprehensive sensor integration and real-time data transmission to FastAPI backend.

### Key Features

- **Multi-Sensor Integration**: pH, temperature, environmental, and methane sensors
- **Real-time Transmission**: HTTP POST every 2 seconds to FastAPI backend
- **INIR2 Protocol**: Specialized methane sensor communication
- **Error Handling**: WiFi reconnection and sensor validation

### Supported Sensors

- **pH**: DFRobot Gravity V2 (0-14 pH, ±0.1 accuracy)
- **Temperature**: Up to 2x DS18B20 (±0.5°C accuracy)
- **Environmental**: BME680 (temperature, humidity, pressure, gas)
- **Methane**: INIR2-ME100 (0-100% LEL with CRC validation)

## Hardware Requirements

- **Board**: ESP32-WROOM-32 (4MB Flash, 520KB RAM)
- **WiFi**: 2.4GHz 802.11 b/g/n
- **Power**: 5V/1A supply with 3.3V regulation

### Pin Assignment

| Sensor | Pin | Type | Description |
|--------|-----|------|-------------|
| pH Sensor | G35 | Analog | ADC1_CH7 (0-3.3V) |
| Temperature | G4 | Digital | 1-Wire Bus |
| BME680 SDA | G21 | I2C | Data Line |
| BME680 SCL | G22 | I2C | Clock Line |
| INIR2 TX | G17 | UART | ESP TX → Sensor RX |
| INIR2 RX | G16 | UART | ESP RX ← Sensor TX |

## Quick Start

1. **Install Arduino IDE** (2.0+) and ESP32 board package
2. **Install libraries**:
   ```cpp
   DFRobot_ESP_PH, OneWire, DallasTemperature, 
   Adafruit_BME680, ArduinoJson
   ```
3. **Configure WiFi** in `esp.ino`:
   ```cpp
   const char* ssid = "YOUR_WIFI_NAME";
   const char* password = "YOUR_WIFI_PASSWORD";
   const char* backend_url = "https://your-domain.com/data";
   ```
4. **Wire sensors** according to pin assignments
5. **Upload and test** via Serial Monitor (115200 baud)

## Data Transmission

**Format**: HTTP POST every 2 seconds  
**Content-Type**: application/json  
**Timeout**: 10 seconds with retry logic

### JSON Payload
```json
{
  "ph": 6.8,
  "ph_voltage": 2150.5,
  "temp1": 35.2,
  "temp2": 34.8,
  "bme_temperature": 22.1,
  "bme_humidity": 65.3,
  "bme_pressure": 1013.25,
  "bme_gas_resistance": 45.2,
  "methan_raw": ["0000005b", "00001234", "0000aaaa", "00000bb8", "12345678", "87654321", "0000005d"]
}
```


