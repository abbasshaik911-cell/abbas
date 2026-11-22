---
name: abbas
description: >
  Abbas: one Indian-markets trading skill (NSE, BSE, MCX) that does two jobs. (1) BUILD:
  writes production-quality Python algo trading strategies (backtest, paper, live) with
  Rupeezy/Vortex as the default broker, strict risk management and Indian market rules.
  (2) ANALYSE: stock and index analysis, F&O and option chains, exact charges/STT, Indian
  tax, position sizing, stops, screeners, market regime, breadth, FII/DII flows, sector
  rotation, IPOs, portfolio review, backtests and trading discipline, using bundled
  zero-dependency calculators.

  MANDATORY TRIGGERS: algo trading, trading bot, strategy code, backtest, Rupeezy, Vortex,
  options selling bot, intraday or positional strategy; or any question about an Indian
  stock, index (NIFTY, BANKNIFTY, SENSEX) or F&O contract: "analyze RELIANCE", "should I
  buy TCS", "my charges", "tax on F&O", "review my holdings", "position size", "expiry".
---

# Abbas — Indian Trading Skill

One skill, two modes. Decide the mode first, then follow that mode's instructions.

## Step 0: Pick the mode

| The user wants… | Mode | Start with |
|---|---|---|
| Code: a strategy, bot, backtest script, live deployment, broker automation | **BUILD** | The "BUILD mode" section below (everything after it). |
| An answer: analyse a stock/index/F&O, plan a trade, charges, tax, sizing, screens, market view, portfolio review | **ANALYSE** | `analysis/india-market-analyst/GUIDE.md` for broad questions, or the specific guide from the table below for narrow ones. |
| Both (e.g. "find a setup on NIFTY and automate it") | ANALYSE, then BUILD | Do the analysis, confirm the plan with the user, then build. |

Read a guide only when you need it — don't load all of them.

## ANALYSE mode

Every analysis guide lives at `analysis/<name>/GUIDE.md`, with its calculators in
`analysis/<name>/scripts/` and data in `analysis/<name>/references/`. When a guide says
"use the `<name>` skill", read `analysis/<name>/GUIDE.md` instead. Script paths inside a
guide are relative to that guide's folder. Run calculators with `python3`; they need no
installs. Sample input files are in the plugin's `examples/` folder.

Calculator numbers beat memory: when a script exists for the question (charges, tax,
expiry dates, sizing, Greeks), run it instead of computing in your head.

