# Data Catalog for Gold Layer

# Overview

The Gold Layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of **dimension tables** and **fact tables** for specific business metrics.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# 1. gold.dim_customers

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
| `birth_date`       | `DATE`         | Date of birth (YYYY-MM-DD).                                              |
| `create_date`     | `DATE`         | Date the customer record was created in the system.                      |

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# 2. gold.dim_products

**- Purpose:** Provides information about the products and their attributes.
**- Columns:**

| **Column Name**        | **Data Type**  | **Description**                                                   |
| ---------------------- | -------------- | ----------------------------------------------------------------- |
| `product_key`          | `INT`          | Surrogate key uniquely identifying each product record.           |
| `product_id`           | `INT`          | Original product ID from source system.                           |
| `product_number`       | `NVARCHAR(50)` | Alphanumeric product code (transformed from `prd_key`).           |
| `product_name`         | `NVARCHAR(50)` | Descriptive name of the product.                                  |
| `category_id`          | `NVARCHAR(50)` | Category ID extracted from `prd_key`, formatted consistently.     |
| `category`             | `NVARCHAR(50)` | Broad product classification (e.g., Bikes, Components).           |
| `subcategory`          | `NVARCHAR(50)` | Mapped product line (e.g., 'Mountain', 'Road', etc.).             |
| `maintenance_required` | `NVARCHAR(50)` | Whether the product requires maintenance ('Yes', 'No', or 'n/a'). |
| `cost`                 | `INT`          | Product base price; nulls replaced with zero.                     |
| `start_date`           | `DATE`         | Product availability start date.                                  |
| `end_date`             | `DATE`         | Inferred end date based on next product version.                  |

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# 3. gold.fact_sales

**- Purpose:** Stores transactional sales data for analytical purposes.
**- Columns:**

| **Column Name** | **Data Type**  | **Description**                              |
| --------------- | -------------- | -------------------------------------------- |
| `order_number`  | `NVARCHAR(50)` | Unique sales order ID (e.g., 'SO54496').     |
| `product_key`   | `INT`          | Foreign key linking to `dim_products`.       |
| `customer_key`  | `INT`          | Foreign key linking to `dim_customers`.      |
| `order_date`    | `DATE`         | Date the order was placed.                   |
| `shipping_date` | `DATE`         | Date the order was shipped to the customer.  |
| `due_date`      | `DATE`         | Payment due date for the order.              |
| `sales_amount`  | `INT`          | Total monetary value of the line item.       |
| `quantity`      | `INT`          | Number of units sold in the order line item. |
| `price`         | `INT`          | Price per unit of the product.               |
