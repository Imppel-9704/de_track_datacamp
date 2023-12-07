# Introduction to Relational Database in SQL

Create table
```
CREATE TABLE table_name (
  col1 text,
  col2 numeric,
  col3 char(5)
);
```

Insert data from table_1 to table_2
```
INSERT INTO table_2
SELECT 
  DISTINCT col1,
  col2
FROM table_1
```

The INSERT INTO statement
```
INSERT INTO table_name (col1, col2)
VALUES ("value_a", "value_b");
```

Rename column
```
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;
```

DROP column
```
ALTER TABLE table_name
DROP COLUMN column_name;
```

Delete table
```
DROP TABLE table_name;
```

Type CAST to chage datatype
```
SELECT CAST(column AS integer)
FROM table_name;
```

## Common Data Types
- Text: Character strings of any length.
- varchar [(x)]: a maximum of n characters.
- char [(x)]: a fixed length string of n characters.
- boolean: True, False, Null.
- date, time, timestamp: formats for date and time.
- numeric: arbitary precision numbers e.g. 3.1455.
- integer: whole numbers in range of -213985 and +1236530.

## Specify data types upon table creation
```
CREATE TABLE students (
  ssn integer,
  name varchar(64),
  dob date,
  average_grade number(3, 2), -- e.g. 5.54
  tution_paid boolean
);
```

## Alter types after table creation
```
ALTER TABLE students
ALTER COLUMN name
TYPE varchar(168);
```

```
ALTER TABLE students
ALTER COLUMN average_grade
-- Turns 5.54 into 6, not 5, before type conversion
USING ROUND(average_grade);
```

## How to add or remove a NOT-NULL constraint 
### when creating a table
```
CREATE TABLE students (
  ssn integer NOT NULL,
  name varchar(64) NOT NULL
  home_phone integer,
  office_phone interger
);
```

### after the table has been created
```
ALTER TABLE students
ALTER COLUMN home_phone
SET NOT NULL;
```

```
ALTER TABLE students
ALTER COLUMN ssn
DROP NOT NULL;
```

## Adding unique constraints
```
CREATE TABLE table_name (
  column_name UNIQUE
);
```

```
ALTER TABLE table_name
ADD CONSTRAINT some_name UNIQUE(column_name);
```

## Primary Key
- Uniquely identifies records, e.g. for referencing in other tables.
- Unique and not null constraints both apply.
- Primary key are time-invariant.

## Specify primary key
```
CREATE TABLE products (
  product_no integer UNIQUE NOT NULL,
  name text,
  price numeric
);
CREATE TABLE products (
  product_no integer PRIMARY KEY,
  name text,
  price numeric
); 
```

```
CREATE TABLE example (
  a integer,
  b integer,
  c integer,
  PRIMARY KEY(a, c)
);
```

```
ALTER TABLE table_name
ADD CONSTRAINT some_name PRIMARY KEY (column_name);
```

## Surrogate key

## Adding surrogate key with serial data type
```
INSERT INTO cars
VALUES ('Opel', 'Astra', 'green', 1);
```

```
ALTER TABLE table_name
ADD COLUMN column_c varchar(256)

UPDATE table_name
SET column_c = CONCAT(column_a, column_b);
ALTER TABLE table_name
ADD CONSTRAINT pk PRIMARY KEY (column_c);
```

```
-- Count the number of distinct rows with columns make, model
SELECT COUNT(DISTINCT(make, model)) 
FROM cars;

-- Add the id column
ALTER TABLE cars
ADD COLUMN id varchar(128);

-- Update id with make + model
UPDATE cars
SET id = CONCAT(make, model);

-- Make id a primary key
ALTER TABLE cars
ADD CONSTRAINT id_pk PRIMARY KEY(id);

-- Have a look at the table
SELECT * FROM cars;
```

## Foreign Key (FK)
- Foreign Key are designated columns that point to a primary key of another table.
- Domain of FK must be equal to domain PK.
- Each value of FK must exist in PK of the other table.
- FKs are not actual keys.

## Specifying foreign keys
```
CREATE TABLE manufactorers (
  name varchar(255) PRIMARY KEY
);

INSERT INTO manufactorers
VALUES ('Ford'), ('VW'), ('GM');

-- after that create table that have foreign key
CREATE TABLE cars (
  model varchar(255) PRIMARY KEY,
  manufactorer_name varchar(255) REFERENCES manufactorers (name)
);

INSERT INTO cars
VALUES ('Ranger', 'Ford'), ('Beetle', 'VW');
```

## Specifying foreign key to existing table
```
ALTER TABLE a
ADD CONSTRAINT a_fkey FOREIGN KEY(b_id) REFERENCES b (id);
```

Example
```
-- Add a professor_id column
ALTER TABLE affiliations
ADD COLUMN professor_id integer REFERENCES professors (id);

-- Rename the organization column to organization_id
ALTER TABLE affiliations
RENAME organization TO organization_id;

-- Add a foreign key on organization_id
ALTER TABLE affiliations
ADD CONSTRAINT affiliations_organization_fkey FOREIGN KEY (organization_id) REFERENCES organizations (id);
```

## Referential Integrity
- A record refering another table must refer to an existing record in that table.
- Specified between 2 table.
- Enforced through foreign keys.

## Dealing with violations
1. NO ACTION : it will throw an error.
2. CASCADE : Delete all referencing records.
3. RESTRICT : Throw an error.
4. SET NULL : Set the referencing column to NULL.
5. SET DEFAULT : Set the referencing column to its default value.

```
-- This way is preventing from delete column that is referenced.
CREATE TABLE a(
  id integer PRIMARY KEY,
  column_a varchar(64),
  b_id integer REFERENCES b (id) ON DELETE NO ACTION
);
```

```
-- For this way if record in table b is deleted, then it will automatically delete referencing record in table a.
CREATE TABLE a (
  id integer PRIMARY KEY,
  column_a varchar(64),
  b_id integer REFERENCES b (id) ON DELETE CASCADE
);
```