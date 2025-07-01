MySQL 使用三值逻辑 —— TRUE, FALSE 和 UNKNOWN。任何与 NULL 值进行的比较都会与第三种值 UNKNOWN 做比较。这个“任何值”包括 NULL 本身。(**`NULL` 与 `NULL` 的比较结果既不是 `TRUE` 也不是 `FALSE`，而是 `UNKNOWN`**)，在 SQL 中，`UNKNOWN` 在查询过滤时会被视为 `FALSE`（即不匹配）。

```sql
-- 正确方式
SELECT NULL IS NULL;      -- 返回 1 (TRUE)
SELECT NULL IS NOT NULL;  -- 返回 0 (FALSE)
```
