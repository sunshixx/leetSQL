MySQL 使用三值逻辑 —— TRUE, FALSE 和 UNKNOWN。任何与 NULL 值进行的比较都会与第三种值 UNKNOWN 做比较。这个“任何值”包括 NULL 本身。(**`NULL` 与 `NULL` 的比较结果既不是 `TRUE` 也不是 `FALSE`，而是 `UNKNOWN`**)，在 SQL 中，`UNKNOWN` 在查询过滤时会被视为 `FALSE`（即不匹配）。

```sql
-- 正确方式
SELECT NULL IS NULL;      -- 返回 1 (TRUE)
SELECT NULL IS NOT NULL;  -- 返回 0 (FALSE)
```

关于降序条件
```sql
select name, population, area from World 
where population >= 25000000 or area >= 3000000
order by population desc, area desc;
```
这个查询会：
1. 选择人口≥2500万或面积≥300万平方公里的国家
2. 先按人口降序排列（人口最多的排在最前面）
3. 如果人口相同，则按面积降序排列

去重直接查询
```sql
select distinct author_id as id
from Views 
where author_id = viewer_id
order by id asc
```

某个字段是Char类型，筛选其长度的查询
```sql
select tweet_id from Tweets 
where CHAR_LENGTH(content)>15
```
