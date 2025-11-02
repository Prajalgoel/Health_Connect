# API Setup Instructions for Health Connect

## Overview
This guide will help you configure all the necessary API keys for the Health Connect application to enable real-time air quality data fetching and AI features.

## Required API Keys

### 1. WAQI (World Air Quality Index) API Key
The WAQI API provides real-time air quality data from monitoring stations worldwide.

#### How to Get Your Free API Key:
1. Visit [https://aqicn.org/data-platform/token/](https://aqicn.org/data-platform/token/)
2. Fill out the registration form with:
   - Your name
   - Your email address
   - A brief description of your project (e.g., "Health monitoring dashboard")
3. Submit the form
4. You'll receive an API token via email (usually within a few minutes)
5. Copy the token - it will look something like: `abc123def456ghi789`

#### Features Enabled:
- Real-time AQI data for 13,000+ cities worldwide
- Pollutant level details (PM2.5, PM10, O3, NO2, SO2, CO)
- Air quality monitoring station information

### 2. GROQ API Key
GROQ powers the AI assistant and medical chatbot features.

#### How to Get Your API Key:
1. Visit [https://console.groq.com/](https://console.groq.com/)
2. Sign up or log in
3. Navigate to API Keys section
4. Create a new API key
5. Copy the key (it starts with `gsk_`)

## Configuration Steps

### Step 1: Locate Your Environment File
Navigate to your project root directory:
```bash
cd e:\webdev\Health_Connect
```

### Step 2: Update the .env File
Open the `.env` file in your project root and update it with your actual API keys:

```env
# GROQ API Key for AI features
GROQ_API_KEY="your_actual_groq_api_key_here"

# WAQI Air Quality API Configuration
NEXT_PUBLIC_WAQI_API_KEY=your_actual_waqi_api_key_here
NEXT_PUBLIC_WAQI_BASE_URL=https://api.waqi.info
```

**Example with real keys:**
```env
GROQ_API_KEY="gsk_abc123XYZ456def789..."
NEXT_PUBLIC_WAQI_API_KEY=1a2b3c4d5e6f7g8h9i0j
NEXT_PUBLIC_WAQI_BASE_URL=https://api.waqi.info
```

### Step 3: Restart Your Development Server
After updating the `.env` file, you **MUST** restart your Next.js development server for the changes to take effect:

1. Stop the current server (Ctrl+C in terminal)
2. Restart it:
```bash
npm run dev
```
or
```bash
pnpm dev
```

### Step 4: Verify the Configuration
1. Open your browser and navigate to `http://localhost:3000/dashboard/air-quality`
2. Check the badge at the top - it should show "Live Data" instead of "Demo Data"
3. Select different cities to test real-time data fetching
4. Check the browser console (F12) for any error messages

## Troubleshooting

### Problem: Still showing "Demo Data" after adding API key

**Solutions:**
1. **Restart the dev server** - Environment variables are only read at server startup
2. **Check API key format** - Make sure there are no extra quotes or spaces
3. **Verify the key is correct** - Test your API key directly:
   ```
   https://api.waqi.info/feed/delhi/?token=YOUR_API_KEY
   ```
4. **Check console logs** - Open browser DevTools (F12) and look for error messages

### Problem: "HTTP 401 Unauthorized" or "Invalid token"

**Solutions:**
- Your API key is incorrect or has expired
- Request a new API key from aqicn.org
- Make sure you copied the entire token

### Problem: "Unable to fetch data" error

**Solutions:**
1. **Check internet connection**
2. **Verify city name** - Try a major city like "delhi", "london", or "beijing"
3. **API might be down** - Check [https://aqicn.org/](https://aqicn.org/) status
4. **Rate limit reached** - Free tier has limits; wait a few minutes

### Problem: Environment variable not found

**Solutions:**
1. **File location** - Make sure `.env` is in the project root (same level as `package.json`)
2. **Variable naming** - Variables must start with `NEXT_PUBLIC_` to be accessible in client components
3. **No quotes for NEXT_PUBLIC vars** - Don't use quotes around values:
   ```env
   # ✅ Correct
   NEXT_PUBLIC_WAQI_API_KEY=abc123
   
   # ❌ Wrong
   NEXT_PUBLIC_WAQI_API_KEY="abc123"
   ```

## Testing Your Setup

### Test 1: Console Logs
Open the air quality page and check the browser console (F12). You should see:
```
=== Loading AQI Data ===
Use Real API: true
Location: delhi
API Key configured: true
Fetching AQI data for: delhi
Successfully fetched AQI: [some number]
```

### Test 2: Manual API Test
Test your API key directly in the browser:
```
https://api.waqi.info/feed/delhi/?token=YOUR_ACTUAL_API_KEY
```

Expected response:
```json
{
  "status": "ok",
  "data": {
    "aqi": 156,
    "city": {
      "name": "Delhi, India"
    },
    ...
  }
}
```

### Test 3: Different Cities
Try selecting different cities from the dropdown:
- Delhi, India
- Beijing, China
- London, UK
- New York, USA

Each should show different real-time AQI values.

## Security Notes

⚠️ **Important Security Information:**

1. **Never commit `.env` to Git** - It's already in `.gitignore`
2. **NEXT_PUBLIC_ variables are exposed to the browser** - They're visible in client-side code
3. **Keep GROQ_API_KEY private** - Server-side only (no NEXT_PUBLIC_ prefix)
4. **Use different keys for production** - Create separate API keys for development and production

## API Limits

### WAQI Free Tier:
- ✅ Unlimited requests for non-commercial use
- ✅ Real-time data from 13,000+ cities
- ✅ Historical data (limited)
- ❌ No SLA guarantee
- ❌ Rate limiting may apply during high traffic

### GROQ Free Tier:
- Check their current limits at [https://console.groq.com/](https://console.groq.com/)

## Need Help?

If you're still experiencing issues:
1. Check the browser console for detailed error messages
2. Verify your API keys are active and valid
3. Test the API endpoint directly in your browser
4. Ensure your `.env` file is in the correct location
5. Confirm you restarted the development server after making changes

## Quick Reference

```bash
# File locations
.env                          # Your actual API keys (DO NOT COMMIT)
.env.example                  # Template file (safe to commit)

# Required environment variables
GROQ_API_KEY                  # Server-side only
NEXT_PUBLIC_WAQI_API_KEY      # Client-side (browser accessible)
NEXT_PUBLIC_WAQI_BASE_URL     # API base URL

# Restart server command
npm run dev                   # or pnpm dev
```

---

**Last Updated:** November 2, 2025
