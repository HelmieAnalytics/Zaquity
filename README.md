# zaquity

This package provides utility functions for working with stock price series data of 350 securities trading on the Johannesburg Stock Exchange (XJSE). It includes processing stock tickers, fetching historical data, cleaning outliers, and saving the price data in ohlcv format as a dataset/data bundle to a folder in your local disc drive. Each file saved in the dataset is in csv format. 

API requirement:

A MarketStack API is required to retrieve stock tickers which the user can obtain by signing up for a free MarketStack account here: https://marketstack.com/
   
## Modules

`jse_tickers`: Retrieves stock tickers from the MarketStack API.

`jse_data`: Fetches historical stock data in ohlcv format (Open, High, Low, Close, Volume).

`jse_process_data`: Processes stock CSV files to remove outliers from the dataset.

## Implementation

### 1. Import the desired module(s) from the package.

```
import zaquity
from zaquity import jse_tickers
from zaquity import jse_data
from zaquity import jse_process_data
```
   
### 2. Use the provided functions to perform specific tasks related to stock data.

`.get.tickers`
```
tickers = jse_tickers.get_tickers("your_api_key_here")
```
`.get.data`
```
jse_data.get_data(['AAPL', 'MSFT'], '2022-01-01', '2022-12-31', '/path/to/output_folder')
```
`.clean`
```
jse_process_data.clean('/path/to/csv_folder')
```

## Example usage


Import functions
```
import pandas as pd
import zaquity
from zaquity import jse_tickers as jt
from zaquity import jse_data as jd
from zaquity import process_data as jpd
```
1. Set variables.
```
my_access_key = '<your_MarketStack_API_key>'

symbols = tickers

start = '2000-01-27'
end = '2024-06-29'

output_folder_path = '/content/jsestocks'
```
2. Call functions.
```
tickers = jt.get_tickers(my_access_key)

jd.get_data(symbols, start, end, output_folder_path)
```
3. Saving the data for each stock to disc.
```
jpd.clean('/content/jsestocks')
```
4. Read data from disc to a pandas dataframe.
```
df = pd.read_csv('/content/jsestocks/NPN.JO.csv') 
```
Passing the `df` variable or `print(df)` function will now display the ohlc price data of Naspers (XJSE.NPN) from 27 January 2000 to 29 June 2024 in a pandas dataframe. 

## Limitations and recommendations

1. The package is currently under development and not available for release and installation on PyPI.

2. The data imported with this package is not suitable for backtesting investment strategies or developing trading systems. It includes only historical prices of companies trading on the XJSE (Johannesburg Stock Exchange) on the specific day and time the package is used. As a result, the dataset suffers from inherent bias, specifically survivorship bias. In future versions of zaquity, efforts will be made to mitigate this effect. To create a more robust dataset, users can supplement it with data from other sources to reduce bias and improve the reliability of their analysis.
