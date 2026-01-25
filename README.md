## E-Commerce-Retail-Datasets-Project

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

# Sales Data Analysis using SQL and Power BI

# Project Overview


# Tools Used
- CSV
- SQL (SQL Server)
- Power BI

# Data Cleaning
- 
- 
- 
- 

# SQL Analysis Performed
- Monthly sales trends.
- Revenue by region.
- Sales by product category.
- Top customers by total spend.

# Key Insights and Results
- 
- 
- 

# Dashboard
A Power BI dashboard was created to visualise the findings.
