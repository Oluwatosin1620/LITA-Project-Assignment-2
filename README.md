# Project Title: Customer Data

[Project Overview](project-overview)
[Key Features](ket-features)
[Data Tools](data-tools)
[Microsoft Excel](microsoft-excel)
[Exploratory Data Analysis ](exploratory-data-analysis)
[Insights Derived](insights-derived)
[SQL](SQL)
[POWER BI](power-bi)
 
### Project Overview
This is an analysis and visualization of customer data using Excel, SQL, and Power BI, to subscription trends of customers. This project, part of my GitHub portfolio, also showcases my proficiency in data storytelling and highlights my ability to transform raw data into actionable insights with advanced tools confidently.

### Data Source
Our facilitator provided this dataset.


### Dataset Description
This dataset provides comprehensive information on customer subscriptions, including details on individual subscription types, durations, and revenue generation. The primary aim is to analyze customer behaviours, subscription trends, and revenue patterns across different regions, helping to guide marketing and retention strategies. This data contains 33,787 rows and 8 columns, while an additional column was added in the cleaning process, making it a total of 9 columns.

---

### Key Features:
**CustomerID**: A unique identifier for each customer.
**CustomerName**: The name of the customer.
**Region**: The geographical region where the customer is located, useful for analyzing trends based on location.
**SubscriptionType**: The type of subscription each customer has selected.
**SubscriptionStart**: The date when the customer's subscription began.
**SubscriptionEnd**: The date when the customer's subscription is scheduled to end.
**Cancelled**: An indicator denoting whether the customer has cancelled their subscription.
**Revenue**: The total revenue generated from each customer’s subscription.


### Data Tools
* Microsoft Excel, for:
  > Data cleaning;
  > Data Analysis and Summarization.
* SQL [Structured Query Language] for Querying data
* Power BI for Data Visualization
* GitHub for Portfolio building


## Microsoft Excel [VIEW PROJECT](https://us.docworkspace.com/d/sIBKeupNZsc6YuQY)
---
Microsoft Excel is a spreadsheet tool for data organization (cleaning and preparation), analysis, and visualization. It offers formulas, pivot tables, and charts, enabling users to manage and interpret data.

**Data Cleaning and Preparation**: Processing the raw data to ensure it is ready for analysis. Steps taken:
> Removing Duplicates: The initial rows of the data were 50001, but after removing duplicates, 33787 rows were left. No missing values were found; 
> Adding filters


### Exploratory Data Analysis
The following insights will be drawn:
* Which region has the highest sales?
* What product was sold the most?
* What month had the highest sales each year?
* What quantity of product was sold in each month of the year?
* What is the total number of products sold in the year?
* What is the total revenue of products sold in each region?
* Which region is best for business?
* Which product should the business focus more on?
* What is the total revenue derived from each product?
* What is the average sales for each product? And many more...


  ### Data Visualization
  **Pivot Table** a data summarization tool found in MS Excel was used for visualization.
  
**Insights Derived**:
1. **Region with the highest Sales**:	

