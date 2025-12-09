# Wise LSTM: Long Short-Term Memory for Stock Prediction

The 'Wise LSTM' page within the WiseTrader application utilizes a Long Short-Term Memory (LSTM) recurrent neural network for predicting stock prices. This model focuses specifically on historical closing prices to identify patterns over time.

## Functionality

This page allows users to:
1.  **Input Stock Ticker**: Enter the symbol of the stock they wish to analyze.
2.  **Define Date Range**: Set a start and end date for fetching historical data.
3.  **Fetch Data**: Downloads historical stock data from Yahoo Finance.
4.  **Preprocess Data**: Normalizes the closing price data using `MinMaxScaler`.
5.  **Prepare for LSTM**: Splits the normalized data into training and testing sets, although the actual LSTM model training and prediction logic is currently partially implemented within the provided code snippet.

## Usage

1.  **Select 'Wise LSTM'**: From the sidebar on the main WiseTrader page, choose 'Wise LSTM'.
2.  **Enter Stock Symbol**: In the text input field, provide a stock ticker (e.g., `AAPL`, `MSFT`).
3.  **Select Start and End Dates**: Use the date pickers to specify the historical period.
4.  The application will then fetch and preprocess the data. Further model training and prediction steps would typically follow this initial data preparation.

## Technical Details

### Data Input:
- **Feature**: `Close` price
- **Source**: Yahoo Finance (`yf.download`)
- **Period**: User-defined `start_date` to `end_date`

### Data Preprocessing:
- **Normalization**: `MinMaxScaler` is applied to the 'Close' prices.
- **Train-Test Split**: Data is divided into 80% training and 20% testing sets.

```python
# Data fetching and preprocessing snippet from wise_lstm.py
# Fetch data from Yahoo Finance
data = yf.download(stock_symbol, start=start_date, end=end_date)

# Selecting 'Close' prices for prediction
df = data[['Close']].copy()

# Normalize the data
scaler = MinMaxScaler()
df['Close'] = scaler.fit_transform(df['Close'].values.reshape(-1, 1))

# Split the data into training and testing sets
train_data = df.iloc[:int(0.8*len(df))]
test_data = df.iloc[int(0.8*len(df)):]
```

**Note**: The current implementation primarily focuses on data preparation. Further development is expected to integrate the LSTM model definition, training, and prediction logic.