| Guide | Use for |
|---|---|
| `backtest-lab` | Backtests rule-based swing ideas on NSE/BSE daily bars with Indian frictions built in: decide on the close and fill at the next open, gap-through stops, slippage, exact per-trade charges by segment and broker (STT, stamp duty, GST, DP), whole shares or lots, circuit-band no-fills, futures-only shorts and an optional STCG/LTCG estimate. |
| `breakout-planner` | Stage-2 breakout setups on NSE/BSE stocks: a trend-template check (rising 200 DMA, 50>150>200 stack, distance from 52-week high/low, relative strength vs NIFTY), base detection (volatility contraction with successively tighter pullbacks, or a flat base) with pivot, depth, duration, volume dry-up and a grade, then an order-ready plan: trigger, chase limit, capped stop, size, Indian charges, R targets, GTT/SL templates, circuit-band and NSE tick-size checks. |
| `broker-integration` | Connect Claude to Indian brokers and use them safely: official MCP servers for Groww, Zerodha Kite, Dhan, Upstox, Fyers and Kotak Neo (endpoints, auth, read vs order capabilities as of Oct 2026), tool discovery and capability mapping, saving candles for the analysis scripts, a mandatory order-confirmation protocol, SEBI retail-algo/static-IP rules, and data fallbacks (yfinance, CSV). |
| `event-calendar` | Offline calendar of the dates that move Indian markets: NSE/BSE F&O expiries (holiday-shifted), exchange holidays, long weekends and special sessions, results-season windows (SEBI LODR), trader tax dates, India macro releases (CPI, WPI, IIP, GDP, PMI, auto sales, GST, AMFI), RBI MPC, Union Budget, US FOMC/CPI/jobs, NIFTY and MSCI rebalances, plus your own results, board-meeting, ex-date and lock-in events. |
| `exhaustion-reversal` | When a move on NSE/BSE has run out of buyers or sellers. |
| `fibonacci-trading` | Fibonacci retracement entry zones and extension targets for NSE/BSE stocks and indices, with automatic swing detection (ta.py fib), trend-based extensions from the pullback point, and confluence with moving averages, support/resistance, round numbers and option OI strikes. |
| `fii-dii-flows` | Institutional money flow in Indian equities, from CSVs you download: FII/FPI and DII cash flows (₹ crore) with 5/10/20-session and month-to-date sums, streaks, how much FII selling DIIs absorbed, largest days and NIFTY correlation; NSE participant-wise F&O open interest (FII index-futures long %, day-over-day change, index calls/puts, client positioning, extreme flags); quarterly shareholding changes with pledge red flags; bulk/block deals by symbol and client. |
| `fno-options-analysis` | Indian F&O analysis for NIFTY, BANKNIFTY, FINNIFTY, MIDCPNIFTY, SENSEX and stock derivatives: lot sizes, holiday-adjusted expiry calendar (NIFTY Tuesday weekly, SENSEX Thursday weekly), option-chain reading (OI walls, change in OI, PCR, max pain, ATM straddle, IV skew), India VIX and expected move, Black-Scholes Greeks and IV, futures OI buildup, margins, F&O ban, physical settlement and SEBI's 2024–26 rule changes. |
| `fundamental-screening` | Fundamental and governance screening of Indian listed companies in the style of Screener.in: valuation (P/E, P/B, EV/EBITDA, PEG vs history and peers), quality (ROCE, ROE, cash conversion, debt), growth, sector-specific metrics (banks, NBFCs, IT, FMCG, manufacturing), shareholding pattern (promoter, FII, DII, pledge), quarterly results reading, and India-specific red flags (promoter pledging, related-party transactions, auditor exits, surveillance lists, SME and operator stocks). |
| `india-market-analyst` | Master workflow for analysing Indian stocks, indices and derivatives on NSE/BSE. |
| `indian-market-structure` | Reference for how Indian stock markets work: NSE/BSE sessions and timings (pre-open, closing VWAP, post-close, block windows, Muhurat), T+1 settlement, optional T+0, product types (CNC, MIS, NRML, MTF), order types (limit, SL, SL-M, GTT, AMO), circuit limits and market-wide circuit breakers, surveillance frameworks (ASM, GSM, ESM, trade-for-trade), F&O ban and MWPL, margins and the 50% cash rule, DDPI/eDIS, corporate actions, and the 2026 trading-holiday calendar. |
| `indian-tax-for-traders` | Income-tax treatment of Indian stock-market income for resident individuals: STCG (20%) and LTCG (12.5% above ₹1.25 lakh) on listed equity and equity funds, grandfathering for pre-2018 shares, intraday as speculative business income, F&O as non-speculative business income, set-off and carry-forward rules, F&O turnover and tax audit, ITR form choice, dividends, buybacks, the new Income-tax Act 2025 section numbers, and tax-loss / LTCG-exemption harvesting. |
| `ipo-analysis` | Evaluate Indian IPOs (mainboard and SME): reading the RHP, price band and lot size, issue structure (fresh issue vs OFS), category quotas (QIB, NII sHNI/bHNI, retail, employee, shareholder), anchor book, subscription data interpretation, allotment odds, grey market premium caveats, valuation vs listed peers, T+3 timeline, UPI mandate, listing-day pre-open and post-listing lock-in expiries. |
| `macro-regime` | Structural (6–24 month) macro regime for Indian equities from monthly cross-asset lines: equal weight or smallcap vs NIFTY (broadening), size, NIFTY Bank leadership, cyclicals vs defensives, NIFTY vs gold in rupees, India 10-year G-sec and the yield curve (10y minus T-bill or repo), USD/INR, Brent, the US 10-year and India VIX. |
| `market-breadth` | Market-wide breadth for Indian equities: how many NSE/BSE stocks are actually joining the index's move. |
| `market-pulse` | Daily Indian market brief and regime check: pre-market (GIFT Nifty, global cues, crude, USD/INR, US yields), previous session's FII/DII cash flows and F&O participant positioning, India VIX, NIFTY/BANKNIFTY levels, sector rotation via NSE sectoral indices, breadth, F&O ban list, results and macro calendar (RBI MPC, CPI, Budget, US Fed), and post-market wrap. |
| `market-regime` | Reads the market regime of NIFTY, BANKNIFTY, SENSEX (or any index/ETF CSV) from the index's own tape: distribution-day clusters with 25-session/5%-rally expiry, the correction → rally attempt → follow-through cycle, 50/200 DMA and 52-week drawdown context, and optional India VIX. |
| `market-valuation` | How expensive and how frothy the Indian market is, from files you download and numbers you look up: NIFTY (or any NSE index) P/E, P/B and dividend-yield percentiles over 5/10/all years with a cheap/fair/expensive/extreme band, handling NSE's 2021 switch to consolidated P/E; earnings yield vs the 10-year G-sec; market cap to GDP with India reference levels; and a 0–100 froth score from valuation, India VIX, breadth, IPO and SME-IPO heat, SIP and demat growth, F&O activity and MTF leverage, mapped to a phase and a risk posture. |
| `momentum-scanner` | Short-term momentum on NSE/BSE stocks across a whole universe: momentum-burst days (a 4%+ up-close out of a quiet base on rising volume, near the high, above a rising 50 DMA, not already extended), episodic pivots (a 5%+ opening gap on 3x+ volume that holds the gap-day low, with a day-1/day-2 read and a catalyst checklist), and a 1-99 relative-strength rating with the RS line vs NIFTY. |
| `multi-timeframe-analysis` | Three-screen multi-timeframe analysis for NSE/BSE stocks and indices: weekly (or monthly) sets the bias, daily finds the setup, and 75-minute / 15-minute bars time the entry, with a 6-factor confluence score that sets position size. |
| `options-strategies` | Choosing, sizing and managing option strategies on NIFTY, BANKNIFTY, SENSEX and stock options in India: a view × volatility selection matrix, defined-risk structures (spreads, iron condors, butterflies, calendars), covered calls and protective puts, expiry-day (Tuesday/Thursday) behaviour, adjustments, margin benefits of hedging, and event playbooks (Budget, RBI, results). |
| `pair-trading` | Statistical pair trading (market-neutral long/short) for NSE stocks. |
| `portfolio-review` | Health check for an Indian delivery (CNC) stock portfolio from a holdings CSV or a Zerodha Console, Kite, Groww or broker-MCP export: value and unrealised P&L, position and sector weights, top-5/top-10 concentration, business-group exposure (Adani, Tata...), large/mid/small mix against a target, pledged, SME and surveillance flags, a per-lot STCG→LTCG countdown, volatility, beta vs NIFTY, drawdown, correlated clusters, portfolio heat to stops, and a tax-aware rebalance plan with charges. |
| `position-sizing` | Position sizing for Indian equity and F&O trades: fixed-fractional risk sizing with round-trip costs included, ATR-based stops, F&O lot rounding and margin checks, MTF/intraday leverage adjustment, gap-through-stop and circuit risk, Kelly from a trade journal, and portfolio limits. |
| `results-season` | Reads the price reaction to quarterly results on NSE/BSE stocks. |
| `risk-reward-ratio` | Risk-reward evaluation for Indian trades after real costs: R multiples per target, weighted R for scale-outs, breakeven win rate, expectancy, trade-filter thresholds, and option-specific R:R (theta, IV, premium). |
| `rsi-divergence` | Detect and trade RSI(14) divergences on NSE/BSE stocks and indices: regular divergence (reversal warning) and hidden divergence (trend continuation), with strength grading, confirmation rules, entries, stops and Fibonacci targets. |
| `sector-rotation` | Sector rotation across NSE sectoral and thematic indices (BANK, IT, AUTO, PHARMA, FMCG, METAL, REALTY, ENERGY, PSU BANK, FIN SERVICE, INFRA, PSE, CONSUMPTION and more) against NIFTY 50: 1W–12M returns, relative strength, an RRG-style RS-Ratio/RS-Momentum quadrant with recent quadrant changes, distance from 50/200 DMA, cyclical-vs-defensive tilt, the midcap/smallcap size factor, and member breadth. |
| `stock-screener` | Filter and rank a universe of Indian stocks from a fundamentals CSV (a Screener.in screen or watchlist export, or your own snake_case file). |
| `stop-loss-strategies` | Initial stop-loss placement and execution for NSE/BSE stocks and F&O: structure, ATR, S/R and moving-average stops with buffers, plus Indian execution realities — SL vs SL-M vs GTT, DAY validity of stop orders, gap and circuit risk, closing-basis stops on a 30-minute VWAP close, stop-hunting around round numbers and OI strikes, and option premium vs underlying stops. |
| `technical-analysis` | Systematic chart reading for NSE/BSE stocks and indices: trend and moving-average alignment, swing structure, support/resistance clusters, unfilled gaps, volume and delivery %, an indicator dashboard (RSI, MACD, Bollinger, ADX, Stochastic), ATR stops, circuit and gap-risk checks, and probabilistic scenarios. |
| `thesis-tracker` | Keeps every Indian stock or F&O trade idea as a written, falsifiable thesis in one JSON file the trader owns, and walks it through an enforced lifecycle (idea, watching, entry-ready, active, closed, or invalidated / expired) with a dated history. |
| `trading-costs` | Exact trading charges for Indian equity and F&O trades on NSE/BSE: brokerage (Zerodha, Groww, Angel One, Upstox, Dhan or custom), STT, exchange transaction charges, SEBI fee, stamp duty, GST, DP charges and MTF interest, plus breakeven price and cost-as-%-of-profit. |
| `trading-discipline` | Rules that protect an Indian trader from themselves: an account-level circuit breaker (daily 2%, weekly 5%, monthly 10% loss limits plus losing-streak cooldowns) read from the trade journal, a pre-trade gate (stop, rupee risk, R:R, written plan, revenge window, regime, F&O ban, ASM/GSM/T2T, results, circuit lock, expiry day, MIS cut-off) that returns PASS / PASS-WITH-WARNINGS / BLOCK before any order ticket, a performance review by setup, weekday, hour, segment and mistake, a weekly digest, and an opt-in decision log. |
| `trailing-stops` | Trailing-stop plans that lock in profit on NSE/BSE positions: the R-multiple ladder (hold → breakeven at 1R → ATR trail at 2R → structure trail at 3R+), plus ATR, structure, moving-average and chandelier trails, with GTT/SL execution realities for Indian brokers. |

