---
Title: DBS101 Flipped Class 5
categories: [DBS101, Flipped_Class5]
tags: [DBS101]
---

## Topic: Reaching the Depths of Relational Database Normalization

Database normalization is the process of organizing a relational database in accordance with a series of so-called normal forms in order to reduce data redundancy and improve data integrity. It was first proposed by Edgar F. Codd.

“Normal Forms” (NF) are the different stages of normalization

    1 NF (First Normal Form)
    2 NF (Second Normal Form)
    3 NF (Third Normal Form)
    BCNF (Boyce -Codd Normal Form)
    4 NF (Fourth Normal Form)
    5 NF (Fifth Normal Form)
    6 NF (Sixth Normal Form)

4NF to 6NF applies to multivalued dependencies and complex table scenarios. 

![DATABASE](https://editor.analyticsvidhya.com/uploads/55956normalization.jpg)

### First Normal Form (1NF):
---

Dictates that every value in a table should be atomic, i.e. no values can be further divided into other values.
Gets rid of repeating groups by putting each attribute in a separate column.
For example, converting a column containing multiple phone numbers into separate columns for each phone number.

A relation R is said to be in 1 NF (First Normal) if and only if:

    1.All the attributes of R are atomic.
    2.It does not contain any multi-valued attributes.

In the above-taken example of the Retail_Outlets table, we have stored multiple values in an address field, such as street name, city name, and pin code.

What if we want to know about all retail outlets in a given city? We may need to perform some string operations on the address field, which is not preferable. So we need to store all these atomic values in separate fields.

A multi-valued attribute is an attribute that can have multiple values like Contact numbers. They should also be separated like ContactNo1, ContanctNo2,.. to achieve 1st Normal form.

![DATABASE](https://editor.analyticsvidhya.com/uploads/40926Blank%20board%20(3).jpeg)

1st Normal Form

Advantage: 1 NF allows users to use the database queries effectively as it removes ambiguity by removing the non-atomic and multi-valued attributes, which creates major issues in the future while updating and extracting the data from the database.

Limitation: Data redundancy still exists even after 1st Normal form, so we need further normalization.

### Second Normal Form (2NF):
---

Builds on 1NF and ensures that all non-key attributes are fully functionally dependent on the primary key.
Simply put, every non-prime attribute is fully dependent on the entire primary key.
In case a table has a composite primary key, then each non-key attribute should be dependent on all parts of the composite key.
Example: A table with columns (OrderID, ProductID, ProductName, ProductDescription). Here, ProductName and ProductDescription are dependent only on ProductID, not on OrderID.

A relation R is said to be in 2 NF (Second Normal) form if and only if:

    1.R is already in 1 NF
    2.There is no partial dependency in R between non-key attributes and key attributes.

Suppose we have a composite primary or candidate key in our table. Partial dependency occurs when a part of the primary key (Key attribute) determines the non-key attribute.

In the Retail Outlets table, the Item_Code and Retail_Outlet_ID are key attributes. The item description is partially dependent on Item_Code only. Outlet_Location depends on Retail_Outlet_ID. These are partial dependencies.

To achieve normalization, we need to eliminate these dependencies by decomposing the relations.

![DATABASE](https://editor.analyticsvidhya.com/uploads/86127Blank%20board%20(7).jpeg)

2nd Normal Form

From the above decomposition, we eliminated the partial dependency.

Advantage: 2 NF attempts to reduce the amount of redundant data in a table by extracting it, placing it in a new table(s), and creating relationships between those tables.

Limitation: There are still some anomalies, as there might be some indirect dependencies between Non-Key attributes, leading to redundant data.

### Boyce-Codd Normal Form (BCNF):
---

A stronger version of 3NF where every determinant (column whose value determines another column’s value) is a candidate key.
A table is in BCNF if for every non-trivial functional dependency, X → Y, X must be a superkey.
Example: If a table has columns (StudentID, CourseID, Professor), and (StudentID,CourseID) determines Professor then both(StudentID,CourseID) must be a superkey.

It is an upgraded version of the 3rd Normal form. It is also called as 3.5 Normal Form.

A relation R is said to be in 3 NF (Third Normal Form) if and only if:

    1.R is already in 3 NF
    2.For any dependency A –> B, then A should be the Super key.

In simple words, if A –> B, then A cannot be a non-prime Attribute if B is a prime attribute which means that A non-prime attribute cannot determine a prime attribute.

You must be wondering how’s this possible. but Yes, there can be some cases in which the Non-Prime attribute will determine the prime attributes even if the relationship was in the 3rd Normal form. BCNF does not allow this kind of dependency.

Sample Table

Let us understand this better with an example. Look at the below Relation of Student Enrollments table.
Student_ID	Course_Name	Professor
101	JAVA	Prof. Java
102	C++	Prof. CPP
101	Python	Prof. Python
103	JAVA	Prof. Java_2
104	Python	Prof. Python_2

In the above relation:

One student can enroll in multiple courses.
Multiple professors can teach one course.
One professor can be assigned only one course.

So the (Student_ID & Course_Name) will form the primary key. These 2 will compositely determine all other attributes in the relation. In our case, it is only the professor.

The Relation is clearly in 1st Normal Form as there are No Multivalued attributes, and all attributes have atomic values.
The Relation is in 2nd Normal Form as there are No Partial dependencies.
Student_Id cannot determine Course_Name as one student can enroll in multiple courses.
Course_Name cannot determine the professor, as multiple professors may teach the same course.
The relation is in 3rd normal form as there are no transitive dependencies.

If we observe here, the “Professor” attribute, a non-prime attribute, can determine the Course_Name as each professor teaches only one course. But Course_Name is a prime attribute, and Professor is not a Super Key. That means a non-prime attribute determines the prime attribute.

This is not allowed in BCNF. So, how do we decompose this relation?

![DATABASE](https://editor.analyticsvidhya.com/uploads/89118Blank%20board%20(9).jpeg)

### Third Normal Form (3NF):
---

Builds on 2NF and makes sure that there are no transitive dependencies: no non-prime attribute is dependent on another non-prime attribute.
In other words, every non-prime attribute must be directly dependent on the primary key.
Example: A table with columns (EmployeeID, DepartmentID, DepartmentLocation). Here, DepartmentLocation is dependent on DepartmentID, not on EmployeeID.

A relation R is said to be in 3 NF (Third Normal Form) if and only if:

    1.R is already in 2 NF
    2.There is no transitive dependency that exists between key attributes and non-key attributes through other non-key attributes.

A transitive dependency exists when another non-key attribute determines a non-key attribute. In other words, If A determines B and B determines C, then automatically, A determines C.

![DATABASE](https://editor.analyticsvidhya.com/uploads/34025Blank%20board%20(6).jpeg)

Transitive Dependency
---

Some other examples:

The Year of birth determines the Age of the person
The price of an Item determines the class of the Item
The ZIP code of a city determines the City’s Name

![DATABASE](https://editor.analyticsvidhya.com/uploads/17533Blank%20board%20(8).jpeg)

3rd Normal Form

Advantage: 3 NF ensures data integrity. It also reduces the amount of data duplication.

### Fourth Normal Form (4NF):
---

A further normalization of a database schema to handle multi-valued dependencies.
A table is in 4NF if it is in BCNF and has no multi-valued dependencies at all.
Multi-valued dependencies occur when a value in one column uniquely determines a set of values in another column(s) which are not part of any candidate key.
Example: A table with columns (EmployeeID, ProjectID, Skill). Here, if (EmployeeID, ProjectID) determines Skill and there are no dependencies between EmployeeID and ProjectID then it's in 4NF.

### Guidelines for Using Normalization
---

Depending on the business requirements, we can normalize the tables up to the 2nd normal form or the 3rd normal form.
Prefer tables in 3 NF in applications with extensive data modifications.
Prefer tables in 2 NF in applications with extensive data retrieval.
Reason: retrieving data from multiple tables is a costly operation.
Converting the tables from higher normal form to lower normal form is called “Denormalization”.

The below picture summarizes how to reach the third normal form from an unnormalized form:

![DATABASE](https://editor.analyticsvidhya.com/uploads/69177Blank%20board%20(10).jpeg)

Any relational database without normalization may lead to problems like large tables, difficulty maintaining the database as it involves searching many records, poor disk space utilization, and inconsistencies. If we fail to eliminate this kind of problem, it would lead to data integrity and redundancy problems. Normalization of a relational database helps to solve these problems. Normalization applies to a series of transformations in terms of normal forms. Any relation in a database must be normalized to get efficient access to the database. Each Normal form eliminates each type of dependency and improves the data integrity.

### REFERENCE
Sathish Routu. "Database Normalization | A Step-by-Step Guide with Examples." Analytics Vidhya, 31 May 2023. [https://www.analyticsvidhya.com/blog/2022/08/database-normalization-a-step-by-step-guide-with-examples/](https://www.analyticsvidhya.com/blog/2022/08/database-normalization-a-step-by-step-guide-with-examples/)

