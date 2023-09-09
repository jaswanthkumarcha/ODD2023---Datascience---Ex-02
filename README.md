# Ex02 Outlier Detection
## AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,
- (1) Remove outliers using IQR
- (2) After removing outliers in step 1, you get a new dataframe.
- (3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result
- (4) for the data set height_weight.csv find the following
   - (i) Using IQR detect weight outliers and print them
   - (ii) Using IQR, detect height outliers and print them
## EXPLANATION:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.
## ALGORITHM:
- Step1: Read the given Data.
- Step2: Get the information about the data.
- Step3: Detect the Outliers using IQR method and Z score.
- Step4: Remove the outliers.
- Step5: Plot the datas using Box Plot.
```
Developed by :chadalawada jaswanth
register number : 212221040030
```
## CODE:
### bhp.csv:
```
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('bhp.csv')
df.info()
print(df.describe())
df.head()
#BEFORE REMOVING OUTLIER
sns.boxplot(y='price_per_sqft',data=df)

# PERFORMING IQR METHOD
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
IQR=q3-q1
low=q1-1.5*IQR
high=q3+1.5*IQR
new=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]

#AFTER REMOVING OUTLIER using IQR method
sns.boxplot(y='price_per_sqft',data=new)

# PERFORMING Zscore METHOD
z=np.abs(stats.zscore(df['price_per_sqft']))
new2=df[(z<3)]

#AFTER REMOVING OUTLIER using Zscore method
sns.boxplot(y="price_per_sqft",data=new2)
```
### height_weight.csv:
```
import pandas as pd
import seaborn as sns
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('height_weight.csv')
df.info()
df.describe()
df.head()

#BEFORE REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
height_q1 = df['height'].quantile(0.25)
height_q3 = df['height'].quantile(0.75)
height_IQR = height_q3 - height_q1
height_low = height_q1 - 1.5 * height_IQR
height_high = height_q3 + 1.5 * height_IQR
height_new=df[((df['height']>=height_low)&(df['height']<=height_high))]
#AFTER REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=height_new)

#BEFORE REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
weight_q1 = df['weight'].quantile(0.25)
weight_q3 = df['weight'].quantile(0.75)
weight_IQR = weight_q3 - weight_q1
weight_low = weight_q1 - 1.5 * weight_IQR
weight_high = weight_q3 + 1.5 * weight_IQR
weight_new=df[((df['weight']>=weight_low)&(df['weight']<=weight_high))]
#AFTER REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=weight_new)
```
## OUTPUT:
### bhp.csv:
![bhp](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/ac329473-447e-4074-a67b-83ec89c74598)

![bhp head](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/a26a59db-13c8-4bb7-9d4a-4c5d48b2da2b)

![1out](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/f2691be0-ca5d-42d5-b197-45d9a0013cf0)

![2out](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/e51f3a4b-d629-47c5-876b-a32f685cf6d3)

![3out](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/2a2b650f-32a4-4e35-88cb-e346fcc3b814)
### weight_height.csv:
![height weight](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/8c2b42a3-43ef-4538-bc6e-16f36b8b7498)

![height head](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/aa051aaa-a4f3-46fc-acd2-69b8e991c2e7)

![height1](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/fa40996a-8529-4cb8-b6c1-d6be674cb2a8)

![height2](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/87fc5b3f-d8aa-410a-9a47-138ecebc7fdb)

![height3](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/f1175dea-05e8-424f-81c5-05597ca6e60c)

![height4](https://github.com/deepikasrinivasans/ODD2023---Datascience---Ex-02/assets/119393935/28060644-5baa-46cc-b176-153656090a6f)


## RESULT:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.



    

