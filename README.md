# Database

## Schema

A schema is the structure or blueprint of a database that defines tables, relationships (e.g., foreign keys), data types, and how data is organized.

### Schemas in Different Database Systems
- **MySQL:** A schema is essentially the same as a database.
- **Oracle:** A schema is a collection of objects (tables, views, sequences, stored procedures, etc.) owned by a single user. Each user in Oracle has their own schema, and only that user can create, modify, or delete objects within it (unless they give permission to others).
  In Oracle, schemas help separate and secure user-specific data while allowing shared access when permissions are granted


## GROUP BY
The GROUP BY clause is used to group rows that have the same values in specified columns into summary rows, such as finding the average, sum, count, or maximum/minimum values for each group. It’s often used with aggregate functions like COUNT(), SUM(), AVG(), MAX(), and MIN().

### How GROUP BY Works:
It combines rows with identical values in the specified column(s) into a single row for each unique value or combination of values.
You typically use GROUP BY when you want to aggregate data in some way, like getting a count or total for each group.

### Important Points:
- Columns in the SELECT statement that aren’t part of an aggregate function must be listed in the GROUP BY clause.
- GROUP BY can be used with multiple columns to form more complex groups.
