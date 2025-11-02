# 🏥 Health Connect

A comprehensive health monitoring and management application built with Next.js, featuring real-time air quality monitoring, health metrics tracking, and AI-powered medical assistance.

## ✨ Features

### 🌬️ Real-Time Air Quality Monitoring
- Live AQI data from 1000+ cities worldwide
- 7-day historical trends and predictions
- Personalized health recommendations
- Best times to go outside
- Multiple pollutant tracking (PM2.5, PM10, O₃, NO₂, SO₂, CO)

### 📊 Health Metrics Dashboard
- Track vital health indicators
- Visualize trends over time
- Set health goals
- Monitor progress

### 🏥 Healthcare Features
- Find nearby clinics
- Book appointments
- Health records management
- Medication reminders
- Alert system

### 🤖 AI Medical Assistant
- Symptom checker
- Health advice
- Medical information
- 24/7 availability

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ 
- pnpm (recommended) or npm
- WAQI API key (free) for real-time AQI data

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Srishti-1806/Health_Connect.git
   cd Health_Connect
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   # or
   npm install
   ```

3. **Set up environment variables**
   
   Create a `.env.local` file in the root directory:
   ```env
   NEXT_PUBLIC_WAQI_API_KEY=your_api_key_here
   ```
   
   **Get your free API key**: https://aqicn.org/data-platform/token/
   
   > 📖 See [QUICK_START_AQI.md](QUICK_START_AQI.md) for detailed setup instructions

4. **Run the development server**
   ```bash
   pnpm dev
   # or
   npm run dev
   ```

5. **Open your browser**
   ```
   http://localhost:3000
   ```

## 📝 Configuration

### Air Quality API Setup

The app uses the **World Air Quality Index (WAQI)** API for real-time air quality data.

**Quick Setup:**
1. Get free API key from https://aqicn.org/data-platform/token/
2. Add to `.env.local`: `NEXT_PUBLIC_WAQI_API_KEY=your_key`
3. Restart server

**Detailed Guide:** See [SETUP_GUIDE.md](SETUP_GUIDE.md) for complete setup and troubleshooting.

**Without API Key:** The app works with demo data - all features remain functional!

## 🏗️ Tech Stack

- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **UI Components**: shadcn/ui
- **Charts**: Recharts
- **Icons**: Lucide React
- **Package Manager**: pnpm

## 📁 Project Structure

```
Health_Connect/
├── app/                      # Next.js app directory
│   ├── dashboard/           # Dashboard pages
│   │   ├── air-quality/    # AQI monitoring
│   │   ├── appointments/   # Appointment management
│   │   ├── find-clinics/   # Clinic finder
│   │   ├── health-metrics/ # Health tracking
│   │   └── health-records/ # Medical records
│   ├── login/              # Authentication
│   └── signup/             # User registration
├── components/             # React components
│   ├── ui/                # shadcn UI components
│   └── *.tsx              # Custom components
├── lib/                   # Utilities
├── public/               # Static assets
└── styles/              # Global styles
```

## 🌟 Key Features Explained

### Air Quality Monitoring

**Real-Time Data:**
- Live AQI updates from global monitoring stations
- Updates every 30 minutes
- Support for 1000+ cities worldwide

**Predictions:**
- ML-based 7-day AQI forecasts
- Historical trend analysis
- Time-slot recommendations

**Health Recommendations:**
- Personalized advice based on respiratory conditions
- Activity suggestions
- Diet recommendations
- Safety precautions

**Setup Your Health Profile:**
- Add respiratory conditions (asthma, COPD, sinus issues)
- Get tailored recommendations
- Severity-based alerts

### Clinic Finder
- Location-based search
- Interactive maps
- Clinic details and ratings
- Directions and contact info

### Health Metrics
- Track vitals (heart rate, blood pressure, etc.)
- Visualize trends
- Set and monitor goals
- Export data

## 🔧 Development

### Available Scripts

```bash
# Development server
pnpm dev

# Build for production
pnpm build

# Start production server
pnpm start

# Lint code
pnpm lint

# Type check
pnpm type-check
```

### Code Style
- TypeScript for type safety
- ESLint for code quality
- Prettier for formatting (if configured)

## 🐛 Troubleshooting

### AQI Data Not Updating
1. Check `.env.local` file exists in root directory
2. Verify API key is correct
3. Restart development server (`Ctrl+C`, then `pnpm dev`)
4. Check browser console for errors

See [SETUP_GUIDE.md](SETUP_GUIDE.md) for detailed troubleshooting.

### Build Errors
```bash
# Clear Next.js cache
rm -rf .next

# Reinstall dependencies
rm -rf node_modules pnpm-lock.yaml
pnpm install

# Rebuild
pnpm build
```

## 📚 Documentation

- **[QUICK_START_AQI.md](QUICK_START_AQI.md)** - Quick 3-step AQI setup
- **[SETUP_GUIDE.md](SETUP_GUIDE.md)** - Complete setup and troubleshooting
- **[AQI_API_SETUP.md](AQI_API_SETUP.md)** - API configuration details
- **[AQI_INTEGRATION_SUMMARY.md](AQI_INTEGRATION_SUMMARY.md)** - Integration overview

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- **WAQI** - World Air Quality Index for AQI data API
- **shadcn/ui** - Beautiful UI components
- **Recharts** - Chart library
- **Next.js** - React framework

## 📧 Support

For issues and questions:
- Open an issue on GitHub
- Check [SETUP_GUIDE.md](SETUP_GUIDE.md) for common problems
- Review documentation files

## 🔐 Security & Privacy

- Environment variables are never committed (`.env*` in `.gitignore`)
- API keys are client-side safe (WAQI API design)
- No sensitive health data is transmitted without encryption
- Data stored locally in browser (localStorage)

## 🌍 Supported Cities

**India**: Delhi, Mumbai, Bangalore, Chennai, Kolkata, Hyderabad, Pune, Ahmedabad

**Global**: Beijing, Shanghai, Tokyo, Singapore, London, Paris, New York, Los Angeles, and 1000+ more cities

## 📈 Roadmap

- [ ] User authentication
- [ ] Cloud data sync
- [ ] Mobile app (React Native)
- [ ] Push notifications for alerts
- [ ] Integration with wearables
- [ ] Telemedicine features
- [ ] Prescription management
- [ ] Lab report integration

---

**Built with ❤️ for better health monitoring**

**Repository**: https://github.com/Srishti-1806/Health_Connect
