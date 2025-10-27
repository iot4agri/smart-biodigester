# Smart Biodigester Monitor - Backend API

FastAPI-based backend server for real-time sensor data processing and storage.

## Overview

Receives, processes, and stores sensor data from ESP32-based multi-sensor systems with specialized protocols for methane gas analysis.

### Key Features

- **Real-time Data Processing**: HTTP POST endpoints for ESP32 sensor data
- **INIR2 Protocol Decoding**: Specialized methane sensor communication with CRC validation
- **Temperature Persistence**: sensor failure handling (15-50°C range)
- **Database Integration**: Supabase PostgreSQL with periodic uploads
- **Error Handling**: Robust validation and fault detection

### Supported Sensors

- **Temperature**: Dual DS18B20 sensors with range validation
- **Environmental**: BME680 (temperature, humidity, pressure, gas resistance)
- **Methane**: INIR2-ME100 with fault detection and CRC validation
- **pH**: DFRobot Gravity V2 sensor

## Quick Start

1. **Install dependencies**
   ```bash
   pip install fastapi uvicorn python-dotenv supabase pytz
   ```

2. **Configure environment**
   ```bash
   # Create .env file with:
   SUPABASE_URL=your_supabase_url
   SUPABASE_KEY=your_supabase_anon_key
   ```

3. **Start server**
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 5000 --reload
   ```

4. **Access API**
   - Server: [http://localhost:5000](http://localhost:5000)
   - Documentation: [http://localhost:5000/docs](http://localhost:5000/docs)


## API Endpoints

### POST /data
Receives sensor data from ESP32 system.

**Request Body:**
```json
{
  "ph": 5.2,
  "ph_voltage": 2.1,
  "temp1": 35.5,
  "temp2": 34.8,
  "bme_temperature": 22.3,
  "bme_humidity": 65.2,
  "bme_pressure": 1013.25,
  "bme_gas_resistance": 50000,
  "methan_raw": ["0000005b", "00001234", "0000aaaa", "00000bb8", "12345678", "87654321", "0000005d"]
}
```
