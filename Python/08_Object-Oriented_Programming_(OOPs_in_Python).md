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
