# Customer Churn Dashboard (Excel)

An interactive Excel dashboard that answers one question for a subscription business: **who is leaving, and why?**

Built by [Basil Thomas](https://www.linkedin.com/in/basil-thomas-0408on28/), a Data Analyst working with SQL, Power BI and Excel.

**[⬇ Download the dashboard (.xlsx)](https://github.com/BasilThomas28/customer-churn-dashboard/raw/main/Customer_Churn_Dashboard.xlsx)**. Open it in desktop Excel to use the slicers.

## At a glance
| Customers | Lost | Kept | Churn rate | Avg spend | Avg tenure |
|---:|---:|---:|---:|---:|---:|
| 64,374 | 30,493 | 33,881 | 47.4% | 541 | 32.0 months |

## What's inside
| Sheet | Purpose |
|---|---|
| **Dashboard** | 6 KPI cards, 6 pivot charts and 4 slicers (Gender, Subscription Type, Contract Length, Age Group). Every chart and KPI updates together when you click a slicer. |
| **Insights** | 8 findings, each with the evidence and a recommended action. |
| **Pivots** | 7 pivot tables that feed the charts and KPIs (via `GETPIVOTDATA`). |
| **Clean_Data** | The cleaned dataset as an Excel table (`tblChurn`), 64,374 rows × 18 columns. |
| **Data_Quality** | Cleaning log, data dictionary and the band definitions used for grouping. |

## Key findings
| # | Finding | Evidence | Recommended action |
|---|---|---|---|
| 1 | **Late payment is the strongest churn signal** | 71% churn at 16+ days late vs 10% at 0–15 days (about 7×) | Reminders and a payment-plan offer before day 15 |
| 2 | **Churn jumps at the 5th support call** | 61% with 5+ calls vs 24% with 0–3 calls (4 calls: 32%) | Escalate to a senior agent at the 4th call |
| 3 | **Long-tenure customers churn more** | 56% after 24 months vs 32% in the first 24 | Loyalty or renewal offer around month 24 |
| 4 | **Very low usage predicts churn** | 64% at 1–5 uses vs 43% for everyone else | Re-engagement campaign for low users |
| 5 | Female customers churn more | 55% vs 39% for male customers | Research the cause before acting |
| 6 | Monthly contracts are slightly riskier | Monthly 52%, Annual 46%, Quarterly 44% | Incentives to move to longer terms |
| 7 | Lower spend and older age add a little risk | Spend ≤500: 52% vs 43%; age 46+: 51% vs 45% | Use to prioritise within the high-risk groups |
| 8 | Subscription tier barely matters | Basic 48%, Standard 47%, Premium 46% | Don't rely on tier upgrades for retention |

## How I built it
1. **Cleaned and validated** the raw CSV: checked for blanks, duplicates, duplicate IDs, invalid categories, out-of-range values and IQR outliers (none found, 0 rows removed), and renamed columns to show units.
2. **Added 6 derived columns** (Churn Status, Age Group, Tenure Band, Payment Delay Band, Spend Band, Usage Band) so the data can be grouped into readable bands.
3. **Built pivot tables** on the Excel table, with **pivot charts** and **slicers** connected to all 7 pivots so the whole page filters together.
4. **Linked the KPI cards** to the pivots with `GETPIVOTDATA`, so the cards follow the slicers.
5. **Wrote up the insights** with evidence and a business action for each one.

**Skills:** Excel · Power Query-style data cleaning · Pivot tables & pivot charts · Slicers · GETPIVOTDATA · Data storytelling

## How to use
1. Download `Customer_Churn_Dashboard.xlsx` and open it in **desktop Excel** (Windows or Mac). Slicers have limited support in Excel for the web.
2. On the **Dashboard** sheet, click a slicer button to filter. Hold **Ctrl** to select more than one; use the funnel icon to clear a filter.
3. If you edit `Clean_Data`, use **Data → Refresh All** to update the pivots.

## Data source & caveats
- **Data:** [Customer Churn Dataset](https://www.kaggle.com/datasets/muhammadshahidazeem/customer-churn-dataset) by Muhammad Shahid Azeem on Kaggle (file `customer_churn_dataset-testing-master.csv`, 64,374 rows), licensed under GPL-2.0 (full text in [`LICENSE-DATA.txt`](LICENSE-DATA.txt); the data in `Clean_Data` is shared under the same license). I verified that every original value is unchanged in `Clean_Data`. My only changes were renaming 3 column headers to show units and adding 6 derived band columns.
- The 47.4% churn rate is far above typical real-world rates, and the values are evenly spread, which suggests a synthetic or sampled dataset. Treat the findings as a demonstration of the analysis method.
- The results are associations, not proven causes; test any action on a pilot group first.
- Units aren't stated in the source: tenure is assumed to be months, payment delay and last interaction to be days, and spend has no currency.
