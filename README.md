# Pizza Restaurant Sales Performance | Power BI 
## Business Context

Despite having a full year of sales data, the restaurant still lacked clear visibility into what actually drives revenue and customer behavior.
This project focuses on turning raw transactional data into meaningful insights and more importantly, translating those insights into practical business actions.
## Problem Statement
**The business had data, but couldn’t confidently answer key questions:**

- Which products and sizes truly drive revenue, not just volume?
- Are there seasonal trends that should influence planning?
- When do customers actually order — and how does that change over time?
## Objectives
**Build a 3-page interactive dashboard for business users.**
- Track core KPIs:
- Total Sales
- Order Count
- Total Quantity
- Average Order Value
- Average Sales per Day
- Month-over-Month Growth
## Dataset

- **Source:** [Pizza Sales Dataset — Kaggle](https://www.kaggle.com/datasets/nextmillionaire/pizza-sales-dataset)
- **Period:** Full year 2015
- **File:** [raw_data.csv](https://github.com/user-attachments/files/26668712/raw_data.csv)

##  Tools & Tech Stack
- Power BI — dashboard development & data modeling
- DAX — KPI calculations, time intelligence
- SQL (MS SQL Server) — data extraction
## Key Technical Highlights
- Built time-intelligence measures (MoM growth, daily averages)

- Designed a clean data model with a DAX calendar table

- Used field parameters to enable dynamic metric switching (Sales / Orders / Quantity)

- Wrote SQL to extract and structure analysis-ready data
  
## Data Preparation
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

##Key DAX Measures
```
-- Average revenue per order
Avg Value per Order =
SUM(pizza_sales[total_price]) / DISTINCTCOUNT(pizza_sales[order_id])

-- Average daily revenue
Avg Sales per Day =
DIVIDE(SUM('pizza_sales'[total_price]), DISTINCTCOUNT('pizza_sales'[order_date]))

-- Month-over-Month growth %
MoM % =
VAR Prev = [Prev month sales]
RETURN
IF(OR(ISBLANK(Prev), Prev = 0), BLANK(),
   DIVIDE([Total Sales] - Prev, Prev))

-- Dynamic metric switcher (field parameter)
Metric = {
    ("Sales",    NAMEOF('pizza_sales'[Sales]),        0),
    ("Quantity", NAMEOF('pizza_sales'[Sum Quantity]), 1),
    ("Orders",   NAMEOF('pizza_sales'[Orders]),       2)}
```
## Dashboard Walkthrough

[View Full Dashboard Walkthrough](https://drive.google.com/file/d/1vMTaH0Z4zQlUux4a4cUFQ7Tl4f-TrMrp/view?usp=sharing)

## Data insights

### Page 1: Sales Overview

#### Provides a high-level snapshot of the business, highlighting key revenue drivers
- Large size dominates both revenue and quantity, suggesting most orders are group-oriented.
- Classic category leads overall, primarily due to its lower price point rather than strong preference.
- Small size and Veggie category consistently underperform across both revenue and quantity, indicating weak positioning.
  
<img width="1409" height="792" alt="image" src="https://github.com/user-attachments/assets/7fc28d7b-8bd8-4c24-a8e1-77af72c24a1d" />

### Page 2: Monthly Performance

#### Analyzes how the business performs over time
- July is the strongest revenue month, indicating a clear seasonal demand peak.
- Overall demand remains stable, with no significant long-term decline.
- Consecutive declines in September and October suggest a potential seasonal slowdown that should be monitored.
  
<img width="1411" height="790" alt="image" src="https://github.com/user-attachments/assets/09d6aff8-632b-477f-8543-1cf9075a3768" />


### Page 3: Customer Behavior

#### Examines when customers order and how their behavior changes
- Lunch (12:00–13:00) is the busiest time on weekdays, indicating typical lunch rush behavior.
- On weekends, the pattern shifts, with dinner (17:00–19:00) outperforming lunch.
- Friday is the strongest day overall, especially during peak months (May–July).
- Wednesday shows lower average order value despite stable sales, suggesting customers purchase more low-priced items rather than higher-value orders.
<img width="1408" height="794" alt="image" src="https://github.com/user-attachments/assets/0c05b97a-bfff-4c43-beca-468c2e514a81" />

## Recommendations

### Address the size imbalance

The Small size is clearly underperforming in both revenue and quantity. Instead of heavy discounting, offering a “Buy 1 Get 1” deal or bundling it with a drink could encourage trial. If successful, this strategy could be scaled long term.

### Give Chicken and Supreme more spotlight

These categories perform similarly to Classic but at higher price points, indicating stronger margins. Increasing their visibility through promotions or combo deals could shift demand toward higher-value orders.

### Give Veggie a clearer identity

Veggie pizzas lack clear positioning. Instead of broad discounts, targeted campaigns such as “Meatless Monday” or health-focused messaging could attract a niche but loyal customer base.

### Capture the weekend dinner window

The 17:00–19:00 time slot on weekends outperforms lunch but receives less marketing attention. Targeted promotions during late afternoons could significantly improve revenue.

### Capitalize on July

As the peak month, July presents the best opportunity for high-impact strategies such as new product launches, upselling campaigns, and premium promotions.

## Final Conclusion

The business demonstrates stable demand with clear opportunities for revenue optimization. By refining product positioning, promoting high-margin categories, and focusing on peak demand periods, the restaurant can drive growth without major operational changes.

