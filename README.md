# GlobalMart-Sales-Perfomance-Analysis
This is a Global Mart Sales performance analysis project.

Executive Summary
This report analyzes Global Mart Sales Performance across diverse products and geographical locations (State and Region) to identify key revenue(sales) drivers, profit gaps and improvement opportunities. The analysis reveals that Ohio delivers a 69.02% profit margin with $58.52K in sales, showing strong profitability despite lower revenue, while Pennsylvania yields the highest sales ($69.67K) but only a 61.35% margin, suggesting discounting or cost pressures. Based on these findings, I recommend:
	A review of Pennsylvania’s discount levels/policies to reduce unnecessary profit leakage. 
	Increase marketing and promoting within Ohio and other low-revenue and high-profit areas such as Illinois and Florida. 
	Exploring different pricing models to align better with market demand and operational costs across different states.
Implementing these strategies will help significantly increase sales and profit across the states.

1. Business Understanding
1.1. Business Problem & Objectives
The primary objective of this project is to evaluate the business sales performance. The goal is to analyze data to gain deeper insights sales vs profit performance, sale trends, and identify growth opportunities for the business.
The key business questions we aim to answer are:
1.	Sales Performance: How is business performance in relation to by sales and profit? What is the comparison between current sales and sales last year? How does a discount affect sales and overall profit? Does shipping time affect sales? What are the sales trends over time? 
2.	Regional Performance: How are the sales and profit performance across various states and regions? How does the geographical location affect overall revenue and profit?
3.	Product Analysis: How many products are in the company’s portfolio? Which category, subcategory, and product has higher sales and profits? What are the best and worst performing products?
4.	Customer Analysis: How many customers has the business had? How is customer distribution by state and region? What type of customers is the business dealing with? What is the average purchasing power for each customer?
5.	Actionable Insights: What’s next after uncovering these insights from the data? What actionable recommendations can I provide to boost sales, drive profit, and address existing opportunities?
   
1.2. Project Goals & Success Criteria
This analysis will be considered successful if it delivers the following outcomes:
●	Identified Opportunities: Identify top products (Category, Subcategory, and Product Name) with the highest sales and profit margin performance.
●	Trend Analysis: Identify sales trend across the 2 fiscal years.
●	Sales and Profit Inefficiency: Identify sales and profit margin performance over the years.
●	Strategic Recommendations: At least three concrete, data-supported recommendations to improve sales growth and bridge opportunities.
●	Interactive Dashboard and Report: A functional dashboard and report in Power BI that allows stakeholders to explore the data dynamically and identify relevant insights.
2. Data Understanding
2.1. Data Source
The dataset used for this analysis is the GlobalMart_Sales_Data.xlsx  file, containing order details, order dates and shipping dates, sales, and product details (Category, Sub-Category, Product Name).

3. Data Preparation
To ensure the accuracy and reliability of the analysis, the following data preparation steps were performed:
1.	Data Cleaning:
○	Missing Values: Filled 51 rows where Order Date, Region and Sales data was null.
o	Used average of sales to fill missing sales values.
o	Used Fill Down to fill null values in the Region Column.
o	Used average shipping time across product categories to calculate missing Order Dates (Shipping date – Average Time).
○	Data Errors: Removed 9 errors from the Order Date and Quantity column.
○	Duplicates: Reviewed the data and removed 10 duplicate rows based on the Order ID column.
○	Standardization: Corrected inconsistent naming in the Region column and Product Name fields (“WEST”, “west” to “West”) Capitalized each word for each in the two columns.
○	Outliers and Anomalies: Identified outlier such as 500,000, 10,000, -5, -100 in sales column. Replaced the outliers and anomalies with reasonable data points with the data distribution and profit. 
○	Left with a dataset of 991 rows to complete the analysis.

