# 💳 Personal Finance Dashboard

A Streamlit app that turns a bank-statement CSV into a categorised spending dashboard. Upload your transactions, teach it your categories once, and it auto-labels every future statement.

## ✨ What it does
- **Upload a bank statement** (CSV) and see debits and credits in separate tabs
- **Auto-categorise transactions** with keyword rules, such as "ETIHAD AIRWAYS" → Travel
- **Create your own categories** and reassign transactions in an editable table. Your rules are saved to `categories.json`, so the app remembers them next time
- **Expense summary** with an interactive Plotly pie chart by category
- **Payment summary** showing total credits received

## 🛠️ Tech stack
| Tool | Why |
|---|---|
| Streamlit | Fast interactive UI with file upload, tabs and an editable data grid |
| pandas | Cleaning amounts (`"18,551.62"` → `18551.62`), parsing dates, grouping by category |
| Plotly Express | Interactive charts |
| JSON | Lightweight persistence for user-defined category rules |

## 🧠 How it works
1. `load_transactions()` reads the CSV, strips column names, converts amounts to numbers and parses dates
2. `categorize_transactions()` matches each transaction's description against the saved keyword list for every category
3. When you move a transaction to a category in the table, its description is saved as a new keyword. This is a simple rule-based "learning" loop.

## 🚀 Run locally
```bash
pip install streamlit pandas plotly
streamlit run main.py
```
Then upload `sample_bank_statement.csv` to try it. The sample data is synthetic.

## 📁 Files
```
main.py                     # Streamlit app
categories.json             # saved category → keyword rules
sample_bank_statement.csv   # synthetic sample statement
```

## 🔮 Next improvements
- Use an LLM to suggest categories for unknown transactions instead of exact keyword match
- Monthly trend charts and budget alerts
- Support multiple bank formats and currencies

---
👩‍💻 **Nidhi Mehta** · [GitHub](https://github.com/itsnidhimehta)
