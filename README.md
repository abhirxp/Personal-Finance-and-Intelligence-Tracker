# Personal Finance and Expense Intelligence

A Python-based personal finance analytics workflow that cleans raw transaction logs, tracks monthly cash flow and savings rates, detects recurring commitments and spending anomalies, and generates a data-backed monthly budget plan.

Built as part of **Programming for Analytics (MBA Business Analytics, 1st Semester)**.

---

## Project Overview

With digital payments (UPI, Credit/Debit Cards, NetBanking) making daily transactions seamless, salaried professionals often lose visibility over recurring bills, category-level overspending, and one-off spikes. This project transforms a 12-month synthetic Indian personal finance ledger (Jan–Dec 2025) into actionable budgeting and savings intelligence.

### Key Capabilities
- **Data Cleaning Pipeline:** Removes exact duplicates, parses mixed date formats (`YYYY-MM-DD` and `DD/MM/YYYY`), filters invalid amounts (`<= 0`), standardizes merchant/category text, and imputes missing labels via merchant-level mode (`521 → 507` clean records).
- **Cash-Flow & Savings Tracking:** Computes monthly income, expenses, net savings, and savings rate (%).
- **Recurring Payment Detection:** Automatically identifies fixed and recurring monthly bills (Rent, Electricity, Gym, JioFiber, Netflix).
- **Budget vs. Actual Variance:** Compares historical monthly averages against a baseline budget to pinpoint overrun drivers.
- **Rule-Based Anomaly Detection:** Compares **Category-Level IQR** (`Q3 + 1.5 × IQR`) against a **30-Transaction Rolling Mean + 2 SD** baseline to justify why IQR handles right-skewed expense data better.
- **Discretionary Spend Sensitivity Check:** Simulates 10%, 15%, and 20% cuts on discretionary categories to project savings-rate gains.

---

## Key Findings (2025 Ledger)

| Metric | Value |
| :--- | :--- |
| **Annual Income** | ₹9,90,000 |
| **Annual Expense** | ₹6,86,762 |
| **Annual Net Savings** | ₹3,03,238 (**30.63%** savings rate) |
| **Monthly Recurring Commitments** | ₹23,724/month (~29.7% of ₹80,000 base salary) |
| **Monthly Budget Overrun** | +₹6,230/month (₹57,230 actual avg vs. ₹51,000 budget) |

- **Top 4 Categories = 78.3% of Spending:** Housing (31.45%), Shopping (19.51%), Groceries (15.39%), and Food & Dining (11.96%) dominate annual outflows.
- **Overruns Concentrated in 2 Buckets:** Shopping (+₹4,664/month) and Food & Dining (+₹1,345/month) account for nearly the entire monthly budget deficit.
- **Category IQR Outperforms Rolling Averages:** IQR cleanly flagged **5 genuine anomalies** (₹24,999 Amazon, ₹16,500 Flipkart, ₹9,500 Apollo Hospital, ₹6,200 Taj Restaurant, ₹5,800 Electricity spike), whereas the global rolling average falsely flagged **11 monthly rent transfers**.
- **Actionable Savings Lever:** Trimming Shopping, Food & Dining, and Entertainment by **15%** saves **₹35,142/year**, lifting the overall savings rate from **30.63% to 34.18%**.

---

## Repository Structure

```text
Personal-Finance-and-Intelligence-Tracker/
├── Project5_Personal_Finance_Intelligence-v2.ipynb   # Main analysis & visualization notebook
├── personal_finance_data-v2.csv                      # Synthetic 2025 Indian transaction dataset (521 raw rows)
└── README.md                                         # Project documentation
