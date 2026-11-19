# Roadmap: Learn relational databases from first principles and build your own

The best way to understand how a relational database works internally is to build a small database engine from scratch, progressively adding the features found in PostgreSQL, SQLite, and MySQL.

As a data engineer, the objective should be to understand not just SQL, but what happens between submitting a query and getting results.

## 1. Understand the complete database architecture

Conceptual architecture of a disk-based relational database. Real engines have additional layers and interactions.

The goal is to implement these components and understand how they interact.

## 2. Learning roadmap — 6 phases

Phase 1 — Storage fundamentals

Weeks 1–3

Binary representation, disk pages, row serialization, heap files, slotted pages, record IDs, B+ trees, buffer pools.

Build: A persistent key-value store with insert, read, update and delete.

Phase 2 — SQL processing

Weeks 4–5

Lexing, parsing, abstract syntax trees, name resolution, type checking, relational algebra.

Build: A SQL parser supporting `CREATE TABLE`, `INSERT`, `SELECT`, `UPDATE`, `DELETE`.

Phase 3 — Query execution and optimization

Weeks 6–8

Sequential scans, index scans, filters, projections, joins, aggregations, sorting, query plans, cost estimation.

Build: A query executor supporting multi-table joins and `EXPLAIN`.

Phase 4 — Transactions and recovery

Weeks 9–11

ACID, write-ahead logging (WAL), checkpoints, crash recovery, locking, isolation levels, deadlocks.

Build: Transactions that survive process crashes and roll back safely.

Phase 5 — Concurrency and MVCC

Weeks 12–14

Multi-version concurrency control, snapshots, visibility rules, transaction IDs, vacuuming, contention.

Build: Multiple concurrent readers and writers with snapshot isolation.

Phase 6 — Production architecture

Weeks 15–20

Client-server protocol, replication, query statistics, partitioning, connection management, observability.

Build: A database server with a CLI, client connections, benchmarks and basic replication.

Timeline assumes roughly 8–12 hours per week. This is a learning prototype, not a production-grade database.

## 3. Best resources, in recommended order

