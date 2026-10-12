# 🚀 Deployment Guide — from zero to live in ~15 minutes

Everything here is **free**. You need: a GitHub account, a browser, and (optionally) a Cloudflare account and a Finnhub account.

Live site: <https://kbgirishhb.github.io/Onepercentage/> · Repo: `KBgirishHB/Onepercentage`

---

## 1 · Create the repository

1. Go to **github.com → New repository**
2. Name: `Onepercentage` · Visibility: **Public** (required — free Pages & the raw-data tier need it)
3. Click **Create repository**

## 2 · Upload the app

1. On the empty repo page click **“uploading an existing file”**
2. Drag in `index.html` (rename it exactly that if needed), plus `README.md`, `LICENSE.txt` and the `docs/` folder
3. Commit changes

## 3 · Turn on GitHub Pages

1. **Settings → Pages** (left sidebar)
2. Source: **Deploy from a branch** → Branch: **main** · Folder: **/ (root)** → **Save**
3. Wait ~1 minute, refresh — the URL appears at the top:

```text
https://kbgirishhb.github.io/Onepercentage/
```

### ✅ Checkpoint 1
Open the URL. The app loads, the ticker tape renders, and the badge shows one of: `LIVE`, `GH · DELAYED`, `CACHED` or `SIMULATED`. Any badge = the app works. Now upgrade the data:

---

## 4 · Fix A — GitHub Action snapshot (guaranteed real data, ~5-min delay)

This runs **inside GitHub itself**, fetches Yahoo server-side (no CORS problem at all), and publishes one JSON file the app auto-detects.

1. In your repo: **Add file → Create new file**
2. Type the path (this creates the folders automatically):

```text
.github/workflows/market-bundle.yml
```

3. Paste this entire file:

```yaml
name: market-bundle
on:
  schedule: [{cron: "*/5 * * * *"}]
  workflow_dispatch: {}
permissions: {contents: write}
concurrency: {group: bundle, cancel-in-progress: true}
jobs:
  bundle:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - uses: actions/checkout@v4
      - run: |
          python3 - <<'PY'
          import json, time, urllib.request, urllib.parse
          SYMS=["AAPL","MSFT","NVDA","TSLA","AMD","GOOGL","SPY","QQQ","IWM","^VIX","GLD","^NSEI","RELIANCE.NS","TCS.NS"]
          UA={"User-Agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64)"}
          def grab(sym,rng,iv):
              u=f"https://query1.finance.yahoo.com/v8/finance/chart/{urllib.parse.quote(sym)}?range={rng}&interval={iv}&includePrePost=false"
              d=json.load(urllib.request.urlopen(urllib.request.Request(u,headers=UA),timeout=20))
              r=d["chart"]["result"][0]; q=r["indicators"]["quote"][0]; ts=r.get("timestamp") or []
              out=[[t*1000,q["open"][i] or c,q["high"][i] or c,q["low"][i] or c,c,q["volume"][i] or 0]
                   for i,t in enumerate(ts) if (c:=q["close"][i]) is not None]
              return out, r["meta"].get("regularMarketPrice"), r["meta"].get("chartPreviousClose"), r["meta"].get("currency","USD")
          b={"ts":int(time.time()*1000)}
          for s in SYMS:
              try:
                  m5,p,pc,cur=grab(s,"1d","5m")
                  m15,_,_,_=grab(s,"5d","15m")
                  d1,_,_,_=grab(s,"1y","1d")
                  if m5: b[s]={"cur":cur,"p":p,"pc":pc,"m5":m5,"m15":m15[-130:],"d1":d1[-252:]}
                  time.sleep(0.7)
              except Exception as e: print("skip",s,e)
          json.dump(b,open("bundle.json","w"),separators=(",",":"))
          PY
      - run: |
          git config user.name "market-bot"
          git config user.email "bot@users.noreply.github.com"
          git checkout --orphan data-tmp
          git rm -rf --cached . -q || true
          git add -f bundle.json
          git commit -m "bundle $(date -u +%FT%TZ)" -q
          git push -f origin HEAD:data -q
```

