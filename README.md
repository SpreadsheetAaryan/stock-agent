# Telegram Stock Assistant Agent

A Telegram chatbot for stock questions, built as a set of [n8n](https://n8n.io/) workflows. A Gemini-powered n8n agent reads each message, keeps a short conversation memory, and calls one of six sub-workflows as a tool. The result comes back as a Telegram message or chart image.

Built in September 2025. These are exported workflow JSON files plus a screenshot of each, not a standalone app.

## Workflows

| Workflow | What it does | Data sources |
|---|---|---|
| `headworkflow` | Telegram trigger, Gemini chat model with window memory, agent that routes to the tools below, Telegram reply | Telegram, Gemini |
| `basic_analysis` | Short-term outlook for a ticker: buy/sell/hold, investment and risk ratings, 1-month/quarter/year outlook | price script, Google Custom Search, Gemini |
| `deep_analysis` | Longer report with a five-year outlook and risk assessment | price script, Google Custom Search, Gemini |
| `learn` | Background on a company or a finance concept | Gemini |
| `visualizations` | Price and RSI chart for a ticker over N days, sent as an image | chart script |
| `rundown` | Summary of the day's market news with sentiment | Alpha Vantage News Sentiment, Gemini |
| `customized_news` | News filtered by ticker, topic and time window | Alpha Vantage News Sentiment, Gemini |

Each workflow folder has a `*_picture.png` of the n8n canvas.

## Running it

1. Run n8n (self-hosted, for example in Docker).
2. Set these environment variables for n8n: `TELEGRAM_API_KEY`, `GEMINI_API_KEY`, `FINANCIAL_API_KEY` (Alpha Vantage). The Google Custom Search node also needs a search engine ID (`cx`).
3. Import the six files in `subworkflows/`, then `headworkflow/headworkflow.json`, and point each tool node at the matching sub-workflow.

**Not included:** the price, chart and date helper scripts (`get_stock_data.py`, `get_chart.py`, `one_day.py`) that the workflows call from `/home/node/n8n_scripts/` are not in this repo, so the analysis, chart and news workflows will not run as-is.

The ratings come from an LLM reading recent prices and news. They are not tested predictions and are not investment advice.
