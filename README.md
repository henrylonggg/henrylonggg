<div align="center">

# ⚡ Joseph H. Long
### **B.S. MIS & Applied AI @ University of Delaware**

<br/>

[![Eval Platform](https://img.shields.io/badge/EVAL_PLATFORM-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://getstockeval.com)
[![LinkedIn Profile](https://img.shields.io/badge/LINKEDIN-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/josephlong1118)
[![Email Contact](https://img.shields.io/badge/EMAIL_ME-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:henryl@udel.edu)

<br/>

<p align="center">
  <img src="https://img.shields.io/badge/SQL-CC292B?style=for-the-badge&logo=microsoftsqlserver&logoColor=white" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" />
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" />
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" />
  <img src="https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white" />
  <img src="https://img.shields.io/badge/Render-46E3B7?style=for-the-badge&logo=render&logoColor=black" />
</p>

</div>

---

<div align="center">
  <h2>🧭 QUICK PLATFORM NAVIGATION</h2>
  <p><i>Click any button below to inspect system specifications & architecture</i></p>

  [![System Architecture](https://img.shields.io/badge/01__Architecture-107C41?style=for-the-badge)](#1-system-architecture--infrastructure)
  [![App Breakdown](https://img.shields.io/badge/02__Web_App_Breakdown-0078D4?style=for-the-badge)](#2-full-website--web-application-breakdown)
  [![Scoring Model](https://img.shields.io/badge/03__Scoring_Model-5C2D91?style=for-the-badge)](#3-algorithmic-engine--scoring-methodology-099)
  [![Database Architecture](https://img.shields.io/badge/04__Database_Caching-D83B01?style=for-the-badge)](#4-database-caching--throughput-scaling)
  [![Code Repositories](https://img.shields.io/badge/05__Codebase-00828A?style=for-the-badge)](#5-repository-directory--codebase)
</div>

---

<a id="1-system-architecture--infrastructure"></a>
## 🚀 Featured Production System: **Eval (Stock Evaluator Engine)**

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
