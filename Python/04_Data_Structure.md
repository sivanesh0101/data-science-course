# Python Data Structures
## Intoduction
Python provides a rich set of built-in and specialized data structures that allow efficient storage, retrieval, transformation, and organization of data.

## Built-in Data Structures
List

Tuples

sets

Dictionaries

## **List []**:

A **list** in Python is a dynamic, mutable, ordered data structure used to store multiple items in a single variable.
It is one of the most commonly used data structures in Python because it is flexible, easy to use, and supports a wide variety of operations.

Python lists:
- Can store **mixed data types**
- Can grow or shrink dynamically
- Are implemented internally as **dynamic arrays** (resizable arrays)

Lists are ideal when you need an ordered, modifiable sequence of elements.

---

**Key Characteristics of Lists**

#### ✔ Ordered
Elements in a list maintain the order in which they are inserted.

```
x = [10, 20, 30]
# index: 0   1   2

#### ✔ Mutable (can be changed)

You can modify elements, append items, delete items, etc.

```
x[1] = 99  # allowed

#### ✔ Allows Duplicate Values

You can store different data types together.

```
x = [10, "hello", 3.14, True]
```

#### ✔ Dynamic Size

Lists grow and shrink automatically as elements are added or removed.

#### ✔ Indexing & Slicing Supported

Allows accessing individual elements or sublists.

```
x = [10, 20, 30, 40, 50]
print(x[2])    # 30
print(x[1:4])  # [20, 30, 40]
```

### Examples of List Usage
#### Creating List

```
numbers = [1, 2, 3, 4]
mixed = [10, "hello", 3.14]
empty = []
```

#### Adding Elements

```
numbers.append(5)        # Add at end
numbers.insert(1, 10)    # Insert 10 at index 1
numbers.extend([6, 7])   # Add multiple items
```

#### Removing Elements

```
numbers.pop()        # Removes last element
numbers.pop(1)       # Removes element at index 1
numbers.remove(3)    # Removes first occurrence of 3
del numbers[0]       # Delete index 0
```
#### Searching

```
if 10 in numbers:
    print("Found")

print(numbers.index(10))   # returns index of 10
```

#### Iteration

```
for n in numbers:
    print(n)
```

#### List Comprehension

```
squares = [x*x for x in range(1, 6)]
```

### Advantages of Lists

✅ 1. Highly Flexible

Can store mixed data types and support multiple operations.

✅ 2. Fast Random Access (O(1))

Indexing is very fast because lists are implemented as dynamic arrays.

✅ 3. Easy to Modify

You can:

add

remove

update

elements easily.

✅ 4. Supports Powerful Built-in Methods

append(), extend(), insert(), remove(), sort(), reverse(), etc.

✅ 5. Dynamic Resizing

The list automatically expands or shrinks as needed.

✅ 6. Great for Iteration

Works smoothly with loops, list comprehensions, and functions like map() or filter().

### Disadvantages of Lists

❌ 1. Slow for Insert/Delete in Middle (O(n))

Because elements must shift to maintain order.

❌ 2. Higher Memory Usage

Since Python lists store references, they consume more memory than arrays in other languages.

❌ 3. Not Type-Safe

Mixed data types can lead to logic errors if not handled carefully.

❌ 4. Searching is O(n)

Linear search is required unless the list is sorted.

❌ 5. Not Efficient for Queue Operations

pop(0) or insert(0, value) is slow because entire list shifts.

### Summary Table

| Feature           | Details                                   |
| ----------------- | ----------------------------------------- |
| Ordered           | Yes                                       |
| Mutable           | Yes                                       |
| Duplicate Allowed | Yes                                       |
| Heterogeneous     | Yes                                       |
| Implementation    | Dynamic Array                             |
| Best Use Cases    | Iteration, random access, general storage |

----

## **Tuple ()**

A tuple in Python is an immutable, ordered data structure used to store multiple items in a single variable.
Unlike lists, tuples cannot be modified after creation, making them ideal for fixed, secure, and read-only data.

Python tuples:

Cannot be changed after creation (immutable)

Can store mixed data types

Maintain order

Are stored more efficiently than lists

Are commonly used for:

Fixed collections of values

Returning multiple values from functions

Using as dictionary keys (because they are hashable)

Tuples are ideal when you want to protect data from modification and ensure stable, predictable structure.

### Key Characteristics of Tuples

### ✔ Ordered

Tuples preserve the order of elements.

```
t = (10, 20, 30)
# index: 0   1   2
```

### ✔ Immutable (cannot be changed)
You cannot modify, add, or delete elements once created.

```
t = (1, 2, 3)
# t[1] = 99  ❌ Not allowed – TypeError
```

### ✔ Allows Duplicate Values
Tuples can contain repeated values.

```
t = (1, 2, 2, 3)
```

### ✔ Supports Heterogeneous Data
Tuples can store different data types.

```
t = (10, "hello", 3.14, True)
```

### ✔ Indexing & Slicing Supported
You can access individual items or sub-tuples.

```
t = (10, 20, 30, 40, 50)
print(t[2])    # 30
print(t[1:4])  # (20, 30, 40)
```

#### ✔ Hashable (if all elements are hashable)
Tuples can be used as keys in dictionaries.

```
coords = {(10, 20): "Location A"}
```

### Examples of Tuples Usage
#### **Creating Tuples**

```
t1 = (1, 2, 3)
t2 = ("apple", 10, 3.14)
t3 = ()            # empty tuple
t4 = (5,)          # single-element tuple (comma required)
```

#### **Accessing Elements**

