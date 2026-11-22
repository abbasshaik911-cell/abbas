# Abbas — Indian Trading Skill for Claude Code

One skill, two modes:

- **BUILD** — writes production-quality Python algo trading strategies for NSE/BSE/MCX
  (backtest → paper → live), Rupeezy/Vortex as default broker, with stop-losses, margin
  checks, tick rounding, IST and graceful shutdown baked in.
- **ANALYSE** — 35 guides + 22 tested calculators: technical analysis, F&O and option
  chains, exact charges/STT, Indian tax, position sizing, stops, screeners, regime,
  breadth, FII/DII flows, sector rotation, IPOs, portfolio review, backtests, discipline.

## Install

```
claude plugin marketplace add <your-github-user>/abbas
claude plugin install abbas@abbas
```

Local: `claude --plugin-dir ./abbas`

## Test

```
python3 -m unittest discover -s tests
```

## Credits

Built by combining [RupeezyTech/algo_ai_skill](https://github.com/RupeezyTech/algo_ai_skill)
and [Shubhamkumartrichy/claude-trading-skills-india](https://github.com/Shubhamkumartrichy/claude-trading-skills-india),
both MIT. See LICENSE.

Not investment advice.
