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

There are do not need handle missing values and remove duplicates.

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

