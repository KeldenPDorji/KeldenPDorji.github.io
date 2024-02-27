---
Title: DBS101 Flipped Class 3
categories: [DBS101, Flipped_Class2]
tags: [DBS101]
---

## Topic: Understanding SQL Set Operation and NULL Values
----

The SQL Set operation is used to combine the two or more SQL SELECT statements. 

1.UNION:

    Syntax:
    SELECT column1, column2, 
    FROM table1
    UNION
    SELECT column1, column2, 
    FROM table2;

Purpose: Combines the results of two or more SELECT statements and removes duplicate tuples.
Constraints:

    Each SELECT statement within UNION must have the same number of columns.
    Columns must have similar data types.
    Result set is sorted and duplicate rows are removed.

2.UNION ALL:

    Syntax:
    SELECT column1, column2, 
    FROM table1
    UNION ALL
    SELECT column1, column2, 
    FROM table2;

Purpose: Similar to UNION,but it retains all rows including duplicates.
It is faster than UNION due to the absence of duplicate elimination.

Constraints:

    Each SELECT statement within UNION ALL must have the same number of columns with compatible data types.

3.Intercept:

    Syntax:
    SELECT column1, column2, 
    FROM table1
    MINUS
    SELECT column1, column2, 
    FROM table2;

Purpose: Returns only the rows that appear commonly in both the sets.

Constraints:

    Each SELECT statement within INTERSECT must have the same number of columns with compatible data types.

4.MINUS:

    Syntax:
    SELECT column1, column2, 
    FROM table1
    MINUS
    SELECT column1, column2, 
    FROM table2;

Purpose: Returns only the rows that appear in the first result set but not in the second.

Constraints:

    Each SELECT statement within MINUS must have the same number of columns with compatible data types.

## NULL values in SQL

In SQL,NULL represents an unknown value or missing value in a table's attribute. It depicts the absence of a value rather than an empty sting or zero.It indicates a misiing information and not equal to anything. 

### Handling NULL Values:

IS NULL: Checks if a value is NULL.

    SELECT * FROM table_name WHERE column_name IS NULL;

IS NOT NULL: Checks if a value is not NULL.

    SELECT * FROM table_name WHERE column_name IS NOT NULL;

COALESCE: Returns the first non-NULL value in a list of expressions.

    SELECT COALESCE(column_name, 'Default') FROM table_name;

NULLIF: Returns NULL if the two specified expressions are equal; otherwise, returns the first expression.

    SELECT NULLIF(column1, column2) FROM table_name;
