# 📊 Sales Data Analysis — Python

An end-to-end **Sales Data Analysis project using Python** to identify sales trends, top-performing products, customer behavior, regional performance, sales-channel contribution, payment preferences, and actionable business insights.
<img width="1233" height="527" alt="image" src="https://github.com/user-attachments/assets/d20a1c1b-24c4-4a93-a3a2-b140ddc3186c" />

---

## 📌 Project Overview

This project analyzes transactional sales data containing information about:

- Transactions
- Products
- Quantity
- Unit Price
- Sales
- Customers
- States
- Sales Channels
- Payment Types
- Dates

The objective is to transform raw sales data into **meaningful business insights** using Python and data visualization.

---

## 🎯 Business Objectives

The analysis aims to answer questions such as:

1. What is the total sales revenue?
2. Which products generate the highest sales?
3. Which states contribute the most revenue?
4. Which sales channel performs better?
5. Which payment method is most commonly associated with sales?
6. Who are the highest-value customers?
7. How are sales changing over time?
8. Are there seasonal sales patterns?
9. Which transactions/products are potential outliers?
10. What business actions can improve sales performance?

---

## 🛠️ Tools & Technologies

| Technology | Purpose |
|---|---|
| Python | Data Analysis |
| Pandas | Data Cleaning & Manipulation |
| NumPy | Numerical Analysis |
| Matplotlib | Data Visualization |
| Seaborn | Statistical Visualization |
| Jupyter Notebook | Analysis Environment |
| Excel | Source Data |

---

## 📂 Dataset

The dataset contains the following fields:

| Column | Description |
|---|---|
| Transaction ID | Unique transaction identifier |
| Product | Product purchased |
| Quantity | Number of units purchased |
| Unit Price (INR) | Price per unit |
| Date | Transaction date |
| Customer Name | Customer name |
| State | Customer/transaction state |
| Country | Country |
| Sales Channel | Store / Online etc. |
| Payment Type | Payment method |
| Sales | Total transaction sales |

### Example

| Transaction ID | Product | Quantity | Unit Price | Sales |
|---|---|---:|---:|---:|
| TX0001 | Smartwatch | 9 | ₹8,941 | ₹80,469 |
| TX0002 | Desktop PC | 9 | ₹19,827 | ₹178,443 |

---

# 🔎 Analysis Workflow

## 1. Data Loading

The Excel dataset is loaded using Pandas.

```python
import pandas as pd

df = pd.read_excel("Sales Data.xlsx")
```

---

## 2. Data Understanding

Initial analysis includes:

- Dataset shape
- Column names
- Data types
- Missing values
- Duplicate records
- Descriptive statistics

```python
df.shape
df.info()
df.describe()
df.isnull().sum()
df.duplicated().sum()
```

---

## 3. Data Cleaning

The project performs several preprocessing operations:

- Convert dates into datetime format
- Convert numerical columns into numeric data types
- Check duplicate transactions
- Identify invalid values
- Handle missing Sales values
- Create derived analytical columns

For transactions where Sales is missing:

```python
df["Sales"] = df["Quantity"] * df["Unit Price (INR)"]
```

---

# 📈 KPI Analysis

The project calculates important business KPIs including:

### Total Sales

```python
total_sales = df["Sales"].sum()
```

### Total Quantity Sold

```python
total_quantity = df["Quantity"].sum()
```

### Total Transactions

```python
total_transactions = df["Transaction ID"].nunique()
```

### Unique Customers

```python
unique_customers = df["Customer Name"].nunique()
```

### Average Transaction Value

```python
average_transaction_value = (
    total_sales / total_transactions
)
```

---

# 📅 Sales Trend Analysis

Sales are analyzed across:

- Year
- Month
- Year-Month
- Calendar month

The project uses line charts to identify:

- Growth trends
- Declining periods
- Seasonal patterns
- Peak sales months

Example:

```python
monthly_sales = (
    df.groupby("Year-Month")["Sales"]
      .sum()
      .reset_index()
)
```

---

# 🛍️ Product Analysis

Product-level analysis identifies:

- Top-selling products
- Lowest-performing products
- Sales contribution
- Quantity sold
- Average unit price
- Transaction count

### Top Products

```python
product_performance = (
    df.groupby("Product")
      .agg(
          Sales=("Sales", "sum"),
          Quantity=("Quantity", "sum"),
          Transactions=("Transaction ID", "nunique")
      )
      .sort_values("Sales", ascending=False)
)
```

---

# 👥 Customer Analysis

Customer analysis helps identify:

- Highest-value customers
- Repeat customers
- Customer purchase frequency
- Customer sales contribution
- Potential high-value customer segments

The project also calculates each customer's contribution to total sales.

### Customer Sales Share

```python
customer_sales_share = (
    customer_sales / total_sales
) * 100
```

---

# 🌎 State-wise Analysis

Sales performance is analyzed across Indian states.

Key metrics:

- Total Sales
- Quantity
- Transactions
- Unique Customers
- Sales Contribution %

This helps identify regions where the business has:

- Strong demand
- Weak performance
- Growth opportunities

---

# 🏪 Sales Channel Analysis

Sales are compared across available channels such as:

- Online
- Store

The analysis measures:

- Total sales
- Quantity
- Transactions
- Customers
- Average transaction value
- Sales contribution

This helps determine which channel generates stronger business performance.

---

# 💳 Payment Type Analysis

The project analyzes sales based on payment methods.

Metrics include:

- Sales
- Transactions
- Quantity
- Sales Share %
- Average Transaction Value

This can help businesses understand customer payment preferences.

---

# 📊 Statistical Analysis

The project analyzes the distribution of:

