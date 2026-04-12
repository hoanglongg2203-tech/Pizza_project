# Pizza Restaurant Sales Performance Analysis

Project Overview
A personal portfolio project analyzing the full-year 2015 sales data of a pizza restaurant. The goal was to go beyond the numbers, understand what was actually happening in the business, and turn those findings into practical recommendations.
## Dataset

- **Source:** [Pizza Place Sales — Kaggle](https://www.kaggle.com/datasets/nextmillionaire/pizza-sales-dataset)
- **Period:** Full year 2015

 ## **Tools Used**

- **SQL** — Extracted and prepared raw data from the dataset
  
 ```sql
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

- **Power BI** — Built a 3-page interactive dashboard

- **DAX Measures** — Custom measures including MoM % growth and other performance metrics
```
Avg Value per Order =
SUM(pizza_sales[total_price])/DISTINCTCOUNT(pizza_sales[order_id])

Avg Sales per Day = 
DIVIDE(SUM('pizza_sales'[total_price]), DISTINCTCOUNT('pizza_sales'[order_date]))

MoM % = 
VAR Prev = [Prev month sales]
RETURN
IF(OR(ISBLANK(Prev), Prev = 0),BLANK(),
DIVIDE([Total Sales] - Prev, Prev))

Metric = {("Sales", NAMEOF('pizza_sales'[Sales]), 0),
("Quantity", NAMEOF('pizza_sales'[Sum Quantity]), 1),
("Orders", NAMEOF('pizza_sales'[Orders]), 2)}
```

## **Dashboard**

[View Full Dashboard Walkthrough](https://drive.google.com/file/d/1vMTaH0Z4zQlUux4a4cUFQ7Tl4f-TrMrp/view?usp=sharing)

## **Data insights**

### **Page 1: Sales Overview**

Gives a high-level snapshot of the business to quickly understand where revenue is coming from and which products are actually driving it.

- Large dominates in both revenue and quantity, suggesting most customers are ordering for groups.

- Classic leads overall but mainly because of its low price point ($14.80), not necessarily because customers prefer it.

- Small(size) and Veggie(category) are both underperforming consistently across revenue and quantity.
  
<img width="1409" height="792" alt="image" src="https://github.com/user-attachments/assets/7fc28d7b-8bd8-4c24-a8e1-77af72c24a1d" />

### **Page 2: Monthly Performance**

Tracks how the business moves over time and helps identify which months, categories, and sizes are growing or slipping.

- July is the strongest revenue month of the year.

- Overall demand is stable with no dramatic drops, which is a healthy sign.

- February dipped the hardest at -6.6% before March bounced back at +8.0%.
  
- September and October declining back to back is a pattern worth watching.
  
<img width="1411" height="790" alt="image" src="https://github.com/user-attachments/assets/09d6aff8-632b-477f-8543-1cf9075a3768" />


### **Page 3: Customer Behavior**

Helps understand when customers actually show up and how their spending behavior shifts across different times and days.
  
- Lunch (12:00–13:00) is the busiest window Monday to Friday, almost certainly the lunch rush.
  
- On weekends the dynamic flips: the 17:00–18:00 dinner slot outperforms lunch on Saturday and Sunday.

- Friday is the strongest day of the week, peaking further during summer months (May to July).

- Wednesday shows lower average order value despite steady total sales, meaning customers are buying more units at lower price points rather than fewer higher-value orders.

<img width="1408" height="794" alt="image" src="https://github.com/user-attachments/assets/0c05b97a-bfff-4c43-beca-468c2e514a81" />

## **Recommendations**

**Address the size imbalance** 

The Small size is clearly underperforming in both revenue and quantity. Instead of heavy discounting, offering something like a “Buy 1 Get 1” deal or bundling it with a drink could encourage more customers to try it. If this strategy proves effective, it could be considered as a long-term offering.

**Give Chicken and Supreme more spotlight**

Chicken and Supreme pizzas perform almost as well as Classic but come at a higher price point, meaning they likely generate better margins. Promoting these categories more actively through combo deals or social media campaigns could gradually shift customer preferences toward higher-value orders.

**Give Veggie a clearer identity**

Veggie pizzas seem to lack a strong positioning. Instead of applying broad discounts, creating targeted campaigns like “Meatless Monday” or promoting them as healthier options could help attract a specific customer segment and build loyalty over time.

**Capture the weekend dinner window**

Interestingly, the 17:00–19:00 time slot on weekends performs better than the lunch period on those same days, yet it receives less marketing attention. Running targeted promotions during late afternoons on weekends could be a highly effective way to boost sales.

**Capitalize on July** 

July stands out as the peak sales month. It would be strategic to align new product launches, upselling strategies, and high-margin promotions with this period when customers are more willing to spend.



