# Database-Automation_Final-Project (Group 2)

## 🚀 Overview

This repository implements a complete **cross-database automation, monitoring, and anomaly detection** pipeline — demonstrating how DevOps, data engineering, and observability practices can come together in a unified workflow.

Key features:

- Automated database provisioning & initialization (MySQL + MongoDB)  
- ETL pipeline to fetch, process and load data (e.g. climate data via API)  
- CI/CD automation via GitHub Actions to run the entire pipeline on code changes  
- Real-time monitoring of database systems using container metrics & observability tools  
- Anomaly detection module (using Python & ML) for data-quality or outlier detection  

---

## 🧰 Stack / Technologies

- **Databases:** MySQL, MongoDB  
- **Scripting & Data Processing:** Python (pandas, requests, etc.)  
- **Containers & Orchestration:** Docker, docker-compose  
- **CI/CD:** GitHub Actions (workflow definitions under `.github/workflows/`)  
- **Monitoring & Observability:** Prometheus / cAdvisor, Grafana, custom monitoring setup (scripts + config in `monitoring/`)  
- **Anomaly Detection / Analytics:** Custom Python scripts in `scripts/` that implement data cleaning, preprocessing, and outlier detection  

---

## 📂 Repository Structure

```
.
├── .github/workflows/        # CI/CD workflows  
├── docker-compose.yml        # Docker-compose for local or container orchestration  
├── sql/                      # SQL scripts to create database schema / tables  
├── scripts/                  # ETL logic, data loading, validation, anomaly detection  
├── mongo/                    # (If applicable) configuration / setup for MongoDB  
├── monitoring/               # Monitoring setup, dashboard configs, metrics exporters  
├── requirements.txt          # Python dependencies  
└── README.md                 # This file  
```

## 🏗️ Architecture
```
┌─────────────────┐
│  GitHub Actions │  ← CI/CD Automation
└────────┬────────┘
         │
    ┌────▼────┐
    │  MySQL  │ ←→ Sync ←→ ┌──────────┐
    └────┬────┘              │ MongoDB  │
         │                   └─────┬────┘
         │                         │
    ┌────▼─────────────────────────▼────┐
    │     Monitoring (Signoz/Grafana)   │
    └───────────────────────────────────┘
              │
         ┌────▼──────┐
         │  Alerts   │
         └───────────┘
```


---

## 🎯 Getting Started — How to Use

1. **Clone the repository**  
   ```bash
   git clone https://github.com/Dhruv7573/Database-Automation_Final-Project_Group_2.git
   cd Database-Automation_Final-Project_Group_2
   ```  

2. **Install requirements**  
   ```bash
   pip install -r requirements.txt
   ```  

3. **Start containers with Docker Compose**  
   ```bash
   docker-compose up
   ```  
   This will spin up required services including database containers.

4. **Run ETL + Data Loading**  
   - Execute the ETL and data-loading scripts from the `scripts/` folder to fetch data from API, process it, and populate MySQL & MongoDB.  
   - Use provided SQL schema under `sql/` when initializing the databases.  

5. **Run Anomaly Detection / Data Validation**  
   - After ingestion, run anomaly detection scripts to identify outliers or abnormal data entries.  

6. **Monitoring & Observability (optional but recommended)**  
   - Use the configurations in `monitoring/` to deploy monitoring stack (Prometheus + Grafana + exporters).  
   - Inspect dashboards to monitor resource usage, container health, query performance, etc.  

---

## 📈 CI/CD Pipeline (GitHub Actions)

Thanks to the workflow definitions under `.github/workflows/`, any time you push changes to the `main` branch:

- The pipeline automatically spins up MySQL + MongoDB containers  
- Runs database initialization via SQL scripts  
- Executes ETL to ingest and load data  
- Optionally runs data validation / anomaly detection  
- Provides reliable, repeatable environment — useful for development, testing or deployment  

---

## ⚠️ Notes & Considerations

- Ensure environment variables / credentials (if any) are correctly configured when connecting to remote databases (especially MongoDB).  
- When monitoring is enabled, make sure ports / metrics exporters are accessible.  
- The anomaly detection logic expects clean data (no missing values, correct types) — make sure ETL handles data cleaning and type conversion properly before detection step.  

---


