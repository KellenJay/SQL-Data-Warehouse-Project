# Naming Conventions

This document outlines the naming conventions used for schemas, tables, views, columns, and other objects in the data warehouse.

---

## Table of Contents
- [General Principles](#general-principles)
- [Table Naming Conventions](#table-naming-conventions)
  - [Bronze Rules](#bronze-rules)
  - [Silver Rules](#silver-rules)
  - [Gold Rules](#gold-rules)
- [Column Naming Conventions](#column-naming-conventions)
  - [Surrogate Keys](#surrogate-keys)
  - [Technical Columns](#technical-columns)
- [Stored Procedure Naming](#stored-procedure-naming)

---

## General Principles

- **Naming Style**: Use `snake_case` — lowercase letters with underscores to separate words.
- **Language**: Use English for all object names.
- **Avoid Reserved Words**: Do not use SQL reserved keywords as names for tables, views, or columns.

---

## Table Naming Conventions

### Bronze Rules

- Format: `<sourcesystem>_<entity>`
- `sourcesystem`: Name of the source system (e.g., `crm`, `erp`)
- `entity`: Exact table name from the source system (no renaming)

**Example**:  
`crm_customer_info` → Customer information table from the CRM system.

---

### Silver Rules

- Same format as Bronze: `<sourcesystem>_<entity>`
- Names must be preserved from the original source.

**Example**:  
`erp_order_header` → Order header data from the ERP system.

---

### Gold Rules

- Format: `<category>_<entity>`
- `category`: Represents the table's role (e.g., `dim`, `fact`)
- `entity`: Descriptive name aligned with the business domain

**Examples**:
- `dim_customers` → Dimension table for customer data
- `fact_sales` → Fact table containing sales transactions

---

## Glossary of Category Prefixes

| **Pattern** | **Meaning**         | **Example(s)**                       |
|-------------|----------------------|--------------------------------------|
| `dim_`      | Dimension table       | `dim_customer`, `dim_product`        |
| `fact_`     | Fact table            | `fact_sales`                         |
| `report_`   | Report output table   | `report_customers`, `report_sales_monthly` |

---

## Column Naming Conventions

### Surrogate Keys

- Format: `<entity>_key`
- Used for all primary keys in dimension tables

**Example**:  
`customer_key` → Surrogate key in the `dim_customers` table

---

### Technical Columns

- Format: `dwh_<column_name>`
- Prefix `dwh_` is reserved for system-generated metadata

**Example**:  
`dwh_load_date` → Date the record was loaded into the data warehouse

---

## Stored Procedure Naming

- Format: `load_<layer>`
- `layer`: Specifies the data warehouse layer being loaded (e.g., bronze, silver, gold)
**Examples**:
- `load_bronze` → Loads data into the Bronze layer
- `load_silver` → Loads data into the Silver layer
- `load_gold` → Loads data into the Gold layer
