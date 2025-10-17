## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
      
import numpy as np
from scipy import stats
df=pd.read_csv("data.csv")
df
<img width="579" height="429" alt="image" src="https://github.com/user-attachments/assets/1016be3d-cbca-479d-8fdb-bddabfc7bc9c" />
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
climate=['Cold','Warm','Hot','Very Hot']
ele=OrdinalEncoder(categories=[climate])
ele.fit_transform(df[["Ord_1"]])
<img width="155" height="232" alt="image" src="https://github.com/user-attachments/assets/db46de97-ccbf-4801-899d-8f1c608b086e" />
df['bo2']=ele.fit_transform(df[['Ord_1']])
df
<img width="604" height="433" alt="image" src="https://github.com/user-attachments/assets/061f8277-e51a-4041-a147-a2fb8e06f856" />
le=LabelEncoder()
df2=df.copy()
df2['Ord_2']=le.fit_transform(df2['Ord_2'])
df2

<img width="566" height="431" alt="image" src="https://github.com/user-attachments/assets/b25bec1c-ca5e-4e24-9588-58400b8faa2a" />
from sklearn.preprocessing import OneHotEncoder 
ohe=OneHotEncoder()
df3=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df[['City']]))
df2=pd.concat([enc,df3],axis=1)
df2

<img width="1039" height="427" alt="image" src="https://github.com/user-attachments/assets/4390e04f-daaa-4765-9f5e-8c0e6b7dfe25" />

pd.get_dummies(df,columns=['City'])

<img width="1027" height="439" alt="image" src="https://github.com/user-attachments/assets/42480dd0-7446-4622-b3e8-b80ea4ffad4f" />
pip install --upgrade category_encoders

<img width="1543" height="353" alt="image" src="https://github.com/user-attachments/assets/a5212204-6435-4fdf-865b-d5dfc9e44e68" />


from category_encoders import BinaryEncoder

import pandas as pd
df=pd.read_csv("C:\Users\priya\Downloads\data.csv")

be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])

df1=pd.concat([df,nd],axis=1)
df1=df.copy()

df1


<img width="656" height="448" alt="image" src="https://github.com/user-attachments/assets/c91ed690-41b9-4c24-b5cc-d81a409061f6" />
from category_encoders import TargetEncoder
te=TargetEncoder()

cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])

cc=pd.concat([cc,new],axis=1)
cc

<img width="750" height="465" alt="image" src="https://github.com/user-attachments/assets/b0a1712d-18ea-4d8b-b6cb-20a49c5ee574" />

import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("Data_to_Transform.csv")
df

<img width="1041" height="535" alt="image" src="https://github.com/user-attachments/assets/f548193c-7d31-47d9-9a28-a2b7900b35fb" />

np.reciprocal(df["Moderate Positive Skew"])



df.skew()



np.log(df["Highly Positive Skew"])


np.reciprocal(df["Highly Positive Skew"])


<img width="740" height="302" alt="image" src="https://github.com/user-attachments/assets/da5f8dfd-2885-4a2f-9e30-38ab8de3b945" />


# RESULT:
       # INCLUDE YOUR RESULT HERE

       
