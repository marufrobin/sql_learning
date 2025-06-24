# SQL Learning

`SELECT *`
means is select everything

`FROM`
means is from which table to select the data

`WHERE`
means is to filter the data based on a condition

`>` means greater than

`<` means less than

`=` means equal to

`!=` means not equal to

`>=` means greater than or equal to

`<=` means less than or equal to

`AND` means is to combine multiple conditions where all conditions must be true

`OR` means is to combine multiple conditions where at least one condition must be true

example of using `NOT` with `AND`

```sql
WHERE NOT (order_date >= '2013-01-01' AND status >= 2)
```

---

```sql
 WHERE state = "VA" or state = "GA" or state = "FL" 
 ```

instead of using `OR` you can use `IN`

```sql
WHERE state in ("VA", "GA", "FL")
```

if we want customer outside of this state
then we can use `NOT IN`

```sql
SELECT *
FROM sql_store.Customers
WHERE state NOT IN  ('VA', 'GA', 'FL');
```
