馃幆 ONEPERCENT
The risk-first market terminal that lives in a single index.html

Real-time stocks & crypto 路 the 1% rule enforced everywhere 路 no backend 路 no API keys

Live DemoLicense: MITAPI KeysBackend

User Guide 路 Deployment 路 Architecture 路 Report an Issue

Why ONEPERCENT exists
Every trading app shows you prices. Almost none forces you to size the position, place the stop, and plan the exit before you get excited.

ONEPERCENT is built backwards from risk: the 1% rule is the spine, and everything else 鈥?charts, signals, the screenshot grader 鈥?exists to answer one question:

"What exactly do I buy, how much of it, where am I wrong, and when do I walk away with the money?"

鉁?Features
Feature	What it does
馃搱	Live market data	Stocks, ETFs, indices, Indian names (.NS), crypto 鈥?keyless, with a tiered fallback chain so the app never dies
馃暞	Hand-built candlestick chart	7 timeframes (1D鈫?Y), 1m鈥?w intervals, zoom / pan / crosshair / volume 鈥?zero chart libraries
馃帥	Indicators	EMA20/50, VWAP, Bollinger Bands, Volume, plus RSI & ATR signals with plain-English reads
馃洝	1% Risk Engine	Daily risk dial with a hard ceiling, position sizer (exact quantity from stop distance), allocation cap, fee-aware breakeven
馃摳	Capture 鈫?Analyze	One click: switches to the 1-minute chart, computes a fresh swing+ATR plan, snapshots it, and grades R:R in the analyzer 鈥?levels pre-marked & synced
馃柤	Screenshot Analyzer	Drop/paste any broker screenshot, calibrate two gridlines, drag three lines 鈫?live verdict: TAKE / MARGINAL / REJECT (anything under 2R is rejected)
鈴?Exit / Withdraw Planner	4 strategies 鈥?Sniper, Scale-out, Time-stop, ATR trail 鈥?with duration estimated from live ATR in real sessions
馃摀	Trade Journal	R-multiple based, auto-logged on close; win rate, expectancy, equity curve 鈥?stored on your device only
馃審	MY PLAN & Timings	Live IST + ET clocks, open/close countdowns, hour-by-hour "when should you trade" windows, and a 4-question wizard that builds your personal plan
馃挶	USD 鈬?INR	One toggle converts the entire terminal at the live FX rate (24h cache, offline fallback)
馃И	Honest feed badges	LIVE / GH 路 DELAYED / CACHED / SIMULATED 鈥?simulated data is never passed off as real
鈱笍	Keyboard-first	/ search 路 1鈥? timeframes 路 C capture 路 ? guide
馃Л The 1% engine in 20 seconds
Account 鈧?,00,000   鈫? daily risk budget 鈧?,000        (1%)Stop is 鈧?0 away    鈫? quantity = 8,000 梅 20 = 400 sharesStopped out?        鈫? you lose exactly 鈧?,000 = 1% 鈥?survivable, repeatableTarget at 2R        鈫? you only need ~40% winners to grow
The dial caps the whole day at 1%. Arming a trade requires passing a 5-point pre-flight checklist 鈥?including "I will not move my stop further away."

馃殌 Try it in 60 seconds
Open the live demo above 鈥?or download index.html and double-click it
Pick USD $ / INR 鈧?in the header, enter your account size
Press /, type any stock 鈫?AUTO PLAN 鈫?CAPTURE 鈫?ANALYZE (1m)
Read the verdict: TAKE = 鈮?R with a defined stop. Everything else is a lesson, not a trade.
馃摝 Deploy your own (free, ~5 minutes)
GitHub Pages hosts it as-is 鈥?one file, no build step.

# 1. create a PUBLIC repo named "onepercent"# 2. upload index.html to main# 3. Settings 鈫?Pages 鈫?Deploy from a branch 鈫?main / (root)# 4. done 鈫?https://kbgirishhb.github.io/Onepercentage/
Full click-by-click guide 鈫?docs/DEPLOYMENT.md

Unlock real-time data (optional, still free)
Static pages can't call Yahoo directly (no CORS headers), so the app ships with a smart fallback chain. To make it bulletproof:

