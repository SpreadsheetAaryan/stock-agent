# Stock Assistant Agent

## Project Overview

This project is a sophisticated AI-powered stock market assistant designed to provide users with instant, in-depth financial analysis and market insights directly through a natural language interface. Built with a robust, modular workflow architecture, this agent demonstrates an advanced application of large language models (LLMs) and API integrations to deliver real-time, data-driven financial information.

This project showcases a deep understanding of:

* **Workflow Automation:** Building complex, interconnected processes to handle diverse user requests.

* **API Integration:** Seamlessly fetching financial data, news, and AI model outputs from multiple external services.

* **Natural Language Processing:** Using a Google Gemini-powered agent to interpret user queries and dynamically route them to the appropriate workflow.

* **Structured Data Handling:** Processing and presenting complex financial data in a clear, actionable format.

## Core Features

The agent interprets user commands from a platform like Telegram and can perform the following actions:

* **Quick Analysis:** Provides a rapid, concise overview of a stock's near-term outlook.

* **In-Depth Report:** Generates a comprehensive, long-term investment report for a company.

* **Company Research:** Offers historical context and details on a company's business model.

* **Visualizations:** Creates a price and RSI chart for a stock over a specified period.

* **Market News Rundown:** Summarizes the latest market headlines and trends.

* **Customized News Search:** Filters news by company, topic, and timeframe.

---

## Workflow Breakdown

Each feature is powered by a dedicated subworkflow, ensuring modularity and maintainability. Below is a description of each workflow and an example of the structured output it provides.

### 1. Basic Analysis

This workflow is triggered for a quick, short-term stock analysis. It pulls recent price data, financial statements, and news to provide a snapshot of the company's performance, along with a simple investment rating.

**Trigger Phrases:**
`basic analysis`, `quick analysis`, `short outlook`, `analyze [ticker]`

**Example Output:**

Company: Apple Inc. (AAPL)
BSH: BUY
Investment Rating: 9/10
Risk Rating: 3/10
Next Month Outlook: POSITIVE
Next Quarter Outlook: POSITIVE
Next Year Outlook: POSITIVE


### 2. Deep Analysis

This comprehensive workflow is designed for a thorough, investor-focused report. It utilizes extended financial data, valuation models, and deep technical indicators to provide a detailed outlook over a 5-year period, along with a detailed risk assessment.

**Trigger Phrases:**
`deep analysis`, `long-term analysis`, `comprehensive report`, `5-year outlook`

**Example Output:**

Company: Apple Inc. (AAPL)

1 Quarter Outlook: The stock has shown strong upward momentum over the last three months, and after a recent period of consolidation, technical patterns suggest a potential continuation of this trend. However, the stock may experience some volatility due to its recent rapid price increase and the historical tendency for "sell-the-news" reactions to upcoming product announcements.

1 Year Outlook: The company's one-year performance will depend on its ability to meet the market's high growth expectations, largely driven by the integration of AI to spur an iPhone upgrade cycle and continued expansion of its services revenue. While the financials are incredibly strong, the stock's current high valuation suggests that strong execution is already priced in and required for further significant gains.

5 Year Outlook: Long-term growth will likely be fueled by the company's expansion into new product categories like augmented reality, the continued growth of its high-margin services and wearables divisions, and its powerful, loyal ecosystem. Apple's immense free cash flow provides the capital for both sustained innovation and shareholder returns, positioning it well for continued market leadership.

Risk Rating: 4/10. Apple's primary risks stem from its high valuation, which makes the stock susceptible to pullbacks if growth expectations are not met. Additional risks include ongoing geopolitical tensions affecting its global supply chain, increasing regulatory scrutiny over its App Store and market power, and the constant pressure to innovate against intense competition in the technology sector.

Long Term Investment Rating: 9/10. Apple remains a premier long-term investment due to its unparalleled brand strength, entrenched ecosystem creating high switching costs, and phenomenal financial health characterized by massive free cash flow generation. The company's consistent ability to grow its high-margin Services division while investing in future technologies provides a durable model for creating shareholder value through both growth and substantial capital return programs.


### 3. Learn

This workflow serves as an educational tool, providing a concise history and a clear explanation of a company's business model. It is perfect for users who want to understand a company's fundamentals before diving into financial metrics.

**Trigger Phrases:**
`learn about [company/ticker]`, `what is [ticker]?`, `company history`, `business model of [company]`

**Example Output:**

Company: Apple Inc. (AAPL)

History: Apple Inc. was founded by Steve Jobs, Steve Wozniak, and Ronald Wayne on April 1, 1976, to develop and sell personal computers, most notably the Apple I and Apple II. The company was incorporated as Apple Computer, Inc. in 1977. Early challenges included intense competition in the nascent personal computer market, particularly from IBM, and internal struggles that led to Steve Jobs' departure in 1985. However, early growth opportunities stemmed from the burgeoning demand for personal computing and Apple's focus on user-friendly interfaces, which helped them establish a foothold in homes and schools.

