# Quick Start Guide

## Open in Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ivikasavnish/forum-notebook/blob/main/nse500_stock_analysis.ipynb)

Click the badge above to open the notebook directly in Google Colab!

## Quick Steps

1. **Open the notebook** in Google Colab (use the badge above)
2. **Run all cells** (Runtime → Run all)
3. **Select a stock** from the dropdown menu
4. **Click "Fetch Data"** and wait for results

## What You'll Get

For each stock, the notebook provides:
- 📊 1 year of hourly (intraday) data analysis
- 📈 1 year of daily data analysis
- 📉 Most common percentage movements (rounded to 0.5%)
- 📊 Statistical summaries (average, median, max/min)
- 📊 Visual charts showing frequency of movements

## Example Output

```
Most Common UP Percentages (Daily):
  +0.5%: 45 times
  +1.0%: 32 times
  +1.5%: 18 times
  +2.0%: 12 times
  +2.5%: 8 times

Most Common DOWN Percentages (Daily):
  -0.5%: 42 times
  -1.0%: 28 times
  -1.5%: 15 times
  -2.0%: 10 times
  -2.5%: 7 times
```

Plus bar charts showing visual representation of these frequencies!

## Available Stocks

The notebook includes 50 popular NSE stocks:
- **Large Caps**: RELIANCE, TCS, HDFCBANK, INFY, ICICIBANK
- **Banking**: SBIN, KOTAKBANK, AXISBANK, INDUSINDBK
- **IT**: TCS, INFY, WIPRO, HCLTECH, TECHM
- **Pharma**: SUNPHARMA, DIVISLAB, DRREDDY, CIPLA
- **Auto**: TATAMOTORS, MARUTI, M&M, HEROMOTOCO, BAJAJ-AUTO
- And many more!

## Important Notes

⚠️ **Data Granularity**: Yahoo Finance limits minute-level data to 7 days. For 1-year analysis, we use hourly intervals for intraday data.

⏱️ **Processing Time**: Each stock analysis takes 30-60 seconds to fetch and process data.

📊 **Rounding**: All percentages are rounded to the nearest 0.5% for pattern analysis.

## Need Help?

- 📖 See [USAGE.md](USAGE.md) for detailed instructions
- 📖 See [README.md](README.md) for full documentation
- 🐛 Having issues? Check the troubleshooting section in USAGE.md

## Features

✅ Interactive stock selection
✅ Automatic data fetching from Yahoo Finance
✅ Statistical analysis
✅ Beautiful visualizations
✅ Easy to customize
✅ No installation required (runs in Colab)

## License

MIT License - Free to use and modify