## Shared rules (both modes)

- When a BUILD reference and an ANALYSE guide disagree on a number (STT, lot size, expiry
  day, tax rate), prefer the one with the more recent date stated in it, and tell the user
  which rate you used. Rates change — verify anything you'll put real money behind.
- Money in rupees, not bare percentages, in anything the user reads.
- Never place a live order without the user's explicit confirmation of that exact order.
- This is education and tooling, not investment advice. Say so once when giving a trade view.

---

# BUILD mode



Write production-quality Python trading strategies for Indian markets. Every strategy must be safe enough to run with real money.

## Who You Are Talking To

The user is a **trader, not a programmer**. Assume they cannot read Python, cannot review your code for correctness, and cannot debug an error message. You are the only reviewer this code will ever have — every safeguard is your responsibility, not theirs.

- **Ask questions they can answer.** Trading vocabulary (strike, stop-loss, lot, expiry, intraday) is fine. Software vocabulary (container, env var, dependency, SDK, token, deployment) is not.
- **Never block on a question they can't answer.** Pick a safe default, state it in one line, move on.
- **Explain in plain English before and after** — confirm the strategy before coding (Step 2), explain what you built after (Strategy Output Format).
- **Walk them through anything they must do themselves.** Give one command per line and say what a good result looks like. Never say "set an environment variable" — say "open the file called `.env` and put your key after the `=`", and prefer writing the file for them.
- **Money in rupees, never bare percentages**, in anything the user reads.

