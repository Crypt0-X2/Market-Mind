# MarketMind

A modular multi-agent framework for generating real-ti    ├── streamlit_app.py              # Streamlit frontend
    ├── gemini_cache.json             # Gemini API cache financial insights, sentiment analytics, and stock visualizations — built using Python, NLTK, Google Cloud, and Streamlit.

---

## What is MarketMind?

**MarketMind** is an intelligent multi-agent system designed to streamline comprehensive financial market analysis. It orchestrates specialized AI agents that work collaboratively to fetch live market data, analyze news sentiment, generate actionable insights, and create compelling visualizations for both Indian and global stocks.

The system operates asynchronously using a supervisor-agent architecture, making it ideal for building intelligence into financial dashboards, research tools, algorithmic trading systems, or data science pipelines.

---

## Key Features

### Real-Time Market Data Processing
- **Live Stock Data**: Fetches real-time stock prices, volumes, and trading metrics using Yahoo Finance API
- **Multi-Market Support**: Supports both Indian stocks (NSE/BSE) and global markets (NASDAQ, NYSE, etc.)
- **Historical Analysis**: Retrieves historical price data for trend analysis and technical indicators
- **Data Persistence**: Optional BigQuery integration for storing and querying large-scale market data

### Advanced Sentiment Analysis
- **News Aggregation**: Pulls latest financial news from multiple sources including Bloomberg, Reuters, Economic Times, and more
- **VADER Sentiment Scoring**: Uses NLTK's VADER sentiment analyzer for accurate financial news sentiment classification
- **Company-Specific Analysis**: Maps stock tickers to company names for precise news filtering
- **Sentiment Trends**: Tracks sentiment changes over time to identify market mood shifts

### AI-Powered Insights Generation
- **Google Gemini Integration**: Leverages Google's Gemini AI for generating sophisticated investment insights
- **Divergence Detection**: Identifies discrepancies between price movements and sentiment signals
- **Risk Assessment**: Analyzes potential risks based on sentiment-price correlations
- **Investment Recommendations**: Provides Buy/Hold/Sell recommendations based on multi-factor analysis

### Comprehensive Visualizations
- **Candlestick Charts**: Professional OHLCV candlestick charts with technical overlays
- **Sentiment Distribution**: Interactive pie charts showing positive/negative/neutral sentiment ratios
- **Price-Volume Analysis**: Dual-axis charts correlating price movements with trading volumes
- **Trend Visualizations**: Line charts with moving averages and trend indicators

### Multi-Agent Architecture
- **Supervisor Agent**: Orchestrates workflow execution and manages inter-agent communication
- **Market Data Agent**: Specialized in fetching and processing stock market data
- **Sentiment Agent**: Handles news retrieval and sentiment analysis
- **Insight Agent**: Generates AI-powered investment insights and recommendations
- **Visualization Agent**: Creates charts, graphs, and visual analytics

### Production-Ready Features
- **Graceful Degradation**: Continues operation even when some data sources are unavailable
- **Caching System**: Intelligent caching for API responses to optimize performance and costs
- **Error Handling**: Robust retry mechanisms and error recovery
- **Scalable Design**: Modular architecture allows easy addition of new agents and data sources
- **Cloud Integration**: Built for deployment on Google Cloud Platform with BigQuery support

---

## Project Structure

```
MarketMind/
├── README.md                          # You are here
├── .env                              # Add your API keys here
├── Dockerfile                        # Docker configuration
├── requirements.txt                  # Python dependencies
├── architecture.png                  # System architecture diagram
├── gemini_cache.json                # Gemini API cache
├── new_re.txt                        # Additional notes
│
└── FinSight-Agents/                  # Main application directory
    ├── main.py                       # Main entry point
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

## How MarketMind Works

### Agent Workflow
MarketMind operates through a coordinated workflow of specialized agents:

1. **Supervisor Agent** initializes and orchestrates the entire analysis pipeline
2. **Market Data Agent** fetches real-time stock prices and historical data for specified companies
3. **Sentiment Agent** retrieves latest financial news and performs sentiment analysis using VADER
4. **Insight Agent** combines market data and sentiment to generate AI-powered investment insights
5. **Visualization Agent** creates charts and visual representations of the analysis

### Data Flow
```
Input: Company Names/Tickers
    ↓
Market Data Agent → Live Stock Prices, Volume, OHLC Data
    ↓
Sentiment Agent → Financial News + Sentiment Scores
    ↓
Insight Agent → AI Analysis + Investment Recommendations
    ↓
Visualization Agent → Charts, Graphs, Visual Analytics
    ↓
Output: Comprehensive Financial Report
```

### User Interfaces
- **Command Line**: Run `python main.py` for batch analysis and console output
- **Streamlit Web App**: Interactive dashboard with real-time charts and insights
- **Programmatic API**: Use individual agents in your own Python applications

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

## Use Cases & Applications

### Financial Professionals
- **Investment Research**: Automated analysis of multiple stocks with sentiment-driven insights
- **Risk Assessment**: Early detection of sentiment-price divergences indicating potential risks
- **Portfolio Management**: Real-time monitoring of holdings with news sentiment tracking
- **Market Analysis**: Comprehensive overview of market conditions across different sectors

### Algorithmic Trading
- **Signal Generation**: Combine technical indicators with sentiment signals for trading decisions
- **Backtesting**: Historical sentiment analysis for strategy validation
- **Risk Management**: Sentiment-based position sizing and risk adjustment
- **Market Screening**: Automated screening of stocks based on sentiment and price patterns

### Data Scientists & Developers
- **Financial ML Models**: Rich dataset generation for machine learning applications
- **Dashboard Development**: Pre-built components for financial applications
- **Research Tools**: Automated data collection and analysis for academic research
- **API Integration**: Modular agents for building custom financial applications

### Business Intelligence
- **Executive Dashboards**: Real-time market insights for decision makers
- **Competitor Analysis**: Track sentiment and performance of competitor stocks
- **Market Timing**: Identify optimal entry/exit points based on multi-factor analysis
- **Reporting Automation**: Automated generation of financial reports and insights

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