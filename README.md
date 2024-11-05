### CAPSTONE- LITA PROJECT
### Project Title: Sales Data
### Project Overview 
In this project, I am tasked with analyzing the sales performance of a retail store.
I explored the sales data to uncover key insights such as top-selling products, regional
performance, and monthly sales trends. The goal was to produce an interactive Power BI
dashboard that highlights these findings.
### Data Sources
The primary sources of my data was Sales data.csv 
### Data Tools Used
1. Microsoft Excel [Download here](https://www.microsoftexcel.com) for data cleaning, analysis and visualizaztion
2. SQL for structured data querrying
3. PowerBI for data cleaning, analysis, visualization
4. GitHub for data showcasing and portfolio building 
### Data Cleaning and Preparation
In the initial stage of my data cleaning, I performed the following actions;
1. Data loading and inspection
2. Handling missing variables
3. Data cleaning and formatting
### Exploratory Data Analysis using microsoft excel
o I performed an initial exploration of the sales data, using pivot tables to summarize total sales by product, region, and month.
![report of total sales by products](https://github.com/user-attachments/assets/f0fc8145-eb75-4e1a-b4f5-93b3225e7ff7)

![reports of total sales per region](https://github.com/user-attachments/assets/9ca361d5-d6d9-49dd-9f17-d2fadff03c81)

![Report of total sales by month](https://github.com/user-attachments/assets/16a17b03-989d-4d1a-95a7-53b989d3f172)


o Use Excel formulas to calculate metrics such as average sales per product and total revenue by region.
![Sales data](https://github.com/user-attachments/assets/6f29225e-bd86-4a6a-a4ca-70a80b406d77)
![Sales data revenue by region](https://github.com/user-attachments/assets/1bee7208-0386-4884-98f5-1a9e059395f1)

o Create any other interesting report

![average sales per region](https://github.com/user-attachments/assets/4cc5270b-0fc9-41b1-b0df-c49edf11c244)

### Exploratory Data Analysis using SQL
Queries were writing to extract key insights based on the following questions.

```SQL
SELECT * FROM [dbo].[SalesData]
```
o retrieve the total sales for each product category.
```SQL
SELECT Product,SUM(SALES) Total_Sales FROM SalesData
GROUP BY Product
```

o find the number of sales transactions in each region.
```SQL
SELECT Region,count(SALES) Sales_Transaction FROM SalesData
GROUP BY Region
```
o find the highest-selling product by total sales value.
```SQL
SELECT TOP 1 Product, SUM(Sales) Total_Sales FROM SalesData
GROUP BY Product
Order by Total_Sales desc
```
o calculate total revenue per product.
```SQL
SELECT Product,SUM(SALES) Total_Revenue FROM SalesData
GROUP BY Product
```
o calculate monthly sales totals for the current year.
```SQL
SELECT DATENAME(MONTH,orderdate) [Month], DATENAME(YEAR,orderdate) [Year], SUM(Sales) Monthly_Sales 
FROM SalesData
WHERE DATENAME(YEAR,orderdate) = DATENAME(YEAR,GETDATE()) -- Targeting the current year
GROUP BY DATENAME(YEAR,orderdate), DATENAME(MONTH,orderdate)
```
o find the top 5 customers by total purchase amount.
```SQL
SELECT TOP 5 Customer_Id, SUM(Sales) Total_Purchase FROM SalesData
GROUP BY Customer_Id
Order by Total_Purchase desc
```
o calculate the percentage of total sales contributed by each region.
```SQL
SELECT region,SUM(Sales) total_Sales, (SUM(Sales)*100)/(select SUM(Sales) Total_Sales FROM SalesData) percentage_of_TotalSales 
FROM SalesData
GROUP BY region

```
o identify products with no sales in the last quarter
```SQL
SELECT Product FROM SalesData 
WHERE ORDERDATE  not BETWEEN DATEADD(QUARTER, DATEDIFF(QUARTER, 0, GETDATE()) - 1, 0) AND DATEADD(SECOND, -1, DATEADD(QUARTER, DATEDIFF(QUARTER, 0, GETDATE()), 0))
GROUP BY Product
```

### Exploratory Data Analysis using PowerBI
I was able to create a dashboard that visualizes the insights found in Excel and SQL which include a sales overview, top-performing products, and
regional breakdowns.

![SALES 1](https://github.com/user-attachments/assets/ac0bc0f0-dbdd-41b7-9c5c-96ffd4204931)

![SALES 2](https://github.com/user-attachments/assets/bf3da117-5b50-47b4-825e-bc3e82f4366d)

![SALES 3](https://github.com/user-attachments/assets/49cd2afa-a309-4ba3-891e-b033daf93c8b)


