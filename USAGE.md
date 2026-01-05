# How to Use the NSE 500 Stock Analysis Notebook

## Opening in Google Colab

### Method 1: Direct GitHub Link
1. Go to [Google Colab](https://colab.research.google.com/)
2. Click on "File" → "Open notebook"
3. Select the "GitHub" tab
4. Enter the repository URL: `ivikasavnish/forum-notebook`
5. Select the `nse500_stock_analysis.ipynb` file

### Method 2: Direct Link
Click here to open directly in Colab:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ivikasavnish/forum-notebook/blob/main/nse500_stock_analysis.ipynb)

## Running the Notebook

### Step-by-Step Instructions

1. **Install Dependencies** (Cell 1)
   - Run the first code cell to install required packages
   - This installs: `yfinance`, `pandas`, `numpy`, `matplotlib`, `seaborn`
   - Wait for installation to complete (~30 seconds)

2. **Import Libraries** (Cell 2)
   - Run this cell to import all necessary libraries
   - You should see "Libraries imported successfully!"

3. **Load Stock List** (Cell 3)
   - Run this cell to load the NSE 500 stock list
   - 50 popular stocks are pre-configured
   - You'll see "Loaded 50 NSE stocks"

4. **Create Stock Selection Widget** (Cell 4)
   - Run this cell to create the interactive dropdown
   - You'll see a dropdown menu and a "Fetch Data" button

5. **Load Functions** (Cells 5-8)
   - Run cells 5, 6, 7, and 8 in sequence
   - These define the data collection, calculation, and visualization functions
   - Each will display a confirmation message

6. **Setup Complete** (Cell 9)
   - Run this cell to connect the button handler
   - You'll see "✅ Setup complete!"

7. **Analyze Stocks**
   - Use the dropdown to select a stock (e.g., "RELIANCE", "TCS", "INFY")
   - Click the "Fetch Data" button
   - Wait for analysis to complete (may take 30-60 seconds)

## Understanding the Output

### For Each Stock, You'll Get:

#### 1. Hourly Data Analysis
- **Data Points**: Number of hourly data points collected (1 year)
- **Statistics**: 
  - Average up/down percentages
  - Median values
  - Maximum and minimum changes
- **Most Common Movements**: Top 5 most frequent percentage changes (rounded to 0.5%)
- **Visualization**: Bar charts showing frequency of up and down movements

#### 2. Daily Data Analysis
- **Data Points**: Number of daily data points collected (1 year)
- **Statistics**: Same as hourly, but for daily movements
- **Most Common Movements**: Top 5 most frequent daily percentage changes
- **Visualization**: Bar charts for daily movements

### Interpreting the Results

#### Percentage Rounding
All percentages are rounded to the nearest 0.5%:
- 0.2% becomes 0.0%
- 0.3% becomes 0.5%
- 0.7% becomes 0.5%
- 0.8% becomes 1.0%
- -1.2% becomes -1.0%
- -1.7% becomes -1.5%

#### Most Common Percentages
The notebook identifies which rounded percentage changes occur most frequently:
- **Green bars** (left): Most common upward movements
- **Red bars** (right): Most common downward movements
- Numbers show how many times each percentage occurred

#### Example Interpretation
If you see "+0.5%: 150 times" in the hourly data, it means:
- The stock moved up by approximately 0.5% (0.25% to 0.74%)
- This happened 150 times in the past year
- This is useful for understanding typical volatility patterns

## Customizing the Notebook

### Adding More Stocks

Edit Cell 3 to add more stocks:

```python
NSE500_STOCKS = [
    "RELIANCE.NS", "TCS.NS", # existing stocks...
    "YOURSTOCK.NS",  # Add your stock here
    # ... more stocks
]
```

**Important**: Always add `.NS` suffix for NSE stocks!

### Changing the Time Period

Currently set to 1 year. To modify:

In Cell 5, change the period parameter:
```python
# For 6 months
df = stock.history(period="6mo", interval="1h")

# For 2 years (daily only, hourly limited to 1 year)
df = stock.history(period="2y")
```

Valid periods: `1d`, `5d`, `1mo`, `3mo`, `6mo`, `1y`, `2y`, `5y`, `10y`, `ytd`, `max`

### Changing the Rounding Increment

Currently rounds to 0.5%. To change:

In Cell 6, modify the rounding factor:
```python
# Round to nearest 0.25%
rounded_changes = (pct_changes / 0.25).round() * 0.25

# Round to nearest 1%
rounded_changes = (pct_changes / 1.0).round() * 1.0
```

### Displaying More Results

To show more than 10 most common values:

In Cell 8, change the `n` parameter:
```python
ups_common_minute = find_most_common(ups_minute, n=20)  # Show top 20
```

## Data Limitations & Notes

### Minute-Level Data
- **Yahoo Finance Limitation**: True minute-level data (1m interval) is only available for the last 7 days
- **Our Solution**: We use hourly intervals (1h) for the full year
- **Why**: Hourly data still provides good intraday pattern analysis
- **Alternative**: For true 1-minute data, you would need a premium data provider

### Data Availability
- Some stocks may have limited data
- Market holidays and weekends have no data
- Data quality depends on Yahoo Finance
- NSE stocks require the `.NS` suffix

### Performance
- Fetching data may take 30-60 seconds per stock
- Larger time periods take longer
- Multiple consecutive requests might be rate-limited

## Troubleshooting

### "No data available for [STOCK]"
- Check if the ticker symbol is correct
- Ensure `.NS` suffix is included
- The stock might be delisted or have no trading data

### Rate Limiting Errors
- Wait a few minutes between requests
- Yahoo Finance may temporarily block excessive requests
- Try again later

### Widget Not Showing
- Make sure you run cells in order
- Restart runtime and run all cells from the beginning
- Check that ipywidgets is installed

### Import Errors
- Re-run Cell 1 to reinstall packages
- Restart the runtime: Runtime → Restart runtime
- Run all cells again

## Tips for Best Results

1. **Run cells in order** - Don't skip cells
2. **Wait for completion** - Don't interrupt data fetching
3. **Start with popular stocks** - They have more reliable data (RELIANCE, TCS, INFY)
4. **Compare multiple stocks** - Run analysis on several stocks to compare patterns
5. **Save your results** - Take screenshots or download the notebook with output

## Advanced Usage

### Batch Analysis
To analyze multiple stocks, modify Cell 10:

```python
# Analyze multiple stocks
stocks_to_analyze = ["RELIANCE.NS", "TCS.NS", "INFY.NS"]
for ticker in stocks_to_analyze:
    analyze_stock(ticker)
```

### Export Results
Add this cell to export data:

```python
# After running analysis, export to CSV
ups_daily.to_csv('ups_daily.csv')
downs_daily.to_csv('downs_daily.csv')
```

### Statistical Analysis
Add more advanced statistics:

```python
# Add to display_statistics function
print(f"  Std Dev: {ups.std():.2f}%")
print(f"  Skewness: {ups.skew():.2f}")
print(f"  Kurtosis: {ups.kurtosis():.2f}")
```

## Support & Feedback

For issues or suggestions:
1. Check the troubleshooting section above
2. Verify you're using the latest version of the notebook
3. Open an issue on the GitHub repository

## License

This notebook is provided as-is for educational and research purposes.
