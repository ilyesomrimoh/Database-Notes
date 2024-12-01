# Database
## Database Goal
The main goal of a database is not just to store data, but to organize the data we want to store in a way that allows it to be quickly retrieved upon user request.

## SQL (Structured Query Language)
Sql is a programming language designed for working with databases, particularly relational databases. 

1. SQL is a **Declarative** programming language which means it focuses on **what** you want to achieve rather than *how* to do it.  
2. You only need to specify the desired result, and the DBMS figures out how to execute it.


## Query
A query is a piece of SQL code executed to retrieve or manipulate data, commonly referred to as "querying the database.

## Database Management Systems (DBMS)  
To use databases and SQL, you need a **Database Management System (DBMS)**. A DBMS is a platform that allows you to create, manage, and interact with databases efficiently. It provides tools for data storage, retrieval, and management.

### **Popular DBMS Examples**:
1. **MySQL**:  
   - Open-source and free.  
   - Developed by the same company behind Oracle.  

2. **Oracle Database**:  
   - A commercial, paid DBMS.  
   - Offers advanced features for enterprise use.  

3. **PostgreSQL**:  
   - Open-source and highly versatile.  
   - Known for its performance and extensibility.  

4. **MariaDB**:  
   - A fork of MySQL.  
   - Free and open-source with a focus on performance.  

5. **Others**:  
   - SQL Server, SQLite, etc., each catering to different needs.

## SQL syntax 


SQL syntax grouped into the categories of DDL, DML, DCL, and TCL:

### **1. Data Definition Language (DDL)**  
Used to define or modify the structure of the database.  
**Commands**:  
- `CREATE` – Create new database objects (e.g., tables, views).  
  ```sql
  CREATE TABLE employees (id INT, name VARCHAR(50));
  ```  
- `ALTER` – Modify existing database objects.  
  ```sql
  ALTER TABLE employees ADD COLUMN department VARCHAR(50);
  ```  
- `DROP` – Delete database objects.  
  ```sql
  DROP TABLE employees;
  ```  
- `TRUNCATE` – Remove all records from a table without removing the table itself.  
  ```sql
  TRUNCATE TABLE employees;
  ```

---

### **2. Data Manipulation Language (DML)**  
Used to manipulate data stored in the database.  
**Commands**:  
- `SELECT` – Retrieve data from one or more tables.  
  ```sql
  SELECT * FROM employees;
  ```  
- `INSERT` – Add new records to a table.  
  ```sql
  INSERT INTO employees (id, name, department) VALUES (1, 'John', 'Sales');
  ```  
- `UPDATE` – Modify existing records.  
  ```sql
  UPDATE employees SET department = 'Marketing' WHERE id = 1;
  ```  
- `DELETE` – Remove specific records.  
  ```sql
  DELETE FROM employees WHERE id = 1;
  ```

---

### **3. Data Control Language (DCL)**  
Used to control access to the database.  
**Commands**:  
- `GRANT` – Provide permissions to users.  
  ```sql
  GRANT SELECT, INSERT ON employees TO user1;
  ```  
- `REVOKE` – Remove permissions from users.  
  ```sql
  REVOKE INSERT ON employees FROM user1;
  ```

---

### **4. Transaction Control Language (TCL)**  
Used to manage transactions within a database.  
**Commands**:  
- `COMMIT` – Save all changes made in a transaction.  
  ```sql
  COMMIT;
  ```  
- `ROLLBACK` – Undo changes made in a transaction.  
  ```sql
  ROLLBACK;
  ```  
- `SAVEPOINT` – Set a point within a transaction to roll back to later.  
  ```sql
  SAVEPOINT savepoint1;
  ROLLBACK TO savepoint1;
  ```
## SQL Constraints

1. **PRIMARY KEY**:  
   Ensures that each row in a table has a unique identifier. Combines the properties of **NOT NULL** and **UNIQUE**. A table can have only one primary key.
  ```sql
   CREATE TABLE Employees (
    id INT PRIMARY KEY,
);
 ```

3. **FOREIGN KEY**:  
   Ensures referential integrity by creating a link between two tables. A foreign key in one table points to the primary key in another table.
```sql
   CREATE TABLE Orders (
        FOREIGN KEY (customer_id) REFERENCES Customers(id)
);
 ```

5. **NOT NULL**:  
   Ensures that a column cannot have NULL values, meaning every row must have a value for this column.

```sql
CREATE TABLE Products (
    product_name VARCHAR(100) NOT NULL
);
 ```

