# RETAIL-SALES-ANALYSIS-SQL

# PROJECT OVERVIEW

# Project Title: Retail Sales Analysis
# Level: Beginner
# Database: retail sales

# PROJECT OBJECTIVE
From the given dataset our main objective to find the insights among different aspects. This
project involves setting retail database, perform exploratory data analysis (EDA) and answering
specific business question. This project is helpfull for those people who want to gain hands on 
exprience in the field of data analysis and SQL.

1.Set up a retail sales database: Create and populate a retail sales database with the provided sales data.
2.Data Cleaning: Identify and remove any records with missing or null values.
3.Exploratory Data Analysis (EDA): Perform basic exploratory data analysis to understand the dataset.
4.Business Analysis: Use SQL to answer specific business questions and derive insights from the sales data.

# PROJECT STRUCTURE

# 1. DATABASE SETUP
CREATE DATABASE retail;

CREATE TABLE retail sales
(
    transactions_id INT PRIMARY KEY,
    sale_date DATE,	
    sale_time TIME,
    customer_id INT,	
    gender VARCHAR(10),
    age INT,
    category VARCHAR(35),
    quantity INT,
    price_per_unit FLOAT,	
    cogs FLOAT,
    total_sale FLOAT
);

# 2. DATA ANALYSIS AND FINDING INSIGHTS
# 1. Write a SQL query to retrieve all columns for sales made on '2022-11-05:
 select * from `retail sales` where sale_date="2022-11-05"

# 2.  Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 10 in the month of Nov-2022
 SELECT * FROM `retail sales`
 WHERE category = 'Clothing'
  AND quantiy >=4 AND sale_date >= '2022-11-01'
 AND sale_date < '2022-12-01';

# Q.3 Write a SQL query to calculate the total sales (total_sale) for each category.
 select category,sum(total_sale) as total_sales_category_by from `retail sales`
 group by category

#  Q.4 Write a SQL query to find the average age of customers who purchased items from the 'Beauty' category.
 select round(avg(age),0) as average_sales from `retail sales` where category="Beauty"

# Q.5 Write a SQL query to find all transactions where the total_sale is greater than 1000.
  select * from `retail sales` where total_sale>1000
 
 # Q.6 Write a SQL query to find the total number of transactions (transaction_id) made by each gender in each category.
  select gender,category, count(*) as total_transcation from `retail sales`
  group by gender,category order by total_transcation desc
 
# Q 7 Write a SQL query to find total sales made by each gender in each category
   select gender,category, sum(total_sale) as total_transcation from `retail sales`
  group by gender,category order by total_transcation desc
 
 
 # Q.7 Write a SQL query to calculate the average sale for each month. Find out best selling month in each year
  select sale_date,avg(total_sale) as average_sale from `retail sales` 
  where sale_date>"2022-01-01" and sale_date <= "2022-12-31"
  group by sale_date order by average_sale desc
 
 # Q.8 Write a SQL query to find the top 5 customers based on the highest total sales 
  select customer_id,sum(total_sale) as total_sales from `retail sales`  group by customer_id  
  order by total_sales desc limit 5
 
 
#  Q.9 Write a SQL query to find the number of unique customers who purchased items from each category.
 select category,count(distinct(customer_id)) as total_unique_customer from `retail sales`
 group by category

