# Airline-Project
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from ast import literal_eval 
data = pd.read_csv('/content/airline data analysis.csv')
print(data.head())
print(data.info())
print(data.isnull().sum())
df=data.fillna(method='ffill') #forward filling the null values
df.isnull().sum()
print("Mean:", np.mean(df.DepTime))
print("Median:", np.median(df.DepTime))
print("Standard Deviation:", np.std(df.DepTime))
print("Maximum Value:", np.max(df.DepTime))
print("Minimum Value:", np.min(df.DepTime))
mean = np.mean(df['DepTime']) # Calculate mean and standard deviation
std_dev = np.std(df['DepTime'])

df['Z_Score'] = (df['DepTime'] - mean) / std_dev # Finding Z-scores

outliers = df[np.abs(df['Z_Score']) > 2] # Identifying outliers

print("Dataset with Z-scores:\n", df)
print("\nOutliers detected:\n", outliers)
