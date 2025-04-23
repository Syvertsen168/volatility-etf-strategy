# syv---student

# Volatility-Aware ETF Trading Bot

A Python-based algorithmic trading strategy that rotates among ETFs (QQQ, IWM, VWO) using simple moving average (SMA) signals, while dynamically rotating to cash during high-volatility periods. The strategy uses Alpaca's Paper Trading API for live trading simulation and backtesting with historical data from Yahoo Finance.

---

##  Strategy Logic

This strategy allocates to ETFs only when:
1. **Short-term trend (50-day SMA)** is above the **long-term trend (200-day SMA)**.
2. **Market volatility** is below the 80th percentile over the past year.

When volatility exceeds the threshold, the portfolio exits positions and rotates fully to **cash**.

---

## Strategy Overview

This strategy blends trend-following signals with a volatility-aware overlay:

- **Technical Signal**: If the 50-day SMA is above the 200-day SMA, the ETF is considered in an uptrend and eligible for allocation.
- **Weighting**: Allocations are distributed equally among qualifying ETFs.
- **Volatility Filter**: If the average volatility exceeds the 80th percentile of the last year, all ETF weights go to zero (cash rotation).
- **Rebalancing**: Scheduled daily via the `schedule` package.

---

##  Assets Traded

- **QQQ** – Nasdaq 100 ETF
- **IWM** – Russell 2000 ETF
- **VWO** – Emerging Markets ETF

---

## 🚀 Features

- SMA crossover-based signal  
- Volatility-based cash protection  
- Dynamic rebalancing using Alpaca API  
- Scheduled execution at 10:00 AM EST on weekdays  
- Historical backtest with 10 years of data  
- Performance metrics: cumulative return, Sharpe ratio, drawdown

---

##  Backtest Example

![Image](https://github.com/user-attachments/assets/ae77e187-b557-4578-89ca-d182f75a3cf6)

| 4/22/25      | Cumulative Return | Sharpe Ratio | Max Drawdown |
|--------------|-------------------|--------------|--------------|
| Strategy     |  347.01%          |  1.05        |  -28.49 %    |
| SPY(Buy/Hold)|  197.04%          |  0.69        |   -33.72%    |