Business Model: Apple's business model today centers on an ecosystem strategy, integrating hardware, software, and services to create a seamless user experience that encourages customer loyalty and drives recurring revenue. They primarily make money through the sale of their iconic consumer electronics, such as the iPhone, Mac computers, iPad tablets, Apple Watch, and AirPods, which are often sold at premium price points reflecting their brand, design, and performance. A significant and growing portion of their revenue comes from their Services segment; this includes commissions from App Store sales, subscriptions to Apple Music, Apple TV+, Apple Arcade, and iCloud storage, as well as revenue from Apple Pay and AppleCare extended warranties. By owning both the devices and the platforms they run on, Apple captures value from both the initial purchase of hardware and the ongoing engagement with its digital services and content.


### 4. Visualizations

This workflow generates a visual chart of a stock's price and RSI (Relative Strength Index) over a user-specified number of days. It's a key feature for users who prefer to analyze trends and momentum visually.

**Trigger Phrases:**
`chart of [ticker]`, `graph for [ticker]`, `show me [ticker] over 30 days`

**Example Output:**

stock chart showing the price over the specified time and RSI values during the specified time


*Note: The agent would actually send an image file of the chart.*

### 5. Rundown

The Rundown workflow provides a daily market news summary. It analyzes the sentiment of recent articles to give the user a quick overview of today’s market activity without focusing on a single stock.

**Trigger Phrases:**
`daily news`, `market news`, `today’s stock market updates`, `market rundown`

**Example Output:**

This is an example of one of the articles the bot would give: Title: Synaptigen Probiotic Brain Formula Now Available as Company Launches Memory Support Supplements with Non-Stimulant Design and Transparent Ingredient Disclosure

Sentiment Value: Bullish

Summary of article: A new company has launched Synaptigen, a probiotic brain health supplement, emphasizing its non-stimulant and transparent formula. This product launch represents an entry into the growing cognitive health and supplement market, which could generate positive business momentum for the new company and reflects ongoing consumer interest in the wellness sector.


### 6. Customized News

This is an advanced news search workflow that allows users to filter news articles by a specific company, topic, and timeframe. It showcases the ability to handle complex, multi-parameter queries.

**Trigger Phrases:**
`Show me Tesla earnings news`, `Give me news about Apple mergers in the past 10 days`

**Example Output:**

Here is an example of one article: News on AAPL:

Title: Best Stock to Buy Now: Alphabet or Apple?
Sentiment Value: Bullish
Summary of article: This article positions Apple as a prominent big tech stock, comparing it with Alphabet. The discussion implies Apple's strong standing in the market and its consideration as a top investment choice, contributing to a positive sentiment for its stock.


---

## Technical Architecture

This project leverages the following technologies to create a scalable and powerful agent:

* **n8n:** The core of the project. n8n is an open-source workflow automation tool that orchestrates all the tasks. The agent logic, API calls, and data processing are all defined within n8n workflows, which provides a visual, modular, and easy-to-manage architecture.

* **Google Gemini API:** Serves as the brain of the agent. The Gemini API is used to power the primary `Stock Market Agent` node, which interprets the user's natural language request and intelligently decides which subworkflow (or "tool") to execute.

* **Telegram API:** This is the user-facing platform. The `Telegram Trigger` node listens for incoming messages, and the `Telegram` node sends responses back to the user, creating a seamless chat experience.

* **Financial & Search APIs:** These are integrated into the subworkflows to fetch real-time financial data (e.g., from Alpha Vantage) and news articles (e.g., via a custom search API). The use of these APIs demonstrates the ability to integrate with third-party data providers.

## Setup and Installation

To run this project, you will need to set up an n8n instance and configure the necessary API keys.

1.  **Clone the Project:**
    Download the JSON files provided.

2.  **Configure Environment Variables:**
    Create a `.env` file based on the provided `env.example` file.

    ```
    # ===============================
    # 📈 Stock Assistant Agent - Env
    # ===============================
    
    # 🔹 Telegram Bot
    TELEGRAM_API_KEY=your_telegram_api_key_here
    
    # 🔹 Google Gemini (PaLM API)
    GEMINI_API_KEY=your_gemini_api_key_here
    
    # 🔹 Financial Data API (e.g. Alpha Vantage / Benzinga)
    FINANCIAL_API_KEY=your_financial_api_key_here
    
    
    ```

3.  **Import Workflows into n8n:**
    Import the main and subworkflow JSON files into your n8n instance.

4.  **Connect Credentials:**
    Update the credential nodes within the n8n workflows to use the environment variables from your `.env` file.

## Future Enhancements

* **Real-time Stock Alerts:** Implement triggers to notify users of significant price movements or breaking news for their tracked stocks.

* **Interactive Charts:** Integrate a more advanced charting library to allow users to interact with the visualizations (e.g., zoom, pan, add indicators).

* **Portfolio Management:** Add functionality to track a user's portfolio, providing summaries of overall performance and tailored insights.

* **Multi-Platform Support:** Expand the agent to support other chat platforms like Slack or Discord.
