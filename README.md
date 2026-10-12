🎯 ONEPERCENT
The risk-first market terminal that lives in a single index.html

Real-time stocks & crypto · the 1% rule enforced everywhere · no backend · no API keys

Live DemoLicense: MITAPI KeysBackendBuild

User Guide · Deployment · Architecture · Report an Issue

Why ONEPERCENT exists
Every trading app shows you prices. Almost none forces you to size the position, place the stop, and plan the exit before you get excited.

ONEPERCENT is built backwards from risk: the 1% rule is the spine, and everything else — charts, signals, the screenshot grader — exists to answer one question:

“What exactly do I buy, how much of it, where am I wrong, and when do I walk away with the money?”

✨ Features
Feature	What it does
📈	Live market data	Stocks, ETFs, indices, Indian names (.NS), crypto — keyless, with a tiered fallback chain so the app never dies
🕯	Hand-built candlestick chart	7 timeframes (1D→5Y), 1m–1w intervals, zoom / pan / crosshair / volume — zero chart libraries
🎛	Indicators	EMA20/50, VWAP, Bollinger Bands, Volume, plus RSI & ATR signals with plain-English reads
🛡	1% Risk Engine	Daily risk dial with a hard ceiling, position sizer (exact quantity from stop distance), allocation cap, fee-aware breakeven
📸	Capture → Analyze	One click: switches to the 1-minute chart, computes a fresh swing+ATR plan, snapshots it, and grades R:R in the analyzer — levels pre-marked & synced
🖼	Screenshot Analyzer	Drop/paste any broker screenshot, calibrate two gridlines, drag three lines → live verdict: TAKE / MARGINAL / REJECT (anything under 2R is rejected)
⏱	Exit / Withdraw Planner	4 strategies — Sniper, Scale-out, Time-stop, ATR trail — with duration estimated from live ATR in real sessions
📓	Trade Journal	R-multiple based, auto-logged on close; win rate, expectancy, equity curve — stored on your device only
🌏	MY PLAN & Timings	Live IST + ET clocks, open/close countdowns, hour-by-hour “when should you trade” windows, and a 4-question wizard that builds your personal plan
💱	USD ⇄ INR	One toggle converts the entire terminal at the live FX rate (24h cache, offline fallback)
🧪	Honest feed badges	LIVE / GH · DELAYED / CACHED / SIMULATED — simulated data is never passed off as real
⌨️	Keyboard-first	/ search · 1–7 timeframes · C capture · ? guide
🧭 The 1% engine in 20 seconds
Account ₹8,00,000   →  daily risk budget ₹8,000        (1%)Stop is ₹20 away    →  quantity = 8,000 ÷ 20 = 400 sharesStopped out?        →  you lose exactly ₹8,000 = 1% — survivable, repeatableTarget at 2R        →  you only need ~40% winners to grow
The dial caps the whole day at 1%. Arming a trade requires passing a 5-point pre-flight checklist — including “I will not move my stop further away.”

🚀 Try it in 60 seconds
Open the live demo above — or download index.html and double-click it
Pick USD $ / INR ₹ in the header, enter your account size
Press /, type any stock → AUTO PLAN → CAPTURE → ANALYZE (1m)
Read the verdict: TAKE = ≥2R with a defined stop. Everything else is a lesson, not a trade.
📦 Deploy your own (free, ~5 minutes)
GitHub Pages hosts it as-is — one file, no build step.

# 1. create a PUBLIC repo named "onepercent"# 2. upload index.html to main# 3. Settings → Pages → Deploy from a branch → main / (root)# 4. done → https://YOUR-USERNAME.github.io/onepercent/
Full click-by-click guide (with screenshots to take) → docs/DEPLOYMENT.md

Unlock real-time data (optional, still free)
Static pages can’t call Yahoo directly (no CORS headers), so the app ships with a smart fallback chain. To make it bulletproof:

Fix	What you get	Setup
A — GitHub Action	A snapshot refreshed every 5 min → guaranteed real data (GH · DELAYED badge)	§4 of DEPLOYMENT.md — one YAML file
B — Cloudflare Worker	Your private proxy → true real-time (LIVE badge, 100k req/day free)	§5 of DEPLOYMENT.md — 12 lines
C — Finnhub key (optional)	Real-time quote upgrades on top of any tier	§6 of DEPLOYMENT.md — one constant
📸 Screenshots
Add yours: run the app, capture these five views, and save them into docs/screenshots/ with these exact filenames — then uncomment the image block below.

