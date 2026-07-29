# DataBase (DB)

- 關聯式資料庫（SQL）
    - 嚴格版的 Excel，適合結構化數據
    - 資料全部是由「行（row）」與「列（column）」組成，而且每張表之前可以建立「關聯」。
    - PostgreSQL、MySQL、SQLite

- 非關聯式資料庫（NoSQL）
    - 其實是為了解決 SQL 在面對海量、格式不固定資料時的瓶頸
    - 沒有欄位限制，一筆資料可能存在多個屬性。會用到 NoSQL 都是 資料關聯性不高、沒有結構描述、物件非常大
    - MongoDB
    
- 時間序列資料庫（Time-series Database/TSDB）
    - 專門處理每一筆都帶有精確時間戳記的連續性數據，寫入速度極快，也是擅長做時間區間的聚合計算
    - InfluxDB、TimescaleDB

- 鍵值資料庫（Key-Value Store/快取）
    - 放在記憶體裡面運作的極速資料庫，讀取寫入速度極快，但事一關機資料就會消失
    - Redis、Memcached

---

### 資料庫的層級

```text
Database（資料庫 / Schema）
 └─ Table（資料表）
     └─ Row（資料列，一筆資料）
         └─ Column（欄位）
```

### 資料庫四大分類

| 類型 | 名稱 | 用途 | 常見指令 |
| :--- | :--- | :--- | :--- |
| **DDL** | Data Definition Language | 定義結構 | `CREATE`, `ALTER`, `DROP` |
| **DML** | Data Manipulation Language | 操作資料 | `INSERT`, `UPDATE`, `DELETE` |
| **DQL** | Data Query Language | 查詢資料 | `SELECT` |
| **DCL** | Data Control Language | 權限控制 | `GRANT`, `REVOKE` |

---

### SQL 語法

#### 資料庫

- 查看現有的**資料庫**
```sql==
SHOW DATABASES;
```

- 建立新的**資料庫**
```sql==
CREATE DATABASE 資料庫名稱;
```


- 刪除現有的**資料庫**
```sql==
DROP DATABASE 資料庫名稱;
```

- 使用現有的**資料庫**
```sql==
USE 資料庫名稱;
```

#### 資料表

- 查看現有的**資料表**
```sql==
SHOW TABLES;
```

- 建立新的**資料表**
```sql==
CREATE TABLE 資料庫名稱(
    欄位名稱一 資料型態 欄位設定;
    欄位名稱二 資料型態 欄位設定;
    欄位名稱三 資料型態 欄位設定;
)
```

- 在資料表中新增資料
```sql==
INSERT INTO 資料表名稱(
    欄位名稱一,
    欄位名稱二,
    欄位名稱三,
    ...
) VALUES(
    欄位一資料,
    欄位二資料,
    欄位三資料,
    ...
);
```

- 取得資料表中的**所有資料**
```sql==
SELECT * FROM 資料表名稱;
```

- 刪除現有的資料表
```sql==
DROP TABLE 資料表名稱;
```

---

### 主鍵、欄位設定

- 主鍵（Primary Key）
    - 獨一無二、不可重複
    - 通常用來代表每一筆資料的編號

- 自動增加（Auto Increment）
    - 搭配主鍵使用，每次新增資料時會自動將編號+1

- NOT NULL
    - 欄位不接受空值

- DEFAULT
    - 欄位的預設值