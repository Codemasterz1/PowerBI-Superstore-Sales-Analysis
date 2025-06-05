# SuperStore Sales Performance Analysis - Power BI Project

## Project Overview
This project involves analyzing the Sample Superstore sales dataset to identify key performance indicators, sales trends, top-performing products, and geographical sales distribution. The primary goal was to create an interactive dashboard in Power BI to visualize these insights.

## Data Source
*   **Dataset:** Sample - Superstore Sales (`train`)
*   **Source:** Kaggle 

*   *   **Description:** The dataset contains historical sales data for a fictional superstore, including order details, customer information, product details, and sales figures.
    *   *(This version specifcally focussed on Sales and didnt include Profit/Quanitty/Discount). 
 
    *   # Tools Used
*   **Power BI Desktop:** For data cleaning (Power Query), data modeling (DAX for measures), and dashboard creation.
*   **Microsoft Excel/Google Sheets (Optional):** For initial data viewing.
*   **GitHub:** For project documentation and sharing.

*  ## Data Cleaning and Preparation (Power Query)
The following steps were taken to clean and prepare the data in Power Query:
*   Loaded the `train` file.
*   Checked and confirmed appropriate data types for all columns (e.g., `Order Date` as Date, `Sales` as Decimal Number).
*   Removed the `Row ID` column as it was not needed for analysis.
*   Verified column quality (no significant errors or missing values that required extensive cleaning for this scope).

*   ## DAX Measures Created
*   **Total Sales:** `Total Sales = SUM('train'[Sales])`
  
 
    *   ## Dashboard Visualizations & Key Insights

The Power BI dashboard consists of the following key visuals:

1.  **Total Sales by Quarter and Year (Column Chart):**
    *   **Insight:** Sales demonstrate an overall upward trend year-over-year. Strong seasonality is evident, with sales consistently peaking in Q4 of each year. 
   
  
2.  **Total Sales by Region (Bar Chart):**
    *   **Insight:** The West region is the highest contributor to total sales, followed by the East.
  3.  **Total Sales by State (Map Visual):**
    *   **Insight:** California and New York are the top-performing states. Sales are notably concentrated in these states, along with others like Texas and Washington. The map provides an interactive way to explore state-level performance.
        4.  **Top 10 Sub-Categories by Sales (Bar Chart):**
    *   **Insight:** Phones (approx. $0.33M) and Chairs (approx. $0.32M) are the leading sub-categories by sales. The chart displays the top 10 sub-categories to focus on key contributors.

## Part 2: Profitability Analysis Dashboard

