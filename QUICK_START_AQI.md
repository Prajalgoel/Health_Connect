# 🚀 Quick Start - Enable Real-Time AQI

## The Problem
Your Air Quality page shows "Demo Data" because the API is not configured yet.

## The Solution (3 Simple Steps)

### 1️⃣ Get FREE API Key (5 minutes)
👉 Visit: **https://aqicn.org/data-platform/token/**
- Fill in your name and email
- Description: "Personal health app"
- Check email for token

### 2️⃣ Add to .env.local file
📝 Open: **`.env.local`** (in root folder - already created!)
```env
NEXT_PUBLIC_WAQI_API_KEY=paste_your_token_here
```
💾 Save the file

### 3️⃣ Restart Server
```powershell
# Press Ctrl+C to stop, then:
pnpm dev
```

## ✅ Check If Working
- Go to **Dashboard → Air Quality**
- Look for **"Live Data"** badge (green)
- AQI should match real values from https://aqicn.org

## 🔧 Not Working?
1. ✔️ Server was restarted (not just browser refresh)
2. ✔️ API key has no extra spaces or quotes
3. ✔️ .env.local is in root folder (not inside app/)
4. ✔️ Internet connection is working

### Test Your Key
Replace YOUR_KEY and open in browser:
```
https://api.waqi.info/feed/delhi/?token=YOUR_KEY
```
Should show: `"status": "ok"`

## 📖 Detailed Help
See **SETUP_GUIDE.md** for complete troubleshooting

## 💡 Current Features Working:
- ✅ Demo data (always works)
- ✅ All UI features
- ✅ Predictions and charts
- ⏳ Real-time updates (needs API key)

---
**Free Tier**: 1,000 requests/day (you'll use ~48/day)
**No Credit Card Required**
