# Data Catalog for Gold Layer

**Overview**

The Gold Layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of **dimension tables** and **fact tables** for specific business metrics.

**1. gold.dim_customers**
**- Purpose:** Stores customer details enriched with demographic and geographic data.
**- Columns:** 
| **Column Name**   | **Data Type**  | **Description**                                                          |
| ----------------- | -------------- | ------------------------------------------------------------------------ |
| `customer_key`    | `INT`          | Surrogate key uniquely identifying each customer in the dimension table. |
| `customer_id`     | `INT`          | Unique identifier assigned to each customer in the source system.        |
| `customer_number` | `NVARCHAR(50)` | Alphanumeric identifier used for customer tracking and referencing.      |
| `first_name`      | `NVARCHAR(50)` | Customer’s first name.                                                   |
| `last_name`       | `NVARCHAR(50)` | Customer’s last name or family name.                                     |
| `country`         | `NVARCHAR(50)` | Country of residence (e.g., 'Australia').                                |
| `marital_status`  | `NVARCHAR(50)` | Marital status (e.g., 'Married', 'Single').                              |
| `gender`          | `NVARCHAR(50)` | Gender (e.g., 'Male', 'Female', 'n/a').                                  |
| `birthdate`       | `DATE`         | Date of birth (YYYY-MM-DD).                                              |
| `create_date`     | `DATE`         | Date the customer record was created in the system.                      |