## Before Writing Any Code

### Step 1: Understand the User's Intent

Ask (skip any already answered):

1. **Asset class** — equity, F&O, currency, commodities? If cash equity: are any symbols F&O-eligible? Those are CAS scrips — continuous trading ends 3:15 PM and their exit deadline differs (Rule 16).
2. **Live or backtest?**
3. **Broker** — Rupeezy/Vortex (default; see `references/brokers/rupeezy-vortex.md`) or other (check `references/brokers/`)?
4. **Where should it run?** Ask this in plain words — do **not** say "self-hosted", "container", "deployment" or "MCP" to the user:
   > "Two choices: **(a) Rupeezy runs it for you** — you install nothing and it keeps trading even when your laptop is off. **(b) You run it yourself** — it lives on your own computer or a rented server, and only trades while that machine is on and the program is running."

   If the user is unsure, says "whichever is easier", or has no server → pick **(a)**, say so in one line, and move on. Never stall here.
   Internal mapping: (a) = Rupeezy container — zero-arg `VortexAPI()`, no login files. (b) = self-hosted — MUST ship `login.py`+`auth.py` (Rule 8).
5. **Risk tolerance** — ask in rupees, not percent: "How much are you OK losing on one bad trade, and what's the most you'd accept losing in a single day before the bot stops?" If they answer in percent or don't know, ask for total capital and convert. Defaults if unknown: 1% of capital per trade / 3% per day / 10% max drawdown — and **always state them back in rupees**.

### Step 2: Discuss Strategy Design

Before any code, agree on: entry logic; exit logic (stop-loss is mandatory — and on a CAS scrip it cannot be a resting exchange-side SL after 3:15 PM, Rule 16); position sizing; scheduling (agree the intraday exit deadline explicitly — before 3:15 PM for cash CAS scrips, 3:20-3:25 for non-CAS cash and F&O); hedging (warn against naked options selling; note a cash/F&O hedge cannot be rebalanced 3:15-3:40).

Then **confirm before coding.** Write the strategy back as a numbered list of plain-English rules plus one worked example with real rupee numbers on their stated capital. Ask "Is that exactly what you want it to do?" and wait. If they correct anything, restate the whole list rather than patching it verbally.

### Step 3: Route to the Right References

Load only what's relevant. Core references — read when topic comes up:

| Need | File |
|---|---|
| New strategy | `references/strategy-patterns.md` |
| Risk / position sizing | `references/risk-management.md` |
| Backtesting | `references/backtesting.md` |
| Indian market rules (expiry, timings, closing auction/CAS, square-off, margins) | `references/indian-market.md` |
| Error handling | `references/error-handling.md` |
| Code quality / testing | `references/code-quality.md` |
| Rupeezy/Vortex SDK — auth, instruments, orders, constants | `references/brokers/rupeezy-vortex.md` |
| Vortex depth — backtest prep, lifecycle examples, error handling | `references/brokers/rupeezy-vortex-advanced.md` (only when you need it) |

**Load the minimum.** Two rules that save most of the budget:

- Load `indian-market.md` unconditionally for any strategy trading cash equity intraday — the closing-auction timings (Rule 16) are not something to infer.
- **If you scaffolded, you do NOT need `code-quality.md` for order tracking.** The scaffolder writes a working `order_tracker.py` and `market_session.py`; reading the canonical listings only duplicates what is already on disk. Open it only to debug tracker behaviour or to write tests.

Advanced (suggest proactively when context fits): `options-greeks.md`, `regime-detection.md`, `india-data-edge.md`, `execution-alpha.md`, `robustness-testing.md`, `portfolio-construction.md`, `psychological-guardrails.md`, `tax-optimization.md`, `python-performance.md`. Don't wait for the user to ask — for MA crossover suggest regime detection; for 40% CAGR backtest demand robustness testing.


## Code Architecture Rules

Every strategy MUST follow this structure. No exceptions.

### Separation of Concerns

```
main.py          → entry point, initialization, scheduling
strategy.py      → signal generation ONLY (no order placement)
execution.py     → order placement, fill tracking (no signal logic)
risk_manager.py  → position sizing, exposure checks, drawdown limits
guardrails.py    → daily loss limits, cooldowns
config.py        → all configurable parameters
```

**Self-hosted only**, add `login.py` (loopback OAuth server) + `auth.py` (`get_client()` helper). Container packages must not include these. See Rule 8.

Signal generation and execution are always in separate modules so signals can be tested independently and execution can be swapped between backtest and live without touching signal code.

### Configuration Externalized

Every tunable parameter lives in `config.py` or env vars: symbols, quantities, thresholds, indicator periods, risk caps, schedules. Broker credentials always env-var, never in code.

### Risk Manager as Gatekeeper

Every order goes through `risk_manager.approve(signal)` before submission. The manager checks position size, daily loss, drawdown, margin, and concentration. Full implementation in `references/risk-management.md`.

```python
def place_order(signal):
    if not risk_manager.approve(signal):
        logger.warning(f"Risk manager rejected: {signal.reason}")
        return None
    return execution.submit_order(signal)
```

### Structured Logging

Use `logging`, not `print()`. Log every decision with timestamp, symbol, action, reason, price, qty, current P&L.

### Graceful Shutdown

Handle SIGTERM/SIGINT: cancel pending orders, optionally square off, log final state. Critical for container deployments where the platform can stop the strategy any time.

The square-off path must be session-aware: for cash equity in a CAS scrip after 3:15 PM there is no continuous book and a market order will fail (and is rejected outright after 3:25). Either route a LIMIT order into the auction inside the ±3% band, or log loudly that the position is carrying to settlement. Never let the handler report success on an unfilled square-off.


## Critical Rules — Violations Cause Real Money Loss

These are non-negotiable. Every strategy must follow them.

> **⚠ Silent-until-live failure modes: Rules 1, 11, 12, 13, 15, 16.** These pass `py_compile`, `pytest`, and often a WebSocket smoke test — they blow up only on the first real broker interaction, on a later trading day when something rolls, or at 3:15 PM when the closing auction starts (Rule 16). Walk these six explicitly whenever you scaffold or modify a strategy. Each rule's body names the specific failure.

### 1. NEVER hardcode instrument tokens

Tokens change daily. Pass `ticker="<EXCHANGE>:<SYMBOL>"` to every Vortex API (`place_order`, `historical_candles`, `get_order_margin`, `client.quotes`, `wire.subscribe`) on `vortex-api >= 2.1.8`. Never build a ticker from `exchange:symbol` (breaks on F&O) — read `inst.ticker` from the master. Feed ticks are tagged with `tick.get("ticker")` (best-effort enrichment; `exchange`/`token` always present).

```python
client.place_order(ticker="NSE:RELIANCE", ...)              # RIGHT
inst = client.instruments.get_by_ticker("NSE:RELIANCE")     # for lot_size, tick, isin
```

Ticker shapes: equities `"NSE:RELIANCE"`; indices append `IDX` (`"NSE:NIFTYIDX"`) but the F&O `symbol` field stays bare (so option-chain filter is `symbol == "NIFTY"`); F&O contracts each have their own ticker — use `client.instruments.all_by_underlying("NSE_FO", "NIFTY")` to enumerate. For other brokers, use whatever symbolic identifier they expose — never raw numeric tokens.

### 2. NEVER hardcode lot sizes

Lot sizes change with corporate actions and SEBI directives. Read them off the instrument object: `client.instruments.get_by_ticker("NSE:NIFTYIDX").lot_size`. For other brokers, look them up from the instrument master.

### 3. ALWAYS use stop-losses

Every strategy ships with one. If the user explicitly refuses, warn and add a wide-buffer stop anyway; document the risk.

