## Retail Store Dataset Project.

## Dataset source:
Retail Store Sales dataset by Ahmed Mohamed.
License: CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/)
Available at: (https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning)
**Licensed for Non-Commercial use only.**

## Data Modelling
The original dataset was provided as a single CSV file.
For this project, the data has been normalised into three relational tables
(customers, products, and transactions) to demonstrate SQL JOINs
and RDB design.

**The underlying dataset is not redistributed in this repository.**

## Dataset Structure

The analysis will be based on 3 tables as shown below.

# 1. Customers
- 'customer_id' (Primary Key)

Contains unique customer identifiers.

# 2. Products
- 'product_id' (Primary Key)
- 'item'
- 'category'
- 'price_per_unit'

Contains product reference data and list pricing.

# 3. Transactions
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

## Initial Data Inspection (CSV)

Before loading the data into SQL Server, the CSV files were inspected to:

- Review column names and the data types.
- Confirm the presence of primary keys in each CSV file.
- Verify that shared keys (Foreign keys) exist across related files.
- Ensure the files could be joined without any structural issues

No cleaning or transformations were applied at this stage.

## Data Ingestion (SQL)

The source CSV files were loaded into SQL Server as staging tables using 'BULK INSERT'.
The staging tables were stored exactly as received, with no transformations applied.
All columns were stored as VARCHAR to preserve the raw structure of the data.
Row counts in the staging table were validated to ensure successful ingestion.

This staging layer will be used to perform validation and to support reproducible data processing.

## Data Validation

Once the data was ingested into SQL Server staging tables, a series of data validation checks were carried out prior to any transformation.

The following checks were performed:
- Row count validation to confirm all records were successfully loaded and present.

[**ROW COUNT VALIDATION**](images/Row_Count_Validation.png)

- Primary key uniqueness checks for customers, products, and transactions.
- Referential integrity checks to ensure all transactions reference valid customers and products in SQL Server.

[**REFERENTIAL INTEGRITY**](images/Referential%20Integrity%20Checks.png)

- Analysis of missing values in transactional fields such as quantity, pricing, discount indicators, etc.
- Null checks were focused on key transactional fields that directly affect revenue calculations and time based analysis.
- All columns contained valid dates and total revenue sales however, missing values were identified in 'Quantity' and 'Price Per Unit' fields which informed how
revenue calculations and cleaning logic were handled later on.

[**Null Checks**](images/Null%20Checks.png)

No changes were made to the data at this stage. The validation results informed how null values, data types, and business rules were handled during the transformation phase.

## Data Transformation

- Following data validation, the data was then transformed into clean, analysis ready tables.
- This step in the project included standardising the data types, handling all missing values, and preparing the data for analytical querying and Reporting in Power BI.

## Sales Data Analysis using SQL and Power BI

## Project Overview


## Tools Used
- CSV
- SQL (SQL Server)
- Power BI

## Data Cleaning
- 
- 
- 
- 

## SQL Analysis Performed
- Monthly sales trends.
- Revenue by region.
- Sales by product category.
- Top customers by total spend.

## Key Insights and Results
- 
- 
- 

## Dashboard
A Power BI dashboard was created to visualise the findings.
