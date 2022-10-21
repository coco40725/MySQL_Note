## MySQL DDL 

DDL is short name of Data Definition Language, which deals with database schemas, its' object (such as table, view, etc...), and descriptions, of how the data should reside in the databas.

### 1. CREATE
To create a database and its objects like (table, index, views, store procedure, function, and triggers).

* **Database**
```sql
-- Create database
CREATE DATABASE MyDatabase;
use MyDatabase;

-- Alternative 
CREATE DATABASE IF NOT EXISTS MyDatabase;
use MyDatabase;

```

* **Table**
> Before  you create the table, make sure you 'use' the right database.

| 類型 | 類型舉例 | 
|---|---|
| 整數類型 | TINYINT、SMALLINT、MEDIUMINT、INT(或INTEGER)、BIGINT |
| 浮點類型 | FLOAT、DOUBLE |
| 定點數類型 | DECIMAL |
| 位類型 | BIT |
| 日期時間 | YEAR、TIME、DATE、DATETIME、TIMESTAMP |
| 文本字符串 | CHAR、VARCHAR、TINYTEXT、TEXT、MEDIUMTEXT、LONGTEXT |
| 枚舉類 | ENUM |
| 集合類型| SET |
| 二進位制類型| BINARY、VARBINARY、TINYBLOB、BLOB、MEDIUMBLOB、LONGBLOB |
|JSON |JSON對象、JSON數組 |
|空間數據類型: 單值類型 | GEOMETRY、POINT、LINESTRING、POLYGON|
|空間數據類型: 集合類型 | MULTIPOINT、MULTILINESTRING、MULTIPOLYGON、GEOMETRYCOLLECTION |

``` sql
CREATE TABLE [IF NOT EXISTS] 表名(
字段1, 數據類型 [約束條件] [默認值],
字段2, 數據類型 [約束條件] [默認值],
字段3, 數據類型 [約束條件] [默認值],
……
[表約束條件]
);

-- Create table
-- # 方式1:
CREATE TABLE IF NOT EXISTS MyTable(
    column1 int,
    column2 varchar(15)
)

-- # 方式2: 基於現有的表，可以結合 select 語句
CREATE TABLE myemp2
AS 
SELECT e.employee_id , e.last_name , e.salary 
FROM employees e ;
```

* **View** 
```sql
-- 完整版
CREATE [OR REPLACE]
[ALGORITHM = {UNDEFINED | MERGE | TEMPTABLE}]
VIEW 名稱 [(column)]
AS select語句
[WITH [CASCADED|LOCAL] CHECK OPTION]

--  精簡版
CREATE VIEW 名稱
AS select語句

-- 例子
CREATE VIEW empvu80
AS
SELECT employee_id, last_name, salary
FROM employees
WHERE department_id = 80;
```

### 2. ALTER
Alters the structure of the existing database. (Not Recommend)
```sql
-- 修改字符集
ALTER DATABASE mytest2 CHARACTER SET 'UTF8MB4'
```
注意! 不能修改數據庫的名字，而在一些視覺化工具中，"似乎有改名的功能"，其實不然， 它真正的操作是創建一個新的數據庫，然後把資料全部複製過去，最後刪掉舊的資料庫，可見成本非常高!

Alters the table.
```sql
-- 新增 constraints
ALTER TABLE mytable 
ADD CONSTRAINT myNew_pk PRIMARY KEY(mycolumn);

-- 刪除 constraints
ALTER TABLE mytable
DROP CONSTRAINT myNew_pk PRIMARY KEY(mycolumn);

-- 修改 column
ALTER TABLE mytable
MODIFY column_name column_definition
    [ FIRST | AFTER column1 ],
MODIFY column_name column_definition
    [ FIRST | AFTER column2 ];

-- 刪除 column
ALTER TABLE mytable
DROP COLUMN mycolumn;

-- 新增 column
ALTER TABLE table_name
ADD new_column_name column_definition
    [ FIRST | AFTER column_name ],
ADD new_column_name column_definition
    [ FIRST | AFTER column_name ];

-- 修改column 的名字
ALTER TABLE employees 
RENAME COLUMN id TO new_id;

-- 修改 column 預設值
ALTER TABLE book 
ALTER column languages SET DEFAULT 'chinese';

ALTER TABLE book
ALTER column languages DROP DEFAULT;
```

### 3. DROP
Delete objects from the database.
```sql
DROP DATABASE IF EXISTS 數據庫名稱;
```
### 4. TRUNCATE
Remove all records from a table, including all spaces allocated for the records are removed.

### 5. COMMENT 
Add comments to the data dictionary.

### 6. RENAME 
Rename an object.
