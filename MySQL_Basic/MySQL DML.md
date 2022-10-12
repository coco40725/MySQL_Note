## MySQL DML
DML is short name of Data Manipulation Language which deals with data manipulation and includes most common SQL statements such SELECT, INSERT, UPDATE, DELETE, etc., and it is used to store, modify, retrieve, delete and update data in a database.

### 1. SELECT 
Retrieve data from a database.
```sql
SELECT COUNT(employee_id) 
FROM employees;
```
### 2. INSERT 
Insert data into a table.
```sql
INSERT INTO table_name (column, column1, column2, column3, ...)
VALUES (value, value1, value2, value3 ...) 
```

### 3. UPDATE 
Updates existing data within a table
```sql
UPDATE table_name
SET column = value, column1=value1,...
WHERE someColumn = someValue;

UPDATE table_name 
SET column = REPLACE(column, 'efg', 'zzz') 
WHERE column_name LIKE 'efg%';
```

### 4. DELETE
Delete all records from a database table
```sql
DELETE FROM tableName
WHERE someColumn = someValue
```
