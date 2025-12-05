# WiseCNN Stock Prediction App

The WiseCNN Stock Prediction App is a feature within WiseTrader that leverages a Convolutional Neural Network (CNN) to make binary predictions on stock price movements (e.g., whether the closing price will be higher or lower than the previous period).

## How to Use

1.  **Navigate to the WiseCNN page:** In the WiseTrader application, select the 'WiseCNN' option.
2.  **Enter Stock Ticker:** You will see an input field labeled 'Enter Stock Ticker'. Type the symbol of the stock you wish to analyze (e.g., `NV20.NS` for Nifty 20, or a standard NASDAQ/NYSE ticker like `MSFT`).
3.  **View Results:** The application will then:
    *   Fetch historical stock data (defaulting to 1 year of 1-hour interval data).
    *   Preprocess the data for the CNN model.
    *   Train a 1D CNN model.
    *   Evaluate the model's accuracy on unseen data.
    *   Display the model's accuracy.
    *   Plot the training and validation accuracy and loss over epochs.

## Technical Details (for advanced users/developers)

The application uses `yfinance` to fetch historical stock data. The data includes 'Open', 'High', 'Low', 'Close', and 'Volume'.

### Model Architecture:

The CNN model is a simple 1D Convolutional Neural Network designed for sequence prediction:

*   **Input Layer:** `Conv1D` layer with 64 filters, kernel size 3, 'relu' activation, expecting sequences of length 10 with 5 features (OHLCV).
*   **Pooling Layer:** `MaxPooling1D` with pool size 2 to reduce dimensionality.
*   **Flatten Layer:** Flattens the output for dense layers.
*   **Dense Layers:** Two `Dense` layers, one with 64 units and 'relu' activation, followed by an output layer with 1 unit and 'sigmoid' activation for binary classification.

### Training:

The model is compiled with the Adam optimizer and 'binary_crossentropy' loss, tracking 'accuracy'. It is trained for 10 epochs with a batch size of 64 and a 20% validation split.

### Output Interpretation:

*   **Accuracy:** Indicates how well the model predicted the direction of the stock price movement on the test set. A higher accuracy means better performance.
*   **Accuracy/Loss Plots:** Visualize the model's learning process. You can observe if the model is overfitting (training accuracy much higher than validation accuracy) or underfitting (both accuracies are low).

## Example Usage

To predict for NIFTY 20:

1.  Go to the WiseCNN page.
2.  Enter `NV20.NS` in the 'Enter Stock Ticker' field.
3.  Observe the data fetching, model training progress, and final accuracy and plots.