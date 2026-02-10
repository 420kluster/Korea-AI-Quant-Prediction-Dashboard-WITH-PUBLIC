# Stock-AI: Hybrid Stock Prediction & Mock Investment Platform

### "High-performance Quant Assistant implemented with $0 server cost"

**Stock-AI** is a web dashboard designed to provide optimal investment information for the Korean stock market (KOSPI, KOSDAQ) by combining **Short-term Prediction (LightGBM)** and **Long-term Prediction (LSTM)** models.

It features an automated pipeline utilizing **GitHub Actions** and a mock investment function powered by **Supabase**.

---

## 🚀 Project Overview

This project moves beyond simple stock price prediction by employing a **'Hybrid Ensemble' strategy**. This approach applies distinct algorithms and datasets optimized for specific investment horizons (Short-term vs. Long-term).

### Key Goals
* **Cost Efficiency**: Achieved **$0 server maintenance cost** by utilizing GitHub Actions & Streamlit Cloud.
* **Dual-Model Engine**:
    * **Short-term**: LightGBM model focused on supply/demand, market psychology, and technical indicators (7-day / 14-day prediction).
    * **Long-term**: LSTM model focused on fundamentals, macroeconomics, and growth potential (1-year / 3-year prediction).
* **User Experience**: An interactive dashboard allowing users to directly select variables and verify results.

---

## 🏗 Architecture

| Component | Tech Stack | Role |
| :--- | :--- | :--- |
| **Data Collection** | FinanceDataReader, yfinance | Collection of stock price, supply/demand, and macro data |
| **Automation** | GitHub Actions | Nightly automated data crawling & preprocessing (Cron) |
| **Model Serving** | LightGBM, PyTorch (LSTM) | Model training and inference |
| **Database** | Supabase (PostgreSQL) | Storage for mock investment user data |
| **Frontend** | HTML/CSS | Web dashboard and visualization (Mobile Responsive) |

---

## 📊 Data Strategy

To maximize AI learning efficiency, customized datasets are constructed according to the time horizon.

### 1. Base Features (Common)
* **Price**: Open, High, Low, Close, Change (Fluctuation Rate)
* **Volume**: Volume, Volume_Z_Score (Outlier Score), Volume_Ratio
* **Calendar**: Day_of_Week effect, Is_Month_End effect
* **Macro**: Exchange Rate (USD/KRW), Oil Price (WTI), KOSPI 200 Index

### 2. Short-term Model Data (< 60 Days, LightGBM)
* **Focus**: Supply/Demand, Charts, Market Psychology
* **Technical**: MA 5/20, RSI, MACD, Bollinger Bands, Volatility, Disparity
* **Supply/Demand**: Foreign/Institutional Net Buy, Program Net Buy
* **Risk**: Credit Balance Ratio, Volatility Index (VIX)
* **Event**: MSCI Rebalancing D-Day

### 3. Long-term Model Data (> 60 Days, LSTM)
* **Focus**: Corporate Value (Fundamentals), Growth, Macroeconomics
* **Fundamental**: Revenue Growth, Operating Margin, ROE, Debt Ratio, PER, PBR (Ratios used; absolute values excluded)
* **Macro**: US 10Y Treasury Rate, KR-US Rate Differential, Dollar Index (DXY), Export YoY, Manufacturing PMI
* **Trend**: MA 60/120, Golden/Death Cross

---

## 📂 Directory Structure

```bash
Stock-AI/
├── .github/workflows/    # GitHub Actions automation scripts
├── data/                 # Collected data (csv)
├── models/               # Trained model files (pkl, pth)
├── src/
│   ├── collector.py      # Data collection code
│   ├── feature_eng.py    # Technical indicators & preprocessing logic
│   └── prediction.py     # Model prediction logic
├── Index.html            # Dashboard main file
├── requirements.txt      # Dependency list
└── README.md             # Project documentation
```

## Disclaimer

The information provided by this service is based on AI analysis of historical data. All investment decisions are the sole responsibility of the user. This service does not constitute investment advice or recommendation.

## Author

* **Developer:** 백야 Baekya (ID)
* **Contact:** [Your Email]@gmail.com
* **Blog/Portfolio:** https://finance-commander.netlify.app/