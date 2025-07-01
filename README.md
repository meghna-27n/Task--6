Task Overview

This task focuses on using subqueries in various SQL clauses to perform advanced data retrieval and filtering logic. You’ll explore scalar, correlated, and nested queries inside `SELECT`, `WHERE`, and `FROM`.

 Subquery in `WHERE`

SELECT name
FROM Customers
WHERE customer_id IN (
    SELECT customer_id
    FROM Orders
    WHERE order_date >= '2024-06-01'
);
 Scalar Subquery in `SELECT`

SELECT name,
    (SELECT COUNT(*) FROM Orders WHERE Orders.customer_id = Customers.customer_id) AS total_orders
FROM Customers;
Subquery in `FROM`


SELECT customer_id, order_count
FROM (
    SELECT customer_id, COUNT(*) AS order_count
    FROM Orders
    GROUP BY customer_id
) AS order_summary
WHERE order_count > 1;

SELECT name
FROM Customers
WHERE EXISTS (
    SELECT 1 FROM Orders
    WHERE Orders.customer_id = Customers.customer_id
);
