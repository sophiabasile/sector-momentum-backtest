# Sector Momentum Backtest

Goal: A clean, explainable backtest of a cross-sectional momentum strategy on the 11 SPDR sector ETFs, benchmarked against SPY. This is a portfolio project I must be able to explain line by line in interviews.

Strategy: Monthly rebalance. Rank sectors by trailing 12-month return, skipping the most recent month (12-1). Go long the top 3, equal weight.

Rules:
- Use pandas, vectorized where reasonable. No backtesting libraries (no backtrader, zipline, vectorbt).
- Signals must be lagged: a signal computed at t can only trade at t+1.
- Include transaction costs (default 10 bps per unit of turnover).
- Keep functions small, with docstrings explaining the finance logic.
- Build one module at a time; don't generate the whole project at once.
- After writing code, explain what it does and point out anything I should verify by hand.

Structure:
- src/data.py: download and cache prices
- src/signals.py: momentum ranking
- src/backtest.py: portfolio weights → daily returns, with costs
- src/metrics.py: CAGR, vol, Sharpe, max drawdown, turnover
- notebooks/analysis.ipynb: charts and results
- tests/: unit tests for metrics and lagging
