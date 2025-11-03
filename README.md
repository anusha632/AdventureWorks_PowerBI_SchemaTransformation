# Adventure Works: Star Schema to Snowflake Schema

## Project Overview
This project represents a real-world business case for Adventure Works, a retail and manufacturing company. 
The goal was to improve the existing Power BI data model by transforming it from a Star Schema into a Snowflake Schema. 
The transformation was done to reduce data redundancy, improve performance, and create a more organized model for sales analysis.

## Case Study
Adventure Works initially maintained its sales data using a Star Schema model with four main tables: Sales, Product, Region, and Salesperson. 
Over time, the team identified that the Product table contained repeated information related to product categories and subcategories. 
This led to inefficient queries and unnecessary duplication of data.

To address this issue, the Product table was normalized into separate Category and Subcategory tables, forming a Snowflake Schema. 
This structure made it easier to analyze performance by category and maintain the product hierarchy more effectively.

## Objective
The objective of this task was to:
- Build a Star Schema using Power BI
- Identify redundant information and normalize it into a Snowflake Schema
- Establish proper relationships between fact and dimension tables
- Ensure all relationships have correct cardinality and filtering direction

## Steps Performed

### Step 1: Data Loading
The Adventure Works Data.xlsx file was imported into Power BI. 
The following tables were selected for analysis:
- Sales  
- Product  
- Region  
- Salesperson

### Step 2: Building the Star Schema
In this schema:
- Sales acted as the fact table containing transaction details.
- Product, Region, and Salesperson acted as dimension tables.

Relationships were created as follows:
- Sales → Product (ProductKey)
- Sales → Region (SalesTerritoryKey)
- Sales → Salesperson (EmployeeKey)

Each relationship was configured as Many-to-One with Single cross-filter direction.

### Step 3: Converting to Snowflake Schema
The Product dimension was normalized into two lookup tables using DAX formulas:

**Category table:**
```DAX
Category = GROUPBY('Product', 'Product'[Category ID], 'Product'[Category])


