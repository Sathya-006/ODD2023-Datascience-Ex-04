# ODD2023-Datascience-Ex-04
# AIM
    To perform Multivariate EDA on the given data set.

# Explanation:
    Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

# ALGORITHM:
STEP 1
Import the built libraries required to perform EDA and outlier removal.

STEP 2
Read the given csv file

STEP 3
Convert the file into a dataframe and get information of the data.

STEP 4
Return the objects containing counts of unique values using (value_counts()).

STEP 5
Plot the counts in the form of Histogram or Bar Graph.

STEP 6
Use seaborn the bar graph comparison of data can be viewed.

STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

STEP 8
Save the final data set into the file

# PROGRAM
~~~
import pandas as pd
from scipy import stats
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
~~~
~~~
from google.colab import files
uploaded = files.upload()
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/6c54503c-9e17-4a1b-ac1c-6a7b0067c2fb)
~~~
df = pd.read_csv('diabetes.csv')
df
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/ec663a32-48a9-4aa0-92a7-c6e340912087)
~~~
df.isnull().sum()
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/1c7951b3-8e19-4174-9f45-33667a429f15)
~~~
q1 = df.quantile(0.25)
q3 = df.quantile(0.75)
iqr = q3 - q1
iqr
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/2d5c1c61-4833-4d9a-a387-6e7617cf9928)
~~~
sns.boxplot(df)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/47165dc0-a8ea-430a-ab98-8d16a2d9aa5f)
~~~
plt.figure(figsize = (14,6))
sns.scatterplot(x = 'Glucose',y='BloodPressure',data = df)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/9ad1f5b9-8c8e-469a-aa3c-1d7ceefc5e89)
~~~
sns.scatterplot(x = 'Glucose',y='Insulin',data = df)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/c65095b1-30b6-4beb-835b-9fe4c546ed22)
~~~
sns.scatterplot(x = 'Glucose',y='DiabetesPedigreeFunction',data = df)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/c9944b23-a21d-4620-9d28-bb4983e01db1)
~~~
sns.scatterplot(x = 'Glucose',y='Age',data = df)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/c5688ceb-20e4-4156-8163-c53427e60eda)
~~~
sns.heatmap(df.corr(),annot = True)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/e7590298-1a79-4b28-a51d-8b8d590cf535)
~~~
from google.colab import files
uploaded = files.upload()
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/c68f5fa3-25d9-401d-a7b1-8a853254d6f4)
~~~
df = pd.read_csv('employeesal.csv')
df
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/b3f9b2c8-f22d-40a5-ac92-11380c8d8779)
~~~
df.isnull().sum()
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/1d9e3e9d-91d5-4261-a4e2-92d668692482)
~~~
numeric_cols = df.select_dtypes(include=[int, float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/45b3a5b4-5cfb-452a-8c88-743b3722bc46)
~~~
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
numeric_cols.dropna()
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/4d7462b7-c5fd-47a3-abf2-6841ad3d9f39)
~~~
sns.boxplot(numeric_cols)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/29360bf9-f0fc-4a73-a8e7-accec0622fe2)
~~~
sns.scatterplot(x = 'Salary',y='Age',data = numeric_cols)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/68252d20-5439-4714-b4f9-cf9ac8275452)
~~~
sns.scatterplot(x = 'Experience_Years',y='Salary',data = numeric_cols)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/32e70c12-5e2b-4fa7-9ad2-4d33f96654d4)
~~~
sns.scatterplot(x = 'Experience_Years',y='Age',data = numeric_cols)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/c2781fbb-e7e4-4e45-bc68-ca5e9f75993e)
~~~
sns.heatmap(numeric_cols.corr(),annot = True)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/54e8b103-5db7-49a0-aeb8-07019664e15b)
~~~
from google.colab import files
uploaded = files.upload()
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/10f9ae4c-56ec-4802-a399-8fa2918ac5e2)
~~~
df = pd.read_csv('SuperStore.csv')
df
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/1b69182d-d5e0-44ab-9e1c-54514dda99f7)
~~~
df.isnull().sum()
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/97149d13-817a-4bdf-80ad-bd6727829829)
~~~
df.dropna()
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/d9416b09-15ad-49ba-9282-23c3dcbd6719)
~~~
df.dtypes
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/149f971b-20ca-4d67-968d-21905e13d0a2)
~~~
numeric_cols = df.select_dtypes(include=[int,float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/38becaeb-bfed-4a89-9fba-ceafb0b0cc1f)
~~~
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
~~~
~~~
sns.boxplot(numeric_cols)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/b65ef01a-c174-4f35-af17-4a890a3129f9)
~~~
sns.heatmap(numeric_cols.corr(),annot = True)
~~~
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-04/assets/121661327/e2182cb7-3a4d-41d8-946d-8378f50451a8)

# RESULT
    Thus we have read the given data and performed the multivariate analysis with different types of plots
