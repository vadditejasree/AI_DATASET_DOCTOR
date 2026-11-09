# AI_DATASET_DOCTOR
# 🧑‍⚕️ AI Dataset Doctor

Diagnoses dataset quality *before* ML: missing values, duplicates, wrong dtypes, outliers (IQR/Z-score),
class imbalance, correlated & irrelevant features, PCA; prescribes fixes, applies them, retrains
(Logistic Regression / Random Forest / XGBoost), compares raw vs. treated, and explains with SHAP.

## Dataset
Kaggle – **Telco Customer Churn** (`blastchar/telco-customer-churn`)
https://www.kaggle.com/datasets/blastchar/telco-customer-churn
File: `WA_Fn-UseC_-Telco-Customer-Churn.csv`  (target column: `Churn`)

Planted issues the Doctor should find:
| Issue | Where |
|---|---|
| Number stored as text + blank values | `TotalCharges` |
| Class imbalance (~73/27) | `Churn` |
| Correlated features | `tenure`, `MonthlyCharges`, `TotalCharges` |
| ID column | `customerID` |

## Run
```bash
pip install -r requirements.txt
streamlit run app.py
```
Upload the CSV, choose `Churn` as target, and go through the four tabs.
Any other CSV with a target column works too.

## Files
- `doctor.py` – diagnose → recommend → treat → train/evaluate → SHAP
- `app.py` – Streamlit UI
