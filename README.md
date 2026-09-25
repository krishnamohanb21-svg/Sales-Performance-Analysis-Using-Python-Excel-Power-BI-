# Sales-Performance-Analysis-Using-Python-Excel-Power-BI-
# Problem Statement of Sales Performance Analysis
The purpose of this project is to analyse sales data to understand the factors that affect sales and profit. The dataset contains information about products, units sold, sales, profit, discounts, customers, segments, countries, and time periods. The analysis will identify high-performing products, sales and profit trends, and relationships between important variables. The findings will help identify areas for improving sales performance, profitability, and business decision-making
# Project Description of the Sales Performance Analysis
This project analyses sales transaction data to uncover key drivers of revenue, profitability, and discount behaviour across a global business. The dataset contains 700 records spanning 2013–2014, covering 5 customer segments (Government, Enterprise, Midmarket, Small Business, and Channel Partners), 5 countries (United States, Canada, Germany, France, and Mexico), and 6 products (Carretera, Paseo, VTT, Velo, Amarilla, and Montana).
Each record captures units sold, manufacturing price, sale price, gross sales, discounts applied (categorized as None, Low, Medium, or High), net sales, cost of goods sold (COGS), and resulting profit, along with the transaction date.
The goal of the analysis is to evaluate sales and profitability trends across segments, countries, and products over time, assess how discounting impacts net sales and margins, and identify top- and under-performing areas of the business to support data-driven decisions on pricing, discounting strategy, and market/segment focus.
# Tools & Technologies
Python (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn	Data cleaning, EDA, visualization, regression modeling)
Jupyter Notebook	Interactive analysis environment
Microsoft Excel	PivotTables, PivotCharts, KPI dashboard
Power BI	Interactive drill-down dashboard, DAX measures
# Data Cleaning Process
1. Overview
Before performing exploratory analysis, the raw sales dataset was inspected and cleaned in Python (Pandas) to ensure accuracy and consistency. The dataset contains 700 rows and 15 columns covering segment, country, product, pricing, sales, and profit information for 2013–2014. The data cleaning process involved four main steps: initial inspection, missing value detection, duplicate detection, and missing value treatment.
2. Initial Data Inspection
The dataset was first loaded and inspected to understand its structure and data types before any cleaning was performed.
•	df.head() / df.tail() — reviewed the first and last rows to sanity-check the data
•	df.shape — confirmed 700 rows × 15 columns
•	df.info() — reviewed column data types and non-null counts
•	df.dtypes — checked each column's data type (object, float64, int64)
•	df.describe() — generated summary statistics (mean, std, min, max, quartiles) for numeric columns
3. Missing Value Detection
The df.isnull().sum() function was used to count missing values in every column. The results showed that only one column contained missing data:
Column	Missing Values	Total Rows	% Missing
Discount Band	53	700	7.6%
All other columns	0	700	0%
All numeric columns (Units Sold, Manufacturing Price, Sale Price, Gross Sales, Discounts, Sales, COGS, Profit, Year) and categorical columns (Segment, Country, Product, Date, Month Name) were fully populated.
4. Duplicate Record Check
The df.duplicated().sum() function was applied to check for fully duplicated rows across the dataset. The result returned 0, confirming that no duplicate records existed and no rows needed to be dropped.
5. Handling Missing Values
A copy of the original dataframe (df_filled = df.copy()) was created before any modification, to preserve the raw dataset. Missing numeric values were then imputed using appropriate statistical measures, chosen based on each column's distribution:
Column	Method Used	Reasoning
Units Sold	Mean (fillna with .mean())	Values were fairly evenly distributed, so the mean was a representative fill value
Sale Price	Mean (fillna with .mean())	Used to keep the average price level consistent
Manufacturing Price	Median (fillna with .median())	Column had outliers / skew, so the median was more robust than the mean