3.	Data Enrichment/Feature Engineering:
○	Created a Profit Margin column, calculated as (Net Profit / Sales) * 100, to standardize profitability measurement across transactions of different sizes.
○	Created a Shipping Time column, calculated as (Shipping Date – Order Date) to easily analyze sales performance against shipping time.
○	Created a Date table using DAX. Extracted Year, Quarter, Month, and Day from the Order Date column to facilitate time-series analysis.
○	Created a Customer Band/Segment Column using IF function. Assigned categories such as “High Value”, “Medium Value”, and “Low Value” customers.
○	Introduced measures such as Total Profit, Total Sales, Sales PY (Past Year), YoY(%), Average Sales, Average Profit Margin and Sales YTD (Year to Date).

4.	Data Transformation:
○	Converted data types for the Sales, Profit columns to currency (Fixed Decimal) with two decimal points.
○	Transformed Discount from decimal numbers to Percentage.
○	Normalized the Global Mart sales performance dataset, to 1 fact table and 5 dimension tables including Region, State, Sub-category, Products and Date tables to configure a star schema, create relationships and reduce redundancy within the dataset.

5. Analysis & Findings
This section addresses the core business questions through descriptive analytics.

Finding 1: “Office Supplies” are the highest performing in revenue and profit.
The analysis shows a significant concentration of performance in a few key products.
●	What: Office Supplies generated $174.93K in revenue (sales) and a 64.09% profit margin, proving to the best performing category by revenue and profit. However there is quite a small difference between the other categories “Technology” with 163.26K in revenue and 62.78% profit margin, and “Furniture” with $161.24K in revenue and 62.68% profit margin.
●	So What: This indicates a healthy balance in positioning and competition across the categories. While Office Supplies are the most performing, furniture and technology also contribute significantly to the company performance without the risk of over-reliance.
●	Supporting Evidence: (Placeholder for a doughnut chart: Total Profit by category & sub-category)
Category	Total Sales	Total Profit	Average Profit Margin
Office Supplies	$174,925.98	$ 121, 294.12	64.09%
Technology	$163.262.70	$111,004.41	62.78%
Furniture	$161,238.88	$111,686.21	62.68%

Finding 2: “Pens” are the highest performing sub-category (Product) in revenue and profit.
The analysis shows a significant concentration of performance in a few key products.
●	What: Pens are the leading sub-category with generated $70.25K in revenue (sales) and a 64.89% profit margin. All categories have a significant performance of (61% - 65%) in profit margin indicating health competition across the product portfolio.
●	So What: Since performance is balanced, the company is not overly reliant on one sub-category, which is good for risk management. However, it also means that incremental improvements in any single category could shift overall sales performance significantly.
●	Supporting Evidence: (Placeholder for a Combined Column and Line Chart: Total sales and profit margin by sub-category)
Sub-Category	Total Sales	Total Profit	Average Profit Margin
Pens	$70.25K	$49.09K	64.89%
Chairs	$56.39K	$39.75K	64.28%
Accessories	$53.85K	$36.6K	63.87%
Paper	$53.05K	$35.98K	63.85%
Binders	$51.62K	$36.23K	63.31%
Laptops	$59.53K	$40.13K	62.63%
Tables	$55.67K	$37.72K	62.28%
Phones	$49.88K	$34.27K	61.86%
Bookcases	$49.18K	$34.22K	61.32%

Finding 3: Ohio is the most profitable, while Pennsylvania is the most performing state by sales.
●	What: Ohio is the most performing state by profit (69.02%) despite showing very minimal revenue ($58.52K) as compared to other states. Pennsylvania on the other hand demonstrates moderately low profit margin (61.35%) despite being the leading state in revenue ($69.67K).
●	So What: The low profit margin in Pennsylvania may be due to high discounts which significantly affect profit. Additionally, profitability affected by differences in market dynamics, product mix, or higher costs. 
●	Supporting Evidence: (Placeholder for a Scatter Plot: Discount and Profit Margin) (Placeholder for a Filled Map: Sales and Profit by State)

