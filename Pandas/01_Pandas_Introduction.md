# Pandas Documentation
## A Complete Guide for Data Science Students

**Author:** Data Science Tutor  
**Version:** 1.0  
**Library:** pandas >= 1.5.x  
**Python Version:** 3.8+

---

## Table of Contents

1. [Installing Pandas](#1-installing-pandas)
2. [Importing Pandas](#2-importing-pandas)
3. [Understanding Series and DataFrames](#3-understanding-series-and-dataframes)
4. [Creating DataFrames](#4-creating-dataframes)
5. [Viewing Data](#5-viewing-data)
6. [Shape and Indexing](#6-shape-and-indexing)
7. [Selecting Data](#7-selecting-data)
8. [Column and Row Selection](#8-column-and-row-selection)
9. [Filtering with Conditions](#9-filtering-with-conditions)
10. [Handling Missing Data](#10-handling-missing-data)
11. [Handling Duplicates](#11-handling-duplicates)
12. [Renaming Columns and Index](#12-renaming-columns-and-index)
13. [Changing Data Types](#13-changing-data-types)
14. [Replacing Values](#14-replacing-values)
15. [Data Transformation](#15-data-transformation)
16. [Grouping and Aggregation](#16-grouping-and-aggregation)
17. [Merging, Joining, and Concatenating](#17-merging-joining-and-concatenating)
18. [Working with Time Series](#18-working-with-time-series)
19. [Input and Output Operations](#19-input-and-output-operations)

---

## 1. Installing Pandas

Pandas is not part of Python's standard library. You need to install it separately using a package manager. The most common ways to install pandas are through `pip` or `conda`.

### Using pip

pip is the default package installer for Python. If you have Python installed, pip is usually already available.

```bash
pip install pandas
```

To install a specific version:

```bash
pip install pandas==2.0.3
```

To upgrade an existing installation:

```bash
pip install --upgrade pandas
```

### Using conda (Anaconda / Miniconda)

If you are working inside an Anaconda environment, use conda instead:

```bash
conda install pandas
```

### Installing in a Virtual Environment

It is strongly recommended to work inside a virtual environment to avoid dependency conflicts across projects.

```bash
# Create a virtual environment
python -m venv my_env

# Activate it (Windows)
my_env\Scripts\activate

# Activate it (macOS / Linux)
source my_env/bin/activate

# Now install pandas
pip install pandas
```

### Verifying the Installation

After installation, confirm that pandas is installed correctly:

```python
import pandas as pd
print(pd.__version__)
```

If this prints a version number without error, your installation is successful.

### Common Dependencies

Pandas relies on a few other libraries internally. These are installed automatically when you run `pip install pandas`, but it is helpful to know about them:

- **NumPy** - for numerical operations on arrays
- **python-dateutil** - for date parsing
- **pytz** - for timezone handling

For reading Excel files, you will additionally need:

```bash
pip install openpyxl    # For .xlsx files
pip install xlrd        # For older .xls files
```

---

## 2. Importing Pandas

Once installed, you import pandas into your Python script or notebook before using it.

### Standard Import Convention

The universally accepted convention in the data science community is to import pandas with the alias `pd`. You should always follow this convention so your code is readable to other developers.

```python
import pandas as pd
```

### Importing NumPy Alongside Pandas

In most data science workflows, pandas and NumPy are used together. NumPy is commonly imported as `np`.

```python
import pandas as pd
import numpy as np
```

### Checking Installed Version

```python
import pandas as pd

print("Pandas version:", pd.__version__)
```

### Suppressing Warnings (Optional)

In some environments, pandas may display deprecation warnings. You can suppress them like this:

```python
import warnings
warnings.filterwarnings('ignore')

import pandas as pd
```

This is optional and should only be done if warnings are interfering with your workflow. In production code, warnings should never be suppressed without understanding their cause.

---

## 3. Understanding Series and DataFrames

Pandas provides two core data structures: **Series** and **DataFrame**. Everything in pandas revolves around these two objects. Understanding them deeply is the foundation of all data work.

### Series

A Series is a one-dimensional labeled array. It can hold any data type: integers, floats, strings, Python objects, and more. Think of it as a single column in a spreadsheet.

Every Series has two components:
- **Values** - the actual data
- **Index** - the label for each value (defaults to 0, 1, 2, ... if not specified)

```python
import pandas as pd

# Creating a Series from a list
scores = pd.Series([85, 90, 78, 92, 88])
print(scores)
```

Output:
```
0    85
1    90
2    78
3    92
4    88
dtype: int64
```

The left column is the index, and the right column is the data.

You can provide your own index:

```python
scores = pd.Series([85, 90, 78, 92, 88], index=['Alice', 'Bob', 'Charlie', 'Diana', 'Edward'])
print(scores)
```

Output:
```
Alice      85
Bob        90
Charlie    78
Diana      92
Edward     88
dtype: int64
```

You can access a value using its label:

```python
print(scores['Alice'])   # Output: 85
print(scores['Diana'])   # Output: 92
```

A Series also has a name attribute:

```python
scores.name = 'Math Score'
print(scores.name)       # Output: Math Score
```

### DataFrame

A DataFrame is a two-dimensional labeled data structure. It is the primary object you will work with in pandas. Think of it as a spreadsheet or a SQL table - it has rows and columns.

A DataFrame is essentially a collection of Series objects that share the same index.

```python
import pandas as pd

data = {
    'Name':   ['Alice', 'Bob', 'Charlie', 'Diana'],
    'Age':    [24, 27, 22, 30],
    'City':   ['Chennai', 'Mumbai', 'Delhi', 'Bangalore'],
    'Score':  [85, 90, 78, 92]
}

df = pd.DataFrame(data)
print(df)
```

Output:
```
      Name  Age       City  Score
0    Alice   24    Chennai     85
1      Bob   27     Mumbai     90
2  Charlie   22      Delhi     78
3    Diana   30  Bangalore     92
```

In this DataFrame:
- Each column is a Series
- All columns share the same row index (0, 1, 2, 3)
- Each column can hold a different data type

### Key Differences Between Series and DataFrame

| Property         | Series              | DataFrame                    |
|------------------|---------------------|------------------------------|
| Dimensions       | 1D                  | 2D                           |
| Structure        | Single column       | Multiple columns             |
| Index            | Row labels          | Row labels + Column labels   |
| Analogy          | A single spreadsheet column | A full spreadsheet   |

---

## 4. Creating DataFrames

There are multiple ways to create a DataFrame. The method you choose depends on where your data is coming from.

### From a Dictionary of Lists

This is the most common way to create a DataFrame manually. Each key becomes a column name, and each list becomes the column's data.

```python
import pandas as pd

data = {
    'Product':  ['Laptop', 'Mouse', 'Keyboard', 'Monitor', 'Webcam'],
    'Price':    [75000, 800, 1500, 18000, 3000],
    'Quantity': [50, 200, 150, 80, 120],
    'Category': ['Electronics', 'Accessories', 'Accessories', 'Electronics', 'Accessories']
}

df = pd.DataFrame(data)
print(df)
```

Output:
```
    Product  Price  Quantity     Category
0    Laptop  75000        50  Electronics
1     Mouse    800       200  Accessories
2  Keyboard   1500       150  Accessories
3   Monitor  18000        80  Electronics
4    Webcam   3000       120  Accessories
```

### From a List of Dictionaries

Each dictionary represents one row. The keys become column names.

```python
rows = [
    {'Name': 'Alice', 'Age': 24, 'Department': 'HR'},
    {'Name': 'Bob',   'Age': 27, 'Department': 'Engineering'},
    {'Name': 'Clara', 'Age': 31, 'Department': 'Marketing'}
]

df = pd.DataFrame(rows)
print(df)
```

### From a NumPy Array

```python
import numpy as np
import pandas as pd

array = np.array([[10, 20, 30],
                  [40, 50, 60],
                  [70, 80, 90]])

df = pd.DataFrame(array, columns=['A', 'B', 'C'])
print(df)
```

### With a Custom Index

By default, the index is 0, 1, 2, ... You can provide your own:

```python
data = {
    'Revenue': [120000, 98000, 145000, 87000],
    'Expenses': [80000, 72000, 95000, 60000]
}

df = pd.DataFrame(data, index=['Q1', 'Q2', 'Q3', 'Q4'])
print(df)
```

Output:
```
    Revenue  Expenses
Q1   120000     80000
Q2    98000     72000
Q3   145000     95000
Q4    87000     60000
```

### Creating an Empty DataFrame

Sometimes you need to create an empty DataFrame first and add data later.

```python
df = pd.DataFrame(columns=['Name', 'Age', 'Score'])
print(df)
print(df.shape)   # Output: (0, 3)
```

### Creating a DataFrame from a CSV File (Real World)

In real-world projects, you will almost never type data manually. You will read it from a file. This is covered in detail in the Input and Output section, but here is a quick preview:

```python
df = pd.read_csv('sales_data.csv')
print(df.head())
```

---

## 5. Viewing Data

Once you have a DataFrame, the first thing you should do is explore it - understand its structure, size, and content. Pandas provides several methods for this.

### head() and tail()

`head(n)` returns the first n rows. The default is 5.  
`tail(n)` returns the last n rows. The default is 5.

```python
import pandas as pd

df = pd.read_csv('employees.csv')

print(df.head())     # First 5 rows
print(df.head(10))   # First 10 rows
print(df.tail())     # Last 5 rows
print(df.tail(3))    # Last 3 rows
```

### info()

`info()` gives a concise summary of the DataFrame: number of rows, columns, data types, and memory usage. It is the first method you should call on any new dataset.

```python
print(df.info())
```

Output:
```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 1000 entries, 0 to 999
Data columns (total 6 columns):
 #   Column      Non-Null Count  Dtype  
---  ------      --------------  -----  
 0   EmployeeID  1000 non-null   int64  
 1   Name        1000 non-null   object 
 2   Department  998 non-null    object 
 3   Salary      995 non-null    float64
 4   JoinDate    1000 non-null   object 
 5   IsActive    1000 non-null   bool   
dtypes: bool(1), float64(1), int64(1), object(3)
memory usage: 40.0+ KB
```

From this output you can immediately see which columns have missing values (Department has 2 missing, Salary has 5 missing).

### describe()

`describe()` generates statistical summary of all numerical columns: count, mean, standard deviation, minimum, quartiles, and maximum.

```python
print(df.describe())
```

To include non-numerical columns:

```python
print(df.describe(include='all'))
```

### dtypes

Returns the data type of each column.

```python
print(df.dtypes)
```

### columns and index

```python
print(df.columns)   # Column names
print(df.index)     # Row index
```

### value_counts()

Used on a single column to see the count of each unique value. Very useful for categorical data.

```python
print(df['Department'].value_counts())
```

Output:
```
Engineering    320
Sales          215
HR             180
Marketing      160
Finance        125
dtype: int64
```

### nunique()

Returns the number of unique values in each column.

```python
print(df.nunique())
```

---

## 6. Shape and Indexing

### Shape

The `shape` attribute returns a tuple: (number of rows, number of columns).

```python
import pandas as pd

df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age':  [24, 27, 22],
    'City': ['Chennai', 'Mumbai', 'Delhi']
})

print(df.shape)         # Output: (3, 3)
print(df.shape[0])      # Number of rows: 3
print(df.shape[1])      # Number of columns: 3
```

### len()

Returns the number of rows only:

```python
print(len(df))          # Output: 3
```

### The Index

The index is the row label. By default it is a RangeIndex (0, 1, 2, ...). You can set any column as the index.

```python
df = df.set_index('Name')
print(df)
```

Output:
```
         Age     City
Name                 
Alice     24  Chennai
Bob       27   Mumbai
Charlie   22    Delhi
```

To reset back to the default numeric index:

```python
df = df.reset_index()
print(df)
```

### iloc - Integer Location Based Indexing

`iloc` selects rows and columns by their integer position (0-based). It works exactly like Python list slicing.

```python
# Single row by position
print(df.iloc[0])        # First row

# Multiple rows
print(df.iloc[0:3])      # First 3 rows (rows 0, 1, 2)

# Specific row and column
print(df.iloc[1, 2])     # Row at position 1, Column at position 2

# Last row
print(df.iloc[-1])

# Select specific rows and columns by position
print(df.iloc[[0, 2], [0, 1]])   # Rows 0 and 2, Columns 0 and 1
```

### loc - Label Based Indexing

`loc` selects rows and columns by their label (name). It is inclusive on both ends.

```python
# If the index is default numeric
print(df.loc[0])          # Row with label 0
print(df.loc[0:2])        # Rows with labels 0, 1, 2 (inclusive)

# Specific row and column by label
print(df.loc[0, 'Name'])  # Row 0, column 'Name'

# Multiple columns
print(df.loc[:, ['Name', 'Age']])   # All rows, columns Name and Age

# If the index is set to a custom column (e.g., Name)
df2 = df.set_index('Name')
print(df2.loc['Alice'])             # Row where index == 'Alice'
```

### iloc vs loc Summary

| Feature       | iloc                          | loc                            |
|---------------|-------------------------------|--------------------------------|
| Based on      | Integer position              | Label / Name                   |
| End inclusive | No (like Python slicing)      | Yes                            |
| Use case      | Positional access             | Named access                   |

---

## 7. Selecting Data

Selecting the right subset of data is one of the most frequent operations in data analysis. Pandas provides several ways to do this.

### Selecting a Single Column

This returns a Series:

```python
import pandas as pd

df = pd.read_csv('employees.csv')

salary_series = df['Salary']
print(type(salary_series))   # <class 'pandas.core.series.Series'>
print(salary_series.head())
```

### Selecting Multiple Columns

This returns a DataFrame. Note the double square brackets:

```python
subset = df[['Name', 'Department', 'Salary']]
print(subset.head())
```

### Selecting Rows by Condition

```python
high_earners = df[df['Salary'] > 80000]
print(high_earners.head())
```

### at and iat - Fast Scalar Access

When you need to access a single specific cell, `at` and `iat` are faster than `loc` and `iloc`.

```python
# at - label based (single value)
print(df.at[0, 'Name'])

# iat - integer position based (single value)
print(df.iat[0, 1])
```

---

## 8. Column and Row Selection

### Selecting Columns

Selecting a single column returns a Series:

```python
print(df['Name'])           # Returns Series
```

Selecting multiple columns returns a DataFrame:

```python
print(df[['Name', 'Salary', 'Department']])   # Returns DataFrame
```

### Adding a New Column

```python
df['AnnualBonus'] = df['Salary'] * 0.10
print(df[['Name', 'Salary', 'AnnualBonus']].head())
```

### Dropping Columns

```python
# Drop one column (does not modify original unless inplace=True)
df_clean = df.drop(columns=['AnnualBonus'])

# Drop multiple columns
df_clean = df.drop(columns=['AnnualBonus', 'EmployeeID'])

# In-place modification
df.drop(columns=['AnnualBonus'], inplace=True)
```

### Selecting Rows

Using a boolean condition:

```python
senior_employees = df[df['Experience'] > 5]
```

Using `.loc` for label-based selection:

```python
# Select rows 10 to 20 (inclusive)
subset = df.loc[10:20]
```

Using `.iloc` for position-based selection:

```python
# Select rows at positions 0, 5, 10
subset = df.iloc[[0, 5, 10]]
```

### Dropping Rows

```python
# Drop row at index 0
df = df.drop(index=0)

# Drop multiple rows
df = df.drop(index=[0, 1, 5])

# Reset the index after dropping
df = df.reset_index(drop=True)
```

The `drop=True` argument in `reset_index` ensures the old index is not added back as a column.

---

## 9. Filtering with Conditions

Filtering is the process of selecting rows that meet certain criteria. It is one of the most powerful features of pandas.

### Single Condition

```python
import pandas as pd

df = pd.read_csv('employees.csv')

# Employees in the Engineering department
engineers = df[df['Department'] == 'Engineering']

# Employees with salary greater than 60000
high_salary = df[df['Salary'] > 60000]

# Employees who are active
active = df[df['IsActive'] == True]
```

### Multiple Conditions with AND (&)

Each condition must be wrapped in parentheses:

```python
# Employees in Engineering AND salary > 70000
result = df[(df['Department'] == 'Engineering') & (df['Salary'] > 70000)]
```

### Multiple Conditions with OR (|)

```python
# Employees in HR OR Finance
result = df[(df['Department'] == 'HR') | (df['Department'] == 'Finance')]
```

### Negation with NOT (~)

```python
# Employees NOT in Sales
result = df[~(df['Department'] == 'Sales')]
```

### Using isin() for Multiple Values

Instead of chaining multiple OR conditions, use `.isin()`:

```python
departments = ['HR', 'Finance', 'Marketing']
result = df[df['Department'].isin(departments)]
```

To negate:

```python
result = df[~df['Department'].isin(departments)]
```

### Using between() for Range Filtering

```python
# Salary between 50000 and 80000 (inclusive)
result = df[df['Salary'].between(50000, 80000)]
```

### String Filtering with str Methods

```python
# Names that start with 'A'
result = df[df['Name'].str.startswith('A')]

# Names that contain 'kumar' (case insensitive)
result = df[df['Name'].str.contains('kumar', case=False)]

# Email addresses that end with @gmail.com
result = df[df['Email'].str.endswith('@gmail.com')]
```

### Using query() for Readable Filtering

The `.query()` method allows you to write filter conditions as a string, which is easier to read for complex conditions:

```python
result = df.query("Department == 'Engineering' and Salary > 70000")
result = df.query("Age >= 25 and Age <= 35")
result = df.query("City in ['Chennai', 'Mumbai', 'Delhi']")
```

---

## 10. Handling Missing Data

Real-world datasets almost always contain missing values. In pandas, missing values are represented as `NaN` (Not a Number) for numerical data, or `None` for object data. Handling them correctly is critical for accurate analysis.

### Detecting Missing Values

```python
import pandas as pd
import numpy as np

df = pd.read_csv('customers.csv')

# Check if each cell is missing
print(df.isnull())       # Returns boolean DataFrame

# Total missing values per column
print(df.isnull().sum())

# Percentage of missing values per column
print((df.isnull().sum() / len(df)) * 100)

# Check if any value is missing in a column
print(df['Email'].isnull().any())

# Rows where any column has a missing value
print(df[df.isnull().any(axis=1)])
```

### Dropping Missing Values

```python
# Drop rows where ANY column has a missing value
df_clean = df.dropna()

# Drop rows where ALL columns are missing
df_clean = df.dropna(how='all')

# Drop rows where specific columns have missing values
df_clean = df.dropna(subset=['Email', 'Phone'])

# Drop columns that have any missing value
df_clean = df.dropna(axis=1)

# Drop columns where more than 50% of values are missing
threshold = len(df) * 0.5
df_clean = df.dropna(thresh=threshold, axis=1)
```

### Filling Missing Values

Rather than dropping rows, you can fill them in:

```python
# Fill all missing values with a single value
df['Salary'] = df['Salary'].fillna(0)

# Fill with the mean of the column
df['Age'] = df['Age'].fillna(df['Age'].mean())

# Fill with the median (better for skewed data)
df['Salary'] = df['Salary'].fillna(df['Salary'].median())

# Fill with the mode (most frequent - good for categorical data)
df['City'] = df['City'].fillna(df['City'].mode()[0])

# Forward fill - use the previous row's value
df['Temperature'] = df['Temperature'].fillna(method='ffill')

# Backward fill - use the next row's value
df['Temperature'] = df['Temperature'].fillna(method='bfill')

# Fill different columns with different values
df.fillna({'Age': df['Age'].median(), 'City': 'Unknown', 'Salary': 0}, inplace=True)
```

### Replacing NaN with np.nan

Sometimes you may encounter missing values stored as strings like 'N/A', 'None', 'unknown', or empty strings. You should convert them to actual NaN first:

```python
df.replace('N/A', np.nan, inplace=True)
df.replace('', np.nan, inplace=True)
df.replace(['None', 'unknown', '-'], np.nan, inplace=True)
```

### Checking After Cleaning

```python
print(df.isnull().sum())   # Should be all zeros if fully cleaned
```

---

## 11. Handling Duplicates

Duplicate rows can arise from data collection errors, merging datasets, or repeated entries. They can distort analysis if not handled.

### Detecting Duplicates

```python
import pandas as pd

df = pd.read_csv('orders.csv')

# Boolean Series: True for every duplicate row
print(df.duplicated())

# Count total duplicate rows
print(df.duplicated().sum())

# Show all duplicate rows
print(df[df.duplicated()])

# Show duplicates including the first occurrence
print(df[df.duplicated(keep=False)])

# Check duplicates based on specific columns only
print(df.duplicated(subset=['CustomerID', 'OrderDate']))
```

The `keep` parameter:
- `keep='first'` (default) - marks duplicates except the first occurrence as True
- `keep='last'` - marks duplicates except the last occurrence as True
- `keep=False` - marks all duplicates as True

### Removing Duplicates

```python
# Remove duplicate rows, keeping first occurrence
df_clean = df.drop_duplicates()

# Keep last occurrence instead
df_clean = df.drop_duplicates(keep='last')

# Remove duplicates based on specific columns
df_clean = df.drop_duplicates(subset=['CustomerID', 'ProductID'])

# In-place removal
df.drop_duplicates(inplace=True)

# Reset index after removing duplicates
df = df.drop_duplicates().reset_index(drop=True)
```

---

## 12. Renaming Columns and Index

Column names in raw datasets are often poorly named - with spaces, mixed case, or unclear abbreviations. Renaming makes your data easier to work with.

### Renaming Specific Columns with a Dictionary

```python
import pandas as pd

df = pd.read_csv('raw_data.csv')

# Rename specific columns
df = df.rename(columns={
    'emp_id':    'EmployeeID',
    'emp_name':  'FullName',
    'dept':      'Department',
    'sal':       'Salary'
})

print(df.columns)
```

### Renaming the Index

```python
df = df.rename(index={0: 'First', 1: 'Second', 2: 'Third'})
```

### Renaming All Columns at Once

If you want to replace all column names, assign a list directly:

```python
df.columns = ['ID', 'Name', 'Department', 'Salary', 'JoinDate']
```

The list must have exactly the same number of elements as the number of columns.

### Standardizing Column Names

A very common preprocessing step is to clean column names - make them lowercase, replace spaces with underscores, and remove special characters:

```python
# Convert all column names to lowercase with underscores
df.columns = df.columns.str.lower().str.replace(' ', '_').str.strip()

print(df.columns)
```

For example, 'Employee Name' becomes 'employee_name', 'Join Date' becomes 'join_date'.

### Renaming the Index Name

```python
df.index.name = 'RecordNumber'
```

---

## 13. Changing Data Types

When you load a dataset, pandas assigns data types automatically. These automatic types are often wrong - dates loaded as strings, booleans loaded as integers, etc. Correcting data types is an essential preprocessing step.

### Checking Current Data Types

```python
print(df.dtypes)
```

Common pandas data types:
- `int64` - integers
- `float64` - decimal numbers
- `object` - strings or mixed types
- `bool` - True/False
- `datetime64` - dates and times
- `category` - categorical data (efficient for repeated strings)

### Converting Data Types with astype()

```python
import pandas as pd

# Convert Salary from float to integer
df['Salary'] = df['Salary'].astype(int)

# Convert EmployeeID from integer to string
df['EmployeeID'] = df['EmployeeID'].astype(str)

# Convert a column to float
df['Price'] = df['Price'].astype(float)

# Convert to category (saves memory for low-cardinality string columns)
df['Department'] = df['Department'].astype('category')

# Convert to boolean
df['IsActive'] = df['IsActive'].astype(bool)
```

### Converting to Datetime

This is extremely important for time series analysis. Never leave date columns as `object` dtype:

```python
# Convert a string column to datetime
df['JoinDate'] = pd.to_datetime(df['JoinDate'])

# With a specific format
df['OrderDate'] = pd.to_datetime(df['OrderDate'], format='%d-%m-%Y')

# Handling errors gracefully (converts invalid values to NaT instead of raising an error)
df['JoinDate'] = pd.to_datetime(df['JoinDate'], errors='coerce')
```

### Converting to Numeric

```python
# Convert a column to numeric, setting non-numeric to NaN
df['Revenue'] = pd.to_numeric(df['Revenue'], errors='coerce')
```

### Memory Optimization with Downcasting

```python
# Downcast integer to smallest possible integer type
df['Age'] = pd.to_numeric(df['Age'], downcast='integer')

# Downcast float
df['Score'] = pd.to_numeric(df['Score'], downcast='float')
```

---

## 14. Replacing Values

The `.replace()` method allows you to substitute specific values in your DataFrame. This is commonly used to clean incorrect data, standardize labels, or encode categorical variables.

### Replacing a Single Value

```python
import pandas as pd

# Replace all occurrences of 'M' with 'Male'
df['Gender'] = df['Gender'].replace('M', 'Male')
```

### Replacing Multiple Values with a Dictionary

```python
df['Gender'] = df['Gender'].replace({'M': 'Male', 'F': 'Female', 'U': 'Unknown'})

df['Status'] = df['Status'].replace({0: 'Inactive', 1: 'Active'})
```

### Replacing Values Across the Entire DataFrame

```python
# Replace 'N/A' string anywhere in the DataFrame with actual NaN
import numpy as np
df.replace('N/A', np.nan, inplace=True)
```

### Replacing a List of Values with a Single Value

```python
df['City'].replace(['Bombay', 'Madras', 'Calcutta'], ['Mumbai', 'Chennai', 'Kolkata'], inplace=True)
```

### Using map() for Series-Level Replacement

`map()` is similar to `replace()` but works on a Series and maps each value through a dictionary or function:

```python
grade_map = {'A': 4.0, 'B': 3.0, 'C': 2.0, 'D': 1.0, 'F': 0.0}
df['GradePoint'] = df['Grade'].map(grade_map)
```

Any values not found in the dictionary are replaced with NaN.

### Using where() and mask()

`where()` keeps values where the condition is True and replaces the rest:

```python
# Replace negative values with 0
df['Quantity'] = df['Quantity'].where(df['Quantity'] >= 0, 0)
```

`mask()` is the inverse - it replaces values where the condition is True:

```python
# Replace values greater than 1000 with 1000 (capping)
df['Score'] = df['Score'].mask(df['Score'] > 1000, 1000)
```

---

## 15. Data Transformation

Data transformation involves reshaping, computing new columns, applying functions, and preparing data for analysis or modeling.

### apply() - Apply a Function to Rows or Columns

`apply()` is one of the most powerful transformation tools. It applies a function along an axis.

```python
import pandas as pd

# Apply a function to a single column
df['Salary_INR'] = df['Salary_USD'].apply(lambda x: x * 83.5)

# Apply a named function
def categorize_salary(salary):
    if salary < 30000:
        return 'Low'
    elif salary < 70000:
        return 'Medium'
    else:
        return 'High'

df['SalaryCategory'] = df['Salary'].apply(categorize_salary)

# Apply to each row (axis=1)
df['FullName'] = df.apply(lambda row: row['FirstName'] + ' ' + row['LastName'], axis=1)
```

### applymap() / map() - Element-wise Operations

For applying a function to every single element in the DataFrame:

```python
# Convert all string values to uppercase
df_str = df[['Name', 'City']].applymap(str.upper)

# In pandas 2.x, applymap() is renamed to map()
df_str = df[['Name', 'City']].map(str.upper)
```

### Creating New Columns from Existing Ones

```python
# Profit column from Revenue and Cost
df['Profit'] = df['Revenue'] - df['Cost']

# Profit margin percentage
df['ProfitMargin'] = (df['Profit'] / df['Revenue']) * 100

# Age group
df['AgeGroup'] = pd.cut(df['Age'], bins=[0, 18, 30, 45, 60, 100],
                         labels=['Under 18', '18-30', '31-45', '46-60', 'Above 60'])
```

### pd.cut() and pd.qcut() - Binning

`pd.cut()` divides data into fixed-width bins:

```python
# Divide scores into 5 equal-width bins
df['ScoreGrade'] = pd.cut(df['Score'], bins=5, labels=['F', 'D', 'C', 'B', 'A'])
```

`pd.qcut()` divides data into quantile-based bins (equal-frequency):

```python
# Divide into 4 equal-frequency quartiles
df['SalaryQuartile'] = pd.qcut(df['Salary'], q=4, labels=['Q1', 'Q2', 'Q3', 'Q4'])
```

### Sorting Data

```python
# Sort by a single column (ascending by default)
df = df.sort_values('Salary')

# Sort descending
df = df.sort_values('Salary', ascending=False)

# Sort by multiple columns
df = df.sort_values(['Department', 'Salary'], ascending=[True, False])

# Sort by index
df = df.sort_index()
```

### pivot_table() - Reshape Data

Pivot tables summarize data much like in Excel:

```python
pivot = df.pivot_table(
    values='Salary',
    index='Department',
    columns='Gender',
    aggfunc='mean',
    fill_value=0
)
print(pivot)
```

### melt() - Unpivot Wide to Long Format

```python
# Convert wide format to long format
df_long = df.melt(id_vars=['EmployeeID', 'Name'],
                  value_vars=['Q1_Sales', 'Q2_Sales', 'Q3_Sales', 'Q4_Sales'],
                  var_name='Quarter',
                  value_name='Sales')
```

### String Transformations on Columns

```python
df['Name'] = df['Name'].str.strip()        # Remove leading/trailing spaces
df['Name'] = df['Name'].str.title()        # Title Case
df['Email'] = df['Email'].str.lower()      # lowercase
df['Phone'] = df['Phone'].str.replace('-', '', regex=False)   # Remove dashes
```

---

## 16. Grouping and Aggregation

Grouping is the process of splitting data into groups based on some criteria, and aggregation summarizes each group using functions like sum, mean, count, etc. This is equivalent to GROUP BY in SQL.

### Basic groupby()

```python
import pandas as pd

df = pd.read_csv('sales.csv')

# Total sales by region
region_sales = df.groupby('Region')['Sales'].sum()
print(region_sales)

# Average salary by department
dept_avg = df.groupby('Department')['Salary'].mean()
print(dept_avg)
```

### Multiple Aggregation Functions with agg()

```python
# Multiple statistics for one column
result = df.groupby('Department')['Salary'].agg(['mean', 'median', 'min', 'max', 'count'])
print(result)

# Different aggregations for different columns
result = df.groupby('Department').agg({
    'Salary':   ['mean', 'max'],
    'Age':      'mean',
    'EmployeeID': 'count'
})
print(result)
```

### Grouping by Multiple Columns

```python
result = df.groupby(['Region', 'Product'])['Sales'].sum()
print(result)
```

### Resetting the Index After groupby

After groupby, the grouped column becomes the index. Use `reset_index()` to get a flat DataFrame back:

```python
result = df.groupby('Department')['Salary'].mean().reset_index()
result.columns = ['Department', 'AvgSalary']
print(result)
```

### Custom Aggregation with Named Aggregation

```python
result = df.groupby('Department').agg(
    TotalSalary   = ('Salary', 'sum'),
    AvgSalary     = ('Salary', 'mean'),
    HeadCount     = ('EmployeeID', 'count'),
    MaxExperience = ('Experience', 'max')
)
print(result)
```

### Transform vs Aggregate

`agg()` reduces rows. `transform()` returns a result with the same shape as the original DataFrame - useful for creating group-level features.

```python
# Add a column with each employee's department average salary
df['DeptAvgSalary'] = df.groupby('Department')['Salary'].transform('mean')

# Add a column with normalized salary within department
df['SalaryNormalized'] = df.groupby('Department')['Salary'].transform(
    lambda x: (x - x.mean()) / x.std()
)
```

### filter() on Groups

Keep only the groups that meet a condition:

```python
# Keep only departments that have more than 50 employees
large_depts = df.groupby('Department').filter(lambda x: len(x) > 50)
```

---

## 17. Merging, Joining, and Concatenating

When working with real data, you rarely have everything in a single table. You need to combine multiple DataFrames. Pandas provides three main operations: `merge`, `join`, and `concat`.

### pd.concat() - Stack DataFrames

`concat` is used to stack DataFrames vertically (row-wise) or horizontally (column-wise).

```python
import pandas as pd

df1 = pd.read_csv('sales_q1.csv')
df2 = pd.read_csv('sales_q2.csv')
df3 = pd.read_csv('sales_q3.csv')

# Stack vertically (all must have same columns)
combined = pd.concat([df1, df2, df3], ignore_index=True)

# Stack horizontally (all must have same number of rows)
combined = pd.concat([df1, df2], axis=1)
```

The `ignore_index=True` parameter resets the index in the combined DataFrame, which is almost always what you want.

### pd.merge() - SQL-Style Joins

`merge` is the most powerful way to combine DataFrames. It works exactly like SQL JOINs.

```python
employees = pd.read_csv('employees.csv')
departments = pd.read_csv('departments.csv')
```

#### Inner Join (default)

Returns only rows where the key exists in both DataFrames:

```python
result = pd.merge(employees, departments, on='DepartmentID', how='inner')
```

#### Left Join

Returns all rows from the left DataFrame. If no match in the right, fills with NaN:

```python
result = pd.merge(employees, departments, on='DepartmentID', how='left')
```

#### Right Join

Returns all rows from the right DataFrame:

```python
result = pd.merge(employees, departments, on='DepartmentID', how='right')
```

#### Outer Join (Full Join)

Returns all rows from both DataFrames:

```python
result = pd.merge(employees, departments, on='DepartmentID', how='outer')
```

#### Joining on Different Column Names

If the key column has different names in each DataFrame:

```python
result = pd.merge(employees, departments,
                  left_on='DeptID',
                  right_on='DepartmentID',
                  how='inner')
```

#### Joining on Multiple Keys

```python
result = pd.merge(orders, products,
                  on=['ProductID', 'CategoryID'],
                  how='inner')
```

### join() - Index-Based Join

`join()` merges on the index rather than on a column:

```python
df1 = df1.set_index('EmployeeID')
df2 = df2.set_index('EmployeeID')

result = df1.join(df2, how='inner')
```

### Practical Example: Building an Analytical Dataset

```python
# Load separate tables
customers = pd.read_csv('customers.csv')
orders    = pd.read_csv('orders.csv')
products  = pd.read_csv('products.csv')

# Merge step by step
orders_with_customers = pd.merge(orders, customers, on='CustomerID', how='left')
full_data = pd.merge(orders_with_customers, products, on='ProductID', how='left')

print(full_data.head())
print(full_data.shape)
```

---

## 18. Working with Time Series

Time series data is data that is indexed or sorted by time. Examples include stock prices, weather data, website traffic logs, and sensor readings. Pandas has excellent built-in support for time series.

### Converting to Datetime

The first step in any time series work is ensuring your date column is properly typed:

```python
import pandas as pd

df = pd.read_csv('stock_prices.csv')

df['Date'] = pd.to_datetime(df['Date'])

print(df['Date'].dtype)   # Should print: datetime64[ns]
```

### Setting Date as Index

For time series work, it is best practice to make the date column the index:

```python
df = df.set_index('Date')
df = df.sort_index()    # Always sort by date
print(df.head())
```

### Extracting Date Components

Once a column is in datetime format, you can extract individual components:

```python
df['Year']       = df['Date'].dt.year
df['Month']      = df['Date'].dt.month
df['Day']        = df['Date'].dt.day
df['DayOfWeek']  = df['Date'].dt.dayofweek      # 0=Monday, 6=Sunday
df['DayName']    = df['Date'].dt.day_name()
df['Quarter']    = df['Date'].dt.quarter
df['WeekNumber'] = df['Date'].dt.isocalendar().week
df['Hour']       = df['Date'].dt.hour
```

### Selecting Date Ranges

When the index is a datetime, you can slice by date strings:

```python
# Rows for year 2023
data_2023 = df.loc['2023']

# Rows for January 2023
data_jan = df.loc['2023-01']

# Rows between two dates
data_range = df.loc['2023-01-01':'2023-06-30']
```

### Resampling - Changing Frequency

Resampling is the process of changing the frequency of your data. For example, converting daily data to monthly data.

```python
# Monthly average of daily data
monthly_avg = df['Price'].resample('M').mean()

# Monthly sum
monthly_sum = df['Revenue'].resample('M').sum()

# Weekly maximum
weekly_max = df['Price'].resample('W').max()

# Quarterly total
quarterly = df['Sales'].resample('Q').sum()
```

Common frequency strings:
- `'D'` - calendar day
- `'B'` - business day
- `'W'` - week
- `'M'` - month end
- `'MS'` - month start
- `'Q'` - quarter end
- `'A'` or `'Y'` - year end
- `'H'` - hour

### Rolling Window Calculations

A rolling window applies a function over a sliding window of rows. This is used to compute moving averages and similar statistics.

```python
# 7-day moving average
df['7DayAvg'] = df['Price'].rolling(window=7).mean()

# 30-day rolling standard deviation (volatility)
df['30DayStd'] = df['Price'].rolling(window=30).std()

# Rolling sum
df['30DaySales'] = df['Sales'].rolling(window=30).sum()
```

### Date Arithmetic

```python
from datetime import timedelta

# Add 30 days to a date column
df['DueDate'] = df['OrderDate'] + pd.Timedelta(days=30)

# Difference between two dates
df['DaysToDeliver'] = (df['DeliveryDate'] - df['OrderDate']).dt.days

# Create a date range
date_range = pd.date_range(start='2024-01-01', end='2024-12-31', freq='D')
print(date_range)
```

### Handling Timezones

```python
# Localize a naive datetime to a timezone
df.index = df.index.tz_localize('Asia/Kolkata')

# Convert between timezones
df.index = df.index.tz_convert('UTC')
```

---

## 19. Input and Output Operations

Reading data from files and writing processed data back to files are the most fundamental operations in any data project.

### Reading CSV Files

```python
import pandas as pd

# Basic read
df = pd.read_csv('data.csv')

# With specific encoding (important for Indian datasets)
df = pd.read_csv('data.csv', encoding='utf-8')
df = pd.read_csv('data.csv', encoding='latin-1')

# Specify which column to use as index
df = pd.read_csv('data.csv', index_col='EmployeeID')

# Read only specific columns
df = pd.read_csv('data.csv', usecols=['Name', 'Salary', 'Department'])

# Parse date columns automatically
df = pd.read_csv('data.csv', parse_dates=['JoinDate', 'LastLogin'])

# Specify data types on load
df = pd.read_csv('data.csv', dtype={'ZipCode': str, 'Phone': str})

# Read a file with a different separator
df = pd.read_csv('data.tsv', sep='\t')     # Tab-separated
df = pd.read_csv('data.csv', sep=';')      # Semicolon-separated

# Skip rows
df = pd.read_csv('data.csv', skiprows=2)    # Skip first 2 rows

# Read only first 1000 rows (useful for large files)
df = pd.read_csv('data.csv', nrows=1000)

# Handle missing value indicators
df = pd.read_csv('data.csv', na_values=['N/A', 'NULL', 'none', '-'])
```

### Writing to CSV

```python
# Write to CSV
df.to_csv('output.csv', index=False)     # index=False avoids writing the row index

# Write with specific encoding
df.to_csv('output.csv', index=False, encoding='utf-8-sig')  # utf-8-sig for Excel compatibility

# Write only specific columns
df.to_csv('output.csv', columns=['Name', 'Salary'], index=False)
```

### Reading Excel Files

```python
# Install first: pip install openpyxl

# Read first sheet (default)
df = pd.read_excel('data.xlsx')

# Read specific sheet by name
df = pd.read_excel('data.xlsx', sheet_name='Sales')

# Read specific sheet by position
df = pd.read_excel('data.xlsx', sheet_name=0)

# Read all sheets into a dictionary
all_sheets = pd.read_excel('data.xlsx', sheet_name=None)
df_sales   = all_sheets['Sales']
df_expenses = all_sheets['Expenses']
```

### Writing to Excel

```python
# Write to Excel
df.to_excel('output.xlsx', sheet_name='Report', index=False)

# Write multiple DataFrames to multiple sheets
with pd.ExcelWriter('report.xlsx', engine='openpyxl') as writer:
    df_sales.to_excel(writer, sheet_name='Sales', index=False)
    df_expenses.to_excel(writer, sheet_name='Expenses', index=False)
    df_summary.to_excel(writer, sheet_name='Summary', index=False)
```

### Reading JSON Files

```python
df = pd.read_json('data.json')

# Read JSON from a URL
df = pd.read_json('https://api.example.com/data')
```

### Writing to JSON

```python
df.to_json('output.json', orient='records', indent=2)
```

The `orient` parameter controls the format:
- `'records'` - list of dictionaries (one per row)
- `'index'` - dictionary with index as keys
- `'columns'` - dictionary with columns as keys

### Reading from SQL Database

```python
import sqlite3
import pandas as pd

# Connect to a SQLite database
conn = sqlite3.connect('company.db')

# Read an entire table
df = pd.read_sql('SELECT * FROM employees', conn)

# Read with a filtered query
df = pd.read_sql('''
    SELECT Name, Department, Salary
    FROM employees
    WHERE Salary > 50000
    ORDER BY Salary DESC
''', conn)

conn.close()
```

### Writing to SQL Database

```python
conn = sqlite3.connect('company.db')

df.to_sql('processed_employees', conn, if_exists='replace', index=False)
# if_exists options: 'fail', 'replace', 'append'

conn.close()
```

### Reading Parquet Files

Parquet is a columnar file format commonly used in big data. It is much faster and smaller than CSV for large datasets.

```python
# pip install pyarrow

df = pd.read_parquet('data.parquet')
df.to_parquet('output.parquet', index=False)
```

### Checking File Size and Memory Usage

```python
# Memory usage of the DataFrame
print(df.memory_usage(deep=True))
print(df.memory_usage(deep=True).sum() / 1024**2, "MB")
```

### Reading Large Files in Chunks

For very large CSV files that do not fit in memory, read them in chunks:

```python
chunk_size = 100000
results = []

for chunk in pd.read_csv('large_file.csv', chunksize=chunk_size):
    # Process each chunk
    processed = chunk[chunk['Salary'] > 50000]
    results.append(processed)

# Combine all processed chunks
df = pd.concat(results, ignore_index=True)
print(df.shape)
```

---

## Summary

This documentation has covered the full lifecycle of data work with pandas, from installation through loading, cleaning, transforming, analyzing, and saving your data. Here is a quick reference of the most important methods grouped by task:

**Exploration:** `head()`, `tail()`, `info()`, `describe()`, `dtypes`, `shape`, `value_counts()`, `nunique()`

**Selection:** `df['col']`, `df[['col1', 'col2']]`, `loc[]`, `iloc[]`, `at[]`, `iat[]`

**Filtering:** Boolean indexing, `isin()`, `between()`, `str.contains()`, `query()`

**Cleaning:** `isnull()`, `dropna()`, `fillna()`, `drop_duplicates()`, `replace()`, `astype()`

**Transformation:** `apply()`, `map()`, `pd.cut()`, `pd.qcut()`, `sort_values()`, `rename()`, `pivot_table()`, `melt()`

**Aggregation:** `groupby()`, `agg()`, `transform()`, `filter()`

**Combining:** `pd.concat()`, `pd.merge()`, `join()`

**Time Series:** `pd.to_datetime()`, `resample()`, `rolling()`, `dt` accessor

**I/O:** `read_csv()`, `to_csv()`, `read_excel()`, `to_excel()`, `read_sql()`, `to_sql()`, `read_parquet()`, `to_parquet()`

---

*This documentation is intended as a practical teaching resource. Every method shown here is used regularly in real-world data analysis projects. The best way to learn is to apply each section to an actual dataset from sources like Kaggle, data.gov.in, or any CSV file from your own work.*