7. **UNIQUE**:  
   Guarantees that all values in a column are distinct, preventing duplicate entries.

8. **CHECK**:  
   Ensures that all values in a column meet a specific condition.  
   Example:  
   ```sql
   CHECK (salary > 0)
   ```

9. **DEFAULT**:  
   Assigns a default value to a column if no value is provided.  
   Example:  
   ```sql
   DEFAULT CURRENT_TIMESTAMP
   ```

10. **INDEX**:  
   Enhances the speed of data retrieval operations on a table by creating an ordered data structure for a specific column or set of columns.
``` SQL
CREATE INDEX idx_author_id ON Books (author_id);
```

---

### Notes:

1. **ON DELETE CASCADE**:  
   When applied to a foreign key, it ensures that if a record in the parent table is deleted, all corresponding records in the child table are also automatically deleted.

2. **UNIQUE KEY and Index in MySQL**:  
   In MySQL, applying a UNIQUE constraint automatically creates an **index** for the column, allowing faster access and retrieval of data.





   
## GROUP BY
The GROUP BY clause is used to group rows that have the same values in specified columns into summary rows, such as finding the average, sum, count, or maximum/minimum values for each group. It’s often used with aggregate functions like COUNT(), SUM(), AVG(), MAX(), and MIN().

### How GROUP BY Works:
It combines rows with identical values in the specified column(s) into a single row for each unique value or combination of values.
You typically use GROUP BY when you want to aggregate data in some way, like getting a count or total for each group.

### Important Points:
- Columns in the SELECT statement that aren’t part of an aggregate function must be listed in the GROUP BY clause.
- GROUP BY can be used with multiple columns to form more complex groups.

## ORDER BY
The `ORDER BY` clause is used to sort the result of a query by one or more columns, either in ascending or descending order. It allows you to control the order in which records appear in your query results.

### Important Points:
- **ASC (Ascending Order)**: This is the default sorting order, which sorts from the lowest to the highest (e.g., A to Z, 0 to 9).
- **DESC (Descending Order)**: This sorts the data from the highest to the lowest (e.g., Z to A, 9 to 0).
- You can sort by multiple columns, and the sorting will be performed based on the order of columns specified.
- The sorting happens after the `WHERE` clause filters the data, so `ORDER BY` is applied last in the query execution process.
  
### Example:
```sql
SELECT * FROM employees
ORDER BY last_name ASC, first_name DESC;
```
In this example:
- The query first sorts by `last_name` in ascending order.
- If two records have the same `last_name`, it will sort those by `first_name` in descending order.

### When to Use ORDER BY:
- **To organize query results**: When you want to display data in a specific order, such as sorting by a date, name, or numerical value.
- **To improve readability**: Sorting results makes it easier to analyze or visualize the data, especially when dealing with large datasets.
- **When displaying reports**: Sorting is often necessary for creating meaningful reports, where data needs to be in a logical sequence (e.g., ranking, chronological order, etc.).

## JOINS
Joins allow you to combine data from multiple tables based on related columns, which is essential in relational databases.

### Types of Joins

#### **INNER JOIN**
- **Definition**: An `INNER JOIN` combines rows from two tables based on a matching condition (usually through the `ON` statement). It only returns rows where there is a match in both tables.
- **Example**: If you have two tables, `customers` and `orders`, the `INNER JOIN` will return only customers who have placed orders.

#### **LEFT JOIN (LEFT OUTER JOIN)**
- **Definition**: A `LEFT JOIN` returns all rows from the left table and the matching rows from the right table. If no match is found, the result will include `NULL` for columns from the right table.
- **Example**: If a customer has no orders, the result will still include that customer’s information, but the order details will be `NULL`.

#### **RIGHT JOIN (RIGHT OUTER JOIN)**
- **Definition**: A `RIGHT JOIN` is similar to a `LEFT JOIN`, but it returns all rows from the right table and the matching rows from the left table. If no match is found, the result will include `NULL` for columns from the left table.
- **Example**: If there are orders with no matching customer, the result will still include the order details, but the customer information will be `NULL`.

### Working with Dates in MySQL

- **Comparing Dates**: Use standard comparison operators (`=`, `<`, `>`, `<=`, `>=`, `<>`).
- **Getting Today's Date**: `CURDATE()` returns the current date.
- **Extracting Date Parts**: Use `YEAR()`, `MONTH()`, and `DAY()` to extract specific parts of a date:
  ```sql
  SELECT YEAR(orderDate), MONTH(orderDate), DAY(orderDate) FROM Orders;
  ```