**CAS caveat:** on a CAS scrip the exchange cancels untriggered stop-loss and disclosed-quantity orders at 3:15 PM (Rule 16). A resting broker-side SL is not protection through the close — and on Rupeezy a **GTT is not a substitute, it stops triggering at 3:15 PM too**. Nothing broker-side protects a cash position through the auction. Either flatten before 3:15 PM, or hold the stop **in-process** and, if it fires after 3:15, send a LIMIT order into the auction inside the ±3% band.

### 4. ALWAYS check margin before placing orders

Call `get_order_margin()` first. If insufficient, log and skip — don't crash.

### 5. ALWAYS handle order rejections

Every `place_order` wrapped in try/except. Rejections happen routinely (margin, price-out-of-range, exchange down).

### 6. NEVER ignore partial fills

A "buy 100" can fill 60 now + 40 later, or 60 then cancel. Track fill state precisely.

### 7. ALWAYS set IST timezone explicitly

**The strategy container runs in UTC.** `datetime.now()` / `utcnow()` and other naive clocks return UTC, not IST — so without an explicit timezone every market-hours and scheduling check is off by 5h30m. Make every time value timezone-aware in IST.

```python
import pytz
from datetime import datetime
IST = pytz.timezone("Asia/Kolkata")
now = datetime.now(IST)   # timezone-aware IST — NOT datetime.now() / utcnow()
```

Never rely on the system timezone (it is UTC) or on naive datetimes.

### 8. Self-hosted strategies MUST ship `login.py` + `auth.py`

For self-hosted (anywhere the user runs `python main.py` themselves, including headless boxes), generate `login.py` and `auth.py`. No exceptions. Never generate `input("auth code: ")`, `VORTEX_ACCESS_TOKEN` in `.env`, or a `broker.py` that exposes a manual auth_code. Run `scripts/scaffold_strategy.py --deployment self-hosted` or replicate its output; the full pattern is in `references/brokers/rupeezy-vortex.md`.

Why: `auth_token` (the `?auth=...` redirect param) and `access_token` (the long-lived bearer) are different. Users confuse them. The loopback HTTP server on `127.0.0.1:8765/callback` does `client.exchange_token()` automatically so the user never sees either token.

Does **not** apply to the container platform — there `VORTEX_ACCESS_TOKEN` is injected at runtime, `main.py` uses zero-arg `VortexAPI()`, and `login.py`/`auth.py` would be dead code that breaks at runtime.

### 9. Order updates have split authority across surfaces. Never sleep-poll.

`VortexFeed.on_order_update` is the only way to learn an order changed in real time. Connect the feed *before* any `place_order` so the first push isn't lost. The callback fires for **five** envelope types — `order`, `trade`, `sl_trigger`, `gtt_order`, `position_conversion` — all signal that state changed for some `order_id`. See `references/brokers/rupeezy-vortex.md` for the payload table and per-type meaning.

**Authority is split between surfaces** because REST orderbook can lag postbacks by tens of seconds on the same order:

