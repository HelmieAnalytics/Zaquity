# zaquity

This package provides utility functions for working with stock price series data of 350 securities trading on the Johannesburg Stock Exchange (XJSE) , including processing stock tickers, fetching historical data, cleaning outliers, and saving the price data in ohlcv format as a dataset in csv files to a folder on your local disc drive.

Modules:
    - `jse_tickers`: Retrieves stock tickers from the MarketStack API.
    - `jse_data`: Fetches historical stock data using the YahooQuery library.
    - `jse_process_data`: Processes stock CSV files to remove outliers.

Usage:
    1. Import the desired module(s) from the package.
    2. Use the provided functions to perform specific tasks related to stock data.

Example:
    >>> from zaquity_data import marketstack_tickers, stock_data_fetcher, stock_data_cleaner
    >>> tickers = marketstack_tickers.get_tickers("your_api_key_here")
    >>> stock_data_fetcher.get_data(['AAPL', 'MSFT'], '2022-01-01', '2022-12-31', '/path/to/output_folder')
    >>> stock_data_cleaner.clean('/path/to/csv_folder')

"""

__version__ = "0.1.0"
__author__ = "Helmie Analytics"
__email__ = "francoishemie@outlool.com"
