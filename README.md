# 📈 Strategies

Strategies is trading strategy written in Pine Script for TradingView. It provides visual signals and backtesting capability using the built-in strategy tester.  
This script is ideal for traders looking to [benefit type, e.g., catch early trends, avoid false breakouts, automate risk management].

## ⚙️ Features

- ✅ Entry based on [e.g., EMA crossover / RSI conditions]
- ✅ Optional stop-loss and take-profit levels
- ✅ Toggleable long and/or short positions
- ✅ Realtime alerts for entries/exits
- ✅ Customizable indicators and thresholds
- ✅ Visual trade plotting on chart

## 🔍 Strategy Logic

### 📥 Entry Conditions
- [e.g.] A **long** trade is triggered when the 50 EMA crosses above the 200 EMA and RSI is below 70.
- [e.g.] A **short** trade is triggered when the 50 EMA crosses below the 200 EMA and RSI is above 30.

### 📤 Exit Conditions
- [e.g.] Take-profit at +5%, stop-loss at -2%
- [Optional] Exit on crossover in opposite direction

### 🧾 Example Code Snippet
```pinescript
emaFast = ta.ema(close, fastLength)
emaSlow = ta.ema(close, slowLength)
longCondition = ta.crossover(emaFast, emaSlow)
if (longCondition)
    strategy.entry("Long", strategy.long)
```

## 🧪 Backtesting

Use the **Strategy Tester** tab in TradingView to evaluate the performance of this strategy.  
For best results:
- Run on [recommended timeframe]
- Apply to [specific asset class, e.g., crypto, forex]

Include example metrics if available:
| Metric          | Value      |
|-----------------|------------|
| Total Trades    | 142        |
| Win Rate        | 56%        |
| Max Drawdown    | -8.3%      |
| Net Profit      | +34.2%     |

## 🚀 How to Use

1. Open [TradingView](https://tradingview.com/)
2. Navigate to **Pine Editor**
3. Paste the entire strategy code
4. Click **"Add to Chart"**
5. Open **Strategy Tester** to see performance
6. Click ⚙️ (Settings) to modify parameters such as:
   - Strategy direction (long/short)
   - Stop loss / Take profit %
   - Signal conditions

## ❌ How to Remove / Customize Features

### Disable Short or Long Trades
Inside the code, use:
```pinescript
if (enableLong)
    strategy.entry("Long", strategy.long)

if (enableShort)
    strategy.entry("Short", strategy.short)
```
Toggle `enableLong` or `enableShort` from the strategy settings panel.

### Remove Take-Profit / Stop-Loss
Find the strategy exit lines:
```pinescript
strategy.exit("TP/SL", "Long", stop=stopPrice, limit=takeProfitPrice)
```
Comment or remove these lines to disable stop-loss/take-profit functionality.

### Change Indicator Logic
Modify or replace indicator lines:
```pinescript
// Replace EMA with SMA if desired
emaFast = ta.sma(close, fastLength)
```

## 🔔 Alerts

This strategy includes built-in alert conditions:
```pinescript
alertcondition(longCondition, title="Long Signal", message="Long setup triggered")
```

To enable:
1. Click "Create Alert"
2. Select "Condition" = Your Strategy
3. Choose your alert type (long, short, exit)
4. Customize notification message/email

## 🧰 Inputs

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `fastLength` | int | 50 | Fast EMA length |
| `slowLength` | int | 200 | Slow EMA length |
| `rsiLength` | int | 14 | RSI period |
| `rsiOverbought` | float | 70 | RSI overbought level |
| `stopLossPercent` | float | 2.0 | % below entry price |
| `takeProfitPercent` | float | 5.0 | % above entry price |
| `enableLong` | bool | true | Enable long trades |
| `enableShort` | bool | true | Enable short trades |

## 📝 Notes

- Tested on [BTCUSDT / AAPL / EURUSD], [1H / 4H / daily] chart
- This strategy does not repaint
- For educational purposes only. Always test before live trading.

## 📄 License

MIT License – free to use, modify, and distribute with attribution.
