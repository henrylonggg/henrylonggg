<div align="center">

# **Henry Long**
### **B.S. MIS & Applied AI @ University of Delaware**

<br/>

<a href="https://getstockeval.com" target="_blank">
  <img src="https://img.shields.io/badge/Eval_Platform-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Eval Platform" />
</a>
<a href="https://www.linkedin.com/in/josephlong1118" target="_blank">
  <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn Profile" />
</a>
<a href="mailto:henryl@udel.edu">
  <img src="https://img.shields.io/badge/Email_Me-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email Contact" />
</a>

</div>

---

## Overview & Live Application

### What is **Eval**?
**Eval** ([getstockeval.com](https://getstockeval.com)) is a full-stack financial analytics web app built with **Node.js, Express, React (JSX), SQL, Clerk, and OpenAI**. Instead of making users comb through messy financial statements and noisy market news, **Eval** pulls raw market data and summarizes it into a clear **0–99 Stock Score** using 40+ key metrics.

### Key System Capabilities
- **Fast Global Frontend:** Built with React (JSX) and hosted on **Vercel** for fast page loads worldwide under 100ms. Backend runs on **Render** using Express and WebSockets.
- **Secure Authentication & Profiles:** Integrates **Clerk** authentication to handle user sign-ins, encrypt personal data, protect user sessions, and power customizable user profiles.
- **Custom Navigation & Access:** Features a responsive navigation bar with intuitive drop-down menus for seamless routing across platform modules, **Support & Contact**, and **Terms & Conditions**.
- **Overnight Data Pipeline (100x Scale):** An automated background job fetches data for **1 stock per minute over 10 hours** (600 stocks/night). This **cuts third-party API costs by 99%** and scales support from 5 users to thousands at once.
- **Smart Database Caching:** Stores financial data in a PostgreSQL database (Supabase), keeping existing numbers and updating changed metrics. Every stock gets updated at least once a week.
- **Accurate AI Assistant:** Integrates OpenAI models directly with structured SQL tables, letting users ask natural language questions with zero hallucination.
- **CSV Portfolio Parser:** Lets users upload trade files to track profit/loss (realized/unrealized P&L) and calculate a total portfolio health score.

---

## Codebase Architecture

| Layer | Environment | Tech Stack | Responsibilities |
| :--- | :--- | :--- | :--- |
| **Frontend UI & Nav** | Vercel | JavaScript (JSX), HTML5, CSS3 | • `main.jsx`: UI state management, rendering, custom navigation bar & dropdown menus.<br/>• `styles.css`: Responsive layouts, score badge colors, dynamic nav menus. |
| **Auth & Security** | Clerk Cloud | Clerk SDK, JWT | • Handles secure multi-tenant sign-in/up, user data encryption, session tokens, and customizable user profile management. |
| **Backend API** | Render | Node.js, Express | • `server.js`: REST API routes, request validation, session checks, CORS management.<br/>• `index.js`: Backend entry point & service orchestration. |
| **Real-Time Data** | Render | Node.js, WebSockets | • `websock.js`: WebSockets for real-time live metric updates. |
| **Scoring Engine** | Node.js Server | JavaScript | • `score.js`: Calculates the 0–99 score using weighted averages across 40+ metrics in 6 core categories. |
| **Database & Cache** | Supabase | SQL (PostgreSQL) | Stores historical SEC metrics, user settings, schema setup, and runs the 10-hour overnight batch script. |
| **AI Integration** | Render & Node | JavaScript, OpenAI API | Injects structured SQL database tables directly into AI prompts to prevent hallucination. |
| **Setup & Config** | Runtime | NPM | • `package.json`: Project dependencies and scripts.<br/>• `.env`: Secure credentials (Clerk keys, API credentials, database URIs). |

---

## Core Platform Features

| Feature Module | UI Element | System Capabilities |
| :--- | :--- | :--- |
| **Navigation & Header** | **Custom Nav Bar & Dropdowns** | • Dynamic navigation header with responsive dropdown menus.<br/>• Direct routing to platform tools, customizable user settings, **Support & Contact**, and legal **Terms & Conditions**. |
| **User Identity & Security** | **Clerk Profile & Auth** | • Enterprise-grade user authentication and data encryption via **Clerk**.<br/>• Customizable user profiles, secure account settings, and protected session states. |
| **Stock Evaluation Engine** | **0–99 Score Dashboard** | • Fast ticker search across thousands of stocks.<br/>• Color-coded badges: **Green** (Healthy), **Yellow** (Fine), **Red** (Unhealthy).<br/>• Quantitative 0–99 score based on weighted averages of 40+ metrics.<br/>• Dropdown accordions showing breakdowns for every metric. |
| **AI Financial Assistant** | **"Ask Eval" Chat** | • Natural-language chat interface powered by OpenAI.<br/>• Queries local SQL tables for factual, zero-hallucination stock answers. |
| **Portfolio Analyzer** | **CSV File Parser** | • Upload trade logs (Ticker, Buy/Sell action, Quantity, Purchase Price).<br/>• Computes tax-lot P&L and overall weighted portfolio score.<br/>• Visualizes sector concentration and asset breakdown. |
| **Stock Comparison** | **Side-by-Side Matrix** | • Compare multiple stocks against industry peers.<br/>• Highlights key differences in profitability, debt, and valuation. |
| **Market Intelligence** | **News Sentiment** | • Real-time market headline sentiment tracking.<br/>• Tracks buying vs. selling trends and price momentum updates. |

---

## Database Architecture & Scaling

Calling external APIs on every search limits capacity to **~5 active users** before hitting strict rate limits. **Eval** solves this with an offline batching layer:

```text
               [ THIRDPARTY FINANCIAL API ]
                            │
                            ▼ (Automated 10-Hour Overnight Pipeline)
                            │ Fetches 1 stock / minute (600 stocks / night)
                            │
              ┌─────────────┴─────────────┐
              │  SQL DATABASE CACHE LAYER │
              └─────────────┬─────────────┘
                            │
                            ├─► Unchanged Data: Kept in database cache
                            ├─► Updated Data: Overwritten with fresh metrics
                            └─► Full Library: 100% updated weekly (~3,500 stocks)
                            │
                            ▼ (Serves thousands of concurrent users instantly)
                     [ CLIENTS & UI ]
