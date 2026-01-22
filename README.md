import pandas as pd
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split, GridSearchCV
from sklearn.preprocessing import OneHotEncoder, StandardScaler
from sklearn.ensemble import RandomForestRegressor
from  sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_squared_error
import numpy as np file_path = "insurance_data.xlsx"
df = pd.read_excel(file_path)
df.shape[0]
list(df.columns)
df.isnull().sum().to_dict()
int(df.isnull().sum().sum())
df.dtypes.astype(str).to_dict()
df.head()
df['gender'] = df['gender'].fillna(df['gender'].mode()[0])
df['bmi'] = df['bmi'].fillna(df['bmi'].median())
df['children'] = df['children'].fillna(df['children'].median())
df['charges'] = df['charges'].fillna(df['charges'].median())
int(df.isnull().sum().sum
df['children'] = df['children'].astype(int)
df['NoClaimsBonus'] = df['NoClaimsBonus'].astype(int)
plt.figure()
plt.hist(df['charges'], bins=30)
plt.title("Distribution of Medical Insurance Charges")
plt.xlabel("Charges")
plt.ylabel("Frequency")
plt.show()
df['bmi_category'] = pd.cut(
    df['bmi'],
    bins=[0, 18.5, 25, 30, float("inf")],
    labels=['underweight', 'normal', 'overweight', 'obese'],
    right=False
)
df['smoker_flag'] = (df['smoker'].str.lower() == 'yes').astype(int)
df['age_smoker_interaction'] = df['age'] * df['smoker_flag']
df.head()
df['NoClaimsBonus_tier'] = df['NoClaimsBonus'].astype(str) + "%"
df.head()
