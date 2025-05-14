# Full-Stack Data Warehouse Project

This portfolio project showcases how I built a complete data warehousing and analytics solution — from setting up the warehouse to uncovering actionable insights. It’s designed to reflect practical, real-world workflows while following industry best practices in data engineering and analytics.

---

## Data Architecture

The architecture follows the **Medallion Architecture** pattern with **Bronze**, **Silver**, and **Gold** layers:

- **Bronze Layer**: Stores raw data as-is from the source systems. Data is ingested from CSV files into a SQL Server database.
- **Silver Layer**: Performs data cleansing, standardization, and normalization to prepare data for analysis.
- **Gold Layer**: Contains business-ready, star-schema modeled data used for reporting and analytics.

---

## Project Overview

This project includes:

- **Data Architecture**: Built a modern data warehouse using the Medallion Architecture with clearly defined Bronze, Silver, and Gold layers.
- **ETL Pipelines**: Extracted, transformed, and loaded data from raw sources into structured layers.
- **Data Modeling**: Designed fact and dimension tables to support efficient analytical querying.
- **Analytics & Reporting**: Developed SQL-based reports and dashboards to turn raw data into actionable insights.

---

## Project Requirements

### Objective

Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

### Specifications

- **Data Sources**: Import data from two source systems (ERP and CRM), provided as CSV files.
- **Data Quality**: Clean and resolve data quality issues prior to analysis.
- **Integration**: Combine both sources into a single, user-friendly data model designed for analytical queries.
- **Scope**: Focus on the latest dataset only (no historization required).
- **Documentation**: Provide clear documentation of the data model for both business and analytics teams.

---

## BI: Analytics & Reporting

### Objective

Develop SQL-based analytics to deliver detailed insights into:

- Customer Behavior  
- Product Performance  
- Sales Trends  

These insights empower stakeholders with key business metrics, enabling strategic decision-making.

---

## Repository Structure

data-warehouse-project/
│
├── datasets/ # Raw datasets used for the project (ERP and CRM data)
│
├── docs/ # Project documentation and architecture details
│ ├── etl.drawio # ETL techniques and pipeline visualization
│ ├── data_architecture.drawio # Project architecture diagram
│ ├── data_catalog.md # Dataset catalog with field descriptions
│ ├── data_flow.drawio # Data flow diagram
│ ├── data_models.drawio # Star schema data models
│ ├── naming-conventions.md # Table, column, and file naming standards
│
├── scripts/ # SQL scripts for ETL and transformation logic
│ ├── bronze/ # Scripts for extracting and loading raw data
│ ├── silver/ # Scripts for data cleansing and transformation
│ ├── gold/ # Scripts for building analytical models
│
├── tests/ # Test scripts and data validation checks
│
├── README.md # Project overview and instructions
├── LICENSE # License information
├── .gitignore # Git ignore file
└── requirements.txt # Dependencies and tools (if any)

---

## License

This project is licensed under the **MIT License**.  
