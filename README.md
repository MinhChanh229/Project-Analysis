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
<img width="445" height="510" alt="image" src="https://github.com/user-attachments/assets/b61e4ffa-1e7f-460a-8d46-08f06589e80e" />
```

