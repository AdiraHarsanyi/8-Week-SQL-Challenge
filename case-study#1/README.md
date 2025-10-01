## Problem Statement:
"Danny wants to use the data to answer a few simple questions about his customers, especially about their visiting patterns, how much money they’ve spent and also which menu items are their favourite. Having this deeper connection with his customers will help him deliver a better and more personalised experience for his loyal customers.
He plans on using these insights to help him decide whether he should expand the existing customer loyalty program - additionally he needs help to generate some basic datasets so his team can easily inspect the data without needing to use SQL.
Danny has provided you with a sample of his overall customer data due to privacy issues - but he hopes that these examples are enough for you to write fully functioning SQL queries to help him answer his questions!

Question 1: What is the total amount each customer spent at the restaurant?

```SQL
SELECT 
  sales.customer_id, 
  SUM(menu.price) AS sum_sales
FROM dannys_diner.sales

INNER JOIN dannys_diner.menu
  ON sales.product_id = menu.product_id
GROUP BY sales.customer_id
ORDER BY sum_sales DESC; 
```
Result:
| customer_id | sum_sales |
| ----------- | --------- |
| A           | 76        |
| B           | 74        |
| C           | 36        |

Question 2: How many days has each customer visited the restaurant?

```SQL
SELECT 
    COUNT(DISTINCT sales.order_date) AS num_days, sales.customer_id
FROM dannys_diner.sales

GROUP BY sales.customer_id
ORDER BY num_days DESC;
```


Result:
| num_days | customer_id |
| -------- | ----------- |
| 6        | B           |
| 4        | A           |
| 2        | C           |
