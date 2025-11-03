Adventure Works: From Star Schema to Snowflake Schema
Case Study

Adventure Works is a retail company that sells various products across different regions. The company maintains large amounts of sales data in Power BI. Initially, the data was structured in a Star Schema, which worked well for basic reporting. However, as the business grew, they faced challenges in managing and maintaining product-related data due to redundancy and performance issues.
To address this, the company decided to restructure its data model into a Snowflake Schema.

Context

In the existing Star Schema, the Sales fact table was connected directly to dimension tables such as:

Product

Region

Salesperson

Although this design made queries simple, the Product table contained repeated information about product categories and subcategories. This made the table large, harder to maintain, and slower to query as data volume increased.

Objective

The main goal of this project was to:

Redesign the Star Schema into a Snowflake Schema for better normalization.

Reduce redundancy and improve the clarity of product-related data.

Improve the overall performance and manageability of the Power BI data model.

What Was Done

Loaded the Adventure Works Data Excel file containing four base tables:

Sales

Product

Region

Salesperson

Created two new dimension tables from the Product data:

Subcategory

Category

Established relationships as follows:

Sales connected to Product (based on Product ID)

Product connected to Subcategory (based on Subcategory ID)

Subcategory connected to Category (based on Category ID)

Sales also connected to Region and Salesperson

This structure removed repeated category information from the Product table, resulting in a cleaner and more organized schema.

Real-World Relevance

In real business environments, data models often start simple but evolve as the company grows.
When multiple departments or reports rely on the same data, normalization helps ensure data consistency and easier updates.
By moving to a Snowflake Schema, Adventure Works can manage product categories independently while still linking all sales data accurately for reporting.

Conclusion and Outcome

After converting the model from a Star Schema to a Snowflake Schema:

Data redundancy in the Product table was eliminated.

Model performance and clarity improved.

The structure became easier to maintain and scale.

This project demonstrates how proper data modeling techniques can directly improve reporting efficiency and data management in Power BI.

