# Project-Analysis
# Bank Customer Churn Analysis in Germany, France and Spain
## Source: 
Public dataset from Kaggle (https://www.kaggle.com/datasets/radheshyamkollipara/bank-customer-churn/data)

## Description: 
The dataset contains information about customers, including demographics, services subscribed, and account information.

## Structure: 
18 columns and 10.000 rows

## Initial Analysis Plan:

## Data Cleaning: 
Handle missing values, correct data types, and remove duplicates.
```code
# import pandas, matplotlip, seaborn
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

### 1. Extract data:
```code
# load data form csv
df = pd.read_csv('/content/Customer-Churn-Records.csv')
df.head()

# check random
df.sample(10)
```

### 2. Transform data:
```code
df.info()
```
<img width="445" height="510" alt="image" src="https://github.com/user-attachments/assets/9b15c03c-77d8-4984-ba27-7a0c0bd7c274" />

Fix data type:
   Correct data types
```code
df['Surname'] = df['Surname'].astype('string')
df['Geography'] = df['Geography'].astype('string')
df['Gender'] = df['Gender'].astype('string')
df['Card Type'] = df['Card Type'].astype('string')

df.info()
```
<img width="464" height="526" alt="image" src="https://github.com/user-attachments/assets/2ef9547e-0661-4664-9b07-f67acc8bc279" />

 Check missing values:
 ```code
print(df.isnull().sum())
```
<img width="235" height="387" alt="image" src="https://github.com/user-attachments/assets/77eca3f3-a872-4072-8329-95a64f8a8e91" />


Basic descriptive statistics:
   Show a descriptive statistics of the numeric columns
```code
df.describe()
```
<img width="1758" height="342" alt="image" src="https://github.com/user-attachments/assets/1408cfa4-c8f6-4459-a862-cfff18b224c2" />
 
   General Dataset Overview

Number of Observations: 10,000 rows.

Exited (Churn Rate):
  
  Mean = 0.2038 → Around 20.4% churn rate.

This is a moderate churn rate in banking datasets.

   Variable-by-Variable Insights
| Variable              | Observation Summary                                                 |
| --------------------- | ------------------------------------------------------------------- |
| **CreditScore**       | Mean: 650.5. Range: 350–850. Wide spread. Some very low scores.     |
| **Age**               | Mean: 38.9 years old. 75% of customers are below 44 years old.      |
| **Tenure**            | Mean: 5 years. Range: 0–10 years. Distribution looks balanced.      |
| **Balance**           | Mean: \~76,465. Around 25% of customers have zero balance.          |
| **NumOfProducts**     | Mean: 1.53. Median: 1 product. Most have 1–2 products.              |
| **HasCrCard**         | Mean: 0.705 → 70.5% have a credit card.                             |
| **IsActiveMember**    | Mean: 0.515 → \~51.5% are active members.                           |
| **EstimatedSalary**   | Mean: \~100,090. Broad range: 11–199,992.                           |
| **Complain**          | Mean: 0.204 → \~20.4% have made a complaint.                        |
| **SatisfactionScore** | Median: 3. Distribution looks roughly uniform (min 1, max 5).       |
| **Point Earned**      | Median: 605 points. Max: 1,000 points. Skewed toward higher values. |

   Business Implications

      Age & Balance:

Older customers tend to have higher balances.

Churn prevention may focus on customers with higher balances.

      Credit Card & Product Count:

70%+ of customers own a credit card, which is normal.

Most customers use 1–2 products → Potential for cross-selling opportunities.

      Complaints & Churn:

20% complaint rate aligns with the churn rate, suggesting possible correlation.

#### Boxplots to compare distributions by churn
```code
for col in ['Age', 'Balance', 'EstimatedSalary', 'CreditScore']:
    plt.figure(figsize=(6, 4))
    sns.boxplot(x='Exited', y=col, data=df)
    plt.title(f'{col} vs. Exited')
    plt.show()
```
<img width="603" height="446" alt="image" src="https://github.com/user-attachments/assets/a95b8ec9-d5b3-48a0-a573-e7947303c9f5" />
<img width="643" height="440" alt="image" src="https://github.com/user-attachments/assets/afc4c514-c841-4a57-8293-ab660c33609b" />
<img width="652" height="448" alt="image" src="https://github.com/user-attachments/assets/5c8a0efe-9cc3-48f2-95b6-6efd97aab88a" />
<img width="620" height="436" alt="image" src="https://github.com/user-attachments/assets/ebf16381-80c2-4bab-aca2-ecb61db9e944" />

```code
sns.violinplot(x='Exited', y='Balance', data=df)
plt.title('Balance vs Churn')
plt.xlabel('Exited')
plt.ylabel('Balance')
plt.show()
```
<img width="674" height="518" alt="image" src="https://github.com/user-attachments/assets/9c31b5d8-27dd-45f7-88cf-1fc50d4a2a2f" />

### 3.Load data:
```code
df.to_csv("bank_customer_churn_cleaned.csv", index=False)
print("✅ ETL pipeline hoàn tất!")
```
