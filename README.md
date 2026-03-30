Notes
MongoDB allowed flexible document insertion and easy filtering.
Cassandra required schema design in advance and only supports efficient queries based on the primary key structure.
Screenshots of MongoDB results can be added below if required by the instructor.
Screenshot section

Add your MongoDB Atlas screenshots here:

Cambodia query
amount > 500 query
projected fields query
updated Bob phone order

---

## `README.md`

```markdown
# 🐳 MongoDB vs Cassandra Lab
### A tale of two databases, one assignment, and zero emotional support from error messages.

---

## Overview

This lab compares two NoSQL databases: MongoDB and Cassandra.

- **MongoDB** stores flexible JSON-like documents.
- **Cassandra** uses a wide-column model and requires queries to follow the table design.

The goal of the lab was to:
1. Insert and query data in MongoDB
2. Create schema, insert, and query data in Cassandra
3. Reflect on the differences between the two systems

---

## Reflection Time™️

### 1. Which system is more suitable when the schema changes often?

MongoDB is more suitable when the schema changes often because it is schema-flexible. Documents in the same collection can have different fields, which makes MongoDB easier to use in applications where data structures evolve over time.

Cassandra is better when the schema is defined in advance and the query patterns are known. It is designed for scalability and high performance rather than flexibility.

**Conclusion:**  
- MongoDB = flexible  
- Cassandra = structured and scalable

---

### 2. What limitation did you notice in Cassandra queries?

A query such as:

```sql
SELECT * FROM orders WHERE customer = 'Alice';

produced an error because customer is not part of the primary key.

Cassandra requires queries to align with the partition key and clustering key. In this table, the primary key is:

PRIMARY KEY (country, order_id)
This means Cassandra can efficiently query by country, but not by customer unless the table is designed for that purpose.

Main limitation noticed:
Cassandra does not support arbitrary filtering like MongoDB unless ALLOW FILTERING is used, which is discouraged because of possible poor performance.
3. Which use case fits each database better?

MongoDB is better for:

e-commerce applications
content management systems
rapidly changing application data
flexible product catalogs

Cassandra is better for:

large-scale distributed systems
time-series data
logging systems
high-write workloads
applications that need high availability across many servers
Final Comment

This lab showed that MongoDB is easier for flexible querying, while Cassandra is more strict and optimized for scalability and performance when the data model matches the query requirements.