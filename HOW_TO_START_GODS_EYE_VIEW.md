# 🌐 Overwatch / God's Eye View — Local Startup Manual

This manual provides step-by-step instructions for running the **God's Eye View (Overwatch)** 3D global intelligence console locally on this machine.

---

## 📋 System Status & Prerequisites Check

The environment on this machine has already been verified:

| Component | Status | Detected Version |
| :--- | :--- | :--- |
| **Project Location** | Ready | `/home/kali/Desktop/gods-eye-view` |
| **Node.js** | Supported | `v24.21.0` (meets `v24.14+` requirement) |
| **npm** | Ready | `12.0.2` |
| **Dependencies** | Installed | `node_modules` verified & ready |
| **Browsers** | Installed | Chromium (`/usr/bin/chromium`), Firefox (`/usr/bin/firefox`) |

---

## 🚀 Quick Start (In 2 Steps)

### Step 1: Open Terminal and Start the Dev Server

Open your terminal and execute:

```bash
cd /home/kali/Desktop/gods-eye-view
npm run dev
```

You should see output similar to:
```text
  VITE v6.4.3  ready in ~3900 ms

  ➜  Local:   http://localhost:4173/
  ➜  press h + enter to show help
```

### Step 2: Open in Your Web Browser

Open your hardware-accelerated browser and navigate to:

👉 **[http://localhost:4173](http://localhost:4173)**

Or launch it directly from another terminal:
```bash
xdg-open http://localhost:4173
```

---

## ⚡ Keyless Mode vs. Optional API Keys

### Ready Out-of-the-Box (No API Keys Needed)
The project runs immediately with free, public datasets:
- **Satellite Basemap & 3D Terrain:** Esri World Imagery (with OSM automatic fallback).
- **Live Flights:** OpenSky Network public feed (anonymous rate-limited).
- **Satellites & Orbital Mechanics:** Active satellites & ISS tracking (NORAD / CelesTrak).
- **Natural Hazards:** Earthquakes (USGS live feed).
- **Public Cameras & Radio:** World CCTV cameras and public web radio streams.
- **Space Missions:** Rocket launches (Launch Library 2).
- **Weather / Cyclone Paths:** GFS / ECMWF wind & cyclone tracking.

### Optional API Keys (For Photorealism & Voice)
You do **not** need to edit config files manually. You can configure keys directly inside the running web app:
1. Look at the bottom-right corner of the running web interface.
2. Click the **POWER UP** button / chip.
3. Paste any keys you have:
   - **Cesium ion Token:** Unlocks Photorealistic 3D Tiles and Cesium World Terrain.
   - **Google Maps API Key:** Unlocks Google Photorealistic 3D Tiles & Google Places search.
   - **OpenAI API Key:** Enables real-time AI voice commands and agent control.
   - **AISStream Key:** Live global marine vessel tracking.
   - **NASA FIRMS Key:** Real-time wildfire and thermal anomaly tracking.
4. The in-app manager will save the keys to `.env` and restart the server automatically.

---

## 🛠️ Helpful Management Commands

Run these from `/home/kali/Desktop/gods-eye-view`:

### Check System & Data Provider Health
```bash
npm run doctor
```
Checks Node version, dependency integrity, and shows which providers (OpenSky, Cesium, OpenAI, etc.) are active or missing keys.

### Run on a Custom Port
If port `4173` is busy or you want a different port:
```bash
PORT=5000 npm run dev
```
Then open `http://localhost:5000`.

### Production Build & Preview
To create an optimized production build:
```bash
npm run build
npm run preview
```

---

## 💡 Troubleshooting & Performance Tips

1. **Hardware Acceleration (GPU):**
   - Cesium 3D runs significantly faster with GPU acceleration enabled.
   - In **Chromium**, visit `chrome://gpu` to verify that "WebGL" and "Hardware Accelerated" are enabled.
2. **Stopping the Server:**
   - In the terminal where `npm run dev` is running, press `Ctrl + C`.
3. **Clearing Cache:**
   - If UI changes or tiles fail to render, clear your browser cache or run:
     ```bash
     rm -rf node_modules/.vite .gev-cache
     npm run dev
     ```