- **Date Arithmetic**: 
  - To subtract one day from a date, use `DATE_SUB()`:
    ```sql
    DATE_SUB(w1.recordDate, INTERVAL 1 DAY)
    ```
  - Alternatively, you can subtract directly using:
    ```sql
    w1.recordDate - INTERVAL 1 DAY
    ```

## when to use NOT EXISTS and LEFT JOIN with NULL value checks:

   ### Use NOT EXISTS:
   
   **Sparse Matches:** When few matches are expected between the two tables.
   **Short-Circuit Evaluation:** If stopping at the first match improves performance (e.g., with well-indexed data).
   **Direct Logic:** When you only care about the presence or absence of rows, not additional data.
   **Cleaner Query Logic:** For simpler readability when checking for non-existence.
   **Index Optimization:** When the database engine optimizes correlated subqueries effectively (e.g., with indexed columns).
   
   ### Use LEFT JOIN with IS NULL:
   **Additional Data:** If you need to retrieve extra columns from the main table or the joined table.
   **Compatibility:** When working with older databases that might not optimize NOT EXISTS well.
   **Complex Joins:** If the query involves multiple joins and the data structure favors LEFT JOIN.
   **Non-Correlated Logic:** When avoiding correlated subqueries due to potential inefficiencies in your database engine.

### Modifying Tables While Querying Them

1. **General Rule**:  
   - MySQL does **not allow modifying a table** (e.g., `DELETE`, `UPDATE`) while querying the same table in a `FROM` clause.

2. **Reason for Restriction**:  
   - Prevents ambiguous behavior or inconsistencies during execution.

3. **Example in MySQL**:  
   ```sql
   -- Causes an error:
   DELETE FROM Person
   WHERE email = (
       SELECT email
       FROM Person p
       WHERE p.id < Person.id
   );
   ```
   **Error**: *"You can't specify target table 'Person' for update in FROM clause."*

4. **Workarounds**:
   - **Self-Join**:
     ```sql
     DELETE p1
     FROM Person p1
     JOIN Person p2
     ON p1.email = p2.email AND p1.id > p2.id;
     ```
   - **Temporary Table**:
     ```sql
     CREATE TEMPORARY TABLE TempPerson AS
     SELECT id FROM Person p1
     JOIN Person p2
     ON p1.email = p2.email AND p1.id > p2.id;

     DELETE FROM Person
     WHERE id IN (SELECT id FROM TempPerson);
     ```

5. **Other Databases**:  
   - PostgreSQL and SQL Server allow such queries.

6. **Best Practice**:  
   - Use **`JOIN`-based solutions** in MySQL for performance and compatibility.  
   - Test and optimize for large datasets using indexes or temporary tables.


### Summary of Window Functions in SQL

#### **What Are Window Functions?**
- **Window functions** perform calculations across a set of rows related to the current row without collapsing the rows into a single result. 
- Common use cases: Ranking, calculating running totals, computing moving averages, and accessing specific rows.

---

#### **Difference Between Window Functions and Aggregate Functions**
| **Window Functions**                             | **Aggregate Functions**                        |
|--------------------------------------------------|-----------------------------------------------|
| Operate on a "window" of rows but return a value for **each row**. | Operate on a group of rows and return **one value per group**. |
| Preserve all rows in the result.                 | Reduce the number of rows (collapse groups).  |
| Example: `SUM(salary) OVER (PARTITION BY dept)` returns the sum for each row in its department. | Example: `SUM(salary)` returns one total value for all rows. |

---

#### **Syntax of Window Functions**
```sql
<function_name> (arguments) 
OVER (
    [PARTITION BY column1, column2, ...]
    [ORDER BY column1 ASC|DESC, column2 ASC|DESC]
    [ROWS | RANGE BETWEEN <frame_specification>]
)
```

- **Function Name**: The window function to apply (e.g., `ROW_NUMBER`, `SUM`, `RANK`).
- **PARTITION BY**: Divides the data into partitions, and the function is applied within each partition.
- **ORDER BY**: Specifies the order of rows within the partition for function evaluation.
- **ROWS/RANGE**: Defines the window frame (optional).

---

#### **ORDER BY and PARTITION BY**
- **PARTITION BY**:
  - Groups rows into partitions for the window function.
  - Without `PARTITION BY`, the function operates on all rows.
  - Example: `SUM(salary) OVER (PARTITION BY department_id)`.

