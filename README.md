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

`BETWEEN` is used to filter data within a range

```sql
SELECT *
FROM sql_store.customers

-- WHERE points >= 1000 AND points<= 3000
WHERE points BETWEEN 1000 AND 3000

```

```sql
SELECT *
FROM sql_store.customers
-- WHERE points >= 1000 AND points<= 3000
-- WHERE points BETWEEN 1000 AND 3000
WHERE birth_date BETWEEN '1990-01-01' AND '2000-01-01'
```
---
`LIKE` is used to filter data based on a pattern
`b%` means starts with `b`
`%` is a wildcard that matches any sequence of characters

```sql
SELECT *
FROM sql_store.customers
WHERE last_name LIKE 'b%'
```

'_' is a wildcard that matches any single character

```sql
SELECT *
FROM sql_store.customers
WHERE last_name LIKE '_a%'
```

``` sql
-- customer addresses contain TRAIL or AVENUE
-- customer phone thoese end with 9
WHERE address like '%TRAIL%' or 
	  address like '%AVENUE%'or
      phone like '%9'
```

The REGEXP function is used to filter data based on a regular expression pattern

- `^` means the beginning of a string
- `$` means the end of a string
- `.` means any character
- `*` means zero or more occurrences of the preceding character
- `+` means one or more occurrences of the preceding character
- `|` means logical OR
- `[]` means a character class, matching any single character within the brackets
- `[a-h]` means any single character from a to h

```sql
SELECT *
FROM sql_store.customers
-- WHERE last_name LIKE '%field%'
-- WHERE last_name REGEXP 'field'

-- '^' sign means the begining of a string
-- WHERE last_name REGEXP '^field'

-- '$' sign means the end of a string 
-- WHERE last_name REGEXP 'field$'

-- '|' means or in string 
WHERE last_name REGEXP 'field|mac|ros'

-- '.*' means any character zero or more times
WHERE last_name REGEXP '.*field.*'

-- '^[a-zA-Z0-9]+$' means only alphanumeric characters
WHERE last_name REGEXP '^[a-zA-Z0-9]+$'

WHERE last_name regexp '[a-h]e'



-- Get the customers whose
-- first names are 'ELKA' or 'AMBUR'
-- last names end with 'EY' or 'ON'
-- last names start with 'MY' or contains 'SE'
-- last names contain 'B' followed by 'R' or 'U'

SELECT *
FROM sql_store.customers
WHERE first_name REGEXP 'ELKA|AMBUR'
-- WHERE last_name REGEXP 'EY$|ON$'
-- WHERE last_name REGEXP '^MY|SE'
-- WHERE last_name REGEXP 'B[RU]'
```

----
The `IS NULL` operator is used to filter data where a column has no value (NULL).

```sql
-- This is NULL Operator
-- SELECT *
-- FROM sql_store.customers
-- WHERE phone IS NOT NULL
 
 
 -- Get the orders that are not shipped
 SELECT *
 FROM sql_store.orders
 WHERE shipped_date IS NULL
 
 ```
----
The `ORDER BY` clause is used to sort the result set by one or more columns.
```sql
SELECT *
FROM sql_store.order_items
-- ORDER BY state, first_name 
-- ORDER BY state DESC, first_name ASC

-- show order by total price

WHERE quantity * unit_price AND order_id =2
ORDER BY (quantity * unit_price) DESC 
```
----

```sql
SELECT * , quantity * unit_price AS total_price 
FROM sql_store.order_items
-- ORDER BY state, first_name 
-- ORDER BY state DESC, first_name ASC

-- show order by total price

WHERE  order_id =2
ORDER BY total_price DESC 

```