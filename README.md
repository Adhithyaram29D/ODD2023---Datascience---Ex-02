# Ex2 Outlier Dectection and Removal
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

## Explaination:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.

## Algorithm:
- Step1: Read the given Data.
- Step2: Get the information about the data.
- Step3: Detect the Outliers using IQR method and Z score.
- Step4: Remove the outliers.
- Step5: Plot the datas using Box Plot.

## Code:

## bhp.csv:
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

## height_weight.csv:
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

## Output:
## bhp.csv:
![Screenshot 2023-09-12 203209](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/6ceda7de-a24a-4bca-9125-b0ffa6c424e3)
![Screenshot 2023-09-12 203304](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/42e39f34-096e-422a-8cbc-b8ab67cdd20e)
![Screenshot 2023-09-12 203447](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/b1cf14e9-5c26-4e0e-911e-cc3884273f7d)
![Screenshot 2023-09-12 203500](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/0da07f50-7e81-4d42-85ae-f0c2f054a688)
![Screenshot 2023-09-12 203520](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/51d85889-7140-4824-93c4-04a03e62baf6)

## height_weight.csv:
![Screenshot 2023-09-12 203824](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/6b1bb20a-b99f-45ff-9467-95e0cbcc6b82)
![Screenshot 2023-09-12 203832](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/ddd72db7-a5e0-4f2b-9c99-d8414bb6b67a)
![Screenshot 2023-09-12 203842](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/8482c9fe-2a51-432d-98e2-d6e63220681d)
![Screenshot 2023-09-12 203851](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/e9af5e06-3959-4de0-b90c-90d35c4f9988)
![Screenshot 2023-09-12 204004](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/09278815-72d8-4d1a-9327-ed7433b6a0c6)
![Screenshot 2023-09-12 204016](https://github.com/Adhithyaram29D/ODD2023---Datascience---Ex-02/assets/119393540/a0bf353a-29c3-4cfd-9831-9ee7c2cfb3fb)
## Result:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.