- **ORDER BY**:
  - Defines the order of rows within the partition.
  - Necessary for ranking and navigation functions like `ROW_NUMBER` or `LAG`.
  - Example: `RANK() OVER (PARTITION BY department_id ORDER BY salary DESC)`.
---

#### **List of Common Window Functions**

1. **Aggregate Functions**:
   - Perform cumulative calculations without collapsing rows.
   - Examples: 
     - `SUM()`: Total of the window.
     - `AVG()`: Average of the window.
     - `MIN()`, `MAX()`: Minimum/maximum value in the window.
     - `COUNT()`: Count of rows in the window.

2. **Ranking Functions**:
   - Assign ranks or sequence numbers to rows.
   - Examples:
     - `ROW_NUMBER()`: Assigns a unique sequential number to rows.
     - `RANK()`: Assigns rank with gaps for ties.
     - `DENSE_RANK()`: Assigns rank without gaps for ties.
     - `NTILE(n)`: Divides rows into `n` equal groups.

3. **Navigation Functions**:
   - Retrieve values from specific rows within the window.
   - Examples:
     - `LAG()`: Returns the value from the previous row.
     - `LEAD()`: Returns the value from the next row.
     - `FIRST_VALUE()`: Returns the first value in the window.
     - `LAST_VALUE()`: Returns the last value in the window.
     - `NTH_VALUE(n)`: Returns the nth value in the window.

4. **Statistical Functions**:
   - Perform percentile calculations or cumulative distribution.
   - Examples:
     - `PERCENT_RANK()`: Relative rank as a percentage (0 to 1).
     - `CUME_DIST()`: Cumulative distribution (percentage of rows ≤ current row).


  ```md
  ![Window Functions Example](images/window-functions-example.png "SQL Window Functions")
  ```







## TRANSACTION
A transaction in SQL is a group of operations treated as a single unit, ensuring that either all changes are applied, or none are, maintaining the consistency and reliability of the database. This process ensures the ACID properties (Atomicity, Consistency, Isolation, Durability).

### How to Make a Transaction:
A transaction differs from a simple SQL script by using the BEGIN TRANSACTION command to start and the COMMIT or ROLLBACK command to end it.

Example:
```sql
BEGIN TRANSACTION;
```
-- SQL operations (e.g., updates, inserts)
```sql
COMMIT;  -- Saves the changes
ROLLBACK;  -- Reverts the changes if something goes wrong
```
### When to Use a Transaction:
Grouping operations: When you need to perform multiple operations that must succeed or fail together, like transferring money between accounts or updating related data.
Error handling: To ensure changes are only applied if all operations succeed, maintaining data integrity.




## ACID Properties

ACID is a set of four key properties that ensure database transactions are processed reliably. ACID stands for **Atomicity, Consistency, Isolation,** and **Durability**, each of which is essential for maintaining data integrity, especially in multi-user and concurrent environments.

### 1. Atomicity
- **Definition**: Atomicity ensures that a transaction is "all-or-nothing." This means all operations within a transaction must succeed for any changes to be applied. If any operation fails, the entire transaction is rolled back, and no changes are saved.
- **Example**: When transferring money between bank accounts, if one part of the transaction (deducting from one account) fails, the whole transfer fails, and the money remains in the original account.

### 2. Consistency
- **Definition**: Consistency ensures that a transaction takes the database from one valid state to another, following all defined rules, constraints, and triggers. This prevents errors like duplicate entries or violations of data integrity constraints.
- **Example**: In a database with a rule that a user ID must be unique, a transaction that attempts to create a duplicate ID would violate consistency, and thus would fail.

### 3. Durability
- **Definition**: Durability guarantees that once a transaction is committed, its changes are permanent, even in the event of a power failure or system crash. This means that once changes are saved, they persist in the database.
- **Example**: If a transaction to add a new order to a database is committed, that order remains recorded even if the server crashes immediately afterward.

### 4. Isolation
- **Definition**: Isolation ensures that transactions do not interfere with each other, even if they are processed concurrently. Each transaction appears to execute independently, preventing conflicts or data corruption.
- **Example**: If two transactions try to update the same record simultaneously, isolation prevents them from seeing each other’s partial changes, avoiding inconsistent data.

### isolation levels
To manage how strictly transactions are isolated, databases offer different **isolation levels**. Each level strikes a balance between **concurrency** (more simultaneous transactions) and **data consistency** (fewer concurrency-related issues). The four main isolation levels are:

