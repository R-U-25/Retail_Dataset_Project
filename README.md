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

- Analysis of missing values was performed on key transactional fields such as quantity, unit price, total spent, and discount indicators.
- Validation focused on columns critical to revenue calculations and analysis.
- All transactions contained valid dates, while missing values were identified in quantity, unit price, total spent, and discount fields. 
  These results guided decisions on how incomplete transactions were treated and how revenue metrics were calculated during data transformation.


[**Null Checks**](images/Null%20Checks.png)

No changes were made to the data at this stage. The validation results informed how null values, data types, and business rules were handled during the transformation phase.

## Data Transformation (SQL Views)

- Clean SQL views were created to standardise data types and prepare the data for analysis.
- The 'transactions_clean' view converts raw text fields into appropriate date and numeric formats
and standardises discount indicators(either 0 or 1).
- The same step was taken for the other CSV files (changing the format for Customers and Products).
[**SQL Views(Standardising Dates and Discounts**](images/SQL%20Views(Standardising%20date%20and%20discount%20fields).png)

## Analytical Data Model

- A final analytical view (VIEW 'Sales') was created by joining cleaned transaction data with cleaned product and cleaned customer reference data.
- LEFT JOINs were used to preserve all transaction records while enriching them with product and customer attributes.
- This view will serve as the primary dataset for analysis and reporting.

**Below is an example of the first 10 rows from the final complete Sales VIEW**
()


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
