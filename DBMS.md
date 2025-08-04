# DBMS

### What is a DBMS? RDBMS?

  * **DBMS (Database Management System):**

      * **Definition:** A software system that allows users to define, create, maintain, and control access to a database. It's a general term for any system that manages data.
      * **Function:** A DBMS acts as an interface between the user/application and the database. It provides a structured way to store, retrieve, and manage data, ensuring data integrity and security.
      * **Examples:** MySQL, PostgreSQL, MongoDB, Microsoft Access.

  * **RDBMS (Relational Database Management System):**

      * **Definition:** A specific type of DBMS that is based on the relational model. Data is organized into tables (relations), which consist of rows and columns.
      * **Function:** RDBMS uses SQL (Structured Query Language) to manage and manipulate data. It enforces relationships between tables using keys.
      * **Examples:** MySQL, PostgreSQL, Oracle, SQL Server.
      * **Key Concept:** The relational model, based on mathematical set theory, provides a powerful and structured way to handle data.

-----

### Difference between SQL and NoSQL?

| Feature | SQL (Relational Databases) | NoSQL (Non-relational Databases) |
| :--- | :--- | :--- |
| **Structure** | Tabular, fixed schema. Data is organized into tables with rows and columns. | Dynamic schema, varied data models (e.g., key-value, document, graph). |
| **Schema** | Pre-defined and rigid schema. Changes require a database migration. | Dynamic schema. Can handle unstructured and semi-structured data. |
| **Language** | Uses SQL (Structured Query Language) for data definition and manipulation. | Varies by database, often uses different query languages (e.g., JSON-based queries). |
| **Scalability** | Vertically scalable (increase server power). Horizontally scalable with more effort. | Horizontally scalable (add more servers). Designed for large-scale, distributed systems. |
| **ACID** | Generally ACID-compliant (Atomicity, Consistency, Isolation, Durability). | Generally BASE-compliant (Basically Available, Soft state, Eventually consistent). |
| **Best for**| Structured data, complex queries, transactions, reporting. | Large, unstructured data, real-time analytics, big data applications. |
| **Examples**| MySQL, PostgreSQL, Oracle, SQL Server. | MongoDB, Cassandra, Redis, Neo4j. |

-----

### Explain Normalization. Why is it important?

**Normalization** is the process of organizing data in a relational database to reduce data redundancy and improve data integrity. It involves breaking down a large table into smaller, related tables and defining relationships between them.

**Why is it important?**

  * **Reduces Redundancy:** It minimizes duplicate data storage, which saves space and ensures that data is consistent.
  * **Improves Data Integrity:** By reducing redundancy, it prevents update anomalies. If data only exists in one place, you only need to update it once.
  * **Simplifies Queries:** A normalized database structure is often easier to understand and query.
  * **Enhances Scalability:** Makes the database easier to maintain and extend as the application grows.

-----

### 1NF, 2NF, 3NF, BCNF – give examples.

**1NF (First Normal Form):**

  * **Rule:** A table is in 1NF if it has no repeating groups or multi-valued attributes. Each column must contain a single, atomic value.
  * **Example:** A table with a column `PhoneNumbers` containing multiple numbers for one person is not in 1NF. To fix it, you would create separate rows for each phone number.

**2NF (Second Normal Form):**

  * **Rule:** A table is in 2NF if it is in 1NF and all non-key attributes are fully dependent on the **entire** primary key. This is relevant for tables with a composite primary key (a key made of multiple columns).
  * **Example:** In a `OrderDetails` table with a composite key of (`OrderID`, `ProductID`), if `ProductName` is dependent only on `ProductID`, it violates 2NF. To fix it, `ProductName` should be moved to a separate `Products` table.

**3NF (Third Normal Form):**

  * **Rule:** A table is in 3NF if it is in 2NF and has no transitive dependencies. A transitive dependency exists when a non-key attribute is dependent on another non-key attribute.
  * **Example:** In a `Employee` table with `EmployeeID` as the key, if `City` is dependent on `ZipCode`, and `ZipCode` is dependent on `EmployeeID`, then `City` is transitively dependent on `EmployeeID`. To fix it, `ZipCode` and `City` should be moved to a separate `ZipCodeDetails` table.

**BCNF (Boyce-Codd Normal Form):**

  * **Rule:** A table is in BCNF if every determinant (a column that determines another column) is a candidate key. It is a stricter version of 3NF.
  * **Example:** It is rare to have a table in 3NF that isn't in BCNF, but it can occur when there are multiple overlapping candidate keys.

-----

### What are ACID properties?

**ACID** is an acronym that stands for four properties guaranteed to be true for a reliable database transaction.

  * **Atomicity:** A transaction is treated as a single, indivisible unit of work. It either completes fully (commits) or it is completely undone (rolls back). There is no "halfway" state.
  * **Consistency:** A transaction brings the database from one valid state to another. It ensures that the transaction only ever changes the database in a way that preserves all its integrity constraints (e.g., foreign keys, unique constraints).
  * **Isolation:** Transactions are executed in a way that makes them appear as if they were running one after another, even if they are happening concurrently. The results of a transaction are not visible to other transactions until it is committed.
  * **Durability:** Once a transaction is committed, its changes are permanent and will survive a system crash, power failure, or other unexpected events.

-----

### What are Transactions in DBMS?

A **transaction** is a logical unit of work that contains one or more database operations. It represents a single, complete, and reliable change to the database. Transactions are the mechanism that guarantees the **ACID** properties.

**Example:** A bank transfer from one account to another. This involves two operations:

1.  Debit Account A.
2.  Credit Account B.

These two operations must be treated as a single transaction. If the debit succeeds but the credit fails, the entire transaction must be rolled back to prevent an inconsistent state.

