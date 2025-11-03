# AdventureWorks_PowerBI_SchemaTransformation

# Adventure Works: Star Schema to Snowflake Schema Transformation in Power BI

## Overview
This project demonstrates how to design and transform a Star Schema into a Snowflake Schema using the Adventure Works dataset in Microsoft Power BI.

The goal of this project is to understand the structure, relationships, and normalization process involved in building efficient data models for analysis.



## Project Objectives
- Build a Star Schema with four main tables: Sales, Product, Region, and Salesperson.
- Transform the Star Schema into a Snowflake Schema by normalizing the Product table.
- Create new lookup tables such as Category and Subcategory.
- Establish proper relationships, cardinality, and cross-filter directions.
- Understand how normalization improves data structure and performance.



## Data Model Summary

### Star Schema
In the Star Schema:
- The Sales table is the fact table.
- Product, Region, and Salesperson are dimension tables.
- Relationships:
  - Sales[ProductKey] → Product[ProductKey]
  - Sales[SalesTerritoryKey] → Region[SalesTerritoryKey]
  - Sales[EmployeeKey] → Salesperson[EmployeeKey]

**Model Preview:**  
(Insert your Star Schema screenshot here.)



### Snowflake Schema
In the Snowflake Schema:
- The Product table is normalized into Category and Subcategory tables.
- Relationships:
  - Category[Category] → Subcategory[Category]
  - Subcategory[Subcategory] → Product[Subcategory]


## Steps Performed

### 1. Data Loading
- Loaded the Adventure Works Excel dataset containing four tables:
  - Sales
  - Product
  - Region
  - Salesperson
- Disabled Autodetect Relationships in Power BI.

### 2. Star Schema Configuration
- Built the fact-dimension relationships.
- Ensured correct cardinality and filter direction.

### 3. Schema Transformation (Normalization)
Created lookup tables using DAX:

Subcategory = DISTINCT(SELECTCOLUMNS(Product,
    "Subcategory", Product[Subcategory],
    "Category", Product[Category]
))



