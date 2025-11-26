

# Customer Behavior Data Analysis Project

This project focuses on exploring and understanding customer shopping patterns using Python, SQL, and Power BI. The objective is to take a raw dataset, clean it, analyze key trends, and present insights in the form of SQL outputs and interactive visual dashboards.

---

## 📌 Project Purpose

The goal of this project is to practice end-to-end data analysis by:

* Cleaning and preparing customer data
* Creating new meaningful features
* Storing the processed data in a SQL database
* Writing analytical SQL queries
* Building a simple visual dashboard

This project reflects what data analysts work on in real business environments.

---

## 🛠️ Tools Used

* **Python (pandas, SQLAlchemy)** – for cleaning and processing data
* **PostgreSQL / MySQL / SQL Server** – for storing and querying data
* **Power BI** – for dashboard creation
* **Jupyter Notebook** – for step-by-step analysis

---

## 📂 Project Structure

```
.
├── data/
│   └── customer_shopping_behavior.csv
│
├── notebooks/
│   └── Customer_Shopping_Behavior_Analysis.ipynb
│
├── sql/
│   └── customer_behavior_sql_queries.sql
│
├── dashboard/
│   └── customer_behavior_dashboard.pbix
│
└── README.md
```

---

## 🔄 Workflow Overview

### **1. Data Preparation (Python)**

In the notebook, I performed:

* Reading the dataset
* Checking data types and missing values
* Filling missing review ratings using median values within each category
* Renaming columns to snake_case for consistency
* Creating new fields such as:

  * Age groups
  * Purchase frequency (mapped into numerical days)
* Removing redundant columns

### **2. Loading Data Into SQL**

The cleaned DataFrame is loaded into a database table using SQLAlchemy.
I included connection code for:

* PostgreSQL
* MySQL
* MS SQL Server

You can choose the database you prefer and update the credentials accordingly.

### **3. SQL Analysis**

The SQL file contains a set of analytical queries that explore:

* Customer spending patterns
* Frequency of purchases
* Category-wise performance
* Age group behavior
* Impact of discounts

These queries help understand how different customer groups behave and what drives purchases.

### **4. Dashboard (Power BI)**

Power BI is connected to the SQL database to visualize:

* Total revenue
* Customer distribution
* Purchases by category
* Age-wise and gender-wise insights
* Discount-related patterns

The dashboard provides a clear view of customer behavior trends.

---

## 🧪 Example Code Snippet From My Notebook

```python
import pandas as pd

df = pd.read_csv('customer_shopping_behavior.csv')

# Fill missing ratings by category
df['Review Rating'] = df.groupby('Category')['Review Rating'].transform(lambda x: x.fillna(x.median()))

# Standardize columns
df.columns = df.columns.str.lower().str.replace(' ', '_')
df = df.rename(columns={'purchase_amount_(usd)': 'purchase_amount'})

# Create age groups
labels = ['Young Adult', 'Adult', 'Middle-aged', 'Senior']
df['age_group'] = pd.qcut(df['age'], 4, labels=labels)

# Map purchase frequency to days
frequency_map = {
    'Weekly': 7, 'Bi-Weekly': 14, 'Fortnightly': 14,
    'Monthly': 30, 'Quarterly': 90,
    'Annually': 365, 'Every 3 Months': 90
}
df['purchase_frequency_days'] = df['frequency_of_purchases'].map(frequency_map)
```

---

## 🎯 What I Learned

* How to handle missing values and clean real-world data
* How to engineer new features for analysis
* How to send data from Python into SQL databases
* How to write SQL queries for business-related insights
* How to build dashboards that represent analytical findings clearly

---

## 📄 License

This project is for learning purposes.
You are welcome to use this structure and modify it for your own practice.

---

