# 🧪 MongoDB and Cassandra Lab
### Because apparently databases also deserve homework.

---

# Part 1 — MongoDB

## 1. Insert Data

### Query
```javascript
db.orders.insertMany([
  { order_id: "001", customer: "Alice", country: "Cambodia", product: "Laptop", amount: 1200 },
  { order_id: "002", customer: "Bob", country: "Thailand", product: "Phone", amount: 800 },
  { order_id: "003", customer: "Alice", country: "Cambodia", product: "Mouse", amount: 25 },
  { order_id: "004", customer: "Carol", country: "Vietnam", product: "Laptop", amount: 1100 },
  { order_id: "005", customer: "Bob", country: "Thailand", product: "Tablet", amount: 600 }
])
db.orders.find({ country: "Cambodia" })
db.orders.find(
  { amount: { $gt: 500 } },
  { _id: 0, customer: 1, product: 1 }
)
db.orders.updateOne(
  { customer: "Bob", product: "Phone" },
  { $set: { amount: 850 } }
)
db.orders.find({ customer: "Bob", product: "Phone" })

# Part 2 — Cassandra
CREATE KEYSPACE shop
WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 1};
USE shop;
CREATE TABLE orders (
  country text,
  order_id text,
  customer text,
  product text,
  amount int,
  PRIMARY KEY (country, order_id)
);
INSERT INTO orders (country, order_id, customer, product, amount)
VALUES ('Cambodia', '001', 'Alice', 'Laptop', 1200);

INSERT INTO orders (country, order_id, customer, product, amount)
VALUES ('Thailand', '002', 'Bob', 'Phone', 800);

INSERT INTO orders (country, order_id, customer, product, amount)
VALUES ('Cambodia', '003', 'Alice', 'Mouse', 25);

INSERT INTO orders (country, order_id, customer, product, amount)
VALUES ('Vietnam', '004', 'Carol', 'Laptop', 1100);

INSERT INTO orders (country, order_id, customer, product, amount)
VALUES ('Thailand', '005', 'Bob', 'Tablet', 600);
SELECT * FROM orders WHERE country = 'Cambodia';
SELECT * FROM orders WHERE customer = 'Alice';
