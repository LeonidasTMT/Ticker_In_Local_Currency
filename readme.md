# TickerFX – Interactive Stock Price Tracker & Currency Converter

**TickerFX** is a web-based tool to track stock prices in any currency, visualize historical performance, and analyze gains/losses with interactive charts. Convert any ticker to your preferred currency, compare against the original currency, and explore price trends over time.

[Live Demo](https://leonidastmt.github.io/TickerFX/)

---

## Features

- **Historical Stock Data:** Fetch 10+ years of historical prices from Yahoo Finance.  
- **Currency Conversion:** Convert stock prices to any target currency using up-to-date FX rates.  
- **Dual-Axis Charts:** Visualize stock performance in both original and converted currencies.  
- **Interactive Plotting:** Click and drag on the chart to measure gains between specific dates.  
- **Dynamic Stats:** Gain/loss calculations update automatically for selected periods.  
- **Data Table:** View recent 30-day price data with conversion rates.  
- **Responsive Design:** Works on desktop and mobile devices.  
- **Easy to Use:** Enter a ticker and target currency, click Convert & Plot, and explore.  

---

## How It Works

1. Open the [Live Demo](https://leonidastmt.github.io/TickerFX/).  

2. Enter a stock ticker (e.g., `AAPL`) and a target currency (e.g., `EUR`) and click **Convert & Plot**.  

3. Optional: Click **Show Dual Currency** to see both original and converted stock prices.  

4. Use the date range buttons (`3M`, `6M`, `1Y`, `5Y`, `MAX`, `YTD`) to filter the chart.  

5. Click and drag on the chart to measure gain/loss between two dates.  

---

## Technical Details

- **Data Source:** Yahoo Finance API via `https://query1.finance.yahoo.com/v8/finance/chart/`  
- **FX Conversion:** Automatically fetches currency pairs; supports inverse FX if direct pair unavailable.  
- **Visualization:** Built with [Plotly.js](https://plotly.com/javascript/) for interactive charts.  
- **Frontend:** Pure HTML, CSS, and JavaScript, no backend required.  
- **CORS Handling:** Uses `https://corsproxy.io/` for API requests.  

---

## Limitations

- Relies on Yahoo Finance; if API or CORS proxy changes, data fetching may fail.  
- FX data may have gaps; the tool fills forward missing rates but very old dates may have limited accuracy.  
- Not a real-time trading tool—intended for historical analysis and visualization.  

---
