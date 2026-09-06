# Task 1: Basic Sales Data Analysis

**KOUAME Koffi Fidèle** · Data Analysis Internship · koffifidelek59@gmail.com

---

## What is in this submission

```
KOUAME_Koffi_Fidèle/
├── Task1_Sales_Analysis.ipynb     Main analysis, executed with all outputs
├── README.md                      This file
├── INSIGHTS.md                    The five insights, standalone
├── report.pdf                     Full report with methodology and findings
├── data/
│   ├── superstore_sales.csv       Original dataset (51,290 rows)
│   └── superstore_clean.csv       Cleaned dataset produced by the notebook
├── charts/                        Five charts as PNG
└── results/                       Analysis tables as CSV and one Excel workbook
```

---

## Dataset

| Item | Detail |
| :--- | :--- |
| Name | Superstore Sales Dataset, 2011 to 2015 |
| Source | Kaggle: https://www.kaggle.com/datasets/vivek468/superstore-dataset-final |
| Rows | 51,290 |
| Fields used | Order Date, Product Name, Category, Region, Quantity, Sales, Profit |

---

## Tools

Python 3, pandas, NumPy, Matplotlib, Seaborn, openpyxl. Jupyter Notebook.

---

## 1. Data Cleaning

Five steps were followed in a deliberate order: diagnose, fix data types, remove duplicates, remove invalid values, and inspect outliers.

**Two defects were found that default settings would have hidden.**

**The Order Date column holds two different formats.** 31,223 rows use `d-m-Y` with dashes and 20,067 use `d/m/Y` with slashes. A single `pd.to_datetime` call parses one format and returns `NaT` for the other. Those rows then disappear at the validity filter. On this file, that discards **60% of the data with no error message**. The notebook parses both formats explicitly and asserts that zero dates remain unparsed.

**Duplicate detection must use the full record.** Two genuinely different orders become identical once Order ID, Customer and City are dropped: same product, same day, same region, same amount. The reduced table shows 2,347 apparent duplicates; the full 24-column record shows **zero**. Deduplicating the reduced table would have deleted 2,347 real orders and understated revenue.

**One decision stated explicitly: negative profit is kept.** 12,544 orders lose money. That is not a data error; it is the most interesting finding in the dataset. Removing it as an outlier would inflate total profit and hide the problem.

---

## 2. Analysis: The Six Answers

| Question | Answer |
| :--- | :--- |
| Total sales | **12,642,502** |
| Total profit | **1,467,457** (margin 11.61%) |
| Top category by sales | **Technology**, 38.4% of total |
| Best-selling product | **Staples** by units sold |
| Top region by sales | **Central**, 22% of total |
| Best month by sales | **December** |

**Orders analysed:** 51,290. **Distinct products:** 3,788.

---

## 3. Charts

| Chart | Type | Why this type |
| :--- | :--- | :--- |
| 1. Sales by category | Horizontal bar | Nominal categories with long labels, no rotation needed |
| 2. Sales over time | Line + moving average | Continuous time axis; the question is trend, not comparison |
| 3. Sales by calendar month | Vertical bar | Ordered categories; answers "which month" as the time series cannot |
| 4. Top 10 products | Horizontal bar | Long product names; only the top 10, since 3,788 bars answer nothing |
| 5. Sales and margin by region | Paired vertical bars | Sales answers the question asked; margin answers the one a manager asks next |

---

## 4. Insights

See `INSIGHTS.md` for the full text. In short:

1. Technology leads on revenue, but **Furniture** has the weakest margin at 6.9%.
2. **Nearly one order in four loses money**, 24.5% of all orders.
3. Sales are strongly seasonal: December sells about **2.5 times** February.
4. **Central** leads on sales, but **Southeast Asia** converts at only 2.0% margin.
5. Revenue is concentrated: 3,788 products, but a small minority carries most of it.

---

## How to Reproduce

```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
jupyter notebook Task1_Sales_Analysis.ipynb
```

Run all cells. The notebook loads `data/superstore_sales.csv` if present and falls back to a public mirror otherwise, so it runs without a Kaggle token.

---

## Repository

GitHub: [koffifidelek59-collab/sales-analysis-task1](https://github.com/koffifidelek59-collab/sales-analysis-task1)
