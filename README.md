# 🌧 HK Rainfall Alert

A lightweight web app that checks the **Hong Kong Observatory Gridded Rainfall Nowcast API** every 12 minutes and alerts you if rain is expected in your location within the **next 30–60 minutes**.

🌐 **Live App:** https://hans-tsang.github.io/hk-rainfall-alert/

## Features

- 📍 Auto-detects your GPS location (falls back to Tung Chung)
- 🌧 Shows rainfall forecast for the next 30 / 60 / 90 / 120 minutes
- 🔔 Browser push notifications (when permission granted)
- 📧 Email alert via `mailto:` (opens your mail client)
- 🔄 Auto-refreshes every 12 minutes (same as HKO update frequency)
- 📊 Visual bar chart for each forecast window
- Activity log for debugging

## Data Source

- HKO Open Data API: `https://data.weather.gov.hk/weatherAPI/hko_data/F3/`
- Gridded rainfall nowcast (CSV), updated every 12 minutes
- Each file covers a 30-minute interval, up to 2 hours ahead
- Docs: [HKO_gridded_rainfall_nowcast_documentation.pdf](https://data.weather.gov.hk/weatherAPI/hko_data/F3/HKO_gridded_rainfall_nowcast_documentation.pdf)

## Notification Methods

| Method | How it works | Requires |
|---|---|---|
| Browser Push | Native notification popup | Click "Enable" in app + allow in browser |
| Email (mailto) | Opens your mail client | Enter email in app |

> **Note:** The `mailto:` approach opens your email client automatically when rain is detected. For fully automated background email (without user interaction), a backend server (e.g. Node.js + SendGrid) would be needed.

## CORS Note

The app uses [corsproxy.io](https://corsproxy.io) to fetch HKO CSV files from the browser. If that proxy is unavailable, the app falls back gracefully.

## Local Development

Just open `index.html` in a browser — no build step needed.
