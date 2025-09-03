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
```
import pandas as pd
df=pd.read_csv('Loan_data.csv')
df
```

### Output
<img width="1569" height="534" alt="image" src="https://github.com/user-attachments/assets/570d533b-a8e0-4880-98f3-4b1eaf21d402" />

```
df.head(5)
```

### Output
<img width="1558" height="260" alt="image" src="https://github.com/user-attachments/assets/c73ddd4f-9a23-4ba7-b31e-7a2ed2a9576e" />

```
df.tail(5)
```
### Output
<img width="1573" height="247" alt="image" src="https://github.com/user-attachments/assets/524c14e1-cd72-466d-967a-3b03db8e67ec" />


```
df.info()
```

<img width="549" height="399" alt="image" src="https://github.com/user-attachments/assets/31c5a028-7d16-484b-a788-d8337fe646ea" />

```
df.describe()
```

### Output
<img width="893" height="372" alt="image" src="https://github.com/user-attachments/assets/714f0cdc-cf73-4b66-b005-a233a0435924" />

```
df.shape
```

<img width="186" height="54" alt="image" src="https://github.com/user-attachments/assets/2eff700d-ccd7-4bcf-96ba-490a52537602" />

```
df.isnull().sum()
```

### Output
<img width="306" height="294" alt="image" src="https://github.com/user-attachments/assets/c6fd2d1d-c29c-479e-96fd-26d266580acd" />

```
df.nunique()
```
### Output
<img width="350" height="297" alt="image" src="https://github.com/user-attachments/assets/eb987be9-079e-4ada-93b0-24c1bedf665d" />

```
mn=df.Credit_History.mean()
mn
```

### Output
<img width="273" height="43" alt="image" src="https://github.com/user-attachments/assets/92e4d0bc-f9fe-443e-8ef1-c63f22d4d83d" />

```
df['Gender'].value_counts()
```

### Output
<img width="346" height="94" alt="image" src="https://github.com/user-attachments/assets/33857183-dcc5-4a96-b3ff-0b5c4c92ed86" />

```
df.Credit_History.fillna(mn,inplace=True)
df.LoanAmount.fillna(0)
```
<img width="506" height="274" alt="image" src="https://github.com/user-attachments/assets/9ff1a8e6-d296-491f-b9f4-0e445f3cded1" />
```
min=df.LoanAmount.min()
min
```

### Output
<img width="139" height="40" alt="image" src="https://github.com/user-attachments/assets/59ac6399-edb3-4c55-8f6a-ed165646d3fa" />

```
df.LoanAmount.fillna(min,inplace=True)
df
```

### Output
<img width="1575" height="519" alt="image" src="https://github.com/user-attachments/assets/1992e972-1b19-44eb-96e1-7133c16c82fa" />

```
df.isnull()
```

### Output
<img width="1538" height="535" alt="image" src="https://github.com/user-attachments/assets/f39112cf-ccad-419c-9893-ab0e8520b944" />

```
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```

### Output
<img width="198" height="583" alt="image" src="https://github.com/user-attachments/assets/1aabf325-26c3-464f-9956-1b056ac80e44" />

```
sns.boxplot(data=af)
```

### Output
<img width="830" height="547" alt="image" src="https://github.com/user-attachments/assets/8f192b50-8333-47bd-ae9b-a784bba6d3d3" />

```
sns.scatterplot(data=af)
```

### Output
<img width="810" height="553" alt="image" src="https://github.com/user-attachments/assets/ab3ce03e-4c08-46ab-8215-adf9e2d89ca6" />

```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```

### Output
<img width="234" height="71" alt="image" src="https://github.com/user-attachments/assets/cfe3ffbb-a8e5-4b2a-9916-50c238229edd" />

```
low=q1-1.5*iqr
low
```

### Output
<img width="213" height="51" alt="image" src="https://github.com/user-attachments/assets/74ba39af-1d39-47c2-aece-0b0ad2ac0b2b" />

```
high=q3+1.5*iqr
high
```

### Output
<img width="229" height="63" alt="image" src="https://github.com/user-attachments/assets/db6b88b3-8ad4-4680-9311-7de7b8cf3098" />

```
af=af[((af>=low)&(af<=high))]
af
```

### Output
<img width="234" height="594" alt="image" src="https://github.com/user-attachments/assets/6a8de177-7845-4903-b739-300c88a78d2c" />

```
af.dropna()
```

### Output
<img width="202" height="421" alt="image" src="https://github.com/user-attachments/assets/760b51a7-d8ae-4178-9dcd-5d3d3c9a31e2" />

```
sns.boxplot(data=af)
```

### Output
<img width="840" height="554" alt="image" src="https://github.com/user-attachments/assets/6e5dd26d-e03b-48e4-9ff9-154f6044d481" />

```
data=[1,12,15,18,21,24,27,20,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,158]
df=pd.DataFrame(data)
df
```

### Output
<img width="107" height="639" alt="image" src="https://github.com/user-attachments/assets/291e40aa-5d0a-41eb-8b95-fbbe48522111" />

```
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
z
```

### Output
<img width="128" height="635" alt="image" src="https://github.com/user-attachments/assets/2d1e196c-6806-4c4e-8d7a-e305e6bf0d92" />

# Result
Thus, we have read the given data and performed data cleaning and saved the cleaned data to a file successfully.
