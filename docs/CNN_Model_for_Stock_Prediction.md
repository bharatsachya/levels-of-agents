# CNN Model for Stock Prediction

The `WiseTrader` application includes a Convolutional Neural Network (CNN) based model for predicting stock price movements. This model, accessible via the `wise_cnn` page, allows users to input a stock ticker and visualize the training and evaluation performance of a simple CNN on historical stock data.

## Functionality

When you navigate to the `wise_cnn` page, the application performs the following steps:

1.  **Stock Data Fetching**: It downloads historical stock data (last 1 year, 1-hour interval) for the entered ticker symbol using `yfinance`.
2.  **Data Preprocessing**: The fetched data (Open, High, Low, Close, Volume) is scaled using `MinMaxScaler`. It then creates sequences of historical data to predict future price direction (up or down).
3.  **Model Training**: A 1D Convolutional Neural Network is built and trained on the preprocessed data. The model consists of:
    *   `Conv1D` layer with 64 filters and a kernel size of 3.
    *   `MaxPooling1D` layer.
    *   `Flatten` layer.
    *   `Dense` hidden layer with 64 units.
    *   Output `Dense` layer with a sigmoid activation for binary classification (predicting price movement direction).
4.  **Model Evaluation**: After training, the model's accuracy and loss are evaluated on a test set.
5.  **Visualization**: The training and validation accuracy and loss over epochs are plotted, providing a visual representation of the model's learning process.

## How to Use

1.  **Enter Stock Ticker**: On the `wise_cnn` page, enter a valid stock ticker symbol in the provided input field (e.g., `NV20.NS` for Nifty 20).
2.  **View Results**: The application will automatically fetch data, train the model, evaluate it, and display:
    *   The overall accuracy of the model on the test set.
    *   Plots showing training/validation accuracy and loss over 10 epochs.

### Example

**Input:** `NV20.NS`

**Output:**

*   A displayed accuracy score (e.g., `Accuracy: 0.7580`)
*   Two plots: one for Train/Validation Accuracy and another for Train/Validation Loss, showing their progression across epochs.

## Technical Details

*   **Data Source**: `yfinance`
*   **Machine Learning Library**: `TensorFlow / Keras`
*   **Input Data**: Open, High, Low, Close, Volume for a specified `sequence_length` (10 time steps).
*   **Output Prediction**: Binary classification (price goes up (1) or down (0)).
*   **Optimizer**: Adam
*   **Loss Function**: Binary Crossentropy
*   **Metrics**: Accuracy

This feature provides an interactive way to explore the application of CNNs to financial time series forecasting within `WiseTrader`.