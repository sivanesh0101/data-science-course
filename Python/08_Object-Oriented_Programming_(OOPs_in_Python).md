# OOPs Concept in Python

OOPS (Object-Oriented Programming System) is a programming paradigm that organizes software design around objects—entities that contain both data (attributes) and behaviors (methods).  Its goal is to make code modular, secure, reusable, and easier to maintain

<p align="center">
<img width="698" height="328" alt="Screenshot 2025-11-25 191134" src="https://github.com/user-attachments/assets/0bbe46cb-32ce-4a08-8f1f-6d0b8a3a32ec" />
</p>

## Python’s four core OOP pillars:

<p align="center">
<img width="565" height="406" alt="Screenshot 2025-11-25 183132" src="https://github.com/user-attachments/assets/185207fa-d592-48e1-9daa-9ac0bd31966b" />

</p>


# Object-Oriented Programming (OOP) in Python — Explained with a Banking System

## Introduction

Object-Oriented Programming (OOP) helps you model real-world systems in code. Instead of writing random functions, you organize everything into structured units called classes and objects.

We will understand every concept using a simple banking system.

---

## 1. Why OOP? (Problem Without It)

Imagine writing a banking app using only functions:

```python
balance = 1000

def deposit(amount):
    global balance
    balance += amount

def withdraw(amount):
    global balance
    balance -= amount
```

Problems:

* Only one account can exist
* Data is not secure
* Not reusable
* Hard to scale

This is where OOP solves everything.

---

## 2. Class and Object

A class is a blueprint. An object is a real instance.

### Banking Example

```python
class BankAccount:
    def __init__(self, name, balance):
        self.name = name
        self.balance = balance
```

Create objects:

```python
acc1 = BankAccount("Siva", 1000)
acc2 = BankAccount("Ravi", 500)
```

Now:

* acc1 and acc2 are separate accounts
* Each has its own data

---

## 3. Understanding `__init__` Clearly

```python
def __init__(self, name, balance):
    self.name = name
    self.balance = balance
```

When you do:

```python
acc1 = BankAccount("Siva", 1000)
```

Python automatically runs:

```python
__init__(acc1, "Siva", 1000)
```

This sets:

* acc1.name = "Siva"
* acc1.balance = 1000

---

## 4. Adding Behavior (Methods)

```python
class BankAccount:
    def __init__(self, name, balance):
        self.name = name
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount
        print("Deposited:", amount)

    def withdraw(self, amount):
        if amount > self.balance:
            print("Insufficient balance")
        else:
            self.balance -= amount
            print("Withdrawn:", amount)

    def check_balance(self):
        print("Balance:", self.balance)
```

Usage:

```python
acc1 = BankAccount("Siva", 1000)

acc1.deposit(500)
acc1.withdraw(200)
acc1.check_balance()
```

---

## 5. Encapsulation (Data Protection)

We should not allow direct access to balance.

```python
class BankAccount:
    def __init__(self, name, balance):
        self.name = name
        self.__balance = balance   # private variable

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance
```

Now:

* `__balance` cannot be accessed directly
* Controlled access improves security

---

## 6. Inheritance (Reusing Code)

Let’s create different account types.

```python
class BankAccount:
    def __init__(self, name, balance):
        self.name = name
        self.balance = balance

    def show(self):
        print(self.name, self.balance)


class SavingsAccount(BankAccount):
    def add_interest(self):
        self.balance += self.balance * 0.05


class CurrentAccount(BankAccount):
    def overdraft(self):
        print("Overdraft allowed")
```

Usage:

```python
s1 = SavingsAccount("Siva", 1000)
s1.add_interest()
s1.show()
```

---

## 7. Polymorphism (Same Method, Different Behavior)

```python
class SavingsAccount:
    def interest(self):
        print("Savings interest: 5%")

class FixedDeposit:
    def interest(self):
        print("FD interest: 7%")
```

Usage:

```python
accounts = [SavingsAccount(), FixedDeposit()]

for acc in accounts:
    acc.interest()
```

