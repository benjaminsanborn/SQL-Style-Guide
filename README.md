SQL style recommendations
=========================

recommended style guide for SQL

# Reserved Words

Because SQL allows you to write very English-esque statements in many different ways. Therefore, SQL has a lot of reserved words. That is just the way of things. Consult your SQL engines documentation for all reserved words. They include, but are not limited to:

```
ABSOLUTE, ALLOCATE, BIT, BOTH, CASCADE, CASE, CAST, CHAR, CHARACTER, COALESCE, COLLATE, COLLATION, COLUMN, CONNECTION, CONSTRAINT, CROSS, CURRENT_DATE, CURRENT_TIME, CURRENT_USER, DATE, DAY, DEFERRABLE, DEFERRED,  DESCENDING, DESCRIBE, DISCONNECT, DOMAIN, EXTRACT, FALSE, FULL, INNER, INT, INTEGER, INTERVAL, JOIN, LANGUAGE, LAST, LEFT, LOWER, MINUTE, MONTH, NATURAL, NEXT, NO, NULL, NULLIF, NUMERIC, OUTER, REAL, RELATIVE, RESTRICT, RIGHT, SMALLINT, SQL, SQLSTATE, SUBSTRING, TIME, TIMESTAMP, TRANSLATE, TRANSLATION, TRIM, TRUE, UPPER, USAGE, VALUE, VARCHAR, YEAR
```

## DO NOT USE RESERVED WORDS

Never name any table, view, function, column name, user after a reserved word. They are reserved; that reservation is not for you.

# 
[http://standards.iso.org/ittf/PubliclyAvailableStandards/c053681_ISO_IEC_9075-1_2011.zip]
_see how many typos you can find!_
