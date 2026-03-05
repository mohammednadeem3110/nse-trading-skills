# NSE Trading Skills for Claude Code

A collection of 9 trading analysis skills for Indian NSE/BSE equity markets, designed to work with [Groww MCP](https://mcp.groww.in) and yfinance.

## Skills

| Skill | Description |
|-------|-------------|
| **nse-trading-toolkit** | Master orchestrator — routes full analysis through all frameworks |
| **technical-analysis** | Chart reading, trend ID, S/R, volume, indicator dashboard, scenarios |
| **position-sizing** | Fixed fractional, ATR-based, Kelly criterion, leverage adjustments |
| **stop-loss-strategies** | Structure, ATR, S/R, MA-based stops with buffer rules |
| **trailing-stops** | ATR trail, structure trail, MA trail, chandelier exit, hybrid approach |
| **risk-reward-ratio** | R:R calculation, min R:R tables, trade filtering, expected value |
| **multi-timeframe-analysis** | 3-screen method (weekly/daily/hourly), confluence scoring |
| **rsi-divergence** | Regular + hidden divergence, confirmation rules, entry strategy |
| **fibonacci-trading** | Retracement entries, extension targets, confluence zones |

## Installation

### Option 1: Symlink to your project
```bash
# Clone this repo
git clone https://github.com/Bhala-Srinivash/nse-trading-skills.git

# Symlink skills to your project's .claude/skills/
mkdir -p your-project/.claude/skills
for skill in nse-trading-skills/*/; do
  name=$(basename "$skill")
  [ "$name" = "evals" ] && continue
  ln -s "$(pwd)/$skill" "your-project/.claude/skills/$name"
done
```

### Option 2: Copy individual skills
Copy any SKILL.md into your `.claude/skills/<skill-name>/SKILL.md`.

## Data Sources

These skills are designed to work with:
- **Groww MCP** — Live quotes, portfolio, technical indicators, historical candles, order placement
- **yfinance** — Historical OHLCV data for backtesting and long-term analysis
- **TradingView MCP** — Crypto screening (not used for equities)

## Usage

Once installed, just ask Claude naturally:
- "Analyze BBTC" → triggers orchestrator + relevant frameworks
- "Position size for RELIANCE with Rs.5L account" → triggers position-sizing
- "RSI divergence on TATAMOTORS?" → triggers rsi-divergence
- "Fib levels for INFY" → triggers fibonacci-trading
- "Where to set stop-loss on my HDFCBANK trade?" → triggers stop-loss-strategies

## Market Focus

These skills are adapted for **Indian NSE/BSE equities** with:
- INR pricing (Rs.)
- NSE/BSE trading hours (9:15 AM - 3:30 PM IST)
- T+1 settlement
- Circuit limit awareness
- STT/brokerage/GST cost considerations
