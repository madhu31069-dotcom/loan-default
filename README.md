import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
     

np.random.seed(42)
n=250
     

data={
     "Student_ID": range(1, n+1),
    "Name": ["Student_" + str(i) for i in range(1, n+1)],
    "Gender": np.random.choice(["Male", "Female"], n),
    "Department": np.random.choice(["CSE", "IT", "ECE"], n),
    "Year": np.random.choice(["1st", "2nd", "3rd"], n),
    "Maths": np.random.randint(35, 100, n),
    "Science": np.random.randint(35, 100, n),
    "English": np.random.randint(35, 100, n),
    "Attendance": np.random.randint(50, 100, n),
    "Internal_Marks": np.random.randint(0, 25, n)
}
     

df=pd.DataFrame(data)
df.head()                   

Your code creates a student dataset with 250 records and then displays the first 5 rows using df.head().

Here’s what each part does:

import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
Imports libraries for:
numerical operations (numpy)
plotting (matplotlib, seaborn)
data handling (pandas)
np.random.seed(42)
Ensures the random values are reproducible.
n = 250
Number of students.

The dictionary data creates columns like:

Student ID
Name
Gender
Department
Year
Subject marks
Attendance
Internal marks
df = pd.DataFrame(data)
Converts the dictionary into a pandas DataFrame.
df.head()
Displays the first 5 rows.

Example output format:

Student_ID	Name	Gender	Department	Year	Maths	Science	English	Attendance	Internal_Marks
1	Student_1	Male	CSE	2nd	78	66	88	92	15
2	Student_2	Female	IT	1st	54	74	61	81	20
3	Student_3	Male	ECE	3rd	91	82	73	95	19
4	Student_4	Female	CSE	1st	69	58	90	77	11
5	Student_5	Male	IT	2nd	84	97	65	89	24

You can also inspect the dataset further with:

df.info()
df.describe()
df.shape
df.columns

Or visualize it:

sns.histplot(df["Maths"])
plt.show()
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
     

np.random.seed(42)
n=250
     

data={
     "Student_ID": range(1, n+1),
    "Name": ["Student_" + str(i) for i in range(1, n+1)],
    "Gender": np.random.choice(["Male", "Female"], n),
    "Department": np.random.choice(["CSE", "IT", "ECE"], n),
    "Year": np.random.choice(["1st", "2nd", "3rd"], n),
    "Maths": np.random.randint(35, 100, n),
    "Science": np.random.randint(35, 100, n),
    "English": np.random.randint(35, 100, n),
    "Attendance": np.random.randint(50, 100, n),
    "Internal_Marks": np.random.randint(0, 25, n)
}
     

df=pd.DataFrame(data)
df.head()                                                                                                                                                                                    df.isnull().sum()
     

df.info()
df.describe()
     

df["Total"]=df["Maths"]+df["Science"]+df["English"]
df["Average"]=df["Total"]/3
     

def grade(avg):
  if avg >= 90:
    return "A"
  elif avg >= 80:
    return "B"
  elif avg >= 70:
    return "C"
  elif avg >= 60:
    return "D"
  else:
    return "F"

df["Grade"]=df["Average"].apply(grade)
     

top_students=df.sort_values(by="Total",ascending=False).head(5)                                                                    fail_students=df[df["Grade"]=="Fail"]
     

df.groupby("Department")["Average"].mean()
     

df.groupby("Gender")["Average"].mean()
     

df.groupby("Year")["Average"].mean()
     

df.groupby("Department")["Average"].mean().plot(kind="bar")
plt.title("Department wise performance")
plt.show
     

df["Gender"].value_counts().plot(kind="pie", autopct='%1.1f%%')
plt.show()
     

plt.hist(df["Average"])
plt.title("Average Marks Distribution")
plt.show()
     

plt.scatter(df["Attendance"], df["Average"])
plt.xlabel("Attendance")
plt.ylabel("Average Marks")
plt.show()    give a readme flie for this coding
Student Performance Analysis System
Overview

This project is a Student Performance Analysis System developed using Python libraries such as NumPy, Pandas, Matplotlib, and Seaborn.
It generates a synthetic dataset of student records and performs data analysis and visualization to evaluate academic performance.

The project includes:

