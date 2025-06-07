# Retail_Sales_Booster
Yes — that's a **great approach**. You can group your variables into **conceptual driver categories** (e.g., income, employment, credit, confidence, policy, prices), then create a **composite indicator for each**, and analyze how each **category-level index correlates or contributes to retail sales**.

---

### 🧩 Step 1: Group Your Drivers into Categories

| **Category**            | **Features (FRED Series)**                                                              |
| ----------------------- | --------------------------------------------------------------------------------------- |
| **Income & Wages**      | `DSPIC96` (Disposable Income), `CES0500000003` (Avg Hourly Earnings)                    |
| **Employment Health**   | `PAYEMS` (Payrolls), `ICSA` (Jobless Claims - inverse), `PCE` (Consumer Spend Proxy)    |
| **Credit Access**       | `REVOLSL` (Revolving Credit), `PSAVERT` (Savings Rate, inverse = willingness to spend)  |
| **Consumer Confidence** | `UMCSENT` (Sentiment Index)                                                             |
| **Monetary Policy**     | `FEDFUNDS` (Interest Rates)                                                             |
| **Prices / Real Power** | `CPIAUCSL_CH1` (Inflation), `RETAILIRSA` (Real Retail Sales), maybe used for adjustment |

---

### 🧠 Step 2: Create Composite Indicator for Each Category

Use **z-scores** to normalize the variables in each category and average them:

```python
from scipy.stats import zscore

# Apply to the full DataFrame
df_z = df.apply(zscore)

# Example: Income Index
df['Income_Index'] = df_z[['DSPIC96', 'CES0500000003']].mean(axis=1)

# Employment Health
df['Employment_Index'] = df_z[['PAYEMS', 'ICSA']].assign(ICSA=lambda x: -x['ICSA']).mean(axis=1)

# Credit Health
df['Credit_Index'] = df_z[['REVOLSL', 'PSAVERT']].assign(PSAVERT=lambda x: -x['PSAVERT']).mean(axis=1)

# Confidence
df['Confidence_Index'] = df_z['UMCSENT']

# Monetary Policy
df['Policy_Index'] = -df_z['FEDFUNDS']  # Higher rates reduce spending

# Optional: Real Power Index (you can adjust RSAFS by CPI)
df['Inflation_Index'] = -df_z['CPIAUCSL_CH1']
```

---

### 📊 Step 3: See Each Category’s Contribution to Sales

#### ✅ Correlation

```python
df[['RSAFS', 'Income_Index', 'Employment_Index', 'Credit_Index', 'Confidence_Index', 'Policy_Index']].corr()
```

#### ✅ Regression / Feature Importance

```python
from sklearn.ensemble import RandomForestRegressor
X = df[['Income_Index', 'Employment_Index', 'Credit_Index', 'Confidence_Index', 'Policy_Index']]
y = df['RSAFS']

model = RandomForestRegressor()
model.fit(X, y)

importances = pd.Series(model.feature_importances_, index=X.columns)
importances.sort_values(ascending=False).plot(kind='barh', title='Category Contribution to Retail Sales')
```

---

### ✅ Optional: Visualize Over Time

```python
df[['Income_Index', 'Employment_Index', 'Credit_Index', 'RSAFS']].plot(figsize=(12,6), title='Drivers vs Retail Sales')
```

---

### 🧪 Interpretation:

* A rising **Income Index** might suggest strong future sales.
* A dropping **Credit Index** could signal consumer caution.
* A tightening **Policy Index** (rising rates) may drag sales later.

---

Would you like me to generate a full Python notebook template to do this? Or would you like help generating these composite columns directly from your CSVs?
