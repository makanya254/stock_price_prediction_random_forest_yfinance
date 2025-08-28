# stock_price_prediction_random_forest_yfinance
A machine learning project that predicts next-day stock price ranges using a Random Forest model on Yahoo Finance data. For educational use only.
📊 Stock Price Prediction with Random Forest (Yahoo Finance Data)

🔍 How the Prediction Works

This project predicts the next day's stock price range by first predicting the **next day's daily return** using a Random Forest Regressor.

---

Features Used (Model Inputs)
1. OHLCV Data for Current Day:
   - `Open` price
   - `High` price
   - `Low` price
   - `Close` price
   - `Adj Close` price
   - `Volume`

2. Lagged Daily Returns (from past 5 days):
   - `lag_1` → Daily return 1 day ago
   - `lag_2` → Daily return 2 days ago
   - `lag_3` → Daily return 3 days ago
   - `lag_4` → Daily return 4 days ago
   - `lag_5` → Daily return 5 days ago

---

Target Variable (What We Predict)
- Next Day’s Daily Return:
\[
\text{Daily Return} = \frac{\text{Adj Close}_t - \text{Adj Close}_{t-1}}{\text{Adj Close}_{t-1}}
\]
The predicted return is then applied to the last Adjusted Close price to estimate the **next-day price range** in:
- USD
- EUR
- INR

---

Feature → Target Flow Diagram

```mermaid
flowchart TD
    A[Historical Stock Data (OHLCV from yfinance)] --> B[Calculate Daily Return]
    B --> C[Create Lag Features: lag_1 ... lag_5]
    C --> D[Combine: OHLCV + Lag Features]
    D --> E[Random Forest Regressor]
    E --> F[Predict Next-Day Daily Return]
    F --> G[Convert to Next-Day Price Range in USD/EUR/INR]
Author: Mr.Ganja890(SHRAVAN N J)
Disclaimer: This notebook is for educational purposes only. It does not constitute financial advice.
