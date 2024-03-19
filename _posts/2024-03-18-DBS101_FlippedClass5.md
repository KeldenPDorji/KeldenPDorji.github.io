---
Title: DBS101 Flipped Class 5
categories: [DBS101, Flipped_Class5]
tags: [DBS101]
---

## Topic: Reaching the Depths of Relational Database Normalization

First Normal Form (1NF):

    Dictates that every value in a table should be atomic, i.e. no values can be further divided into other values.
    Gets rid of repeating groups by putting each attribute in a separate column.
    For example, converting a column containing multiple phone numbers into separate columns for each phone number.

Second Normal Form (2NF):

    Builds on 1NF and ensures that all non-key attributes are fully functionally dependent on the primary key.
    Simply put, every non-prime attribute is fully dependent on the entire primary key.
    In case a table has a composite primary key, then each non-key attribute should be dependent on all parts of the composite key.
    Example: A table with columns (OrderID, ProductID, ProductName, ProductDescription). Here, ProductName and ProductDescription are dependent only on ProductID, not on OrderID.

Boyce-Codd Normal Form (BCNF):

       A stronger version of 3NF where every determinant (column whose value determines another column’s value) is a candidate key.
       A table is in BCNF if for every non-trivial functional dependency, X → Y, X must be a superkey.
       Example: If a table has columns (StudentID, CourseID, Professor), and (StudentID,CourseID) determines Professor then both(StudentID,CourseID) must be a superkey.

Third Normal Form (3NF):

    Builds on 2NF and makes sure that there are no transitive dependencies: no non-prime attribute is dependent on another non-prime attribute.
    In other words, every non-prime attribute must be directly dependent on the primary key.
    Example: A table with columns (EmployeeID, DepartmentID, DepartmentLocation). Here, DepartmentLocation is dependent on DepartmentID, not on EmployeeID.

Fourth Normal Form (4NF):

    A further normalization of a database schema to handle multi-valued dependencies.
    A table is in 4NF if it is in BCNF and has no multi-valued dependencies at all.
    Multi-valued dependencies occur when a value in one column uniquely determines a set of values in another column(s) which are not part of any candidate key.
    Example: A table with columns (EmployeeID, ProjectID, Skill). Here, if (EmployeeID, ProjectID) determines Skill and there are no dependencies between EmployeeID and ProjectID then it's in 4NF.