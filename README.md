<div align="center">

# ⚡ Joseph H. Long
### **Data & Analytics Engineer | MIS & Applied AI @ University of Delaware**

<br/>

[![Eval Platform](https://img.shields.io/badge/EVAL_PLATFORM-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://getstockeval.com)
[![LinkedIn Profile](https://img.shields.io/badge/LINKEDIN-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/josephlong1118)
[![Email Contact](https://img.shields.io/badge/EMAIL_ME-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:henryl@udel.edu)

</div>

---

<div align="center">
  <h2>NAVIGATE TO MODULE</h2>
  <p><i>Select a section below to jump directly to system specifications</i></p>

  [![System Architecture](https://img.shields.io/badge/System_Architecture-107C41?style=for-the-badge)](#system-architecture--infrastructure)
  [![Web App Breakdown](https://img.shields.io/badge/Web_App_Breakdown-0078D4?style=for-the-badge)](#full-website--web-application-breakdown)
  [![Scoring Model](https://img.shields.io/badge/Scoring_Model-5C2D91?style=for-the-badge)](#algorithmic-engine--scoring-methodology-099)
  [![Database Caching](https://img.shields.io/badge/Database_Caching-D83B01?style=for-the-badge)](#database-caching--throughput-scaling)
  [![Codebase](https://img.shields.io/badge/Codebase-00828A?style=for-the-badge)](#repository-directory--codebase)
</div>

---

## System Architecture & Infrastructure

> **Eval** ([getstockeval.com](https://getstockeval.com)) is a full-stack financial analytics engine engineered to evaluate equities on a normalized **0–99 Health Score** scale. It replaces financial data bloat with an actionable metric by processing SEC filings, fundamental balance sheets, income statements, cash flows, and price momentum vectors in real time through a dynamic multi-weighted algorithm.

```text
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                     CLIENT / PRESENTATION LAYER                                  │
│                 HTML5  •  CSS3 Grid System  •  Vanilla JS (ES6+)  •  Vercel Edge                   │
└─────────────────────────────────────────────────┬────────────────────────────────────────────────┘
                                                  │ REST APIs / JSON Streams
┌─────────────────────────────────────────────────▼────────────────────────────────────────────────┐
│                                     API & APPLICATION BACKEND                                    │
│             Node.js Runtime  •  Render Container  •  Async Microservices Gateway                  │
└─────────────────────────────────────────────────┬────────────────────────────────────────────────┘
                                                  │ Queries & Aggregations
┌─────────────────────────────────────────────────▼────────────────────────────────────────────────┐
│                                     DATA & AI PIPELINE LAYER                                     │
│          Custom SQL Relational Caching Engine  •  Python ETL Pipeline  •  OpenAI API             │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