```
t = (10, 20, 30)
print(t[0])   # 10
print(t[-1])  # 30
```

#### **Tuple Unpaking**
Useful for returning multiple values.

```
point = (5, 10)
x, y = point
```

#### **Iteration**

```
for item in (1, 2, 3):
    print(item)
```

#### **Membership Test**

```
t = (1, 2, 3)
print(2 in t)   # True
```

#### Concatenation & Repetition

```
a = (1, 2)
b = (3, 4)
print(a + b)     # (1,2,3,4)

print(a * 3)     # (1,2,1,2,1,2)
```

#### Using Tuples as Dictionary Keys

```
location = {}
location[(10.5, 20.7)] = "Home"
```

### **Advantages of Tuples**

✅ 1. Faster than Lists

Since they are immutable, Python can optimize memory and access speed.

✅ 2. Immutable (Data Safety)

Prevents accidental modification.

Useful in:

Multi-threaded programs

Configuration values

Constant datasets

✅ 3. Hashable

Can be used as keys in dictionaries and elements of sets.

✅ 4. Lower Memory Usage

Tuples consume less memory than lists.

✅ 5. Ideal for Fixed Data

Such as coordinates, RGB values, dates, database records, etc.

### **Disadvantages of Tuples**

❌ 1. Immutable

You cannot:

Add elements

Remove elements

Modify elements

This limits flexibility.

❌ 2. Not Suitable for Dynamic Data

If the data changes frequently, use a list instead.

❌ 3. Fewer Built-in Methods

Tuples only support:

count()

index()

Unlike lists (append, remove, insert, etc.).

❌ 4. Harder to Modify Complex Data Structures

If you need to update values often, tuple is not ideal.

### Summary Table

| Feature           | Details                                     |
| ----------------- | ------------------------------------------- |
| Ordered           | Yes                                         |
| Mutable           | ❌ No                                        |
| Duplicate Allowed | Yes                                         |
| Heterogeneous     | Yes                                         |
| Implementation    | Immutable sequence                          |
| Best Use Cases    | Fixed data, keys in dict, efficient reading |

## **set {}**

A set in Python is an unordered, mutable, and unique-element data structure used to store a collection of distinct items.

Python sets:

Store only unique values

Are unordered

Are mutable

Provide O(1) average time complexity for add, remove, check operations

Support powerful set operations: union, intersection, difference, symmetric difference

Sets are ideal when you need fast membership testing, duplicate removal, or mathematical set operations.

### Key Characteristics of Sets

✔ Unordered

Set elements do not maintain insertion order.
You cannot rely on indexing.

```
s = {10, 20, 30}
# No index positions
```

✔ Contains Only Unique Elements

Duplicates are automatically removed.

```
s = {1, 2, 2, 3}
print(s)   # {1, 2, 3}
```

✔ Mutable (can be changed)

You can add or remove elements.

```
s = {1, 2, 3}
s.add(4)
s.remove(2)
```

✔ Only Hashable Elements Allowed

You can store:

int

float

string

tuple

But not:

lists

dicts

sets

```
s = {1, "hello", (2, 3)}   # valid
# s = {[1, 2], 3}         # ❌ TypeError
```

✔ No Indexing or Slicing

This will give an error:

```
s = {1, 2, 3}
# s[0] ❌ Not allowed
```

✔ Fast Membership Testing

Checking membership is extremely fast (O(1)).

```
if 10 in {10, 20, 30}:
    print("Exists")
```

### Examples of Set Usage

**Creating Sets**

```
s1 = {1, 2, 3}
s2 = set([4, 5, 6])
s3 = set()        # empty set
```

**Adding Elements**

```
s = {1, 2}
s.add(3)
s.update([4, 5, 6])    # Add multiple items
```

**Removing Elements**

```
s = {1, 2, 3}
s.remove(2)   # removes 2, errors if not found
s.discard(5)  # no error if 5 not found
s.pop()       # removes a random element
s.clear()     # removes all elements
```

**Checking Membership**

```
s = {1, 2, 3}
print(2 in s)   # True
print(4 in s)   # False
```

### **Advantages of Sets**

✅ 1. Fast Membership Testing

Checking x in set is O(1) on average.

✅ 2. No Duplicates

Automatically removes duplicate values.

✅ 3. Efficient Mathematical Operations

Union, intersection, etc., are highly optimized.

✅ 4. Good for Data Cleaning

Easily remove duplicates from lists:

```
unique_list = list(set([1,2,2,3,3,4]))
```

✅ 5. Mutable but Elements Must Be Hashable

Allows adding/removing items efficiently.

### **Disadvantages of Sets**

❌ 1. Unordered

You cannot rely on element positions; indexing is not supported.

❌ 2. Cannot Store Unhashable Items

Lists, dicts, and sets cannot be stored.

❌ 3. No Duplicate Allowed

Sometimes you want duplicates (e.g., counting).

❌ 4. Random Element Removal with pop()

Not ideal for predictable removals.

❌ 5. Not Suitable for Ordered Tasks

If you need order → use list
If you need sorted order → use sorted(), list, or OrderedSet (3rd-party)

### Summary Table

| Feature            | Details                                                  |
| ------------------ | -------------------------------------------------------- |
| Ordered            | ❌ No                                                     |
| Mutable            | ✔ Yes                                                    |
| Duplicates Allowed | ❌ No                                                     |
| Heterogeneous      | ✔ Yes                                                    |
| Implementation     | Hash Table                                               |
| Best Use Cases     | Membership testing, removing duplicates, math operations |