Finding 4: ‘Q2 and Q3” are the most performing season of the year with July as the best performing month by average sales.
●	What: Quarter 2 and 3 is most performing month with $126.93K in sales and average of $524.49. June is the most performing month by average sales of $552.74. Sale starts to skyrocket from May to August. All product categories perform best during the 3rd quarter apart from Furniture which is significantly low with average sales of $482.83 across the two fiscal years.
●	So What: This suggests that there is possible high season for products during the 2nd and 3rd quarter. This seasonal increase in sales signals a strategic opportunity to capitalize on demand by increasing inventory, marketing, and promotional efforts in late Q1 to maximize performance.
●	Supporting Evidence: (Placeholder for a Line Chart: Avg Sales by Month), (Placeholder for an Area Chart: Avg Sales by Month and Category)

6. Evaluation of Results
The analysis successfully addressed the initial business questions. We identified sales and profit performance across Categories, Sub-Categories, States, etc, highlighted sales trends overtime and uncovered relationships discount impact on Profit.
The descriptive statistics confirm the high variability in the data:
●	Mean Profit: $347.11
●	Standard Deviation of Profit: $222.32 
●	Coefficient Value: 64% (The standard deviation within the profit dataset is high indicating data distribution within a wide range)
●	Range of Profit: -$25.55 to $962.90 (The presence of negative profit transactions is a key finding.)
●	Mean Sales: $503.96
●	Standard Deviation of Sales: $270.93 
●	Coefficient Value: 54% (The standard deviation and co-efficient value indicates dataset deviates further from the mean)
●	Range of Sales: From $ 20.46 - $1000 (Data is distributed within a wide range typically impacting the mean/average)
Limitations: The current data does not include the production and distribution cost of goods. A deeper analysis incorporating these variables could help determine their impact on pricing strategy affecting sales and customer behaviour, and overall net profitability.

8. Recommendations & Next Steps
Based on the findings, we propose the following actions:
1.	Recommendation 1: Optimize Pricing and Discount Strategies by State
○	Why: Ohio delivers 69.02% profit margin with $58.52K in sales (among the least performing states in revenue), showing strong profitability despite lower revenue. Pennsylvania, meanwhile, brings the highest sales ($69.67K) but only a 61.35% margin (among least performing state by profit margin), suggesting discounting or cost pressures.
○	Action: Review Pennsylvania’s discount levels to reduce unnecessary profit leakage. Explore different pricing models to align better with market demand and operational costs.
○	Expected Impact: Closing the profit margin gap in Pennsylvania could skyrocket the company profits as there is already noticeable demand within the state.

3.	Recommendation 2: Develop targeted promotions for high performing sub-categories such as Pens, Chairs and Accessories. 
○	Why: Pens generate $70.25K in revenue with a 64.89% margin, outperforming all sub-categories. Chairs and Accessories also show strong returns with $56.39K (64.28% margin) and $53.85K (63.87% margin).
o	Action: Offer loyalty discounts on the already high-profit margin items. Promote these products more heavily in marketing campaigns.
o	Expected Impact: Potential increase in sales and a significant boost on profit margin.

5.	Recommendation 3: Develop an upselling and cross-selling strategies to prevent over-reliance on key products.
○	Why: While Pens lead at $70.25K revenue, many sub-categories trail significantly — e.g., Phones ($49.88K) and Bookcases ($49.18K). Current performance is concentrated in just a few products, leaving untapped growth potential. 
○	Action: Develop bundled offers (Pens + Paper + Binders, Chairs + Tables, Laptops + Accessories, Phones + Accessories) to boost the visibility and performance of underperforming products.
○	Expected Impact: Potential increase in sales across the least performing products and subsequent increase in profitability.

4.	Recommendation 4: Capitalize on Seasonal Demand in the end of Q2 and the beginning of Q3
○	Why: Quarter 2 and 3 contributes $206.92K in sales as compared to quarter 1 and 4, the highest across all periods, with average monthly sales of $524.49 over the two fiscal years. July stands out with averages of $552.74 and strong peaks from May to August. 
○	Action: Boost inventory and marketing in early Q2 to take advantage of the rising demand in towards the end of Q2 and beginning Q3.
○	Expected Impact: Strategic promotion in Q2 and Q3 could raise annual sales.