4. **Commit changes** (to `main` — Actions only run scheduled jobs from the default branch)
5. Go to the **Actions** tab → **market-bundle** → **Run workflow** → **Run workflow** (manual first run)
6. Wait ~2 minutes until the run shows a green ✓

### ✅ Checkpoint 2
Open this in a browser:

```text
https://raw.githubusercontent.com/KBgirishHB/Onepercentage/data/bundle.json
```

You should see JSON with a `"ts"` field and your symbols. Then **hard-refresh your site** (`Ctrl+Shift+R`) → the badge shows **`GH · DELAYED`** and every bundled symbol has real candles.

> **Notes**
> - GitHub disables scheduled workflows after ~60 days of repo inactivity — push anything, or re-run manually, to reactivate.
> - Want more symbols? Add them to `SYMS` in the YAML **and** to `DIR` + `SIMBASE` in `index.html` (see ARCHITECTURE §Extend).
> - The bundle carries 5m / 15m / 1D candles — true 1-minute captures need Fix B (or the live-relay tier).

---

## 5 · Fix B — Cloudflare Worker (true real-time, your private proxy)

1. Create a free account at **workers.dev** → **Create Worker**
2. Replace the starter code with:

```js
export default {
  async fetch(req) {
    const target = new URL(req.url).searchParams.get("url");
    if (!target) return new Response("missing ?url=", { status: 400 });
    const r = await fetch(target, { headers: { "User-Agent": "Mozilla/5.0" } });
    const h = new Headers(r.headers);
    h.set("Access-Control-Allow-Origin", "*");
    h.delete("content-encoding");
    return new Response(r.body, { status: r.status, headers: h });
  }
};
```

3. **Deploy** → copy your URL, e.g. `https://my-proxy.yourname.workers.dev/`
4. Edit `index.html` in your repo, find this line near the top of the script:

```js
const MY_WORKER  = "";
```

and set it:

```js
const MY_WORKER  = "https://my-proxy.yourname.workers.dev/?url=";
```

5. Commit. Hard-refresh your site.

### ✅ Checkpoint 3
Badge shows **`LIVE`** and the load toast names `my-worker`. Free tier = 100,000 requests/day — far more than this app uses.

---

## 6 · Fix C — optional Finnhub real-time quotes

1. Register free at **finnhub.io** → copy your API key
2. Edit `index.html`:

```js
const KEYS = { finnhub: "YOUR_KEY_HERE" };
```

US-stock quotes then tick in real time even while charts come from the GH snapshot (60 req/min free).

---

## 7 · Optional: custom domain

Repo **Settings → Pages → Custom domain** → add your domain, plus a `CNAME` record `www → kbgirishhb.github.io` at your DNS provider. GitHub issues an HTTPS certificate automatically.

## 8 · Updating the app later

Replace `index.html` with the new version (upload → commit). Pages redeploys automatically in ~1 minute. Your journal, settings and plan live in **your browser’s** localStorage — updates never lose them.

## 9 · Badge verification matrix

| Badge | Meaning | You likely did |
|---|---|---|
| `● LIVE` | Real-time data (relay or Worker; WebSocket for crypto) | Fix B — or relays are healthy today |
| `● GH · DELAYED` | Real data ≤ ~10 min old from your repo | Fix A |
| `● CACHED` | Your last real data for this symbol | Nothing — auto, upgrades itself |
| `● SIMULATED` | Nothing real reachable right now | Do Fix A first |

## 10 · Troubleshooting

| Symptom | Fix |
|---|---|
| Raw URL gives 404 | The Action didn’t push — open Actions tab, check the log; confirm repo is **Public** |
| Action fails at push | Re-run the workflow; ensure the workflow file is on `main` |
| Badge stuck on `SIMULATED` after Fix A | Hard refresh (`Ctrl+Shift+R`) — browsers cache aggressively |
| 1m captures show `5m` in the header stamp | You’re on the GH tier (5m/15m/1D only) — expected; add Fix B for true 1m |
| Crypto works, stocks don’t | Normal without Fix A/B — Binance is CORS-open, Yahoo is not |
