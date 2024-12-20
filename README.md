# pizza_sales_report_powerbi_-_SQL

**Pizza Sales Analysis Report**

**Overview**

This report analyzes pizza sales from January to December, highlighting key trends, performance metrics, and actionable insights. The findings are based on two dashboards: the primary Pizza Sales Report and the supplementary Best/Worst Sellers dashboard.

**Key Metrics from the Pizza Sales Report**

Average Order Value: 1.00

Average Pizzas per Order: 2.32

Total Orders: 21,000

Total Pizzas Sold: 50,000

Total Revenue: $817.86K

**Insights from the Pizza Sales Report**

Busiest Days & Times:

Days: Sales are highest on weekends, particularly Friday and Saturday evenings.

Months: July and January see the most orders.

Sales Performance:

Category: The "Classic" category contributes the most to sales and total orders.

Size: Large-sized pizzas dominate sales performance with 45.89% of total sales.

Daily and Monthly Trends:

Daily Trend: Friday records the highest sales volume (3.5K orders).

Monthly Trend: Sales peak in July (1,935 orders) and decline in February and September.

Sales Distribution:

By Category:

Classic: 14,888 pizzas sold.

Supreme: 11,987 pizzas sold.

Veggie: 11,649 pizzas sold.

Chicken: 11,050 pizzas sold.

By Size:

Large: 45.89% of total sales.

Medium: 30.49%.

Regular: 21.77%.

X-Large and XX-Large combined: 1.72%.

**Insights from the Best/Worst Sellers Dashboard**

Best Pizza Sellers:

The best-selling pizza is from the Classic category, consistently outperforming other categories across all months.

Large-sized pizzas within this category have the highest demand, accounting for a significant portion of total revenue.

Friday evenings contribute the most to these sales, aligning with overall busiest day trends.

Worst Pizza Sellers:

The XX-Large size is the least popular, contributing only 0.8% to total sales.

Chicken category pizzas underperform relative to others, particularly in medium sizes.

Sales of these items decline sharply during weekdays, especially on Tuesdays.

**Recommendations**

Boost Weekend Sales:

Offer discounts or combo deals on Friday and Saturday evenings to capitalize on high demand.

Improve Low-Performing Items:

Analyze customer feedback to understand why chicken pizzas and XX-Large sizes are less popular.

Test promotional offers or bundle deals for these items to encourage sales.

Seasonal Promotions:

Focus on peak months like July and January to introduce seasonal offers, ensuring sustained interest and maximizing revenue.

Inventory and Staffing Optimization:

Align inventory levels and staff schedules with peak times to meet demand efficiently, especially on weekends and during July and January.

**Conclusion**

This analysis provides actionable insights to enhance pizza sales performance. The "Classic" category and large-sized pizzas dominate sales, while certain low-performing items present opportunities for growth. By leveraging trends from the busiest times and addressing weaknesses in the worst sellers, the business can optimize revenue and customer satisfaction.


![image](https://github.com/user-attachments/assets/24abe2d4-54f2-4eda-9be7-7bb693aff493)

![image](https://github.com/user-attachments/assets/911e4158-2cc5-4db7-ba54-f55db9448336)

                                                           PIZZA SALES QUERIES


KPI’s

Total Revenue: 
Select Sum(total_price) AS Total_Revenue from pizza_sales_excel_file                                            

  ![image](https://github.com/user-attachments/assets/9ee10586-7576-42a8-bec3-1d96814cb550)


Average Order Value:
Select Sum(total_price) / Count(Distinct order_id) as Avg_Order_Value from pizza_sales_excel_file

![image](https://github.com/user-attachments/assets/864eae71-4189-4db3-a7bd-24cecf703e2f)


Total Pizzas Sold: 
Select Sum(quantity) As Total_Pizza_Sold from pizza_sales_excel_file

![image](https://github.com/user-attachments/assets/610140e5-bae6-4bff-ad4a-19951f22987e)


Total Orders:
Select Count(Distinct order_id) AS Total_orders from pizza_sales_excel_file
 
![image](https://github.com/user-attachments/assets/a2f7b85a-1109-4e41-82d5-6c3a26ae7410)


 
Average Pizza Per Order:
Select Cast (Cast (Sum(quantity) As Decimal(10,2)) / 
Cast (Count(Distinct order_id) As Decimal (10,2)) As Decimal(10,2)) AS Avg_pizza_per_order
from pizza_sales_excel_file


![image](https://github.com/user-attachments/assets/d389013e-caaa-400e-87c7-8b034353eef1)




Problem Statement

Charts Requirement 

Daily Trend for total orders:

Select Datename(DW, order_date) as order_day, Count(Distinct order_id) As Total_Order
From pizza_sales_excel_file
Group by  Datename(DW, order_date)

![image](https://github.com/user-attachments/assets/72b3033e-eb7c-4b96-93a1-cdfb2f1db2dc)




  

 Monthly Trend for total Orders: 

             Select Datename(Month, order_date) AS Month_Name, Count(Distinct order_id) As Total_Orders
From pizza_sales_excel_file
Group by Datename(Month, order_date)
Order by Total_Orders DESC

![image](https://github.com/user-attachments/assets/52e867a5-9bc6-443c-9e7c-f2003eba1aeb)



![image](https://github.com/user-attachments/assets/8e8fd5cb-2aa8-4782-aaac-298ed5ffa902)











 Percentage of sales by pizza category
 
Select pizza_category, sum(total_price) as Total_Sales, sum(total_price) * 100/ (Select Sum(total_price) from pizza_sales_excel_file) As PCT
From pizza_sales_excel_file
Group By pizza_category


![image](https://github.com/user-attachments/assets/6847d5c8-bfa0-4895-a86e-3b574fd4f8f2)








Top 5 best sellers by revenue, total quantity and total orders

      Select Top 5 pizza_name, Sum(total_price) as Total_revenue from pizza_sales_excel_file
Group by pizza_name
Order by Total_revenue DESC


![image](https://github.com/user-attachments/assets/19d2163d-5b71-4976-a39f-caad717b7a8f)







Select Top 5 pizza_name, Sum(quantity) as Total_Quantity from pizza_sales_excel_file
Group by pizza_name
Order by Total_Quantity DESC

![image](https://github.com/user-attachments/assets/c0d31319-f27f-4123-a1c7-8525e34304e6)



Select Top 5 pizza_name, COUNT(DISTINCT order_id) as Total_Orders from pizza_sales_excel_file
Group by pizza_name
Order by Total_Orders DESC


![image](https://github.com/user-attachments/assets/f3901658-fe36-4a65-a91d-200c66d2a0fb)























Bottom 5 best sellers by revenue, total quality and total orders


Select Bottom 5 pizza_name, Sum(total_price) as Total_revenue from pizza_sales_excel_file
Group by pizza_name
Order by Total_revenue ASC
![image](https://github.com/user-attachments/assets/4c3c0463-1130-4968-9c9c-f85cea20caf6)



Select Bottom 5 pizza_name, Sum(quantity) as Total_Quantity from pizza_sales_excel_file
Group by pizza_name
Order by Total_Quantity ASC

![image](https://github.com/user-attachments/assets/91354744-ac1d-4681-8fcf-cda8fdfcf256)


Select Bottom 5 pizza_name, COUNT(DISTINCT order_id) as Total_Orders from pizza_sales_excel_file
Group by pizza_name
Order by Total_Orders ASC

![image](https://github.com/user-attachments/assets/730d3779-4cf4-48b6-a45f-3257ab16299d)


