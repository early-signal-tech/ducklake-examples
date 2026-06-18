# DuckLake Quick Start Guide (CLI Only)

Pure CLI workflow for DuckLake. Copy and paste each command directly into your shell.

---

## 1. Download and Install DuckDB

**Download directly:**

```bash
curl curl https://install.duckdb.org | sh
```

For other platforms, visit [DuckDB releases](https://github.com/duckdb/duckdb/releases).

---

## 2. Launch DuckDB CLI

```bash
duckdb
```

You're now in the DuckDB interactive shell.

---

## 3. Install DuckLake

Inside the DuckDB shell:

```sql
INSTALL ducklake;
```

---

## 4. Load DuckLake

```sql
LOAD ducklake;
```

---

## 5. Attach Catalog

Attach a DuckDB database:

```sql
ATTACH 'ducklake:quickstart.duckdb' AS mydb;
USE mydb;
```

---

## 6. List Tables

View tables in your database:

```sql
.tables
```

Or use SQL:

```sql
SHOW TABLES;
```

---

## 7. Create Table and Insert Data

Create a table:

```sql
CREATE TABLE users (
  id INTEGER,
  name TEXT,
  age INTEGER
);
```

Insert data:

```sql
INSERT INTO users (id, name, age) VALUES
  (1, 'Alice', 28),
  (2, 'Bob', 33),
  (3, 'Charlie', 25);
```

---

## 8. Create Table from Source

Build a new table from a SELECT query:

```sql
CREATE TABLE users_over_30 AS
  SELECT * FROM users WHERE age > 30;
```

---

## 9. Query Tables

Query the original table:

```sql
SELECT * FROM users;
```

Query the derived table:

```sql
SELECT * FROM users_over_30;
```

---

## 10. Flush Inlined Data

Flush inlined data from a table using DuckLake:

```sql
CALL ducklake_flush_inlined_data('mydb;', table_name => 'users');
```

---

## 11. Insert Multiple Rows to Demonstrate Inlining Threshold

Insert 11 rows to show DuckLake's data inlining behavior:

```sql
INSERT INTO users (id, name, age) VALUES
  (4, 'Diana', 45),
  (5, 'Eve', 31),
  (6, 'Frank', 29),
  (7, 'Grace', 35),
  (8, 'Henry', 42),
  (9, 'Iris', 26),
  (10, 'Jack', 38),
  (11, 'Karen', 33),
  (12, 'Leo', 27),
  (13, 'Megan', 41),
  (14, 'Noah', 30);
```

---

Exit the shell when done:

```sql
.exit
```

---

For more details, see [DuckDB documentation](https://duckdb.org/docs/).
For more information and advanced usage, check out the [DuckLake documentation](https://ducklake.select/docs/).

