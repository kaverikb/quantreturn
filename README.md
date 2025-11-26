# **QuantReturn: Multi-Model Time-Series Forecasting for Tech Equities**

This project performs a comparative analysis of ARIMA and LightGBM models for forecasting daily stock returns of leading technology equities (TESLA, GOOGLE, NVDIA, AMD, ORACLE). Using 10 years of OHLCV data and 100+ engineered features, the project evaluates statistical vs. machine learning forecasting approaches with a focus on out-of-sample robustness and trading relevance.
*Full methodology and results documented in* `TSA_task.pdf`. 

---

## ** Key Features**

* **Data Pipeline:**

  * 2015–2024 historical OHLCV data via *yfinance*.
  * Data quality checks, anomaly detection, missing value handling, and stationarity validation (ADF tests show p < 0.0001 for all stocks).
* **Feature Engineering:**

  * 116 engineered features including lagged returns, rolling statistics, technical indicators (RSI, MACD, SMA), volume features, sector ETF metrics (XLK), and calendar variables.
* **Models Implemented:**

  * **ARIMA** for univariate statistical forecasting on differenced data.
  * **LightGBM** gradient boosting model leveraging all engineered features.
  * Baseline models: Naive, 5-day Moving Average, Linear Regression (lags only).
* **Evaluation Metrics:**

  * RMSE, MAE, MAPE (with caveats), directional accuracy, residual diagnostics, Ljung-Box tests.
  * 5-fold expanding window time-series cross-validation.

---

## ** Summary of Findings**

* **LightGBM outperforms ARIMA** by a large margin after normalization, offering 50× lower error relative to target magnitude.
* Lagged returns and short-term volatility dominate feature importance across all models.
* Directional accuracy remains close to random (≈50%), in line with the Efficient Market Hypothesis.
* CV scores closely match test scores (<7% deviation), indicating strong generalization.

---

## ** Results (Condensed)**

* **LightGBM Test RMSE (returns space):**

  * TSLA: 0.0366
  * GOOG: 0.0184
  * ORCL: 0.0197
* **ARIMA RMSE (price space):**

  * TSLA: 116
  * GOOG: 60
  * ORCL: 49
* **Directional Accuracy:** 51–54%
* **Residuals:** Near-normal, no autocorrelation (Ljung-Box p > 0.05).
* **Ratio of predictions:** ≈0.60

---




