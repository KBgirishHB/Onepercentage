# 📘 ONEPERCENT — User Guide

*Beginner-friendly, expert-capable. All timings in IST (UTC+5:30) beside real market time.*

---

## 1 · Your first 10 minutes

1. **Pick your currency** — `USD $ / INR ₹` in the header. If you think in rupees, toggle **INR first**, then set your account size (the whole terminal follows: chart axis, sizer, risk budget).
2. **Set your account** — Trade Desk → *Account size*. The amber number is your **daily risk budget: exactly 1%**.
3. **Open the MY PLAN tab** — answer the 4 questions (goal, daily time, capital, experience). You get personal timeframes, risk %, login windows and this week’s mission.
4. **Search your first stock** — press `/`, type a name (“reliance”, “nvda”, “btc”). Every symbol opens at **1D · 5m**.
5. **Run your first analysis** — **AUTO PLAN** → **CAPTURE → ANALYZE (1m)**.

> ### 🟡 THE GOLDEN RULE
> If the sizer says **quantity 0**, your stop is too wide for a 1% loss. Never widen the risk — find a closer stop, or skip the trade. **Skipping is a position too.**

---

## 2 · The Trade Desk & the 1% rule

| Element | What it does |
|---|---|
| **Risk dial** | How much of today’s 1% budget is consumed. At 100% the ceiling is hard — no more risk today. |
| **Risk per trade** | Capped at 1.00%. Choose 0.25–0.75% while learning (recommended). |
| **Position sizer** | Exact quantity so a stop-hit loses at most your risk. Also caps allocation (default 25%) and shows breakeven incl. fees. |
| **R-table** | 1R / 2R / 3R prices with profit. A 2R target means you can be wrong more often than right and still grow. |
| **Signals** | Trend (EMA structure) · RSI · ATR volatility · Volume — with a plain-English sentence. **MIXED trend = smaller size or no trade.** |

**Worked example (INR):** Account ₹8,00,000 → budget ₹8,000 → stop ₹20 away → **400 shares** → stopped out = exactly ₹8,000 lost = 1%.

---

## 3 · Chart, search & indicators

- **Timeframes:** 1D / 5D / 1M / 3M / 6M / 1Y / 5Y · inside 1D pick **1m / 5m / 15m**
- **Interactions:** scroll = zoom · drag = pan · double-click = reset · hover = crosshair with full OHLCV
- **Plan lines:** typing entry/stop/target draws dashed amber/red/green lines on the chart
- **Search:** US stocks, ETFs, indices (`^GSPC`), Indian stocks (`TCS.NS`), crypto
- **Tape:** SPY · QQQ · IWM · VIX · GLD · NIFTY · BTC · ETH — click any to open it

---

## 4 · Capture → Analyze (the 1-minute pipeline)

1. Click **CAPTURE → ANALYZE** (or press `C`)
2. If you’re not on 1m, the app **switches to the 1-minute chart first**
3. A **fresh plan is computed from those 1m candles** — entry = live price, stop = 10-bar swing low − 0.25×ATR, target = 2R. Never stale, never arbitrary.
4. The snapshot (with header stamp + watermark) opens in the analyzer with all three levels **pre-marked at exact heights** — prices, verdict and Trade Desk are already synced
5. **Drag any line** to test alternatives — the price tag, R:R verdict, quantity and live-chart lines all update together

---

## 5 · Screenshot Analyzer (external images)

1. Drag any broker screenshot in — or paste with `Ctrl+V`
2. **To auto-read prices:** open *CALIBRATE*, type the highest & lowest visible axis prices, then drag the two blue **H / L** tags onto those gridlines
3. Without calibration, just type the three prices
4. Verdict: 🟢 **TAKE** (≥2R) · 🟡 **MARGINAL** (1–2R) · 🔴 **REJECT** (<1R)
5. Accepted? **LOAD INTO TRADE DESK** — or it’s already there if calibrated

---

## 6 · Exit / Withdraw Planner — the “short period” answer

| Strategy | How it exits | Best when |
|---|---|---|
| **Sniper** | All out at the target | One clean level, high conviction |
| **Scale-out** ⭐ | 50% at 1R · 30% at 2R · 20% trails EMA20 | Default choice — banks early, keeps upside |
| **Time-stop** | Flat after N bars, no exceptions | Strict short-period mandate |
| **ATR trail** | Stop rides 3×ATR under the highest high | Strong trends |

Duration is estimated from live ATR: *“distance to target ≈ 3.4× ATR ≈ 2 trading sessions.”*

---

## 7 · Trade Journal

Closed armed trades log automatically (or add manually). Stats: **trades, win rate, expectancy (average R — the most important number), best trade**, plus an equity curve in R. Everything stays in your browser.

---

## 8 · MY PLAN — when to trade (all times IST)

### 🇺🇸 US stocks — session ≈ 19:00–01:30 IST (summer) · 19:30–02:30 (winter)

