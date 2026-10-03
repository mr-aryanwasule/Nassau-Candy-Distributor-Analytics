# 🍬 Nassau Candy Distributor Analytics

## 📊 Sales, Profitability & Distribution Analysis

This project analyzes the **Nassau Candy Distributor dataset** and presents the results through a **single-page interactive Power BI dashboard**.

The dashboard focuses on key business areas including **sales, gross profit, profitability, products, regions, divisions, shipping, and monthly performance**.

---

## 🎯 Project Objective

The objective of this project is to analyze distribution data and create a simple, interactive dashboard that helps users understand overall business performance.

The analysis focuses on:

* Sales performance
* Gross profit
* Profitability
* Product performance
* Regional performance
* Division performance
* Shipping performance
* Monthly profit trends

---

## ❓ Business Questions

The dashboard was created to answer these key business questions:

1. Which are the **Top 10 profit-generating products**?
2. Which **division** generates the highest sales and profit?
3. Which **region** contributes the highest sales?
4. Which **shipping mode** handles the highest number of orders?
5. Which **months** have the highest and lowest gross profit?
6. How efficiently are orders being shipped based on **average shipping days**?
7. Is higher sales consistently associated with higher gross profit across divisions?
8. Which combination of **region, division, product, and shipping mode** should management focus on to improve profitability and operational efficiency?

---

## 📈 Key Performance Indicators

The single-page dashboard includes important KPIs such as:

* **Total Sales**
* **Total Gross Profit**
* **Gross Profit Margin**
* **Total Orders**
* **Average Shipping Days**

These KPIs provide a quick overview of overall business performance.

---

## 🛠️ Tools & Technologies

| Tool        | Purpose                                   |
| ----------- | ----------------------------------------- |
| 🐍 Python   | Data analysis and data preparation        |
| 🗄️ SQL     | Business data analysis                    |
| 📊 Excel    | Data inspection and preparation           |
| 📈 Power BI | Interactive dashboard                     |
| 🧮 DAX      | KPI and calculated measures               |
| 🐙 GitHub   | Project documentation and version control |

---

## 🔄 Project Workflow

```text
Raw Dataset
     ↓
Data Cleaning
     ↓
Data Preparation
     ↓
Data Analysis
     ↓
KPI Creation
     ↓
Power BI Visualization
     ↓
Single-Page Dashboard
     ↓
Business Insights
```

---

## 🧹 Data Preparation

The dataset was prepared before creating the dashboard.

The preparation process included:

* Checking data quality
* Handling missing values where required
* Checking duplicate records
* Validating data types
* Standardizing data
* Preparing calculated fields
* Creating required measures
* Preparing the dataset for Power BI

---

# 📊 Power BI Dashboard

The project contains **one newly created single-slide Power BI dashboard**.

The dashboard provides a consolidated view of important business metrics and allows users to analyze different aspects of the distribution business from one page.

### Dashboard includes:

* KPI Cards
* Top 10 Product Analysis
* Regional Analysis
* Division Analysis
* Shipping Mode Analysis
* Monthly Profit Analysis
* Interactive Filters/Slicers
* Business Performance Metrics

---

## 📌 Dashboard Analysis

### 💰 Sales & Profitability

The dashboard provides an overview of total sales, gross profit, and profit margin.

This helps users understand the overall financial performance of the business.

### 🍫 Product Performance

The **Top 10 Products** analysis identifies products that contribute significantly to profitability.

### 🌎 Regional Performance

Regional analysis helps identify which regions contribute more to overall sales.

### 🏭 Division Performance

Division-level analysis allows comparison of sales and profitability across different business divisions.

### 🚚 Shipping Performance

Shipping analysis provides information about order distribution across different shipping modes and average shipping time.

### 📅 Monthly Performance

The monthly profit analysis helps identify periods with higher and lower profitability.

---

# 🧮 DAX & Calculated Measures

Power BI DAX was used to create business metrics and KPIs.

Example:

```DAX
Total Sales =
SUM('Nassau Candy Distributor'[Sales])
```

```DAX
Total Gross Profit =
SUM('Nassau Candy Distributor'[Gross Profit])
```

```DAX
Profit Margin =
DIVIDE(
    [Total Gross Profit],
    [Total Sales],
    0
)
```

> The exact DAX formulas may vary depending on the final Power BI data model and column names.

---

# 💡 Business Value

The dashboard can help users:

* Identify profitable products
* Compare divisions
* Understand regional sales
* Monitor shipping performance
* Track monthly profitability
* Monitor important business KPIs
* Support data-driven decision making

---

# 📷 Dashboard Preview

The project contains a **single-page dashboard**.

Add the dashboard screenshot to the repository and display it using:

```markdown
![Nassau Candy Distributor Dashboard](Dashboard_Screenshot.png)
```

If your screenshot is inside another folder, update the path accordingly.

---

# 📁 Project Structure

```text
Nassau-Candy-Distributor-Analytics/
│
├── Nassau_Candy_Distributor.csv
├── Nassau_Candy_Distribution_Dashboard.pbix
├── Dashboard_Screenshot.png
└── README.md
```

> Adjust the filenames if your actual GitHub repository uses different names.

---

# 🎓 Skills Demonstrated

This project demonstrates practical experience with:

* Data Analytics
* Data Cleaning
* Data Preparation
* Exploratory Data Analysis
* Business Analysis
* Python
* SQL
* Excel
* Power BI
* DAX
* Data Visualization
* Dashboard Development
* KPI Development
* Business Intelligence

---

# 🚀 Future Improvements

Possible future improvements include:

* Sales forecasting
* Profit forecasting
* Demand prediction
* Customer segmentation
* Advanced Power BI analytics
* What-if analysis
* Automated data refresh
* Machine learning-based prediction
* Shipping cost optimization

---

# 🏆 Project Outcome

The project converts the Nassau Candy distribution dataset into a **single-page interactive Power BI dashboard**.

The dashboard provides a consolidated view of:

**Sales → Profit → Products → Regions → Divisions → Shipping → Monthly Performance**

This project demonstrates an end-to-end data analytics workflow from raw data to business intelligence dashboard.

---

# 👨‍💻 Author

## Aryan Wasule

**Computer Engineering Student | Data Analytics Enthusiast**

NIT Polytechnic, Nagpur

### Technical Skills

`Python` `SQL` `Excel` `Power BI` `DAX` `Data Analytics`

---

## 🔗 Connect With Me

**GitHub:** https://github.com/mr-aryanwasule

**LinkedIn:** [www.linkedin.com/in/aryanwasule-data](http://www.linkedin.com/in/aryanwasule-data)

---

## ⭐ Project

If you find this project useful, consider giving the repository a **⭐ Star**.