Same method name, different behavior.

---

## 8. Abstraction (Hiding Internal Logic)

```python
from abc import ABC, abstractmethod

class Bank(ABC):
    @abstractmethod
    def loan(self):
        pass

class SBI(Bank):
    def loan(self):
        print("Providing loan")
```

User only sees "loan", not how it works internally.

---

## 9. Final Combined Example

```python
class BankAccount:
    def __init__(self, name, balance):
        self.name = name
        self.__balance = balance

    def deposit(self, amount):
        self.__balance += amount

    def withdraw(self, amount):
        if amount <= self.__balance:
            self.__balance -= amount

    def get_balance(self):
        return self.__balance


class SavingsAccount(BankAccount):
    def add_interest(self):
        self._BankAccount__balance += self._BankAccount__balance * 0.05


acc = SavingsAccount("Siva", 1000)
acc.deposit(500)
acc.add_interest()
print(acc.get_balance())
```

---

## 10. Key Takeaways

* Class = blueprint
* Object = real instance
* `__init__` initializes data
* Encapsulation protects data
* Inheritance reuses code
* Polymorphism allows flexibility
* Abstraction hides complexity

---

## Conclusion

Using OOP, you can build scalable systems like real banking applications where each user has independent data, secure transactions, and reusable code structure.

---


# Object-Oriented Programming (OOP) Concepts

> A complete guide to OOP principles with real-world examples in Python and Java.

---