- **Postback `data.status`** is authoritative for **status transitions** — believe terminal postbacks immediately, don't wait for REST.
- **`client.orders()` / `client.trades()`** are authoritative for **fill quantities, traded_price, avg fill** — refresh from these on every postback (coalesced 500 ms debounce so a many-fill order doesn't trip the REST rate limit).
- **Downgrade guard**: once terminal is recorded for an order_id, a later non-terminal REST row is stale — merge fill fields but DO NOT overwrite the status.

**Do NOT poll** `client.orders()` / `client.order_history()` / `client.trades()` on a sleep-loop. Refresh-on-postback is event-driven — REST is called *only* when a postback indicates a change.

**Order outcomes are events, not return values.** Live strategies wire `tracker.on_terminal = strategy.on_order_terminal` to receive `(order_id, status)` callbacks for every terminal transition. **Do NOT call `tracker.wait()` inside the strategy main loop** — `wait()` is the script / test / `cancel_and_wait()` primitive only; its `timeout` is required (pass `float("inf")` for forever). Call `tracker.initialize()` once at startup before placing orders so historical fills don't fire spurious callbacks.

Terminal-status detection is **substring-based** to catch broker-decorated forms (`REJECTED_BY_RMS`, `AMO_CANCELLED`); canonical tokens are `COMPLETED` / `EXECUTED` (same state — postback uses COMPLETED, orderbook uses EXECUTED), `REJECTED`, `CANCELLED`. Rejection-reason field name varies by surface (`status_message` / `error_reason` / `message`) — use `tracker.rejection_reason(order_id)`.

The reference `OrderTracker` in `references/code-quality.md` (and the scaffolded `order_tracker.py`) implements all of this — wire it, don't re-implement.

**CAS mass-cancel:** at 3:15 PM the exchange cancels every untriggered SL and disclosed-quantity order on CAS scrips, one message per order, producing a burst of exchange-initiated `CANCELLED` postbacks. `on_order_terminal` must not read these as the user withdrawing protection, and must never infer a position was closed from an SL cancellation.

### 10. NEVER short sell illiquid equities intraday

**Settlement-auction** risk (a different mechanism from the Closing Auction Session in Rule 16): stock hits upper circuit → you can't exit → 20%+ penalty above your sell price. Check volume + circuit band before shorting; prefer F&O for shorts. A cash short in a CAS scrip must additionally be flat before 3:15 PM — after that there is no continuous book and the resting stop-loss has been cancelled. Details in `references/indian-market.md`.

### 11. ALWAYS respect tick sizes

Round prices to the instrument's `tick` (from `client.instruments.get_by_ticker(...).tick`). Mis-tick prices get rejected.

```python
def round_to_tick(price, tick): return round(round(price / tick) * tick, 2)
```

### 12. ALWAYS respect Daily Price Range (DPR)

Exchanges set a daily circuit-limit band per instrument. Orders outside it are rejected by the broker's OMS before reaching the exchange — common cause of failed deep stop-losses and ambitious targets. Read DPR from the broker's quote/market data and clamp `price` / `trigger_price` accordingly.

On a CAS scrip during the closing auction a second, tighter band applies: ±3% of the auction reference price (VWAP of 3:00-3:15 PM). Clamp to `min(DPR, CAS band)` for any auction-routed order, and compute the reference price yourself from 3:00 PM ticks if the broker doesn't publish it. See Rule 16 and `references/indian-market.md` §1A/§11.

### 13. Account for calendar spread margin removal on expiry day

On expiry day, calendar-spread margin benefits are removed and required margin can jump 5-10x (₹26K → ₹2.6L per lot). Check if any spread leg expires today and pre-flight margin. See `references/risk-management.md`.

### 14. NSE has no public data API

All market data (quotes, historical candles, OI, FII/DII, depth) must come through the broker API or third-party providers. Never write code that scrapes or calls NSE endpoints directly.

### 15. Pass SDK enum instances, not their string values

The Vortex SDK runtime-typechecks every `transaction_type`, `product`, `variety`, `validity`, `mode`, `exchange`, `resolution` argument via `isinstance(value, EnumClass)`. Passing the string value (`"INTRADAY"`) where the SDK expects the enum (`Vc.ProductTypes.INTRADAY`) raises `TypeError: product must be of type ProductTypes` **even though the enum's `.value` IS "INTRADAY"** — the check is class-based, not value-based. Silent until the first live `place_order` / `get_order_margin`; `py_compile` and unit tests don't catch it.

```python
from vortex_api import Constants as Vc

# WRONG — string passes type-hint, fails at runtime on first live call
client.place_order(product="INTRADAY", ...)

# RIGHT — enum instance
client.place_order(product=Vc.ProductTypes.INTRADAY, ...)
```

If you store these in `config.py`, store the enum directly (the scaffolded `config.py` does). Name ≠ value for many `Vc.*` enums (`Vc.VarietyTypes.REGULAR_LIMIT_ORDER.value == "RL"`, `Vc.ExchangeTypes.NSE_EQUITY.value == "NSE_EQ"`), so a stringly-typed config with `getattr(Vc.X, name)` lookup also works but only if you store the **member name**, not the value.

### 16. Cash-equity intraday exits must clear the Closing Auction Session

Since 3 Aug 2026 the cash segment has **three different closes**, so no single market-close constant is correct. **Never hardcode a session time — import `market_session.py`** (the scaffolder generates it; it encodes every boundary below):

```python
import market_session as session

self.segment = session.segment_for(client, "RELIANCE")   # resolve ONCE at startup
if session.should_exit_now(self.segment)[0]:             # not `if now > time(15,25)`
    self.square_off()
```

| Segment | Continuous ends | Then |
|---|---|---|
| Cash **with** F&O contracts (CAS scrip) | **3:15 PM** | Call auction sets the close; random end 3:28-3:30 |
| Cash without F&O contracts | 3:30 PM | Unchanged |
| Equity derivatives | **3:40 PM** | Extended by the CAS framework |

What this breaks in code — the parts no import can fix:

- **Untriggered stop-loss and disclosed-quantity orders are cancelled by the exchange at 3:15 PM**, and on Rupeezy GTTs stop triggering then too. **Nothing broker-side protects a cash position through the auction** (Rule 3). Be flat before 3:15, or send a deliberate auction limit order.
- **Price band** in the auction is ±3% of the 3:00-3:15 VWAP reference price — usually tighter than DPR, so clamp to the narrower (Rule 12). Limit orders only after 3:25; Rupeezy rejects rather than buffers orders during 3:15-3:20.
- **"The close" changed meaning** — it is the auction equilibrium price, and it differs between NSE and BSE for the same stock.
- **No candles exist for a CAS scrip between 3:15 and 3:30 PM** — not empty bars, none at all. `df.iloc[-1]` at 3:22 returns the 3:14 bar, so "current price" is silently stale, and "wait for the next bar" loops never fire. Drive closing-window logic off the clock, never off bar arrival.
- **Resolve the segment at runtime**, never from a hardcoded symbol list — the F&O universe moves with SEBI reviews.

The **pre-open realigns to the same shape on 7 Sep 2026** (random close 9:08-9:10); `session.pre_open_schedule()` branches on the date for you.

Full timeline, order-type table, carry-forward and broker-layer rules: `references/indian-market.md` §1A and §1B.


## Backtesting Standards

Every backtest must include realistic friction. Zero-cost backtests produce fantasy returns.

- **Costs**: STT (eq 0.1%, fut 0.05%, opt 0.1%) + brokerage + exchange. `commission=0.001` minimum in backtesting.py (raise for options). Rates in `references/indian-market.md`.
- **Slippage**: ≥0.05% liquid, 0.1-0.2% illiquid; double near F&O expiry.
- **CAS structural break (3 Aug 2026)**: for CAS scrips the daily close switched from a last-30-minutes VWAP to the auction equilibrium price. Any series spanning that date has a regime break in its Close column — flag it, don't fit close-anchored signals across it, and rebuild intraday volume profiles from post-CAS data only.
- **Intraday exit fills**: model the last continuous fill at 3:15 PM for CAS scrips, not 3:25/3:29. A backtest that exits "at the close" is assuming an auction fill at the equilibrium price — state and stress that assumption.

If CAGR > 30%, flag and require robustness testing (walk-forward, Monte Carlo, OOS). If parameters are tunable, run grid optimization with heatmap. See `references/robustness-testing.md`.


## Strategy Output Format

**Both modes:** `main.py`, `strategy.py`, `risk_manager.py`, `config.py`, `market_session.py`, `requirements.txt`, `README.md`.

**Scaffold, don't handwrite.** Run `scripts/scaffold_strategy.py` and edit the generated `strategy.py` — the output already satisfies Rules 1, 2, 7, 8, 11, 15 and 16 by construction, and its writes are ASCII-guarded for the container. Handwriting six files from scratch reintroduces every one of those as a memory test.

**Self-hosted only, additionally:** `login.py`, `auth.py`, `.env.example` (with `VORTEX_API_KEY` + `VORTEX_APPLICATION_ID` only — never `VORTEX_ACCESS_TOKEN`). `requirements.txt` includes `python-dotenv`.

**Container only:** `requirements.txt` does NOT include `python-dotenv`; no `.env.example` for credentials (platform injects them).

Backtest-only strategies can be a single file as long as risk management, realistic costs, and parameters are present. If a backtest touches `VortexAPI`, the self-hosted layout applies.

### Mandatory gate before handover

The user cannot review this code — you are the only reviewer. Before handing anything over:

```bash
python scripts/validate_strategy.py <strategy_dir>/
```

Run it on the **whole directory**. Interpret the output yourself; never paste it at the user. Exit 2 (hardcoded token/lot size, NSE scraping) is blocking — fix and re-run. Exit 1 warnings are per-file substring heuristics, so a warning on `strategy.py` (no order code) or `config.py` (no timezone) is expected — confirm each is a false positive against the actual file before dismissing it. The validator does **not** cover the silent-until-live rules (1, 11, 12, 13, 15, 16); hand-check those yourself.

If the script isn't reachable from the install, replicate its checks by hand rather than skipping the gate.

### Explaining the result

The README is the only artifact this user can read. After generating any strategy:

1. **Restate what it does** in 5-8 numbered plain-English lines — no code, no library names.
2. **State the money numbers**: risk per trade, daily stop, and worst observed drawdown, in rupees on their actual capital.
3. **Say what it will not do** — the failure modes it doesn't handle, and what happens if the machine or container stops.
4. **Give the exact run and stop instructions**, one command per line, with expected output.

If CAGR > 30%, say so plainly and unprompted before the user gets excited: numbers that good usually mean the settings were fitted to past data. Then run robustness testing and report the outcome in the same plain terms — read the heatmap yourself rather than handing it over.


## Proactive Suggestions

After generating a strategy, offer the relevant ones:

- **Regime detection** when the strategy assumes a single regime (trending OR sideways).
- **Robustness testing** (walk-forward, Monte Carlo) when going live or when CAGR > 30%.
- **Psychological guardrails** (daily loss caps, consecutive-loss pause) on any live strategy.
- **Tax optimization** when holding-period tweaks could move trades from STCG (20%) to LTCG (12.5%).
- **VWAP execution** for orders > 5% of ADV. On CAS scrips the schedule must end by 3:15 PM — compress the profile into 9:15-3:15 and route any residual as one deliberate auction limit order. Pre-Aug-2026 volume profiles overweight the final 30 minutes with liquidity that has moved into the auction.
- **Vectorization** when you see Python loops over price data.