Data generation
Data cleaning and inspection
Student grading system
Performance analysis
Data visualization
Technologies Used
Python
NumPy
Pandas
Matplotlib
Seaborn
Features
Generate random student dataset
Calculate total and average marks
Assign grades automatically
Identify top-performing students
Analyze performance by:
Department
Gender
Year
Create visualizations:
Bar chart
Pie chart
Histogram
Scatter plot
Dataset Details

The dataset contains the following columns:

Column Name	Description
Student_ID	Unique student ID
Name	Student name
Gender	Male/Female
Department	CSE / IT / ECE
Year	1st / 2nd / 3rd
Maths	Maths marks
Science	Science marks
English	English marks
Attendance	Attendance percentage
Internal_Marks	Internal assessment marks
Installation

Install the required Python libraries using pip:

pip install numpy pandas matplotlib seaborn
How to Run
Copy the Python code into a file named:
student_analysis.py
Run the file:
python student_analysis.py
Project Workflow
1. Import Libraries
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
2. Generate Dataset

Random student data is generated using NumPy.

np.random.seed(42)
n = 250
3. Create DataFrame
df = pd.DataFrame(data)
4. Data Inspection
df.head()
df.info()
df.describe()
df.isnull().sum()
5. Calculate Total and Average
df["Total"] = df["Maths"] + df["Science"] + df["English"]
df["Average"] = df["Total"] / 3
6. Grade Assignment

Grades are assigned based on average marks.

Average Marks	Grade
90 and above	A
80–89	B
70–79	C
60–69	D
Below 60	F
7. Performance Analysis
Top Students
top_students = df.sort_values(by="Total", ascending=False).head(5)
Department-wise Average
df.groupby("Department")["Average"].mean()
Gender-wise Average
df.groupby("Gender")["Average"].mean()
Year-wise Average
df.groupby("Year")["Average"].mean()
Visualizations
1. Department-wise Performance
df.groupby("Department")["Average"].mean().plot(kind="bar")
2. Gender Distribution
df["Gender"].value_counts().plot(kind="pie", autopct='%1.1f%%')
3. Average Marks Distribution
plt.hist(df["Average"])
4. Attendance vs Average Marks
plt.scatter(df["Attendance"], df["Average"])
Sample Output
Student grade classification
Department performance comparison
Attendance correlation with marks
Top 5 students list
Statistical summary of dataset
Future Improvements
Add CSV file export
Build interactive dashboard
Use real student datasets
Add machine learning prediction models
Create web application interface
Author

Student Performance Analysis Project using Python and Data Visualization.

import pandas as pd
import numpy as np
from io import StringIO
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_absolute_error
from sklearn.preprocessing import LabelEncoder


csv_data = '''
loan_amnt,term,int_rate,annual_inc,emp_length,home_ownership,purpose,grade,loan_status
5000,36 months,10.65%,24000,10 years,RENT,credit_card,B,Fully Paid
2500,60 months,15.27%,30000,1 year,RENT,car,C,Charged Off
2400,36 months,15.96%,12252,10 years,OWN,small_business,C,Fully Paid
10000,36 months,13.49%,49200,3 years,MORTGAGE,other,B,Fully Paid
3000,60 months,12.69%,80000,9 years,RENT,debt_consolidation,B,Charged Off
5000,36 months,7.90%,36000,4 years,MORTGAGE,home_improvement,A,Fully Paid
7000,36 months,18.64%,47000,2 years,RENT,medical,D,Charged Off
12000,60 months,21.28%,95000,8 years,MORTGAGE,credit_card,E,Charged Off
4000,36 months,11.14%,42000,5 years,OWN,vacation,B,Fully Paid
15000,60 months,16.29%,65000,7 years,MORTGAGE,debt_consolidation,C,Fully Paid
'''

     

loan_data = pd.read_csv(StringIO(csv_data))

print("Dataset Loaded Successfully")


print("\nFirst 5 Rows:")
print(loan_data.head())                                                                                                                           print("\nDataset Shape:")
print(loan_data.shape)

print("\nDataset Information:")
print(loan_data.info())


print("\nMissing Values:")
print(loan_data.isnull().sum())

# Remove percentage symbol from interest rate
loan_data['int_rate'] = loan_data['int_rate'].str.replace('%', '')
loan_data['int_rate'] = loan_data['int_rate'].astype(float)

# Convert term into integer
loan_data['term'] = loan_data['term'].str.extract('(\d+)').astype(int)

