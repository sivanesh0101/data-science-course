# employees2 table

| emp_id | name      | department | salary | join_date  |
| ------ | --------- | ---------- | ------ | ---------- |
| 101    | Arjun     | HR         | 35000  | 2021-03-15 |
| 102    | Meera     | IT         | 55000  | 2020-07-10 |
| 103    | Rahul     | Finance    | 45000  | 2022-01-05 |
| 104    | Sneha     | IT         | 60000  | 2019-11-20 |
| 105    | Kiran     | Marketing  | 30000  | 2021-06-01 |
| 106    | Priya     | Finance    | 48000  | 2020-02-12 |
| 107    | Varun     | IT         | 62000  | 2023-04-18 |
| 108    | Divya     | HR         | 37000  | 2021-09-22 |
| 109    | Sanjay    | Marketing  | 32000  | 2018-12-11 |
| 110    | Kavya     | IT         | 58000  | 2022-06-25 |
| 111    | Rohit     | Finance    | 52000  | 2019-08-30 |
| 112    | Aishwarya | HR         | 40000  | 2023-01-14 |
| 113    | Mohan     | Marketing  | 28000  | 2020-10-03 |
| 114    | Teja      | IT         | 65000  | 2017-05-19 |
| 115    | Vignesh   | Finance    | 47000  | 2021-12-09 |


## Create employees2 Table

```CREATE TABLE employees2 (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50),
    salary INT,
    join_date DATE
);
```
## Insert Data into employees2 Table

```
INSERT INTO employees2 (emp_id, name, department, salary, join_date) VALUES
(101, 'Arjun', 'HR', 35000, '2021-03-15'),
(102, 'Meera', 'IT', 55000, '2020-07-10'),
(103, 'Rahul', 'Finance', 45000, '2022-01-05'),
(104, 'Sneha', 'IT', 60000, '2019-11-20'),
(105, 'Kiran', 'Marketing', 30000, '2021-06-01'),
(106, 'Priya', 'Finance', 48000, '2020-02-12'),
(107, 'Varun', 'IT', 62000, '2023-04-18'),
(108, 'Divya', 'HR', 37000, '2021-09-22'),
(109, 'Sanjay', 'Marketing', 32000, '2018-12-11'),
(110, 'Kavya', 'IT', 58000, '2022-06-25'),
(111, 'Rohit', 'Finance', 52000, '2019-08-30'),
(112, 'Aishwarya', 'HR', 40000, '2023-01-14'),
(113, 'Mohan', 'Marketing', 28000, '2020-10-03'),
(114, 'Teja', 'IT', 65000, '2017-05-19'),
(115, 'Vignesh', 'Finance', 47000, '2021-12-09');
```

# Interview Questions

1. Write a query to display all records from the employees table.

```
SELECT * FROM employees2;
```

2. Write a query to display only emp_id and name.

4. Write a query to find all employees working in the IT department.
5. Write a query to find employees whose salary is greater than 40,000.
6. Write a query to sort employees by salary in descending order.
7. Write a query to get the highest salary from the employees table.
8. Write a query to count the number of employees in each department.
9. Write a query to find employees who joined after 2021-01-01.
10. Write a query to find the total salary paid to all employees.
11. Write a query to update the salary of employee with emp_id 103 to 50000.
12. Write a query to delete an employee who works in the Marketing department.
13. Write a query to find the minimum salary in the IT department.
14. Write a query to display employees whose name starts with 'S'.
15. Write a query to find employees where salary is between 30,000 and 50,000.
16. Write a query to group employees by department and show average salary.
17. Write a query to display employees ordered by join_date (oldest first).
18. Write a query to rename the column "name" to "employee_name" in output (using alias).
