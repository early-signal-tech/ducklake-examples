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
ATTACH 'quickstart.duckdb' AS mydb;
```

---

## 6. Create Table and Insert Data

Create a table:

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
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

## 7. Create Table from Source

Build a new table from a SELECT query:

```sql
CREATE TABLE users_over_30 AS
  SELECT * FROM users WHERE age > 30;
```

---

## 8. Query Tables

Query the original table:

```sql
SELECT * FROM users;
```

Query the derived table:

```sql
SELECT * FROM users_over_30;
```

---

Exit the shell when done:

```sql
.exit
```

---

For more details, see [DuckDB documentation](https://duckdb.org/docs/).
For more information and advanced usage, check out the [DuckLake documentation](https://ducklake.select/docs/).

