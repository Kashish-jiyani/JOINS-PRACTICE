
Name: Kashish Jiyani

Company: CODTECH IT SOLUTIONS

ID :CT08LQI

Domain: SQL

Tasks Duration: January 10th,2025 to February 10th, 2025.

Mentor:Santhosh
# JOINS-PRACTICE
To perform `INNER`, `LEFT`, `RIGHT`, and `FULL` joins on tables and combine data meaningfully, let’s break down each join type and show some SQL examples.

### 1. **INNER JOIN**:
An `INNER JOIN` returns records that have matching values in both tables.

**Example:**

You have two tables:

- **Employees**:
  | EmployeeID | Name    | DepartmentID |
  |------------|---------|--------------|
  | 1          | Alice   | 101          |
  | 2          | Bob     | 102          |
  | 3          | Charlie | 103          |

- **Departments**:
  | DepartmentID | DepartmentName |
  |--------------|----------------|
  | 101          | HR             |
  | 102          | IT             |
  | 104          | Marketing      |

**SQL Query:**
```sql
SELECT Employees.EmployeeID, Employees.Name, Departments.DepartmentName
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

**Result:**
| EmployeeID | Name    | DepartmentName |
|------------|---------|----------------|
| 1          | Alice   | HR             |
| 2          | Bob     | IT             |

**Explanation:**
The `INNER JOIN` matches rows where the `DepartmentID` exists in both the `Employees` and `Departments` tables.

---

### 2. **LEFT JOIN** (or **LEFT OUTER JOIN**):
A `LEFT JOIN` returns all records from the left table and the matching records from the right table. If there is no match, NULL values are returned for columns from the right table.

**SQL Query:**
```sql
SELECT Employees.EmployeeID, Employees.Name, Departments.DepartmentName
FROM Employees
LEFT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

**Result:**
| EmployeeID | Name    | DepartmentName |
|------------|---------|----------------|
| 1          | Alice   | HR             |
| 2          | Bob     | IT             |
| 3          | Charlie | NULL           |

**Explanation:**
The `LEFT JOIN` ensures that all employees are included, even if they don't belong to a department. For Charlie, there is no department with `DepartmentID = 103`, so the `DepartmentName` is `NULL`.

---

### 3. **RIGHT JOIN** (or **RIGHT OUTER JOIN**):
A `RIGHT JOIN` returns all records from the right table and the matching records from the left table. If there is no match, NULL values are returned for columns from the left table.

**SQL Query:**
```sql
SELECT Employees.EmployeeID, Employees.Name, Departments.DepartmentName
FROM Employees
RIGHT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

**Result:**
| EmployeeID | Name    | DepartmentName |
|------------|---------|----------------|
| 1          | Alice   | HR             |
| 2          | Bob     | IT             |
| NULL       | NULL    | Marketing      |

**Explanation:**
The `RIGHT JOIN` ensures that all departments are included, even if no employees are assigned to them. The `DepartmentID = 104` (Marketing) has no matching employees, so the employee fields are `NULL`.

---

### 4. **FULL JOIN** (or **FULL OUTER JOIN**):
A `FULL JOIN` returns all records when there is a match in either the left or right table. It returns `NULL` for non-matching rows in both tables.

**SQL Query:**
```sql
SELECT Employees.EmployeeID, Employees.Name, Departments.DepartmentName
FROM Employees
FULL JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

**Result:**
| EmployeeID | Name    | DepartmentName |
|------------|---------|----------------|
| 1          | Alice   | HR             |
| 2          | Bob     | IT             |
| 3          | Charlie | NULL           |
| NULL       | NULL    | Marketing      |

**Explanation:**
The `FULL JOIN` ensures that all employees and all departments are included, regardless of whether a match exists. For Charlie, there is no department, so `DepartmentName` is `NULL`. For Marketing, there is no employee, so the employee fields are `NULL`.

---

### Summary of Differences:

| Join Type      | Includes rows from Left Table | Includes rows from Right Table | Rows without Match |
|----------------|-------------------------------|--------------------------------|---------------------|
| **INNER JOIN** | Yes                           | Yes                            | Excluded            |
| **LEFT JOIN**  | Yes                           | Yes (if match exists)          | NULL for right table|
| **RIGHT JOIN** | Yes (if match exists)         | Yes                            | NULL for left table |
| **FULL JOIN**  | Yes (if match exists)         | Yes (if match exists)          | NULL for both tables|

By choosing the right type of join based on the data relationship you're interested in, you can combine tables meaningfully.