![Total Revenue by Region](https://github.com/user-attachments/assets/cc057deb-cd66-4a05-87a3-1334e0aaf65d)
![image](https://github.com/user-attachments/assets/411ac86b-f729-47f3-9c9e-f0bad8b73611)


**key Finding**
Based on this analysis, the South Region has the highest sales, followed by the East Region, while the West Region has the lowest sales. Though the business is doing well in all regions, it should focus more on the South Region, which has a huge sales difference from others.

2. **Product that was sold the most**;

![Total Sales by Product](https://github.com/user-attachments/assets/c3d7def7-d6cb-442f-9b9f-6bed8c281312)
![image](https://github.com/user-attachments/assets/ae64607c-3a54-44a8-8888-442004daaf8e)


**Key Finding**
This analysis shows that shoes were the the most sold product with a total of 613,380 followed by shirts which had a total of 485,600 and socks coming as the least with totals of 180,785. 

3. **What month had the highest sales each year**;

![Total Sales by Month](https://github.com/user-attachments/assets/dc651dfe-c073-44af-ab93-6170d3a965b8)
![image](https://github.com/user-attachments/assets/04b218d5-72fd-4016-82c8-441da280d5f6)


**Key Finding**
It shows that in 2023 and 2024, February had the highest sales. July was the second-highest sales in 2023, but in 2024, Jul declined in sales, and Jan had the second-highest total sales.

4. **What are the average sales of products sold**;
   
![Average Sales by Product](https://github.com/user-attachments/assets/8de4825c-6816-484f-b2b4-a5a1645913c4)
![image](https://github.com/user-attachments/assets/14fab66c-0922-4257-bf9d-904574c40e2d)


5. **What is the total revenue of products sold in each region**?    
  
![Total Revenue by Region](https://github.com/user-attachments/assets/715259c0-4a91-4015-9ea2-5bdc5e827e79)
![image](https://github.com/user-attachments/assets/ce788d61-9f5a-4b31-b28b-8f0848ddf26e)


6. **What is the total No of products sold in a month at each region**;

![Total Product by Month and Region](https://github.com/user-attachments/assets/aaa55f49-39b6-4f95-bc80-ec2a4d9ae108)

**Key Findings**
In this analysis, lots of insights were generated. It answers the questions:

  * What is the total No of products sold in 2023? **5,952**
  * How many product types were sold in each month? **1**
  * How many products were sold in Jan? **496**
  * What is the total No of products sold in 2024? **3,969**
    
In Summary, the business focuses on a particular type of product and a specific region each month. There was only a change in the product type in August when the business initially sold shoes in 2023 but later changed to selling Hats in 2024.  
  

## SQL (STANDARD QUERY LANGUAGE)
---
It is used for querying, storing and managing data in a database. The following queries: were derived in the analysis:

**Insights Derived**:
1. Retrieve the total number of customers from each region:

~~~ SQL
SELECT region, count(customerID) as TotalCustomers
from [dbo].[LITA Capstone Dataset11]
Group by region
order by TotalCustomers
~~~

2. Find the most popular subscription type by the number of customers:

~~~ SQL
SELECT SubscriptionType, count(customerid) as MostPopular
FROM [dbo].[LITA Capstone Dataset11]
GROUP BY SubscriptionType
ORDER BY MostPopular
~~~

3. Find customers who cancelled their subscription within 6 months:
   
~~~ SQL
select *,
   DATEDIFF(month, SubscriptionStart, subscriptionend) as subscription_month
from [dbo].[LITA Capstone Dataset11]
where
    canceled = 1
    and DATEDIFF(month, subscriptionstart, subscriptionend) <= 6
order by 
    subscription_month;
~~~

4. Calculate the average subscription duration for all customers:

~~~ SQL
SELECT AVG(datediff(month, subscriptionstart, subscriptionend)) 
 as Averagesubscription
from [dbo].[LITA Capstone Dataset11]
~~~

5. Find customers with subscriptions longer than 12 months:

~~~ SQL
select *,
    DATEDIFF(month, SubscriptionStart, subscriptionend) as subscription_month
from [dbo].[LITA Capstone Dataset11]
where
    canceled = 1
    and DATEDIFF(month, subscriptionstart, subscriptionend) >12 
order by 
    subscription_month;
~~~

6. Calculate total revenue by subscription type:

~~~ SQL
SELECT SubscriptionType, sum(CAST(revenue AS INT)) as TotalRevenue
from [dbo].[LITA Capstone Dataset11]
group by subscriptiontype
order by TotalRevenue
~~~

7. Find the top 3 regions by subscription cancellations:

~~~ SQL
select top 3 region, count(*) as Total_cancel
from [dbo].[LITA Capstone Dataset11]
where canceled = 1
group by region
order by Total_Cancel desc
~~~

8. Find the total number of active and cancelled subscriptions:

~~~ SQL
select case when canceled = 0 then 'Active_Sub'
	else 'Canceled_Sub' end as Subscription_Status, 
Canceled, count(*) as Total_cancel
from [dbo].[LITA Capstone Dataset11]
group by canceled
order by Total_Cancel desc
~~~


## POWER BI
A data Visualization and business intelligence tool for converting data from different sources to interactive dashboards. The Excel file was loaded and transformed before visualization was performed, A calculated column was created to attain the Duration.





![CustomerData Dashboard](https://github.com/user-attachments/assets/72854ad1-0471-4231-b624-4eec797251bc)

![CustomerData Dashboard 2](https://github.com/user-attachments/assets/12719791-70fd-4263-8a8c-f0890f690257)


