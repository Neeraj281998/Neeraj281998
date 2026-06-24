# 💫 About Me

Backend Engineer (2 yrs production) + AI Researcher (1 yr MSc — Dublin City University).

I build things that ship: 10+ Spring Boot microservices in production, a production LLM agent (QuerySense) that achieved 98.8% query latency reduction, and an ETL pipeline that cut a 24-hour manual reporting process down to under 5 minutes.

My work sits at the intersection of backend systems and applied AI — I care about systems that are reliable, measurable, and actually deployed. Not demos.

Currently seeking **Backend / AI Engineer roles** — Dublin, United Kingdom, or across Europe.

---

## 🌐 Connect With Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/neeraj-prasad-944422202/)
[![Portfolio](https://img.shields.io/badge/Portfolio-%23000000.svg?logo=firefox&logoColor=white)](https://neeraj281998.github.io/)
[![LeetCode](https://img.shields.io/badge/LeetCode-%23FFA116.svg?logo=leetcode&logoColor=white)](https://leetcode.com/u/Neeraj281998/)

---

## 💻 Tech Stack

### Languages
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=java&logoColor=white)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![SQL](https://img.shields.io/badge/SQL-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)

### Frameworks & Tools
![Spring Boot](https://img.shields.io/badge/Spring_Boot-F2F4F9?style=for-the-badge&logo=spring-boot)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

### AI & LLMs
![Claude API](https://img.shields.io/badge/Claude_API-CC785C?style=for-the-badge)
![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-%23D00000.svg?style=for-the-badge&logo=Keras&logoColor=white)

### Databases
![PostgreSQL](https://img.shields.io/badge/postgresql-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/mysql-%2300f.svg?style=for-the-badge&logo=mysql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white)

---

## 🏆 GitHub Trophies
![](https://github-profile-trophy.vercel.app/?username=Neeraj281998&theme=tokyonight&no-frame=false&no-bg=false&margin-w=4)

---

## 💼 Professional Experience

### Software Engineer — AlignBits LLC
**Mar 2023 – Aug 2024** *(Promoted from Intern)*

- Replaced a fragile monolith with **10 independent Spring Boot microservices** using event-driven architecture (AWS SQS/SNS). Teams deployed features in parallel without coordination; release cycle dropped from **3 days → 4 hours**.
- Analytics dashboards were timing out at **P95 12s**. Added strategic composite indexes and refactored N+1 queries; latency dropped to **800ms**. Dashboard errors dropped to zero.
- BI team spent **3 hours daily** exporting ad metrics from Meta and Instagram into CSVs manually. Built async ETL pipeline (FastAPI + Celery) syncing data every 15 minutes. Reporting latency dropped from **24 hours → under 5 minutes**.
- Implemented AWS health checks, auto-scaling policies, and CloudWatch dashboards. System uptime improved from **97.5% → 99.8%**; on-call incidents dropped from **5/month → 1/month**.
- Designed event-driven backend workflows using AWS SQS/SNS; downstream services reacted autonomously to upstream state changes, reducing manual intervention to zero.
- Conducted code reviews across 10 services; standardised error handling and added circuit breakers. Customer-facing errors dropped **60%**; cascading failures eliminated.

---

### Software Engineer Intern — AlignBits LLC
**Jan 2023 – Feb 2023**

- Optimised Spring Boot REST APIs reducing response time by **20%** in first 6 weeks using profiling tools — leading directly to full-time offer.
- Wrote unit tests achieving **95% code coverage**; caught 12 critical bugs before production.

---

### MSc Thesis Researcher — Generative AI
**Dublin City University | Sep 2024 – Oct 2025**

- Built and trained **DCGAN and CGAN** architectures in TensorFlow/Keras, generating **256×256** synthetic images for plant health monitoring datasets.
- Designed novel dataset augmentation strategies achieving **15% training efficiency improvement** over standard CGAN baseline.
- Evaluated models against quantitative industry benchmarks across multiple metrics; results competitive with state-of-the-art baselines.

---

## 🎓 Education

**MSc Computing (Artificial Intelligence)** — Dublin City University, Ireland
*Sep 2024 – Oct 2025*
Thesis: Generative model architectures (DCGAN/CGAN) for synthetic data generation. Coursework: Deep Learning, Computer Vision, Probabilistic Models.

**Master in Computer Applications (MCA)** — Sinhgad Institute of Management, India
*2020 – 2022*

**Bachelor in Computer Applications (BCA)** — Marathwada Mitra Mandal's College of Commerce, India
*2017 – 2020*

---

## 🔍 Featured Projects

## ⚡ QuerySense — PostgreSQL AI Query Optimizer
**Production LLM Agent · Rule Engine + Claude API**

EXPLAIN ANALYZE has existed for 30 years. It prints terrifying output that most developers ignore. I built QuerySense to fix that — paste a slow query, get back plain English: what's slow, why, and exactly how to fix it. With before/after proof.

### ✦ The Architecture Decision That Matters
The rule engine runs **before** Claude, not after. Deterministic rules catch known patterns instantly (free, always correct). Claude only runs for explanation and nuance. Every senior engineer asks *"what if the LLM is wrong?"* — this answers that question.

```python
def analyze(plan):
    issues = rule_engine.detect(plan)                        # Step 1 — deterministic, free, fast
    ai_analysis = claude.explain(plan, known_issues=issues)  # Step 2 — human explanation
    return merge(issues, ai_analysis)                        # Rules give facts, AI gives language
```

### ✦ What It Detects (7 Rules)
- **SequentialScanRule** — flags full table scans on tables with > 1,000 rows
- **MissingIndexRule** — detects WHERE filters with no index to serve them
- **MissingJoinIndexRule** — catches unindexed JOIN columns causing full scans on both sides
- **NestedLoopLargeTableRule** — warns when nested loops produce > 10,000 rows (O(n×m))
- **HighCostNodeRule** — identifies single nodes consuming > 50% of total query cost
- **StaleStatisticsRule** — detects when row estimates are off by > 10x from reality
- **PartialIndexOpportunityRule** — suggests partial indexes for constant-value WHERE filters

### ⚡ Features
- **Before/after benchmarking** — applies fix in a rollback transaction, measures real execution time — confirmed **98.8% latency reduction** on missing-index queries
- **Evaluation layer** — verifies the plan actually changed (Seq Scan → Bitmap Heap Scan), not just timing
- **Redis caching** — same query never hits the Claude API twice (24h TTL)
- **History persistence** — every analysis saved to PostgreSQL for audit and replay
- **CLI tool** — Typer + Rich with formatted benchmark tables and coloured severity output
- **Web UI** — single-file professional dark demo, zero framework
- **Seed database** — 261K rows across 5 tables, no indexes intentionally — so QuerySense finds real slow queries out of the box

### 📊 Benchmark Results
| Query | Before | After | Improvement |
|-------|--------|-------|-------------|
| `SELECT * FROM orders WHERE user_id = 5` | 46.8 ms | 0.032 ms | ↓ 98.8% |
| `SELECT * FROM orders WHERE created_at > '2024-01-01'` | 5.6 ms | 5.0 ms | n/a (low selectivity — honest) |
| JOIN query (3 tables, 200K rows) | 141 ms | 121 ms | ↓ 13.9% |

### 🏗 Stack
| Layer | Tech |
|-------|------|
| API | FastAPI + asyncpg |
| AI | Claude Haiku (Anthropic) |
| Cache | Redis 7 (Upstash) |
| Database | PostgreSQL 15 (Neon.tech) |
| CLI | Typer + Rich |
| Infrastructure | Docker + Railway + GitHub Actions |
| Frontend | Single HTML file + GitHub Pages |
| Total cost | $0 |

**Skills:** `Python` `FastAPI` `PostgreSQL` `Claude API` `Redis` `Docker` `asyncpg` `Rule Engine` `GitHub Actions`

**Links:** [Live Demo](https://neeraj281998.github.io/Querysense/) · [API Docs](https://querysense-production.up.railway.app/docs) · [Repository](https://github.com/Neeraj281998/Querysense)

---

## 🧠 JavaMem — Java Memory Visualizer
**DSA & Memory Education Tool**

Most Java memory tools — and most textbooks — quietly teach wrong mental models. I identified 8 specific misconceptions and built a visualizer that corrects each one through how it actually renders, not through a warning label in the corner.

### ✦ What Makes It Different
- **HashMap** displays entries by hash bucket index — because HashMap does not preserve insertion order
- **LinkedList** spawns individual node cards scattered across the heap — because each node is a separate allocation, not one contiguous block
- **Two-phase GC** — objects become GC-eligible first, collected after a random delay — because GC is non-deterministic
- **ArrayList** renders as contiguous indexed cells, **Stack** as a LIFO tower — the visual matches the actual memory behaviour

### ⚡ Features
- Visualizes **Stack, Heap & String Pool** in real time with animated SVG reference arrows
- Supports **8+ data structures** with live Add / Remove controls — no re-run required
- Simulates **String interning**, **Integer cache** (−128 to 127), and the `==` trap above 127
- **Canvas-rendered BST** with dynamic layout and in-order traversal display
- Zero dependencies — entire application ships as a single HTML file

**Skills:** `Data Structures` `Java Memory Model` `Canvas API` `JavaScript` `HTML` `CSS`

**Links:** [Live Demo](https://neeraj281998.github.io/JavaMem-Java-Memory-Visualizer/) · [Repository](https://github.com/Neeraj281998/JavaMem-Java-Memory-Visualizer)

---

## 🧠 SQLMem — MySQL Query Visualizer
**SQL & Database Education Tool**

Most people learn SQL by memorising syntax. The deeper issue is the lack of a clear mental model of what actually happens inside the database engine when a query runs. I built a visualizer that animates every operation in execution order — rows being scanned, filtered, joined, grouped, sorted, and mutated — step by step, exactly as MySQL processes them.

### ✦ What Makes It Different
- **Schema canvas** renders `CREATE TABLE` statements as draggable table cards with animated dashed foreign key arrows
- **JOIN animator** scans rows one-by-one with a glowing beam between tables — `INNER`, `LEFT`, `RIGHT`, and `FULL JOIN` produce visually distinct Venn diagrams and result streams
- **WHERE engine** supports `LIKE`, `IN`, `BETWEEN`, `IS NULL`, `IS NOT NULL` — matching rows flash green, filtered rows receive a strike-through animation
- **DML animations** — `INSERT` (green flash), `UPDATE` (yellow highlight), `DELETE` (strikethrough), `TRUNCATE` (instant wipe with DELETE comparison)
- **GROUP BY + Aggregates** (`SUM`, `AVG`, `COUNT`, `MIN`, `MAX`) animate as proportional bar charts per group
- **Execution Order Explainer** — side-by-side view of written order vs MySQL's actual execution order
- Zero dependencies — entire application ships as a single HTML file

**Skills:** `SQL` `MySQL` `Database Internals` `JavaScript` `HTML` `CSS` `SVG Animation`

**Links:** [Live Demo](https://neeraj281998.github.io/SQLMem-MySQL-Query-Visualizer/) · [Repository](https://github.com/Neeraj281998/SQLMem-MySQL-Query-Visualizer)

---

## 📬 SmartMail Drive Sync Engine
**Production-Grade Gmail → Google Drive Automation**

People receive dozens of file attachments daily and have to manually download and organise them in Google Drive — error-prone, time-consuming, and easy to forget. I built an automation pipeline that handles this end-to-end with zero duplication and crash-safe reliability.

### ✦ Key Design Decisions
- **Message-level idempotency** via MySQL persistence — guaranteed exactly-once processing even across crashes and restarts
- **Fault-tolerant pipeline** — crash-safe, restart-safe, rate-limit aware
- **Dual execution modes** — scheduled (every 3 minutes via APScheduler) + on-demand REST trigger
- **OAuth2 authentication** — secure, permissioned access to Gmail and Google Drive APIs
- Human-readable file renaming with sender-based local organisation

**Skills:** `Python` `FastAPI` `Gmail API` `Google Drive API` `MySQL` `OAuth2` `APScheduler`

**Links:** [Repository](https://github.com/Neeraj281998/mail-to-drive-pipeline/blob/110be8e59f1d86f1a194fd87e484c2c3ba7e6c25/README.md)

---

## ☁️ Pexeluxe — Cloud-Native Photography Platform
**Scalable AWS-Powered Image Gallery**

Designed and deployed a live cloud-native photography platform on AWS. Newly uploaded images are automatically indexed via event-driven Lambda functions and served globally through CloudFront CDN.

**Skills:** `AWS (S3, Lambda, CloudFront)` `CDN Architecture` `Event-Driven Architecture` `HTML5` `JavaScript` `Performance Optimisation`

**Links:** [Live Demo](https://d23oj82a8a9j68.cloudfront.net/) · [Repository](https://github.com/Neeraj281998/Pexeluxe/blob/9392f45e34b3ef74897d86ad688e4f125d81fc64/README.md)

---

## 📜 Certifications

- Data Structures & Algorithms — NPTEL, IIT Madras *(April 2022)*: sorting, graphs, dynamic programming, trees
- Algorithmic Toolbox — Coursera, UC San Diego & HSE University *(July 2021)*
- JavaScript Advanced — Udemy *(December 2021)*: ES6+, async/await, closures, functional programming
- Docker & Kubernetes — Udemy *(2021)*: container orchestration and deployment pipelines

---

## ✍️ Random Dev Quote
![](https://quotes-github-readme.vercel.app/api?type=vertical&theme=radical)

---

<div align="center">

*Last updated: June 2026*

</div>
