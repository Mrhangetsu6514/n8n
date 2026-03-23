n8n Property Pipeline Infrastructure
This repository contains the containerized infrastructure and automated data pipeline for Matzati.casa. It utilizes a microservices architecture to ingest, process, and persist real estate listing data from external sources into a structured PostgreSQL database.

🏗 System Architecture
The system is orchestrated using Docker Compose, ensuring an isolated and secure environment where the automation engine and database communicate via a private virtual network.

Automation Engine: n8n (Workflow Automation)

Database: PostgreSQL 16 (Alpine-based)

Orchestration: Docker Compose

Interface: REST API / Webhooks

📁 Repository Structure
docker-compose.yml: Defines the multi-container environment, service networking, and volume persistence.

.gitignore: Configured to protect sensitive information (like .env files and local database storage).

Simple_webhook_SQL_query.json: The exported n8n workflow. This contains the logic for the Webhook listener and the SQL execution node.

Data_sent_test_webhook2.JSON: Sample JSON payload used to verify the API handshake and schema compatibility.

Doco: Project documentation and process logs.

🚀 Key Features & Engineering Highlights
Service Discovery: Implemented internal Docker networking so that n8n identifies the database via the hostname db, rather than volatile IP addresses.

Data Persistence: Configured Docker Volumes to ensure that all property data and workflow configurations remain persistent across container restarts.

Infrastructure as Code (IaC): The entire environment can be deployed with a single command (docker-compose up -d), demonstrating a modern DevOps approach to data engineering.

Security-First Design: Sensitive credentials are abstracted into environment variables, following industry best practices for configuration management.

Manual Handshake Verification: Successfully verified database connectivity and schema integrity using psql via docker exec, ensuring a healthy "pipe" before enabling automation.

🛠 Setup & Usage
Clone the Repo: git clone https://github.com/Mrhangetsu6514/n8n.git

Environment Setup: Create a .env file with your POSTGRES_USER, POSTGRES_PASSWORD, and POSTGRES_DB.

Deploy: Run docker-compose up -d.

Import Workflow: Import the Simple_webhook_SQL_query.json into your local n8n instance at localhost:5678.
