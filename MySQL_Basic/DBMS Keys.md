## DBMS Keys

0. **When to create the key?**

(1) CREATE TABLE
```SQL
create table 表名称(
字段名 数据类型,
字段名 数据类型 unique,
字段名 数据类型 unique key,
字段名 数据类型
);
create table 表名称(
字段名 数据类型,
字段名 数据类型,
字段名 数据类型,
[constraint 约束名] unique key(字段名)
);

```

(2) ALTER TABLE
```SQL
#字段列表中如果是一个字段，表示该列的值唯一。如果是两个或更多个字段，那么复合唯一，即多个字段的组合是唯
一的
#方式1：
alter table 表名称 add unique key(字段列表);
#方式2：
alter table 表名称 modify 字段名 字段类型 unique;

```


1. **Super Key** – The set of attributes that can uniquely identify a tuple is known as Super Key. For Example, STUD_NO, (STUD_NO, STUD_NAME), etc. 
Or  A super key is a group of single or multiple keys that identifies rows in a table. It supports NULL values. Example: SNO+PHONE is a super key. 
[唯一性]
- Adding zero or more attributes to the candidate key generates the super key.
- A candidate key is a super key but vice versa is not true.

---

2. **Primary Key** –  There can be more than one candidate key in relation out of which one can be chosen as the primary key. 
[從Candidate Key 挑選出來，因此符合 最小性, 唯一性,與 not null]
- It is a unique key.
- It can identify only one tuple (a record) at a time.
- It has no duplicate values, it has unique values.
- **It cannot be NULL.**
- Primary keys are not necessarily to be a single column; more than one the column can also be a primary key for a table.

---

3. **Candidate Key** – The minimal set of attributes that can uniquely identify a tuple is known as a candidate key. [最小性與唯一性]
- It is a minimal super key.
- It is a super key with no repeated data is called a candidate key.
- The minimal set of attributes that can uniquely identify a record.
- It must contain unique values.
- It can contain NULL values.
- Every table must have at least a single candidate key.
- A table can have multiple candidate keys but only one primary key (the primary key cannot have a NULL value, so the candidate key with NULL value can’t be the primary key).

---

4. **Alternate Key** – is a column or group of columns in a table that uniquely identify every row in that table.

---

5. **Foreign Key** – is a column that creates a relationship between two tables. The purpose of Foreign keys is to maintain data integrity and allow navigation between two different instances of an entity. **The referenced attribute of the referenced relation should be the primary key to it.**
It may be worth noting that unlike the Primary Key of any given relation, **Foreign Key can be NULL** as well as may contain duplicate tuples. 
Also, you CANNOT add the forign key's value which did not exist, and you CANNOT REMOVE the table which has foreign key (unless you delete the table which refered to this table first). [防止你從A table 串聯到 B table 後，出現資料消失或對不起來的問題]

---

6. **Compound Key** – has two or more attributes that allow you to uniquely recognize a specific record. It is possible that each column may not be unique by itself within the database.

---

7. **Composite Key** – is a combination of two or more columns that uniquely identify rows in a table. The combination of columns guarantees uniqueness, though individual uniqueness is not guaranteed.

---

8. **Surrogate Key** – An artificial key which aims to uniquely identify each record is called a surrogate key. These kind of key are unique because they are created when you don’t have any natural primary key.


#### 4. reference
https://www.geeksforgeeks.org/types-of-keys-in-relational-model-candidate-super-primary-alternate-and-foreign/
