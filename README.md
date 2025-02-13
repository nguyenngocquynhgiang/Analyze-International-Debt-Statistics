# **Analyze International Debt Statistics**

In the [**Analyze International Debt Statistics**](https://www.datacamp.com/projects/754) project, I will analyze international debt data from the World Bank using SQL queries. SQL is an essential tool for efficient data analysis.

Write SQL queries to answer interesting questions about international debt using data from The World Bank.

In the project, I will be finding the:

1. Distinct countries  
2. Distinct debt indicators  
3. Total amount of debt owed by the countries  
4. Country with the highest debt  
5. Average amount of debt across indicators  
6. The highest amount of principal repayments  
7. The most common debt indicator  

I will connect to the [**World Nations**](https://www.datacamp.com/workspace/datasets/sample-integration-mariadb) MariaDB dataset and apply similar queries to gain more experience in SQL database analysis. I will also take the [**Exploratory Data Analysis in SQL**](https://www.datacamp.com/courses/exploratory-data-analysis-in-sql) course to learn advanced techniques for working with various SQL databases.

---

# **Project Description**

In this project, I will analyze international debt data collected by The World Bank. The dataset shows the amount of debt (in USD) that developing countries owe across various categories. I will use data manipulation skills to determine which countries have the highest and lowest debt amounts, a Summary Report, etc. 

## 1. Exploring the Dataset

| Column | Definition | Data Type |
| --- | --- | --- |
| country_name | Name of the country | varchar |
| country_code | Code representing the country | varchar |
| indicator_name | Name of the debt indicator | varchar |
| indicator_code | Code representing the debt indicator | varchar |
| debt | Value of the debt indicator for the given country (in current US dollars) | float |

## 2. Main Process

### 2.1 The Dataset

The datasets have 124 countries.

The **DISTINCT** keyword ensures that only unique country names are counted.

The **COUNT()** function gives the total number of these unique entries.

My query identifies the top 5 countries with the most records in the international_debt table. The result shows that Dominican Republic, Albania, Cameroon, Indonesia, and Ghana all have 25 records each, tied for the most.

**Validate unique mapping between country_name and country_code**

### 2.2 Analysis

#### **Country with the Highest Amount of Debt**
- `SUM(debt)` aggregates the debt values for each country.
- `GROUP BY country_name` groups the rows by country.
- `ORDER BY total_debt DESC` sorts the result in descending order of total debt.
- `LIMIT 1` ensures that only the country with the highest debt is returned.

The query results show that China has the highest total debt at **285,793,494,734.2 USD**.

#### **Country with the Lowest Principal Repayments**
- The `WHERE indicator_name LIKE '%Repayment%'` filters rows to include only those where the `indicator_name` mentions "Repayment."
- `SUM(debt)` calculates the total repayments for each country.
- `ORDER BY total_repayments ASC` sorts the result in ascending order to find the lowest repayments.
- `LIMIT 1` ensures that only the country with the lowest repayments is returned.

Timor-Leste has the lowest amount of principal repayments for external long-term debt, with a repayment amount of **825,000 USD**.

#### **Top 5 Countries with the Highest Total Debt**
- **China**: Holds the largest total debt, approximately **285.79 billion USD**.
- **Brazil**: Close behind China, with a total debt of **280.62 billion USD**.
- **Regions and Groupings**: Presence of regions like *"South Asia"* and *"Least developed countries: UN classification"* indicates that the dataset aggregates debt data not only by countries but also by broader economic or geographic classifications.

#### **Total Debt by Each Indicator**
- **Top Indicator**: The largest contributor to total debt is **"Principal repayments on external debt, long-term (AMT, current US$)"**, with approximately **732.20 billion USD**.
- **Second Indicator**: "Principal repayments on external debt, private nonguaranteed (PNG)" contributes around **407.73 billion USD**.
- **Interest Payments**: "Interest payments on external debt, long-term (INT)" rank fifth, with a total of **203.86 billion USD**.

#### **Average Debt per Country**
- **China and Brazil Lead**: China has the highest average debt per record, approximately **11.91 billion USD**, closely followed by Brazil at **11.69 billion USD**.
- **Regional Classifications**: Regions like *"South Asia"* and *"Least developed countries: UN classification"* have high average debt values.

#### **Exploring Outliers**
This query identifies outlier debt records where the debt value exceeds the average plus two standard deviations of all debt values in the dataset.

- **China and Brazil Dominate**: China has **two outlier entries**, with a combined debt of over **168 billion USD**. Brazil also has two records totaling approximately **133.6 billion USD**.
- **Long-Term Debt is the Primary Contributor**: Most outliers are associated with "Principal repayments on external debt, long-term," indicating large repayments in this category.

### **Create a Summary Report**
This report will provide insights into the highest and lowest debts, common debt indicators, and average debt distribution. Further analysis can be conducted to explore debt patterns across different economic regions.

