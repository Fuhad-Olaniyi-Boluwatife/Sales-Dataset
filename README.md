# E - Commerce Sales Dataset

## Table of Contents

> - [Introduction](#introduction )
>
> - [Statement of Problem](#statement-of-problem)
>
> - [Tools and methodology](#tools-and-methodology)
>
> - [Data Source](#data-source)
>
> - [Data Preparation and Trasformation](#data-preparation-and-transformation)
>
> - [Data Visualization and Analysis](#data-visualization-and-analysis)
>
> - [Conclusion](#conclusion)
>
> - [Observations](#observations)
>
> - [Recommendations](#recommendations)
>
> - [Referencing](#referencing)
>
>   



## Introduction

This is an open dataset, provided by *Pragmatic World*, that contains comprehensive sales records from a typical e-commerce operation. It captures various facets of sales activities, with key data points including unique identifiers for products, customers, and manufacturers, along with other essential transaction details.

Each record represents a specific sales event, detailing the transaction date, the number of units purchased, and financial metrics such as unit cost and unit price. Additionally, the dataset enriches product insights with information like product names, categories, market segments, and manufacturer details.

To provide deeper geographical context, the dataset also includes location-based data for each transaction, such as zip code, city, state, region, district, and country, enabling robust spatial analysis.

Here is the look of the dataset 

![dataset](https://github.com/user-attachments/assets/adb383dd-67d2-4bb8-b93c-57ba0305628c)



By leveraging this dataset, I have analyzed sales trends, explored customer behaviour, and assessed geographical performance, uncovering valuable insights to guide strategic decisions. The dashboard below presents key findings and interactive visualizations, enabling deeper exploration of the data’s potential.

[Dashboard]()





## Statement of Problem

This is to see how we can optimize product and regional performance by identifying high-value customers, best-selling product segments, and underperforming areas over time.





## Tools and Methodology

Microsoft Power BI and Power Query;

- **Data Preparation**: Performed data normalization, extraction, and cleaning using **Power Query**.
- **Data Modeling**: Built a **star schema** in **Microsoft Power BI** for optimized analytics.
- **Advanced Analytics**: Leveraged **DAX** to create calculated columns, custom measures, and a dynamic **calendar table** for time intelligence in Microsoft Power BI.
- **Visualization**: Developed interactive dashboards to transform raw data into actionable insights using Microsoft Power BI.

below is how the data looks after data preparation in power query

![Capture](https://github.com/user-attachments/assets/adcb423e-39d3-483a-ad81-6f7367e5837c)




## Data Source 

This analysis utilizes an open dataset provided by **Pragmatic World**, containing **675,368 rows and 19 columns** in its raw form.

#### **Dataset Structure**:

- **Initial State**: Single table with transactional sales data

- **Transformed Structure**: Normalized into **6 tables** using dimensional modelling:

  - **1 Fact Table**: Sales transactions (granular records)
  - **5 Dimension Tables**: Supporting reference data (DimProducts, DimCustomers, Dimdate(custom -built for time intelligence analytics), dimCatergories, dimGeographical Tables.

Here are the tables in power bi

  ![power bi table](https://github.com/user-attachments/assets/9d244032-9e02-43e4-b1e4-045d4750350f)






## Data Preparation and Transformation
The dataset is nearly in its final cleaned form, with only minor amendments required to ensure optimal data efficiency. These refinements will be applied to the unified dataset before splitting it into various dimension and fact tables. The transformations were performed using the Power Query Editor in Power BI and include the following steps:

### Dimensional Modeling
The dataset was normalized into 6 tables using dimensional modeling principles:

- 1 Fact Table: Contains granular sales transaction records.

- 5 Dimension Tables: Store supporting reference data, including:

    - DimProducts (Product details)
    
    - DimCustomers (Customer information)
    
    - DimDate (Custom-built for time intelligence analytics)
    
    - DimCategories (Product categorization)
    
    - DimGeography (Geographical data)

All tables are linked via primary and foreign keys to establish relational integrity. Below is modelling diagram

![Modelling](https://github.com/user-attachments/assets/c860eef9-5577-40d2-abf6-a65840c452a3)


### Key Insights
Following the data modeling process, key insights were derived and categorized into three main areas for analysis:

-  Customer Performance
-  Sales Performance
-  Geographical Performance

This structured approach ensures efficient data analysis and supports robust reporting capabilities.


## Data visualization and analysis
### Customer Perfromance
To enhance the analytical depth of the report, I introduced the following measures and calculated columns:

**Key Measures** 
- Total Customer Count: Calculates the distinct number of customers.
- Average Revenue per Customer: Determines the mean revenue generated per customer.
  
  ```DAX
  average revenue per customer = DIVIDE([Total Revenue],COUNT(DimCustomer[Full name]))
  ```
  
  ​    

**Customer Segmentation (Calculated Column)**
- Customers were categorized into four tiers based on their generated revenue:
  
  - Platinum (Highest revenue)
  - Gold
  - Silver
  - Bronze (Lowest revenue)
    
  
  This segmentation enables targeted performance analysis across customer groups. Below is the DAX code used for categorization:
  
  ```DAX
  ustomer Segementation = 
  SWITCH(
      TRUE(),
      DimCustomer[revenue per customer]>=450, "Platinum",
      DimCustomer[revenue per customer]>=300, "Gold",
      DimCustomer[revenue per customer]>=150, "Silver",
      "Bronze"
  )
  ```
Below is the customer page 
[image]()
  
The dashboard provides an overview of customer metrics, segmentation, and top performers.
  ### Overall Customer Base
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
    
The customer spending data can be filtered by year to track purchasing behavior over time. This reveals valuable insights, such as whether top customers like Rhonda Hanson ($1,250 total spend) maintained consistent spending year after year or had fluctuating patterns. By analyzing these yearly trends, we can identify loyal customers, spot emerging high-value clients, and notice any declining spenders who may need re-engagement. This time-based view helps tailor customer retention strategies and personalize marketing efforts more effectively


## Observations

## Recommendations

## Referencing  



