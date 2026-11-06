<div align="center">

# Joseph H. Long
### **B.S. MIS & Applied AI @ University of Delaware**

<br/>

[![Eval Platform](https://img.shields.io/badge/EVAL_PLATFORM-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://getstockeval.com)
[![LinkedIn Profile](https://img.shields.io/badge/LINKEDIN-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/josephlong1118)
[![Email Contact](https://img.shields.io/badge/EMAIL_ME-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:henryl@udel.edu)

</div>

---

## Breakdown & Live Application Overview

### What is **Eval**?
**Eval** ([getstockeval.com](https://getstockeval.com)) is a full-stack financial analytics platform engineered using **JavaScript (Node.js, JSX), HTML5, CSS3, SQL, and OpenAI**. Instead of forcing users to analyze overwhelming financial statements, and noisy market feeds across multiple platforms, **Eval** ingests raw fundamental data from third-party financial data providers to generate a single, normalized **0–99 Stock Evaluation Score** across 40+ distinct metrics.

### Production System & Architectural Capabilities
* **Auto-Scaling Cloud System:** Frontend built with JSX and custom CSS hosted on the **Vercel** for sub-100ms global delivery; backend microservices running on **Render** powered by Node.js, Express, and WebSockets.
* **Overnight Batching & 100x Scaling:** Features an automated backend ingestion engine that fetches data for **1 stock per minute over a 10-hour overnight window** (600 stocks/night). **Reduces third-party API costs by 99% while boosting platform throughput capacity from 5 concurrent users to thousands of simultaneous sessions.**
* **Smart Delta Caching:** Retains unchanged fundamental statement data in a relational SQL database while overwriting updated metrics. Every tracked stock is guaranteed a complete refresh at least once per week.
* **Conversational AI Assistant:** Integrates OpenAI API models directly with cached SQL relational tables to deliver context-aware, on-demand financial analysis without LLM hallucinations.
* **.CSV Portfolio Engine:** Ingests raw brokerage trade execution logs to calculate realized/unrealized P&L alongside an overall capital-weighted portfolio health score.

---

## Codebase Architecture

| Architectural Layer | Target Environment | Core Technology | File Modules & Responsibilities |
| :--- | :--- | :--- | :--- |
| **Frontend Presentation** | Vercel | JavaScript (JSX), HTML5, CSS3 | • `main.jsx`: Core UI state management, rendering, search autocompletion.<br/>• `styles.css`: Responsive layout, custom styling, dynamic score badge color styling. |
| **Backend API Gateway** | Render | Node.js Runtime, Express | • `server.js`: REST API routing, request validation, CORS management.<br/>• `index.js`: Main backend entry point & microservice orchestration. |
| **Real-Time Streaming** | Render | Node.js, WebSockets | • `websock.js`: WebSocket communication layer for real-time client metric updates and live data feeds. |
| **Scoring Algorithm** | Node.js Server | JavaScript | • `score.js`: Quantitative scoring model evaluating 40+ financial indicators across 6 core categories to output the 0–99ovr stock evaluation score. |
| **Data & Caching Engine** | Supabase | SQL (PostgreSQL Architecture) | Database schema handling stored historical SEC metrics, third-party financial data source, indexing, and the 10-hour overnight batch ingestion script. |
| **AI Intelligence** | Render & Node | JavaScript, OpenAI API | Prompt injection module passing pre-cached SQL tables to LLM models for hallucination-free user queries. |
| **Project Setup & Environment** | Environment & Runtime | Node Package Manager | • `package.json`: Dependency manifests and execution scripts.<br/>• `.env`: Secure environment key configuration (API credentials, database strings). |

---

## Comprehensive Platform Modules

| Platform Module | Core UI Feature | Key Technical & Operational Capabilities |
| :--- | :--- | :--- |
| **Stock Evaluation Engine** | **0–99 Score Dashboard** | • Real-time debounced ticker search across thousands of equities.<br/>• Color-coded health badges (*Critical*, *Neutral*, *Exceptional*).<br/>• Expandable accordion menus exposing underlying metrics per category. |
| **Conversational Intelligence** | **"Ask Eval" AI Assistant** | • Natural language financial query interface powered by OpenAI API.<br/>• Contextual prompt injection pulling structured financial tables straight from local SQL cache.<br/>• Answers complex valuation & momentum prompts with zero hallucination. |
| **Portfolio Health Analyzer** | **Batch .CSV Parser** | • Upload raw trade execution logs (Buys, Sells, Execution Prices).<br/>• Calculates tax-lot accounting (realized/unrealized P&L).<br/>• Computes a capital-weighted **Composite Portfolio Evaluation Score**.<br/>• Sector risk concentration & asset allocation breakdown. |
| **Side-by-Side Equities** | **Stock Comparison Tool** | • Head-to-head comparison matrix for two or more target tickers.<br/>• Normalizes financial ratios across industry-specific peer benchmarks.<br/>• Highlights category win/loss differentials (e.g., Margin efficiency vs. Leverage). |
| **Market Intelligence** | **News Sentiment** | • Real-time financial headline ingestion & sentiment scoring.<br/>• Identifies institutional accumulation vs. retail distribution trends.<br/>• Correlates headline shifts with short-term price momentum. |

---

## Database Architecture & Throughput Scaling

Connecting client UI searches directly to third-party financial APIs restricts system capacity to roughly **5 concurrent users** before hitting rate limits or high vendor costs. **Eval** bypasses this limitation with an offline batching caching layer:

```text
               [ THIRDPARTY FINANCIAL API ]
                            │
                            ▼ (Automated 10-Hour Overnight Batching Pipeline)
                            │ Pulls 1 stock / minute (600 stocks / night)
                            │
              ┌─────────────┴─────────────┐
              │  SQL DATABASE CACHE LAYER │
              └─────────────┬─────────────┘
                            │
                            ├─► Unchanged Data: Retained & Cached
                            ├─► Changed Metrics: Overwritten & Refreshed
                            └─► Full Catalog: 100% Refreshed Min. 1x / Week (~3500 U.S stocks up-to-date scores every week)
                            │
                            ▼ (Serves thousands of concurrent users instantly)
                     [ CLIENTS & UI ]
