# ABA Transaction Analysis

Exploratory data analysis of ABA Bank payment notifications exported from Telegram. Parses raw chat messages into a structured dataset and produces revenue, customer, and payment insights.

## 📊 Dashboard Preview

![ABA Transaction Dashboard](sell_analysis.pdf)

## Dataset

| Metric | Value |
|---|---|
| Transactions | 5,509 |
| Total Revenue | $79,347.90 |
| Avg. per Transaction | $14.40 |
| Date Range | 2025-10-02 to 2026-06-16 |
| Unique Customers | 3,678 |
| Payment Methods | 48 |

## Files

| File | Description |
|---|---|
| `telegram_aba_data.json` | Raw Telegram chat export containing ABA payment notification messages |
| `aba_eda.ipynb` | Jupyter notebook — parsing, cleaning, and all analysis |
| `aba_transactions.csv` | Cleaned, structured output ready for Power BI or further analysis |

## Analysis Steps

1. **Parse** — regex extracts amount, customer name, payment method, and transaction ID from each notification message
2. **Dataset overview** — totals, date range, unique customers, payment method count
3. **Top customers by frequency** — who buys the most often (top 15)
4. **Top customers by spending** — who spends the most in total (top 15)
5. **Payment method breakdown** — ABA PAY vs KHQR by transaction count and revenue
6. **Daily revenue trend** — line chart over the full date range
7. **Hour & day-of-week patterns** — when transactions peak
8. **Amount distribution** — histogram of transaction sizes
9. **Monthly summary** — transactions, revenue, avg amount, and unique customers per month
10. **CSV export** — `aba_transactions.csv` for Power BI

## Quick Start

```bash
pip install pandas matplotlib jupyter
jupyter notebook aba_eda.ipynb
```

The notebook expects `telegram_aba_data.json` in the same directory. Run all cells in order; the final cell writes `aba_transactions.csv`.

## Data Source

Payment notifications follow this format in the Telegram export:

```
$14.00 paid by CUSTOMER NAME (*1234) on ... via ABA PAY at 3s by S.C. Trx. ID: 123456789
```

The regex in Step 1 of the notebook captures amount, name, payment method, and transaction ID from each message.