#### 1. Read Uncommitted (dirty reads issue)
- **Definition**: The lowest level of isolation, where transactions can read data that other transactions have modified but not yet committed (uncommitted data).
- **Issues**: At this level, transactions can encounter “dirty reads,” meaning they might read data from another transaction that could still be rolled back. If that happens, the read data may not reflect the final committed state.
- **Use Case**: Rarely used because it sacrifices data consistency for concurrency.

#### 2. Read Committed(non-repeatable reads issue)
- **Definition**: At this level, a transaction can only read data that has been committed by other transactions. This prevents dirty reads but allows for “non-repeatable reads,” where data that has already been read might change if another transaction updates it and commits.
- **Issues**: Non-repeatable reads can occur, meaning if a transaction reads a row, another transaction might update the same row, leading to different results if the first transaction reads the row again.
- **Use Case**: This is the default isolation level for many databases, providing a balance between consistency and performance.

#### 3. Repeatable Read(Phantom reads issue)
- **Definition**: At this level, if a transaction reads a row, no other transaction can update or delete that row until the first transaction is complete. This prevents both dirty reads and non-repeatable reads.
- **Issues**: Phantom reads can still occur, meaning new rows added by another transaction might appear in a range query if the transaction re-runs it.
- **Use Case**: Useful for applications that need a higher level of consistency, such as financial applications where intermediate changes must be avoided.

#### 4. Serializable
- **Definition**: The highest isolation level, where transactions are executed in such a way that the results are as if they were processed one after another, serially. This prevents all issues—dirty reads, non-repeatable reads, and phantom reads.
- **Issues**: Achieving this level of isolation often results in significant performance impacts, as it can lead to locking on rows, tables, or even the entire database, thereby reducing concurrency.
- **Use Case**: Used when absolute data consistency is essential, such as in highly critical systems where data integrity must be completely assured.

---

### Summary of Isolation Levels and Concurrency Issues

| Isolation Level       | Dirty Read | Non-Repeatable Read | Phantom Read |
|-----------------------|------------|----------------------|--------------|
| Read Uncommitted      | Yes        | Yes                 | Yes          |
| Read Committed        | No         | Yes                 | Yes          |
| Repeatable Read       | No         | No                  | Yes          |
| Serializable          | No         | No                  | No           |

---

#### Choosing the Right Isolation Level
Each isolation level comes with a trade-off between data consistency and system performance. The appropriate level depends on the application's needs:
- **For high concurrency with minimal locking**, use `Read Committed`.
- **For moderate concurrency with higher consistency**, use `Repeatable Read`.
- **For maximum consistency with low concurrency**, use `Serializable`.

Understanding and choosing the right isolation level is key for building robust applications where transactional integrity and performance are in balance. 


## Schema

A schema is the structure or blueprint of a database that defines tables, relationships (e.g., foreign keys), data types, and how data is organized.

### Schemas in Different Database Systems
- **MySQL:** A schema is essentially the same as a database.
- **Oracle:** A schema is a collection of objects (tables, views, sequences, stored procedures, etc.) owned by a single user. Each user in Oracle has their own schema, and only that user can create, modify, or delete objects within it (unless they give permission to others).
  In Oracle, schemas help separate and secure user-specific data while allowing shared access when permissions are granted.

## Some Notes
- The maximum size of **CHAR** is 255 characters, while **VARCHAR** can hold up to 65,535 characters.  
- **CHAR** is faster than **VARCHAR** due to its fixed-length structure, which enables the database to access and process data more quickly.
- integer types like INT are signed by default, meaning they can store both positive and negative values. If only positive values are needed, you must specify the UNSIGNED keyword in the query.
- **DECIMAL** and **NUMIRIC** are  Numbers with a fixed number of digits before and after the decimal point. ex: DECIMAL(5, 2)
- **FLOAT** or **REAL** and **DOUBLE**  or  **DOUBLE PRECISION** are  Numbers with a decimal point that can "float," meaning the number of digits before and after the decimal point can vary.
- **Fixed-Point** Data Types are slower and more storage intensive than the **Floating-Point** Data Types
-**BLOB** is a data type in SQL used to store large amounts of unstructured binary data, such as images, audio files, and video files (generally better to store file paths or URLs  and store the files themselves in a file system or object storage system for efficiency.)
-**TIMESTAMP** data type has a limited range, from January 1, 1970, to January 19, 2038, making it less suitable for storing birthdates. DATE or DATETIME would be more appropriate.
