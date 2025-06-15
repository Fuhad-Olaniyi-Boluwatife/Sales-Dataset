# E - Commerce Sales Dataset

## Table of Contents

> - [Introduction](#introduction )
> - [Statement of Problem](#statement-of-problem)
> - [Tools and methodology](#tools-and-methodology)
> - [Data Source](#data-source)
> - [Data Preparation and Transformation](#data-preparation-and-transformation)
> - [Data Analysis and Observations](#data-analysis-observations)
> - [Conclusion](#conclusion)
> - [Recommendations](#recommendations)
> - [Referencing](#referencing)





## Introduction

This is an open dataset provided by the Pragmatic Works which contains sales records for a typical e-commerce business. It touches upon various aspects of sales activities, with key data points including unique identifiers for products, customers, and manufacturers, along with some other important details concerning the transactions.

Each entry corresponds to a concrete sales event, which has transaction dates, the number of units sold to a customer, and financial details like unit cost and unit price. Alongside the sales transactions, the products are further detailed with information about product name, product category, market segment, and manufacturer.

In addition to these details, the dataset also provides location details for every transaction, including zip code, city, state, region, district, and country, which makes it conducive to spatial analysis.

Here is how the dataset looks: 

![dataset](https://github.com/user-attachments/assets/adb383dd-67d2-4bb8-b93c-57ba0305628c)

By leveraging on this dataset, I have analyzed sales trends, explored customer behaviour, and assessed geographical performance, uncovering valuable insights to guide strategic decisions. The dashboard below presents key findings and interactive visualizations, enabling deeper exploration of the data’s potential.

https://github.com/user-attachments/assets/e1e41cc0-6411-44ed-9fb9-7e42e0c9fd9a


The dashboard consists of 4 pages: one is a welcome page, and the other 3 are for the customer, sales, and geographical analysis, respectively. This dashboard has fixture buttons to help navigate through each page more easily, no matter where you are on the page. Here is the link to the dashboard



## Statement of Problem

This is to see how we can optimize product and regional performance by identifying high-value customers, best-selling product segments, and underperforming areas over time.



## Tools and Methodology

Microsoft Power BI and Power Query;

- **Data Preparation**: Performed data normalization, extraction, and cleaning using **Power Query**.
- **Data Modelling**: Built a **star schema** in **Microsoft Power BI** for optimized analytics.
- **Advanced Analytics**: Leveraged **DAX** to create calculated columns, custom measures, and a dynamic **calendar table** for time intelligence in Microsoft Power BI.
- **Visualization**: Developed interactive dashboards to transform raw data into actionable insights using Microsoft Power BI.

below is how the data looks after data preparation in power query

![Capture](https://github.com/user-attachments/assets/adcb423e-39d3-483a-ad81-6f7367e5837c)




## Data Source 

This analysis utilizes an open dataset provided by **Pragmatic Works**, containing **675,368 rows and 19 columns** in its raw form.

### Dataset Structure:

- **Initial State**: Single table with transactional sales data

- **Transformed Structure**: Normalized into **6 tables** using dimensional modelling:
  - **1 Fact Table**: Sales transactions (granular records)
  - **5 Dimension Tables**: Supporting reference data (DimProducts, DimCustomers, Dimdate(custom -built for time intelligence analytics), dimCatergories, dimGeographical Tables.

Here are the tables in power bi

  ![power bi table](https://github.com/user-attachments/assets/9d244032-9e02-43e4-b1e4-045d4750350f)






## Data Preparation and Transformation
The dataset is nearly in its final cleaned form, with only minor amendments required to ensure optimal data efficiency. These refinements will be applied to the unified dataset before splitting it into various dimension and fact tables. The transformations were performed using the Power Query Editor in Power BI and include the following steps:

### Dimensional Modelling

The dataset was normalized into 6 tables using dimensional modelling principles:

- 1 Fact Table: Contains granular sales transaction records.

- 5 Dimension Tables: Store supporting reference data, including:

    - DimProducts (Product details)
    
    - DimCustomers (Customer information)
    
    - DimDate (Custom-built for time intelligence analytics)
    
    - DimCategories (Product categorization)
    
    - DimGeography (Geographical data)

All tables are linked via primary and foreign keys to establish relational integrity. Below is modelling diagram

![Modelling](https://github.com/user-attachments/assets/c860eef9-5577-40d2-abf6-a65840c452a3)

**Key Insights**

Following the data modelling process, key insights were derived and categorized into three main areas for analysis:

-  Customer Performance
-  Sales Performance
-  Geographical Performance

This structured approach ensures efficient data analysis and supports robust reporting capabilities.


## Data Analysis and Observations
### Customer Performance
To enhance the analytical depth of the report, I introduced the following measures and calculated columns:

**Key Measures** 

- Total Customer Count: Calculates the distinct number of customers.
- Average Revenue per Customer: Determines the mean revenue generated per customer.
  
  ```DAX
  average revenue per customer = DIVIDE([Total Revenue],COUNT(DimCustomer[Full name]))    
  ```
  

**Customer Segmentation (Calculated Column)**

- Customers were categorized into four tiers based on their generated revenue:
  
  - Platinum (Highest revenue)
  - Gold
  - Silver
  - Bronze (Lowest revenue)
    
  
  This segmentation enables targeted performance analysis across customer groups. Below is the DAX code used for categorization:
  
  ```DAX
  Customer Segementation = 
  SWITCH(
      TRUE(),
      DimCustomer[revenue per customer]>=450, "Platinum",
      DimCustomer[revenue per customer]>=300, "Gold",
      DimCustomer[revenue per customer]>=150, "Silver",
      "Bronze"
  )
  ```
  

Below is the customer page 

![customer page](https://github.com/user-attachments/assets/1c035e00-d1d7-4624-b0e3-015c50da0cca)


The dashboard provides an overview of customer metrics, segmentation, and top performers.

**Overall Customer Base**

  - Total Customer: 282600
  - average revenue generated per customer: 231.95
  - Customer Type: The customer base is dominated by returning customers (276,760) with a much smaller number of new customers (5,830).
  - Customer Spending Segmentation:
      - The largest segment is Silver, accounting for 72.36% of customers based on spending.
      - Gold customers make up 16.75%.
      - Bronze customers represent 10.62%.
      - Platinum customers are the smallest group at 0.26%.
  - The evaluation of customer spending patterns identifies Rhonda Hanson as the highest-spending individual, with total purchases amounting to $1,250 during the entire analysis period. This finding emerges from our ranking of the top 10 customers based on cumulative expenditure, which serves as a valuable indicator of client value and purchasing behavior.
  - Customer distribution by state shows the highest concentrations in Texas (TX) with 25,366 customers, California (CA) with 19,975, and Florida (FL) with 18,859. The table further breaks down these state totals by spending tier (Bronze, Gold, Platinum, Silver).
    

**Key Observation:** From the results of the analysis of the customer data, several conclusions may be drawn. first and foremost, the business enjoys a very high customer retention rate, with over 98% of the 282,600 customers having been repeat customers (276,760)over the years; this reflects very strong customer loyalty and, subsequently, repeat business. From a financial point of view, the average revenue per customer is $231.95, providing a good reference for evaluating the lifetime value of customers and identifying potential upsell opportunities.

Furthermore, customer segmentation indicates that the base is dominated by Silver-tier customers, who account for 72.36% of all customers. The Gold-tier clients occupy the second position at 16.75% of the customer base, while Bronze-tier customers come in third at 10.62%. A scant 0.26% belongs to platinum-level, suggesting a potential area for growth by cultivating more high-value relationships. Worth mentioning is the top individual spender, in the name of Rhonda Hanson, who has shelled out to the tune of $1,250, constituting an excellent example worth looking into even for analyzing the behaviours of high-value customers.

Geographically, customers are more heavily concentrated in some states than in the other states, with Texas having 25,366 customers, California having 19,975 customers, and Florida having 18,859 customers. These states could be chosen for more targeted, localized campaigns and for more involvement with deeper customer engagements. in addition to number of customer, we see from the tool tip the category they tend to buy more which is urban products. Furthermore, looking at how much customers spend in each state also helps us improve our nationwide marketing, especially when trying to keep Silver-tier customers in our biggest states.

Finally, filtering customer spending per year allows for a deep dive into analysis by date, revealing treat-worthy insights such as whether the highest-spending customer  Rhonda Hanson ($1,250 total spend), kept spending consistently year after year or if they probably had fluctuating shapes and the category of product she bought. By analyzing these annual spend trends, we can spot loyal customers, identify rising stars, see if sales trends are consistent over time in states, notice those who are losing spenders needing re-engagement, and finally suit customer retention strategies and thus segmentation marketing based on this decision.

### Sales performance
To enhance the analytical depth of the report, I introduced the following calculate measures:
- Gross Profit(Select year, previous year and the percentage change bewteen both)
- Total Cost (Select year, previous year and the percentage change bewteen both)
- Total Revenue (Select year, previous year and the percentage change bewteen both)
- Total Sales (Select year, previous year and the percentage change bewteen both)
- Profit margin (switch is uniform over the years for this dataset)

here is the dax expression for the percentage change
  ```DAX
%total cost = 
  VAR current_cost = [Total Cost]
  VAR last_cost = [total cost(last year)]
  RETURN
  IF(ISBLANK(current_cost) && ISBLANK(last_cost),
      BLANK(),
      DIVIDE((current_cost-last_cost),last_cost)
  )
  ```
here is the DAX expression for the previous year

```DAX
Gross Profit(last year) = 
CALCULATE(
    [Gross Profit],PREVIOUSYEAR(DimDate[Date])
    )
```
The Sales Performance page provides a comprehensive overview of key metrics, trends, and product/category performance, including KPIs like gross profit, revenue, Cost Sales trends from 2011-2016, unit price-cost relationships, top-performing products, and dominant sales in the Urban category. Below is the sale performance page of our report.

![SharedScreenshot1](https://github.com/user-attachments/assets/28fd0876-32c3-4d7c-966b-962921467e57)


**Overview**
The dashboard displays four main KPI cards, each providing critical sales performance metrics:

1. **Gross Profit**
    - Value: $17.70M
    - Year-over-Year Comparison: "Last year ---" (Data not available)
    - Gross Profit Margin: 27.00%
2. **Total Cost**
   - Value: $47.85M
   - Year-over-Year Comparison: "Last year ---" (Data not available)
3. **Total Revenue**
   - Value: $65.55M
   - Year-over-Year Comparison: "Last year ---" (Data not available)
5. **Total Sales**
   - Value: 675K
   - Year-over-Year Comparison: "Last year ---" (Data not available)
     

**Reason for Missing Year-over-Year Comparison Data**
The dashboard currently shows aggregated data for the entire period (2011–2016) due to the absence of a specific year filter. As a result, the "Last year" comparison field remains blank.

However, if a specific year (e.g., 2013) is selected, the KPIs will dynamically update to display:

![SharedScreenshot](https://github.com/user-attachments/assets/a916d2d9-bff5-4a64-9b4c-2aeb8a7e14b7)

This functionality allows for more precise trend analysis and performance benchmarking when filtering by individual years.

**Performance Trends by Revenue, Profit, and Sales (2011–2016)**
The panel presents a multi-line chart tracking the trends of total revenue, gross profit, and total sales from 2011 to 2016. Total revenue is represented by a white line, gross profit by a light teal line, and total sales by a dark teal line. The visualization reveals notable fluctuations in all three metrics over the six-year period. Notably, revenue and profit exhibit a strong correlation, moving in close alignment throughout the timeline. This suggests that changes in revenue directly influenced profit margins during these years. Meanwhile, total sales followed a distinct but related trajectory, providing additional context on overall business performance.

![SharedScreensh](https://github.com/user-attachments/assets/a7097cec-b411-4e6d-83b7-f5798693e50d)

**Unit Price vs Cost Price**
This shows a strong positive linear relationship between unit cost and unit price, indicating a consistent pricing strategy relative to cost over the entire year. This consistency remains uniform for individual years when filtering the dashboard by year, though with a slight change in the rate at which the unit price changes with respect to cost price.

![SharedScreenshot](https://github.com/user-attachments/assets/81ebaf07-7725-42aa-adf5-b019ab9d110c)

**Top product**
This displays the top-performing products ranked by a selected metric, helping to identify the most patronized products. A toggle feature allows users to switch the ranking criteria between 'Profit' and 'Sales,' with the current view set to 'Profit' for this analysis.

![top Produt](https://github.com/user-attachments/assets/1aa062b7-a43b-442b-8808-d744b4cd7d86)

![sales](https://github.com/user-attachments/assets/9fb83731-35c3-473a-8c1e-3f4cea62cd88)

**Sales by catergories**
The data clearly indicates that the "Urban" category accounts for the overwhelming majority of sales, significantly outperforming all other segments. By contrast, the "Rural" category contributes only a negligible portion of total sales across the entire period. While minor fluctuations in Rural sales become apparent when examining the data on a year-by-year basis, they remain consistently low in absolute terms. This stark disparity underscores Urban's dominant position in the market

![tyutu](https://github.com/user-attachments/assets/1bace0a6-5374-47be-90b2-6e81c0327e7d)

**Key Observation:** From the performance trend, the revenue and the gross profit have the same relationship, meaning that a fluctuation in revenue will be accompanied by a corresponding fluctuation in gross profit from period to period. The total sales follow allied but slightly different trajectories, thus reflecting broader trends in the business. Also from the scatter plot, we can see that there exists a strong and positive linear relationship between the unit price and cost price, implying that the pricing strategy is consistent throughout the period. Even when we filter the data by year, we still see the pattern appear, although just with a little deviation in the rate of change. 

The dashboard also features a Top Products view, where products are ranked according to selected performance metrics: profit and sales. The change in these performance metrics causes a shift in product rankings; however, some products remain consistently strong in the top 10. In addition, we also observed an overwhelming contribution in sales by the urban product category, which stands well ahead of all other categories. On the other hand, sales contribution from the rural product category is very little, accounting for approximately zero in the sale. These trends thus indicate the urban product as the major founding pillar of the sales and also point to the possibility of either enhancing or restructuring strategy for the less successful rural market.

Finally, filtering the dataset by specific years offers deeper insight into year-over-year sales performance and helps identify consistent patterns or anomalies in key performance indicators (KPIs). This functionality is essential for understanding how metrics vary over time and supports more informed, data-driven decision-making.

### Geography Performance
![Geography](https://github.com/user-attachments/assets/9ef9e37e-5f9c-4a02-928d-57a6a271b4db)


**Overview**

**Sales growth region over the years**  

The line chart visualization illustrates sales trends across three regions—Central, East, and West—from 2011 to 2016. The y-axis represents total sales, while the x-axis displays the years 2011 through 2016. Each region is represented by a distinct line: Central (light teal), East (medium teal), and West (white).  

![trend](https://github.com/user-attachments/assets/f0b2b4d0-b055-45b7-bae7-5defe7cc0674)

**Key observations:** There is cyclical patterns in sales within each year, likely reflecting quarterly fluctuations. The East region consistently outperforms the others, maintaining the highest sales throughout the period (top line), while the Central region shows middle-range performance. The West region remains the lowest-performing (bottom line). Despite these differences, all regions exhibit a general upward trend over the six-year period, indicating overall growth in sales. This analysis highlights both regional disparities and consistent market expansion across the board. 



**Proportion of sales by region**

The donut chart depicts the proportional division of total sales among the three primary regions: East, Central, and West. The East exerts dominance with $318K in sales, making up 47% of the whole, which is basically half of the revenue. It is then followed by the Central region, with $247K, or 37%, contributing just over one-third to the sales, while the West region is grossly behind at $110K (16%). 

![Geography0](https://github.com/user-attachments/assets/e574956d-c54a-4a02-8cf5-25990187abab)


**Key Observation:** This indicates a big imbalance in regional performance, with the East region having most of its sales. Because the West region underperforms to such an extent, contributing less than one-fifth to total revenue, there lie opportunities for implementing focused sales strategies in improving this area toward more balanced regional contributions to total sales.

**Category Breakdown Across the Region**

This profit analysis depicts money generation across three regions (East, Central, and West) for five product categories. As have been seen before, the East puffs up as the most profitable region ($291,533, contributing almost half of all profits), followed by the Central ($223,877—contributing roughly one-third), and then lastly the West ($99,120—just 16%). All regions display the same basic pattern: urban products are in the lead, accessories seem negligible, and other products contribute few profits. Urban products generate 91%-93% of profits from any region. Accessories earn profits that range between 5% and 7%, whereas Mix products stand at around 2.5% to 2.7%. Rural and youth products barely make any money at all.

![1](https://github.com/user-attachments/assets/0998a6b0-3bbb-4ab5-8168-234432ad5c03)


**Key observation:** This shows we should probably focus mostly on looking at Urban products anywhere, possibly push more accessory products as well, and find out why West is not making much money despite selling similar products. Looking at rural products, they tend to bring almost zero in profits across all regions. I think we must either work on selling them better or give up on them. This uniformity across regions suggests that customers all over share the preference for the same kind of products, which may facilitate the planning process.

**sales and profit by region**
this show the percentage of gross profit and revenue of the total gross profit and sales both in map version and table version(based on the selected option).

![geo](https://github.com/user-attachments/assets/e5d9ae2f-10cd-4d3e-b58e-e6bc1cd4b960)

![map view](https://github.com/user-attachments/assets/ae8520a2-a661-464a-9f01-321d0d0bcec7)

**Key Obseeravation:** Texas, Florida, and California stand as the highest-performing states, contributing a combined 22.47% of the total gross profits. The 10 highest-ranking states, in fact, contribute in aggregate almost half (48.7%) of all profits, showing the levels of concentration business success enjoys in a few regions. An average gross profit margin of 27% is reported across states, which falls in line with the trend presented for gross sales.

High profit levels in the East occur thanks to states that are reasonably ranked, such as Texas, Ohio, Pennsylvania, New York, Michigan, and North Carolina; meanwhile, Illinois, Ohio, Michigan, and Wisconsin provide second-place support to the Central Region.

Beyond the big-league states is a world of sharp declines: 11 states each bring in 1-2% of revenue and profit; 10 states weigh in from 2-3%; and the remaining last 19 states, representing 11.23% combined, weighing below 1%. This distribution shows the sheer proportion of successes coming from a handful of states.

## Conclusion

Looking from the customer perspective, the business gets high retention rates and a loyal customer base that keeps returning to them, indicating very high satisfaction and loyalty. While on customer segmentation, the Silver-tier customers constitute a strong base at mid-level, although greater efforts can be channelled into acquiring higher-value Platinum-tier customers. Based on location, we found customers clustered in states like Texas, California, and Florida; these markets clearly stand to benefit from marketing and engagement efforts targeted at them. Annual spending amount trends are further used to identify consistent high spenders as well as mark those customers who may require re-engagement.

We can see from the sales perspective that the revenue and profit show a tight relationship between 2011 and 2016, inferring the latter always being brought about by the former in same proportion from the performance trend. Also, the linear positive correlation between unit price and unit cost affirms stable pricing policies, indicating that at no point in time does the store run at a loss merely looking at the gross profit. But since from the data set nothing was said about the operation cost, taxation, and other expenses, we can't drill down to see if the company isn't at risk after other expenses have been paid. Still on sales, Urban products show sustained growth, with the majority of sales coming from this category. In contrast, underperforming Rural products continue to damage the brand's image, necessitating further consideration for uplifting or repositioning this category. Additional yearly sales filters provide more insights into the inner workings of sales and point to new trends or irregularities.

Revenue-wise, the East region is the topper, whereas the West significantly underperforms. This regional split may hold some clues for strategies in the underperforming areas, especially the West. The urban product category is a constant success across all regions. This suggests that there are strong customer affinities that are uniformly established, which should now ease the way forward with planning and product focus.

## Recommendations

- If further details can be provided to see the net profit, as these will help to know the future of the business and how it can improve on expanding the business width.
- Conduct a study regarding low sales areas, especially in the West; find reasons for low sales, making use of customer data from states of these sorts, and analyze further to find selling remedies, while also working to maintain strong performance in the highly-earning states.
- Further surveys could be conducted among customers to ascertain reasons behind the declining purchases, especially in the youths and rural products category. The outcomes could help to improve sales in the currently depressed categories.

## Referencing  

pragmatic works



