# OOPs Concept in Python

OOPS (Object-Oriented Programming System) is a programming paradigm that organizes software design around objects—entities that contain both data (attributes) and behaviors (methods).  Its goal is to make code modular, secure, reusable, and easier to maintain

<p align="center">
<img width="698" height="328" alt="Screenshot 2025-11-25 191134" src="https://github.com/user-attachments/assets/0bbe46cb-32ce-4a08-8f1f-6d0b8a3a32ec" />
</p>

## Python’s four core OOP pillars:

<p align="center">
<img width="565" height="406" alt="Screenshot 2025-11-25 183132" src="https://github.com/user-attachments/assets/185207fa-d592-48e1-9daa-9ac0bd31966b" />

</p>


# Object-Oriented Programming (OOP) in Python

## Introduction

Object-Oriented Programming (OOP) is a programming paradigm that organizes code using "objects" and "classes". It helps in writing clean, reusable, and scalable code.

---

## 1. What is a Class?

A class is a blueprint or template used to create objects. It defines properties (variables) and behaviors (functions).

### Example:

```python
class Car:
    color = "red"

    def drive(self):
        print("Car is moving")
```

---

## 2. What is an Object?

An object is an instance of a class. It represents a real-world entity.

### Example:

```python
c1 = Car()
print(c1.color)
c1.drive()
```

---

## 3. The `__init__` Method (Constructor)

The `__init__` method is a special method that is automatically called when an object is created. It is used to initialize object attributes.

### Example:

```python
class Car:
    def __init__(self, color):
        self.color = color

c1 = Car("blue")
print(c1.color)
```

---

## 4. The `self` Keyword

* `self` refers to the current instance of the class.
* It is used to access variables and methods within the class.

---

## 5. Instance Variables vs Class Variables

### Instance Variables

* Unique to each object
* Defined inside `__init__`

```python
class Car:
    def __init__(self, color):
        self.color = color
```

### Class Variables

* Shared across all objects
* Defined outside methods

```python
class Car:
    wheels = 4
```

---

## 6. Methods in Classes

### Instance Methods

Work with object data

```python
def drive(self):
    print("Driving")
```

### Class Methods

```python
@classmethod
def info(cls):
    print("This is a class method")
```

### Static Methods

```python
@staticmethod
def greet():
    print("Hello")
```

---

## 7. Four Pillars of OOP

### 1. Encapsulation

Bundling data and methods together.

```python
class Bank:
    def __init__(self, balance):
        self.__balance = balance
```

---

### 2. Inheritance

One class inherits properties from another.

```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Dog(Animal):
    pass
```

---

### 3. Polymorphism

Same method name behaves differently.

```python
class Dog:
    def sound(self):
        print("Bark")

class Cat:
    def sound(self):
        print("Meow")
```

---

### 4. Abstraction

Hiding implementation details.

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass
```

---

## 8. Inheritance Types

* Single Inheritance
* Multiple Inheritance
* Multilevel Inheritance
* Hierarchical Inheritance

---

## 9. Example: Simple Student System

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def display(self):
        print(self.name, self.marks)

s1 = Student("Siva", 90)
s1.display()
```

---

## 10. Advantages of OOP

* Code reusability
* Better organization
* Easy debugging
* Scalability

---

## Conclusion

OOP helps structure programs using real-world concepts. By using classes and objects, developers can write modular, reusable, and maintainable code.

---

## Next Steps

* Practice creating classes and objects
* Build small projects (Bank system, Library system)
* Learn advanced concepts like decorators and design patterns
