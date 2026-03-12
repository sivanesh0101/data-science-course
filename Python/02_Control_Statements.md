## 1. Control Statements
A control statement in Python is used to control the flow of execution of a program —
that means deciding which part of the code should run and when.

### Types of Control Statements
<p align="center">
if

else

elif
</p>

### 1.1 if Statement:

The if statement is a decision-making statement.

It allows your program to execute a block of code only if a certain condition is true.

#### Syntax
<p align="center">
<img width="369" height="103" alt="image" src="https://github.com/user-attachments/assets/8519d604-3e40-4861-ae78-0cff6c9ebf9f" />
</p>


#### Example
```
age = 20

if age >= 18:
    print("You are eligible to vote.")
```
### 1.2 if...else Statement
Used when you want to do one thing if the condition is true, and something else if it’s false.

#### Syntax

<p align="center">
<img width="433" height="154" alt="image" src="https://github.com/user-attachments/assets/b67754c8-2306-4e06-bcd4-04521ef510c5" />
</p>

#### Example
```
age = 16

if age >= 18:
    print("Eligible to vote")
else:
    print("Not eligible to vote")
```
### 1.3 elif Statement
Used when you have multiple conditions to check.

#### Syntax
<p align="center">
<img width="623" height="254" alt="image" src="https://github.com/user-attachments/assets/5f613ec7-debe-4512-abaf-6af45aeee885" />
</p>

#### Example

```
marks = 85

if marks >= 90:
    print("Grade A")
elif marks >= 75:
    print("Grade B")
elif marks >= 60:
    print("Grade C")
else:
    print("Fail")
```
### 1.4 Nested `if`

A `nested if` statement means an if statement **inside another** if statement.

It allows you to check multiple conditions one inside another — useful for complex decision-making.

#### Syntax
<p align="center">
<img width="654" height="251" alt="image" src="https://github.com/user-attachments/assets/2d2cc0a9-b243-41d0-b01a-ef26bfc6c508" />
</p>

#### Example
```
age = 20
citizen = True

if citizen:
    if age >= 18:
        print("You are eligible to vote.")
    else:
        print("You must be 18 or older to vote.")
else:
    print("You must be a citizen to vote.")
```
### 1.5 Indentation is Important
```
if True:
print("Hello")   # ❌ Error — no indentation

if True:
    print("Hello")  # ✅ Correct
```
### 1.6 Summary

| **Type**           | **Description**                    | **Example**              |
| ------------------ | ---------------------------------- | ------------------------ |
| `if`               | Executes code if condition is true | `if x > 0:`              |
| `if...else`        | Either one block executes          | `if x>0: else:`          |
| `if...elif...else` | Multiple conditions                | `if x>0 elif x==0 else:` |
| Nested `if`        | One `if` inside another            | `if x>0: if x%2==0:`     |

### Python Programming Practice Report (control statements)
```
Control Statements

1.Ask the user for their age — print if they are a child, teenager, or adult.

2.Take temperature input — print “Hot”, “Warm”, or “Cold”.

3.Ask for a number — print if it’s even or odd.

4.Ask for marks — print the grade (A/B/C/Fail).

5.Ask for a password — print “Access granted” only if correct.
```
