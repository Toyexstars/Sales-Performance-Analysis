# Project Title: Retail Store Analysis

## Project Outline

[Project Overview](#project-overview)

[Data Source](#data-source)

[Tools Used](#tools-used)

[Visualization](#visualization)

[Result/Findings](#result-findings)

[Recommendation](#recommendation)

[Conclusion](#conclusion)

## Project Overview
This project aimed at analyzing sales performance of a retail store in order to uncover key insight such as top-selling products, regional performance and monthly sales trends.
Also, make data driven recommendation useful for decision making.

## Data Source
The primary data used is LITA Capstone Sales dataset used during the training. [Sales Data.xlsx](https://github.com/user-attachments/files/17561916/Sales.Data.xlsx)


## Tools Used
 - Miscrosoft Excel
 - MYSQL Workbench

 - Power BI

## Microsoft Excel Analysis
 - Summarize total sales by product, region and month using Pivot Table.
 - Excel formula to calculate average sales per product and total revenue by region.
    1. Average Sales Per Product = AVERAGEIF(Table1[Product],C2,Table1[Quantity])
    2. Total Revenue Per Region = SUMIF(Table 1[Region], D2, (Table 1[Revenue])
 - Create interesting report

## Pivot Table
It summarizes the total sales by product, region and month.
<img width="658" alt="Sales Pivot Table" src="https://github.com/user-attachments/assets/30d9f306-9d82-43c8-b102-f6a27dff6286">


## Excel Report Dashboard
 <img width="578" alt="Excel Dashboard" src="https://github.com/user-attachments/assets/f3a5881a-23f6-4c49-aac4-e6bf84bcd87d">





## SQL Analysis
 This aspect involves writing queries to answer the following questions:
  - Total Sales for each product category (Total quantity was used as total sales)
  - Number of sales transaction in each region
  - Highest-Selling product by total sales value
  - Total Revenue per product (Quantity * Price was used as revenue)
  - Monthly sales total for the current year
  - Top 5 customers by total purchase amount.
  - Percentage of total sales by each region
  - Products with no sales in the last quarter

## SQL Queries (Structured Query Language)
The following are some of the queries used to answer the questions above:

 - Total Sales for each product category
```SQL
 SELECT Product, SUM(Quantity) AS TotalSales_ProductCategory FROM Salesdata
 GROUP BY Product
 ORDER BY 2 DESC;
```

 - Number of sales transaction in each region
```SQL
 SELECT region, COUNT(quantity) AS No_Sales_Per_Region FROM Salesdata
 GROUP BY region
 ORDER BY 2 DESC;
```

  - Highest-Selling product by total sales value
```SQL
 SELECT Product, SUM(quantity * Price) AS Highest_Selling_Product FROM salesdata
 GROUP BY Product
 LIMIT 1;
```

 - Total Revenue per product
```SQL
 SELECT product, SUM(quantity * Price) AS Total_Revenue_Per_Product FROM salesdata
 GROUP BY product
 ORDER bY 2 DESC;
```

 - Monthly sales total for the current year
```SQL
 SELECT MONTH(orderdate) AS Month, Sum(quantity) AS Total_Sales FROM salesdata
 WHERE YEAR(orderdate) = YEAR(CURRENT_DATE)
 GROUP BY MONTH(orderdate)
 ORDER BY Month;
```
 - Top 5 customers by total purchase amount.
```SQL
 SELECT customer_id, sum(Quantity*Price) AS Total_Purchase_Amount FROM salesdata
 GROUP BY customer_id
 ORDER BY 2 desc
 LIMIT 5;
```

- Percentage of total sales by each region
```SQL
 SELECT Product, SUM(Quantity) * 100 / (SELECT SUM(Quantity) FROM salesdata) AS Percentage_Sales_Region
 FROM salesdata
 GROUP BY Product;
```

- Products with no sales in the last quarter
```SQL
 SELECT Product FROM saledata
 GROUP BY Product
 HAVING SUM(CASE
 WHEN OrderDate Between '2024-06-01' AND '2024-O8-31'
 THEN 1 ELSE 0 END) = 0;
```

## Power BI Dashboard 

 - KPI'S Requirement (Key Performance Indicator)
    1. Total Sales Analysis: Examine the overall sales performance to gain insight to product demand.
    2. Total Revenue Analysis: Examine the overall revenue made from sales by multiplying quantity by price per unit.
    3. Total Customers: Determine all the customers by counting the Customer Id.
    4. Profitability Analysis: Examine the difference between the Total Revenue and Total Sales.
    5. Average Sales: Determine the average sales from the total quantity
 - Chart Requirement
   1. Total Sales by Month (Area Chart): Visualize the monthly distribution of total sales.
   2. Yearly Sales by Product (Matrix Chart): Visualize the current sales and previous sales by product.
   3. Total Sales by Region (Donut Chart): Visualize the distribution of sales by region.
   4. Total Sales by Product (Bar Chart): To determine sales from each product.
   5. Average Sales by Product (Bar Chart): To visualize average sales made from each product.

## Visualization

<img width="484" alt="Sales Dashboard" src="https://github.com/user-attachments/assets/c37be1a7-817a-4ea6-98ef-f7ed3ff62b6f">



## Result/Findings
- The top selling product based on quantity in year 2023 was shirt while top selling product based on quantity in 2024 is hat. The store made a lot sales due to children school party.
- The store made highest sales in "South Region" in 2023 and 2024 while made the lowest sales in "West Region".
- The store made the highest sales in the month of June as a result of seasonal celebration.


## Recommendation
Based on the result and findings:
- The store should focus marketing efforts on the sales of hat and shirt.
- Building and upselling opportunities in other products.
- Allocate more resources to the South Region and and develop targeted marketing campaigns for other regions.
- Implementation of discount offers and continuous monitoring of sales data to respond quickly to emerging trend.


## Conclusion
This report provides a clear overview of sales performance, highlighting area of strength  and opportunities for growth.
