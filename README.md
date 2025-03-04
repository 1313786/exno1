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
              import pandas as pd
              import numpy as np
              import seaborn as sns
              import os 
              df=pd.read_csv("SAMPLEIDS.csv")
              df
  ![image](https://github.com/user-attachments/assets/ac94080a-8b8b-4993-b88f-fc5f11015ea4)
             
             df.isnull().sum()
  ![image](https://github.com/user-attachments/assets/94400342-1c3a-4d8d-86a7-9077d6f39b09)

             df.isnull().any()
  ![image](https://github.com/user-attachments/assets/a257a60d-a429-4569-997f-f031f6499aa6)

             df.dropna()
  ![image](https://github.com/user-attachments/assets/edb3367d-6dbb-46d7-adbc-0d8fa1d023f3)  

             df.fillna(0)
 ![image](https://github.com/user-attachments/assets/de591f57-efb5-447b-b591-1ee7c2274000)

             df.fillna(method = 'ffill')
![image](https://github.com/user-attachments/assets/5060093f-e8f8-4ddd-8392-c4a4a62955b3)

             df.fillna(method = 'bfill')
![image](https://github.com/user-attachments/assets/2955f31e-bd58-4fa8-be56-ccb274f47439)

             df_dropped = df.dropna()
               df_dropped
![image](https://github.com/user-attachments/assets/3289eb51-454a-45de-a9a0-7e5f26049126)

             df.fillna({'GENDER':'MALE','NAME':'KANISHKAR','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
![image](https://github.com/user-attachments/assets/c1361b56-6d4d-44c7-b9b5-41c8262f143e)

             import pandas as pd
             
             ir=pd.read_csv('iris.csv')
             ir
![image](https://github.com/user-attachments/assets/9071e7c2-ed41-4a26-9e8b-4ce9a9fa828d)

             ir.describe()

![image](https://github.com/user-attachments/assets/e33721cb-1eda-4371-b2ee-3447a4e11593)

             import seaborn as sns
             
             sns.boxplot(x='sepal_width',data=ir)
![image](https://github.com/user-attachments/assets/9baa2f04-556a-45ec-b5e7-d27750f4add7)

               c1=ir.sepal_width.quantile(0.25)
               c3=ir.sepal_width.quantile(0.75)
               iq=c3-c1
               print(c3)
![image](https://github.com/user-attachments/assets/f75b0cbb-0644-4d38-a84d-7d60ec4bcb58)

                rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
                rid['sepal_width']
![image](https://github.com/user-attachments/assets/ee76115a-0579-481a-aea9-6f543128e6fb)

                delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
                delid
![image](https://github.com/user-attachments/assets/7ce4a415-b73c-432f-8aa7-8456fcd464a5)

               sns.boxplot(x='sepal_width',data=delid)
![image](https://github.com/user-attachments/assets/b77cbb9a-1515-4dc0-9f4e-37e31def4071)

                import matplotlib.pyplot as plt
                import pandas as pd
                import numpy as np
                import scipy.stats as stats

                dataset=pd.read_csv("heights.csv")
                dataset
![image](https://github.com/user-attachments/assets/e45fdc5c-9aab-4166-a43a-5db2e7fff711)


                df = pd.read_csv("heights.csv")
                q1 = df['height'].quantile(0.25)
                q2 = df['height'].quantile(0.5)
                q3 = df['height'].quantile(0.75)
                
                iqr = q3-q1
                iqr

![image](https://github.com/user-attachments/assets/21716205-f3ee-4e32-b4c6-77d90339c872)

            low = q1 - 1.5*iqr
            low
![image](https://github.com/user-attachments/assets/1cdf729d-3b2e-493f-b060-477317e7d5a9)

            high = q3 + 1.5*iqr
            high
![image](https://github.com/user-attachments/assets/2d32820e-a68f-4f7a-b33f-fe2883032278)


            df1 = df[((df['height'] >=low)& (df['height'] <=high))]
            df1
![image](https://github.com/user-attachments/assets/b0d039ac-5d74-4d1d-82b6-e17fb446d82b)

            z = np.abs(stats.zscore(df['height']))
            z
![image](https://github.com/user-attachments/assets/8cc50a8c-aca8-4c09-8539-de026443135d)

            df1 = df[z<3]
            df1
![image](https://github.com/user-attachments/assets/ab066131-c05d-407b-a25a-17245d160034)













       





# Result
          Hence the data was cleaned , outliers were detected and removed.
