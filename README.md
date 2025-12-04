## Stock Predictino app

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/bharatsachya/WiseTrader.git
    cd WiseTrader
    ```

2.  **Set up a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Install dependencies:**
    All required dependencies are listed in `requirements.txt`.
    ```bash
    pip install -r requirements.txt
    ```
    *Note: The `yfinance` library is now a required dependency for fetching stock data.*

### Developer Setup Notes

A `.gitignore` file has been added to exclude development artifacts like virtual environments (`venv/`) and Python cache files (`__pycache__/`) from version control. This ensures a clean repository and aids in standard development practices.

### About the Models

The application uses different models for stock prediction. The `wise_cnn.py` model, a core component of our prediction engine, has received recent updates to improve its performance and fix some bugs. Further details on model usage and configuration will be added soon.