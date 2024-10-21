# Retail-Sales-Analysis

📊 Sales Data Analysis Using SQL

Table of Contents

Project Overview

Dataset

Objectives

Technologies Used

Database Design

Key Features

Sample Queries


Setup Instructions

Conclusion

Contributing

License

Project Overview

This project demonstrates how SQL can be used for in-depth sales data analysis. Using a fictional retail sales dataset, the project covers various aspects of business intelligence, including customer behavior analysis, inventory management, store performance, and overall sales trends. The goal is to leverage SQL queries to extract insights that can drive strategic decisions in a retail setting.

Dataset

The 3 key datasets for this case study:

The dataset used in this project consists of several tables:

a. FactTable: The Fact Table has 14 columns mentioned below and 4200 rows. Date, ProductID, Profit, Sales, Margin, COGS, Total Expenses, Marketing, Inventory, Budget Profit, Budget COGS, Budget Margin, Budget
Sales, and Area Code
Note: COGS stands for Cost of Goods Sold

b. ProductTable: The ProductTable has four columns named Product Type, Product, ProductID, and Type. It has 13 rows which can be brokendowninto further details to retrieve the information mentioned in theFactTable. 

c. LocationTable: Finally, the LocationTable has 156 rows and follows a similar approach to ProductTable. It has four columns named AreaCode, State, Market, and Market Size

The primary objectives of this analysis are:

To evaluate sales performance by analyzing revenue, top-selling products, and sales growth over time.

To segment customers based on purchase frequency and average spend.

To analyze store performance and identify high-performing locations.

To optimize inventory by identifying products that are under- or overstocked.

To produce actionable insights that can inform strategic business decisions.

Technologies Used

SQL: Used for querying and analyzing data.

SQL Server: Database management system used to store and manipulate the data.

DBMS Tools: (Optional) pgAdmin, MySQL Workbench, or any SQL IDE for interacting with the database.

Google Sheet: Used for exporting data to visualize key findings.

Database Design

The relational database follows a normalized structure for efficiency:

FactTable (Date, ProductID, Profit, Sales, Margin, COGS, Total Expenses, Marketing, Inventory, Budget Profit, Budget COGS, Budget Margin, Budget, Sales, and Area Code)

ProductsTable (Product Type, Product, ProductID, and Type)

LocationTable (AreaCode, State, Market, and Market Size)


Key Features

1. Sales Performance Analysis
Track overall revenue and break it down by product categories, regions, and store locations.
Calculate key metrics such as Average Order Value (AOV) and Total Revenue per period.

2. Customer Segmentation
Group customers into segments based on Recency, Frequency, and Monetary value (RFM).
Identify high-value customers and develop insights for personalized marketing.

3. Inventory Management
Analyze stock levels and flag low-stock items.
Track fast-moving products and suggest restock quantities.

4. Time-Series Sales Analysis
Perform Month-over-Month (MoM) and Year-over-Year (YoY) analysis to identify sales trends and growth patterns.

5. Store & Employee Performance
Analyze store performance by comparing sales across locations.
Evaluate employee performance based on sales figures.

Sample Queries
Below are some examples of the SQL queries used in the project:

The state wise profit and sales along with the product name.

sql
Copy code
select  location.state, product.product,sum(fact.Sales) as sales ,sum(fact.Profit) as profit from fact join product on fact.productid= product.productid 
join location on fact.area_code=location.area_code
group by state,Product
order by state

Maximum profit along with the product ID and producttype.

sql
Copy code

select fact.productid,product.Product_Type, fact.Profit from fact join product on fact.productid=product.productid 
where profit= (select max(profit) as max_profit from fact)

Average total expense of each product ID on an individual date
sql
Copy code

select date, productid, avg(total_expenses) as Avg_total_expenses from fact 
group by ProductId, Date
order by Date

bash
Copy code
git clone https://github.com/go-cool10/sales-data-analysis-sql.git
Navigate to the project folder:

bash
Copy code
cd sales-data-analysis-sql
Import the dataset:

Load the SQL dump file (/data/sales_data.sql) into your PostgreSQL or MySQL database.
Alternatively, create the tables manually based on the schema provided in /schema.sql.
Execute the SQL queries provided in /queries/ to run the analysis.

Conclusion
This project showcases the power of SQL in performing detailed sales analysis in a retail context. From customer segmentation to store performance tracking, this analysis can help businesses make data-driven decisions.

Feel free to explore the SQL scripts and sample queries to gain insights into how data can be used to optimize sales operations.

Contributing
Contributions are welcome! Feel free to submit issues, fork the repository, or create pull requests to suggest improvements or new features.
