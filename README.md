# MarketMind
A modular mult├── README.md                          # You are here
├── .env                              # Add your API keys here
├── Dockerfile                        # Docker configuration
├── requirements.txt                  # Python dependencies
├── architecture.png                  # System architecture diagram
├── gemini_cache.json                # Gemini API cache
├── new_re.txt                        # Additional notes
│
└── FinSight-Agents/                  # Main application directory
    ├── main.py                       # Main entry point
    ├── streamlit_app.py              # Streamlit frontend
    ├── gemini_cache.json             # Gemini API cacheework for generating real-time financial insights, sentiment analytics, and stock visualizations — built using Python, NLTK, Google Cloud, and Streamlit.

---

## What is MarketMind?

**MarketMind** is a multi-agent system designed to streamline the analysis of financial markets. It brings together live market data, news sentiment, and technical indicators to produce clear and actionable insights for Indian and global stocks.

This system operates asynchronously using a supervisor-agent architecture and is ideal for building intelligence into financial dashboards, research tools, or data science pipelines.

---

## Features

- Fetches live stock prices and trends
- Performs sentiment analysis on the latest news
- Produces visualizations like candlesticks, pie charts, and technical overlays
- Uses agents that collaborate and pass data to one another
- Automatically adapts if no data is available (graceful degradation)
- Built to run locally with optional cloud storage

---

## Project Structure

```
MarketMind/
├── README.md                          # 🔹 You are here
├── .env                              # 🔐 Add your API keys here
├── Dockerfile                        # 🐳 Docker configuration
├── requirements.txt                  # 📦 Python dependencies
├── architecture.png                  # 📈 System architecture diagram
├── gemini_cache.json                # 🗄️ Gemini API cache
├── new_re.txt                        # 📄 Additional notes
│
└── FinSight-Agents/                  # 🤖 Main application directory
    ├── main.py                       # 🚀 Main entry point
    ├── streamlit_app.py              # 🖥️ Streamlit frontend
    ├── gemini_cache.json             # �️ Gemini API cache
    │
    ├── agents/                       # Core agents
    │   ├── __init__.py
    │   ├── supervisor_agent.py       # Orchestrates other agents
    │   ├── market_data_agent.py      # Fetches stock data
    │   ├── sentiment_agent.py        # Analyzes news sentiment
    │   ├── insight_agent.py          # Generates insights
    │   └── visualization_agent.py    # Creates charts
    │
    ├── core/                         # Agent orchestration logic
    │   ├── __init__.py
    │   ├── agent_base.py             # Base agent class
    │   └── pipeline.py               # Agent pipeline
    │
    ├── utils/                        # Helper utilities
    │   ├── __init__.py
    │   ├── bigquery_helpers.py       # BigQuery operations
    │   ├── company_to_ticker.py      # Company name mapping
    │   ├── gemini_helpers.py         # Gemini AI helpers
    │   ├── news_fetcher.py           # News API integration
    │   ├── tickers_to_company.py     # Ticker mapping
    │   ├── vertexai_helpers.py       # Vertex AI utilities
    │   └── yfinance_helper.py        # Yahoo Finance API
    │
    ├── data/                         # Data storage
    │   ├── processed/                # Generated charts & CSVs
    │   │   ├── *.png                 # Chart images
    │   │   └── *.csv                 # Processed data
    │   └── schemas/                  # BigQuery schema definitions
    │       └── market_data.json      # Market data schema
    │
    ├── notebooks/                    # Jupyter notebooks & scripts
    │   ├── init_bigquery.py          # BigQuery initialization
    │   └── save_news_sample.py       # News data sample
    │
    └── tests/                        # Unit tests
        ├── __init__.py
        ├── test_agents.py            # Agent tests
        ├── test_sentiment_agent.py   # Sentiment analysis tests
        └── test_utils.py             # Utility tests
```

---

## Quickstart

### 1. Install Dependencies

From the root directory (`MarketMind/`):

```bash
cd FinSight-Agents
pip install -r requirements.txt
```

Also download required NLTK data:

```bash
python -c "import nltk; nltk.download('vader_lexicon')"
```

### 2. Add Your API Keys

In `MarketMind/`, create a `.env` file:

```env
NEWSAPI_KEY=your_newsapi_key_here
GEMINI_API_KEY=your_gemini_key_here
```

### 3. Set Up Google Cloud (Optional but recommended)

Authenticate and configure the project:

```bash
gcloud auth application-default login
gcloud config set project your-project-id
```

### 4. (Optional) Initialize Data

Run the data fetchers (only once):

```bash
python notebooks/init_bigquery.py
python notebooks/save_news_sample.py
```

### 5. Run the Agent Workflow

```bash
python main.py
```

This will execute the entire agent pipeline: fetching data, analyzing sentiment, generating insights, and saving output.

### 6. Launch the UI

```bash
streamlit run streamlit_app.py
```

Use this to explore company insights visually using the dashboard.

---

## Running Tests

To verify everything is working:

```bash
pytest tests/
```

---

## Built With

- **Python** (asyncio, pandas, requests)
- **NLTK + VADER** for sentiment analysis
- **yfinance** for stock prices
- **NewsAPI** for headlines
- **Streamlit** for web UI
- **Google Cloud BigQuery** (optional)
- **Matplotlib, Seaborn, mplfinance** for visualizations