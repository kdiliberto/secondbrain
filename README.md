# Second Brain — AI Sales Intelligence for Insurance

A 4-step AI-powered sales engine for insurance agents: client fingerprinting, target market recommendations, live prospect radar, and pipeline coaching.

---

## Project Structure

```
second-brain/
├── public/
│   └── index.html       ← Frontend (deploy to GitHub Pages)
├── server/
│   └── index.js         ← Proxy server (deploy to Railway)
├── package.json
├── .env.example
└── README.md
```

---

## Step 1 — Deploy the Frontend to GitHub Pages

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Source: **Deploy from a branch** → Branch: `main` → Folder: `/public`
4. Save — your app is live at `https://YOUR-USERNAME.github.io/second-brain`

The app works immediately with smart mock AI. To enable real Claude AI, complete Step 2.

---

## Step 2 — Deploy the Proxy Server to Railway

The proxy lets your frontend call the Anthropic API securely (no API key exposed in the browser).

### Option A: Railway (recommended, free tier available)

1. Go to [railway.app](https://railway.app) and sign in with GitHub
2. Click **New Project → Deploy from GitHub repo** → select this repo
3. Railway auto-detects Node.js and runs `npm start`
4. Go to **Variables** and add:
   ```
   ANTHROPIC_API_KEY=your_key_here
   ```
5. Go to **Settings → Networking → Generate Domain**
6. Copy your Railway URL (e.g. `https://second-brain-proxy.up.railway.app`)

### Option B: Render (also free)

1. Go to [render.com](https://render.com) → New → Web Service
2. Connect your GitHub repo
3. Build command: `npm install`
4. Start command: `npm start`
5. Add environment variable: `ANTHROPIC_API_KEY=your_key_here`
6. Deploy and copy your URL

---

## Step 3 — Connect Frontend to Proxy

1. Open your live GitHub Pages app
2. In the **PROXY URL** bar at the top, paste your Railway/Render URL
   - Example: `https://second-brain-proxy.up.railway.app`
3. Click **Test connection** — it should turn green: `● Live AI connected`
4. Done — all AI responses now use real Claude via your proxy

---

## Running Locally

```bash
# Install dependencies
npm install

# Add your API key
cp .env.example .env
# Edit .env and add your ANTHROPIC_API_KEY

# Start the proxy server
npm start

# Open public/index.html in your browser
# Set proxy URL to: http://localhost:3001
```

---

## Features

| Feature | Description |
|---|---|
| 🧠 Client Fingerprint | AI interviews agent across 4 questions, builds ideal client profile |
| 🎯 Target Markets | 3 ranked market segments personalized to the agent's fingerprint |
| ⚡ Prospect Radar | 7 prioritized prospects with live trigger signals + fit scores |
| 💬 Pipeline Coach | Deal-by-deal diagnosis + next action recommendation |
| 🔔 Alert Tray | Real-time notification center for stale deals + new triggers |
| 📧 Email Digest | One-click daily summary sendable via email client |
| ✉️ Outreach Drafts | AI-written outreach message per prospect or deal |

---

## Environment Variables

| Variable | Required | Description |
|---|---|---|
| `ANTHROPIC_API_KEY` | Yes (for live AI) | Your Anthropic API key |
| `PORT` | No | Server port (default: 3001) |

---

## Tech Stack

- **Frontend**: Vanilla HTML/CSS/JS — zero dependencies, works anywhere
- **Proxy**: Node.js + Express — 20 lines, dead simple
- **AI**: Claude claude-sonnet-4-20250514 via Anthropic API
- **Hosting**: GitHub Pages (frontend) + Railway or Render (proxy)
