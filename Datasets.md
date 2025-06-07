Got it — here's a curated list of **FRED (Federal Reserve Economic Data)** datasets you can use to explore what may be **driving retail sales up**, all from [https://fred.stlouisfed.org](https://fred.stlouisfed.org):

---

### 🛍️ **Core Retail Sales**

| Dataset                                  | Description                                | FRED Code     | Link                                                 |
| ---------------------------------------- | ------------------------------------------ | ------------- | ---------------------------------------------------- |
| **Retail Sales: Total (Monthly)**        | Headline measure of U.S. retail activity   | **RSAFS**     | [Link](https://fred.stlouisfed.org/series/RSAFS)     |
| **Retail Sales: Control Group**          | Retail sales excluding volatile components | **RSCCAS**    | [Link](https://fred.stlouisfed.org/series/RSCCAS)    |
| **E-Commerce Retail Sales (% of Total)** | Online retail share of all sales           | **ECOMPCTSA** | [Link](https://fred.stlouisfed.org/series/ECOMPCTSA) |

---

### 💳 **Consumer Financial Health**

| Dataset                        | Description                          | FRED Code   | Link                                               |
| ------------------------------ | ------------------------------------ | ----------- | -------------------------------------------------- |
| **Disposable Personal Income** | Total income available to households | **DSPIC96** | [Link](https://fred.stlouisfed.org/series/DSPIC96) |
| **Personal Saving Rate**       | % of disposable income saved         | **PSAVERT** | [Link](https://fred.stlouisfed.org/series/PSAVERT) |
| **Revolving Consumer Credit**  | Credit card borrowing levels         | **REVOLSL** | [Link](https://fred.stlouisfed.org/series/REVOLSL) |

---

### 🔮 **Consumer Sentiment / Expectations**

| Dataset                                        | Description                            | FRED Code     | Link                                                 |
| ---------------------------------------------- | -------------------------------------- | ------------- | ---------------------------------------------------- |
| **University of Michigan: Consumer Sentiment** | Consumer mood and expectations         | **UMCSENT**   | [Link](https://fred.stlouisfed.org/series/UMCSENT)   |
| **Consumer Expectations**                      | Forward-looking component of sentiment | **UMCSENTEX** | [Link](https://fred.stlouisfed.org/series/UMCSENTEX) |
| **Conference Board Consumer Confidence**       | Broader confidence index               | **CONCCONF**  | [Link](https://fred.stlouisfed.org/series/CONCCONF)  |

---

### 📈 **Labor Market (Spending Power Proxy)**

| Dataset                         | Description                   | FRED Code         | Link                                                     |
| ------------------------------- | ----------------------------- | ----------------- | -------------------------------------------------------- |
| **Total Nonfarm Payrolls**      | Job growth indicator          | **PAYEMS**        | [Link](https://fred.stlouisfed.org/series/PAYEMS)        |
| **Average Hourly Earnings**     | Wage growth across industries | **CES0500000003** | [Link](https://fred.stlouisfed.org/series/CES0500000003) |
| **Initial Unemployment Claims** | Employment stability (weekly) | **ICSA**          | [Link](https://fred.stlouisfed.org/series/ICSA)          |

---

### 🧾 **Spending Behavior**

| Dataset                                    | Description                                | FRED Code   | Link                                               |
| ------------------------------------------ | ------------------------------------------ | ----------- | -------------------------------------------------- |
| **Real Personal Consumption Expenditures** | Total inflation-adjusted consumer spending | **PCECC96** | [Link](https://fred.stlouisfed.org/series/PCECC96) |
| **Retail Sales per Capita**                | Retail activity adjusted for population    | **RRSFS**   | [Link](https://fred.stlouisfed.org/series/RRSFS)   |

---

Would you like a Python script that pulls and visualizes these from FRED using `fredapi` or `pandas_datareader`?
