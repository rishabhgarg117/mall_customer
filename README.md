import pandas as pd
import numpy as np 
import matplotlib.pyplot as plt 
import seaborn as sns
df = pd.read_csv('/content/drive/MyDrive/archive.zip')
df.head()
df.tail()
df.describe()
df.sample()
df.shape
df.info()
df.isna().sum()
df
df['Gender'].value_counts()
sns.barplot(x=df['Gender'].value_counts().index,y=df['Gender'].value_counts(),color='red',alpha=.3)
plt.show()
explode =[0,0.1]
plt.pie(df['Gender'].value_counts(),labels=df['Gender'].value_counts().index,autopct='%1.1f%%',colors=['gold','r'],explode=explode)
plt.show()
df
df['Age']
pd.crosstab(df['Age'],df['Gender'])
pd.crosstab(df['Age'],df['Gender']).plot(kind='bar')
pd.crosstab(df['Gender'],df['Annual Income (k$)'])
pd.crosstab(df['Annual Income (k$)'],df['Gender']).plot(kind='bar')
plt.show()
pd.crosstab(df['Age'],df['Annual Income (k$)'])
crosstab = pd.crosstab(df['Age'], df['Annual Income (k$)'])
total_income_by_age = crosstab.dot(crosstab.columns)
highest_income_age_group = total_income_by_age.idxmax()
highest_income_amount = total_income_by_age.max()
print(f"The age group with the highest total income is {highest_income_age_group} with a total income of {highest_income_amount}k$.")
crosstab = pd.crosstab(df['Age'], df['Spending Score (1-100)'])
total_spending_by_age = crosstab.sum(axis=1)
highest_spending_age_group = total_spending_by_age.idxmax()
highest_spending_amount = total_spending_by_age.max()
print(f"The age group with the highest total spending score is {highest_spending_age_group} with a total spending score of {highest_spending_amount}.")
df[df['Age']==32]['Gender'].value_counts()
plt.pie(df[df['Age']==32]['Gender'].value_counts(),labels=['Female','Male'],autopct='%1.1f%%')
plt.show()
pd.crosstab(df['Spending Score (1-100)'],df['Gender']).plot(kind='bar')
crosstab = pd.crosstab(df['Gender'],df['Annual Income (k$)'],values=df['Spending Score (1-100)'],aggfunc='count')
total_counts = crosstab.sum(axis=1)
print("Total counts by Gender:")
print(total_counts)
if total_counts['Male'] > total_counts['Female']:
    print("Males are the most frequent.")
else:
    print("Females are the most frequent.")
pd.crosstab([df['Age'],df['Annual Income (k$)']],df['Gender'])
pd.crosstab(df['Annual Income (k$)'],df['Spending Score (1-100)'])
sns.scatterplot(data=df,x='Spending Score (1-100)',y='Annual Income (k$)')
sns.scatterplot(data=df,x='Spending Score (1-100)',y='Annual Income (k$)',hue='Gender')
df.hist()
df.hist(figsize=(10,10))
df['CustomerID'].nunique()
sns.pairplot(df)
df
df['Annual Income (k$)'].describe()
df['Spending Score (1-100)'].describe()
