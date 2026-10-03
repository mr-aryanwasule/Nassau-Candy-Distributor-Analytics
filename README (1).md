# 🍬 Nassau Candy Distributor Analytics

End-to-end analytics on 10,194 order lines (8,549 orders) from a US/Canada candy distributor: data cleaning, feature engineering, EDA, a leakage-aware modelling check, and an interactive Power BI dashboard.

## 📷 Dashboard

![Nassau Candy Distributor Dashboard](Dashboard_Screenshot.png)

Slicers for Division, Region, and Year drive every visual. Individual visuals are in [`screenshots/`](screenshots/). Open `Nassau_Candy_distribution Dashboard.pbix` in Power BI Desktop for the interactive version.

## 🎯 Business questions and answers

| Question | Answer (verified in Python) |
| --- | --- |
| Total sales / gross profit / margin? | **$141,784** sales, **$93,443** gross profit, **65.9%** margin |
| Which division leads? | **Chocolate**: 92.9% of sales and 95.1% of gross profit (67.4% margin) |
| Top products by profit? | Five Wonka Bars (Scrumdiddlyumptious, Triple Dazzle Caramel, Milk Chocolate, Nutty Crunch Surprise, Fudge Mallows), **$16.6K to $19.4K profit each** |
| Which region sells most? | **Pacific** ($46.3K, 32.7%), then Atlantic ($41.2K), Interior ($32.0K), Gulf ($22.2K) |
| Does region or ship mode change margin? | No. Margins sit between 65.5% and 66.4% across all regions and ship modes |
| Most-used ship mode? | **Standard Class**: 60.15% of orders (Second 19.34%, First 15.35%, Same Day 5.17%) |
| Best / worst month? | Highest profit Dec 2025 ($8,116); lowest Feb 2024 ($909) |
| Growth? | 2025 vs 2024: sales **+44.6%**, profit **+44.9%**, orders **+45.5%** |
| Seasonality? | Strong. Averaged over both years, Nov (~$10.3K) and Dec (~$10.6K) sales are roughly 4x the Jan (~$2.8K) and Feb (~$2.0K) levels |
| Where to focus? | See the product watch-list below |

### Product watch-list
- **Kazookles**: $1,206 in sales but only **7.7% margin** ($93 profit), the weakest product.
- **Lickable Wallpaper** (Other division): $7,860 in sales at 50% margin, well below the chocolate bars (65–71%).
- The "Other" division as a whole earns 44.8% margin vs 67.4% for Chocolate.
- Sugar division is negligible ($427 in sales, 40 lines).

## 🛠️ Known dashboard issues

- **"Sum of Profit Margin" (678.03K) is not a valid KPI.** It adds up each row's margin percentage. The correct measure is `DIVIDE([Total Gross Profit], [Total Sales])`, which gives **65.9%**.
- **"Avg Ship Days" (1.32K)** reflects the corrupted ship dates described below, not real shipping speed.
- "Total Orders" shows 9K because of rounding; the exact value is 8,549.
- The "Top 10 Profit Generators" title has a duplicated word and the visual scrolls past 8 bars.

## 📌 KPIs

| KPI | Value |
| --- | ---: |
| Total Sales | $141,783.63 |
| Total Gross Profit | $93,442.80 |
| Gross Profit Margin | 65.9% |
| Total Orders (unique) | 8,549 |
| Order Lines | 10,194 |
| Unique Customers | 5,044 |
| Average Profit per Line | $9.17 |

## ⚠️ Data quality findings

1. **Ship dates are not usable.** The dashboard's "Avg Ship Days" card shows 1.32K days for this reason. Ship Date falls **904 to 1,642 days (mean about 1,321) after** Order Date, with ship dates running to June 2030. Order IDs carry years 2021–2024 while order dates are 2024–2025, so the dates appear to have been altered during preparation. As a result, **"Average Shipping Days" is not meaningful**, and the `Shipping Efficiency` feature labels every row "Slow". Re-check this KPI in the dashboard and do not draw shipping-speed conclusions until source dates are fixed.
2. **No missing values or duplicates** in the 18 raw columns. Sales, cost, and profit have no negative values.
3. **Margins are unusually high (65.9%)** for a distributor, so treat profit levels as dataset-specific.
4. **Dataset is small and short:** 24 months (Jan 2024 – Dec 2025), so seasonality is based on two cycles only.

