# stock_price_prediction_random_forest_yfinance
A machine learning project that predicts next-day stock price ranges using a Random Forest model on Yahoo Finance data. For educational use only.

📊 Stock Price Prediction with Random Forest (Yahoo Finance Data)

🔍 How the Prediction Works

This project predicts the next day's stock price range by first predicting the **next day's daily return** using a Random Forest Regressor.

---

### Features Used (Model Inputs)
1.  **OHLCV Data for Current Day:**
    * `Open` price
    * `High` price
    * `Low` price
    * `Close` price
    * `Adj Close` price
    * `Volume`

2.  **Lagged Daily Returns (from past 5 days):**
    * `lag_1` → Daily return 1 day ago
    * `lag_2` → Daily return 2 days ago
    * `lag_3` → Daily return 3 days ago
    * `lag_4` → Daily return 4 days ago
    * `lag_5` → Daily return 5 days ago

---

### Target Variable & Final Output
The model's primary goal is to predict the **Next Day’s Daily Return**, calculated as:
$$
\text{Daily Return} = \frac{\text{Adj Close}_t - \text{Adj Close}_{t-1}}{\text{Adj Close}_{t-1}}
$$
This predicted return is then used to generate two key outputs:

1.  **Next-Day Price Range:** The estimated price range (high-low) for the next trading day, converted into **USD**, **EUR**, and **INR**.

2.  **Formatted Word Report:** All results, including performance metrics (MSE, Accuracy), price predictions, and visualizations, are automatically compiled into a professional Microsoft Word (`.docx`) document for easy review and sharing.

---

### Full Project Flow Diagram

```mermaid
flowchart TD
    A["Historical Stock Data (OHLCV from yfinance)"] --> B["Calculate Daily Return"]
    B --> C["Create Lag Features: lag_1 ... lag_5"]
    C --> D["Combine: OHLCV + Lag Features"]
    D --> E["Random Forest Regressor"]
    E --> F["Predict Next-Day Daily Return"]
    F --> G["Convert to Next-Day Price Range in USD/EUR/INR"]
    G --> H["Generate Formatted Word Report (.docx)"]
