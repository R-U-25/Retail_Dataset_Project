# Retail Store Sales Analysis (CSV, SQL & Power BI)
## Project Overview

This project demonstrates an end-to-end data analysis workflow using a retail sales dataset.
The focus here was on data modelling, validation, transformation, and business-focused analysis using SQL Server, followed by interactive visualisation in Power BI.

The project simulates a realistic analytics pipeline, from raw CSV ingestion through to analytical reporting.

### Dataset source:
Retail Store Sales dataset by Ahmed Mohamed.
License: CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/)
Available at: (https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning)
**Licensed for Non-Commercial use only.**

## Data Model Overview
The original dataset was provided as a single CSV file.
For this project, the data has been normalised into three relational tables
(customers, products, and transactions) to demonstrate SQL JOINs
and RDB design.

**The underlying dataset is not redistributed in this repository.**

## Dataset Structure

The analysis will be based on 3 tables as shown below.

## Customers
- 'customer_id' (Primary Key)

Contains unique customer identifiers.

## Products
- 'product_id' (Primary Key)
- 'item'
- 'category'
- 'price_per_unit'

Contains product reference data and list pricing.

## Transactions
- 'transaction_id' (Primary Key)
- 'transaction_date'
- 'customer_id' (Foreign Key → Customers)
- 'product_id' (Foreign Key → Products)
- 'quantity'
- 'price_per_unit'
- 'total_spent'
- 'discount_applied'
- 'payment_method'
- 'location'

COntains all customer transactions and additional details.

## Initial Data Inspection (CSV)

Before loading the data into SQL Server, the CSV files were inspected to:

- Review column names and the data types.
- Confirm the presence of primary keys in each CSV file.
- Verify that shared keys (Foreign keys) exist for JOIN compatibility.
- Ensure the files could be joined without any structural issues

No cleaning or transformations were applied at this stage.

## Data Ingestion (SQL)

- The source CSV files were loaded into SQL Server as staging tables using 'BULK INSERT'.
- The staging tables were stored exactly as received, with no transformations applied.
- All columns were stored as VARCHAR to preserve the raw structure of the data.
- Row counts in the staging table were validated to ensure successful ingestion.

This staging layer will be used to perform validation and to support reproducible data processing.

## Data Validation

After ingestion into SQL Server staging tables, data validation checks were performed before any transformation.

The following checks were performed:

- Row count validation to confirm all records were successfully loaded and present.
[**ROW COUNT VALIDATION**](images/Row_Count_Validation.png)

- Primary key uniqueness checks for customers, products, and transactions.

- Referential integrity checks to ensure all transactions reference valid customers and products in SQL Server.
[**REFERENTIAL INTEGRITY**](images/Referential%20Integrity%20Checks.png)

- Null analysis on key transactional fields (quantity, price_per_unit, total_spent, discount_applied).
- These results guided decisions on how incomplete transactions were treated and how revenue metrics were calculated during data transformation.
[**Null Checks**](images/Null%20Checks.png)

No changes were made to the data at this stage. The validation results informed how null values, data types, and business rules were handled during the transformation phase.

## Data Transformation (SQL Views)

- Data was cleaned and created to standardise data types and prepare the data for analysis.
- The 'transactions_clean' view converted raw text fields into appropriate date and numeric formats
and standardised discount indicators(either 0 or 1).
- Similar clean VIEWs were created for Customers and Products.
[**SQL Views(Standardising Dates and Discounts**](images/SQL%20Views(Standardising%20date%20and%20discount%20fields).png)

## Analytical Data Model (Final VIEW)

- A final analytical view (VIEW 'Sales') was created by joining cleaned transaction data with cleaned product and cleaned customer reference data.
- LEFT JOINs were used to preserve all transaction records while enriching them with product and customer attributes.
- This view will serve as the primary dataset for analysis and reporting.
[**Creation of the Final VIEW (Sales)**](images/Final%20VIEW%20(Sales).png)

## Preview of the final VIEW

[**First 10 Rows in the Final Sales VIEW**](images/First%2010%20Records%20in%20Sales%20(VIEW).png)

## Data Analysis (SQL)

SQL queries were written on the final analytical dataset to answer key business questions,
including 
- Monthly revenue trends using CTE.
- Revenue by Category.
- Top 10 Customers by Revenue using JOINs.

Below are some KPIs and important details which were extracted using SQL Queries.

[**Monthly Revenue (CTE)**](images/Monthly%20Revenue%20(CTE).png)

[**Revenue by Category**](images/Total%20Income%20by%20Category.png)

[**Top 10 Customers by Revenue**](images/Top%2010%20Customers%20by%20Revenue.png)

## Data Visualisation (Power BI)

- Insights which were derived from my SQL Analysis from the clean view was visualised through Power BI to provide an interactive and clear picture of the results gathered. Below are some of the visualisations which were created.

[**Monthly Revenue Trend**](images/Monthly%20Revenue%20Trend.png)

[**Total Revenue by Category**](images/Total%20Revenue%20by%20Category.png)

[**Top 10 Customers by Revenue**](images/Top%2010%20Customers%20by%20Revenue.png)

## Conclusion

This project demonstrated an end-to-end data analysis workflow using a real-world retail sales dataset.
The data was modelled into relational tables, validated for structural and referential integrity, and
transformed into an analytical dataset from a raw and messy dataset using SQL views.

Business-focused SQL queries were used to extract insights around revenue trends, category performance,
and customer activity, with careful handling of missing values and join logic.
When cleaned, these insights were then visualised in Power BI to aid interactive exploration and reporting.

Overall, the project showcases the importance and benefits of SQL data modelling, data validation, analytical querying,
and visualisation as it can aid in transforming business decisions.
