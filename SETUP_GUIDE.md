# Health Connect - Real-Time AQI Setup Guide

## 🔧 Quick Fix for Real-Time AQI Updates

Your AQI page is currently showing **demo data** because the API key is not configured. Follow these steps to enable real-time air quality updates:

---

## ✅ Step-by-Step Setup

### 1. Get Your Free WAQI API Key

1. **Visit the WAQI Token Page**
   - Go to: https://aqicn.org/data-platform/token/

2. **Fill Out the Form**
   - **Name**: Your name
   - **Email**: Your email address
   - **Project Description**: "Personal health monitoring application"
   
3. **Submit and Check Email**
   - You'll receive your API token within 5-10 minutes
   - Check your spam folder if you don't see it

### 2. Configure the API Key

1. **Open the `.env.local` file** (already created in the root directory)

2. **Replace the placeholder** with your actual API key:
   ```env
   NEXT_PUBLIC_WAQI_API_KEY=your_actual_api_token_here
   ```
   
   Example (use your own token):
   ```env
   NEXT_PUBLIC_WAQI_API_KEY=abc123def456ghi789xyz
   ```

3. **Save the file** (Ctrl+S or Cmd+S)

### 3. Restart the Development Server

**Important**: Next.js only reads environment variables at startup!

1. **Stop the server**:
   - Press `Ctrl+C` in the terminal where your dev server is running

2. **Start the server again**:
   ```powershell
   pnpm dev
   ```
   
   Or if using npm:
   ```powershell
   npm run dev
   ```

3. **Wait for the server to start** (you'll see "Ready in X ms")

### 4. Verify It's Working

1. **Navigate to the Air Quality page**
   - Dashboard → Air Quality

2. **Check for the "Live Data" badge**
   - You should see a green "Live Data" badge next to the location
   - If you see "Demo Data", the API key isn't configured correctly

3. **Open Browser Console** (F12 or Right-click → Inspect → Console)
   - Look for console logs showing:
     ```
     === Loading AQI Data ===
     Using API key: configured
     Fetching AQI data for: delhi
     Successfully fetched AQI: 156
     ```

4. **Compare with Official Data**
   - Visit https://aqicn.org/city/delhi/ (or your selected city)
   - The AQI value should match (±5 points)

---

## 🔍 Troubleshooting

### Issue: Still Showing "Demo Data"

**Solution 1: Check the .env.local file**
- Make sure the file is in the ROOT directory (not in app/ or any subfolder)
- File should be named exactly `.env.local` (with the dot at the start)
- No extra spaces before or after the API key

**Solution 2: Verify the API key**
- Copy the key exactly as received in your email
- No quotes around the key
- No spaces before or after the equals sign

**Solution 3: Restart properly**
- Make sure you actually stopped the server (Ctrl+C)
- Don't just refresh the browser
- Start the server fresh with `pnpm dev`

### Issue: "Unable to fetch data" Error

**Check Console Logs**
```
Open browser console (F12) and look for error messages
```

**Common Causes:**
1. **Invalid API Key**: Double-check your token
2. **Network Issues**: Check your internet connection
3. **City Not Found**: Try different city name formats:
   - Just city: `delhi`, `mumbai`, `bangalore`
   - With country: `delhi, india`
   - Try alternative names: `new delhi` instead of `delhi`

**Solution**:
- Try selecting a different city from the dropdown
- Verify the API key at: https://api.waqi.info/feed/delhi/?token=YOUR_API_KEY
  (Replace YOUR_API_KEY with your actual key)

### Issue: Browser Console Shows Errors

**CORS Error**:
```
Access to fetch at 'https://api.waqi.info/...' has been blocked by CORS
```
- This shouldn't happen with WAQI API as it supports CORS
- Try using a different browser
- Clear browser cache

**Network Error**:
```
Failed to fetch
```
- Check your internet connection
- Try disabling browser extensions (ad blockers)
- Check if your firewall is blocking the API

### Issue: Data Not Updating

**Auto-refresh runs every 30 minutes**
- Click the "Refresh Data" button for manual updates
- Check browser console for any errors
- Verify the API key is still valid

---

## 📊 Understanding the Data

### What Data You'll See

**Real-Time Metrics:**
- **AQI**: Overall Air Quality Index (0-500)
- **PM2.5**: Fine particulate matter
- **PM10**: Coarse particulate matter
- **O₃**: Ozone levels
- **NO₂**: Nitrogen dioxide
- **SO₂**: Sulfur dioxide
- **CO**: Carbon monoxide

**Features:**
- Current AQI with health category
- 7-day historical trends
- 7-day predictions (ML-based)
- Today's hourly recommendations
- Personalized health advice

### Update Frequency

- **WAQI Stations**: Update every 1 hour
- **App Auto-Refresh**: Every 30 minutes
- **Manual Refresh**: Anytime via button

---

## 🌍 Supported Locations

### Popular Indian Cities
- Delhi, Mumbai, Bangalore, Chennai, Kolkata
- Hyderabad, Pune, Ahmedabad, Jaipur, Lucknow

### International Cities
- Beijing, Shanghai, Tokyo, Singapore
- London, Paris, Berlin, Amsterdam
- New York, Los Angeles, San Francisco

**Format Options:**
- Simple: `delhi`, `mumbai`, `bangalore`
- With country: `delhi, india`
- Coordinates: `@28.6139,77.2090`

---

## 🔐 Security & Privacy

✅ **Safe to Use**:
- WAQI API is designed for client-side use
- Free tier limits prevent abuse
- No sensitive data transmitted

⚠️ **Best Practices**:
- Never commit `.env.local` to Git (already in .gitignore)
- Don't share your API key publicly
- Use environment variables for production

---

## 📈 API Limits

**Free Tier:**
- 1,000 requests per day
- No credit card required
- No expiration

**Your Usage:**
- Auto-refresh: ~48 requests/day per user
- Manual refresh: As needed
- **Total**: Well within limits

---

## 🆘 Still Having Issues?

### Debug Checklist

- [ ] `.env.local` file exists in root directory
- [ ] API key is correctly pasted (no extra spaces/quotes)
- [ ] Development server was restarted after adding key
- [ ] Browser was refreshed (hard refresh: Ctrl+Shift+R)
- [ ] Console shows no errors
- [ ] Internet connection is working
- [ ] API key is valid (test at aqicn.org)

### Test Your API Key Manually

Open this URL in your browser (replace YOUR_API_KEY):
```
https://api.waqi.info/feed/delhi/?token=YOUR_API_KEY
```

**Expected Response:**
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

If you see `"status": "error"`, your API key is invalid.

---

## 📚 Additional Resources

- **Get API Key**: https://aqicn.org/data-platform/token/
- **API Documentation**: https://aqicn.org/json-api/doc/
- **Check AQI**: https://aqicn.org/
- **Support**: https://aqicn.org/contact/

---

## ✨ Next Steps After Setup

Once you have real-time data working:

1. **Add Your Health Conditions**
   - Click "Set Up Health Profile" on the Health Recommendations tab
   - Get personalized advice based on AQI levels

2. **Explore Features**
   - Check today's best times to go outside
   - View 7-day AQI predictions
   - Monitor historical trends

3. **Set Up Notifications** (optional)
   - Enable alerts for high AQI levels
   - Get reminders to check air quality

---

**That's it!** You should now have real-time AQI data updating in your application. If you followed all steps and it's still not working, check the debug checklist above or open the browser console for detailed error messages.