Fix	What you get	Setup
A 鈥?GitHub Action	Snapshot refreshed every 5 min 鈫?guaranteed real data (GH 路 DELAYED badge)	搂4 of DEPLOYMENT.md 鈥?workflow file included in this repo
B 鈥?Cloudflare Worker	Your private proxy 鈫?true real-time (LIVE badge, 100k req/day free)	搂5 of DEPLOYMENT.md 鈥?12 lines
C 鈥?Finnhub key (optional)	Real-time quote upgrades on top of any tier	搂6 of DEPLOYMENT.md 鈥?one constant
馃摳 Screenshots
Add yours: capture the five views listed below into docs/screenshots/, then add image tags linking to them.

Filename	What to capture
terminal.png	Full workspace 鈥?chart + Trade Desk + signals
capture-analyze.png	The analyzer with pre-marked ENTRY / STOP / TARGET
plan.png	MY PLAN tab with the live IST clocks
exit-planner.png	A scale-out schedule
journal.png	The journal with a few logged trades
馃梻 Documentation
Doc	Contents
User Guide	Every feature, IST market timings, broker quick-steps, indicator cheat-sheet, glossary
Deployment	GitHub Pages setup + GitHub Action + Cloudflare Worker + Finnhub, with verification checklists
Architecture	Data-tier decision flow, capture pipeline, bundle schema, extension recipes
馃彈 Architecture (30-second version)
flowchart LR    U[Browser 路 one file] --> Q{Symbol}    Q -- crypto --> B[Binance REST + WebSocket<br/>LIVE 路 keyless]    Q -- stocks / ETFs --> C[localStorage cache]    C --> G[GitHub Actions bundle<br/>raw.githubusercontent<br/>GH 路 DELAYED]    G --> W{Worker configured?}    W -- yes --> WR[Your Cloudflare Worker<br/>LIVE real-time]    W -- no --> R[Public CORS relays<br/>health-scored race]    R -- all fail --> S[Simulated tape<br/>clearly badged]
All math 鈥?indicators, R-multiples, grading, sizing 鈥?runs in your browser. Nothing about you leaves the device. Full details in ARCHITECTURE.md.

馃敩 Built on the shoulders of
Research & inspiration from these excellent repositories:

Repo	What it informed
TradingView/lightweight-charts	chart UX reference 鈥?we hand-rolled ours to stay single-file
ranaroussi/yfinance	Yahoo endpoint behaviour
gadicc/node-yahoo-finance2	chart-API edge cases & rate limits
twopirllc/pandas-ta	indicator definitions (EMA/RSI/ATR/VWAP/Bollinger)
backtrader/backtrader	exit-strategy concepts (scale-out, chandelier)
Zibri/cloudflare-cors-anywhere	the Worker relay pattern
public-apis/public-apis	market-data landscape survey
馃椇 Roadmap
 1% risk engine 鈥?sizer, daily dial, checklist
 Capture 鈫?Analyze 1-minute pipeline
 USD/INR conversion 路 IST market timings 路 personal plan wizard
 GitHub-Action data tier (real data on a static host)
 Price alerts with browser notifications
 Daily screener 鈥?top movers matching your signal profile
 Backtested stats per exit strategy
 Hindi UI
 PWA offline mode
馃 Contributing
Issues and PRs welcome 鈥?especially:

new symbols / relays (each is a one-line addition 鈥?see ARCHITECTURE 搂Extend)
bug reports with a screenshot showing the feed badge + timeframe
code style rule: it must stay one file, no build step, no required keys
鉂?FAQ
Does it place real orders?No 鈥?it's analysis + discipline tooling. You execute in your broker app; the User Guide's "Quick Steps" covers the exact workflow.

Is the data delayed?The badge always tells you: LIVE (real-time) 路 GH 路 DELAYED (鈮?~10 min) 路 CACHED (your last real data) 路 SIMULATED (not real 鈥?never trade on it).

Why do stocks need "Fix A/B" when crypto just works?Binance sends open CORS headers; Yahoo doesn't. Browsers physically cannot call Yahoo directly 鈥?搂4/搂5 of the Deployment guide solve it permanently.

What does it cost?Nothing. GitHub Pages, Actions, and the Cloudflare Worker free tier cover everything.

鈿狅笍 Disclaimer
ONEPERCENT is an educational tool. Nothing here is investment advice. Market data may be delayed, incomplete, or 鈥?when the badge says so 鈥?simulated. Always verify prices with your broker before acting. Trading involves substantial risk of loss; the 1% rule exists because survival is the prerequisite of every other skill in the market.

License
MIT 鈥?do whatever you like; keep the disclaimer.

If ONEPERCENT saved you from one oversized position, consider 猸?starring the repo.