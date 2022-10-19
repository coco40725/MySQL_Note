## 資料庫正規化
資料庫正規畫的好處:
1. 易維護
2. 減少資料異常
3. 提升操作資料庫的效率

注意: 正規化越多，表格會越細，有時會過碎，因此一般是用到 第三正規化。
(總共有 5 個正規化， 這裡介紹前三個)

### 1. First Normal Form
The value of an attribute should be an atomic value. It could not be multi-value, array, composite values, or any other relation.

> 1NF 需要完成的事:
> 1. 一個欄位只能有單一值
> 2. 消除意義上重複的欄位
> 3. 決定主鍵

The following table does not follw the 1NF.
|  id | 食物   |
|---  |---     |
| 1   | 水蜜桃, 香蕉 |
| 2   | 牛奶, 橘子 |


### 2. Second Normal Form
Remain the columns which are related to the primary key. Also, if the primary key is the combination key, such as ``SID`` and ``PID``, then you should remain the columns which are related to ``SID`` **AND** ``PID``. If the column is only related to ``SID``, then this column violates the 2NF.

> 2NF要完成的工作：
> 1. 消除部分相依

### 3. Third Normal Form 
The columns should be irrelative. Remove the columns which are relative to the other columns. For example:
|  id | 數量   | 價格 |  總計|
|---  |---     |---   |---  |
| 1   |  2 | 12 | 24 |
| 2   |  3 | 10 | 30 |

In this case, you should reomve column "總計"。

