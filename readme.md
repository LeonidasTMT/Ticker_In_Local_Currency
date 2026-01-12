\# Ticker in Local Currency



When your local currency moves, it becomes surprisingly hard to tell whether an investment actually gained or lost value for you.



This tool provides a clean, FX-adjusted historical view of any ticker in any target currency — showing what one unit of the asset was actually worth in your currency over time.



---



\## Live Demo



https://leonidastmt.github.io/Ticker\_In\_Local\_Currency/



No installation, no backend, no login — just open and use.



---



\## Purpose



This tool answers a question most brokers don’t:



“What was this asset worth in my currency at any point in time?”



It removes FX noise and lets you see historical performance the way it would have felt in your own currency.



Good for:

\- Understanding FX-adjusted historical performance

\- Comparing growth across assets with different base currencies

\- Sanity-checking whether gains were real or just FX effects



Not intended for:

\- Trading or execution decisions

\- Technical analysis

\- Tax, accounting, or regulatory reporting



---



\## Features



\- Any ticker, any currency

\- Automatic base (functional) currency detection from Yahoo Finance metadata

\- FX-adjusted historical price chart

\- Forward-filled FX rates to align with trading days

\- Inverse FX pair fallback when direct FX pairs do not exist

\- Time range presets:

&nbsp; - Max

&nbsp; - 5Y

&nbsp; - 1Y

&nbsp; - YTD

&nbsp; - 6M

&nbsp; - 3M

\- Drag-to-measure returns directly on the chart

\- Broker-style period statistics:

&nbsp; - Period start value

&nbsp; - Period end value

&nbsp; - Absolute gain / loss

&nbsp; - Percentage gain / loss

\- Collapsible data table showing recent underlying data

\- Fully frontend-only (static hosting friendly)



---



\## Technical Overview



\### Architecture



\- Frontend only

\- Single index.html

\- Vanilla JavaScript

\- Plotly.js for charting

\- No backend

\- No database

\- No build step



Designed to run entirely in the browser and be hosted on any static site provider.



---



\## Data Sources



\### Asset Price Data



\- Source: Yahoo Finance (unofficial chart API)

\- Endpoint:

&nbsp; https://query1.finance.yahoo.com/v8/finance/chart/{symbol}

\- Granularity: Daily (interval=1d)

\- Price used:

&nbsp; - Adjusted Close (preferred)

&nbsp; - Close (fallback)

\- Metadata extracted:

&nbsp; - Ticker symbol

&nbsp; - Functional currency

&nbsp; - Short name

&nbsp; - Long name



Limitations:

\- Daily data only

\- No intraday prices

\- No dividends beyond what is reflected in adjusted close

\- No corporate action modelling



---



\### FX Data



\- Source: Yahoo Finance FX tickers

\- Formats supported:

&nbsp; - Direct pair: BASEQUOTE=X (e.g. USDMYR=X)

&nbsp; - Inverse pair fallback: QUOTEBASE=X (auto-inverted)

\- Logic:

&nbsp; 1. Attempt direct FX pair

&nbsp; 2. If unavailable, attempt inverse pair and invert the rate

\- FX rates are forward-filled to match stock trading days



Limitations:

\- Reference FX rates only

\- No bid/ask spread

\- No execution prices

\- Dependent on Yahoo Finance availability



---



\## Currency Conversion Logic



\- Functional currency is automatically detected from ticker metadata

\- Target currency is specified by the user

\- Conversion formula:



&nbsp; converted\_price = asset\_price × fx\_rate



\- If functional currency equals target currency:

&nbsp; - FX rate defaults to 1

\- Missing FX values:

&nbsp; - Forward-filled using the last known rate



---



\## Chart \& Interactivity



\- Line chart rendered using Plotly.js

\- Unified hover crosshair for easy comparison

\- All filtering performed client-side



Gain / Loss Calculation:



&nbsp; percentage\_change = (end\_value - start\_value) / start\_value × 100%



Drag-to-measure:

\- Click and drag horizontally on the chart

\- Displays:

&nbsp; - Start date and value

&nbsp; - End date and value

&nbsp; - Absolute gain or loss

&nbsp; - Percentage change

\- Double-click resets the measurement to the full visible range



---



\## Data Table



\- Hidden by default

\- Toggle using View Data Table

\- Displays the most recent 30 days:

&nbsp; - Date

&nbsp; - Original price (functional currency)

&nbsp; - FX rate used

&nbsp; - Converted price (target currency)



Designed for transparency without cluttering the main interface.



---



\## Usage



1\. Enter a ticker symbol 

2\. Enter a target currency 

3\. Click Convert \& Plot

4\. Use the preset buttons to filter by time range

5\. Drag across the chart to measure returns

6\. Toggle the data table to inspect raw values



---



\## Hosting



This project is deployed as a static site using GitHub Pages:



https://leonidastmt.github.io/Ticker\_In\_Local\_Currency/



The app is fully frontend-only and can be hosted anywhere that supports static files:

\- GitHub Pages

\- Netlify

\- Cloudflare Pages

\- Any static web server



---



\## Limitations \& Caveats



\- Daily data only (no intraday or real-time pricing)

\- FX rates are reference values, not executable prices

\- No dividends, tax adjustments, or transaction costs

\- Yahoo Finance APIs are unofficial and may change or rate-limit

\- Relies on a public CORS proxy for browser access





