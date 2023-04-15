# Ex-02-Outlier-Detection-and-Removal


# AIM:

To read the given data and perform data cleaning and save the cleaned data to a file

# EXPLANATION:

Outliers are extreme values that differ from most other data points in a dataset. They can have a big impact on your statistical analyses and skew the results of any hypothesis tests. It’s important to carefully identify potential outliers in your dataset and deal with them in an appropriate manner for accurate results.

# ALGORITHM:

# STEP-1:

Read the given data.

# STEP-2:

Get the information about the data.

# STEP-3:

Detect the outliers in the given datasets.

# STEP-4:

Remove the outliers from the given datasets by using outlier handling techniques.

# STEP-5:

Save the Cleaned data to the file.

# CODE:

# BHP dataset:

import pandas as pd

import numpy as np

import seaborn as sns

from google.colab import files

uploaded = files.upload()

df=pd.read_csv("bhp.csv")

df

# Remove outliers using IQR and Get a new Dataframe:

q1=df['price_per_sqft'].quantile(0.25)

q3=df['price_per_sqft'].quantile(0.75)

IQR=q3-q1

print("First quantile:",q1," Third quantile:",q3," IQR: ",IQR,"\n")

lower=q1-1.5*IQR

upper=q3+1.5*IQR

outliers=df[(df['price_per_sqft']>=lower)&(df['price_per_sqft']<=upper)]

print("Outliers: \n")

print(outliers)

# Using zscore of 3 to remove outliers:

from scipy.stats import zscore

z=outliers[(zscore(outliers['price_per_sqft'])<3)]

print("Cleaned Data: \n")

print(z)

# Height_Weight dataset:

import pandas as pd

import numpy as np

import seaborn as sns

from google.colab import files

uploaded = files.upload()

df=pd.read_csv("height_weight.csv")

df

# Using IQR detect weight outliers and print them:

q1=df['weight'].quantile(0.25)

q3=df['weight'].quantile(0.75)

IQR=q3-q1

print("First quantile:",q1," Third quantile:",q3," IQR: ",IQR,"\n")

lower=q1-1.5*IQR

upper=q3+1.5*IQR

outliers=df[(df['weight']>=lower)&(df['weight']<=upper)]

print("Outliers: \n")

print(outliers)

# Using IQR, detect height outliers and print them:

q1=df['height'].quantile(0.25)

q3=df['height'].quantile(0.75)

IQR=q3-q1

print("First quantile:",q1," Third quantile:",q3," IQR: ",IQR,"\n")

lower=q1-1.5*IQR

upper=q3+1.5*IQR

outliers=df[(df['height']>=lower)&(df['height']<=upper)]

print("Outliers: \n")

print(outliers)

# OUTPUT:
![Screenshot (50)](https://user-images.githubusercontent.com/128019999/232205902-e6713bbf-0d91-40a0-a816-bb7cacbe2bba.png)

![Screenshot (51)](https://user-images.githubusercontent.com/128019999/232205923-a368c844-3e08-46cb-b781-dbf7dad85d2b.png)

![Screenshot (54)](https://user-images.githubusercontent.com/128019999/232206052-5b3f8441-5dd3-4a5f-be58-27f16b542f2f.png)

![Screenshot (53)](https://user-images.githubusercontent.com/128019999/232206066-9c90ce8c-5ec6-4711-a6ac-52ac263a4dcc.png)

![Screenshot (57)](https://user-images.githubusercontent.com/128019999/232206221-2fac0953-b999-4edd-99e7-6d26c81894d8.png)

![Screenshot (55)](https://user-images.githubusercontent.com/128019999/232206083-d8b44fdc-5c0b-4b16-8e38-d2958d14453a.png)

# RESULT:

Thus the outliers were detected and removed from the given datasets by using outlier handling 
