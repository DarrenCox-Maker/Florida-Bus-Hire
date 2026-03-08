# 🚐 MiamiBusWatch

A self-contained, single-file price monitoring tool for **15-seat minibus hire in Miami Beach** — built for a specific trip: **Sunday 16 August → Sunday 30 August 2026** (14 days).

Powered by the [Anthropic Claude API](https://www.anthropic.com/) with live web search, so it finds and compares real current prices from rental companies and charter services every time you run it.

---

## ✨ Features

- **Live AI-powered price search** — Claude searches the web in real time for current minibus hire prices across multiple providers
- **Miami Beach pickup zones** — 8 selectable pickup locations all within 10 miles of Miami Beach, including MIA Airport, Downtown, South Beach, Wynwood and more
- **Auto-refresh timer** — re-checks prices automatically every 6 hours, with a live countdown ring
- **Email alerts** — triggers a mailto draft when prices drop, a new best deal appears, or a new provider is found
- **Daily summary emails** — scheduled digest sent once per day at your chosen time, including price trend vs. the previous day
- **Preview before send** — inspect the full email digest before it fires
- **Search history log** — tracks every manual and auto search with timestamps and best prices found

---

## 🚀 Getting Started

### 1. Get an Anthropic API Key

- Go to [console.anthropic.com](https://console.anthropic.com)
- Sign up or log in
- Navigate to **API Keys** and create a new key
- Note: API usage is billed per request. Claude Sonnet with web search costs roughly $0.01–0.05 per search run — very cheap for occasional monitoring

### 2. Open the App

Download `miami-minibus-tracker.html` and open it in any modern browser (Chrome, Firefox, Safari, Edge). No installation, no server, no build step required.

Or deploy to **GitHub Pages** — see below.

### 3. Enter Your API Key

Paste your Anthropic API key (`sk-ant-...`) into the key field at the top of the app and click **Save**.

> ⚠️ Your key is stored **in browser memory only** for the current session. It is never written to disk, never committed to this repo, and is cleared when you close the tab. Never share or publish your API key.

### 4. Select Pickup Locations & Run a Search

Choose your preferred pickup zones, configure vehicle type and pricing view, then hit **⚡ Search & Analyse Prices**.

---

## 🌐 Deploying to GitHub Pages

1. Fork or clone this repo
2. Go to your repo **Settings → Pages**
3. Set source to **Deploy from a branch → main → / (root)**
4. GitHub will publish the app at `https://yourusername.github.io/repo-name/miami-minibus-tracker.html`

Anyone with the link can use it — they'll just need to enter their own Anthropic API key.

---

## 🏗️ How It Works

```
User opens HTML file in browser
       ↓
Enters Anthropic API key (stored in memory only)
       ↓
Clicks Search (or auto-refresh timer fires)
       ↓
App sends prompt to Claude via Anthropic API
       ↓
Claude uses web_search tool to find current prices
       ↓
Returns structured JSON with providers, prices, tags
       ↓
App renders price cards + summary + recommendations
       ↓
If alerts triggered → opens pre-filled mailto: draft
```

All logic runs entirely in the browser. There is no backend, no database, no server.

---

## ⚙️ Configuration

Everything is editable directly in the HTML file:

| Variable | Location | Description |
|---|---|---|
| `PICKUP_DATE` | JS constants | Fixed pickup date |
| `RETURN_DATE` | JS constants | Fixed return date |
| `DURATION` | JS constants | Hire duration label |
| `HIRE_ZONE` | JS constants | Search zone description |
| `PICKUP_LOCATIONS` | JS array | Selectable pickup location chips |
| `INTERVAL_MS` | JS constant | Auto-refresh interval (default: 6 hours) |

To adapt this for different dates, locations, or vehicle types, edit those constants at the top of the `<script>` block.

---

## 📋 Requirements

- A modern web browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- An [Anthropic API key](https://console.anthropic.com) with access to `claude-sonnet-4-20250514`
- The tab must remain open for auto-refresh and scheduled daily emails to fire

---

## 🔒 Privacy & Security

- Your API key is **never stored** beyond the browser session memory
- No analytics, no tracking, no external requests except to `api.anthropic.com`
- Email alerts use `mailto:` links — your email client sends them, not this app
- No data is written to localStorage or any persistent storage

---

## 📄 License

MIT — see [LICENSE](LICENSE)

---

## 🤝 Contributing

This is a personal trip planning tool but PRs are welcome. Some ideas for extension:

- Support for multiple trip configurations
- CSV export of price history
- Browser notification support (Web Notifications API)
- Support for other vehicle types or cities
- Proxy server mode so the API key lives server-side

---

*Built with Claude Sonnet + web search. Not affiliated with Anthropic, any rental company, or any service mentioned in search results.*
