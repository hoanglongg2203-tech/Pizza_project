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

- **DAX** — Custom measures including MoM % growth and other performance metrics

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
Small is consistently underperforming across both revenue and quantity. A "Buy 1 Get 1" or a Small plus drink bundle could drive trial without heavy discounting. If that moves the needle, it is worth making permanent.

**Give Chicken and Supreme more spotlight**
Both categories sell nearly as well as Classic but at a higher price, which means better margin per order. Featuring them more in promotions, combo deals, or social media could naturally shift customers toward higher-value orders without changing anything on the menu.

**Give Veggie a proper identity.**
A blanket discount probably hurts more than it helps. A "Meatless Monday" promo or a health-focused campaign could build a loyal niche customer base that the restaurant is currently not speaking to at all.

**Capture the weekend dinner window**
The 17:00–19:00 slot on Saturday and Sunday quietly outperforms the lunch peak on those same days, but it gets far less marketing attention. A weekend dinner deal pushed through social media in the late afternoon could be one of the highest-ROI moves available right now.

**Capitalize on July**
It is the peak month of the year. New launches, upsell campaigns, and high-margin promotions should all be timed around this window when customers are in a spending mood.
Dataset



