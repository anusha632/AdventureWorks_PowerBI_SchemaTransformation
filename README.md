# Adventure Works: Star Schema to Snowflake Schema

## 📘 Project Summary
This Power BI project demonstrates how to build a **Star Schema** and then convert it into a **Snowflake Schema** using the **Adventure Works** dataset.  
The objective is to understand the difference between the two data modeling approaches and how normalization affects data relationships.

---

## ⭐ Step 1: Star Schema

### 1. Load Dataset
- Imported `Adventure Works Data.xlsx` into Power BI.
- Selected the following tables:
  - `Sales`
  - `Product`
  - `Region`
  - `Salesperson`

### 2. Identify Tables
- **Fact Table:** `Sales`
- **Dimension Tables:** `Product`, `Region`, `Salesperson`

### 3. Create Relationships
- `Sales.ProductKey` → `Product.ProductKey`
- `Sales.SalesTerritoryKey` → `Region.SalesTerritoryKey`
- `Sales.EmployeeKey` → `Salesperson.EmployeeKey`

### 4. Result
- Simple **star-shaped** model with one fact table in the center.
- Relationship type: **Many-to-One**
- Cross filter direction: **Single**

---

## ❄️ Step 2: Snowflake Schema

### 1. Normalize Product Table
Created two new lookup tables using DAX in Power BI:

```DAX
Category = GROUPBY('Product', 'Product'[Category ID], 'Product'[Category])
Subcategory = GROUPBY('Product', 'Product'[Subcategory ID], 'Product'[Category ID], 'Product'[Subcategory])