| IST | US ET | Phase | What to do |
|---|---|---|---|
| 17:30–19:00 | 08:00–09:30 | 🧭 **PREP** | Market closed — analyze, build plans, review journal |
| 19:00–19:30 | 09:30–10:00 | 🔴 **AVOID** | Opening chaos — spreads wide, fake moves. Watch only |
| **19:30–21:30** | **10:00–12:00** | 🟢 **PRIME** | **Best beginner window — trends are established** |
| 21:30–23:30 | 12:00–14:00 | 🟡 GOOD | Manage positions, scale-outs |
| 23:30–00:30 | 14:00–15:00 | ⚪ SLOW | Volume fades |
| 00:30–01:30 | 15:00–16:00 | 🔴 **EXPERTS** | Power hour — fastest moves, experience only |

### 🇮🇳 Indian stocks (NSE) — 09:15–15:30 IST

| IST | Phase | Note |
|---|---|---|
| 09:15–09:45 | 🔴 AVOID | Opening auction noise |
| 09:45–10:15 | ⚪ WARM | Let the opening range form |
| **10:15–13:00** | 🟢 **PRIME** | Best window |
| 13:00–14:45 | 🟡 GOOD | Manage & scale out |
| 14:45–15:15 | 🔴 EXPERTS | Power hour |
| 15:15–15:30 | 🔴 AVOID | Closing scramble |

### ₿ Crypto — 24×7
Never closes; liquidity peaks **19:30–21:30 IST** (US-morning overlap).

The **wizard** in MY PLAN personalises all of this — e.g. *“Same-day trades + 1–2h/day + beginner”* → 15m trend gate · 5m setup · capture on 1m · **0.25% max risk** · in the seat 19:30–21:30 IST · flat by 23:30.

---

## 9 · Quick steps — zero to first disciplined trade

1. **Install a broker app & finish KYC.** 🇮🇳 Zerodha Kite · Groww · Upstox · Angel One · 🇺🇸 Robinhood · Webull · IBKR · crypto: any regulated exchange. Use paper/virtual mode first if available.
2. **Research HERE, not in the app.** `/` → search → check Signals → **AUTO PLAN** → **CAPTURE → ANALYZE**. Only a **TAKE** verdict proceeds.
3. **Execute in the broker app.** LIMIT buy at the entry · stop-loss order at the stop · quantity exactly as the sizer says. Use **bracket/cover orders** if offered — they bind stop + target.
4. **Set two alerts** in the broker app (stop & target). Keep Armed Trades open here for live R.
5. **Journal the same night** — one honest sentence. Weekly: review expectancy. **Three straight losses → drop to 0.25% risk until green again.**

---

## 10 · Indicator cheat sheet

| Indicator | Beginner rule | Intermediate edge |
|---|---|---|
| **EMA20 / EMA50** | Price above both = uptrend → only look for BUYs | Buy pullbacks touching EMA20 on 15m; stop just under |
| **VWAP** | Above VWAP = buyers in control | Longs near VWAP in uptrends; avoid entries >2% stretched |
| **Bollinger** | Squeeze = big move coming; wait for the break | Fade outer bands only in ranges — never against trend |
| **Volume** | Real moves need fuel: >1.5× average | Volume climaxes often *end* moves, not start them |
| **RSI** | >70 hot · <30 washed out | In strong trends RSI stays >70 — never short on RSI alone |
| **ATR** | Sets stop distance: 1–1.5×ATR | ATR% > 4 (HOT) → cut position size in half |

---

## 11 · Currency, badges & shortcuts

**Currency:** the USD/INR toggle converts everything at the live rate (hover to see it; 24h cache, offline fallback). `.NS` symbols convert correctly both ways. Armed trades convert; the journal keeps history as-entered.

**Feed badges:**

| Badge | Meaning | Action |
|---|---|---|
| `● LIVE` | Real-time market data | None |
| `● GH · DELAYED` | Real data from your repo’s Action (≤ ~10 min) | Fine for practice/planning; add the Worker for real-time |
| `● CACHED` | Your last real data; retrying | Wait |
| `● SIMULATED` | Nothing real reachable | See [DEPLOYMENT §4](DEPLOYMENT.md) — never trade real money on SIM |

**Shortcuts:** `/` search · `1–7` timeframes · `C` capture · `?` guide · `Ctrl+V` paste screenshot · `Esc` close · double-click reset zoom.

---

## 12 · Troubleshooting & glossary

- **Stuck on SIMULATED?** → DEPLOYMENT §4 (10 minutes, permanent fix).
- **Capture did nothing?** → it needs loaded candles.
- **Popup (guide) blocked?** → allow popups for this site.
- **Crypto works, stocks don’t?** → normal without Fix A/B — see DEPLOYMENT.

| Term | Meaning |
|---|---|
| **R** | One unit of risk = what you lose at your stop. +2R = made twice what you risked |
| **ATR** | Average movement per bar — drives stop width & duration estimates |
| **EMA20/50** | Trend averages; price above both = uptrend structure |
| **VWAP** | Volume-weighted intraday fair value |
| **R:R** | Reward ÷ risk. This tool rejects below 2:1 |
| **Expectancy** | Average R per trade. Positive expectancy + 1% rule = survival first, growth second |

---

*ONEPERCENT is an educational tool. Nothing here is investment advice. Verify prices with your broker before acting.*