# Convert employment length into integer
loan_data['emp_length'] = loan_data['emp_length'].str.extract('(\d+)')
loan_data['emp_length'] = loan_data['emp_length'].fillna(0)
loan_data['emp_length'] = loan_data['emp_length'].astype(int)


loan_data['loan_status'] = loan_data['loan_status'].map({
    'Fully Paid': 0,
    'Charged Off': 1
})


encoder = LabelEncoder()

loan_data['home_ownership'] = encoder.fit_transform(
    loan_data['home_ownership']
)                                                                                                                                                            loan_data['purpose'] = encoder.fit_transform(
    loan_data['purpose']
)

loan_data['grade'] = encoder.fit_transform(
    loan_data['grade']
)


print("\nDescriptive Statistics:")
print(loan_data.describe())

print("\nAverage Loan Amount:")
print(loan_data['loan_amnt'].mean())

print("\nAverage Annual Income:")
print(loan_data['annual_inc'].mean())

print("\nAverage Interest Rate:")
print(loan_data['int_rate'].mean())   give a readme file 
Loan Data Analysis and Prediction System
Overview

This project is a Loan Data Analysis and Prediction System developed using Python.
The project demonstrates how to:

Load and preprocess loan data
Perform exploratory data analysis (EDA)
Clean and transform data
Encode categorical variables
Analyze loan-related statistics

The dataset used in this project is a sample loan dataset created directly inside the Python script using CSV format.

Technologies Used
Python
Pandas
NumPy
Matplotlib
Seaborn
Plotly
Scikit-learn
Features
Load loan dataset from CSV string
Display dataset structure and statistics
Handle missing values
Clean percentage and text-based columns
Convert categorical data into numerical form
Analyze:
Loan amount
Annual income
Interest rates
Prepare dataset for machine learning models
Dataset Description

The dataset contains the following columns:

Column Name	Description
loan_amnt	Loan amount requested
term	Loan duration (36 or 60 months)
int_rate	Interest rate
annual_inc	Applicant annual income
emp_length	Employment length
home_ownership	Home ownership status
purpose	Purpose of loan
grade	Loan grade
loan_status	Loan repayment status
Installation

Install required libraries using pip:

pip install pandas numpy matplotlib seaborn plotly scikit-learn
Project Workflow
1. Import Required Libraries
import pandas as pd
import numpy as np
from io import StringIO
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
2. Load Dataset

The dataset is stored as a CSV string and loaded using StringIO.

loan_data = pd.read_csv(StringIO(csv_data))
3. Explore Dataset
Display First 5 Rows
print(loan_data.head())
Dataset Shape
print(loan_data.shape)
Dataset Information
print(loan_data.info())
Missing Values
print(loan_data.isnull().sum())
Data Preprocessing
1. Clean Interest Rate Column

Remove % symbol and convert to float.

loan_data['int_rate'] = loan_data['int_rate'].str.replace('%', '')
loan_data['int_rate'] = loan_data['int_rate'].astype(float)
2. Convert Loan Term into Integer
loan_data['term'] = loan_data['term'].str.extract('(\d+)').astype(int)
3. Convert Employment Length
loan_data['emp_length'] = loan_data['emp_length'].str.extract('(\d+)')
loan_data['emp_length'] = loan_data['emp_length'].fillna(0)
loan_data['emp_length'] = loan_data['emp_length'].astype(int)
4. Encode Loan Status
Loan Status	Encoded Value
Fully Paid	0
Charged Off	1
loan_data['loan_status'] = loan_data['loan_status'].map({
    'Fully Paid': 0,
    'Charged Off': 1
})
5. Label Encoding

Categorical columns are converted into numerical values using LabelEncoder.

encoder = LabelEncoder()
Encoded Columns:
home_ownership
purpose
grade
Statistical Analysis
Descriptive Statistics
print(loan_data.describe())
Average Loan Amount
print(loan_data['loan_amnt'].mean())
Average Annual Income
print(loan_data['annual_inc'].mean())
Average Interest Rate
print(loan_data['int_rate'].mean())
Machine Learning Preparation

The project imports machine learning tools from Scikit-learn:

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_absolute_error

These can be used later for:

Loan risk prediction
Loan approval analysis
Interest rate prediction
Possible Visualizations

You can extend the project with charts such as:

Loan Amount Distribution
sns.histplot(loan_data['loan_amnt'])
plt.show()
Interest Rate Analysis
sns.boxplot(x=loan_data['int_rate'])
plt.show()
Loan Status Count
sns.countplot(x=loan_data['loan_status'])
plt.show()
Sample Output

The project generates:

Dataset summary
Statistical analysis
Cleaned numerical dataset
Encoded categorical values
Mean loan statistics
Future Enhancements
Add real-world loan dataset
Build loan default prediction model
Create interactive dashboard using Plotly
Add classification algorithms
Deploy as a web application
How to Run
Save the code into a Python file:
loan_analysis.py
Run the program:
python loan_analysis.py
Author

Loan Data Analysis and Machine Learning Preparation Project using Python.

import pandas as pd
import numpy as np
from io import StringIO
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_absolute_error
from sklearn.preprocessing import LabelEncoder


csv_data = '''
loan_amnt,term,int_rate,annual_inc,emp_length,home_ownership,purpose,grade,loan_status
5000,36 months,10.65%,24000,10 years,RENT,credit_card,B,Fully Paid
2500,60 months,15.27%,30000,1 year,RENT,car,C,Charged Off
2400,36 months,15.96%,12252,10 years,OWN,small_business,C,Fully Paid
10000,36 months,13.49%,49200,3 years,MORTGAGE,other,B,Fully Paid
3000,60 months,12.69%,80000,9 years,RENT,debt_consolidation,B,Charged Off
5000,36 months,7.90%,36000,4 years,MORTGAGE,home_improvement,A,Fully Paid
7000,36 months,18.64%,47000,2 years,RENT,medical,D,Charged Off
12000,60 months,21.28%,95000,8 years,MORTGAGE,credit_card,E,Charged Off
4000,36 months,11.14%,42000,5 years,OWN,vacation,B,Fully Paid
15000,60 months,16.29%,65000,7 years,MORTGAGE,debt_consolidation,C,Fully Paid
'''

     

loan_data = pd.read_csv(StringIO(csv_data))

print("Dataset Loaded Successfully")


print("\nFirst 5 Rows:")
print(loan_data.head())

print("\nDataset Shape:")
print(loan_data.shape)

print("\nDataset Information:")
print(loan_data.info())


print("\nMissing Values:")
print(loan_data.isnull().sum())

# Remove percentage symbol from interest rate
loan_data['int_rate'] = loan_data['int_rate'].str.replace('%', '')
loan_data['int_rate'] = loan_data['int_rate'].astype(float)

# Convert term into integer
loan_data['term'] = loan_data['term'].str.extract('(\d+)').astype(int)

# Convert employment length into integer
loan_data['emp_length'] = loan_data['emp_length'].str.extract('(\d+)')
loan_data['emp_length'] = loan_data['emp_length'].fillna(0)
loan_data['emp_length'] = loan_data['emp_length'].astype(int)


loan_data['loan_status'] = loan_data['loan_status'].map({
    'Fully Paid': 0,
    'Charged Off': 1
})


encoder = LabelEncoder()

loan_data['home_ownership'] = encoder.fit_transform(
    loan_data['home_ownership']
)

loan_data['purpose'] = encoder.fit_transform(
    loan_data['purpose']
)

loan_data['grade'] = encoder.fit_transform(
    loan_data['grade']
)


print("\nDescriptive Statistics:")
print(loan_data.describe())

print("\nAverage Loan Amount:")
print(loan_data['loan_amnt'].mean())

print("\nAverage Annual Income:")
print(loan_data['annual_inc'].mean())

print("\nAverage Interest Rate:")
print(loan_data['int_rate'].mean())

     Dataset Loaded Successfully

First 5 Rows:
   loan_amnt       term int_rate  annual_inc emp_length home_ownership  \
0       5000  36 months   10.65%       24000   10 years           RENT   
1       2500  60 months   15.27%       30000     1 year           RENT   
2       2400  36 months   15.96%       12252   10 years            OWN   
3      10000  36 months   13.49%       49200    3 years       MORTGAGE   
4       3000  60 months   12.69%       80000    9 years           RENT   

              purpose grade  loan_status  
0         credit_card     B   Fully Paid  
1                 car     C  Charged Off  
2      small_business     C   Fully Paid  
3               other     B   Fully Paid  
4  debt_consolidation     B  Charged Off  