### Data Source (for Profitability Analysis)
*   Dataset: Sample - Superstore Sales (Full version including `Sales`, `Profit`, `Quantity`, `Discount`)
*   Source: ... (e.g., Kaggle - specify if it's a different link or version) ...
*   Table Name in Power BI: `Orders`

### Tools Used (for Profitability Analysis)
*   Power BI Desktop, etc.

### DAX Measures Created (for Profitability Analysis)
*   Total Sales = SUM('Orders'[Sales])
*   Total Profit = SUM('Orders'[Profit])
*   Profit Margin = DIVIDE([Total Profit], [Total Sales])
    *   *(Formatted as percentage)*

### Profitability Dashboard Visualizations & Key Insights
*   **Sum of Profit by Sub-Category (Bar Chart):**
    *   Insight: Revealed key profit drivers (Copiers, Phones) and loss-making sub-categories (Tables, Bookcases).
*   **Sum of Profit by State (Map Visual):**
    *   Insight: Highlighted states with highest and lowest profit contributions.
*   **Sales vs. Profit by Sub-Category (Scatter Plot):**
    *   Insight: Segmented sub-categories into high/low sales and high/low profit, identifying "problem children" like Tables (high sales, negative profit).
*   **Table: Sub-Category, Sales, Profit, Profit Margin:**
    *   Insight: Provided detailed financial breakdown and clear profit margin percentages per sub-category.
* 

### Profitability Dashboard Screenshot
![image](https://github.com/user-attachments/assets/1a58c09f-a717-4d63-9e5a-d087eb9267f3)


## Future Enhancements (Applies to further Superstore analysis)
*   Customer segmentation (e.g., RFM analysis).
*   Deeper trend analysis (YoY, MoM growth rates for both sales and profit).

## Dashboard Screenshot
*Placeholder:
![image](https://github.com/user-attachments/assets/ac142612-45e5-4576-a37d-2dbc515a6ce8)

Populated README with project details and dashboard insights


---

## Part 3: RFM Customer Segmentation Analysis

### Objective (Part 3)
To segment customers based on their Recency (how recently they purchased), Frequency (how often they purchase), and Monetary Value (how much they spent) to identify distinct customer groups for targeted marketing strategies.

### Methodology (Part 3)
1.  Data Preparation for RFM:
    *   A snapshot date of **31/12/2017** was used (one day after the last transaction in the `Orders` table).
    *   A new calculated table, **`RFM_Data`**, was created using `SUMMARIZECOLUMNS`. This table summarized, per `Customer ID`:
        *   `LastPurchaseDate`: Most recent `Order Date`.
        *   `Frequency`: Distinct count of `Order ID`s.
        *   `MonetaryValue`: Sum of `Sales`.
    *   A `Recency` column was added to `RFM_Data`, calculated as (Snapshot Date - `LastPurchaseDate`) in days.
2.  **RFM Scoring:**
    *   `R_Score`, `F_Score`, and `M_Score` (1-5 scale) were calculated as new columns in `RFM_Data`.
    *   Fixed thresholds were used for scoring (e.g., for Recency: 0-30 days = Score 5; for Frequency: 10+ orders = Score 5; for Monetary: >$2000 = Score 5). **
3. Segmentation:
    *   An `RFM_Score` column was created by concatenating R, F, M scores (e.g., "555").
    *   An `RFM_Segment` column was created using a `SWITCH(TRUE(), ...)` statement, assigning segments like "Champions," "Loyal Customers," "At Risk," etc., based on combinations of R, F, and M scores. *(You can see the exact segment definitions in the DAX for the `RFM_Segment` column in the Power BI file).*

### Key Visuals on the RFM Dashboard (Part 3)
*   RFM Segment Profile (Table): Displays Customer Count, Total Sales, Avg. Sales per Customer, Avg. Recency (Days), and Avg. Frequency for each defined segment.
*   **Count of Customer ID by RFM_Segment (Bar Chart):** Visualizes the number of customers in each segment. *"Champions" shows as the largest segment).*
*   Sum of MonetaryValue by RFM_Segment (Bar Chart):** Visualizes the total revenue generated by each customer segment. 
*  ![M score, F score, and R score dashboard](https://github.com/user-attachments/assets/c822bcc1-5377-4191-b0bf-7088a4795458)


### Key Insights & Potential Actions from RFM Analysis (Part 3)
*   Dominance of Champions: The "Champions" segment is the largest both in customer count (approx. 286) and in total sales contribution (over $1M). This highlights the critical importance of retaining these high-value, engaged customers.
    *   *Potential Action:* Implement targeted loyalty programs and exclusive offers for Champions.
*   Value in "Needs Attention": The "Needs Attention" segment is the second largest in terms of customer count and also contributes significantly to sales.
    *   *Potential Action:* Develop re-engagement campaigns to understand their needs and encourage further purchases.
*   Segment Diversity: The analysis successfully identified distinct customer groups such as "Potential Loyalists," "Loyal Customers," "Promising," and smaller but important segments like "At Risk" and "Hibernating," each requiring different engagement strategies.
  
### RFM Customer Segmentation Dashboard Screenshot (Part 3)
![RFM Dashboard Screenshot] ![sSupersotre profitablity analysis](https://github.com/user-attachments/assets/14b0a574-276d-4689-af7d-15706bdeb396)
![RFM Customer segmentation Analysis dashboard](https://github.com/user-attachments/assets/dfde1ec8-f685-4bab-86a1-a4bb2455a25f)








