## Stock Prediction App

This repository provides tools and models for stock price prediction based on historical data and technical indicators.

### Logistic Regression Model

**File:** `logistic_regression_model.py`

This script implements a Logistic Regression model to predict the direction of stock price movement (up or down) based on various technical indicators and historical price data. It's designed for binary classification tasks, making it suitable for forecasting short-term trends.

#### Features:
*   **Data Preparation:** Fetches historical stock data (e.g., from Yahoo Finance) and computes a range of technical indicators like SMA, EMA, RSI, MACD, Bollinger Bands, etc.
*   **Target Variable:** Defines the target variable as the future stock price movement (e.g., whether the 'Close' price will be higher or lower after a specified number of days).
*   **Model Training:** Trains a Logistic Regression classifier on the prepared dataset.
*   **Evaluation:** Evaluates model performance using metrics such as accuracy, confusion matrix, and classification report.
*   **Prediction:** Predicts the probability of the stock price moving up or down.

#### Dependencies:
To run the Logistic Regression model, you need the following Python libraries:
*   `pandas`
*   `numpy`
*   `scikit-learn`
*   `yfinance` (for data fetching)
*   `ta` (Technical Analysis library)

You can install them using pip:
```bash
pip install pandas numpy scikit-learn yfinance ta
```

#### Usage:
1.  **Run the script:**
    ```bash
    python logistic_regression_model.py
    ```
2.  **Configuration:**
    *   The script is currently configured with a default stock ticker (`AAPL`), start date, end date, and `n_days` for future prediction. You might need to modify these parameters directly within the script to fit your specific analysis.
    *   Look for variables like `ticker`, `start_date`, `end_date`, and `n_days_future_prediction` at the beginning of the `logistic_regression_model.py` file to adjust.

#### Output:
The script will print:
*   The shape of the training and testing datasets.
*   Model accuracy.
*   A confusion matrix.
*   A classification report.
*   Predictions (probabilities of price movement) for the test set.

#### Example Code Snippet (from `logistic_regression_model.py`):
```python
import pandas as pd
import numpy as np
import yfinance as yf
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report, confusion_matrix, accuracy_score
import ta

# --- Configuration Parameters (can be modified) ---
# ticker = 'AAPL'
# start_date = '2010-01-01'
# end_date = '2023-01-01'
# n_days_future_prediction = 5 # Predict movement 5 days into the future
# --------------------------------------------------

# ... (Data fetching, feature engineering, and model training logic)

# Example of getting predictions
# predictions = model.predict(X_test)
# probabilities = model.predict_proba(X_test)
# print(probabilities[:5]) # Print first 5 prediction probabilities
```