Note: The Discount Band column (the only column with actual missing values) is categorical, so it was retained as-is (NaN) for segmentation purposes rather than being numerically imputed; rows with a missing Discount Band typically corresponded to transactions with zero discount.
6. Data Cleaning Summary
Step	Action Taken	Result
Inspect structure	head(), tail(), shape, info(), dtypes, describe()	Confirmed 700 rows × 15 columns, correct data types
Check missing values	isnull().sum()	53 missing values found in 'Discount Band' only
Check duplicates	duplicated().sum()	0 duplicate rows found
Impute Units Sold	fillna(mean())	Missing values replaced with column mean
Impute Sale Price	fillna(mean())	Missing values replaced with column mean
Impute Manufacturing Price	fillna(median())	Missing values replaced with column median
# Exploratory Data Analysis & Visualizations
1) Which segment has the highest sales?
<img width="1090" height="862" alt="image" src="https://github.com/user-attachments/assets/e1cc9ead-fbe5-424d-982c-b9f28e5159cb" />
2) Which country has the lowest sales?
<img width="1006" height="847" alt="image" src="https://github.com/user-attachments/assets/3eb4f1f3-958e-4322-8dac-be0985c26282" />
3) Which Product has the Highest Sales ?
<img width="963" height="761" alt="image" src="https://github.com/user-attachments/assets/8a383e39-8726-4422-9118-7d53ec2f1f5a" />
4) Which product has highest in the profit ?
 <img width="1019" height="786" alt="image" src="https://github.com/user-attachments/assets/43c32f34-9e42-47a3-b94d-baa882d8b294" />
