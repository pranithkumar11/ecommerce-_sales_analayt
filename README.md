# E-Commerce Performance & Operations Analytics

## 📋 Overview
This repository contains two enterprise e-commerce datasets designed for sales performance analysis, shipping efficiency tracking, profitability auditing, and data cleaning pipeline development. The records span transactional details across multiple customer segments, regions, and product categories.

---

## 📁 Dataset Files

| Filename | Description | Shape | Primary Use Case |
| :--- | :--- | :--- | :--- |
| `ecommerce_cleaned_dataset.xls` | Fully processed dataset featuring imputed values, standardized dates, and derived delivery metrics. | 100,500 rows × 18 columns | Predictive modeling, dashboarding, and KPI reporting. |
| `ecommerce_dirty_dataset.csv` | Raw, uncleaned dataset containing natural missing values, unstandardized fields, and raw transaction logs. | 100,500 rows × 16 columns | Data cleaning pipelines, anomaly detection, and data wrangling exercises. |

---

## 📊 Data Dictionary / Schema

Both datasets share core transactional attributes, while the cleaned dataset includes additional engineered columns:

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Order_ID` | Integer | Unique identifier for each order transaction. |
| `Order_Date` | Date (YYYY-MM-DD) | Date when the order was placed (Range: 2021–2023). |
| `Ship_Date` | Date (YYYY-MM-DD) | Date when the order was shipped. |
| `Customer_ID` | Integer | Unique identifier for the customer. |
| `Customer_Segment` | String | Customer classification (e.g., Consumer, Corporate, Home Office). |
| `Region` | String | Geographic region of fulfillment (North, South, East, West). |
| `State` | String | State where the order was delivered (12 distinct states). |
| `Product_Category` | String | High-level category (e.g., Clothing, Electronics, Home). |
| `Sub_Category` | String | Detailed product sub-category (e.g., Mobile, Laptops). |
| `Product_Name` | String | Specific product name or SKU title. |
| `Sales` | Float | Total gross sales revenue ($). |
| `Quantity` | Integer | Number of units purchased per transaction (1–5). |
| `Discount` | Float | Applied discount rate (0.0 to 0.9). |
| `Profit` | Float | Net profit generated from the transaction. |
| `Shipping_Cost` | Float | Associated shipping expense ($). |
| `Payment_Mode` | String | Payment method used (e.g., Debit Card, Credit Card, UPI, Net Banking). |
| `Delivery_Time_Days` | Integer | *(Cleaned only)* Calculated shipping duration in days. |
| `Delivery_Status` | String | *(Cleaned only)* Delivery performance tier (e.g., Fast, Standard, Delayed). |

---

## 🛠️ Data Quality & Cleaning Summary

* **Missing Values:** The raw dataset contains null entries in `Customer_Segment`, `Profit`, and `Shipping_Cost`, which were imputed or handled in the cleaned release.
* **Metrics Summary:** 
  * Total Records: $100,500$ transactions per file.
  * Sales Range: $-\$5,000.00$ to $\$399,965.00$ (reflecting potential returns or adjustments).
  * Quantity Range: $1$ to $5$ units.

---

## 🚀 Quick Start (Python / Pandas)

To load and inspect the datasets in your local environment, run the following Python code:

```python
import pandas as pd

# Load cleaned dataset
df_clean = pd.read_excel('ecommerce_cleaned_dataset.xls')
print("Cleaned Dataset Shape:", df_clean.shape)
print(df_clean.head())

# Load dirty dataset
df_dirty = pd.read_csv('ecommerce_dirty_dataset.csv')
print("Dirty Dataset Shape:", df_dirty.shape)
print(df_dirty.info())
