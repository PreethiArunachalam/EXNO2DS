# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("titanic_dataset.csv")
df
```
![Screenshot 2024-09-10 160546](https://github.com/user-attachments/assets/6af0c00e-9450-4385-a240-6ea0f436f8c6)

```
df.info()
```
![Screenshot 2024-09-10 160639](https://github.com/user-attachments/assets/c772d113-0809-4f52-b6ae-e3bdd80405b9)

```
df.shape
```
![Screenshot 2024-09-10 160712](https://github.com/user-attachments/assets/19172a3f-9c36-4bab-bb3c-21dde07a647c)

```
df.set_index("PassengerId",inplace=True)
df.describe()
```
![Screenshot 2024-09-10 160812](https://github.com/user-attachments/assets/af036684-96fa-47cc-9911-d475a291052e)

```
df.shape
```
![Screenshot 2024-09-10 160853](https://github.com/user-attachments/assets/a29dfd03-bb1a-47f1-8f06-7986dd780501)

## Categorical data analysis:
```
df.nunique()
```
![Screenshot 2024-09-10 160932](https://github.com/user-attachments/assets/e1403475-0ab9-468d-ae0a-3968099a1f49)

```
df["Survived"].value_counts()
```
![Screenshot 2024-09-10 161019](https://github.com/user-attachments/assets/67b9a2bf-678a-47d8-9c53-25026531556c)

```
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
```
![Screenshot 2024-09-10 161112](https://github.com/user-attachments/assets/26e2166c-fe2f-4cb4-99d8-2b5db062ccd2)

```
sns.countplot(data=df,x="Survived")
```
![Screenshot 2024-09-10 161156](https://github.com/user-attachments/assets/eb1aba9b-14ef-405d-95cc-23870a1637b5)

```
df.Pclass.unique()
```
![Screenshot 2024-09-10 161242](https://github.com/user-attachments/assets/1654be75-8202-42dd-aa4d-3fdaa4e88cdd)

## Bivariate Analysis:
```
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
```
![Screenshot 2024-09-10 161324](https://github.com/user-attachments/assets/e1751b00-8376-4f6a-9338-9bf22f4713a0)

```
 sns.catplot(x="Survived",hue="Gender",data=df,kind="count")
```
![Screenshot 2024-09-10 161406](https://github.com/user-attachments/assets/4808fad0-cfea-49cd-9756-318070f5be5e)

```
df.boxplot(column="Age",by="Survived")
```
![Screenshot 2024-09-10 161447](https://github.com/user-attachments/assets/87d813a8-0b9a-4c8d-baac-d10f4953df62)

```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```
![Screenshot 2024-09-10 161534](https://github.com/user-attachments/assets/3a2ed9c6-4618-4eb6-a571-16eae6b1c8be)

```
sns.jointplot(x="Age",y="Fare",data=df)
```
![Screenshot 2024-09-10 161614](https://github.com/user-attachments/assets/7c9b0969-565c-40e1-b255-b59a9571911b)

## Multivariate Analysis:

```
fig, ax1 = plt.subplots(figsize=(8,5))
plt = sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)
```
![Screenshot 2024-09-10 161700](https://github.com/user-attachments/assets/2b5a41d3-c867-4d4b-8d55-27fff77d5652)

```
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![Screenshot 2024-09-10 161747](https://github.com/user-attachments/assets/4e9bd19a-f1e8-4b4f-bd03-baf28f2f09b0)

## Co-relation:
```
numeric_df = df.select_dtypes(include=[np.number])
corr = numeric_df.corr()
sns.heatmap(corr, annot=True)
```
![Screenshot 2024-09-10 161824](https://github.com/user-attachments/assets/22b65fc3-d7bc-4631-a3f8-9c7375de373d)

```
sns.pairplot(df)
```
![Screenshot 2024-09-10 161926](https://github.com/user-attachments/assets/9806d8bb-e862-4325-a5cc-b044132558de)

# RESULT
         We have performed Exploratory Data Analysis on the given data set successfully.