[Free Video: Database Storage: Files and Pages - Lecture 3 from CMU Database Group | Class Central](https://images.openai.com/static-rsc-4/Bxm-V1MomuXrD2obfhvWXmBUSx4nhIoUMTwcz3mx61pMqoG-8sKBLKWkzTZ40kEtB4qEMh8Ksj28fzrAPpJyCP57JLQDaACFAiJSkh2VKpp90boNXTSHEiWrKzi4nNnLFXpHeuLSB0rr4S2y3aQogiMVeISBi9nLJgHkpmE6bSU?purpose=inline)

1\. Carnegie Mellon University — Database Systems (15-445)

Best overall course

Covers storage engines, indexing, query execution, optimization, concurrency and recovery, with substantial C++ programming assignments.

Free course materials · Intermediate to advanced

[Course and lectures](https://15445.courses.cs.cmu.edu/fall2025/?utm_source=chatgpt.com) · [Programming assignments](https://15445.courses.cs.cmu.edu/spring2026/assignments.html?utm_source=chatgpt.com)&#x20;

[image](https://www.google.com/s2/favicons?domain=https://15445.courses.cs.cmu.edu\&sz=32)

CMU 15-445/645+1



[Lets Build a Simple Database | Online Playground](https://images.openai.com/static-rsc-4/PLcPlUHQOQF4I7EQUCUqN4FHa1k23IbzUYpOkegEeefo2TwS3E4OHuxGJne7NL0nlHj5i8MNLBQltPeyK9adtkFywiw46ax5iGt7n-3hK2r8VtdGkv9zWbJHXpR9QnNrraPpTAjbzTFXtM_M5TgrDbVKihcFmAcublqoQLxS2Xc?purpose=inline)

2\. Let's Build a Simple Database — cstack

A practical walkthrough of implementing a SQLite-like database in C, covering persistence, B-trees and basic SQL execution.

Free · Beginner to intermediate · Project-based

[Start tutorial](https://cstack.github.io/db_tutorial/?utm_source=chatgpt.com) · [GitHub](https://github.com/cstack/db_tutorial?utm_source=chatgpt.com)&#x20;

[image](https://www.google.com/s2/favicons?domain=https://cstack.github.io\&sz=32)

Let’s Build a Simple Database+1



[Database Internals](https://images.openai.com/static-rsc-4/oPXKta6DzypYZt9lrg6VqWhVqingmcWH3_T77XAGxVyfsi2RxSUt-8wkyHAc_9hbQJ4t3BUqxLI73soL_w_ZPcYSrjq5W7fO3WqN1mAi000ayf_F1L4kAaLtywAQ5VYtR287l3eodh3UtFFn_euYYbq_7Lcsdzd0iaDDasDhNDE?purpose=inline)

3\. Database Internals — Alex Petrov

Excellent reference for B-trees, LSM trees, buffer pools, write-ahead logging and distributed storage.

Book · Advanced

[Book details](https://www.oreilly.com/library/view/database-internals/9781492040330/?utm_source=chatgpt.com)&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.oreilly.com\&sz=32)

O'Reilly Media



[Designing Data-Intensive Applications: The Big Ideas Behind Reliable, Scalable, and Maintainable Systems Second Hand Books - Snatch Books](https://images.openai.com/static-rsc-4/6T8CXy60nH90l13QA2zy8rG8-6yp1ZfwCEkWXFxIU1ndsp_nBJdqK8XWqnsfMcTY6IGcmbfRRXv0e-RJLjGu2ZT-EC9DNNcyYHOO1vZMOfgBbMTyf-dPUCKIp3wvhTkwGa-HdbtshAwIE0YKT3g53I9yA4ENJLTr5oNjiOtzUUo?purpose=inline)

4\. Designing Data-Intensive Applications — Martin Kleppmann

Explains storage trade-offs, replication, partitioning, consistency, transactions and distributed systems.

Book · Intermediate to advanced

[Official book website](https://dataintensive.net/?utm_source=chatgpt.com)

Additional references worth bookmarking: [SQLite architecture](https://www.sqlite.org/arch.html?utm_source=chatgpt.com), [PostgreSQL internals](https://www.postgresql.org/docs/current/internals.html?utm_source=chatgpt.com) and [CMU BusTub source code](https://github.com/cmu-db/bustub?utm_source=chatgpt.com).

## 4. What to build

Build a project called `mini-rdbms`, using this progression.

| Version | Features                  | Key learning            |
| ------- | ------------------------- | ----------------------- |
| v0.1    | In-memory tables and CRUD | Records and schemas     |
| v0.2    | Binary file persistence   | Pages and serialization |
| v0.3    | B+ tree primary index     | Indexing                |
| v0.4    | Buffer pool and eviction  | Memory management       |
| v0.5    | SQL parser                | Compilers               |
| v0.6    | Scans, filters, joins     | Query execution         |
| v0.7    | Cost-based planning       | Query optimization      |
| v0.8    | WAL and recovery          | Durability              |
| v0.9    | Transactions and MVCC     | Concurrency             |
| v1.0    | TCP server and client     | Database protocols      |

### Which programming language?

| Language | Recommendation                                                                                                                |
| -------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Python   | Good for prototyping parsers, query execution and relational algebra. Less suitable for learning low-level memory management. |
| C        | Excellent for understanding bytes, memory, pages and filesystem operations.                                                   |
| C++      | Strong choice for the full project, especially alongside CMU BusTub.                                                          |
| Rust     | Excellent for a systems-level database, with a steeper learning curve.                                                        |

Recommended: C++ for the main engine. Use Python separately to experiment with query optimizers and algorithms.

## 5. Questions you should eventually be able to answer

Use these as checkpoints to measure actual understanding.

Understanding checklist

0/8

How is a SQL row physically represented as bytes on disk?

What happens internally when INSERT executes?

How does a B+ tree index locate a row?

Why can an index scan be slower than a sequential scan?

How does a database choose between hash join and nested-loop join?

How does a database recover after crashing halfway through a transaction?

How can readers and writers operate concurrently using MVCC?

How does the optimizer estimate query cost and cardinality?

## 6. Suggested starting sequence

1. First 2 weeks: Complete the cstack SQLite clone sections on storage and B-trees.
2. Next 4 weeks: Follow CMU lectures on storage, buffer pools and indexes. Implement these independently.
3. Next 4 weeks: Build the SQL parser, executor and joins.
4. Next 4 weeks: Implement WAL, transactions and crash recovery.
5. Remaining weeks: Study MVCC, optimizer design and real PostgreSQL source code.

After completing the relational engine, extend your learning toward data engineering systems: columnar storage, vectorized execution, Parquet, DuckDB internals, distributed SQL and Spark's query execution model.

Best starting combination: CMU 15-445 for theory, cstack for your first implementation, and Database Internals for deeper architectural understanding.