## Table of Contents
1. [Class & Object](#1-class--object)
2. [Encapsulation](#2-encapsulation)
3. [Abstraction](#3-abstraction)
4. [Inheritance](#4-inheritance)
5. [Polymorphism](#5-polymorphism)
6. [Association, Aggregation & Composition](#6-association-aggregation--composition)
7. [Method Overloading & Overriding](#7-method-overloading--overriding)
8. [Interfaces](#8-interfaces)
9. [Static & Instance Members](#9-static--instance-members)
10. [SOLID Principles (Quick Reference)](#10-solid-principles-quick-reference)

---

## 1. Class & Object

A **Class** is a blueprint. An **Object** is an instance of that class.

### Python
```python
class Car:
    def __init__(self, brand, model, year):
        self.brand = brand
        self.model = model
        self.year = year

    def display_info(self):
        return f"{self.year} {self.brand} {self.model}"

# Creating Objects
car1 = Car("Toyota", "Camry", 2022)
car2 = Car("Tesla", "Model 3", 2024)

print(car1.display_info())  # 2022 Toyota Camry
print(car2.display_info())  # 2024 Tesla Model 3
```

### Java
```java
class Car {
    String brand, model;
    int year;

    Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }

    String displayInfo() {
        return year + " " + brand + " " + model;
    }

    public static void main(String[] args) {
        Car car1 = new Car("Toyota", "Camry", 2022);
        Car car2 = new Car("Tesla", "Model 3", 2024);
        System.out.println(car1.displayInfo()); // 2022 Toyota Camry
        System.out.println(car2.displayInfo()); // 2024 Tesla Model 3
    }
}
```

---

## 2. Encapsulation

**Encapsulation** is the bundling of data and methods that operate on that data, restricting direct access to some components using access modifiers (`private`, `protected`, `public`).

> 🔑 **Key Idea:** Hide internal state, expose only what's necessary via getters/setters.

### Python
```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.__balance = balance  # Private attribute

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            print(f"Deposited ₹{amount}. New balance: ₹{self.__balance}")

    def withdraw(self, amount):
        if amount > self.__balance:
            print("Insufficient funds!")
        else:
            self.__balance -= amount
            print(f"Withdrawn ₹{amount}. Remaining: ₹{self.__balance}")

    def get_balance(self):
        return self.__balance  # Controlled access

account = BankAccount("Alice", 1000)
account.deposit(500)       # Deposited ₹500. New balance: ₹1500
account.withdraw(200)      # Withdrawn ₹200. Remaining: ₹1300
# account.__balance = 9999  ❌ This won't affect the real private balance
```

### Java
```java
class BankAccount {
    private String owner;
    private double balance;

    public BankAccount(String owner, double balance) {
        this.owner = owner;
        this.balance = balance;
    }

    public void deposit(double amount) {
        if (amount > 0) balance += amount;
    }

    public void withdraw(double amount) {
        if (amount > balance) System.out.println("Insufficient funds!");
        else balance -= amount;
    }

    public double getBalance() { return balance; } // Getter
    public String getOwner()   { return owner; }   // Getter
}
```

---

## 3. Abstraction

**Abstraction** means hiding complex implementation details and showing only the essential features. Achieved via **abstract classes** and **interfaces**.

> 🔑 **Key Idea:** *What* it does, not *how* it does it.

### Python
```python
from abc import ABC, abstractmethod

class Shape(ABC):  # Abstract class
    @abstractmethod
    def area(self):
        pass

    @abstractmethod
    def perimeter(self):
        pass

    def describe(self):  # Concrete method
        return f"I am a {self.__class__.__name__}"

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14159 * self.radius ** 2

    def perimeter(self):
        return 2 * 3.14159 * self.radius

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

shapes = [Circle(5), Rectangle(4, 6)]
for shape in shapes:
    print(f"{shape.describe()} | Area: {shape.area():.2f} | Perimeter: {shape.perimeter():.2f}")
```

---

## 4. Inheritance

**Inheritance** allows a class (child) to acquire properties and methods from another class (parent), promoting code reuse.

### Types of Inheritance

| Type | Description |
|------|-------------|
| Single | One child inherits from one parent |
| Multi-level | Chain of inheritance (A → B → C) |
| Multiple | One child inherits from multiple parents |
| Hierarchical | Multiple children from one parent |

### Python
```python
class Animal:
    def __init__(self, name, sound):
        self.name = name
        self.sound = sound

    def speak(self):
        return f"{self.name} says {self.sound}!"

    def breathe(self):
        return f"{self.name} breathes air."

# Single Inheritance
class Dog(Animal):
    def __init__(self, name):
        super().__init__(name, "Woof")  # Call parent constructor

    def fetch(self):
        return f"{self.name} fetches the ball! 🎾"

# Multi-level Inheritance
class Puppy(Dog):
    def __init__(self, name):
        super().__init__(name)

    def play(self):
        return f"{self.name} loves to play! 🐶"

dog = Dog("Buddy")
puppy = Puppy("Max")

print(dog.speak())    # Buddy says Woof!
print(dog.fetch())    # Buddy fetches the ball! 🎾
print(puppy.speak())  # Max says Woof!   ← inherited from Animal
print(puppy.fetch())  # Max fetches the ball! 🎾  ← inherited from Dog
print(puppy.play())   # Max loves to play! 🐶
```

### Java
```java
class Animal {
    String name;
    Animal(String name) { this.name = name; }
    void breathe() { System.out.println(name + " breathes air."); }
}

class Dog extends Animal {
    Dog(String name) { super(name); }
    void speak() { System.out.println(name + " says Woof!"); }
}

class Puppy extends Dog {
    Puppy(String name) { super(name); }
    void play() { System.out.println(name + " loves to play!"); }
}
```

---

## 5. Polymorphism

**Polymorphism** means "many forms" — the same interface behaves differently based on the object. Two types:
- **Compile-time (Static):** Method Overloading
- **Run-time (Dynamic):** Method Overriding

### Python — Runtime Polymorphism
```python
class Payment:
    def pay(self, amount):
        raise NotImplementedError

class CreditCard(Payment):
    def pay(self, amount):
        return f"💳 Paid ₹{amount} via Credit Card."

class UPI(Payment):
    def pay(self, amount):
        return f"📱 Paid ₹{amount} via UPI."

class NetBanking(Payment):
    def pay(self, amount):
        return f"🏦 Paid ₹{amount} via Net Banking."

# Polymorphic behavior
methods = [CreditCard(), UPI(), NetBanking()]
for method in methods:
    print(method.pay(500))

# 💳 Paid ₹500 via Credit Card.
# 📱 Paid ₹500 via UPI.
# 🏦 Paid ₹500 via Net Banking.
```

### Java — Compile-time Polymorphism (Overloading)
```java
class Calculator {
    int add(int a, int b)           { return a + b; }
    double add(double a, double b)  { return a + b; }
    int add(int a, int b, int c)    { return a + b + c; }

    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(2, 3));         // 5
        System.out.println(calc.add(2.5, 3.5));     // 6.0
        System.out.println(calc.add(1, 2, 3));      // 6
    }
}
```

---

## 6. Association, Aggregation & Composition

These define **relationships between classes**.

| Relationship | Type | Lifecycle |
|---|---|---|
| Association | "uses-a" / "knows-a" | Independent |
| Aggregation | "has-a" (weak) | Child can exist without parent |
| Composition | "has-a" (strong) | Child cannot exist without parent |

### Python
```python
# ── ASSOCIATION ──────────────────────────────────────
class Driver:
    def __init__(self, name): self.name = name

class Car:
    def __init__(self, model): self.model = model
    def drive(self, driver):
        return f"{driver.name} is driving {self.model}."  # Just uses Driver

# ── AGGREGATION ──────────────────────────────────────
class Player:
    def __init__(self, name): self.name = name

class Team:
    def __init__(self, name, players):
        self.name = name
        self.players = players  # Players exist independently of Team

    def roster(self):
        return [p.name for p in self.players]

# ── COMPOSITION ──────────────────────────────────────
class Engine:
    def __init__(self, horsepower):
        self.horsepower = horsepower

    def start(self):
        return f"Engine with {self.horsepower}hp started 🔥"

class SportsCar:
    def __init__(self, model, horsepower):
        self.model = model
        self.engine = Engine(horsepower)  # Engine is CREATED inside SportsCar

    def start(self):
        return f"{self.model}: {self.engine.start()}"

car = SportsCar("Ferrari F40", 478)
print(car.start())  # Ferrari F40: Engine with 478hp started 🔥
# If SportsCar is deleted, Engine ceases to exist too.
```

---

## 7. Method Overloading & Overriding

### Overloading (same name, different parameters)
```python
# Python achieves overloading via default args or *args
class MathUtils:
    def multiply(self, *args):
        result = 1
        for n in args:
            result *= n
        return result

m = MathUtils()
print(m.multiply(3, 4))       # 12
print(m.multiply(2, 3, 4))    # 24
print(m.multiply(1, 2, 3, 4)) # 24
```

### Overriding (child redefines parent's method)
```python
class Employee:
    def __init__(self, name, base_salary):
        self.name = name
        self.base_salary = base_salary

    def calculate_salary(self):
        return self.base_salary

class Manager(Employee):
    def __init__(self, name, base_salary, bonus):
        super().__init__(name, base_salary)
        self.bonus = bonus

    def calculate_salary(self):  # ✅ Overrides parent method
        return self.base_salary + self.bonus

class Intern(Employee):
    def calculate_salary(self):  # ✅ Overrides parent method
        return self.base_salary * 0.5  # Half pay

employees = [
    Employee("Bob", 50000),
    Manager("Alice", 80000, 20000),
    Intern("Charlie", 30000),
]

for emp in employees:
    print(f"{emp.name}: ₹{emp.calculate_salary()}")
# Bob: ₹50000
# Alice: ₹100000
# Charlie: ₹15000
```

---

## 8. Interfaces

An **Interface** defines a contract — a set of methods a class *must* implement. Python uses `ABC`, Java uses `interface`.

### Python
```python
from abc import ABC, abstractmethod

class Flyable(ABC):
    @abstractmethod
    def fly(self): pass

class Swimmable(ABC):
    @abstractmethod
    def swim(self): pass

class Duck(Flyable, Swimmable):  # Implements both interfaces
    def fly(self):
        return "Duck is flying 🦆"

    def swim(self):
        return "Duck is swimming 🌊"

class Eagle(Flyable):  # Implements only Flyable
    def fly(self):
        return "Eagle soars high 🦅"

duck = Duck()
eagle = Eagle()
print(duck.fly())    # Duck is flying 🦆
print(duck.swim())   # Duck is swimming 🌊
print(eagle.fly())   # Eagle soars high 🦅
```

### Java
```java
interface Flyable  { void fly();  }
interface Swimmable { void swim(); }

class Duck implements Flyable, Swimmable {
    public void fly()  { System.out.println("Duck is flying 🦆"); }
    public void swim() { System.out.println("Duck is swimming 🌊"); }
}

class Eagle implements Flyable {
    public void fly() { System.out.println("Eagle soars high 🦅"); }
}
```

---

## 9. Static & Instance Members

| Feature | Instance | Static |
|---|---|---|
| Belongs to | Each object | The class itself |
| Access | `self.attr` | `ClassName.attr` |
| Use case | Object-specific data | Shared/global data |

```python
class Counter:
    total_count = 0  # ← Static (class variable)

    def __init__(self, name):
        self.name = name         # ← Instance variable
        Counter.total_count += 1

    @staticmethod
    def get_total():             # ← Static method
        return Counter.total_count

    @classmethod
    def reset(cls):              # ← Class method
        cls.total_count = 0

c1 = Counter("First")
c2 = Counter("Second")
c3 = Counter("Third")

print(Counter.get_total())  # 3
Counter.reset()
print(Counter.get_total())  # 0
```

---

## 10. SOLID Principles (Quick Reference)

| Letter | Principle | Meaning |
|--------|-----------|---------|
| **S** | Single Responsibility | A class should have only one reason to change |
| **O** | Open/Closed | Open for extension, closed for modification |
| **L** | Liskov Substitution | Subclasses must be substitutable for parent class |
| **I** | Interface Segregation | Many specific interfaces > one general interface |
| **D** | Dependency Inversion | Depend on abstractions, not concretions |

### Example — Single Responsibility Principle
```python
# ❌ BAD: One class doing too many things
class UserManager:
    def save_to_db(self, user): ...
    def send_email(self, user): ...
    def generate_report(self, user): ...

# ✅ GOOD: Each class has one responsibility
class UserRepository:
    def save(self, user): ...

class EmailService:
    def send_welcome(self, user): ...

class ReportGenerator:
    def generate(self, user): ...
```

### Example — Open/Closed Principle
```python
# ✅ GOOD: Add new shapes without modifying existing code
class Shape(ABC):
    @abstractmethod
    def area(self): pass

class Circle(Shape):
    def __init__(self, r): self.r = r
    def area(self): return 3.14 * self.r ** 2

class Triangle(Shape):  # ← extend without modifying Shape
    def __init__(self, b, h): self.b, self.h = b, h
    def area(self): return 0.5 * self.b * self.h

def total_area(shapes):
    return sum(s.area() for s in shapes)  # Works for ALL shapes!

print(total_area([Circle(5), Triangle(4, 6)]))  # 98.5
```

---

## Summary Cheat Sheet

```
┌─────────────────────────────────────────────────────────┐
│                   OOP CONCEPTS                          │
├──────────────────┬──────────────────────────────────────┤
│ Class & Object   │ Blueprint → Instance                 │
│ Encapsulation    │ Bundle data + restrict access        │
│ Abstraction      │ Hide complexity, show essentials     │
│ Inheritance      │ Child reuses parent code             │
│ Polymorphism     │ Same interface, different behavior   │
│ Association      │ "uses-a" — independent objects       │
│ Aggregation      │ "has-a" — weak ownership             │
│ Composition      │ "has-a" — strong ownership           │
│ Overloading      │ Same name, different parameters      │
│ Overriding       │ Child redefines parent method        │
│ Interface        │ Contract a class must fulfill        │
│ Static Members   │ Shared across all instances          │
└──────────────────┴──────────────────────────────────────┘
```

---

*Happy Coding! 🚀*