Filename	What to capture
terminal.png	Full workspace — chart + Trade Desk + signals
capture-analyze.png	The analyzer with pre-marked ENTRY / STOP / TARGET
plan.png	MY PLAN tab with the live IST clocks
exit-planner.png	A scale-out schedule
journal.png	The journal with a few logged trades
📋 Ready-made image block (uncomment after adding screenshots)
🗂 Documentation
Doc	Contents
User Guide	Every feature, IST market timings, broker quick-steps, indicator cheat-sheet, glossary
Deployment	GitHub Pages setup + GitHub Action + Cloudflare Worker + Finnhub, with verification checklists
Architecture	Data-tier decision flow, capture pipeline, bundle schema, extension recipes
🏗 Architecture (30-second version)
flowchart LR    U[Browser · one file] --> Q{Symbol}    Q -- crypto --> B[Binance REST + WebSocket<br/>LIVE · keyless]    Q -- stocks / ETFs --> C[localStorage cache]    C --> G[GitHub Actions bundle<br/>raw.githubusercontent<br/>GH · DELAYED]    G --> W{Worker configured?}    W -- yes --> WR[Your Cloudflare Worker<br/>LIVE real-time]    W -- no --> R[Public CORS relays<br/>health-scored race]    R -- all fail --> S[Simulated tape<br/>clearly badged]
All math — indicators, R-multiples, grading, sizing — runs in your browser. Nothing about you leaves the device. Full details in ARCHITECTURE.md.

🔬 Built on the shoulders of
Research & inspiration from these excellent repositories:

Repo	What it informed
TradingView/lightweight-charts	chart UX reference — we hand-rolled ours to stay single-file
ranaroussi/yfinance	Yahoo endpoint behaviour
gadicc/node-yahoo-finance2	chart-API edge cases & rate limits
twopirllc/pandas-ta	indicator definitions (EMA/RSI/ATR/VWAP/Bollinger)
backtrader/backtrader	exit-strategy concepts (scale-out, chandelier)
Zibri/cloudflare-cors-anywhere	the Worker relay pattern
public-apis/public-apis	market-data landscape survey
🗺 Roadmap
 1% risk engine — sizer, daily dial, checklist
 Capture → Analyze 1-minute pipeline
 USD/INR conversion · IST market timings · personal plan wizard
 GitHub-Action data tier (real data on a static host)
 Price alerts with browser notifications
 Daily screener — top movers matching your signal profile
 Backtested stats per exit strategy
 Hindi UI
 PWA offline mode
🤝 Contributing
Issues and PRs welcome — especially:

new symbols / relays (each is a one-line addition — see ARCHITECTURE §Extend)
bug reports with a screenshot showing the feed badge + timeframe
code style rule: it must stay one file, no build step, no required keys
❓ FAQ
Does it place real orders?No — it’s analysis + discipline tooling. You execute in your broker app; the User Guide’s “Quick Steps” covers the exact workflow.

Is the data delayed?The badge always tells you: LIVE (real-time) · GH · DELAYED (≤ ~10 min) · CACHED (your last real data) · SIMULATED (not real — never trade on it).

Why do stocks need “Fix A/B” when crypto just works?Binance sends open CORS headers; Yahoo doesn’t. Browsers physically cannot call Yahoo directly — §4/§5 of the Deployment guide solve it permanently.

What does it cost?Nothing. GitHub Pages, Actions, and the Cloudflare Worker free tier cover everything.

⚠️ Disclaimer
ONEPERCENT is an educational tool. Nothing here is investment advice. Market data may be delayed, incomplete, or — when the badge says so — simulated. Always verify prices with your broker before acting. Trading involves substantial risk of loss; the 1% rule exists because survival is the prerequisite of every other skill in the market.

License
MIT — do whatever you like; keep the disclaimer.

If ONEPERCENT saved you from one oversized position, consider ⭐ starring the repo.
