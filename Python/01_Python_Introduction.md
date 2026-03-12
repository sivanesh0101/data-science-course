# Python Introduction

## 1.Print Statment
### what is print statement in python?

>In Python, the print() statement is used to display output on the screen.

#### Syntax
```
print(object, sep=' ', end='\n', file=sys.stdout, flush=False)
```
#### Example
```
print("Hello, World!")
```
#### Output
Hello, World!

---
## 2.Comments in python
### what is comments line in python and it's type?
>A comment in Python is a piece of text that starts with the # symbol and is not executed by the Python interpreter.

### Types
#### 1. Single-line comment
Starts with a # symbol — anything after # on that line is ignored.

#### Example
```
# This is a single-line comment
print("Hello, World!")  # This prints a message
```
#### output

Hello, World!

### 2. Multi-line comment
Python doesn’t have a dedicated multi-line comment syntax,
but we can use triple quotes (''' or """) to write multi-line comments.

#### Example
```
'''
This is a multi-line comment.
You can use it to describe your code
in detail.
'''
print("Python Comments Example")
```
#### output

Python Comments Example

### 3.Multiple Statements on a single line

```
x=5;y=10;z=x+y
print(z)
```

### 4.Line Continuation

```
total=1+2+3+4+5+6+7+\
4+5+6

print(total)
```

### why use comments?
To **describe** what your code does

To make **debugging easier**

To **temporarily disable** lines of code

To **improve readability** for others (and your future self)

---
## 3. Indentation

Indentation in Python is used to define the structure and hierarchy of the code. Unlike many other programming languages that use braces {} to delimit blocks of code, Python uses indentation to determine the grouping of statements. This means that all the statements within a block must be indented at the same level.

Python uses indentation to define blocks of code. Consistent use of spaces (commonly 4) or a tab is required.


```
age=32
if age>30:
    
    print(age)
    
print(age)
```

## 3. Data Types
In Python, data types tell the interpreter what kind of value a variable holds — like a number, text, list, etc.

| **Category**           | **Data Type** | **Description / Summary**                         | **Example**                             |
| ---------------------- | ------------- | ------------------------------------------------- | --------------------------------------- |
| **1️⃣ Numeric Types**  | `int`         | Integer numbers (no decimals)                     | `x = 10`                                |
|                        | `float`       | Decimal or floating-point numbers                 | `y = 10.5`                              |
|                        | `complex`     | Complex numbers (a + bj)                          | `z = 3 + 5j`                            |
| **2️⃣ Sequence Types** | `str`         | String (collection of characters in quotes)       | `name = "Python"`                       |
|                        | `list`        | Ordered, changeable collection of items           | `numbers = [1, 2, 3]`                   |
|                        | `tuple`       | Ordered, **unchangeable** collection of items     | `point = (10, 20)`                      |
| **3️⃣ Mapping Type**   | `dict`        | Key-value pairs (like a real dictionary)          | `student = {"name": "John", "age": 21}` |
| **4️⃣ Set Types**      | `set`         | Unordered, unique items only                      | `colors = {"red", "green", "blue"}`     |
|                        | `frozenset`   | Same as set but **immutable (cannot be changed)** | `fset = frozenset({1, 2, 3})`           |
| **5️⃣ Boolean Type**   | `bool`        | Logical values — `True` or `False`                | `flag = True`                           |
| **6️⃣ Binary Types**   | `bytes`       | Sequence of bytes (immutable)                     | `b = b"Hello"`                          |
|                        | `bytearray`   | Mutable sequence of bytes                         | `ba = bytearray([65, 66, 67])`          |
|                        | `memoryview`  | Memory view of bytes (advanced)                   | `mv = memoryview(b"abc")`               |
| **7️⃣ None Type**      | `NoneType`    | Represents the absence of value                   | `x = None`                              |

### Example
```
# Numeric
a = 10          # int
b = 10.5        # float
c = 2 + 3j      # complex

# Sequence
name = "Python" # str
numbers = [1, 2, 3] # list
coords = (10, 20)   # tuple

# Mapping
student = {"name": "Bhuvan", "age": 22}

# Set
colors = {"red", "blue"}

# Boolean
is_active = True

# None
x = None
```
### Summary
| **Category** | **Purpose**                                       |
| ------------ | ------------------------------------------------- |
| **Numeric**  | Store numbers (whole, decimal, or complex)        |
| **Sequence** | Store ordered collections (text or list of items) |
| **Mapping**  | Store data as key–value pairs                     |
| **Set**      | Store unique, unordered items                     |
| **Boolean**  | Store truth values (`True` / `False`)             |
| **Binary**   | Store byte data (for files, images, etc.)         |
| **None**     | Represent “no value” or “empty”                   |

---
## 4. Variables
Variables are **containers** for storing data **values.**

A variable is a **name** used to store a **value** in memory.
### 4.1 Rules for Python variables
A variable name must start with a letter or the underscore character

A variable name cannot start with a number

A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and _ )

Variable names are case-sensitive (age, Age and AGE are three different variables)

A variable name cannot be any of the Python keywords.

| Rule                                                                | Example                         |
| ------------------------------------------------------------------- | ------------------------------- |
| 1️⃣ Variable names must start with a **letter or underscore (`_`)** | ✅ `_name`, `age`                |
| 2️⃣ Cannot start with a **number**                                  | ❌ `1name`                       |
| 3️⃣ Can contain **letters, numbers, and underscores**               | ✅ `student_1`, `marks_count`    |
| 4️⃣ Are **case-sensitive**                                          | `Age` and `age` are different   |
| 5️⃣ Should not use **Python keywords**                              | ❌ `if`, `while`, `for`, `class` |

### 4.2 Declaring And Assigning Variables

```
age=32
height=6.1
name="bhuvi"
is_student=True

## printing the variables

print("age :",age)
print("Height:",height)
print("Name:",name)
```

### 4.3 Case Sensitivity

In Python, case sensitive means that uppercase and lowercase letters are treated as different characters.

```
name="bhuvanesh"
Name="bhuvaneshwaran"
```
### 4.4 Understnading Variable types

Python is dynamically typed,type of a variable is determined at runtime

```
age=25 #int
height=6.1 #float
name="KRish" #str
is_student=True #bool

print(type(name))
```
### 4.5 Dynamic Typing

Python allows the type of a vraible to change as the program executes

```
var=10 #int
print(var,type(var))

var="Hello"
print(var,type(var))

var=3.14
print(var,type(var))
```

### 4.6 Get value from Users

```
### Simple calculator
num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))

sum = num1 + num2
difference = num1 - num2
product = num1 * num2
quotient = num1 / num2

print("Sum:", sum)
print("Difference:", difference)
print("Product:", product)
print("Quotient:", quotient)
```

---
## 5. Keywords in Python
🔹 Keywords are special reserved words in Python that have a specific meaning and purpose.

🔹 You cannot use them as variable names, function names, or identifiers.

🔹 They define the syntax and structure of the Python language.

### example
```
if = 5      # ❌ Error — 'if' is a keyword
```
### List of All Python Keywords (Python 3.11 / 3.12)
| Category               | Keywords                                       | Meaning / Usage                  |
| ---------------------- | ---------------------------------------------- | -------------------------------- |
| **Control Flow**       | `if`, `elif`, `else`                           | Conditional statements           |
|                        | `for`, `while`, `break`, `continue`, `pass`    | Loops and control flow           |
| **Functions**          | `def`, `return`, `yield`, `lambda`             | Define and return from functions |
| **Classes & Objects**  | `class`, `self`, `del`                         | Object-oriented programming      |
| **Boolean & None**     | `True`, `False`, `None`                        | Boolean values and null value    |
| **Logical Operators**  | `and`, `or`, `not`, `in`, `is`                 | Logical and identity operations  |
| **Exception Handling** | `try`, `except`, `finally`, `raise`, `assert`  | Error handling                   |
| **Importing Modules**  | `import`, `from`, `as`                         | Module management                |
| **Variable Scope**     | `global`, `nonlocal`                           | Define variable scope            |
| **Async Programming**  | `async`, `await`                               | Asynchronous programming         |
| **Other Keywords**     | `with`, `yield`, `breakpoint`, `match`, `case` | Special use cases                |

### View all keywords
```
import keyword
print(keyword.kwlist)
```
### Python Programming Practice Report (print, variable)
I.Print Statement

1.Print your name, age, and favorite hobby in a single line.

2.Display a welcome message: Welcome to Python Learning, <your name>!

3.Print a short poem or quote using multiple `print`() lines.

4.Print a shopping list with each item on a new line.

5.Print your favorite movie name in uppercase letters.

II.Variables

1.Store your name, age, and city in variables and print them.

2.Store the cost of 3 products and calculate the total bill.

3.Create two variables a and b, swap their values, and print the result.

4.Store your birth year and calculate your age.

5.Store your school name in a variable and print:
"I study at <school_name>"

---
## 6.String_Handling

## 🧩 **Basic**

| Method   | Description        | Example            |
| :------- | :----------------- | :----------------- |
| `len(s)` | Returns length     | `len("abc") → 3`   |
| `str()`  | Converts to string | `str(123) → "123"` |

---

## 🔠 **Case Conversion**

| Method           | Description          | Example                            |
| :--------------- | :------------------- | :--------------------------------- |
| `s.lower()`      | All lowercase        | `"Hello".lower() → "hello"`        |
| `s.upper()`      | All uppercase        | `"Hello".upper() → "HELLO"`        |
| `s.title()`      | Title case           | `"hi there".title() → "Hi There"`  |
| `s.capitalize()` | 1st letter uppercase | `"python".capitalize() → "Python"` |
| `s.swapcase()`   | Swap case            | `"PyThOn".swapcase() → "pYtHoN"`   |

---

## ✂️ **Trim / Padding**

| Method                      | Description             | Example                          |
| :-------------------------- | :---------------------- | :------------------------------- |
| `s.strip()`                 | Remove both side spaces | `"  hi  ".strip() → "hi"`        |
| `s.lstrip()`                | Remove left spaces      | `"  hi".lstrip() → "hi"`         |
| `s.rstrip()`                | Remove right spaces     | `"hi  ".rstrip() → "hi"`         |
| `s.center(w, c)`            | Center with fill        | `"hi".center(6, "*") → "**hi**"` |
| `s.ljust(w)` / `s.rjust(w)` | Left/Right align        | `"hi".rjust(5) → "   hi"`        |
| `s.zfill(w)`                | Pad with zeros          | `"42".zfill(5) → "00042"`        |

---

## 🔍 **Search / Count**

| Method            | Description                      | Example                              |
| :---------------- | :------------------------------- | :----------------------------------- |
| `s.find(sub)`     | Index of sub or -1               | `"banana".find("na") → 2`            |
| `s.rfind(sub)`    | Last index                       | `"banana".rfind("na") → 4`           |
| `s.index(sub)`    | Like find but error if not found | `"abc".index("b") → 1`               |
| `s.count(sub)`    | Count occurrences                | `"aaa".count("a") → 3`               |
| `s.startswith(x)` | Check prefix                     | `"hello".startswith("he") → True`    |
| `s.endswith(x)`   | Check suffix                     | `"data.csv".endswith(".csv") → True` |

---

## 🔗 **Split / Join**

| Method             | Description          | Example                              |
| :----------------- | :------------------- | :----------------------------------- |
| `s.split(sep)`     | Split to list        | `"a,b,c".split(",") → ['a','b','c']` |
| `s.rsplit(sep)`    | Split from right     | `"a,b,c".rsplit(",",1)`              |
| `s.splitlines()`   | Split by newlines    | `"a\nb".splitlines() → ['a','b']`    |
| `'sep'.join(list)` | Join list to string  | `",".join(['a','b']) → "a,b"`        |
| `s.partition(x)`   | Split once (3 parts) | `"key=val".partition("=")`           |

---

## 🔁 **Replace / Map**

| Method                 | Description       | Example                                |
| :--------------------- | :---------------- | :------------------------------------- |
| `s.replace(a,b)`       | Replace text      | `"hi hi".replace("hi","yo") → "yo yo"` |
| `s.maketrans(from,to)` | Build map         | `t=str.maketrans("ae","12")`           |
| `s.translate(map)`     | Apply translation | `"apple".translate(t) → "1ppl2"`       |

---

## ✅ **Check Content**

| Method             | Description       | Example                          |
| :----------------- | :---------------- | :------------------------------- |
| `s.isalpha()`      | Letters only      | `"abc".isalpha() → True`         |
| `s.isdigit()`      | Digits only       | `"123".isdigit() → True`         |
| `s.isalnum()`      | Letters or digits | `"abc1".isalnum() → True`        |
| `s.islower()`      | All lowercase     | `"abc".islower() → True`         |
| `s.isupper()`      | All uppercase     | `"ABC".isupper() → True`         |
| `s.isspace()`      | Whitespace only   | `"  ".isspace() → True`          |
| `s.istitle()`      | Title case        | `"Hello World".istitle() → True` |
| `s.isidentifier()` | Valid Python name | `"var1".isidentifier() → True`   |

---

## 🧮 **Formatting**

| Method               | Description              | Example                                    |
| :------------------- | :----------------------- | :----------------------------------------- |
| `s.format()`         | Replace `{}` with values | `"Hi {}".format("Bhuvi")`                  |
| `f"..."`             | f-string formatting      | `f"Hi {name}"`                             |
| `s.format_map(dict)` | Format using dict        | `"Hi {name}".format_map({"name":"Bhuvi"})` |

---

## ⚙️ **Encoding**

| Method       | Description | Example                 |
| :----------- | :---------- | :---------------------- |
| `s.encode()` | To bytes    | `"hi".encode() → b'hi'` |
| `b.decode()` | To string   | `b'hi'.decode() → 'hi'` |

---

### ⚡ Quick tip:

* Strings are **immutable** → all methods return a **new string**.
* For multiple replacements, prefer `translate()` over multiple `replace()` calls.
* For performance, use `' '.join(list)` instead of repeated `+` concatenations.

---


