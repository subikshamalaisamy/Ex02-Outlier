# Ex02-Outlier

# Aim:

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

   (i) Using IQR detect weight outliers and print them
   
   (ii) Using IQR, detect height outliers and print them
   
# Algorithm:

# Step 1:

Read the given Data.

# step 2:

Remove outliers using IQR.

# step 3:

Use zscore of 3 to remove outliers and save the data to the file.

# step 4:

Read the next given Data.

# step 5:

Using IQR detect weight outliers and print them.

# step 6:

Using IQR, detect height outliers and print them.

# step 7:

Save the data to the file.

# Code:

import pandas as pd

import numpy as np

from scipy import stats

df1=pd.read_csv('/content/bhp.csv')

df1.head()

# (1) Remove outliers using IQR 

# (2) After removing outliers in step 1, you get a new dataframe.

q1=df1['price_per_sqft'].quantile(0.25)

q3=df1['price_per_sqft'].quantile(0.75)

IQR=q3-q1

df1=df1[((df1['price_per_sqft']>=q1-1.5*IQR)&(df1['price_per_sqft']<=q3+1.5*IQR))]

print(df1)

# (3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

z=np.abs(stats.zscore(df1['price_per_sqft']))

df1['price_per_sqft'][(z<3)]

print(df1)

# (4) for the data set height_weight.csv find the following

df2=pd.read_csv('/content/height_weight.csv')

df2.head()

# (i) Using IQR detect weight outliers and print them
    
q1=df2['weight'].quantile(0.25)
    
q3=df2['weight'].quantile(0.75)
    
IQR=q3-q1
    
df3=df2[((df2['weight']<=q1-1.5*IQR)|(df2['weight']>=q3+1.5*IQR))]
    
df3

# (ii) Using IQR, detect height outliers and print them
    
q1=df2['height'].quantile(0.25)
    
q3=df2['height'].quantile(0.75)
    
IQR=q3-q1
    
df2=df2[((df2['height']<=q1-1.5*IQR)|(df2['height']>=q3+1.5*IQR))]
    
df2

# Output:

<img width="491" alt="image" src="https://user-images.githubusercontent.com/87276633/227706942-e296194b-2c37-4e96-a17b-26f797f8ae19.png">
<img width="437" alt="image" src="https://user-images.githubusercontent.com/87276633/227707017-ced8fd99-8570-4961-8486-56649b0a35c7.png">
<img width="413" alt="image" src="https://user-images.githubusercontent.com/87276633/227707040-64190b91-6f70-408b-a3b2-ef33eb752ede.png">
<img width="344" alt="image" src="https://user-images.githubusercontent.com/87276633/227707062-60465369-4ed8-42be-b7b5-9ca1bc772f36.png">
<img width="425" alt="image" src="https://user-images.githubusercontent.com/87276633/227707075-ab923dec-0b26-41f1-a20e-0989556232ac.png">
<img width="437" alt="image" src="https://user-images.githubusercontent.com/87276633/227707140-cc9f4fa0-2718-45b5-a079-930719bdcd10.png">

# Result:

Thus the outliers are removed and the given datas are examined


