# MarketMind 🧠📊  
A modular multi-agent framework for generating real-time financial insights, sentiment analytics, and stock visualizations — built using Python, NLTK, Google Cloud, and Streamlit.

---

## 🔍 What is MarketMind?

**MarketMind** is a multi-agent system designed to streamline the analysis of financial markets. It brings together live market data, news sentiment, and technical indicators to produce clear and actionable insights for Indian and global stocks.

This system operates asynchronously using a supervisor-agent architecture and is ideal for building intelligence into financial dashboards, research tools, or data science pipelines.

---

## ⚙️ Features

- 📈 Fetches live stock prices and trends
- 🗞️ Performs sentiment analysis on the latest news
- 📊 Produces visualizations like candlesticks, pie charts, and technical overlays
- 🧠 Uses agents that collaborate and pass data to one another
- 💡 Automatically adapts if no data is available (graceful degradation)
- 🔧 Built to run locally with optional cloud storage

---

## 📁 Project Structure

Your cloned project should look like this:

MarketMind/
├── README.md # 🔹 You are here
├── .env # 🔐 Add your API keys here
└── FinSight-Agents/
├── main.py # 🚀 Main entry point
├── streamlit_app.py # 🖥️ Streamlit frontend
├── requirements.txt # 📦 Python dependencies
│
├── agents/ # 🤖 Core agents
│ ├── supervisor_agent.py
│ ├── market_data_agent.py
│ ├── sentiment_agent.py
│ ├── insight_agent.py
│ └── visualization_agent.py
│
├── core/ # 🔧 Agent orchestration logic
├── utils/ # 🧰 BigQuery, yfinance, news helpers
├── data/
│ ├── processed/ # 📊 Charts, output CSVs
│ └── schemas/ # 🧾 BigQuery schema definitions
├── notebooks/
│ ├── init_bigquery.py # (Optional) Fetch and store data
│ └── save_news_sample.py
└── tests/ # ✅ Unit tests

yaml
Copy
Edit

---

## 🚀 Quickstart

### 1. 📦 Install Dependencies

From the root directory (`MarketMind/`):

```bash
cd FinSight-Agents
pip install -r requirements.txt
Also download required NLTK data:

bash
Copy
Edit
python -c "import nltk; nltk.download('vader_lexicon')"
2. 🔐 Add Your API Keys
In MarketMind/, create a .env file:

env
Copy
Edit
NEWSAPI_KEY=your_newsapi_key_here
GEMINI_API_KEY=your_gemini_key_here
3. ☁️ Set Up Google Cloud (Optional but recommended)
Authenticate and configure the project:

bash
Copy
Edit
gcloud auth application-default login
gcloud config set project your-project-id
4. 💾 (Optional) Initialize Data
Run the data fetchers (only once):

bash
Copy
Edit
python notebooks/init_bigquery.py
python notebooks/save_news_sample.py
5. 🧠 Run the Agent Workflow
bash
Copy
Edit
python main.py
This will execute the entire agent pipeline: fetching data, analyzing sentiment, generating insights, and saving output.

6. 🖼️ Launch the UI
bash
Copy
Edit
streamlit run streamlit_app.py
Use this to explore company insights visually using the dashboard.

🧪 Running Tests
To verify everything is working:

bash
Copy
Edit
pytest tests/
🛠️ Built With
Python (asyncio, pandas, requests)

NLTK + VADER for sentiment analysis

yfinance for stock prices

NewsAPI for headlines

Streamlit for web UI

Google Cloud BigQuery (optional)

Matplotlib, Seaborn, mplfinance for visualizations