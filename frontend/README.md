# Smart Biodigester Monitor - Frontend

Next.js web application for real-time sensor data visualization and monitoring.

## Overview

Modern web-based dashboard for monitoring and visualizing sensor data from biogas fermenters with real-time updates and alarm systems.

### Key Features

- **Real-time Dashboard**: Live sensor data display with automatic updates
- **Interactive Charts**: Time-series visualization with adaptive scaling
- **Alarm Management**: Visual warnings for critical parameter ranges
- **Responsive Design**: Mobile-first user interface


### Monitored Parameters

- **Temperature**: Dual tank sensors (optimal: 30-40°C)
- **pH Level**: Fermenter acidity (optimal: 6-8)
- **Environmental**: Temperature, humidity, pressure, gas resistance
- **Methane**: Concentration in ppm/percent with sensor temperature
- **System Status**: Error diagnosis and sensor monitoring

## Quick Start

1. **Install dependencies**
   ```bash
   npm install
   ```

2. **Configure environment**
   ```bash
   # Create .env.local with:
   NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Access application**
   - Open [http://localhost:3000](http://localhost:3000)

## Technology Stack

- **Frontend**: Next.js 15 with TypeScript and Tailwind CSS
- **UI Components**: shadcn/ui with Radix UI primitives
- **Charts**: Recharts with adaptive scaling and alarm zones
- **Database**: Supabase PostgreSQL with real-time subscriptions

## Features

- **Dashboard**: Live sensor data display with alarm status
- **Charts**: Interactive time-series with time range selection (1h-1m)
- **Alarm System**: Visual warnings for temperature (30-40°C) and pH (6-8) ranges
- **Responsive Design**: Mobile-first interface with touch optimization

## Development

```bash
npm run dev    # Development server
npm run build  # Production build
npm run start  # Production server
npm run lint   # Code linting
```