Dataset Shape:
(10, 9)

Dataset Information:
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 10 entries, 0 to 9
Data columns (total 9 columns):
 #   Column          Non-Null Count  Dtype                                                                                            0   loan_amnt       10 non-null     int64 
 1   term            10 non-null     object
 2   int_rate        10 non-null     object
 3   annual_inc      10 non-null     int64 
 4   emp_length      10 non-null     object
 5   home_ownership  10 non-null     object
 6   purpose         10 non-null     object
 7   grade           10 non-null     object
 8   loan_status     10 non-null     object
dtypes: int64(2), object(7)
memory usage: 852.0+ bytes
None

Missing Values:
loan_amnt         0
term              0
int_rate          0
annual_inc        0
emp_length        0
home_ownership    0
purpose           0
grade             0
loan_status       0
dtype: int64

Descriptive Statistics:
          loan_amnt       term   int_rate    annual_inc  emp_length  \
count     10.000000  10.000000  10.000000     10.000000     10.0000   
mean    6590.000000  45.600000  14.331000  48045.200000      5.9000   
std     4355.443593  12.393547   3.982173  25565.469493      3.3483   
min     2400.000000  36.000000   7.900000  12252.000000      1.0000                                                     25%     3250.000000  36.000000  11.527500  31500.000000      3.2500   
50%     5000.000000  36.000000  14.380000  44500.000000      6.0000   
75%     9250.000000  60.000000  16.207500  61050.000000      8.7500   
max    15000.000000  60.000000  21.280000  95000.000000     10.0000   

       home_ownership    purpose      grade  loan_status  
count       10.000000  10.000000  10.000000    10.000000  
mean         1.000000   3.100000   1.700000     0.400000  
std          0.942809   2.330951   1.159502     0.516398  
min          0.000000   0.000000   0.000000     0.000000  
25%          0.000000   1.250000   1.000000     0.000000  
50%          1.000000   2.500000   1.500000     0.000000  
75%          2.000000   4.750000   2.000000     1.000000  
max          2.000000   7.000000   4.000000     1.000000  

Average Loan Amount:
6590.0

Average Annual Income:
48045.2

Average Interest Rate:
14.331
<>:24: SyntaxWarning: invalid escape sequence '\d'
<>:27: SyntaxWarning: invalid escape sequence '\d'
<>:24: SyntaxWarning: invalid escape sequence '\d'
<>:27: SyntaxWarning: invalid escape sequence '\d'
/tmp/ipykernel_587/1072533968.py:24: SyntaxWarning: invalid escape sequence '\d'
  loan_data['term'] = loan_data['term'].str.extract('(\d+)').astype(int)
/tmp/ipykernel_587/1072533968.py:27: SyntaxWarning: invalid escape sequence '\d'
  loan_data['emp_length'] = loan_data['emp_length'].str.extract('(\d+)')

print("\nLoan Status Counts:")
print(loan_data['loan_status'].value_counts())                                                                                         plt.figure(figsize=(6, 4))
sns.countplot(x='loan_status', data=loan_data)
plt.title('Loan Default Distribution')
plt.show()

plt.figure(figsize=(8, 5))
sns.histplot(loan_data['annual_inc'], bins=10, kde=True)
plt.title('Annual Income Distribution')
plt.show()

plt.figure(figsize=(8, 5))
sns.histplot(loan_data['loan_amnt'], bins=10, kde=True)
plt.title('Loan Amount Distribution')
plt.show()

plt.figure(figsize=(8, 5))
sns.scatterplot(
    x='annual_inc',
    y='loan_amnt',
    hue='loan_status',
    data=loan_data
)
plt.title('Income vs Loan Amount')
plt.show()

plt.figure(figsize=(8, 5))
sns.boxplot(
    x='loan_status',
    y='int_rate',
    data=loan_data
)
plt.title('Interest Rate vs Loan Status')
plt.show()

