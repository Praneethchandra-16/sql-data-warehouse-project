# SQL Data Warehouse Project

## Overview
This project demonstrates the design and implementation of a SQL-based Data Warehouse using the Medallion Architecture (Bronze → Silver → Gold).  

The pipeline ingests raw data from multiple sources (CRM and ERP systems) into SQL Server, applies cleaning and standardization, and produces business-ready star schema models for reporting and analytics.  

---

## High-Level Architecture
<img width="1544" height="799" alt="data_architecture" src="https://github.com/user-attachments/assets/adfcc5c3-a97d-469e-b37c-0b5ffc28ed70" />


- **Bronze Layer (Raw Data)**: Load raw CSV data into staging tables without transformation.  
- **Silver Layer (Cleaned Data)**: Apply cleansing, standardization, normalization, and enrichment.  
- **Gold Layer (Business-Ready Data)**: Create star-schema models with fact and dimension tables for analytics.  
- **Consumption**: Enable BI dashboards, ad-hoc queries, and machine learning use cases.  

---

## Data Flow
<img width="1094" height="559" alt="data_flow" src="https://github.com/user-attachments/assets/c39d248e-7fc4-418d-954e-1ad90f44de48" />

- **Sources**: CRM & ERP CSV files  
- **Bronze**:  
  - `crm_sales_details`, `crm_cust_info`, `crm_prd_info`  
  - `erp_cust_az12`, `erp_loc_a101`, `erp_px_cat_g1v2`  
- **Silver**: Cleansed versions of the same datasets  
- **Gold**:  
  - Fact: `fact_sales`  
  - Dimensions: `dim_customers`, `dim_products`  

---

## Project Structure
```
sql-data-warehouse-project/
│
├── datasets/              # Raw input datasets (CRM, ERP CSVs)
├── docs/                  # Documentation & diagrams (data_flow.png, data_architecture.png)
├── scripts/
│   ├── bronze/            # SQL scripts for raw layer
│   ├── silver/            # SQL scripts for transformations
│   ├── gold/              # SQL scripts for star schema
│   └── init_database.sql  # Database initialization
├── tests/
│   ├── quality_checks_bronze.sql
│   ├── quality_checks_silver.sql
│   └── quality_checks_gold.sql
└── README.md
```

---

## Tech Stack
- Database: SQL Server / Azure SQL  
- Query Language: T-SQL  
- Tools: SSMS, Draw.io (for diagrams)  
- Version Control: GitHub  

---

## Key Features
- End-to-end ETL pipeline across Bronze, Silver, Gold layers  
- Star-schema modeling with fact and dimension tables  
- Data quality checks to enforce integrity (PK/FK, duplicates, nulls, business rules)  
- Reproducible SQL scripts for database creation, transformations, and validation  

---

## Data Quality Checks
Implemented in the `tests/` folder:
- Row count and non-empty checks  
- Primary key uniqueness validation  
- Foreign key referential integrity checks  
- Not-null enforcement on critical fields  
- Duplicate detection on business keys  
- Negative or invalid amounts detection  
- Date sanity checks (no future service dates, visit ≤ service ≤ paid)  

---

## How to Run
1. Clone the repo:
   ```bash
   git clone https://github.com/Praneethchandra-16/sql-data-warehouse-project.git
   ```
2. Initialize database & schemas:
   ```sql
   scripts/init_database.sql
   ```
3. Execute scripts in order:
   - `scripts/bronze/*`  
   - `scripts/silver/*`  
   - `scripts/gold/*`  
4. Run quality checks:
   ```sql
   tests/quality_checks_gold.sql
   ```

---

## Learnings & Outcomes
- Built a layered data warehouse from raw sources to business-ready models  
- Applied ETL design principles: cleansing, enrichment, normalization  
- Designed a star schema to support reporting and analytics  
- Implemented data quality governance through SQL testing  

---

## Future Enhancements
- Automate the ETL process with Azure Data Factory or SSIS  
- Implement scheduling and orchestration using Apache Airflow or Azure Synapse Pipelines  
- Add a semantic layer and dashboards using Power BI  
- Incorporate Slowly Changing Dimensions (SCD) for historical tracking  
- Extend the model with additional dimensions and fact tables for advanced analytics  
- Integrate with cloud storage for scalable data ingestion  

---

## About Me
I am Praneeth Chandra Budala, a recent Master’s graduate in Business Analytics & Artificial Intelligence from The University of Texas at Dallas. I specialize in data engineering, machine learning, and analytics, with hands-on experience in building end-to-end data pipelines and analytical models. I am passionate about turning raw data into actionable insights and delivering measurable business value.  

**Connect with me:**  
- [GitHub](https://github.com/Praneethchandra-16)  
- [LinkedIn](https://www.linkedin.com/in/praneeth-chandra-budala-6795b8214)  
- [Portfolio Website](https://praneeths-ai-career.lovable.app)  
- [Medium Blog](https://medium.com/@praneethchandrabudala)  
