# Oklahoma Regional Weather Service

A regional weather service website for Oklahoma, built to be hosted on GitHub Pages. Pulls live data from the National Weather Service API with a custom GitHub-hosted fallback for the forecaster discussion.

## Setup

### 1. Create your GitHub repo
- Create a new public repo (e.g. `oklahoma-rws`)
- Upload `index.html`, `discussion.json`, and this `README.md`

### 2. Enable GitHub Pages
- Go to **Settings → Pages**
- Under **Source**, select `main` branch, `/ (root)` folder
- Hit **Save** — your site will be live at `https://YOUR_USERNAME.github.io/YOUR_REPO/`

### 3. Configure `index.html`
Open `index.html` and find the `CONFIG` block near the bottom:

```js
const CONFIG = {
  githubDiscussionUrl: "discussion.json",  // relative path — works as-is
  nwsOffice: "OUN",                        // NWS Norman, OK (covers statewide)
  nwsGridX: 61,
  nwsGridY: 89,
  discordUrl: "https://discord.gg/YOURINVITE",  // ← update this
};
```

Update `discordUrl` with your Discord server invite link.

### 4. Update contact info in the footer
Find the footer section in `index.html` and update:
- Email address
- Twitter/X handle
- YouTube channel

---

## Updating the Forecaster Discussion

The page tries to pull the **live NWS Area Forecast Discussion (AFD)** from Norman, OK automatically. If that fails, it falls back to your `discussion.json` file.

To write your own discussion, edit `discussion.json`:

```json
{
  "updated": "2025-03-28T12:00:00Z",
  "sections": [
    {
      "label": "Short Term (Today through Tomorrow)",
      "text": "Your short-term discussion here..."
    },
    {
      "label": "Long Term (Sunday onward)",
      "text": "Your long-term discussion here..."
    }
  ]
}
```

Push the updated file to your repo and it will appear on the site within minutes.

---

## NWS Gridpoint

The site uses the NWS gridpoint for Norman/OKC (`OUN 61,89`) which covers central Oklahoma and is representative of statewide conditions. You can look up other gridpoints at:

```
https://api.weather.gov/points/{LAT},{LON}
```

---

## Data Sources
- **7-Day Forecast**: [NWS API](https://api.weather.gov)
- **Current Conditions**: NWS Observations (KOKC, KTUL, KLTS, KEND stations)
- **Radar**: Windy.com embed
- **Alerts**: NWS Active Alerts for Oklahoma
