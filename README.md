# Ex02-Outlier
# AIM
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# EXPLANATION
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.

# ALGORITHM
STEP 1: Read the given Data.
STEP 2: Get the information about the data.
STEP 3: Detect the Outliers using IQR method and Z score.
STEP 4: Remove the outliers:
STEP 5: Plot the datas using box plot.

# PROGRAM
### For heights.csv
```
import pandas as pd
import seaborn as sns

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df

sns.boxplot(data=df)
sns.scatterplot(data=df)

q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr

low=q1-1.5*iqr
low

high=q3+1.5*iqr
high

aq=df[((df>=low)&(df<=high))]
aq.dropna()

df=df[((df>=low)&(df<=high))]
df.dropna()

sns.boxplot(data=df)
sns.scatterplot(data=df)

import pandas as pd
import seaborn as sns

af=pd.read_csv("heights.csv")
af
sns.boxplot(data=af)
sns.scatterplot(data=af)

min=af['height'].quantile(0.25)
max=af['height'].quantile(0.75)

max
min
iqr=max-min
iqr

dq=af[((af['height']>=min)&(af['height']<=max))]
dq

low=min-1.5*iqr
low

high=max+1.5*iqr
high

qm=af[((af['height']>=low)&(af['height']<=high))]
qm

import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats

data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df

sns.boxplot(data=df)
sns.scatterplot(data=df)

z=np.abs(stats.zscore(df))
print(df[z['weight']>3])

val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]

out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out
op=d_o(val)
op
```
### For iris.csv
```
 ir=pd.read_csv('iris.csv')
 ir
ir.describe()
sns.boxplot(x='sepal_width',data=ir)

c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid

sns.boxplot(x='sepal_width',data=delid)
```

# OUTPUT

### For heights.csv
![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/06334619-2127-48a9-a7ba-cd1489bac463)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/04dd12a2-6494-479a-ba35-5d6be307d6e9)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/8743ef5e-a66a-4266-b751-9e51936ae27e)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/94347b7d-7b4f-4ca0-9bf0-17e1d0c159f1)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/39e29e36-a9a6-4e8f-a41e-47a400167801)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/68fa2880-39c2-49de-8b7c-de9a6d044d68)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/1d1ddd03-a56a-4d39-b772-b8c7ab1d75e5)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/ac5543ef-ac59-4610-9ed8-7d02947604c9)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/0418756e-1bd6-4d68-8f7c-2279ecb43c11)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/fe79ddf8-e6ba-4839-8239-1afa7cdbe845)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/24096d2a-584c-4074-9d57-8ad04caf7eb8)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/bba3864d-0014-452f-90aa-a34dda0b6cb0)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/8179634c-e2c6-47a7-8513-7f6f56d87f1b)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/00cdb6bc-927f-481e-b097-8eb83451b9ff)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/2d5522c8-1685-4877-a11a-b283ed6400d1)

### For iris.csv
![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/87736ffa-868f-4549-a3dc-b07bb3f85f8f)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/bdfdb9ea-20b9-4448-8807-978a672b227f)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/cb5d817a-9e93-4f50-b194-3605da873a08)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/a0032a51-4d86-44a4-b8c2-e2387957593b)

![image](https://github.com/Jenishajustin/ODD2023---Datascience---Ex-02/assets/119405070/693bfa15-0e7f-47b1-8a35-27269341074b)

# RESULT
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.
