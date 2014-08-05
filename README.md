SQL Style Guide  - v.0.1
=========================

This guide is intended to provide best-practices for SQL.

# DDL (Data Definition Language)

DDL style and convention is the single most important factor in creating a schema that people understand and don't hate you for. Properly documenting your style and convention is the second most important thing you can do. If you are building a schema from scratch, this guide is not for you. I would recommend picking up [Database Design for Mere Mortals](http://www.amazon.com/Database-Design-Mere-Mortals-Relational/dp/0201752840). More info under [Further Reading](#further-reading).

If you're working with an existing schema, understanding both the original spirit of the schema and the best-practices outlined below is essential. The below style conventions need to be balanced with the existing schema to minimize confusion.

## Reserved Words

SQL allows you to write very English-esque statements in many different ways. Therefore, SQL has a lot of reserved words. Consult your SQL engine's documentation for all reserved words. They include, but are not limited to:

```
ABSOLUTE, ALLOCATE, AS, BOTH, CASCADE, CASE, CAST, CHAR, CHARACTER, COALESCE, COLLATE, COLLATION, COLUMN, CONNECTION, CONSTRAINT, CROSS, CURRENT_DATE, CURRENT_TIME, CURRENT_USER, DATE, DAY, DEFERRABLE, DEFERRED,  DESCENDING, DESCRIBE, DISCONNECT, DOMAIN, EXTRACT, FALSE, FULL, IN, INNER, INT, INTEGER, INTERVAL, JOIN, LANGUAGE, LAST, LEFT, LOWER, MINUTE, MONTH, NATURAL, NEXT, NO, NULL, NULLIF, NUMERIC, OUTER, REAL, RELATIVE, RESTRICT, RIGHT, SMALLINT, SQL, SQLSTATE, SUBSTRING, TIME, TIMESTAMP, TRANSLATE, TRANSLATION, TRIM, TRUE, UPPER, USAGE, VALUE, VARCHAR, YEAR
```

### DO NOT USE RESERVED WORDS

Never name any table, view, function, column name, or user after a reserved word. They are reserved; that reservation is not for you.

## Casing

All DB names (tables, views, functions, columns) should be in snake_case.

### Tables

Tables should always be singular. A single tuple in you table should generally be exactly the name of the table. If a table is singularly dependent on another table (i.e. a status lookup table) then that table should be named after the parent table. This allows for tables of similar concern to be grouped together.

```SQL
-- Parent table
CREATE TABLE user (id serial PRIMARY KEY, name text, user_status_id int);

-- Dependent lookup table
CREATE TABLE user_status(id serial PRIMARY KEY, status text);

-- Foreign key reference
ALTER TABLE user
  ADD FOREIGN KEY fk_user_status_id user (user_status_id)
  REFERENCES user_status (id);
```

This naming convention can be extended to any arbitrary depth.

```
user
user_action
user_action_status
user_action_attribute
user_status
```

#### Linking tables (many-to-many relationships)
Linking tables should be the snake_case concatenation of the linked tables. The first table is generally the table more "central" to the rest of the schema.

```SQL
-- If the schema is more user concerned
CREATE TABLE contract (id int, signatories text);
CREATE TABLE user (id int, name text);
CREATE TABLE user_contract (user_id int, contract_id int);

-- If the schema is more contract concerned
CREATE TABLE user (id int, name text);
CREATE TABLE contract (id int, signatories text);
CREATE TABLE contract_user (contract_id int, user_id int);
```

### Columns

Column names, again, should not be named after reserved words or data types. Ideally, for non-foreign key columns, you should be able to syntactically define the contents of the column by calling it the "<<table_name>>'s <<column_name>>"

  i.e.
  the USERs NAME
  the WAREHOUSE_GOODs STOCK_CODE.
  
#### Boolean types

When possible, boolean column names should be stripped of any logical modifiers and answer a simple question.

  i.e.
  _BAD_ - ANSWER.IS_NOT_REQUIRED
  _GOOD_ - ANSWER.IS_REQUIRED
  
Although certain SQL engines will force a TINYINT or other on your BOOLEAN columns-- it's best to treat them semantically.

#### Primary keys
If the primary key of a table is a single, autoincrementing integer, it should be named "id".

#### Foreign keys
A foreign key column should always be named the referenced table followed by "_id".

```SQL
ALTER TABLE user_code ADD COLUMN user_id REFERENCES user (id);
```

#### Composite keys

## Line wrapping

Generally, every clause should get its own line.

```SQL
WHERE guests > 1 AND start_time > NOW();
```

# DML (Data Manipulation Language)

Hopefully, most SQL you are writing is DML. SQL DML is an incredibly powerful and flexible syntax and, being as such, a very easily abused and obscured language for conveying intent.

## Formatting

## Conventions for clarity


# SQL for Applications

## Inline SQL

Depending on the application framework, there are ce


# SQL Schema Migrations

As your application develops, you schema needs to develop along side it. 
## Idempotency

## Migration tools

# Further Reading
* [SQL:2011](http://standards.iso.org/ittf/PubliclyAvailableStandards/c053681_ISO_IEC_9075-1_2011.zip) - For reference, this is the current SQL Standard. Check the documentation of your SQL engine for adherence and deviation.
* [Database Design for Mere Mortals](http://www.amazon.com/Database-Design-Mere-Mortals-Relational/dp/0201752840) - For actionable guidance on schema design, this is the best book on the market.
