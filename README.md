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

## Dashboard Screenshot
*Placeholder:
![image](https://github.com/user-attachments/assets/ac142612-45e5-4576-a37d-2dbc515a6ce8)

Populated README with project details and dashboard insights
