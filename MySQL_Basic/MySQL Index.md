## MySQL Index
索引可分為主索引鍵( primary key )、唯一索引( unique index )與非唯一索引( non-unique index )、 全文檢索( full-text search) 4種。

### 1. 簡介
- **主索引鍵( primary key )**
最為常見，而且一個表格通常會有一個，而且只能有一個。在一個表格中，設定為主索引鍵的欄位值不可以重複，而且不可以儲存「NULL」值。適合使用在類似編碼、代號或身份證字號這類欄位。

- **唯一索引( unique index )**
也稱為「不可重複索引」，在一個表格中，設定為唯一索引的欄位值不可以重複，但是可以儲存「NULL」值。

- **非唯一索引( non-unique index )**
就只是用來增加查詢與維護資料效率的索引。設定為非唯一索引的欄位值可以重複，也可以儲存「NULL」值。

- **全文檢索( full-text search)**
是只能用在「 CHAR 」、「 VARCHAR 」與「 TEXT 」型態的欄位字元型態且允許 「NULL」的欄位所組成。

### 2. 如何建立 Index
#### 在 create table 時便建立
```sql
CREATE TABLE t_index(  
   col1 INT PRIMARY KEY,  
   col2 INT NOT NULL,  
   col3 INT NOT NULL,  
   col4 VARCHAR(20),  
   INDEX (col2,col3)   
);  
```
#### create 完table 後才建立
```sql
CREATE INDEX [index_name] ON [table_name] (column names);
CREATE INDEX ind_1 ON t_index(col4);  
```

### 3. 原理
每一個 index 會建立一個 B+Tree
<img src="https://media.geeksforgeeks.org/wp-content/uploads/Btree.jpg">