**Key operations:**

  * **`COMMIT`:** Makes the changes permanent.
  * **`ROLLBACK`:** Undoes all the changes in the transaction.

-----

### What is Indexing? How does it improve performance?

**Indexing** is a data structure technique used to improve the speed of data retrieval operations on a database table. An index is a separate data structure that stores the values of a column (or columns) and a pointer to the location of the corresponding row in the main table.

**How it improves performance:**

  * **Faster Search:** An index works like an index in a book. Instead of scanning the entire table (a full table scan) to find a row, the database can use the index to quickly locate the data.
  * **Reduced I/O:** Since the index is typically smaller than the full table, less disk I/O is required to find the data.
  * **Sorted Data:** Indexes can be used to store data in a sorted order, which is very efficient for range queries (e.g., `WHERE salary > 50000`).
  * **Unique Constraints:** Indexes are used to enforce unique constraints on columns.

However, indexes also add overhead for data modification operations (INSERT, UPDATE, DELETE) because the index itself must be updated.

-----

### Primary Key vs. Foreign Key

| Feature | Primary Key | Foreign Key |
| :--- | :--- | :--- |
| **Purpose** | Uniquely identifies each record in a table. | Establishes a link or relationship between two tables. |
| **Null Values** | Cannot have `NULL` values. | Can have `NULL` values. |
| **Uniqueness** | Must be unique. | Can contain duplicate values. |
| **Number per Table**| A table can have only one primary key. | A table can have multiple foreign keys. |
| **Reference** | It is referenced by a foreign key in another table. | It references the primary key of another table. |

**Example:**

  * In an `Employees` table, `EmployeeID` would be the primary key.
  * In a `Departments` table, `DepartmentID` would be the primary key.
  * In the `Employees` table, `DepartmentID` would be a foreign key that references the `DepartmentID` of the `Departments` table, linking an employee to their department.

-----

### Clustered vs. Non-clustered Index

| Feature | Clustered Index | Non-clustered Index |
| :--- | :--- | :--- |
| **Structure** | The physical order of the data rows on the disk is the same as the sorted order of the index. | The physical order of the data rows is independent of the index's sorted order. The index contains pointers to the data rows. |
| **Number per Table**| A table can have only one clustered index. | A table can have many non-clustered indexes. |
| **Performance** | Faster for retrieval because the data is physically next to the index entry. | Slower than clustered because an extra lookup is needed to find the data row. |
| **Storage** | Does not require extra storage for the data, only for the index structure. | Requires additional storage for the index structure and pointers. |
| **Primary Key** | A primary key is often, but not always, implemented as a clustered index by default. | Can be created on any column (or set of columns). |

-----

### What is a Join? Types?

A **join** is a SQL clause used to combine rows from two or more tables based on a related column between them.

**Types of Joins:**

  * **`INNER JOIN`:** Returns only the rows where there is a match in both tables.
  * **`LEFT (OUTER) JOIN`:** Returns all rows from the left table and the matching rows from the right table. The unmatched rows from the right table will have `NULL` values.
  * **`RIGHT (OUTER) JOIN`:** Returns all rows from the right table and the matching rows from the left table. The unmatched rows from the left table will have `NULL` values.
  * **`FULL (OUTER) JOIN`:** Returns all rows from both tables, combining the matching rows and including `NULL` values for the unmatched rows.
  * **`CROSS JOIN`:** Returns the Cartesian product of the two tables, which means it combines every row from the first table with every row from the second table.

-----

### What is a Subquery?

A **subquery** (or inner query or nested query) is a query that is embedded inside another SQL query. It is a powerful tool for performing complex queries.

  * **Placement:** A subquery can appear in the `SELECT`, `FROM`, `WHERE`, or `HAVING` clause of a query.
  * **Execution:** The inner query executes first, and its result is used by the outer query.
  * **Example:**
    ```sql
    SELECT EmployeeName
    FROM Employees
    WHERE DepartmentID IN (SELECT DepartmentID FROM Departments WHERE DepartmentName = 'IT');
    ```
    In this example, the inner query finds the `DepartmentID` for the 'IT' department, and the outer query then finds all employees in that department.

-----

### What is a View?

A **view** is a virtual table based on the result set of an SQL query. It does not store data itself; it is a stored query that retrieves data from one or more tables.

  * **Function:** A view provides a simplified, customized, or restricted perspective of the data in the underlying tables.
  * **Advantages:**
      * **Simplicity:** It can hide complex joins and calculations, making it easier for users to query the data.
      * **Security:** It can be used to restrict user access to certain rows or columns of a table.
      * **Data Consistency:** It presents a consistent view of the data, even if the underlying schema changes.

-----

### What are Stored Procedures?

A **stored procedure** is a pre-compiled set of one or more SQL statements that are stored on the database server. It is a reusable block of code that can be executed on demand.

  * **Function:** Stored procedures can perform complex tasks, such as data validation, business logic, or data manipulation.
  * **Advantages:**
      * **Performance:** They are pre-compiled and optimized, leading to faster execution.
      * **Security:** They can be used to restrict direct access to tables. Users can be given permission to execute a stored procedure but not to modify the underlying data directly.
      * **Maintainability:** The logic is centralized, making it easier to maintain and update.
      * **Reduced Network Traffic:** Instead of sending multiple SQL statements, only a single command is sent to execute the stored procedure.

-----

### What is SQL Injection? How to prevent?

**SQL injection** is a code injection technique used to attack data-driven applications. An attacker inserts malicious SQL code into an input field (e.g., a login form) to trick the application into executing it. This can lead to unauthorized access, data theft, or data deletion.

**Example:**
A login form uses the following query:
`SELECT * FROM Users WHERE Username = '...user_input...' AND Password = '...password_input...'`
If an attacker enters `' OR '1'='1` as the password, the query becomes:
`SELECT * FROM Users WHERE Username = 'admin' AND Password = '' OR '1'='1';`
This query will always evaluate to true, allowing the attacker to bypass authentication.

**How to prevent it:**

  * **Prepared Statements with Parameterized Queries:** This is the most effective defense. The SQL code is sent to the database separately from the user data. The database then compiles the query and treats the user data as a literal value, not as executable code.
  * **Input Validation:** Sanitize and validate all user input to ensure it conforms to the expected format.
  * **Escaping Characters:** Escape special characters in user input to prevent them from being interpreted as SQL code.
  * **Least Privilege:** Give the database user account only the necessary permissions to perform its tasks.

-----

### Difference between DELETE, TRUNCATE, DROP

| Command | DELETE | TRUNCATE | DROP |
| :--- | :--- | :--- | :--- |
| **Purpose** | Deletes rows from a table. | Removes all rows from a table. | Deletes an entire table or database. |
| **Transaction**| DML (Data Manipulation Language). Can be rolled back. | DDL (Data Definition Language). Cannot be rolled back. | DDL. Cannot be rolled back. |
| **Speed** | Slower, as it logs each deleted row. | Faster, as it deallocates the data pages without logging each row. | Instantaneous. |
| **WHERE Clause** | Can use a `WHERE` clause to delete specific rows. | Cannot use a `WHERE` clause. | Cannot use a `WHERE` clause. |
| **Table Structure**| Keeps the table structure, indexes, and constraints. | Keeps the table structure and some constraints. Resets the identity column. | Removes the table structure, indexes, and all data. |

-----

### What is a Deadlock in DB?

A **deadlock** in a database is a situation where two or more transactions are waiting for a lock on a resource that is held by another transaction, and no transaction can proceed.

**Example:**

  * Transaction A acquires a lock on resource X.
  * Transaction B acquires a lock on resource Y.
  * Transaction A now tries to acquire a lock on resource Y. It must wait for B to release the lock.
  * Transaction B now tries to acquire a lock on resource X. It must wait for A to release the lock.
  * Both transactions are now in a deadlock, waiting for each other indefinitely.

**Prevention/Handling:**

  * **Detection:** The DBMS has a deadlock detection mechanism that periodically checks for cycles in the "wait-for graph."
  * **Resolution:** When a deadlock is detected, the DBMS terminates one of the transactions (the "victim") and rolls it back, allowing the other transactions to proceed. The terminated transaction can then be restarted.

-----

### What is a Trigger?

A **trigger** is a special type of stored procedure that is automatically executed in response to a specific event on a database table or view. The events are typically data modification statements like `INSERT`, `UPDATE`, or `DELETE`.

  * **Function:** A trigger is used to enforce business rules, audit data changes, or automate tasks.
  * **Example:**
      * An `AFTER INSERT` trigger on an `Orders` table could automatically update the `StockQuantity` in a `Products` table.
      * An `AFTER UPDATE` trigger on a `Salaries` table could log the old and new salary values for auditing purposes.

-----

### Difference between Inner and Outer Join

  * **Inner Join:**

      * **Result:** Returns a new table containing only the rows where the join condition is met in **both** tables.
      * **Logic:** It's an intersection of the two tables.
      * **Example:** Joining an `Employees` table and a `Departments` table on `DepartmentID` using an inner join will only return employees who are assigned to an existing department. Employees with no department will be excluded.

  * **Outer Join (Left, Right, Full):**

      * **Result:** Returns a new table containing all rows from one of the tables (the "outer" table) and the matching rows from the other.
      * **Logic:** It's a combination of the intersection and the unique rows from one of the tables.
      * **Example (Left Outer Join):** Joining an `Employees` table and a `Departments` table on `DepartmentID` using a left join will return all employees, including those without a department. The `DepartmentName` column for these employees will be `NULL`.

-----

### What is the difference between WHERE and HAVING?

| Feature | WHERE Clause | HAVING Clause |
| :--- | :--- | :--- |
| **Purpose** | Filters individual rows. | Filters groups of rows. |
| **Execution** | Processes before `GROUP BY`. | Processes after `GROUP BY`. |
| **Data Access** | Can be used with columns from the table being queried. | Can be used with aggregate functions (e.g., `SUM`, `COUNT`, `AVG`). |
| **Aggregate Functions**| Cannot be used with aggregate functions. | Can be used with aggregate functions. |

**Example:**

```sql
SELECT DepartmentID, AVG(Salary)
FROM Employees
WHERE HireDate > '2023-01-01'  -- WHERE filters individual rows before grouping
GROUP BY DepartmentID
HAVING AVG(Salary) > 60000;  -- HAVING filters the groups after aggregation
```

In this example, the `WHERE` clause first filters employees hired after '2023-01-01'. Then, the `GROUP BY` clause groups the remaining employees by department. Finally, the `HAVING` clause filters those groups to show only departments where the average salary is greater than $60,000.

### How is data consistency maintained in distributed DBs?

Maintaining data consistency in a distributed database is a complex challenge, as data is replicated and stored across multiple nodes. The goal is to ensure that all copies of the data are synchronized. This is often a trade-off between consistency, availability, and partition tolerance (as per the CAP theorem).

Key mechanisms for maintaining consistency include:
* **Two-Phase Commit (2PC):** A protocol that ensures all participating nodes in a distributed transaction either commit or abort the transaction. A coordinator node first sends a "prepare" message to all participants. If all nodes vote "yes," the coordinator sends a "commit" message. If any node votes "no," the coordinator sends an "abort" message.
* **Consensus Algorithms:** Algorithms like Paxos or Raft are used to ensure that all nodes in a cluster agree on the state of the data, even in the event of failures.
* **Eventual Consistency:** A consistency model where, if no new updates are made, all replicas of the data will eventually converge to the same value. This is a common model in NoSQL databases, where high availability is prioritized over strong consistency.
* **Strong Consistency:** A model that ensures all nodes have the most recent committed version of the data at any given time. This is often achieved using protocols like 2PC.

---

### What is CAP theorem?

The **CAP theorem** (also known as Brewer's theorem) is a fundamental principle in distributed systems. It states that it is impossible for a distributed system to simultaneously provide all three of the following guarantees:

* **Consistency:** All nodes see the same data at the same time.
* **Availability:** The system remains operational and responds to every request, even if some nodes fail.
* **Partition Tolerance:** The system continues to operate even if there is a communication failure (a "partition") between nodes.

In a distributed system, network partitions are inevitable. Therefore, a designer must choose between **Consistency** and **Availability**.
* **CP System:** Prioritizes consistency and partition tolerance. If a network partition occurs, the system will become unavailable on the side of the partition that cannot reach the primary copy of the data. (e.g., traditional RDBMS with 2PC).
* **AP System:** Prioritizes availability and partition tolerance. If a network partition occurs, the system will remain available on both sides, but it may result in data inconsistencies until the partition is resolved. (e.g., many NoSQL databases like Cassandra).

---

### What is Sharding and Partitioning?

* **Partitioning:**
    * **Definition:** A horizontal division of a logical database into multiple independent, physical partitions. All partitions remain within a single database server.
    * **Purpose:** To improve performance by distributing the workload and making a single table easier to manage. A common method is to partition a table by range (e.g., by date) or by a list of values.
* **Sharding:**
    * **Definition:** A type of partitioning where a single logical database is partitioned into multiple smaller, independent databases (shards) that are each hosted on a different database server.
    * **Purpose:** To scale a database horizontally. Each shard is a separate database instance, which allows the system to handle a larger volume of data and traffic.
    * **Key Difference:** Sharding involves splitting a database across multiple physical servers, while partitioning involves splitting a table within a single database server.

---

### Explain 2PL (Two-Phase Locking)

**Two-Phase Locking (2PL)** is a concurrency control protocol that guarantees transaction isolation and prevents conflicts. It ensures that a transaction acquires all the locks it needs before releasing any of them. The protocol has two phases:

1.  **Growing Phase:**
    * The transaction can only acquire locks; it cannot release any.
    * It acquires a shared lock for reading and an exclusive lock for writing.
2.  **Shrinking Phase:**
    * The transaction can only release locks; it cannot acquire any new ones.
    * Once a transaction releases its first lock, it enters this phase and cannot acquire any new locks.

This protocol ensures that once a transaction has modified a piece of data, it holds the lock until it's ready to commit, preventing other transactions from seeing inconsistent data.

---

### What are Locks? Shared vs. Exclusive?

**Locks** are a concurrency control mechanism used in databases to protect transactions from interfering with each other. A lock is a temporary restriction on an object (e.g., a row, a table) to prevent others from accessing or modifying it.

* **Shared Lock (Read Lock):**
    * **Purpose:** A transaction acquires a shared lock when it wants to read data.
    * **Compatibility:** Multiple transactions can hold a shared lock on the same resource at the same time. This is because multiple readers do not interfere with each other.
    * **Conflict:** A shared lock conflicts with an exclusive lock. A transaction with a shared lock cannot read a resource that has an exclusive lock.

* **Exclusive Lock (Write Lock):**
    * **Purpose:** A transaction acquires an exclusive lock when it wants to write (insert, update, delete) to a resource.
    * **Compatibility:** Only one transaction can hold an exclusive lock on a resource at a time.
    * **Conflict:** An exclusive lock conflicts with both a shared lock and another exclusive lock. A transaction cannot write to a resource that has any kind of lock.

---

### What is Optimistic vs. Pessimistic Locking?

These are two different strategies for managing concurrency and avoiding conflicts between transactions.

* **Pessimistic Locking:**
    * **Principle:** Assumes that conflicts are likely to occur. It acquires an exclusive lock on a resource as soon as a transaction needs to modify it, preventing other transactions from accessing it.
    * **Mechanism:** A transaction locks the resource, performs its work, and then commits and releases the lock.
    * **Advantages:** Prevents all data conflicts.
    * **Disadvantages:** Can lead to deadlocks and reduced concurrency, as other transactions may have to wait.
    * **Use Case:** High-contention environments where the cost of a rollback is high.

* **Optimistic Locking:**
    * **Principle:** Assumes that conflicts are rare. It allows multiple transactions to access and modify a resource without a lock.
    * **Mechanism:** When a transaction tries to commit its changes, it checks if the data has been modified by another transaction since it was first read. If there's a conflict, the transaction is rolled back and must be restarted. This is often done using a version number or a timestamp.
    * **Advantages:** High concurrency; no deadlocks.
    * **Disadvantages:** A transaction might have to be rolled back and retried, which can be inefficient if conflicts are common.
    * **Use Case:** Low-contention environments.

---

### What is a Materialized View?

A **materialized view** is a database object that stores the result of a query, similar to a regular view. However, unlike a regular view, a materialized view's result set is physically stored on disk.

* **Function:** It acts as a pre-computed cache of a query result.
* **Advantages:**
    * **Performance:** Queries against a materialized view are much faster because the data is already computed and doesn't need to be re-run every time. This is especially useful for complex queries involving joins, aggregations, and subqueries.
* **Disadvantages:**
    * **Staleness:** The data in a materialized view can become stale if the data in the underlying tables changes. The view must be "refreshed" periodically (either manually or automatically) to stay up-to-date.
    * **Storage:** It requires additional storage space.
* **Use Cases:** Data warehousing, reporting, and business intelligence applications where data is read frequently but updated infrequently.

---

### Explain ER Diagrams

An **ER (Entity-Relationship) diagram** is a visual tool used to model the structure of a database. It shows the logical relationship between entities and their attributes.

* **Components:**
    * **Entities:** A real-world object or concept (e.g., `Employee`, `Department`). Represented by a rectangle.
    * **Attributes:** A property of an entity (e.g., `EmployeeID`, `Name`, `Salary`). Represented by ovals. The primary key is often underlined.
    * **Relationships:** The association between entities (e.g., `works in`). Represented by a diamond.
    * **Cardinality:** The number of instances of one entity that can be associated with an instance of another entity. It's represented by numbers or symbols on the relationship lines (e.g., `1:1`, `1:N`, `N:M`).

* **Purpose:** ER diagrams are essential for database design, helping designers to logically structure the data before moving to a physical implementation.

---

### What are Functional Dependencies?

A **functional dependency** is a relationship between two attributes in a relational database. It states that the value of one attribute (or a set of attributes) uniquely determines the value of another attribute.

* **Notation:** `A -> B` means that attribute A functionally determines attribute B.
* **Example:** In a table with attributes (`StudentID`, `StudentName`), `StudentID -> StudentName`. This means that if you know a student's ID, you can uniquely determine their name.
* **Importance:** Functional dependencies are a key concept in database **normalization**. Normalization rules (like 2NF and 3NF) are based on the concept of eliminating unwanted functional dependencies to reduce data redundancy and improve data integrity.

---

### What is a Surrogate Key?

A **surrogate key** is a unique identifier assigned to each record in a database table. It has no intrinsic meaning or business value to the data it represents.

* **Characteristics:**
    * It is typically an integer, and its value is automatically generated by the database (e.g., an auto-incrementing ID).
    * It is used as the primary key for the table.
    * It is not derived from any other data in the table.
* **Advantages:**
    * **Simplicity:** It is simple, short, and easy to use as a primary key.
    * **Stability:** It never changes, even if the data in the record changes. This is in contrast to a **natural key**, which is derived from business data (e.g., a Social Security Number) and can sometimes change.
    * **Performance:** Integer keys are often more efficient for indexing and joins than a composite key or a long string.
* **Use Cases:** Surrogate keys are widely used in modern database design.

---

### What is Schema vs. Instance?

* **Database Schema:**
    * **Definition:** The logical design and structure of a database. It defines what data is stored and how it is related.
    * **Static:** The schema is relatively static and is defined during the database design phase.
    * **Components:** It includes the names of tables, columns, data types, constraints (e.g., primary keys, foreign keys), and the relationships between them.
    * **Analogy:** The schema is like a blueprint of a house.

* **Database Instance:**
    * **Definition:** The actual data stored in the database at a particular point in time.
    * **Dynamic:** The instance is dynamic and changes constantly as data is inserted, updated, and deleted.
    * **Analogy:** The instance is like the actual house built from the blueprint, with all the furniture and people inside.

---

### What is a Cursor?

A **cursor** is a database object that enables a user to traverse and manipulate the rows of a result set one at a time. It's a way to process a result set as if it were a sequential data stream, rather than a single, set-based operation.

* **Function:** A cursor is typically used within a stored procedure or a function to perform row-by-row processing, which is useful when the logic is too complex for a single SQL query.
* **Steps:**
    1.  **Declare:** A cursor is declared for a specific query.
    2.  **Open:** The cursor is opened, and the query is executed. The result set is now available.
    3.  **Fetch:** Rows are fetched one by one into local variables.
    4.  **Process:** Each fetched row is processed.
    5.  **Close:** The cursor is closed.
    6.  **Deallocate:** The memory used by the cursor is deallocated.
* **Disadvantage:** Row-by-row processing with cursors is generally much slower and less efficient than set-based operations. It should be used only when necessary.

---

### What is the difference between OLTP and OLAP?

| Feature | OLTP (Online Transaction Processing) | OLAP (Online Analytical Processing) |
| :--- | :--- | :--- |
| **Purpose** | To process day-to-day transactions (e.g., e-commerce, banking). | To perform complex data analysis and business intelligence. |
| **Data Model**| Highly normalized (e.g., 3NF) to reduce redundancy. | De-normalized (e.g., star schema) to optimize for reading. |
| **Operations** | Short, fast, simple transactions (e.g., `INSERT`, `UPDATE`). | Complex queries, aggregations, and joins on large datasets. |
| **Volume** | Many small transactions. | Few large, read-intensive queries. |
| **Latency** | Low latency is critical. | High latency is acceptable. |
| **Data** | Current, real-time data. | Historical, aggregated data. |
| **Users** | A large number of users. | A small number of power users (e.g., analysts). |
| **Examples**| Online banking, airline reservation systems, point-of-sale systems. | Data warehouses, business intelligence dashboards. |

---

### Explain B+ Tree Indexing

A **B+ Tree** is a tree-like data structure that is widely used for database indexing. It's an extension of the B-tree that is optimized for disk-based storage.

* **Structure:**
    * **Root Node:** The top-most node of the tree.
    * **Internal Nodes:** Contain keys and pointers to child nodes. They do not contain data.
    * **Leaf Nodes:** Contain the actual data pointers or the data itself, and are linked together in a sequential manner (a doubly-linked list). This allows for efficient range queries.
* **How it works:**
    * When a record is inserted, the B+ Tree is updated to maintain its sorted and balanced structure.
    * When a record is searched for, the database traverses the tree from the root node down to a leaf node. At each internal node, it compares the search key to the keys in the node to determine which child node to follow.
    * The sequential linking of the leaf nodes is what gives the B+ Tree its power for range queries. It only needs to find the first record and then can traverse the leaf nodes linearly.

---

### What is Consistency in DB?

**Consistency** is one of the four ACID properties. It means that a transaction brings the database from one valid state to another valid state.

* **Rules:** Consistency is defined by the integrity constraints of the database, such as:
    * **Foreign key constraints:** A foreign key must reference a valid primary key.
    * **Unique constraints:** A column marked as unique cannot contain duplicate values.
    * **Check constraints:** A value must meet a certain condition (e.g., a salary must be greater than zero).
    * **Business rules:** Any other rules defined by the application.
* **Function:** The database management system enforces these rules. If a transaction attempts to perform an operation that violates a consistency rule, the transaction is aborted.

---

### Explain the role of a Query Planner

A **query planner** (or query optimizer) is a component of a database management system that is responsible for determining the most efficient way to execute a given SQL query.

* **Function:** A query can often be executed in many different ways. The query planner analyzes the query, the database schema, and the statistics of the data (e.g., number of rows, distribution of values) to generate an **execution plan**.
* **Key Tasks:**
    * **Parsing:** It first parses the SQL query to understand its structure.
    * **Rewriting:** It may rewrite the query to a more efficient form.
    * **Cost Estimation:** It estimates the cost (e.g., CPU time, I/O operations) of different possible execution plans.
    * **Plan Selection:** It chooses the plan with the lowest estimated cost. This plan dictates the order of operations, the join methods to use, and whether to use indexes.
* **Importance:** The query planner is a critical component that ensures the database performs well, especially for complex queries.

---

### How is Concurrency handled in DBs?

Concurrency control is a set of techniques used to ensure that multiple transactions running at the same time do not interfere with each other and that data integrity is maintained.

Key mechanisms include:
* **Locking:** The most common method. Transactions acquire locks on data to prevent other transactions from accessing or modifying it (e.g., 2PL).
* **Timestamp Ordering:** Each transaction is assigned a unique timestamp. The database ensures that conflicting operations (e.g., a write operation) are executed in timestamp order. If an operation violates this order, the transaction is rolled back.
* **Optimistic Concurrency Control:** Assumes conflicts are rare and only checks for them at commit time.
* **Multiversion Concurrency Control (MVCC):** A widely used technique in modern databases (e.g., PostgreSQL). It allows a transaction to access a snapshot of the data from when it started, without blocking other writers. This eliminates read-write conflicts and is highly efficient.

---

### What is Isolation Level?

The **isolation level** is a setting that defines how a transaction is isolated from other concurrent transactions. It determines the degree to which a transaction is protected from the effects of other transactions. A higher isolation level means more protection but can also lead to lower concurrency.

The SQL standard defines four isolation levels:
1.  **`READ UNCOMMITTED`:** The lowest level. A transaction can read uncommitted data from other transactions.
2.  **`READ COMMITTED`:** A transaction can only read data that has been committed. It prevents dirty reads but can still suffer from non-repeatable reads and phantom reads.
3.  **`REPEATABLE READ`:** A transaction can reread data and be guaranteed that the data has not been changed by another committed transaction. It prevents dirty reads and non-repeatable reads but can still suffer from phantom reads.
4.  **`SERIALIZABLE`:** The highest level. It guarantees that transactions are executed in a way that is equivalent to a serial execution (one after another). It prevents all read phenomena but can lead to a significant drop in concurrency.

---

### Read Phenomena: Dirty Read, Non-repeatable Read, Phantom Read

These are common concurrency problems that can occur if the isolation level is not high enough.

* **Dirty Read (Uncommitted Read):**
    * **What it is:** A transaction reads data that has been modified by another transaction that has not yet committed.
    * **Problem:** If the first transaction is rolled back, the data that the second transaction read becomes invalid.
    * **Prevention:** The `READ COMMITTED` isolation level prevents dirty reads.

* **Non-repeatable Read:**
    * **What it is:** A transaction reads the same data twice, and the second read returns a different value because another committed transaction has modified the data between the two reads.
    * **Problem:** The transaction sees an inconsistent view of the data.
    * **Prevention:** The `REPEATABLE READ` isolation level prevents non-repeatable reads.

* **Phantom Read:**
    * **What it is:** A transaction performs a query that returns a set of rows. When it runs the same query later, it finds a new row has been added by another committed transaction.
    * **Problem:** The transaction sees "phantom" rows that didn't exist before.
    * **Prevention:** The `SERIALIZABLE` isolation level prevents phantom reads.

### What is Serializability?

**Serializability** is the strongest and most desirable isolation level for concurrent transactions in a database. A schedule of concurrent transactions is considered serializable if its result is equivalent to the result of some serial schedule of those same transactions.

  * **Serial Schedule:** A schedule where transactions are executed one after the other, with no interleaving of operations.
  * **Serializable Schedule:** A schedule where multiple transactions run concurrently, but the end result is exactly the same as if they had run in some sequential order.
  * **Guarantee:** Serializability guarantees that concurrent transactions do not interfere with each other, preventing all read phenomena (dirty reads, non-repeatable reads, and phantom reads).
  * **Cost:** The `SERIALIZABLE` isolation level provides the highest level of data integrity but often comes with a performance penalty. This is because the database has to do more work to enforce the strict isolation, which can reduce concurrency.
  * **Use Case:** It's used in applications where data integrity is absolutely critical, such as financial systems or systems with complex, interdependent transactions.

-----

### Difference between NoSQL types: document, key-value, columnar, graph?

NoSQL databases are a diverse group of non-relational databases, each with its own data model and use case.

1.  **Document Databases:**

      * **Data Model:** Stores data in flexible, semi-structured documents, typically in JSON, BSON, or XML format.
      * **Structure:** Documents can contain nested documents, arrays, and other complex structures. The schema is dynamic.
      * **Use Case:** Ideal for applications with a flexible schema, such as content management systems, e-commerce, and catalogs.
      * **Example:** MongoDB, CouchDB.

2.  **Key-Value Stores:**

      * **Data Model:** The simplest NoSQL model. Data is stored as a collection of key-value pairs. The key is a unique identifier, and the value can be anything (a string, an image, a complex object).
      * **Structure:** The database doesn't care about the content or structure of the value.
      * **Use Case:** Highly efficient for simple read/write operations. Used for caching, session management, and real-time data.
      * **Example:** Redis, Amazon DynamoDB.

3.  **Columnar Databases (Wide-Column Stores):**

      * **Data Model:** Stores data in columns rather than rows. Related data is stored contiguously, which makes it very efficient for queries that need to read a large number of rows but only a few columns.
      * **Structure:** Rows can have different columns.
      * **Use Case:** Best for data analytics, data warehousing, and big data applications where you need to perform aggregations on massive datasets.
      * **Example:** Cassandra, HBase.

4.  **Graph Databases:**

      * **Data Model:** Stores data as nodes (entities), edges (relationships), and properties (attributes of nodes and edges).
      * **Structure:** Optimized for traversing and querying complex relationships between data points.
      * **Use Case:** Ideal for social networks, recommendation engines, fraud detection, and network management.
      * **Example:** Neo4j.

-----

### Difference between MongoDB and SQL?

**MongoDB (a NoSQL document database):**

  * **Data Model:** Stores data in JSON-like documents, which are grouped into collections.
  * **Schema:** Dynamic and schema-less. Documents in the same collection can have different fields and structures.
  * **Query Language:** Uses a JSON-based query language (MQL) and has a rich set of operators for querying documents.
  * **Joins:** No traditional `JOIN` operations. Relationships are handled by embedding documents or using manual references.
  * **Scalability:** Designed for horizontal scalability (sharding).
  * **ACID:** Supports transactions but is generally more BASE-compliant, prioritizing availability and partition tolerance.

**SQL (a relational database):**

  * **Data Model:** Stores data in structured tables with a fixed number of columns and rows.
  * **Schema:** A rigid, pre-defined schema. All rows in a table must have the same columns.
  * **Query Language:** Uses SQL (Structured Query Language) for all data manipulation and definition.
  * **Joins:** Supports powerful `JOIN` operations to combine data from multiple tables.
  * **Scalability:** Traditionally scales vertically, but horizontal scaling (sharding) is possible with more effort.
  * **ACID:** Strictly ACID-compliant, prioritizing consistency.

-----

### Use case: When would you pick SQL vs. NoSQL?

**Choose SQL (Relational Database) when:**

  * **Data is highly structured:** Your data fits neatly into a tabular format with a fixed schema.
  * **Data integrity is critical:** You need strong data consistency and ACID guarantees (e.g., financial transactions).
  * **Complex queries are common:** Your application relies on complex joins, aggregations, and multi-table queries.
  * **Scalability is vertical:** Your application can scale by increasing the power of a single server.

**Use cases:** E-commerce, banking, inventory management, or any application with well-defined relationships between data.

**Choose NoSQL (Non-relational Database) when:**

  * **Data is unstructured or semi-structured:** You are dealing with data that is dynamic or has an evolving schema (e.g., user profiles, IoT sensor data).
  * **High availability and scalability are top priorities:** You need to scale horizontally to handle massive traffic and data volumes.
  * **Performance is key for simple operations:** You need fast, low-latency key-value lookups.
  * **Flexibility is important:** Your application's data model may change frequently, and you need the flexibility of a dynamic schema.

**Use cases:** Real-time analytics, big data applications, content management, social networking, and caching.

-----

### What is Replication?

**Replication** is the process of creating and maintaining multiple copies of a database on different servers. The goal of replication is to improve data availability, fault tolerance, and performance.

  * **How it works:** Data changes on a primary server (the "master") are copied to one or more secondary servers (the "slaves" or "replicas").
  * **Types of Replication:**
      * **Master-Slave:** A single master server handles all writes, and the changes are replicated to one or more slave servers. The slaves are read-only.
      * **Multi-Master:** Any server can accept a write, and the changes are replicated to all other servers. This is more complex to manage and can lead to conflicts.
  * **Benefits:**
      * **High Availability:** If the master server fails, a slave can be promoted to become the new master.
      * **Disaster Recovery:** A copy of the data is stored at a remote location.
      * **Performance:** Read-heavy applications can distribute their read queries across multiple slave servers, reducing the load on the master.

-----

### Explain Log-Based Recovery

**Log-based recovery** is a database recovery technique used to ensure the durability of transactions. The database maintains a **transaction log** (or journal) that records every change made to the database.

  * **How it works:**
    1.  Before any change is made to the database, a record of that change is written to the transaction log. This is known as the **Write-Ahead Logging (WAL)** principle.
    2.  The log entry contains information like the transaction ID, the data item changed, the old value, and the new value.
    3.  If the system crashes before a transaction is committed, the log can be used to perform recovery.
  * **Recovery Process:**
      * **`UNDO`:** The recovery manager reads the log and uses the old values to undo the changes made by any transactions that were not committed.
      * **`REDO`:** It then uses the new values in the log to redo the changes made by any transactions that were committed but whose changes had not yet been written to disk.
  * **Benefit:** This method ensures that the database can be restored to a consistent state after a crash, thus guaranteeing the durability of committed transactions.

-----

### Difference between File System and DBMS

| Feature | File System | DBMS (Database Management System) |
| :--- | :--- | :--- |
| **Data Storage** | Stores data in individual files in a hierarchical directory structure. | Stores data in a structured, integrated format (tables, documents, etc.). |
| **Data Access** | Requires custom code for each application to access and manage files. | Provides a standard interface (e.g., SQL) for all applications to access data. |
| **Data Integrity** | Limited data integrity mechanisms. Data consistency is the responsibility of the application. | Strong data integrity mechanisms (e.g., constraints, foreign keys, ACID properties). |
| **Data Redundancy** | High potential for data redundancy and inconsistency. | Controlled data redundancy through normalization and a structured schema. |
| **Concurrency** | Limited or no support for concurrent access. | Built-in concurrency control mechanisms (e.g., locking) to handle multiple users. |
| **Security** | File-level security (e.g., read/write permissions). | Granular, user-based security (e.g., permissions on tables, rows, or specific actions). |

A DBMS is a more sophisticated and robust way to manage data than a file system, especially for applications that require multiple users, complex queries, and high data integrity.

-----

### Explain Data Modeling

**Data modeling** is the process of creating a visual representation of a database's structure. It's a crucial step in database design, as it helps to define and analyze the business requirements and how they relate to the data.

  * **Purpose:**
      * To ensure all necessary data is stored and that relationships between data are clear.
      * To facilitate communication between designers, developers, and business stakeholders.
      * To help in designing an efficient and consistent database.
  * **Types of Data Models:**
      * **Conceptual Model:** The highest-level model, which describes the entities and relationships from a business perspective, without worrying about technology.
      * **Logical Model:** Defines the structure of the data in detail, including tables, columns, data types, and relationships. It is independent of the specific DBMS.
      * **Physical Model:** The lowest-level model, which describes how the data is physically stored on the database (e.g., indexes, partitions). It is specific to the chosen DBMS.
  * **Tools:** ER diagrams are a popular tool for data modeling.

-----

### What are Aggregate Functions in SQL?

**Aggregate functions** are SQL functions that perform a calculation on a set of values and return a single value. They are often used with the `GROUP BY` clause to perform calculations on groups of rows.

  * **Common Aggregate Functions:**
      * **`COUNT()`:** Counts the number of rows in a set.
      * **`SUM()`:** Calculates the sum of a numeric column.
      * **`AVG()`:** Calculates the average value of a numeric column.
      * **`MIN()`:** Finds the minimum value in a set.
      * **`MAX()`:** Finds the maximum value in a set.
  * **Example:**
    ```sql
    SELECT DepartmentID, COUNT(EmployeeID), AVG(Salary)
    FROM Employees
    GROUP BY DepartmentID
    HAVING AVG(Salary) > 60000;
    ```
    This query uses `COUNT()` and `AVG()` to find the number of employees and the average salary for each department.

-----

### What are Constraints in SQL?

**Constraints** are rules or restrictions applied to a table's columns to enforce data integrity and consistency. They are a fundamental part of relational database design.

  * **Common Constraints:**
      * **`PRIMARY KEY`:** Uniquely identifies each row in a table. A table can have only one primary key, and it cannot contain `NULL` values.
      * **`FOREIGN KEY`:** Links a column in one table to the primary key in another table, enforcing a relationship.
      * **`UNIQUE`:** Ensures that all values in a column are unique. Unlike a primary key, a table can have multiple unique constraints, and they can contain `NULL` values.
      * **`NOT NULL`:** Ensures that a column cannot have a `NULL` value.
      * **`CHECK`:** Ensures that a column's values satisfy a specific condition (e.g., `Age > 18`).
      * **`DEFAULT`:** Specifies a default value for a column if no value is provided.

-----

### Explain the structure of the SQL execution engine.

The **SQL execution engine** is the core component of a DBMS that executes SQL queries. The process can be broken down into several stages:

1.  **Parser:** The SQL query is parsed to check for syntactic and semantic correctness. It generates an internal representation of the query (e.g., a query tree).
2.  **Query Optimizer/Planner:** The optimizer analyzes the query and the database's metadata (e.g., indexes, statistics) to find the most efficient way to execute the query. It generates an execution plan.
3.  **Execution Engine:** The execution engine takes the plan from the optimizer and performs the actual work. It calls various modules to perform operations like:
      * **Access Methods:** Fetching data from disk (e.g., a full table scan or an index scan).
      * **Relational Operators:** Performing operations like joins, selections, and projections.
      * **Buffer Manager:** Manages the movement of data between disk and main memory (the buffer pool).
      * **Concurrency Control Manager:** Ensures that transactions don't interfere with each other by using locks.
      * **Transaction Manager:** Manages transactions, ensuring the ACID properties.
4.  **Result Set:** The final result is returned to the client.

-----

### What is the ACID test in practice?

In a practical sense, the **ACID test** refers to a set of tests used to verify that a database system or an application's transactions meet the ACID properties.

  * **Atomicity Test:**
      * **Scenario:** A transaction with multiple steps. A failure is simulated (e.g., a system crash or an error) in the middle of the transaction.
      * **Expected Result:** The entire transaction is rolled back, and the database remains in its original state. There are no partial changes.
  * **Consistency Test:**
      * **Scenario:** A transaction is executed that would violate a database constraint (e.g., trying to set a foreign key to a non-existent value or creating a negative balance).
      * **Expected Result:** The database rejects the transaction, and the database remains in a valid state.
  * **Isolation Test:**
      * **Scenario:** Two or more transactions are executed concurrently, with one transaction trying to read data that another is modifying.
      * **Expected Result:** The transactions do not interfere with each other. For example, a transaction reading data should not see the uncommitted changes of another transaction (depending on the isolation level). The final state of the database is the same as if the transactions were run sequentially.
  * **Durability Test:**
      * **Scenario:** A transaction is successfully committed. Immediately after, a power failure is simulated.
      * **Expected Result:** When the system is restarted, the committed changes are still present in the database.
