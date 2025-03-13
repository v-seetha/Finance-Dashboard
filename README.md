# Finance-Dashboard

Below is a comprehensive narrative of how the personal finance dashboard was created for a friend, following a structured template similar to the one shown in the second image. The goal is to illustrate the entire process—from the casual conversation that sparked the project, to the detailed data analysis steps, and finally the insights derived from the dashboard visualizations.

## 1. The Story Behind the Project

I was having tea with a friend when, mid-conversation, she mentioned that she doesn’t really track her spending or saving habits. She felt like her finances were on “autopilot,” and she had no idea where her money went each month. I immediately offered to help by creating a personal finance dashboard, which would give her a clear view of her income, expenses, savings, and overall net worth. She agreed and provided me with all the data she had regarding her monthly expenditures and income sources.


## 2. Project Overview

This personal finance dashboard project aims to empower my friend with insights into her financial habits. By structuring and visualizing her data, the dashboard answers questions such as:

- **How much does she spend each month, and on which categories?**  
- **How do her savings compare to her total income over time?**  
- **What is her net worth trend and how has it changed month-over-month?**  
- **Which expense categories are growing the fastest?**  
- **Is she allocating her money effectively among savings instruments (mutual funds, fixed deposits, etc.)?**

### 2.1 Dataset Description
- **Columns**:  
  - **Type**: Indicates whether the record is an Income or an Expense.  
  - **Component**: The specific category (e.g., Salary, Bills, Groceries & Food, House Rent, Leisure, Mutual Funds, etc.).  
  - **Date**: Month and year of the transaction (e.g., Jan 18, Feb 18).  
  - **Value**: The amount of money in each transaction or category for that month.  
  - **Year**: The calendar year (e.g., 2018, 2019, 2020, etc.).

- **Data Source**: My friend’s personal records, which included monthly bank statements, credit card bills, and notes she kept in a spreadsheet.  
- **Time Period Covered**: January 2018 to January 2021.

### 2.2 Goal of the Project
- To build a user-friendly dashboard that tracks income, expenses, savings, and net worth.  
- To help my friend understand her financial habits and make informed decisions about budgeting, saving, and investing.  
- To identify any trends or anomalies in her spending patterns over the past few years.


## 3. Import Libraries

