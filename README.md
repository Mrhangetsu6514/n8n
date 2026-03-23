# 🚀 Automated Data Ingestion & Persistence Engine
> **A Containerized Microservices Pipeline for Real-Time Lead Capture**

![n8n](https://img.shields.io/badge/n8n-FF6D5B?style=for-the-badge&logo=n8n&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Status](https://img.shields.io/badge/Status-Functional-brightgreen?style=for-the-badge)

## 📖 Overview
This project demonstrates a production-ready **Extract, Load, Transform (ELT)** architecture. It provides a robust endpoint for capturing JSON-based lead data via Webhooks and persisting it into a structured PostgreSQL data warehouse. 

The entire stack is orchestrated via **Docker Compose**, emphasizing security, service isolation, and environment-agnostic deployment.

---

## 🛠 Technical Architecture
* **Container Orchestration:** [Docker Compose](https://docs.docker.com/compose/) manages the lifecycle of the automation and database layers.
* **Logic Engine:** [n8n](https://n8n.io/) handles the asynchronous request-response cycle and SQL formatting.
* **Storage Layer:** [PostgreSQL 16](https://www.postgresql.org/) provides relational data integrity with persistent volumes.
* **Tooling:** PowerShell for infrastructure verification and `psql` for manual schema validation.

---

## 🏗 Engineering Highlights
### 🔒 Network Isolation & Security
- **Internal DNS:** Services communicate via a private Docker bridge. The database is shielded from external access, reachable only by the n8n container using the `db` hostname.
- **Environment Abstraction:** Utilized `.env` files to decouple sensitive credentials from the codebase, adhering to the Twelve-Factor App methodology.

### 💾 Reliability & Scaling
- **Stateful Persistence:** Configured host-to-container volume mapping, ensuring that lead data and workflow states survive container lifecycles and host reboots.
- **Atomic Operations:** Utilized raw SQL execution nodes to handle data inserts, allowing for high-performance transactions and schema-specific logic.

---

## 📂 Repository Structure
| File | Role |
| :--- | :--- |
| `docker-compose.yml` | Infrastructure-as-Code (IaC) configuration. |
| `Simple_webhook_SQL_query.json` | Logic for the Webhook-to-SQL pipeline. |
| `Data_sent_test_webhook2.JSON` | Production-spec payload example. |
| `Doco` | Technical implementation logs. |

---

## 🎯 Project Motivation
As the founder of **Matzati.casa**, a property listing platform in Israel, I faced a significant technical hurdle: **Lead Fragmentation.**

In a fast-moving real estate market, manual data entry is a bottleneck. I built this infrastructure to act as the "Central Nervous System" for our data ingestion. By moving away from manual spreadsheets and into a containerized SQL environment, we achieved:
* **Real-time Synchronization:** Leads move from discovery to database in <1s.
* **System Independence:** The platform can be moved from a local dev machine to a cloud VPS (AWS/DigitalOcean) without changing a single line of logic.
* **Data Sovereignty:** By self-hosting our infrastructure via Docker, we maintain full control over our users' data and property insights.

---
*Created and maintained by the Matzati.casa Engineering Team.*
