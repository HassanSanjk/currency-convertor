# Currency Exchange Dashboard

A web-based currency converter built with Flask that combines official exchange rates with real-world Sudan parallel market data. The system is designed to address discrepancies between official SDG rates and actual market values.

---

## Live Demo

https://currency-dashboard-yqzr.onrender.com

---

## Features

- Convert between multiple currencies using official exchange-rate APIs  
- Special handling for SDG using real-world parallel market rates  
- USD used as an intermediate currency for accurate cross-currency conversion (e.g. EUR → SDG)  
- Live USD/SDG rate scraped from Alsoug (alsoug.com)  
- MySQL caching system to reduce repeated API calls  
- Displays data status (Live / Cached) and last updated timestamps  
- Simple, responsive UI built with Bootstrap  

---

## Tech Stack

- **Backend:** Python (Flask)  
- **Database:** MySQL  
- **Frontend:** HTML, CSS, Bootstrap, Jinja2  
- **Data Sources:** Exchange Rate API, Alsoug (web scraping with BeautifulSoup)  

---

## How It Works

- Official rates are fetched from an external API  
- For SDG:
  - The system retrieves the USD → SDG market rate from Alsoug  
  - Uses USD as a bridge to calculate conversions involving SDG  
- Results are cached in MySQL with timestamps  
- Cached data is reused within a time window to reduce external requests  

---

## Project Structure


project/
│
├── app.py
├── config.py
├── db.py
├── services/
│ ├── official_rates.py
│ └── market_rates.py
├── templates/
├── static/
└── .env


---

## Running Locally

### 1. Clone the repository

```bash
git clone https://github.com/your-username/currency-exchange-dashboard.git
cd currency-exchange-dashboard
2. Install dependencies
pip install -r requirements.txt
3. Set environment variables

Create a .env file:

SECRET_KEY=your_secret_key
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=currency_exchange_dashboard
CURRENCYAPI_KEY=your_api_key
ALSOUG_URL=https://www.alsoug.com

4. Run the app
python app.py
Notes
The parallel SDG rate is based on publicly available listings and may vary
Official API rates may not reflect real-world SDG value
The caching layer helps reduce API calls and improve response time
Future Improvements
Support for additional market-based currencies
Historical rate tracking and charts
User watchlist for selected currencies
Auto-detection of user timezone