5) Which Year has highest in the Sales ?
<img width="1148" height="753" alt="image" src="https://github.com/user-attachments/assets/ef21bc1e-9004-48a5-a155-0f9a31e764c2" />
6) Which product has the highest units sold?
<img width="1043" height="823" alt="image" src="https://github.com/user-attachments/assets/37f3c5c1-2a9c-4a2a-878e-0157fc670cfe" />
7) What are the major sales and profit trends in the dataset?
<img width="1007" height="831" alt="image" src="https://github.com/user-attachments/assets/34d76804-01f2-4915-92ce-d7f43730e98d" />
<img width="1632" height="521" alt="image" src="https://github.com/user-attachments/assets/43100fb1-f459-48cf-bb07-022a80cabff6" />
8) Are there any outliers in Sales, Profit, or Units Sold?
<img width="1743" height="712" alt="image" src="https://github.com/user-attachments/assets/408c53b3-2732-48d8-bdd8-264cefcfc696" />
<img width="1979" height="598" alt="image" src="https://github.com/user-attachments/assets/303a12f4-4617-47f2-865d-a042195791b3" />
<img width="2000" height="500" alt="image" src="https://github.com/user-attachments/assets/5a713baa-5d0c-40c1-b754-c8f7e403a867" />
9) What is the correlation between Units Sold, Sales, COGS, and Profit?
<img width="855" height="879" alt="image" src="https://github.com/user-attachments/assets/fcf1b9b4-9baa-489b-85b9-d556424c5e01" />
# Explanation of Heatmap 
1) Gross Sales ↔ Sales ↔ COGS (≈0.99–1.00): Near-perfect correlation — expected, since Sales is derived from Gross Sales minus Discounts, and COGS scales directly with sales volume.
2) Gross Sales/Sales ↔ Profit (0.78–0.81): Strong positive relationship — higher sales generally drive higher profit, though not perfectly, since discounts and costs eat into margins.
3) Discounts ↔ Gross Sales/Sales (0.74–0.78): Higher discounts are associated with higher gross sales — likely because discounts are applied more on large-volume deals, not that discounting causes more sales.
4) Discounts ↔ Profit (0.38): Only a moderate relationship, weaker than Discounts ↔ Sales — suggesting heavy discounting boosts revenue but doesn't proportionally boost profit (it erodes margin).
5) Sale Price ↔ Profit (0.65): Moderately strong — pricing has a meaningful but not dominant effect on profitability.
6) Units Sold ↔ most variables (0.23–0.33): Surprisingly weak correlation with Sales/Profit — implying revenue is driven more by price and product mix than raw unit volume.
7) Manufacturing Price: Very weak correlation with almost everything (≈0.00–0.07) — manufacturing cost doesn't vary much with sales performance in this dataset.
8) Year: Near-zero correlation with all variables — no strong time-based trend captured here (makes sense, since correlation only checks linear year-over-year scaling, not seasonal patterns).
# Create a regression model to predict sales
<img width="1599" height="1045" alt="image" src="https://github.com/user-attachments/assets/82fadb99-0fa4-4327-99d8-030ea6f57380" />
# Excel Dashboard
Microsoft Excel is a spreadsheet program developed by Microsoft that allows users to organize, calculate, format, and analyse data in a grid of rows and columns
<img width="1364" height="963" alt="image" src="https://github.com/user-attachments/assets/5f33623c-1f71-4b39-abdc-03ebbbd15c22" />
# Sales Dataset
<img width="1744" height="806" alt="image" src="https://github.com/user-attachments/assets/1cbfd550-a2f5-47c1-a986-1eea8085a8f7" />
# Segment Analysis
<img width="1626" height="906" alt="image" src="https://github.com/user-attachments/assets/1aa37ba7-601d-411f-af93-2df70c2871c1" />
# Country Analysis
<img width="1510" height="803" alt="image" src="https://github.com/user-attachments/assets/baf49179-89e3-44ac-ad42-4fa7efc2736f" />
# Month Analysis
<img width="1536" height="766" alt="image" src="https://github.com/user-attachments/assets/650396b4-7662-4eb5-a3eb-9647b836a144" />
# Product Analysis
<img width="1695" height="781" alt="image" src="https://github.com/user-attachments/assets/fe64abe2-73c2-4045-a20b-1ed68b96bd87" />
# Discount Analysis
<img width="1608" height="862" alt="image" src="https://github.com/user-attachments/assets/fee20d4f-d540-4a49-96df-9020b46b9332" />
# Power BI Dashboard
An interactive dashboard with slicers (Year, Month, Product) and drill-through visuals, built on DAX measures 
<img width="1757" height="943" alt="image" src="https://github.com/user-attachments/assets/f137e3e8-4d5d-4e03-b5bb-48e041da8a03" />
# Table View
<img width="1631" height="645" alt="image" src="https://github.com/user-attachments/assets/26708946-9405-421b-a4b1-1686b38f8682" />
<img width="247" height="942" alt="image" src="https://github.com/user-attachments/assets/96bf95a1-196a-4296-afaa-9457076c114f" />
<img width="230" height="945" alt="image" src="https://github.com/user-attachments/assets/0a86c51a-2654-47a3-9e5f-b0d83f4492ec" />
<img width="221" height="903" alt="image" src="https://github.com/user-attachments/assets/85f5497a-72c0-4660-a909-2e64bf69e5eb" />
# DAX View 
Sum of sales = SUM('Sales Dataset'[ Sales])
<img width="1417" height="655" alt="image" src="https://github.com/user-attachments/assets/988e9391-fa2e-4d9d-9438-9a6dee8d466a" />
Sum of Profit = SUM('Sales Dataset'[Profit])
<img width="1663" height="806" alt="image" src="https://github.com/user-attachments/assets/71b8df5c-0816-4408-a5ff-21f18483418c" />
Total no of Units sold = sum('Sales Dataset'[Units Sold])
<img width="1649" height="800" alt="image" src="https://github.com/user-attachments/assets/603ff734-34e2-4eae-a0d8-18f70d0236f1" />
Average Sales = AVERAGE('Sales Dataset'[ Sales])
<img width="1623" height="791" alt="image" src="https://github.com/user-attachments/assets/7dced0ca-99a6-44e4-8b8b-16c044dee0f6" />
Total Discount = SUM('Sales Dataset'[Discounts])
<img width="1582" height="781" alt="image" src="https://github.com/user-attachments/assets/b74cb42f-6333-44de-943f-517ddfc52331" />
Profit Margin % = [Sum of Profit]/[Sum of sales]*100
<img width="1607" height="791" alt="image" src="https://github.com/user-attachments/assets/3d15994d-ab10-4ea7-864c-ec26d5389f9d" />
# Summary of Findings and Recommendations
# Summary of Findings 
The analysis reveals some significant differences in terms of sales and profits by product, year, country, and customer segment. Certain products contribute much more towards total sales and profit than others. Units sold are shown to have an important relationship with sales, although there may be impacts from discounts affecting profit margins. Analysis at a year- and month-wise level allows us to see periods of increased sales performance.
# Recommendations
High performing products/customer segments should focus efforts upon to increase sales & profitability as required. It would seem prudent to monitor levels of discounting in order to prevent unwarranted reductions in profit margins. It will be necessary to analyze low performing products and regions in search of avenues of improvements. Sales Trends could assist planning for inventories and marketing activities and sales strategy's for high demand times.
