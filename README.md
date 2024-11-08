# Project Title: Customer Data

[Project Overview](#project-overview)

[Key Features](#ket-features)

[Data Tools](#data-tools)

[Microsoft Excel](#microsoft-excel)

[Exploratory Data Analysis ](#exploratory-data-analysis)

[Insights Derived](#insights-derived)

[SQL](#SQL)

[POWER BI](#power-bi)

 
### Project Overview
This is an analysis and visualization of customer data using Excel, SQL, and Power BI on customer subscription trends. This project, part of my GitHub portfolio, also showcases my proficiency in data storytelling and highlights my ability to transform raw data into actionable insights with advanced tools confidently.

### Data Source
Our facilitator provided this dataset.


### Dataset Description
This dataset provides comprehensive information on customer subscriptions, including details on individual subscription types, durations, and revenue generation. The primary aim is to analyze customer behaviours, subscription trends, and revenue patterns across different regions, helping to guide marketing and retention strategies. This data contains 33,787 rows and 8 columns, while additional columns were added in the cleaning process, making it a total of 11 columns.

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
> Removing Duplicates: The initial rows of the data were 75000, but after removing duplicates, 33787 rows were left. No missing values were found; 
> Adding filters


### Exploratory Data Analysis
The following insights will be drawn:
* Which region has the largest revenue?
* What is the most popular subscription type?
* What is the total revenue by subscription type?
* Which region has the most cancelled subscriptions? Top 3.
* What is the total number of active and cancelled subscriptions?
* What is the total duration of subscription in each region?
* What is the cancellation rate by customers?
* How many customers had subscriptions longer than 12 months?
* How many customers cancelled their subscriptions within 6 months?
* What is the total number of customers by subscription?
* Which region is best for business?
* Which region should the business focus more on?
* What is the total revenue derived from each subscription type?
* What is the average subscription duration for all customers? And many more...


  ### Data Visualization
  **Pivot Table** a data summarization tool found in MS Excel was used for visualization.
  
**Insights Derived**:

1. **Which region has the largest revenue**:	

![Total Revenue by Region](https://github.com/user-attachments/assets/cc057deb-cd66-4a05-87a3-1334e0aaf65d)
![image](https://github.com/user-attachments/assets/1ff7d808-5858-4650-afe5-d748fbb4759d)
![image](https://github.com/user-attachments/assets/8b48c719-d708-427b-9c53-2daf2942348f)

**key Finding**
Based on this analysis, the East Region has the highest revenue, followed by the South Region, while the North Region has the lowest revenue. The business is doing well in all regions. The basic subscription type should be introduced in the south and west regions. which will also bring more revenue to the business.


2. **What is the average subscription duration for all customers**;

![Average Subscription Duration](https://github.com/user-attachments/assets/37cdc783-721b-4586-9798-2208293c0546)
![image](https://github.com/user-attachments/assets/9afcc55b-4e69-421a-bf18-815451d37ad9)

**Key Finding**
This analysis shows that all subscription durations have equal span.


3. **What is the total duration of subscription in each region**;


![Total Duration by Region](https://github.com/user-attachments/assets/02b5f04a-eaf4-4b28-812c-73566705d954)
![image](https://github.com/user-attachments/assets/5a53192a-3898-4362-ae40-fb65122ae985)


4. **What is the total cancellation rate by customers**;
   

![Total Cancellations by Customers](https://github.com/user-attachments/assets/5ccad6da-5412-4050-bbda-2f466409ce1d)
![image](https://github.com/user-attachments/assets/0b52f759-d33e-4e9f-b30d-a3c93b43fd58)


5. **What is the most popular subscription type**?    
  

![Most popular Subscription Type](https://github.com/user-attachments/assets/2d10d420-65af-46ad-8e81-32f68d24bbb7)
![image](https://github.com/user-attachments/assets/1763453f-fc08-4811-9b82-cec7b93a4a40)


6. **What is the subscription trend at start and end date**;


![Subscription Trends](https://github.com/user-attachments/assets/052d7690-ce39-4a6b-b231-91ef109764e1)
![image](https://github.com/user-attachments/assets/07b7af75-d761-408f-b123-93e039090e39)
![image](https://github.com/user-attachments/assets/965e4e56-ad2d-49a5-b979-4317c6cae1c9)




**Key Findings**
In this analysis, lots of insights were generated. It answers the questions:

  * What is the total revenue for active subscriptions? **37,208,727**
  * How many subscription types were subscribed for in each month? **1**
  * How many subscription types were focused on in each region? **1**
  * What is the total revenue for cancelled subscriptions? **30,331,448**
    
In Summary, a particular type of subscription was subscribed for each month and a particular type of subscription in each region.   
  

## SQL (STANDARD QUERY LANGUAGE)
---
It is used for querying, storing and managing data in a database. The following queries: were derived in the analysis:

**Insights Derived**:

1. **Retrieve the total number of customers from each region**:

~~~ SQL
SELECT region, count(customerID) as TotalCustomers
from [dbo].[LITA Capstone Dataset11]
Group by region
order by TotalCustomers
~~~

2. **Find the most popular subscription type by the number of customers**:

~~~ SQL
SELECT SubscriptionType, count(customerid) as MostPopular
FROM [dbo].[LITA Capstone Dataset11]
GROUP BY SubscriptionType
ORDER BY MostPopular
~~~

3. **Find customers who cancelled their subscription within 6 months**:
   
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

4. **Calculate the average subscription duration for all customers**:

~~~ SQL
SELECT AVG(datediff(month, subscriptionstart, subscriptionend)) 
 as Averagesubscription
from [dbo].[LITA Capstone Dataset11]
~~~

5. **Find customers with subscriptions longer than 12 months**:

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

6. **Calculate total revenue by subscription type**:

~~~ SQL
SELECT SubscriptionType, sum(CAST(revenue AS INT)) as TotalRevenue
from [dbo].[LITA Capstone Dataset11]
group by subscriptiontype
order by TotalRevenue
~~~

7. **Find the top 3 regions by subscription cancellations**:

~~~ SQL
select top 3 region, count(*) as Total_cancel
from [dbo].[LITA Capstone Dataset11]
where canceled = 1
group by region
order by Total_Cancel desc
~~~

8. **Find the total number of active and cancelled subscriptions**:

~~~ SQL
select case when canceled = 0 then 'Active_Sub'
	else 'Canceled_Sub' end as Subscription_Status, 
Canceled, count(*) as Total_cancel
from [dbo].[LITA Capstone Dataset11]
group by canceled
order by Total_Cancel desc
~~~


## POWER BI
A data Visualization and business intelligence tool for converting data from different sources to interactive dashboards. The following are required to be presented on the visualization tool:

1. Build a Power BI dashboard that visualizes key customer segments, cancellations, and subscription trends.
2. Include slicers for interactive analysis.

    The Excel file was loaded and transformed before visualization was performed, A conditional column was created to attain the Region Sort and Cancelled Range, while a calculated column was created to attain the Duration. The column quality, profile, and distribution were checked and are ready for visualization.
   

![CustomerData Quality](https://github.com/user-attachments/assets/18e981f6-2a6d-4bd1-8d29-ae32d6589af2)

### Data Visualization


![CustomerData Dashboard](https://github.com/user-attachments/assets/72854ad1-0471-4231-b624-4eec797251bc)

![CustomerData Dashboard 2](https://github.com/user-attachments/assets/12719791-70fd-4263-8a8c-f0890f690257)


**INSIGHTS DRIVEN**

The customer dataset of this business provides a detailed look into the profiles and engagement of 33,787 unique customers, each contributing valuable insights into revenue streams, subscription preferences, and regional performance. Initially, this dataset contained 75,000 rows across 8 columns, but after removing duplicates, it was reduced to 33,787 unique entries, with additional columns added to capture essential details such as "Cancellation Range," "Region Sort," and "Subscription Duration." These enhancements bring the total column count to 11.

The data shows that from previous years up to the present, the business has generated an impressive total revenue of 67,540,175. Among the four regions, the East stands out as the top performer, contributing a substantial 16,958,763 to the overall revenue. The South follows closely, while the North records the lowest revenue at 16,817,972. Despite these differences, each region yields a strong revenue stream, indicating that all areas are profitable and vital to the business’s overall success.

This dataset also reveals customer behaviour regarding subscription types and durations. Each customer subscribed for one year, with the East and North favouring the Basic subscription, the West opting for the Standard type, and the South preferring the Premium subscription. Basic subscriptions were the most popular overall, totalling 6,181,221 in revenue—a significant portion of the business’s income.

Customer retention and cancellations provide further insights. Out of the total customers, 18,612 maintained their subscriptions, while 15,175 chose to cancel. Interestingly, the East region saw no subscription cancellations, highlighting its high retention rate, while the North, South, and West experienced notable cancellations, with figures at 10,093,242; 10,126,800; and 10,111,406, respectively. The East region also led in active subscriptions, with 8,488 customers subscribed to the Basic plan. The South came in second, with 8,420 subscribers on the Premium plan, while the North trailed slightly with 8,433 active subscribers.

These findings suggest growth opportunities: with high profitability across all regions, the business could consider expanding subscription options to enhance customer satisfaction and diversify its revenue base further. The popularity of the Basic subscription and the minimal cancellations in the East region underscore a valuable trend that could be mirrored in other regions to boost retention and engagement.