## 🤖 Machine learning: what the results really show

| Notebook | Result | Verdict |
| --- | --- | --- |
| 5. Machine Learning Models | Sales R² = 1.0; "High Demand" accuracy = 100% | **Data leakage.** `Revenue Check` = Cost + Gross Profit = Sales, and "High Demand" is just `Sales > mean`. Not real skill. |
| 6. Professional ML Pipeline | Removes leaking columns (correct approach); saved output stops before final metrics | Re-run to complete. See the script below for reproducible results. |

`ml_leakage_free_check.py` reproduces the leak-free results:

| Task | Model | Test R² | 5-fold CV R² |
| --- | --- | ---: | ---: |
| Predict Sales (no leaking columns) | Linear Regression | 0.927 | 0.884 |
| Predict Sales (no leaking columns) | Random Forest | 0.998 | 0.993 |
| Predict Units (order quantity) | Mean baseline | 0.000 | 0.000 |
| Predict Units (order quantity) | Random Forest | -0.004 | -0.005 |

How to read this:
- **Sales is an exact identity: Sales = unit price × Units.** A simple price lookup by product reaches R² = 1.0 with zero error, so a Sales model only relearns multiplication. It is not a useful forecasting task.
- **Order quantity is not predictable** from product, region, ship mode, state, or date. Models score no better than guessing the average, which means demand here looks random at the line level.
- Useful modelling would need richer drivers (promotions, prices over time, customer history) or aggregated forecasting (monthly sales), where the clear seasonal pattern above is the signal.

## 📁 Repository contents

| File | Description |
| --- | --- |
| `Nassau_Candy_Distributor.csv` | Raw data |
| `cleaned_nassau_candy.csv`, `feature_engineered_nassau_candy.csv` | Cleaned and feature-engineered data |
| `1.` – `6.` `*.ipynb` | Pipeline notebooks: load, clean, features, EDA, ML, ML pipeline |
| `ml_leakage_free_check.py` | Reproducible leak-free modelling check |
| `eda_summary.csv`, `dataset_summary.csv` | Summary outputs |
| `Nassau_Candy_distribution Dashboard.pbix` | Power BI dashboard |
| `Dashboard_Screenshot.png` | All dashboard visuals merged into one image |
| `screenshots/` | The five individual dashboard screenshots |
| `merge_screenshots.py` | Rebuilds `Dashboard_Screenshot.png` from `screenshots/` |
| `requirements.txt` | Python dependencies |

## ▶️ How to run

```bash
pip install -r requirements.txt
jupyter notebook          # run notebooks 1 to 6 in order from the repo root
python ml_leakage_free_check.py
```

All file paths are relative to the repo root.

## 🧮 DAX measures

```
Total Sales = SUM('Nassau Candy Distributor'[Sales])
Total Gross Profit = SUM('Nassau Candy Distributor'[Gross Profit])
Profit Margin = DIVIDE([Total Gross Profit], [Total Sales], 0)
Total Orders = DISTINCTCOUNT('Nassau Candy Distributor'[Order ID])
```

## 🚀 Next steps

- Replace the Profit Margin card with the DIVIDE measure and fix or remove the shipping card
- Fix or re-source the Ship Date column, then restore the shipping KPI
- Add a monthly sales forecast that uses the seasonal pattern
- Re-run notebook 6 and save its metrics
- Review margin on Kazookles and Lickable Wallpaper

## 👤 Author

**Aryan Wasule** — Computer Engineering student, NIT Polytechnic, Nagpur
[GitHub](https://github.com/mr-aryanwasule) · [LinkedIn](https://www.linkedin.com/in/aryanwasule-data)

Licensed under the MIT License.
