# NumPy Complete Documentation
### A Structured Guide for Data Science Students — From Basics to Real-World Datasets

---

## Table of Contents

1. [Installing NumPy](#1-installing-numpy)
2. [Importing NumPy](#2-importing-numpy)
3. [NumPy Arrays Basics](#3-numpy-arrays-basics)
4. [Indexing and Slicing](#4-indexing-and-slicing)
5. [Arithmetic Operations](#5-arithmetic-operations)
6. [Broadcasting Rules in NumPy](#6-broadcasting-rules-in-numpy)
7. [Universal Functions](#7-universal-functions)
8. [Aggregate Functions](#8-aggregate-functions)
9. [Reshaping and Manipulating Arrays](#9-reshaping-and-manipulating-arrays)
10. [Linear Algebra with NumPy](#10-linear-algebra-with-numpy)
11. [Random Module](#11-random-module)
12. [Integration with Real-World Datasets](#12-integration-with-real-world-datasets)
13. [Advanced Operations](#13-advanced-operations)

---

## 1. Installing NumPy

NumPy is a third-party library and does not come pre-installed with Python. You need to install it once in your environment before you can use it.

### Using pip (Standard Python)

```bash
pip install numpy
```

### Using conda (Anaconda / Miniconda users)

```bash
conda install numpy
```

### Verifying the Installation

After installation, open a Python shell or Jupyter Notebook and confirm the version:

```python
import numpy
print(numpy.__version__)
```

Expected output (version may vary):

```
1.26.4
```

If no error appears and a version number is printed, NumPy is installed correctly.

### Note for Virtual Environments

Always install NumPy inside your project's virtual environment to avoid dependency conflicts across projects:

```bash
python -m venv myenv
source myenv/bin/activate       # On Windows: myenv\Scripts\activate
pip install numpy
```

---

## 2. Importing NumPy

Once installed, you import NumPy at the top of every Python script or notebook where you plan to use it.

### Standard Import Convention

```python
import numpy as np
```

The alias `np` is an industry-wide convention. Every NumPy user and every data science tutorial uses this alias. You should adopt it from day one so your code is readable to others and you can follow external resources easily.

### Accessing NumPy Functions

Once imported, all NumPy functionality is accessed through the `np` prefix:

```python
import numpy as np

arr = np.array([1, 2, 3])
print(arr)
```

Output:

```
[1 2 3]
```

---

## 3. NumPy Arrays Basics

The core of NumPy is the `ndarray` (N-dimensional array). Unlike Python lists, NumPy arrays are homogeneous (all elements share the same data type), which makes numerical computation much faster and more memory-efficient.

### 3.1 Creating Arrays from Python Lists

```python
import numpy as np

# 1D array
arr1d = np.array([10, 20, 30, 40, 50])
print(arr1d)
# Output: [10 20 30 40 50]

# 2D array (matrix)
arr2d = np.array([[1, 2, 3],
                  [4, 5, 6]])
print(arr2d)
# Output:
# [[1 2 3]
#  [4 5 6]]

# 3D array
arr3d = np.array([[[1, 2], [3, 4]],
                  [[5, 6], [7, 8]]])
print(arr3d.shape)
# Output: (2, 2, 2)
```

### 3.2 Array Attributes

Every NumPy array carries important metadata:

```python
arr = np.array([[1.0, 2.0, 3.0],
                [4.0, 5.0, 6.0]])

print("Shape   :", arr.shape)    # (2, 3) — 2 rows, 3 columns
print("Ndim    :", arr.ndim)     # 2 — number of dimensions
print("Size    :", arr.size)     # 6 — total number of elements
print("Dtype   :", arr.dtype)    # float64
print("Itemsize:", arr.itemsize) # 8 bytes per element
```

### 3.3 Built-in Array Creation Functions

NumPy provides several functions to create arrays without manually typing values:

```python
# Zeros and ones
zeros = np.zeros((3, 4))        # 3x4 matrix of 0.0
ones  = np.ones((2, 3))         # 2x3 matrix of 1.0

# Identity matrix
eye = np.eye(4)                  # 4x4 identity matrix

# Evenly spaced values (like Python's range)
arange = np.arange(0, 20, 2)    # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# Evenly spaced values between two endpoints
linspace = np.linspace(0, 1, 5) # [0.  , 0.25, 0.5 , 0.75, 1.  ]

# Array filled with a constant
full = np.full((3, 3), 7)       # 3x3 matrix filled with 7

# Uninitialized memory (fast, but unpredictable values — use only when you will overwrite)
empty = np.empty((2, 2))
```

### 3.4 Data Types

Specifying the data type explicitly is good practice, especially when memory efficiency matters:

```python
arr_int   = np.array([1, 2, 3], dtype=np.int32)
arr_float = np.array([1, 2, 3], dtype=np.float64)
arr_bool  = np.array([0, 1, 0, 1], dtype=np.bool_)
arr_str   = np.array(['Chennai', 'Mumbai', 'Delhi'], dtype=np.str_)

# Type casting
arr_float_to_int = arr_float.astype(np.int32)
```

Common dtypes you will encounter in real datasets:

| NumPy dtype | Meaning | Size |
|---|---|---|
| int32 / int64 | Integer | 4 / 8 bytes |
| float32 / float64 | Floating-point | 4 / 8 bytes |
| bool_ | Boolean | 1 byte |
| str_ | Unicode string | variable |
| object | Python objects | variable |

---

## 4. Indexing and Slicing

Accessing specific elements or subsets of arrays is one of the most frequently used skills in data science.

### 4.1 1D Array Indexing

```python
arr = np.array([100, 200, 300, 400, 500])

print(arr[0])    # 100  — first element
print(arr[-1])   # 500  — last element
print(arr[2])    # 300  — third element
```

### 4.2 1D Array Slicing

```python
arr = np.array([10, 20, 30, 40, 50, 60, 70])

print(arr[1:4])   # [20 30 40]  — index 1 up to (not including) 4
print(arr[:3])    # [10 20 30]  — from start to index 3
print(arr[4:])    # [50 60 70]  — from index 4 to end
print(arr[::2])   # [10 30 50 70] — every second element
print(arr[::-1])  # [70 60 50 40 30 20 10] — reversed
```

### 4.3 2D Array Indexing

For 2D arrays, think of rows and columns: `arr[row, column]`.

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6],
                [7, 8, 9]])

print(arr[0, 0])    # 1  — row 0, column 0
print(arr[1, 2])    # 6  — row 1, column 2
print(arr[-1, -1])  # 9  — last row, last column

# Entire row
print(arr[1, :])    # [4 5 6]

# Entire column
print(arr[:, 2])    # [3 6 9]

# Submatrix — rows 0:2, columns 1:3
print(arr[0:2, 1:3])
# [[2 3]
#  [5 6]]
```

### 4.4 Fancy Indexing

Fancy indexing allows you to select multiple non-consecutive elements at once using an integer array or list as the index:

```python
arr = np.array([10, 20, 30, 40, 50, 60])
indices = [0, 2, 5]
print(arr[indices])
# Output: [10 30 60]

# 2D fancy indexing
matrix = np.array([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9]])

rows = [0, 2]
cols = [1, 2]
print(matrix[rows, cols])   # [2 9] — (0,1) and (2,2)
```

### 4.5 Boolean Indexing

This is one of the most powerful filtering mechanisms in NumPy and is used heavily in real datasets:

```python
arr = np.array([15, 82, 43, 67, 91, 28, 55])

# Create a boolean mask
mask = arr > 50
print(mask)
# Output: [False  True False  True  True False  True]

# Apply the mask
print(arr[mask])
# Output: [82 67 91 55]

# Combine conditions
print(arr[(arr > 40) & (arr < 80)])
# Output: [43 67 55]
```

Real-world scenario — filtering temperature readings:

```python
temperatures = np.array([22.1, 35.8, 18.4, 40.2, 28.6, 33.1, 15.9])
heat_wave_days = temperatures[temperatures >= 33.0]
print(heat_wave_days)
# Output: [35.8 40.2 33.1]
```

---

## 5. Arithmetic Operations

NumPy performs arithmetic element-wise, meaning the operation is applied to each pair of corresponding elements. This eliminates the need for explicit loops.

### 5.1 Basic Element-wise Operations

```python
a = np.array([10, 20, 30, 40])
b = np.array([2, 4, 6, 8])

print(a + b)    # [12 24 36 48]
print(a - b)    # [ 8 16 24 32]
print(a * b)    # [ 20  80 180 320]
print(a / b)    # [5. 5. 5. 5.]
print(a // b)   # [ 5  5  5  5]  — integer division
print(a % b)    # [0 0 0 0]  — modulo
print(a ** 2)   # [100 400 900 1600]  — power
```

### 5.2 Scalar Operations

Any arithmetic between an array and a single number is applied to every element:

```python
prices = np.array([250.0, 480.0, 175.0, 390.0])

# Apply a 10% discount
discounted = prices * 0.90
print(discounted)
# Output: [225.  432.  157.5 351. ]

# Add flat tax
with_tax = prices + 18
print(with_tax)
# Output: [268. 498. 193. 408.]
```

### 5.3 Comparison Operations

Comparisons also return element-wise boolean arrays:

```python
a = np.array([1, 5, 3, 8, 2])
b = np.array([3, 3, 3, 3, 3])

print(a > b)    # [False  True False  True False]
print(a == b)   # [False False  True False False]
print(a != b)   # [ True  True False  True  True]
```

### 5.4 Real-world Example — Normalizing Sensor Data

```python
raw_readings = np.array([200, 450, 310, 580, 120, 670])

minimum = raw_readings.min()
maximum = raw_readings.max()

normalized = (raw_readings - minimum) / (maximum - minimum)
print(normalized.round(3))
# Output: [0.146 0.6   0.349 0.84  0.    1.   ]
```

This normalization pattern (min-max scaling) is used in machine learning to bring all features to the same scale.

---

## 6. Broadcasting Rules in NumPy

Broadcasting is NumPy's mechanism for applying operations between arrays of different shapes without creating unnecessary copies of data. Understanding broadcasting prevents bugs and helps you write cleaner code.

### 6.1 The Broadcasting Rules

NumPy compares shapes dimension by dimension, starting from the trailing (rightmost) dimension:

- If two dimensions are equal, they are compatible.
- If one of them is 1, it is "stretched" to match the other.
- If neither is 1 and they are not equal, NumPy raises an error.

### 6.2 Scalar and Array

The simplest case — a scalar broadcasts to all elements:

```python
arr = np.array([1, 2, 3, 4, 5])
print(arr + 100)
# Output: [101 102 103 104 105]
```

### 6.3 1D Array and 2D Array

```python
matrix = np.array([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9]])

row_bias = np.array([10, 20, 30])

result = matrix + row_bias
print(result)
# Output:
# [[11 22 33]
#  [14 25 36]
#  [17 28 39]]
```

Here `row_bias` has shape `(3,)` which NumPy treats as `(1, 3)` and replicates it across all rows.

### 6.4 Column Vector Broadcasting

```python
col_vector = np.array([[100],
                       [200],
                       [300]])        # shape (3, 1)

row_vector = np.array([1, 2, 3, 4])  # shape (4,) treated as (1, 4)

result = col_vector + row_vector      # result shape: (3, 4)
print(result)
# Output:
# [[101 102 103 104]
#  [201 202 203 204]
#  [301 302 303 304]]
```

### 6.5 Common Broadcasting Error

```python
a = np.array([1, 2, 3])       # shape (3,)
b = np.array([1, 2, 3, 4])    # shape (4,)

# a + b   <-- This raises ValueError: operands could not be broadcast with shapes (3,) (4,)
```

### 6.6 Real-world Example — Centering a Dataset

```python
# A dataset of 4 samples, each with 3 features
data = np.array([[2.5, 3.0, 1.0],
                 [1.0, 4.5, 2.5],
                 [3.5, 2.0, 0.5],
                 [2.0, 3.5, 3.0]])

column_means = data.mean(axis=0)     # Mean of each feature column
print("Means:", column_means)
# Means: [2.25 3.25 1.75]

centered = data - column_means       # Broadcasting: (4,3) - (3,) => (4,3)
print(centered)
# Output:
# [[ 0.25 -0.25 -0.75]
#  [-1.25  1.25  0.75]
#  [ 1.25 -1.25 -1.25]
#  [-0.25  0.25  1.25]]
```

---

## 7. Universal Functions

Universal functions, commonly called ufuncs, are functions that operate element-wise on arrays. They are written in compiled C code internally, making them significantly faster than equivalent Python loops.

### 7.1 Mathematical Ufuncs

```python
arr = np.array([1.0, 4.0, 9.0, 16.0, 25.0])

print(np.sqrt(arr))    # [1. 2. 3. 4. 5.]
print(np.square(arr))  # [  1.  16.  81. 256. 625.]
print(np.log(arr))     # Natural log
print(np.log2(arr))    # Base-2 log
print(np.log10(arr))   # Base-10 log
print(np.exp(arr))     # e raised to each element
print(np.abs(np.array([-3, -1, 0, 4, -7])))  # [3 1 0 4 7]
```

### 7.2 Trigonometric Ufuncs

```python
angles = np.linspace(0, np.pi, 5)
# [0.         0.78539816 1.57079633 2.35619449 3.14159265]

print(np.sin(angles))  # [0.   0.707  1.   0.707  0.  ]
print(np.cos(angles))  # [1.   0.707  0.  -0.707 -1.  ]
print(np.tan(angles))  # [0.   1.    very large  -1.   0.  ]

# Inverse trig
print(np.arcsin(np.array([0, 0.5, 1])))  # in radians
print(np.degrees(np.arcsin(0.5)))        # convert to degrees: 30.0
```

### 7.3 Comparison Ufuncs

```python
a = np.array([3, 7, 1, 9, 4])
b = np.array([5, 2, 8, 6, 4])

print(np.maximum(a, b))     # [5 7 8 9 4] — element-wise maximum
print(np.minimum(a, b))     # [3 2 1 6 4] — element-wise minimum
print(np.greater(a, b))     # [False  True False  True False]
```

### 7.4 Real-world Example — Signal Processing

```python
# Generating a time series sine wave (like sensor readings)
t = np.linspace(0, 2 * np.pi, 100)
signal = np.sin(t) + 0.1 * np.sin(10 * t)  # Main frequency + noise

# Clipping the signal to a safe operating range [-0.8, 0.8]
safe_signal = np.clip(signal, -0.8, 0.8)
print(safe_signal[:5].round(4))
```

---

## 8. Aggregate Functions

Aggregate functions reduce an array along one or more axes, producing a summary value. These are the building blocks of statistical analysis.

### 8.1 Basic Aggregation

```python
arr = np.array([4, 7, 2, 9, 1, 5, 8, 3, 6])

print(np.sum(arr))     # 45
print(np.min(arr))     # 1
print(np.max(arr))     # 9
print(np.mean(arr))    # 5.0
print(np.median(arr))  # 5.0
print(np.std(arr))     # standard deviation
print(np.var(arr))     # variance
print(np.prod(arr))    # product of all elements
print(np.cumsum(arr))  # cumulative sum: [ 4 11 13 22 23 28 36 39 45]
```

### 8.2 The axis Parameter

The `axis` parameter is critical for 2D and higher-dimensional arrays. Without specifying it, aggregation flattens the entire array.

```python
scores = np.array([[85, 90, 78],    # Student 1
                   [72, 88, 95],    # Student 2
                   [60, 74, 82]])   # Student 3
#                  Math Sci  Eng

# axis=0 — aggregate down the rows (result is per column/subject)
print(np.mean(scores, axis=0))
# Output: [72.33 84.   85.  ] — average score per subject

# axis=1 — aggregate across the columns (result is per row/student)
print(np.mean(scores, axis=1))
# Output: [84.33 85.   72.  ] — average score per student

# No axis — overall average
print(np.mean(scores))
# Output: 80.44
```

### 8.3 Locating Min and Max Values

```python
sales = np.array([[500, 320, 780],
                  [410, 890, 245],
                  [670, 555, 430]])

# Index of maximum value in the entire array (flattened)
print(np.argmax(sales))       # 4 — flattened index
print(np.unravel_index(np.argmax(sales), sales.shape))
# Output: (1, 1) — row 1, column 1 — value 890

# Index of min/max along each axis
print(np.argmin(sales, axis=0))   # [1 0 1] — row index of min per column
print(np.argmax(sales, axis=1))   # [2 1 0] — column index of max per row
```

### 8.4 Real-world Example — Sales Data Summary

```python
monthly_revenue = np.array([
    [12000, 15000, 13500],   # Q1: Jan, Feb, Mar
    [14200, 16800, 17000],   # Q2: Apr, May, Jun
    [18500, 19200, 17800],   # Q3: Jul, Aug, Sep
    [20100, 22000, 21500]    # Q4: Oct, Nov, Dec
])

quarterly_total = np.sum(monthly_revenue, axis=1)
print("Quarterly Totals:", quarterly_total)
# Output: [40500 48000 55500 63600]

best_month_per_quarter = np.argmax(monthly_revenue, axis=1)
months = ['Jan/Apr/Jul/Oct', 'Feb/May/Aug/Nov', 'Mar/Jun/Sep/Dec']
print("Best Month per Quarter Index:", best_month_per_quarter)

annual_growth = ((quarterly_total[-1] - quarterly_total[0]) / quarterly_total[0]) * 100
print(f"Annual Growth: {annual_growth:.2f}%")
# Output: Annual Growth: 57.04%
```

---

## 9. Reshaping and Manipulating Arrays

Reshaping is the process of changing the shape of an array without changing its data. This is fundamental when preparing data for machine learning models and when working with images or time series.

### 9.1 reshape()

```python
arr = np.arange(12)
print(arr)
# Output: [ 0  1  2  3  4  5  6  7  8  9 10 11]

# Reshape to 3 rows, 4 columns
matrix = arr.reshape(3, 4)
print(matrix)
# Output:
# [[ 0  1  2  3]
#  [ 4  5  6  7]
#  [ 8  9 10 11]]

# Use -1 to let NumPy infer one dimension automatically
reshaped = arr.reshape(6, -1)   # 6 rows, NumPy figures out 2 columns
print(reshaped.shape)            # (6, 2)
```

Important: `reshape()` returns a view wherever possible, not a copy. Modifying the reshaped array may affect the original.

### 9.2 flatten() and ravel()

```python
matrix = np.array([[1, 2, 3], [4, 5, 6]])

flat = matrix.flatten()   # Returns a copy — safe to modify
rav  = matrix.ravel()     # Returns a view where possible — more memory efficient

print(flat)   # [1 2 3 4 5 6]
print(rav)    # [1 2 3 4 5 6]
```

### 9.3 Transposing

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6]])

print(arr.shape)       # (2, 3)
print(arr.T.shape)     # (3, 2)
print(arr.T)
# Output:
# [[1 4]
#  [2 5]
#  [3 6]]
```

### 9.4 Stacking and Splitting

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

# Horizontal stack — join side by side
print(np.hstack([a, b]))    # [1 2 3 4 5 6]

# Vertical stack — stack as rows
print(np.vstack([a, b]))
# [[1 2 3]
#  [4 5 6]]

# Stack along new axis
print(np.stack([a, b], axis=0))   # shape (2, 3)
print(np.stack([a, b], axis=1))   # shape (3, 2)

# Splitting
arr = np.array([10, 20, 30, 40, 50, 60])
parts = np.split(arr, 3)             # Split into 3 equal pieces
print(parts)
# [array([10, 20]), array([30, 40]), array([50, 60])]

# Horizontal and vertical splits for 2D arrays
matrix = np.arange(16).reshape(4, 4)
top, bottom = np.vsplit(matrix, 2)
left, right = np.hsplit(matrix, 2)
```

### 9.5 Adding and Removing Dimensions

```python
arr = np.array([1, 2, 3])    # shape (3,)

# Add an axis to make it a column vector
col = arr[:, np.newaxis]     # shape (3, 1)
row = arr[np.newaxis, :]     # shape (1, 3)

# Equivalent using expand_dims
col2 = np.expand_dims(arr, axis=1)

# Remove size-1 dimensions
big = np.array([[[1, 2, 3]]])   # shape (1, 1, 3)
small = np.squeeze(big)          # shape (3,)
```

### 9.6 Real-world Example — Reshaping Image Data

```python
# Grayscale image: 28x28 pixels (like MNIST digits)
image = np.random.randint(0, 256, size=(28, 28), dtype=np.uint8)
print("Image shape:", image.shape)     # (28, 28)

# Flatten to a 1D vector for input into a neural network
flat_image = image.flatten()
print("Flat shape:", flat_image.shape) # (784,)

# A batch of 100 such images
batch = np.random.randint(0, 256, size=(100, 28, 28), dtype=np.uint8)
flat_batch = batch.reshape(100, -1)
print("Batch shape:", flat_batch.shape) # (100, 784)
```

---

## 10. Linear Algebra with NumPy

NumPy's `linalg` module provides a full suite of linear algebra operations that underpin machine learning, scientific computing, and engineering.

### 10.1 Matrix Multiplication

```python
A = np.array([[1, 2],
              [3, 4]])

B = np.array([[5, 6],
              [7, 8]])

# Element-wise multiplication (NOT matrix multiplication)
print(A * B)
# [[ 5 12]
#  [21 32]]

# True matrix multiplication
print(A @ B)           # Preferred Python 3.5+ syntax
print(np.dot(A, B))    # Equivalent older syntax
# Output (both):
# [[19 22]
#  [43 50]]

# Matrix-vector multiplication
v = np.array([1, 2])
print(A @ v)           # [5 11]
```

### 10.2 Determinant and Trace

```python
A = np.array([[4, 7],
              [2, 6]])

det = np.linalg.det(A)
print(f"Determinant: {det:.2f}")   # 10.00

trace = np.trace(A)
print(f"Trace: {trace}")            # 10  (sum of diagonal)
```

### 10.3 Inverse Matrix

```python
A = np.array([[4.0, 7.0],
              [2.0, 6.0]])

A_inv = np.linalg.inv(A)
print(A_inv)

# Verify: A @ A_inv should be the identity matrix
print(np.round(A @ A_inv, 10))
# [[1. 0.]
#  [0. 1.]]
```

If a matrix is singular (non-invertible), `np.linalg.inv()` raises a `LinAlgError`. Always verify the determinant is non-zero before attempting inversion.

### 10.4 Solving Systems of Linear Equations

Suppose you want to solve the system:

```
2x + 3y = 8
5x - y  = 1
```

```python
A = np.array([[2, 3],
              [5, -1]])

b = np.array([8, 1])

x = np.linalg.solve(A, b)
print(x)
# Output: [1. 2.]  — x=1, y=2

# Verify
print(A @ x)
# Output: [8. 1.]
```

### 10.5 Eigenvalues and Eigenvectors

```python
A = np.array([[4, 1],
              [2, 3]])

eigenvalues, eigenvectors = np.linalg.eig(A)
print("Eigenvalues:", eigenvalues)
# Output: [5. 2.]

print("Eigenvectors:")
print(eigenvectors)
```

Eigenvalues and eigenvectors are fundamental to Principal Component Analysis (PCA) in machine learning.

### 10.6 Norms

```python
v = np.array([3.0, 4.0])

print(np.linalg.norm(v))          # 5.0 — L2 (Euclidean) norm
print(np.linalg.norm(v, ord=1))   # 7.0 — L1 (Manhattan) norm
print(np.linalg.norm(v, ord=np.inf))  # 4.0 — max norm

# Matrix norm
A = np.array([[1, 2], [3, 4]])
print(np.linalg.norm(A, 'fro'))   # Frobenius norm
```

### 10.7 Real-world Example — Linear Regression via Normal Equation

```python
# Predicting house price from size (sq ft) using linear regression
# Normal Equation: theta = (X^T X)^(-1) X^T y

X_raw = np.array([650, 800, 1000, 1200, 1500, 1800])
y     = np.array([120, 145, 185,  220,  280,  340])   # Price in thousands

# Add intercept column
X = np.column_stack([np.ones(len(X_raw)), X_raw])

# Solve using least squares (numerically stable alternative to explicit inverse)
theta, residuals, rank, sv = np.linalg.lstsq(X, y, rcond=None)
print(f"Intercept: {theta[0]:.2f}, Slope: {theta[1]:.4f}")
# Interpret: for each additional sq ft, price increases by theta[1] * 1000
```

---

## 11. Random Module

NumPy's `random` module is used to generate random numbers, create synthetic datasets, simulate experiments, and set up reproducible tests.

### 11.1 Setting the Seed for Reproducibility

Always set a random seed when your code needs to produce the same random results every time:

```python
rng = np.random.default_rng(seed=42)   # Modern NumPy approach (recommended)

# Legacy approach (still widely used)
np.random.seed(42)
```

### 11.2 Generating Random Numbers

```python
rng = np.random.default_rng(42)

# Uniform distribution — values between 0 and 1
uniform = rng.random(size=(3, 4))
print(uniform)

# Uniform distribution between custom bounds
custom = rng.uniform(low=10, high=50, size=6)

# Normal (Gaussian) distribution — mean=0, std=1
normal = rng.standard_normal(size=(3, 3))

# Normal with custom mean and std
heights = rng.normal(loc=165, scale=10, size=1000)   # Indian population heights

# Integer values
dice = rng.integers(low=1, high=7, size=10)    # Rolling a die 10 times
print(dice)
```

### 11.3 Distributions

```python
rng = np.random.default_rng(0)

# Binomial — number of successes in n trials
coin_flips = rng.binomial(n=10, p=0.5, size=5)    # 10 flips, 5 experiments

# Poisson — events per interval
arrivals = rng.poisson(lam=3.5, size=10)           # Average 3.5 arrivals per minute

# Exponential — time between events
wait_times = rng.exponential(scale=2.0, size=8)    # Average wait of 2 minutes

# Beta distribution — for probabilities and proportions
proportions = rng.beta(a=2, b=5, size=10)
```

### 11.4 Shuffling and Sampling

```python
rng = np.random.default_rng(7)

arr = np.arange(10)

# Shuffle in place
rng.shuffle(arr)
print(arr)

# Sample without replacement
sample = rng.choice(arr, size=4, replace=False)
print(sample)

# Sample with replacement (bootstrapping)
bootstrap = rng.choice(arr, size=10, replace=True)
print(bootstrap)
```

### 11.5 Real-world Example — Simulating Stock Returns

```python
rng = np.random.default_rng(99)

# Daily stock returns follow an approximately normal distribution
# Assume 1% average daily return, 2% standard deviation
n_days = 252          # Trading days in a year
n_simulations = 5000  # Run 5000 portfolio simulations

daily_returns = rng.normal(loc=0.001, scale=0.02, size=(n_days, n_simulations))

# Starting value 10000 rupees
initial_value = 10000.0
portfolio_values = initial_value * np.cumprod(1 + daily_returns, axis=0)

final_values = portfolio_values[-1, :]
print(f"Median final value: {np.median(final_values):,.0f}")
print(f"5th percentile (worst case):  {np.percentile(final_values, 5):,.0f}")
print(f"95th percentile (best case):  {np.percentile(final_values, 95):,.0f}")
```

---

## 12. Integration with Real-World Datasets

NumPy is the computational backbone of nearly all Python data science tools, including Pandas, Scikit-learn, and Matplotlib. Understanding how NumPy integrates with these tools is essential.

### 12.1 NumPy and Pandas

Pandas DataFrames store their underlying data as NumPy arrays. You can extract and manipulate this data directly:

```python
import numpy as np
import pandas as pd

# Load a CSV file using Pandas
df = pd.read_csv('sales_data.csv')

# Extract a column as a NumPy array
revenue = df['revenue'].to_numpy()
print(type(revenue))      # <class 'numpy.ndarray'>
print(revenue.mean())

# Compute z-scores manually
z_scores = (revenue - revenue.mean()) / revenue.std()

# Multi-column extraction
features = df[['age', 'income', 'spending_score']].to_numpy()
print(features.shape)     # (n_samples, 3)
```

### 12.2 Loading Numeric Data Directly with NumPy

For simple CSV files with purely numeric data, NumPy can load them without Pandas:

```python
# Load numeric CSV
data = np.loadtxt('temperatures.csv', delimiter=',', skiprows=1)

# Load with mixed types using genfromtxt
data = np.genfromtxt('records.csv', delimiter=',', names=True, dtype=None, encoding='utf-8')
print(data.dtype.names)   # Column names
```

### 12.3 Saving and Loading NumPy Arrays

```python
arr = np.array([[1.0, 2.5, 3.7],
                [4.2, 5.8, 6.1]])

# Save as binary (fast, lossless)
np.save('array.npy', arr)
loaded = np.load('array.npy')

# Save multiple arrays in one file
np.savez('dataset.npz', features=arr, labels=np.array([0, 1]))
archive = np.load('dataset.npz')
print(archive['features'])
print(archive['labels'])

# Save as human-readable text
np.savetxt('array.csv', arr, delimiter=',', fmt='%.4f')
```

### 12.4 Real-world Pipeline — Iris-style Dataset Analysis

```python
import numpy as np

# Simulated dataset: 150 samples, 4 features (sepal_l, sepal_w, petal_l, petal_w)
rng = np.random.default_rng(42)
n_samples = 150
features = rng.normal(loc=[5.8, 3.0, 3.7, 1.2], scale=[0.8, 0.4, 1.8, 0.8],
                      size=(n_samples, 4))
labels = np.repeat([0, 1, 2], 50)    # 3 classes, 50 samples each

# --- Basic statistics per feature ---
print("Feature means:")
print(features.mean(axis=0).round(3))

print("Feature std deviations:")
print(features.std(axis=0).round(3))

# --- Per-class statistics ---
for cls in [0, 1, 2]:
    mask = labels == cls
    class_data = features[mask]
    print(f"\nClass {cls} — mean: {class_data.mean(axis=0).round(2)}")

# --- Correlation between features ---
corr_matrix = np.corrcoef(features.T)   # shape (4, 4)
print("\nCorrelation Matrix:")
print(corr_matrix.round(3))

# --- Z-score normalization ---
means = features.mean(axis=0)
stds  = features.std(axis=0)
normalized = (features - means) / stds
print("\nNormalized data range:", normalized.min().round(3), "to", normalized.max().round(3))
```

---

## 13. Advanced Operations

### 13.1 Sorting

```python
arr = np.array([5, 2, 8, 1, 9, 3, 7])

# Sort and return sorted array (original unchanged)
print(np.sort(arr))          # [1 2 3 5 7 8 9]

# Sort in descending order
print(np.sort(arr)[::-1])    # [9 8 7 5 3 2 1]

# Sort in place (modifies original)
arr.sort()
print(arr)                   # [1 2 3 5 7 8 9]

# argsort — returns indices that would sort the array
arr = np.array([50, 10, 40, 30, 20])
sorted_indices = np.argsort(arr)
print(sorted_indices)        # [1 4 3 2 0]
print(arr[sorted_indices])   # [10 20 30 40 50]

# Sorting 2D along a specified axis
matrix = np.array([[3, 1, 2],
                   [6, 4, 5]])
print(np.sort(matrix, axis=1))   # Sort each row: [[1 2 3] [4 5 6]]
print(np.sort(matrix, axis=0))   # Sort each column: [[3 1 2] [6 4 5]]
```

### 13.2 Unique Values and Set Operations

```python
arr = np.array([3, 1, 4, 1, 5, 9, 2, 6, 5, 3])

uniq = np.unique(arr)
print(uniq)                              # [1 2 3 4 5 6 9]

uniq, counts = np.unique(arr, return_counts=True)
print(dict(zip(uniq, counts)))
# {1: 2, 2: 1, 3: 2, 4: 1, 5: 2, 6: 1, 9: 1}

a = np.array([1, 2, 3, 4, 5])
b = np.array([3, 4, 5, 6, 7])

print(np.intersect1d(a, b))    # [3 4 5]
print(np.union1d(a, b))        # [1 2 3 4 5 6 7]
print(np.setdiff1d(a, b))      # [1 2] — in a but not b
print(np.isin(a, b))           # [False False  True  True  True]
```

### 13.3 Structured Arrays

Structured arrays allow you to store data of mixed types in a single NumPy array, similar to a table:

```python
dtype = np.dtype([
    ('name',   'U20'),     # Unicode string, up to 20 chars
    ('age',    'i4'),      # 32-bit integer
    ('salary', 'f8')       # 64-bit float
])

employees = np.array([
    ('Alice', 30, 75000.0),
    ('Bob',   25, 62000.0),
    ('Carol', 35, 91000.0)
], dtype=dtype)

print(employees['name'])           # ['Alice' 'Bob' 'Carol']
print(employees['salary'].mean())  # 76000.0

# Filter by condition
seniors = employees[employees['age'] >= 30]
print(seniors)
```

### 13.4 Memory Views and Copies

Understanding the difference between views and copies prevents subtle bugs:

```python
original = np.array([1, 2, 3, 4, 5])

# View — shares memory with original
view = original[1:4]
view[0] = 99
print(original)   # [ 1 99  3  4  5] — original was changed!

# Copy — completely independent
copy = original[1:4].copy()
copy[0] = 0
print(original)   # [ 1 99  3  4  5] — original unchanged

# Check if an array owns its data
print(view.base is original)   # True — it's a view
print(copy.base is None)       # True — it owns its data
```

### 13.5 Vectorization — Replacing Loops with NumPy

One of the most important performance practices in NumPy is vectorizing operations that would otherwise require Python loops:

```python
import time

n = 1_000_000
data = np.random.rand(n)

# Slow Python loop
start = time.time()
result_loop = [x ** 2 for x in data]
loop_time = time.time() - start

# Fast NumPy vectorized
start = time.time()
result_numpy = data ** 2
numpy_time = time.time() - start

print(f"Loop time:  {loop_time:.4f} seconds")
print(f"NumPy time: {numpy_time:.4f} seconds")
print(f"Speedup:    {loop_time / numpy_time:.1f}x")
# NumPy is typically 50-200x faster
```

### 13.6 np.where — Conditional Element Selection

`np.where` is NumPy's vectorized conditional expression. Think of it as: "where the condition is True, use x; otherwise use y."

```python
arr = np.array([10, -5, 30, -20, 15, -8])

# Replace negatives with 0
result = np.where(arr > 0, arr, 0)
print(result)   # [10  0 30  0 15  0]

# Categorize values
grades = np.array([85, 42, 73, 91, 60, 55])
label = np.where(grades >= 75, 'Pass', 'Fail')
print(label)    # ['Pass' 'Fail' 'Pass' 'Pass' 'Fail' 'Fail']
```

Real-world usage — flagging anomalies:

```python
sensor_data = np.array([23.1, 22.8, 45.7, 23.5, 22.9, 24.0, 48.2, 23.3])
threshold = 35.0

status = np.where(sensor_data > threshold, 'ALERT', 'NORMAL')
for reading, stat in zip(sensor_data, status):
    print(f"{reading:.1f}  -> {stat}")
```

### 13.7 Percentiles and Statistical Summaries

```python
data = np.array([14, 18, 11, 13, 6, 8, 2, 19, 20, 17, 15, 16, 9, 7, 3])

print(np.percentile(data, 25))    # Q1 — 25th percentile
print(np.percentile(data, 50))    # Q2 — median
print(np.percentile(data, 75))    # Q3 — 75th percentile

q1, q3 = np.percentile(data, [25, 75])
iqr = q3 - q1
print(f"IQR: {iqr}")

# Outlier detection using IQR
lower_bound = q1 - 1.5 * iqr
upper_bound = q3 + 1.5 * iqr
outliers = data[(data < lower_bound) | (data > upper_bound)]
print("Outliers:", outliers)
```

### 13.8 Vectorized String Operations (for object arrays)

When working with string arrays in NumPy, use `np.char` for vectorized operations:

```python
names = np.array(['alice', 'bob', 'carol', 'david'])

print(np.char.upper(names))         # ['ALICE' 'BOB' 'CAROL' 'DAVID']
print(np.char.capitalize(names))    # ['Alice' 'Bob' 'Carol' 'David']
print(np.char.add(names, '@org'))   # ['alice@org' 'bob@org' ...]

# Check string properties
emails = np.array(['user@mail.com', 'invalid', 'admin@domain.in'])
print(np.char.find(emails, '@'))    # Index of '@' in each string: [4 -1 5]
contains = np.char.find(emails, '@') >= 0
print(contains)   # [ True False  True]
```

---

## Summary Table

| Category | Key Functions |
|---|---|
| Array creation | array, zeros, ones, eye, arange, linspace, full, empty |
| Array info | shape, ndim, size, dtype, itemsize |
| Indexing | arr[i], arr[i,j], arr[a:b], boolean mask, fancy index |
| Arithmetic | +, -, *, /, //, **, np.add, np.multiply |
| Broadcasting | Automatic shape alignment for compatible arrays |
| Ufuncs | sqrt, exp, log, sin, cos, abs, maximum, clip |
| Aggregation | sum, min, max, mean, median, std, var, cumsum, argmax |
| Reshaping | reshape, flatten, ravel, T, hstack, vstack, split, squeeze |
| Linear Algebra | dot, @, inv, det, solve, eig, norm, lstsq |
| Random | default_rng, random, normal, integers, choice, shuffle |
| Advanced | sort, argsort, unique, where, isin, percentile, intersect1d |

---

## Best Practices for Students

**Use vectorization over loops.** Any time you write a for loop that iterates over array elements and performs arithmetic, ask yourself whether NumPy has a built-in way to do that operation. It almost always does, and it will be dramatically faster.

**Always set a random seed** when generating random data for experiments or homework. This ensures your results are reproducible and can be verified.

**Specify dtypes explicitly** when memory matters. float32 instead of float64 cuts memory in half, which is important for large datasets and neural network training.

**Understand views versus copies.** Slicing returns a view. If you need to modify a subset of an array without affecting the original, always call `.copy()` on the slice.

**Use axis thoughtfully.** For 2D arrays, `axis=0` operates along rows (gives per-column results), and `axis=1` operates along columns (gives per-row results). This confuses beginners frequently — practice it with small examples until it becomes second nature.

**Profile before optimizing.** Use Python's `time` module or `%timeit` in Jupyter to measure where your code spends time before rewriting it. NumPy's biggest gains come from replacing Python loops, not from micro-optimizing NumPy calls.

---

*This documentation was written for students learning data science from the ground up. All examples are self-contained and can be run in a standard Python environment with NumPy installed.*
