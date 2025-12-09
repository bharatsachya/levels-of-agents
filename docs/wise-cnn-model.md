# Wise CNN: Convolutional Neural Network for Stock Prediction

The 'Wise CNN' page within the WiseTrader application implements a Convolutional Neural Network (CNN) for predicting stock price movement (up or down). This model leverages historical high-frequency stock data, including Open, High, Low, Close, and Volume.

## Functionality

This page allows users to:
1.  **Input Stock Ticker**: Specify the stock symbol for which predictions are desired.
2.  **Fetch Data**: Automatically downloads historical stock data (1 year, 1-hour intervals).
3.  **Preprocess Data**: Scales the financial data and converts it into sequences suitable for CNN input.
4.  **Train Model**: Trains a 1D CNN model to predict whether the closing price will increase or decrease.
5.  **Evaluate & Visualize**: Displays the model's accuracy and plots its training history (accuracy and loss over epochs).

## Usage

1.  **Select 'Wise CNN'**: From the sidebar on the main WiseTrader page, choose 'Wise CNN'.
2.  **Enter Stock Ticker**: In the provided text input, enter a valid stock ticker symbol (e.g., `NV20.NS`, `GOOG`).
3.  The application will automatically fetch data, preprocess it, train the CNN model, and display the accuracy and training plots.

## Technical Details

### Data Input:
- **Features**: `Open`, `High`, `Low`, `Close`, `Volume`
- **Period**: 1 year
- **Interval**: 1 hour
- **Target**: Binary classification (1 if `Close` price increases, 0 otherwise)

### Model Architecture (Sequential):
- `Conv1D` layer with 64 filters, kernel size 3, ReLU activation, and `(sequence_length, 5)` input shape.
- `MaxPooling1D` layer with pool size 2.
- `Flatten` layer.
- `Dense` layer with 64 units and ReLU activation.
- `Dense` output layer with 1 unit and Sigmoid activation (for binary classification).

### Training Parameters:
- **Optimizer**: Adam
- **Loss Function**: Binary Crossentropy
- **Metrics**: Accuracy
- **Epochs**: 10
- **Batch Size**: 64

### Example Output

After entering a stock ticker, the page will display the fetched data (if successful), the model training progress, and finally, the overall accuracy and plots illustrating the training and validation accuracy/loss over epochs.

```python
# Preprocessing snippet from wise_cnn.py
df = stock_data[['Open', 'High', 'Low', 'Close', 'Volume']]
scaler = MinMaxScaler()
scaled_data = scaler.fit_transform(df)

sequence_length = 10
X = np.array([scaled_data[i:i+sequence_length] for i in range(len(scaled_data) - sequence_length)])
closing_prices = scaled_data[sequence_length:, 3]
y = np.where(closing_prices > scaled_data[:-sequence_length, 3], 1, 0)

# Model definition snippet from wise_cnn.py
model = Sequential([
    Conv1D(filters=64, kernel_size=3, activation='relu', input_shape=(sequence_length, 5), padding='same'),
    MaxPooling1D(pool_size=2),
    Flatten(),
    Dense(64, activation='relu'),
    Dense(1, activation='sigmoid')
])
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
model.fit(X_train, y_train, epochs=10, batch_size=64, verbose=1, validation_split=0.2)
```