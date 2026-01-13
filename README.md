# GridBot-Mql5

# Gridbot5 - EUR/USD MQL5 Grid Trading Expert Advisor

A sophisticated grid trading Expert Advisor (EA) for MetaTrader 5 that automatically trades in sideways markets using Bollinger Bands for market condition detection.

## 🎯 Features

### Market Condition Detection
- **Bollinger Bands Analysis**: Uses Bollinger Bands to identify sideways/ranging markets
- **Bandwidth Filter**: Only trades when Bollinger Band width is below a specified threshold, ensuring the bot operates in low-volatility, ranging conditions
- **M5 Timeframe**: Analyzes market conditions on 5-minute candles for optimal entry timing

### Grid Trading Strategy
- **Automatic Grid Placement**: Places buy or sell orders at predefined grid intervals
- **Smart Entry Logic**: Determines trade direction based on price action (buy on pullbacks, sell on rallies)
- **Grid Spacing**: Configurable grid size in points to control trade frequency

### Risk Management
- **Daily Order Limit**: Prevents overtrading by limiting the number of orders per day
- **Maximum Drawdown Protection**: Automatically stops trading if drawdown exceeds the specified percentage
- **Stop Loss & Take Profit**: Each trade is protected with configurable SL and TP levels
- **Daily Reset**: Automatically resets equity baseline and order counter at midnight

### Trade Management
- **Position Tracking**: Monitors existing positions to maintain proper grid spacing
- **Error Handling**: Comprehensive error reporting for failed order submissions

## 📊 Input Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| `Lots` | 0.01 | Position size (lot size) |
| `GridSizePoints` | 300 | Grid spacing in points (30 pips for 5-digit brokers) |
| `TakeProfitPoints` | 150 | Take profit distance in points |
| `InputStopLossPoints` | 200 | Stop loss distance in points |
| `MaxOrdersPerDay` | 10 | Maximum number of orders allowed per day |
| `MaxDrawdownPct` | 5.0 | Maximum drawdown percentage before trading stops |
| `BB_Period` | 14 | Bollinger Bands period |
| `BB_Deviation` | 2.0 | Bollinger Bands standard deviation multiplier |
| `MaxBBWidthPrice` | 0.006 | Maximum Bollinger Band width to consider market as sideways (e.g., 60 pips) |
| `MagicNumber` | 123456 | Unique identifier for bot's trades |

## 🔧 How It Works

1. **Market Analysis**: On each new M5 candle, the bot calculates Bollinger Band width
2. **Sideways Detection**: If band width is below the threshold, the market is considered sideways
3. **Grid Entry**: When conditions are met:
   - Checks if price has moved enough from the last entry (grid spacing)
   - Determines direction based on price action (current price vs. previous close)
   - Places a buy or sell order with SL and TP
4. **Risk Checks**: Before each trade:
   - Verifies daily order limit hasn't been reached
   - Checks if maximum drawdown hasn't been exceeded
5. **Daily Reset**: At midnight, resets the equity baseline and order counter

## ⚠️ Important Notes

- **Broker Compatibility**: Designed for 5-digit brokers (adjust point values for 4-digit brokers)
- **Market Conditions**: Best suited for ranging/sideways markets, not trending markets
- **Risk Warning**: Trading involves risk. Always test on a demo account first and use appropriate risk management
- **Single Symbol**: Currently designed to trade one symbol at a time

## 📝 Requirements

- MetaTrader 5 platform
- MQL5 compiler
- Account with the broker you wish to trade

## 🚀 Installation

1. Copy `Gridbot5.mq5` to your MetaTrader 5 `Experts` folder
2. Restart MetaTrader 5 or refresh the Navigator window
3. Drag the EA onto a chart
4. Configure input parameters according to your risk tolerance
5. Enable AutoTrading

## 📈 Strategy Logic

The bot uses a mean-reversion approach:
- **Buy Signal**: When price is below the previous candle's close (pullback detected)
- **Sell Signal**: When price is above the previous candle's close (rally detected)
- **Grid Logic**: Only enters new trades when price has moved the specified grid distance from the last entry

## 🔍 Monitoring

The bot provides detailed logging:
- Daily reset notifications
- Bollinger Band width measurements
- Trade execution confirmations
- Error messages for failed orders
- Drawdown protection alerts

## ⚙️ Customization

You can customize the bot by modifying:
- Grid spacing for different volatility levels
- Bollinger Band parameters for different market conditions
- Risk parameters (SL, TP, drawdown limits)
- Daily order limits based on your trading style

## 📄 License

This is a trading tool for educational and personal use. Use at your own risk.

## 🤝 Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

---

**Disclaimer**: This Expert Advisor is provided as-is for educational purposes. Past performance does not guarantee future results. Always test thoroughly on a demo account before using real money.

