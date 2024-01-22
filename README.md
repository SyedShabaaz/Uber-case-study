# Uber-case-study
# Uber Case study for Python libraries Mock interview. 
# For the given cab pick up data set, can you find how many drivers didn't meet any other drivers at the airport? we consider two drivers met each other if they are at the airport at the same time i.e difference between two drivers "Request timestamp" is less than 5min.
import numpy as np
import pandas as pd
from datetime import datetime
df = pd.read_csv("Uber.csv")
df
mask = ~df['Request timestamp'].isna()
mask
df = df.loc[mask]
df
df = df[df['Pickup point']=='Airport']
df
df.dropna(axis = 0,how = "any",inplace=True)
df['Request timestamp'] = pd.to_datetime(df['Request timestamp'])
df['Request timestamp'].dt.time
df.sort_values(by=['Request timestamp'], inplace=True)
df
df['Request timestamp'].dt.time
isinstance(df,pd.DataFrame)
df['Request timestamp'] = pd.to_datetime(df['Request timestamp'])
df['time_diff'] = df['Request timestamp'].diff()
df
df[df['time_diff'] > pd.Timedelta(minutes=5)]
df[df['time_diff'] > pd.Timedelta(minutes=5)].shape[0]
