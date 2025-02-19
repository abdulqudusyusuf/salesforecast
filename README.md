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

![img1](https://github.com/user-attachments/assets/a5056ef9-12e8-47c0-a4e9-ce45e2d955ac)
![img2](https://github.com/user-attachments/assets/dacb62e2-99fa-46f6-bc10-fe103d234af2)
![img3](https://github.com/user-attachments/assets/08906831-4e69-4b0b-b5f9-7df90d91f550)
<img width="529" alt="img4" src="https://github.com/user-attachments/assets/036b25e3-18cd-4ebc-b2b8-03150336af05" />
<img width="679" alt="img5" src="https://github.com/user-attachments/assets/ff556a92-b435-4073-ac5c-f9a62598a91c" />
![img6](https://github.com/user-attachments/assets/27bfef57-484b-4096-a4f4-089b485e8850)
<img width="670" alt="img7" src="https://github.com/user-attachments/assets/a886122a-2115-4d74-9782-c42d14814a79" />
<img width="669" alt="img8" src="https://github.com/user-attachments/assets/f0bd7b59-5075-487e-aa5e-9ea9133334f3" />
![img9](https://github.com/user-attachments/assets/2541f150-d6b8-4bc0-9762-9645e739f436)
![img10](https://github.com/user-attachments/assets/96dd899f-3b91-4c07-8128-dff41998a20c)


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

<img width="584" alt="img11" src="https://github.com/user-attachments/assets/ce61857a-1d36-483b-9e24-8f5e6a5b4603" />
<img width="579" alt="img12" src="https://github.com/user-attachments/assets/8c94654b-75a4-480f-88e2-8b8bee89ec36" />
<img width="498" alt="img13" src="https://github.com/user-attachments/assets/bd34f34d-8707-47c6-b0cb-67710a93c4db" />
![img14](https://github.com/user-attachments/assets/01a1479a-d92d-4426-86b2-2fde8ff40f8e)


- **Second Iteration:** Used **2015-2017** data for training and **2018** as a test set, achieving a **Mean Absolute Error (MAE) of 38,533.1**, showing significant improvement after tuning.

![img15](https://github.com/user-attachments/assets/25d66c74-cbf0-427d-9ce6-ea387d762b70)
![img16](https://github.com/user-attachments/assets/b80a31f2-8724-46aa-ab91-d6b14de34951)
<img width="364" alt="img17" src="https://github.com/user-attachments/assets/69ad255d-d628-427c-bd33-bf5d460d4602" />
<img width="596" alt="img18" src="https://github.com/user-attachments/assets/a3f7bdfc-7cab-4231-b512-18336295e554" />

- **Final Iteration:** Used **2015-2016** as training and **2017-2018** as test data. Though the model identified trends, it struggled to predict spikes in Q4 sales accurately.

![img19](https://github.com/user-attachments/assets/75af7d0f-4a1d-49d9-bf99-cc3a494aa9ce)
![img20](https://github.com/user-attachments/assets/88bdc6c3-0caa-4123-b277-72b9f175cc01)
![img21](https://github.com/user-attachments/assets/b6c42666-d90c-440d-82cb-dad558d88146)


Overall, the **second iteration yielded the most accurate results**, demonstrating the importance of incorporating **recent sales behavior** into forecasting models.

## Limitations
- **Lack of Global Coverage**: The dataset focuses on a specific superstore’s sales and may not generalize to other industries or regions.
- **Limited External Factors**: While GDP was considered, other economic influences like inflation or interest rates were not included.
- **Short Timeframe**: The dataset spans only **four years**, limiting long-term forecasting accuracy.
- **Data Quality Issues**: Despite cleaning, there may still be unaccounted-for discrepancies affecting accuracy.

---
This project highlights the value of **data-driven decision-making** in sales forecasting, optimizing business strategies, and identifying trends that impact revenue growth.
