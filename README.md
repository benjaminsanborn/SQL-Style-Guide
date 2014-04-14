SQL Style Guide  - v.0.1
=========================

This guide is intended to provide best-practices for SQL in use in Play! frameworks, but can be generally applied.

## Reserved Words

Because SQL allows you to write very English-esque statements in many different ways. Therefore, SQL has a lot of reserved words. That is just the way of things. Consult your SQL engines documentation for all reserved words. They include, but are not limited to:

```
ABSOLUTE, ALLOCATE, AS, BOTH, CASCADE, CASE, CAST, CHAR, CHARACTER, COALESCE, COLLATE, COLLATION, COLUMN, CONNECTION, CONSTRAINT, CROSS, CURRENT_DATE, CURRENT_TIME, CURRENT_USER, DATE, DAY, DEFERRABLE, DEFERRED,  DESCENDING, DESCRIBE, DISCONNECT, DOMAIN, EXTRACT, FALSE, FULL, IN, INNER, INT, INTEGER, INTERVAL, JOIN, LANGUAGE, LAST, LEFT, LOWER, MINUTE, MONTH, NATURAL, NEXT, NO, NULL, NULLIF, NUMERIC, OUTER, REAL, RELATIVE, RESTRICT, RIGHT, SMALLINT, SQL, SQLSTATE, SUBSTRING, TIME, TIMESTAMP, TRANSLATE, TRANSLATION, TRIM, TRUE, UPPER, USAGE, VALUE, VARCHAR, YEAR
```

### DO NOT USE RESERVED WORDS

Never name any table, view, function, column name, user after a reserved word. They are reserved; that reservation is not for you.

## Naming

All DB names (tables, views, columns) should be in snake_case.

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

#### Primary keys
If the primary key of a table is a single, autoincrementing integer, it should be named "id".

#### Composite keys

## Line wrapping

Generally, every clause should get its own line.

```
...
WHERE guests > 1 AND start_time > NOW();
```
# 
[http://standards.iso.org/ittf/PubliclyAvailableStandards/c053681_ISO_IEC_9075-1_2011.zip]
_see how many typos you can find!_
