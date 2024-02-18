# Honda-Cars-Data
The program analyzes and visualizes data with all 6 topics.
- Reading and Writing Files
- Working with CSV Files
- NumPy
- Pandas
- Data Cleaning and Organizing
- Data Analytics and Visualization

Link Dataset : https://www.kaggle.com/datasets/omartorres25/honda-data?classId=c5712fa0-51ea-46b4-90aa-000bb7d83c44&assignmentId=430b8ac7-ff60-4fc6-801d-1e34cd709911&submissionId=c737a0d1-7219-2593-6f3a-7816df4d21f5

### Working with CSV Files

```
with open("honda_sell_data.csv", "r") as file:
    lines = file.readlines()
```
### Use the for command to display each line.
```
for line in lines:
    print(line.strip())
```
### Read honda_sell_data.csv files only for Consumer_Rating data
```
import csv

with open("honda_sell_data.csv", "r") as file:
    reader = csv.DictReader(file) 
    Consumer_Rating = [float(row["Consumer_Rating"]) for row in reader] 
```
### Display data, totals, and total amounts of Consumer_Rating data.
```
print("Consumer_Rating :") 
print(Consumer_Rating)

print("\nSum of Consumer_Rating :")
print(sum(Consumer_Rating )) # คำนวณผลรวม

print("\nLenght of Consumer_Rating :")
print(len(Consumer_Rating)) # หาความยาวจำนวนทั้งหมด
```
### Displays the average calculation of Consumer_Rating
```
Consumer_Rating = sum(Consumer_Rating) / len(Consumer_Rating)
print("Consumer_Rating:")
print(Consumer_Rating)
```
### Import numpy and use NumPy to load and display the data of the honda_sell_data.csv file.
```
import numpy as np

data = np.loadtxt('honda_sell_data.csv', delimiter=',', skiprows=1, usecols=[0])
print(data)
```
### Calculate the average of columns in the NumPy array of data.
- Mean 
- Median 
- Standard Deviation 
- Variance 
- Minimum 
- Maximum
```
#Mean
mean = np.mean(data, axis=0)
print("Mean:")
print(mean)

#Median
median = np.median(data, axis=0)
print("Median:")
print(median)

#Standard Deviation
std_dev = np.std(data, axis=0)
print("Standard Deviation:")
print(std_dev)

#Variance
variance = np.var(data, axis=0)
print("Variance:")
print(variance)

#Minimum
min = np.amin(data, axis=0)
print("Min:")
print(min)

#Maximum
max = np.amax(data, axis=0)
print("Max:")
print(max)
```
### The program displays the value Normalize each feature.
```
data_norm = (data - mean) / std_dev
print(data_norm)
```
### Import pandas files and use pandas to read honda_sell_data.csv files, store DataFrame data, and display data.
```
import pandas as pd

honda_sell_data_df = pd.read_csv("honda_sell_data.csv")
print(honda_sell_data_df)
     
```
### Use the info() command.
```
print(honda_sell_data_df.info())
```
### Read the honda_sell_data.csv file.
```
import pandas as pd
import numpy as np
import csv

honda_sell_data_df =  pd.read_csv("honda_sell_data.csv")
honda_sell_data_df
```
### The program uses the .isnull().sum() command to check the number of null values or missing values.
```
honda_sell_data_df.isnull().sum()
```
### Programs to Remove Unwanted Columns
```
to_drop = ['Engine', 
           'VIN', 
           'Transmission']

honda_sell_data_df.drop(to_drop, inplace = True, axis = 1)
honda_sell_data_df
```
### The program imports numpy, pandas, matplotlib, seaborn, and honda_sell_data.csv file readers.
```
#import numpy, pandas, matplotlib and seaborn
import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sns

#Read the honda_sell_data.csv file.
honda_sell_data_df = pd.read_csv("honda_sell_data.csv")
honda_sell_data_df.head()
```
### The program uses the value_counts() command to count the data count of Value_For_Money_Rating
```
sns.countplot(x="Value_For_Money_Rating", data=honda_sell_data_df, palette="tab10")
plt.show()
```
### The program displays the mean values of various data of the Value_For_Money_Rating group.
```
honda_sell_data_df.groupby('Value_For_Money_Rating').mean()
```