plt.figure(figsize=(10, 6))                                                                                                                 correlation = loan_data.corr()
sns.heatmap(correlation, annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()

     
Loan Status Counts:
loan_status
0    6
1    4
Name: count, dtype: int64                                                                                                             conditions = [
    (loan_data['int_rate'] < 10),
    (loan_data['int_rate'] >= 10) & (loan_data['int_rate'] < 18),
    (loan_data['int_rate'] >= 18)
]

risk_labels = ['Low Risk', 'Medium Risk', 'High Risk']

loan_data['risk_category'] = np.select(
    conditions,
    risk_labels,
    default='Unknown'
)

print("\nRisk Category Counts:")
print(loan_data['risk_category'].value_counts())


X = loan_data[['annual_inc', 'int_rate', 'term']]
y = loan_data['loan_amnt']

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

model = LinearRegression()

model.fit(X_train, y_train)

predictions = model.predict(X_test)

r2 = r2_score(y_test, predictions)
mae = mean_absolute_error(y_test, predictions)

print("\nModel Evaluation")
print("R2 Score:", r2)
print("Mean Absolute Error:", mae)


comparison = pd.DataFrame({
    'Actual': y_test.values,
    'Predicted': predictions
})

print("\nActual vs Predicted Loan Amount")
print(comparison)


fig1 = px.histogram(
    loan_data,
    x='loan_amnt',
    color='risk_category',
    title='Loan Amount Distribution'
)

fig1.show()

fig2 = px.scatter(
    loan_data,
    x='annual_inc',
    y='loan_amnt',
    color='risk_category',
    title='Income vs Loan Amount'
)

fig2.show()                                                                                                                                             fig3 = px.box(
    loan_data,
    x='loan_status',
    y='int_rate',
    color='loan_status',
    title='Interest Rate vs Loan Status'
)

fig3.show()

fig4 = px.bar(
    loan_data,
    x='purpose',
    color='risk_category',
    title='Loan Purpose vs Risk Category'
)

fig4.show()


print("\nProject Completed Successfully")
print("Insights:")
print("1. High interest rates indicate higher default risk")
print("2. Income influences loan amount approval")
print("3. Employment length affects repayment behavior")
print("4. Risk categories help identify potential defaulters")

     
Risk Category Counts:
risk_category
Medium Risk    7
High Risk      2
Low Risk       1
Name: count, dtype: int64
Model Evaluation
R2 Score: -16.845194038587035
Mean Absolute Error: 2918.004804494313

Actual vs Predicted Loan Amount
   Actual    Predicted
0    4000  5683.837228
1    2500  6652.172381
Project Completed Successfully
Insights:
1. High interest rates indicate higher default risk
2. Income influences loan amount approval
3. Employment length affects repayment behavior                                                                                 4. Risk categories help identify potential defaulters                 give a readme file for this project 
Loan Risk Analysis and Prediction System
Overview

This project is a Loan Risk Analysis and Prediction System developed using Python, Data Analysis, Data Visualization, and Machine Learning techniques.

The project performs:

Loan dataset preprocessing
Exploratory Data Analysis (EDA)
Risk categorization
Data visualization
Loan amount prediction using Linear Regression

The system helps analyze loan applicants and identify potential loan default risks based on:

Interest rate
Annual income
Employment length
Loan term
Technologies Used
Python
Pandas
NumPy
Matplotlib
Seaborn
Plotly Express
Scikit-learn
Project Features
Load and clean loan dataset
Handle missing values
Convert categorical data into numerical format
Analyze loan statistics
Visualize loan trends
Generate risk categories
Train a machine learning model
Predict loan amounts
Evaluate model performance
Dataset Description

The dataset contains the following attributes:

Column Name	Description
loan_amnt	Requested loan amount
term	Loan repayment period
int_rate	Interest rate
annual_inc	Applicant annual income
emp_length	Employment duration
home_ownership	Home ownership type
purpose	Loan purpose
grade	Loan grade
loan_status	Loan repayment status
Libraries Required

Install dependencies using pip:

pip install pandas numpy matplotlib seaborn plotly scikit-learn
Project Workflow
1. Import Required Libraries
import pandas as pd
import numpy as np
from io import StringIO
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
2. Load Dataset

The dataset is stored as CSV text and loaded using StringIO.

loan_data = pd.read_csv(StringIO(csv_data))
3. Dataset Inspection

The project checks:

Dataset shape
Data types
Missing values
Statistical summary
loan_data.head()
loan_data.info()
loan_data.describe()
loan_data.isnull().sum()
4. Data Preprocessing
Interest Rate Cleaning

Percentage symbols are removed and converted into float values.

loan_data['int_rate'] = loan_data['int_rate'].str.replace('%', '')
loan_data['int_rate'] = loan_data['int_rate'].astype(float)
Loan Term Conversion

Loan term values are converted into integers.

loan_data['term'] = loan_data['term'].str.extract(r'(\d+)').astype(int)
Employment Length Conversion

Employment duration is converted into numeric format.

loan_data['emp_length'] = loan_data['emp_length'].str.extract(r'(\d+)')
loan_data['emp_length'] = loan_data['emp_length'].fillna(0)
loan_data['emp_length'] = loan_data['emp_length'].astype(int)
Loan Status Encoding
Loan Status	Encoded Value
Fully Paid	0
Charged Off	1
loan_data['loan_status'] = loan_data['loan_status'].map({
    'Fully Paid': 0,
    'Charged Off': 1
})
Label Encoding

Categorical columns are encoded using LabelEncoder.

from sklearn.preprocessing import LabelEncoder

encoder = LabelEncoder()

Encoded columns:

home_ownership
purpose
grade
5. Exploratory Data Analysis (EDA)
Loan Status Distribution
sns.countplot(x='loan_status', data=loan_data)
Annual Income Distribution
sns.histplot(loan_data['annual_inc'], bins=10, kde=True)
Loan Amount Distribution
sns.histplot(loan_data['loan_amnt'], bins=10, kde=True)
Income vs Loan Amount
sns.scatterplot(
    x='annual_inc',
    y='loan_amnt',
    hue='loan_status',
    data=loan_data
)
Interest Rate vs Loan Status
sns.boxplot(
    x='loan_status',
    y='int_rate',
    data=loan_data
)
Correlation Heatmap
correlation = loan_data.corr()

sns.heatmap(
    correlation,
    annot=True,
    cmap='coolwarm'
)
6. Risk Categorization

Applicants are categorized based on interest rate.

Interest Rate	Risk Category
Below 10%	Low Risk
10% – 18%	Medium Risk
Above 18%	High Risk
loan_data['risk_category'] = np.select(
    conditions,
    risk_labels,
    default='Unknown'
)
Risk Category Output
Risk Category	Count
Medium Risk	7
High Risk	2
Low Risk	1
7. Machine Learning Model
Linear Regression Model

The model predicts loan amount based on:

Annual income
Interest rate
Loan term
Features
X = loan_data[['annual_inc', 'int_rate', 'term']]
Target
y = loan_data['loan_amnt']
Train-Test Split
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
Model Training
model = LinearRegression()
model.fit(X_train, y_train)
Prediction
predictions = model.predict(X_test)
8. Model Evaluation
Evaluation Metrics
R² Score
r2_score(y_test, predictions)
Mean Absolute Error
mean_absolute_error(y_test, predictions)
Model Results
Metric	Value
R² Score	-16.845
Mean Absolute Error	2918.00

Note: The dataset is very small (10 records), so model performance is not reliable.

9. Interactive Visualizations using Plotly
Histogram
px.histogram(
    loan_data,
    x='loan_amnt',
    color='risk_category'
)
Scatter Plot
px.scatter(
    loan_data,
    x='annual_inc',
    y='loan_amnt',
    color='risk_category'
)
Box Plot
px.box(
    loan_data,
    x='loan_status',
    y='int_rate',
    color='loan_status'
)
Bar Chart
px.bar(
    loan_data,
    x='purpose',
    color='risk_category'
)
Key Insights
Higher interest rates indicate greater loan default risk.
Annual income influences loan amount approval.
Employment length affects repayment capability.
Risk categorization helps identify potential defaulters.
Project Output

The project produces:

Cleaned loan dataset
Statistical analysis
Risk categorization
Data visualizations
Machine learning predictions
Model evaluation metrics
Future Enhancements
Use a larger real-world dataset
Improve prediction accuracy
Implement classification algorithms
Add dashboard interface
Deploy as a web application
Add deep learning models
How to Run
Step 1: Save the File

Save the Python code as:

loan_risk_analysis.py
Step 2: Run the Project
python loan_risk_analysis.py
Important Note

You may see this warning:

SyntaxWarning: invalid escape sequence '\d'

Fix it using raw strings:

str.extract(r'(\d+)')

instead of:

str.extract('(\d+)')
Sample Final Output
Project Completed Successfully

Insights:
1. High interest rates indicate higher default risk
2. Income influences loan amount approval
3. Employment length affects repayment behavior
4. Risk categories help identify potential defaulters
Author
