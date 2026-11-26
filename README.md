# 📊 Power BI Assignment 2 – Business Performance Dashboard

> A single-page Power BI dashboard that analyses **country-wise orders**, **order trends over time** and **layoff distribution**, built with charts, a calculated column and DAX measures.

## 🎯 Project Overview
This project is the second sectional assignment in Power BI. The goal is to load multiple Excel datasets, build the required visuals, create a calculated column, and write DAX measures. All of this is combined into one clean **Business Performance Dashboard** with the sections *Country Orders | Order Trends | Layoff Distribution*.

---

## 📝 Assignment Tasks
1. Load `Amazingcart.xlsx` and create a **Clustered Column chart** that explains the countries with the highest order placements.
2. Use `Customer_Data.xlsx` to create a **Line chart** showing the count of orders received per date.
3. From `Employee_Layoffs.xlsx`, create a **Pie chart** that best explains the locations with the highest number of layoffs.
4. Create a **Calculated Column** in the Customer Data table that multiplies quantity by price (replicating the existing *Total Price* column).
5. Create **DAX Measures** for: sum of a numerical column, total number of rows, number of valid records, total missing values, and the smallest and largest value of a column.

---

## 📂 Datasets Used
| File | Used For |
|---|---|
| `Amazingcart.xlsx` | Orders placed by country (Clustered Column chart) |
| `Customer_Data.xlsx` | Orders per date, calculated column, DAX measures |
| `Employee_Layoffs.xlsx` | Layoffs by location (Pie chart) |

---

## 🖼️ Dashboard Preview
![Business Performance Dashboard](dashboard.png)

The dashboard has two parts:
- **KPI cards (top row):** Total Sales, Total No.Of Rows, No.Of Valid Records, Total Missing Values, Smallest Quantity, Largest Quantity
- **Charts:** Order placed by countries, Count of Orders Received as per Date, Highest Number of Layoff

---

## 🛠️ Task-wise Solution

### 1️⃣ Order Placed by Countries – Clustered Column Chart
- **Data:** `Amazingcart.xlsx`
- **X-axis:** Country  |  **Y-axis:** Number of orders
- Sorted in descending order so the countries with the most orders appear first.
- **Result:** France, Germany and the United Kingdom have the highest order placements, followed by Italy and Spain. Orders drop sharply for countries such as Norway, Portugal, Finland and Denmark.

### 2️⃣ Count of Orders Received per Date – Line Chart
- **Data:** `Customer_Data.xlsx`
- **X-axis:** Date  |  **Y-axis:** Count of Order ID
- **Result:** The chart covers 2013 to 2016 and shows how daily order volume rises and falls, with a few clear peak days.

### 3️⃣ Highest Number of Layoffs – Pie Chart
- **Data:** `Employee_Layoffs.xlsx`
- A **Top N filter (Top 10 locations by total layoffs)** is applied, because showing every location makes the pie unreadable.
- **Result:** SF Bay Area has the largest share (123K layoffs, about 46% of the top 10), followed by Seattle (35K) and New York City (29K).

### 4️⃣ Calculated Column
Created in the `Customer Data` table to replicate **Total Price**:

```DAX
Calculated Total Price = 'Customer Data'[Quantity] * 'Customer Data'[Price Per Unit]
```

### 5️⃣ DAX Measures
See the next section.

---

## 🧮 DAX Measures & Results

```DAX
Total Sales = SUM('Customer Data'[Total Price])

Total No.Of Rows = COUNTROWS('Customer Data')

No.Of Valid Records = COUNT('Customer Data'[Order ID])

Total Missing Values = COUNTBLANK('Customer Data'[Total Price]) + 0

Smallest Quantity = MIN('Customer Data'[Quantity])

Largest Quantity = MAX('Customer Data'[Quantity])
```

| Measure | What it does | Result |
|---|---|---|
| **Total Sales** | Sum of the Total Price column | 725K |
| **Total No.Of Rows** | Counts all rows in the table | 699 |
| **No.Of Valid Records** | Counts non-empty Order ID values | 699 |
| **Total Missing Values** | Counts blank values in Total Price (`+ 0` makes it show 0 instead of blank) | 0 |
| **Smallest Quantity** | Minimum value in Quantity | 1 |
| **Largest Quantity** | Maximum value in Quantity | 6 |

> ✅ Total rows (699) equals valid records (699), which confirms there are no missing values in the data.

---

## 💡 Key Insights
- **France, Germany and the UK** account for the largest number of orders.
- Order activity over time is uneven, with sudden spikes on specific dates.
- **SF Bay Area** alone makes up almost half of the layoffs among the top 10 locations.
- The dataset is clean: all 699 records are valid and no values are missing.
- Each order contains between **1 and 6** units.

---

## 🧰 Tools Used
- **Power BI Desktop**
- **DAX** (calculated column and measures)
- **Microsoft Excel** (source data)

---

## 📁 Repository Structure
```
PowerBI-Assignment-2/
│
├── README.md
├── Power BI- Assignment 2.pbix
├── dashboard.png (Dashboard Preview Screenshots)
└── data/
    ├── Amazingcart.xlsx
    ├── Customer_Data.xlsx
    └── Employee_Layoffs.xlsx
```

---

