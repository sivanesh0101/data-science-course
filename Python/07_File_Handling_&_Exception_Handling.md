
# Python File Handling and Exception Handling

## Introduction

In Python, file handling and exception handling are two important concepts that are often used together in real-world programs. File handling allows us to work with files stored on the system, while exception handling helps us manage errors that may occur during program execution.

This document explains both concepts in a clear and structured way.

---

## File Handling in Python

### What is File Handling?

File handling refers to the process of reading from and writing to files. Unlike variables, which store data temporarily in memory, files allow data to be stored permanently.

Python provides built-in functions to perform file operations such as opening, reading, writing, and closing files.

---

### Opening a File

To work with a file, it must first be opened using the `open()` function.

```python
file = open("example.txt", "r")
```

The `open()` function takes two main arguments:

* The file name
* The mode in which the file is opened

---

### File Modes

Different modes define how a file is used:

* `"r"`: Opens the file for reading. This is the default mode.
* `"w"`: Opens the file for writing. If the file already exists, its contents are overwritten.
* `"a"`: Opens the file for appending. Data is added at the end of the file.
* `"x"`: Creates a new file. If the file already exists, an error occurs.
* `"b"`: Binary mode.
* `"t"`: Text mode (default).

---

### Reading from a File

```python
file = open("example.txt", "r")
content = file.read()
print(content)
file.close()
```

Other useful methods include:

* `readline()` to read a single line
* `readlines()` to read all lines as a list

---

### Writing to a File

```python
file = open("example.txt", "w")
file.write("Hello World")
file.close()
```

In write mode, the existing content of the file is replaced.

---

### Appending to a File

```python
file = open("example.txt", "a")
file.write("\nNew line")
file.close()
```

Append mode allows adding data without removing existing content.

---

### Using the `with` Statement

A better way to handle files is by using the `with` statement:

```python
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

This approach ensures that the file is automatically closed after the operation is completed.

---

## Exception Handling in Python

### What is Exception Handling?

Exception handling is used to handle runtime errors in a program. Without proper handling, errors can cause the program to stop abruptly.

By using exception handling, we can control how errors are managed and ensure that the program continues to run smoothly.

---

### Basic Structure

```python
try:
    # code that may cause an error
except:
    # code to handle the error
```

---

### Handling Specific Exceptions

```python
try:
    x = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
```

Handling specific exceptions helps in identifying and managing different types of errors more effectively.

---

### Complete Structure

```python
try:
    # code
except ExceptionType:
    # handle specific error
else:
    # executes if no error occurs
finally:
    # executes regardless of error
```

* The `else` block runs only if no exception occurs.
* The `finally` block always executes.

---

### Common Exceptions

* `FileNotFoundError`: Raised when a file does not exist
* `ZeroDivisionError`: Raised when division by zero is attempted
* `ValueError`: Raised when an invalid value is used
* `TypeError`: Raised when an operation is applied to an inappropriate data type

---

## Using File Handling with Exception Handling

In practical programs, file operations are often combined with exception handling to ensure reliability.

For example:

```python
try:
    with open("data.txt", "r") as file:
        content = file.read()
        print(content)
except FileNotFoundError:
    print("The file does not exist")
except Exception as e:
    print("An unexpected error occurred:", e)
finally:
    print("Program execution completed")
```

In this example:

* The program attempts to open and read a file
* If the file is not found, a specific error message is displayed
* Any other unexpected errors are also handled
* The `finally` block ensures that a message is printed regardless of the outcome

---

## Conclusion

File handling and exception handling serve different purposes but are closely connected in practice. File handling is used to perform operations on files, while exception handling ensures that errors during those operations are managed properly.

Understanding both concepts is essential for writing reliable and maintainable Python programs.
