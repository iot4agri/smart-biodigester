# Smart Biodigester Monitoring System

A comprehensive IoT solution for real-time monitoring of biogas fermenters, featuring multi-sensor data collection, real-time processing, and web-based visualization.

## Overview

This system provides continuous monitoring of critical parameters in biogas production facilities through an integrated hardware-software architecture. The solution consists of three main components:

- **ESP32 Firmware** (`/esp/`): Multi-sensor data collection and wireless transmission
- **FastAPI Backend** (`/backend/`): Real-time data processing and storage
- **Next.js Frontend** (`/frontend/`): Web-based monitoring dashboard

## Monitored Parameters

- **Temperature**: Dual DS18B20 sensors (15-50°C range validation)
- **pH Level**: DFRobot Gravity V2 sensor (0-14 pH range)
- **Environmental**: Temperature, humidity, pressure, gas resistance (BME680)
- **Methane Concentration**: INIR2-ME100 sensor with CRC validation (0-100% LEL)

## Technical Architecture

### Hardware
- **Microcontroller**: ESP32-WROOM-32
- **Sensors**: DS18B20, DFRobot Gravity V2, BME680, INIR2-ME100

### Software Stack
- **Firmware**: Arduino Core for ESP32
- **Backend**: Python FastAPI with Supabase integration
- **Frontend**: Next.js 15 with TypeScript and Tailwind CSS
- **Database**: PostgreSQL (Supabase)

## Quick Start

1. **Hardware Setup**: Wire sensors according to pin assignments in `/esp/README.md`
2. **Backend Deployment**: Configure environment variables and start FastAPI server
3. **Frontend Setup**: Install dependencies and configure Supabase connection
4. **Data Flow**: ESP32 → FastAPI → Supabase → Next.js Dashboard

## Repository Structure

```
iot4agri/
├── esp/           # ESP32 firmware
├── backend/       # FastAPI server
├── frontend/      # Next.js web application
├── materials.md   # Materials List
└── LICENSE        # MIT License
```

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Contributors

- **Tim Siebert** - Lead Developer
- **Max Zboralski** - Co-Developer
