# Amazon Sales Data Analysis

A complete **EDA (Exploratory Data Analysis)** workflow for Amazon Sales data including product insights, category distribution, revenue analysis, and delivery performance metrics.



---

## 📌 Project Overview

This project analyzes Amazon sales data to understand:

* Top selling products
* Category-wise contribution
* Revenue distribution by state
* Delivery success rates
* Outlier detection in sales

All visualizations are generated using **Matplotlib** and **Seaborn**, and data processing is done with **Pandas**.

---

## 📂 Dataset Requirements

Your dataset should contain the following columns (case-sensitive based on your script):

* `Product_Name`
* `Product_Category`
* `Total_Sales_INR`
* `State`
* `Delivery_Status`

If column names differ, update them accordingly before running the analysis.

---

## 🚀 How to Run the Project

### 1. Install required libraries

```bash
pip install pandas numpy matplotlib seaborn
```

### 2. Load the dataset

```python
import pandas as pd
df = pd.read_csv("amazon_sales.csv")
```

### 3. Run the analysis code (shown below)

Copy the following Python code into your notebook or script.

---

## 📊 Analysis Code

### **1. Top 10 Best-Selling Products**

```python
if 'Product_Name' in df.columns:
    top_product = df.groupby('Product_Name')['Total_Sales_INR'].sum().sort_values(ascending=False).head(10)
    plt.figure(figsize=(10,5))
    sns.barplot(x=top_product.values, y=top_product.index)
    plt.title('Top 10 Best Selling Products')
    plt.xlabel('Total Sales')
    plt.ylabel('Product')
    plt.show()
```

### **2. Category-wise Sales Distribution**

```python
if 'Product_Category' in df.columns:
    df.groupby('Product_Category')['Total_Sales_INR'].sum().plot(kind='pie', autopct="%1.1f%%", startangle=90)
    plt.title("Category Wise Sales")
    plt.ylabel("")
    plt.show()
```

### **3. Outlier Detection in Sales**

```python
plt.figure(figsize=(8,4))
sns.boxplot(x=df['Total_Sales_INR'])
plt.title("Outliers in Total Sales")
plt.show()
```

### **4. State-wise Revenue**

```python
if 'Total_Sales_INR' in df.columns:
    state_sales = df.groupby('State')['Total_Sales_INR'].sum().sort_values(ascending=False)
    plt.figure(figsize=(10,5))
    sns.barplot(x=state_sales.values, y=state_sales.index)
    plt.title("Total Revenue by State")
    plt.xlabel("Revenue")
    plt.ylabel("State")
    plt.show()
```

### **5. Delivery Success Rate by State**

```python
if 'State' in df.columns and 'Delivery_Status' in df.columns:
    delivery_perf = (
        df.groupby('State')['Delivery_Status']
        .apply(lambda x: (x == 'Delivered').mean() * 100)
        .sort_values(ascending=False)
    )

    plt.figure(figsize=(10,5))
    sns.barplot(x=delivery_perf.values, y=delivery_perf.index)
    plt.title("Delivery Success Rate (%) by State")
    plt.xlabel("Delivery Success %")
    plt.ylabel("State")
    plt.show()
```

---

## 📈 Key Insights Generated

* Identifies top-performing products
* Shows revenue contribution by category
* Reveals state revenue ranking
* Highlights states with strong or weak delivery performance
* Detects unusually high or low sales values

---

## 📜 License

This project is free to use and modify.


