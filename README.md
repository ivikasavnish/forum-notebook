# forum-notebook
a specific notebook designed to be embedded in colab and forum

## NSE 500 Stock Analysis Notebook

This repository contains a Google Colab notebook for analyzing NSE 500 stocks.

### Features

- **Stock Selection**: Interactive dropdown to select from 50 popular NSE stocks
- **Data Collection**: 
  - 1 year of hourly (intraday) data
  - 1 year of daily data
- **Analysis**:
  - Calculates percentage changes for all data points
  - Rounds percentages to nearest 0.5%
  - Identifies most common up and down movements
  - Provides statistical summaries
  - Visualizes results with charts

### Usage

1. Open the notebook in Google Colab:
   - Click on `nse500_stock_analysis.ipynb`
   - Click "Open in Colab" button at the top

2. Run all cells in sequence (or use Runtime > Run all)

3. Select a stock from the dropdown menu

4. Click "Fetch Data" to analyze the selected stock

### Requirements

The notebook automatically installs required packages:
- yfinance
- pandas
- numpy
- matplotlib
- seaborn

### Data Source

Stock data is fetched using the [yfinance](https://github.com/ranaroussi/yfinance) library, which provides access to Yahoo Finance data.

### Note on Data Limitations

- **Minute Data**: Yahoo Finance API limits minute-level data to the last 7 days. For 1-year intraday analysis, the notebook uses **hourly intervals**.
- **Daily Data**: Full 1 year of daily data is available.

### Sample Stocks Included

The notebook includes 50 popular NSE stocks including:
- Large caps: RELIANCE, TCS, HDFCBANK, INFY, ICICIBANK
- Banking: SBIN, KOTAKBANK, AXISBANK, INDUSINDBK
- IT: TCS, INFY, WIPRO, HCLTECH, TECHM
- Consumer: HINDUNILVR, ITC, NESTLEIND, BRITANNIA
- Auto: TATAMOTORS, MARUTI, M&M, HEROMOTOCO
- And many more...

### Customization

You can easily extend the stock list by editing the `NSE500_STOCKS` list in the notebook. Add any NSE stock ticker with the `.NS` suffix (e.g., "STOCKNAME.NS").