- Sales
- Quantity
- Unit Price

Descriptive statistics include:

- Mean
- Median
- Standard deviation
- Minimum
- Maximum
- Quartiles

---

# 🚨 Outlier Detection

Potential sales outliers are identified using the **Interquartile Range (IQR)** method.

### Formula

```text
IQR = Q3 - Q1

Lower Bound = Q1 - 1.5 × IQR

Upper Bound = Q3 + 1.5 × IQR
```

Transactions outside these boundaries are investigated as potential outliers.

---

# 🔗 Correlation Analysis

Correlation analysis is performed between:

- Quantity
- Unit Price
- Sales

A heatmap is used to visualize relationships between numerical variables.

```python
correlation = df[
    ["Quantity", "Unit Price (INR)", "Sales"]
].corr()
```

---

# 📊 Visualizations

The project creates multiple business-oriented visualizations.

### Sales Trend

Line chart showing monthly sales.

### Top Products

Bar chart showing highest revenue-generating products.

### Top States

Bar chart showing state-wise sales.

### Channel Performance

Comparison of Online vs Store sales.

### Payment Analysis

Sales contribution by payment type.

### Sales Distribution

Histogram showing distribution of transaction sales.

### Quantity Distribution

Distribution of units sold per transaction.

### Correlation Heatmap

Relationship between important numerical variables.

---

# 💡 Business Insights

The analysis generates insights such as:

- Which product contributes the most revenue
- Which state generates maximum sales
- Which channel performs best
- Which customers generate the most revenue
- Which months have peak sales
- How concentrated sales are among top customers
- Where potential growth opportunities exist
- Which transactions require further investigation

---

# 🚀 Business Recommendations

Based on the analysis, potential recommendations include:

### 1. Focus on High-Value Customers

Create targeted retention and upselling campaigns for customers generating significant revenue.

### 2. Prioritize Top Products

Ensure high-performing products have sufficient inventory and marketing support.

### 3. Improve Weak Products

Investigate products with low sales for:

- Pricing issues
- Low demand
- Poor positioning
- Marketing gaps

### 4. Optimize Sales Channels

Compare Online and Store performance and allocate marketing resources accordingly.

### 5. Regional Strategy

Focus regional campaigns and distribution efforts on high-potential states.

### 6. Seasonal Planning

Use historical monthly trends to improve:

- Inventory planning
- Marketing campaigns
- Sales targets

### 7. Monitor Large Transactions

Investigate unusually large transactions because they can significantly influence overall revenue.

---

# 📁 Project Structure

```text
Sales-Data-Analysis/
│
├── Sales_Data_Full_Analysis.ipynb
│
├── Sales Data.xlsx
│
├── Sales_Analysis_Output.xlsx
│
├── README.md
│
└── images/
    ├── monthly_sales_trend.png
    ├── top_products.png
    ├── top_states.png
    ├── channel_analysis.png
    └── payment_analysis.png
```

---

# ▶️ How to Run the Project

## Step 1 — Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/Sales-Data-Analysis.git
```

## Step 2 — Open Project

```bash
cd Sales-Data-Analysis
```

## Step 3 — Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

## Step 4 — Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
Sales_Data_Full_Analysis.ipynb
```

## Step 5 — Run All Cells

In Jupyter:

```text
Kernel → Restart & Run All
```

---

# 📌 Key Skills Demonstrated

This project demonstrates practical knowledge of:

- Python for Data Analysis
- Pandas
- NumPy
- Data Cleaning
- Exploratory Data Analysis (EDA)
- Data Aggregation
- GroupBy
- Pivot Tables
- Time-Series Analysis
- Customer Analysis
- Product Analysis
- Business KPI Analysis
- Statistical Analysis
- Outlier Detection
- Correlation Analysis
- Data Visualization
- Business Insight Generation
- Data-driven Recommendations

---

# 💼 Portfolio / Resume Description

**Sales Data Analysis using Python**

> Developed an end-to-end sales analytics project using Python, Pandas, NumPy, Matplotlib and Seaborn. Performed data cleaning, exploratory data analysis, KPI analysis, time-series analysis, product and customer performance analysis, geographic analysis, sales-channel and payment analysis, outlier detection and correlation analysis. Generated business insights and recommendations to support sales and strategic decision-making.

---

# 🎯 Interview Explanation

### Tell me about your project.

> "I worked on an end-to-end Sales Data Analysis project using Python. I started by loading the Excel dataset using Pandas and performed data quality checks for missing values, duplicates and incorrect data types. Then I cleaned the data and created derived columns such as Year, Month and Average Selling Price.
>
> After that, I performed exploratory data analysis across different business dimensions including products, customers, states, sales channels and payment methods. I also analyzed monthly and yearly sales trends and identified top-performing products and customers.
>
> For visualization, I used Matplotlib and Seaborn to create trend charts, bar charts, distributions and correlation heatmaps. Finally, I converted the analysis into business insights and recommendations that could help improve sales, customer retention, regional strategy and channel performance."

---

## ⭐ Project Outcome

The project converts raw transactional data into a structured **business intelligence analysis**, demonstrating how Python can be used to move from:

```text
Raw Data
    ↓
Data Cleaning
    ↓
EDA
    ↓
KPI Analysis
    ↓
Visualization
    ↓
Business Insights
    ↓
Recommendations
```

---

## 👨‍💻 Author

**Dheeraj Sharma**

Aspiring Data Analyst | Python | SQL | Power BI | Excel

### Areas of Interest

- Data Analytics
- Business Intelligence
- MIS Analytics
- Data Visualization
- Business Analysis
- Python Analytics
- SQL

---

⭐ If you find this project useful, consider giving the repository a star!
