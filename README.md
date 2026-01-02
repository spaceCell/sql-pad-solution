# Task from sqlpad.io

    Top store for movie sales
    
```sql
SELECT store, manager
FROM sales_by_store
WHERE total_sales = (
SELECT MAX( total_sales)
FROM sales_by_store
);
