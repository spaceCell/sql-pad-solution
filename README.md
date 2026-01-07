# Task from sqlpad.io

    Top store for movie sales

```sql
SELECT store, manager
FROM sales_by_store
WHERE total_sales = (
SELECT MAX(total_sales)
FROM sales_by_store
);
```

    Top 3 movie categories by sales

```sql
SELECT category
FROM (
    SELECT category,
           total_sales,
           DENSE_RANK() OVER (ORDER BY total_sales DESC) AS rnk
    FROM sales_by_film_category
) AS ranked_categories
WHERE rnk <= 3
ORDER BY total_sales DESC;
```

     Top 5 shortest movies

```sql
SELECT title
FROM film
ORDER BY length ASC
LIMIT 5;
```

    Monthly revenue

```sql
SELECT
  EXTRACT(YEAR FROM payment_ts) AS year,
  EXTRACT(MONTH FROM payment_ts) AS mon,
  SUM(amount) AS rev
FROM payment
GROUP BY year, mon
ORDER BY year, mon;
```

    Unique customers count by month

```sql
SELECT
  EXTRACT(YEAR from rental_ts) AS year,
  EXTRACT(MONTH from rental_ts) AS mon,
  COUNT(DISTINCT customer_id) AS uu_cnt
FROM rental
GROUP BY year, mon
ORDER BY year, mon;
```
