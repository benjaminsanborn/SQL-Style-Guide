SQL Style Guide  - v.0.1
=========================

This guide is intended to provide best-practices for SQL in use in Play! frameworks, but can be generally applied.

# DDL (Data Definition Language)

DDL style and convention is the single most important factor in creating a schema that people understand and don't hate you for. Properly documenting your style and convention is the second most important thing you can do. If you are building a schema from scratch, this guide is not for you. I would recommend picking up [Database Design for Mere Mortals](http://www.amazon.com/Database-Design-Mere-Mortals-Relational/dp/0201752840).

If you're working with an existing schema, understanding both the original spirit of the schema and the best-practices outlined below is essential. The below style conventions need to be balanced with the existing schema to minimize confusion.

## Reserved Words

Because SQL allows you to write very English-esque statements in many different ways. Therefore, SQL has a lot of reserved words. That is just the way of things. Consult your SQL engines documentation for all reserved words. They include, but are not limited to:

```
ABSOLUTE, ALLOCATE, AS, BOTH, CASCADE, CASE, CAST, CHAR, CHARACTER, COALESCE, COLLATE, COLLATION, COLUMN, CONNECTION, CONSTRAINT, CROSS, CURRENT_DATE, CURRENT_TIME, CURRENT_USER, DATE, DAY, DEFERRABLE, DEFERRED,  DESCENDING, DESCRIBE, DISCONNECT, DOMAIN, EXTRACT, FALSE, FULL, IN, INNER, INT, INTEGER, INTERVAL, JOIN, LANGUAGE, LAST, LEFT, LOWER, MINUTE, MONTH, NATURAL, NEXT, NO, NULL, NULLIF, NUMERIC, OUTER, REAL, RELATIVE, RESTRICT, RIGHT, SMALLINT, SQL, SQLSTATE, SUBSTRING, TIME, TIMESTAMP, TRANSLATE, TRANSLATION, TRIM, TRUE, UPPER, USAGE, VALUE, VARCHAR, YEAR
```

### DO NOT USE RESERVED WORDS

Never name any table, view, function, column name, user after a reserved word. They are reserved; that reservation is not for you.

## Naming

All DB names (tables, views, functions, columns) should be in snake_case.

### Tables

Tables should always be singular. A single tuple in you table should generally be exactly the name of the table.

#### Linking tables (many-to-many relationships)
Linking tables should be the snake_case concatenation of the linked tables. The first table is generally the table more "central" to the rest of the schema.

```
CREATE TABLE user (id int, name text);
CREATE TABLE contract (id int, signatories text);
CREATE TABLE user_contract (user_id int, contract_id int);
```

### Columns

Column names, again, should not be named after reserved words or data types. Ideally, for non-foreign key columns, you should be able to syntactically define the contents of the column by calling it the "<<table_name>>'s <<column_name>>"

  i.e.
  the USERs NAME
  the WAREHOUSE_GOODs STOCK_CODE.

#### Primary keys
If the primary key of a table is a single, autoincrementing integer, it should be named "id".

#### Foreign keys
A foreign key column should always be named the referenced table followed by "_id".

```
ALTER TABLE user_code ADD COLUMN user_id REFERENCES user (id);
```

#### Composite keys

## Line wrapping

Generally, every clause should get its own line.

```
...
WHERE guests > 1 AND start_time > NOW();
```

# DML (Data Manipulation Language)

Hopefully, most SQL you are writing is DML. SQL DML is an incredibly powerful and flexible syntax and, being as such, a very easily abused and obscured language for conveying intent.

## Formatting

## Conventions for clarity


# SQL for Applications

## Inline SQL

# SQL Schema Migrations

## Idempotency

## Migration tools

# 
[http://standards.iso.org/ittf/PubliclyAvailableStandards/c053681_ISO_IEC_9075-1_2011.zip]
_see how many typos you can find!_