In the data notebook, the following libraries (or equivalents, depending on the chosen data analysis environment) were used:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
# ... and any other libraries like plotly, etc., as needed
```

- **pandas** and **numpy** for data manipulation and analysis.  
- **matplotlib** and **seaborn** for exploratory visualizations.  
- Additional libraries might be used for interactive dashboards (e.g., Power BI, Plotly, etc.).

---

## 4. Load Data

1. **Reading the CSV/Excel File**  
   ```python
   df = pd.read_csv('finance_data.csv')
   ```
   or
   ```python
   df = pd.read_excel('finance_data.xlsx')
   ```

2. **Initial Data Glance**  
   ```python
   df.head()  # Shows the first 5 rows
   df.info()  # Provides data types and memory usage
   ```

3. **Check Column Names**  
   - Renamed columns if necessary (e.g., “Value” to “Amount” or “Date” to “MonthYear”) for consistency.  

4. **Check for Missing or Incorrect Values**  
   - Filled or removed missing values where appropriate.  
   - Ensured that the **Date** column was in a proper date format if needed for time-series analysis.

---

## 5. Data Cleaning and Preparation

- **Date Conversion**: Converted the date column into a datetime format (or created a Month-Year format) so that the data could be easily grouped by month and year.  
- **Categorical Encoding**: Since “Type” (Income/Expense) and “Component” (Salary, Groceries, etc.) are categorical, no numeric encoding was strictly necessary for basic aggregations, but for advanced analyses, label encoding or one-hot encoding might be used.  
- **Creating Derived Columns**:  
  - **Month** and **Year** columns for grouping and time-series analysis.  
  - **Net Savings**: A possible derived metric (Income - Expenses) per month.

---

## 6. Exploratory Data Analysis (EDA)

### 6.1 Univariate Analysis
- **Income**: Checked the distribution of income over months and years.  
- **Expenses**: Looked at the range, mean, and median of expenses to understand overall spending patterns.  
- **Savings %**: Calculated how much of the income was saved each month (savings / income * 100).

### 6.2 Categorical Feature Selection
- **Type**: Segregated the data into Income vs. Expense to see the proportion and trends.  
- **Component**: Classified expenses into categories (Bills, Groceries, Health, House Rent, Leisure, Shopping, etc.) and also classified savings or investment categories (Mutual Funds, Fixed Deposit, etc.).

### 6.3 Numerical Features
- **Value**: This is the main numeric feature representing monetary amounts. Analyzed min, max, mean, median, etc.  
- **Net Worth**: Summed up all assets (cash, investments, etc.) and subtracted any liabilities if provided. Tracked over time.

### 6.4 Key Insights from the Distribution
- **High-Spend Categories**: Identified the categories that consumed the largest share of expenses (e.g., House Rent, Groceries, Leisure).  
- **Growth in Net Worth**: Observed how consistent savings and investments led to a rising net worth trend.  
- **Saving Habits**: Found that some months had a significantly higher savings percentage than others, possibly due to bonus income or reduced spending.



## 7. Building the Finance Dashboard

Using the cleaned dataset, I created a series of visualizations to offer a comprehensive view of my friend’s financial journey. Below are the key components of the dashboard and the questions they help answer:

### 7.1 Overall Finance Dashboard
- **Key Figures**:  
  - **Total Income** (e.g., ₹1.51M),  
  - **Total Expenses** (e.g., 78% of income),  
  - **Savings %** (e.g., 22%),  
  - **Net Worth** (e.g., ₹325.5K).  
- **Question it answers**: “At a glance, how am I doing financially? How much am I saving, and what’s my current net worth?”

### 7.2 Detailed Statement Table
- Shows the breakdown by **Type** (Income, Expense), **Component** (Salary, Bills, Groceries, etc.), **Date**, **Value**, and **Year**.  
- **Question it answers**: “Where exactly is each rupee going or coming from each month?”

### 7.3 Monthly Trends by Expense Category
- A line chart that plots each expense category over time (Bills, Groceries & Food, Health, House Rent, Leisure, Shopping, etc.).  
- **Question it answers**:  
  - “How do my expenses in each category change month-over-month?”  
  - “Are certain categories (like Shopping or Groceries) creeping up over time?”

### 7.4 Savings & Investments Over Time
- Another line chart focusing on savings components: Emergency Fund, Fixed Deposit, Liquid Cash, Mutual Funds, etc.  
- **Question it answers**:  
  - “How much am I contributing to each savings/investment instrument each month?”  
  - “Is my Emergency Fund growing as planned? How volatile are my Mutual Fund contributions?”

### 7.5 Net Worth Trend
- A single line chart showing the upward (or downward) movement of net worth from Jan 2018 to Jan 2021.  
- **Question it answers**:  
  - “Is my overall wealth increasing over time? By how much each month?”  
  - “Are there any months where net worth dipped, and why?”

### 7.6 Total Income vs. Total Expenses vs. Savings %
- A combined bar and line chart: bars for total income and expenses, and a line for savings percentage.  
- **Question it answers**:  
  - “Am I living within my means?”  
  - “What proportion of my monthly income am I able to save?”



## 8. Key Insights and Observations

1. **Steady Salary Growth**: The salary component showed an incremental rise from ₹30K to ₹35K, reflecting possible raises or job changes.  
2. **High Expense Categories**: House Rent and Groceries & Food dominated the monthly expenses.  
3. **Savings Percentage Fluctuations**: Some months had a savings rate as high as 30%, while others dipped below 10%. Likely reasons include festive season spending, travel, or unexpected bills.  
4. **Net Worth Growth**: A consistent upward trend suggests disciplined saving and investing. The friend’s net worth climbed from around ₹70K in Jan 2018 to over ₹350K in Jan 2021.  
5. **Investment Portfolio Distribution**: A substantial chunk was going into Mutual Funds, indicating a preference for market-based investments, while Fixed Deposits and Liquid Cash were used for emergency or short-term needs.


## 9. Conclusion

Creating this personal finance dashboard turned out to be incredibly insightful. My friend, who initially had little visibility into her spending and saving habits, can now easily see:

- Where her money is being spent each month.  
- How her income and expenses have changed over time.  
- Whether she is meeting her savings targets.  
- The progress of her net worth, which serves as a motivating factor to continue saving and investing.

With these visualizations and analyses, she can make informed decisions about adjusting her budget, planning for future goals, and possibly optimizing her investment strategy.



## 10. Possible Next Steps

1. **Budget Setting**: Use the dashboard to set monthly or quarterly budget targets for each category.  
2. **Automated Data Updates**: Automate the data refresh (e.g., using a connection to bank statements or a manual monthly update routine).  
3. **Further Analysis**: Conduct a deeper dive into correlation between spending categories and savings (e.g., “If I reduce leisure spending by 10%, how much more can I invest?”).  
4. **Predictive Modeling**: Extend the project to predict future expenses or net worth based on historical trends and planned lifestyle changes.  


### Final Thoughts

This personal finance dashboard not only provides clarity on current financial status but also lays the groundwork for better money management.

*I hope this detailed walkthrough gives you a comprehensive understanding of how the project was structured, the data was processed, and the insights were derived.*
