# salesforecast

## Table of Content
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools Used](#tools-used)
- [Data Cleaning & Preparation](#data-cleaning--preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Key Insights](#key-insights)
- [Sales Forecasting](#sales-forecasting)
- [Limitations](#limitations)

## Project Overview
The project analyzes a **Sales dataset** containing **9,800 rows and 16 columns**, recording daily sales in a global superstore from **2015 to 2018**. The dataset includes transactional details such as **Order Date, Ship Date, Ship Mode, Customer ID, Segment, Country, City, State, Region, Product ID, Category, Sub-Category, Product Name, and Sales**. The goal of this analysis is to extract meaningful insights related to **sales trends, customer behaviors, and the impact of external economic factors** on sales performance.

## Data Source
The dataset was sourced from **Kaggle**, [View here](https://www.kaggle.com/code/rizwanrizwannazir/forecasting-sales-with-timeseries)

## Tools Used
The following tools were utilized for data processing, analysis, and forecasting:
- **Tableau**: Used for creating visualizations and identifying key sales trends.
- **Python** (Pandas, NumPy, Matplotlib, Seaborn, Statsmodels): Assisted in data manipulation, visualization, and statistical modeling.
- **Microsoft Excel**: Used for initial exploration and data formatting.
- **Statsmodels (SARIMAX)**: Applied for sales forecasting

## Data Cleaning & Preparation
To ensure accuracy and reliability, several data preprocessing steps were performed:
- **Handling missing values**: The dataset contained **11 null values**, primarily in the 'Postal Code' column, which was deemed unnecessary and removed.
- **Dropping irrelevant columns**: 'Row ID' and 'Order ID' were removed as they did not contribute to the analysis.
- **Ensuring data type consistency**: Dates were converted to **DateTime format**, and sales values were stored as floating-point numbers.
- **Removing duplicate entries**: To maintain data integrity, duplicate rows were identified and removed.
- **Feature engineering**: A new variable, **Processing Time**, was created by calculating the difference between **Order Date** and **Ship Date**, providing insights into order processing efficiency.

## Exploratory Data Analysis
EDA involved answering key questions such as:
- What is the overall sales trend from 2015 to 2018?
- Which months and quarters generate the highest sales revenue?
- How does GDP influence sales trends over time?
- What is the relationship between order volume and processing time?
- Which shipping modes provide the fastest processing times?
- Who are the top customers by total sales, and how can their loyalty be incentivized?
- Which states generate the most revenue, and should additional stores be opened in those locations?
- Which product categories perform best over the years?
- How do sales vary across different customer segments?

## Key Insights:
- **Sales show a consistent upward trend** over the years, with a slight decline in 2016 but a 40% growth overall.
- **Seasonality in sales is evident**, with Q4 generating the highest revenue, followed by Q3.
- **GDP and sales have a strong positive correlation**, indicating that economic growth impacts sales performance.
- **Processing time does not significantly correlate with order volume**, meaning prioritization based solely on order count may not be justified.
- **Same-day shipping results in the shortest processing times**, whereas standard-class shipping takes the longest.
- **Top 10 customers generate a large portion of sales**, and offering incentives could further enhance retention.
- **California and New York lead in total sales**, suggesting potential expansion opportunities in these states.
- **Technology consistently outperforms other categories**, while Office Supplies see high purchase frequency but lower revenue per transaction.

## Sales Forecasting
To predict future sales, a **SARIMAX (Seasonal AutoRegressive Integrated Moving Average with Exogenous Variables) model** was implemented. The GDP was incorporated as an external factor influencing sales.

### Model Development
- **First Iteration:** Used **2015-2018** data as training and forecasted **2019 sales**, though accuracy could not be verified due to missing actual values.
- **Second Iteration:** Used **2015-2017** data for training and **2018** as a test set, achieving a **Mean Absolute Error (MAE) of 38,533.1**, showing significant improvement after tuning.
- **Final Iteration:** Used **2015-2016** as training and **2017-2018** as test data. Though the model identified trends, it struggled to predict spikes in Q4 sales accurately.

Overall, the **second iteration yielded the most accurate results**, demonstrating the importance of incorporating **recent sales behavior** into forecasting models.

## Limitations
- **Lack of Global Coverage**: The dataset focuses on a specific superstore’s sales and may not generalize to other industries or regions.
- **Limited External Factors**: While GDP was considered, other economic influences like inflation or interest rates were not included.
- **Short Timeframe**: The dataset spans only **four years**, limiting long-term forecasting accuracy.
- **Data Quality Issues**: Despite cleaning, there may still be unaccounted-for discrepancies affecting accuracy.

---
This project highlights the value of **data-driven decision-making** in sales forecasting, optimizing business strategies, and identifying trends that impact revenue growth.
