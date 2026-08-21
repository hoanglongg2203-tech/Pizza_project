# Pizza Restaurant Sales Performance | Power BI 
## Business Context

Despite having a full year of sales data, the restaurant still lacked clear visibility into what actually drives revenue and customer behavior.
This project focuses on turning raw transactional data into meaningful insights and more importantly, translating those insights into practical business actions.
## Problem Statement
**The business had access to data but lacked clear insights to answer key questions.**
- Which products and sizes truly drive revenue, not just volume?
- Are there seasonal trends that should influence planning decisions?
- When do customers actually order and how does that change over time?
## Objectives
- Data Extraction & Cleaning: Extracted transactional data using SQL and cleaned 48,620 records in Power Query, standardizing formats and removing duplicates to ensure data integrity.
- Data Modeling: Developed a relational data model in Power BI, including a custom calendar table and optimized relationships to support time-series analysis across orders, categories, and sizes.
- Business Intelligence: Built a 3-page interactive dashboard with dynamic metric selection  and key DAX measures, identifying revenue drivers, seasonal trends, and customer ordering patterns.

##  Tools 
- Power BI — dashboard development & data modeling.
- DAX — KPI calculations, time intelligence.
- SQL (MS SQL Server) — data extraction.

## Data Preparation & Modeling Process
  
### 1. Data Preparation
```
SELECT 
    order_date,
    order_time,
    pizza_category,
    pizza_size,
    pizza_name,
    unit_price,
    total_price,
    quantity
FROM pizza_sales
```
- Data loaded directly into Power BI
- No major data quality issues detected
### 2. Data Modeling
- Built a central pizza_sales table for transactional data.
- Created a calendar table using DAX to support time-based analysis.
```
Date = CALENDAR(
    MIN(pizza_sales[order_date]),
    MAX(pizza_sales[order_date]))
```
- Established a relationship between order_date and the calendar table.
- Extracted time components such as month and weekday to analyze trends and customer behavior
### 3. Dynamic Metric Selection
```
Metric = {
    ("Sales",    NAMEOF('pizza_sales'[Sales]),        0),
    ("Quantity", NAMEOF('pizza_sales'[Sum Quantity]), 1),
    ("Orders",   NAMEOF('pizza_sales'[Orders]),       2)}
```
- Implemented a metric selector using field parameters
- Enabled users to switch between Sales, Order, and Quantity
### 4. DAX Measures
```
-- Total Order
Total Orders = DISTINCTCOUNT ( pizza_sales[order_id] )

-- Total Sales
Total Sales = SUM(pizza_sales[total_price])

-- Total Quantity 
Total Quantity = SUM(pizza_sales[quantity])

-- Average revenue per order
Avg Value per Order =
SUM(pizza_sales[total_price]) / DISTINCTCOUNT(pizza_sales[order_id])

-- Month-over-Month growth %
MoM % =
VAR Prev = [Prev month sales]
RETURN
IF(OR(ISBLANK(Prev), Prev = 0), BLANK(),
   DIVIDE([Total Sales] - Prev, Prev)) 
```
After preparing the data and measures, a 3-page interactive dashboard was built to explore and present key insights.
## Data insights

### Page 1: Sales Overview

#### Provides a high-level snapshot of the business, highlighting key revenue drivers
- Large size dominates both revenue and quantity, suggesting most orders are group-oriented.
- Classic category leads overall, primarily due to its lower price point rather than strong preference.
- Small size and Veggie category consistently underperform across both revenue and quantity, indicating weak positioning.
  
<img width="1372" height="773" alt="image" src="https://github.com/user-attachments/assets/ba15a565-63f2-497f-9c8b-5a49b277c834" />

### Page 2: Monthly Performance
#### Analyzes how the business performs over time
- July is the strongest revenue month, indicating a clear seasonal demand peak.
- Order volume and quantity remain relatively consistent across months, while sales show noticeable variation, suggesting that revenue fluctuations are driven more by pricing or product mix than demand.
  
<img width="1371" height="771" alt="image" src="https://github.com/user-attachments/assets/b1ecbcbe-f55f-412f-b3bc-5297080e73ce" />

### Page 3: Customer Behavior

#### Examines when customers order and how their behavior changes
- Lunch (12:00–13:00) is the busiest time on weekdays, indicating typical lunch rush behavior.
- On weekends, the pattern shifts, with dinner (17:00–19:00) outperforming lunch.
- Friday is the strongest day overall, especially during peak months (May–July).
- Wednesday shows lower average order value despite stable sales, suggesting customers purchase more low-priced items rather than higher-value orders.

<img width="1367" height="770" alt="image" src="https://github.com/user-attachments/assets/e7c8c151-a26a-47f0-b238-6765a5af6d4a" />
## Dashboard Walkthrough

[View Full Dashboard Walkthrough](https://drive.google.com/file/d/1fwjCf5gOIo1YVBfTm53W_n9be_l8zDgW/view?usp=sharing)

## Recommendations

### Address the size imbalance

The Small size is clearly underperforming in both revenue and quantity. Instead of heavy discounting, offering a “Buy 1 Get 1” deal or bundling it with a free drink could encourage trial. 

### Give Chicken and Supreme more spotlight

These categories perform similarly to Classic but at higher price points, indicating stronger margins. Increasing their visibility through promotions or combo deals could shift demand toward higher-value orders.

### Give Veggie a clearer identity

Veggie pizzas lack clear positioning. Instead of broad discounts, targeted campaigns such as “Meatless Monday” or health-focused messaging could attract a niche but loyal customer base.

### Capture the weekend dinner window

The 17:00–19:00 weekend slot is a high-potential period for family dining. Targeted family combo offers (3+ people) could drive additional revenue.

### Capitalize on July

As the peak month, July presents the best opportunity for high-impact strategies such as new product launches, upselling campaigns, and premium promotions.

## Final Conclusion

The business maintains stable sales performance, with clear opportunities to improve revenue. By focusing on product mix, promoting higher-value items, and making better use of peak periods, the restaurant can drive growth without major operational changes. 


