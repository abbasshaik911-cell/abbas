# Abbas — Indian Trading Skill for Claude Code

One skill, three modes:

- **BUILD** — writes production-quality Python algo trading strategies for NSE/BSE/MCX
  (backtest → paper → live), Rupeezy/Vortex as default broker, with stop-losses, margin
  checks, tick rounding, IST and graceful shutdown baked in.
- **ANALYSE** — 35 guides + 22 tested calculators: technical analysis, F&O and option
  chains, exact charges/STT, Indian tax, position sizing, stops, screeners, regime,
  breadth, FII/DII flows, sector rotation, IPOs, portfolio review, backtests, discipline.
- **US DAY TRADING** — 11 tools for NYSE/NASDAQ: chart scanner, news monitor, entry timer,
  exit planner, 10,000-session time machine, risk and budget manager, paper-first
  Alpaca/IBKR order tickets, price alerts, SEC earnings analyst, Pelosi tracker.

## Install

```
claude plugin marketplace add <your-github-user>/abbas
claude plugin install abbas@abbas
```

Local: `claude --plugin-dir ./abbas`

## Test

```
python3 -m unittest discover -s tests
python3 -m unittest discover -s tests_us
```

## Credits

Built by combining [RupeezyTech/algo_ai_skill](https://github.com/RupeezyTech/algo_ai_skill)
[Shubhamkumartrichy/claude-trading-skills-india](https://github.com/Shubhamkumartrichy/claude-trading-skills-india)
and [Jakeschincariol/day-trader-skill](https://github.com/Jakeschincariol/day-trader-skill). Rupeezy's part is Apache-2.0; the other two are MIT. Files were reorganised and adapted; see LICENSE.

Not investment advice.
