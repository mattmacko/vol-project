# Realized Volatility Measurement and Forecasting

Measurement and short-horizon forecasting of realized volatility on US equity data.
Nasdaq TotalView-ITCH tick data (AAPL, ~1 year) via Databento; daily OHLC for the
estimator comparison.

## Parts

1. **Volatility signature plot** — realized variance across sampling frequencies from
   tick to 30 minutes, showing the bias–variance tradeoff: upward bias at high
   frequency from bid-ask bounce, noise at low frequency.
2. **Estimator comparison** — open-to-close, Parkinson, Garman–Klass, and
   Rogers–Satchell ranked against 5-minute RV as the benchmark.
3. **HAR forecasting** — daily/weekly/monthly lagged RV as OLS regressors, evaluated
   with QLIKE loss and a Diebold–Mariano test against a naive persistence benchmark.

The goal is honest measurement, not alpha. No trading strategy.

## Setup

```bash
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt
```

Requires a Databento API key in a `.env` file at the project root: