# Database Design

## OLTP and OLAP
- OLTP : Online Transaction Processing
- OLAP : Online Analytical Processing

## Concrete Example
If working in Book Store
OLTP
- Find the price of a book.
- Update latest customer transaction.
- Keep track of employee hour.

OLAP
- Calculate books with best profit margin.
- Find most loyal customers.
- Decide employee of month.

### Structuring Data
1. Structured Data
- SQL, Tables in RDBMS, .csv file.

2. Unstructured Data
- photos, chat logs, mp3.

3. Semi-structured Data
- .json, .xml, NoSQL.

## Data Warehouse
- Optimized for analytics. - OLAP
- Contains data from multiple sources.
- Massive parallel Processing (MPP).
- Typically uses a denormalized schema and dimensional modeling.

## Data Mart
- Subset of data warehouse.
- Dedecated to a specific topic.

## Data Lake
- Store all types of data
- Retains all data and can take up petabytes.
- Schema-on-read as opposed to schema-on-write.
- Need to catalog data otherwise becomes a dataswamp.
- Run big data analytics using services such as Apache Spark or Hadoop.

## Data Modeling
1. Conceptual data model: describes entities, relationships, and attributes.
2. Logical data model: deifines tables, columns, relationships.
3. Physical data model: describes physical storage.

## Normalization
- Database design technique.
- Divides tables into smaller tables and connect them via relationships.
Purpose : to reduce redundancy and increase data integrity.
Advantages
1. It eliminates data redundancy = save on storage.
2. Better data integrity = accurate and consistent data.
Disadvantages
1. Complex queries = require more CPU.

Denormalized: Star schema
Normalized: Snowflake schema

## Normal Form
### 1NF rules
- Each record must be unique (No duplicates).
- Each cell must hold one value.

### 2NF rules
- Must satifies 1NF
- If primary key is one column then automatically satifies 2NF.
- If there is composite primary key then each one key column must be dependent on all the keys.

### 3NF rules
- Satifies 2NF
- No transitive dependencies: non-key columns can't depend on other non-key column.

## Data Anomalies
1. Update anomaly : Data inconsistency caused by data redendancy when updating.
2. Insertion anomaly : Unable to add a record due to missing attributes.
3. Deletion anomaly : Deletion of record(s) causes unintentional loss of data.

## Database View
- Query, not data, is stored in memory.
- Data is aggregated from data in tables.
- Can be queried like a regular database tables.
- No need to retype common queries or alter schema.

### Syntax
```
CREATE VIEW view_name AS
SELECT col1, col2
FROM table
WHERE condition
```

## Viewing views (PostgreSQL)
```
SELECT * FROM INFORMATION_SCHEMA.views;
```

## Granting or Revoking access to view
- GRANT privilege(s) or REVOKE privilege(s)
- Privilege : SELECT, INSERT, UPDATE, DELETE, etc.

```
GRANT UPDATE ON ratings TO PUBLICS;
```

```
REVOKE INSERT ON films FROM db_user;
```

## Updating a View
```
UPDATE films SET kind = 'dramatic' WHERE kind = 'drama'
```

## Dropping a View
```
DROP VIEW view_name [ CASCADE | RESTRICT ];
```
- CASCADE : drops view and object that depends on that view.
- RESTRICT (default) : return an error if there are object that depends on that view.

## 2 types of Views
1. Views
- AKA. non-materialized views.

2. Materialized views
- Physically materialized.
- Stores query results, not the query.
- accessing the stored query result. (not running query like non-materialized views)
- Refreshed or rematerialized when prompted or scheduled.

## When to use materialized view?
- Long running queries.
- Underlying query results don't change often.
- Data Warehouse because OLAP is not write-intensive.

```
CREATE MATERIALIZED VIEW my_mv AS 
SELECT * 
FROM table;
```

```
REFRESH MATERIALIZED VIEW my_mv;
```

## Database Roles
- Manage database access permission.
- Define the role's privileges.
- Interact with the client authentication system.
- Roles can be assigned to one or more users.
- Roles are global across a database cluster installation.

## Create roles.
### empty role
```
CREATE ROLE data_analyst;
```

### Role with some attributes set
```
CREATE ROLE intern WITH PASSWORD 'passwordforintern' VALID UNTIL '2023-12-31';
```

```
CREATE ROLE admin CREATEDB;
```

```
CREATE ROLE admin CREATEROLE;
```

### Users and groups
- A role is an entity that can function as a user and/or a group.
  - User group.
  - Group roles.

```
GRANT data_analyst TO intern;
```
```
REVOKE data_analyst FROM intern;
```

## Partitioning
1. Vertical partitioning
  - split the table vertically by its columns.
2. Horizontal partitioning

```
CREATE TABLE sales (
  ...
  timestamp DATE NOT NULL
)
PARTITION BY RANGE (timestamp);

CREATE TABLE sales_2019_q1 PARTITION OF sales
FOR VALUES FROM ('2019-01-01') TO ('2019-03-31');

CREATE TABLE sales_2019_q4 PARTITION OF sales
FOR VALUES FROM ('2019-10-01') TO ('2019-12-31');

CREATE INDEX ON sales ('timestamp');
```

### Example
```
-- Create a new table called film_partitioned
CREATE TABLE film_partitioned (
  film_id INT,
  title TEXT NOT NULL,
  release_year TEXT
)
PARTITION BY LIST (release_year);

-- Create the partitions for 2019, 2018, and 2017
CREATE TABLE film_2019
	PARTITION OF film_partitioned FOR VALUES IN ('2019');

CREATE TABLE film_2018
	PARTITION OF film_partitioned FOR VALUES IN ('2018');

CREATE TABLE film_2017
	PARTITION OF film_partitioned FOR VALUES IN ('2017');

-- Insert the data into film_partitioned
INSERT INTO film_partitioned
SELECT film_id, title, release_year FROM film;

-- View film_partitioned
SELECT * FROM film_partitioned;
```