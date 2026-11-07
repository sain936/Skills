# SQL and Database Engineering

Adapt examples to the learner's stated database dialect. If no dialect or
schema is known, state assumptions and use a small illustrative schema.

## Foundation

- Relational databases; tables, rows, columns, keys, and basic data types.
- `SELECT`, `WHERE`, `ORDER BY`, `DISTINCT`, and limiting results.
- Aggregates, `GROUP BY`, and `HAVING`.

## Intermediate

- `INNER`, `LEFT`, `RIGHT`, and `FULL` joins; join cardinality.
- Subqueries, common table expressions, `CASE`, and set operations.
- Date and string functions; `NULL` semantics and safe comparisons.
- Transactions and data modification basics.

## Advanced

- Window functions: partitioning, ordering, ranking, running totals, and moving
  averages.
- Recursive CTEs and hierarchical data.
- Indexes, query plans, statistics, and query optimization.
- Stored procedures, transactions, and isolation concepts.

## Expert applications

- Query tuning and performance measurement.
- Partitioning and distributed SQL.
- Warehouses, star and snowflake schemas, and slowly changing dimensions.
- Incremental processing and advanced analytical SQL.

## Practice checklist

- Define sample input tables and expected result rows.
- Explain logical query processing and how joins can multiply rows.
- Ask the learner to predict results before revealing them.
- Discuss correctness, `NULL`s, duplicates, and performance.
