# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output

## df=pd.read_csv("SAMPLEIDS.csv")
![image](https://github.com/user-attachments/assets/3f6cdfbd-75d5-4f47-a548-13616b13d01b)

## df.isnull().sum()
![image](https://github.com/user-attachments/assets/d1987000-223b-4940-94d5-3e48527a1620)

## df.isnull().any()
![image](https://github.com/user-attachments/assets/ec4d19a1-3b10-420a-8b89-6cf4f98eb22f)

## df.dropna()
![image](https://github.com/user-attachments/assets/a49b3e0b-e013-4f4b-bf2f-3f89e92c0b9b)

## df.fillna(0)
![image](https://github.com/user-attachments/assets/8da1cc7e-3cf1-48ca-ac44-e11912362465)

## df.fillna(method = 'ffill')
![image](https://github.com/user-attachments/assets/0520b1a7-c8a1-4ab4-a9aa-69962f19e7d3)

## df.fillna(method = 'bfill')
![image](https://github.com/user-attachments/assets/6498cba7-4297-4bf4-b6ff-0e135fe05d05)

## df_dropped = df.dropna()
df_dropped
![image](https://github.com/user-attachments/assets/985c5c0a-6701-44ef-8082-3141e06d88fc)

## df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})

## ir=pd.read_csv('iris.csv')
ir
![image](https://github.com/user-attachments/assets/8f3df478-1347-4474-8be5-12aff7f53b91)

## ir.describe()
![image](https://github.com/user-attachments/assets/e113e335-0e08-40b5-bb25-8e02c9b52a5d)

## sns.boxplot(x='sepal_width',data=ir)
![image](https://github.com/user-attachments/assets/757fa210-1028-4c5a-b5b5-804eb74dbbfd)

## c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
![image](https://github.com/user-attachments/assets/2b841c4e-5375-48c7-a3d5-6d01b420ad40)

## rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
![image](https://github.com/user-attachments/assets/116db429-70a1-4471-af91-e6e903a16210)

## delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
![image](https://github.com/user-attachments/assets/dda4a158-581f-44b4-9ffb-7eba35ba1f73)

## sns.boxplot(x='sepal_width',data=delid)
![image](https://github.com/user-attachments/assets/7bd8b828-a0da-4f13-a837-d29423c563bd)

## import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset

![image](https://github.com/user-attachments/assets/2ea6c0d3-9d13-428c-933a-c898286b6d2b)

## df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr

![image](https://github.com/user-attachments/assets/2241e403-e0ed-4066-b975-fc6d5b4b7180)

## low = q1 - 1.5*iqr
low
![image](https://github.com/user-attachments/assets/7df271a7-9c5f-4099-8d05-3ef92fe57583)

## high = q3 + 1.5*iqr
high
![image](https://github.com/user-attachments/assets/a9382c0f-ded8-4457-9212-4c68755dfc39)

## df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
![image](https://github.com/user-attachments/assets/46b3aa58-81c0-450a-83fd-4f4058c71070)

## z = np.abs(stats.zscore(df['height']))
z
![image](https://github.com/user-attachments/assets/7e7461d7-3f3b-439f-bd18-e4aceca6c3fb)

## df1 = df[z<3]
df1
![image](https://github.com/user-attachments/assets/d4c9f9ea-b421-4bb1-ad7c-bb890dacecfd)


# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
