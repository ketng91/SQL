## Welcome to GitHub Pages

SELECT
     c.first_name,
     o.order_details,
     o.order_cost,
     ROUND(100*o.order_cost/SUM(o.order_cost) OVER
     (PARTITION BY (c.first_name))) AS percentage_total_spend 
FROM
    orders o
INNER JOIN
    customers c
ON
    o.cust_id = c.id
ORDER BY
    c.first_name
;
