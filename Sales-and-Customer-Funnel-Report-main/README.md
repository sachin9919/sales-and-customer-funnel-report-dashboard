# Sales and Customer Funnel Report | Power BI Project

##  Overview
This project gives in-depth analysis of e-commerce sales data using Microsoft Power BI, with the aim of uncovering actionable insights into:

- Transaction performance

- Customer purchasing behavior

-  Long-term customer value

By transforming raw e-commerce data into an interactive, dynamic dashboard, this project empowers business stakeholders and decision-makers to Monitor and evaluate key performance indicators (KPIs) such as revenue growth, average order value, and customer lifetime value (CLV).Identifying  purchasing trends across customer segments, time periods, and product categories and to track customer retention and engagement metrics to optimize marketing strategies and sales funnels.

Uncover high-performing products and regions contributing significantly to business success.

Ultimately, this dashboard facilitates data-driven decision-making by delivering clear, visual, and filterable insights into the commercial performance of the e-commerce platform, enabling businesses to act with agility and precision in a competitive digital marketplace.

##  Objectives

- Track the Company's Transactions Performance .
- To track Customer Purchase Behavior.
- Analyze key performance metrics like revenue, customer acquisition cost, and retention.
- Provide actionable insights using advanced DAX measures and interactivity.
- To provide Regional Overview based on Province and Cities.
- Analysis of Sales Trend over time.

---

## Tools & Technologies

- **Power BI Desktop**
- **DAX (Data Analysis Expressions)**
- **Power Query (M language)**
- **Excel (Source data)**

---

## Steps to be Followed 
- Requirement Gathering/ Business Requirements
- Data Walkthrough
- Data Connection
- Data Cleaning / Quality Check
- Data Modeling
- Data Processing
- DAX Calculations
- Dashboard Lay outing
- Charts Development and Formatting
- Dashboard / Report Development
- Insights Generation


## Key Dashboard Visuals

The following visuals are used to represent data meaningfully:

| Visualization | Description |
|---------------|-------------|
| 📉 **Line Chart** | Show the daily trend of the selected measure (e.g., daily Net Sales or daily Repeat Customers). |
| 📊 **Bar/Column Charts** |Comparision of top performing cities and Display sales or customer activity by hour of the day.  |
| 📍 **Donut Chart** |Identify the most and least used payment methods and to detect customer preferences across regions or campaigns. |
| 🧮 **KPI Cards** |Evaluating the overall health and effectiveness of sales operations by tracking Net Sales,Total Quantity and Net Avg Order Value. |
| 🌍 **Map Visual** |Visually represent sales or customer density at a more granular level.|

---


## Parameter Measure

#### This Parameter is used to Make Dashboard Dynamic and Interactive. 

```


Select Measure = {("Net Sales", NAMEOF('Measure Table'[Net Sales]), 0),
("Total Quantity", NAMEOF('Measure Table'[Total Quantity]), 1),
("Total Customers", NAMEOF('Measure Table'[Total Customers]), 2
,("Repeate Rate", NAMEOF('Measure Table'[Repeate Rate]), 3)
}
```

#### DAX measure used in making title dynamic :
```
Dynamic Title = IF('Select Measure'[Select Measure Order]=0,"Net Sales",
IF('Select Measure'[Select Measure Order]=1,"Total Quantity",
IF('Select Measure'[Select Measure Order]=2,"Total Customers",
IF('Select Measure'[Select Measure Order]=3,"Repeat Rate","Other"))))

```
##  Key DAX Measures Used

> Here's a list of custom DAX formulas used to drive insights:

### Funnel Metrics [ Measures Table ]

```dax
Repeat order customer = CALCULATE(COUNTROWS(VALUES(shopify_sales[Customer Id])),FILTER(VALUES(shopify_sales[Customer Id]),CALCULATE(DISTINCTCOUNT(shopify_sales[Order Number]))>1)))

Single order customer = CALCULATE(COUNTROWS(VALUES(shopify_sales[Customer Id])), FILTER(VALUES(shopify_sales[Customer Id]),CALCULATE(DISTINCTCOUNT(shopify_sales[Order Number]))=1))

Purchase Frequency = DISTINCTCOUNT(shopify_sales[Order Number])/[Total Customers])

Product type title = SELECTEDVALUE('Select Measure'[Dynamic Title]) & " by Product Type"

Trend Title = SELECTEDVALUE('Select Measure'[Dynamic Title])&" Trend over Time"

Life Time Value = [Net Sales]/[Total Customers]

Map Title = "Regional Overview - Province & Cities by " & SELECTEDVALUE('Select Measure'[Dynamic Title])

Net Sales = SUM(shopify_sales[Subtotal Price])

Net Average Order Value = AVERAGE(shopify_sales[Subtotal Price])

Retention and Value KPI's = "Retention and Value KPI's "

```

## Business Insights

#### 1. Revenue Performance
- Total Net Sales is $4.17M , which indicates strong overall revenue generation.

- Net Average Order Value is $562.6, suggesting that on average, customers spend a high amount per transaction — valuable for luxury or niche positioning.

- Total Quantity Sold is 7,523 units, meaning fewer units sold at higher price points (indicating a higher-end strategy).

####  2. Customer Behavior
- Out of 4,425 total customers, 2,388 are single-order customers and 2,037 are repeat customers.

- This shows that 46% of customers return to purchase again, which is a healthy repeat rate in retail. However, increasing this further could significantly boost revenue.

- The purchase frequency is 1.68, which also supports the presence of returning customers .

####  3. Sales Trend Over Time
- Net sales show significant fluctuations month-to-month, with a peak of $682,570 and a dip to $524,537.

- The upward spike in the last month suggests potential seasonal demand, successful campaigns, or product launches.

- Business Action: Analyze what caused the spike and replicate it in future marketing strategies.

####  4. Geographic Insights
- Washington, Houston, New York City, El Paso, and Dallas are the top-performing cities by net sales.

- Strong sales clusters are visible across the East Coast and Southern US.

- Business Action: Focus expansion, stock availability, and marketing efforts on high-performing and neighboring regions to leverage established demand.

####  5. Payment Method Preferences
- UPI (58.43%) is the most preferred payment method, followed by Paypal (17.64%) and Gift Cards (16.3%).

- Amazon Payments and Manual represent less than 10% of payments.

- Business Action: Ensure continued support and optimization for UPI . Consider promotional campaigns for underused methods to diversify risk.

####  6. Product Category Insights
- Running Shoes ($1.5M) and Tennis Shoes ($0.9M) dominate sales.

- Walking, Working, and Climbing Shoes follow, with decreasing values.

- Several categories like Boots, Accessories, Kids’ Shoes, etc., show $0 sales, suggesting either low visibility or no availability.

- Business Action:Increase inventory and promotion for top-selling product types.

## Strategic Recommendations
- Boost Repeat Purchases: Target single-order customers with retargeting campaigns or loyalty programs to improve purchase frequency beyond 1.68.

-  Geo-Targeted Marketing: Double down on campaigns in Washington, Texas, and New York markets.


