# Ex02-Outlier
# AIM
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# ALGORITHM
### STEP 1:
Read the given Data.

### STEP 2:
Get the information about the data.

### STEP 3:
Detect the Outliers using IQR method and Z score.

### STEP 4:
Remove the outliers:

### STEP 5:
Plot the datas using box plot.

# PROGRAM
### For heights.csv
```
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
low=q1-1.5*iqr
low
high=q3+1.5*iqr
high
af=af[((af>=low) & (af<=high))]
af.dropna()
sns.scatterplot(data=af)
sns.boxplot(data=af)

import pandas as pd
import seaborn as sns
df=pd.read_csv("heights.csv")
df
sns.boxplot(data=df)
sns.scatterplot(data=df)
max=df['height'].quantile(0.75)
min=df['height'].quantile(0.25)
iqr=max-min
low=min-1.5*iqr
low
high=max+1.5*iqr
high
df
qm=df[((df['height']>=low) & (df['height']<=high))]
qm.dropna()
sns.boxplot(data=qm)
max
min
dq=df[((df['height']>=min) & (df['height']<=max))]
dq

import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight' :[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
sns.boxplot(data=df)
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
