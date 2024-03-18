---
Title: DBS101 Flipped Class 4
categories: [DBS101, Flipped_Class4]
tags: [DBS101]
---

## Topic: Exploring Advanced SQL Aggregation Techniques: Ranking, Windowing, Pivoting, and Rollup/Cube Functions

### Ranking

Ranking functions are used to give each row within a partition a unique rank. The typical types of ranking functions are RANK(), DENSE_RANK(), ROW_NUMBER(),& NTILE(). ALL these functions can be used with the OVER() clause to set the order of the ranking.

ROW_NUMBER():is a function in the database language Transact-SQL that assigns a unique sequential number to each row in the result set of a query. It gives a distinctive sequenced number to each row within a partition.This is pertinent, for example, for creating a list of items with a unique identifier as a list of students in order of their assessment:

    SELECT StudentName, Subject, Marks,
    ROW_NUMBER() OVER (ORDER BY Marks DESC) AS RowNumber
    FROM ExamResult;

    Output:
    StudentName	Subject	Marks	RowNumber
    Kelden      Maths	65  	1
    Dechen      Science	80  	2
    Tshering    English	89	    3
    Kinley      Science	80	    4
    Sonam       English	90	    5
    Kelden      English	55	    6

RANK(): This function is quite similar to the ROW_NUMBER() above, only that it gives the same value for the rank to the identical rows and gaps the order for the following rank. 

    SELECT StudentName, Subject, Marks,
    RANK() OVER (ORDER BY Marks DESC) AS Rank
    FROM ExamResult;

    Output:
    StudentName	Subject	Marks	Rank
    Kelden	    Maths	65  	1
    Dechen	    Science	80	    2
    Tshering	English	89	    3
    Kinley	    Science	80	    2
    Sonam	    English	90  	4
    Kelden	    English	55  	5

DENSE_RANK(): The DENSE_RANK() function performs the same as RANK() but will not gap the order for the subsequent rank. The computation is performed with the help of the query:

    SELECT StudentName, Subject, Marks,
    DENSE_RANK() OVER (ORDER BY Marks DESC) AS DenseRank
    FROM ExamResult;

    Output:
    StudentName	Subject	Marks	DenseRank
    Kelden	    Maths	65	    1
    Dechen	    Science	80	    2
    Tshering	English	89	    3
    Kinley	    Science	80	    2
    Sonam	    English	90	    4
    Kelden	    English	55	    5   

NTILE(N): This function divides the outcome set into the definite number of groups or buckets. Such groups will contain precisely equal tuples when possible. 

    SELECT *,
    NTILE(2) OVER (ORDER BY Marks DESC) AS Rank
    FROM ExamResult
    ORDER BY rank;

    Output:
    StudentName	Subject	Marks	Rank
    Kelden	    Maths	65  	1
    Dechen	    Science	80  	1
    Tshering	English	89  	1
    Kinley	    Science	80  	2
    Sonam	    English	90  	2
    Kelden	    English	55	    2

### Windowing

SQL window functions are calculation functions similar to aggregate functions but, unlike normal aggregate functions like “group by,” have access to individual rows and can even add some of their attributes into the result set. 
Its a tool used for tasks like moving averages, cumulative sums, running totals, etc.. The basic window function syntax includes PARTITION BY and ORDER BY clauses: 

Moving Average: Calculates the average of a set of values over a specified window.

    SELECT StudentName, Subject, Marks,
    AVG(Marks) OVER (ORDER BY Marks ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS MovingAverage
    FROM ExamResult;

    Output:
    StudentName	Subject	Marks	MovingAverage
    Kelden	    Maths	65  	65
    Dechen	    Science	80  	70
    Tshering	English	89  	84.5
    Kinley	    Science	80  	80
    Sonam	    English	90	    85
    Kelden	    English	55	    72.5

Cumulative Sum: Calculates the cumulative sum of a column over a specified window.

    SELECT StudentName, Subject, Marks,
    SUM(Marks) OVER (ORDER BY Marks ROWS UNBOUNDED PRECEDING) AS CumulativeSum
    FROM ExamResult;

    Output:
    StudentName	Subject	Marks	CumulativeSum
    Kelden	    Maths	65	    65
    Dechen	    Science	80	    145
    Tshering	English	89	    234
    Kinley	    Science	80	    325
    Sonam	    English	90	    425
    Kelden	    English	55	    480

### Pivoting

Pivoting in SQL involves transforming data from a row-oriented format to a column-oriented format, enabling the analysis of data across various categories or time periods. This process is crucial for converting extensive datasets into a more compact and readable structure. In SQL, pivoting can be achieved through the use of the PIVOT operator or by employing conditional aggregation with CASE statements. 

Using PIVOT Operator: Pivots data based on specified columns.

    SELECT *
    FROM (
    SELECT StudentName, Subject, Marks
    FROM ExamResult
    ) AS SourceTable
    PIVOT (
    AVG(Marks)
    FOR Subject IN ([Maths], [Science], [English])
    ) AS PivotTable;

    Output:
    StudentName	Maths	Science	English
    Kelden	    65	    80  	NULL
    Dechen  	NULL	70	    90
    Tshering	55	    NULL	89

Using CASE Statements: Another way to pivot data without using the PIVOT operator.

    SELECT StudentName,
    AVG(CASE WHEN Subject = 'Maths' THEN Marks END) AS Maths,
    AVG(CASE WHEN Subject = 'Science' THEN Marks END) AS Science,
    AVG(CASE WHEN Subject = 'English' THEN Marks END) AS English
    FROM ExamResult
    GROUP BY StudentName;

    Output:
    StudentName	Maths	Science	English
    Kelden	    65	    80	    NULL
    Dechen	    NULL	70	    90
    Tshering	55	    NULL	89

### Rollup and Cube

ROLLUP and CUBE are simple extensions to the SELECT statement's GROUP BY clause. ROLLUP creates subtotals at any level of aggregation needed, from the most detailed up to a grand total. CUBE is an extension similar to ROLLUP , enabling a single statement to calculate all possible combinations of subtotals.

ROLLUP: Generates a result set that includes subtotals for each level of grouping.

    SELECT StudentName, Subject, AVG(Marks) AS AverageMarks
    FROM ExamResult
    GROUP BY ROLLUP(StudentName, Subject);

    Output:
    StudentName	Subject	AverageMarks
    Kelden  	Maths	    65
    Kelden	    Science 	80
    Dechen	    Maths	    50
    Dechen	    Science	    70
    Dechen	    English	    90
    Tshering	Maths	    55
    Tshering	Science	    60
    Tshering	English	    89
    NULL	    NULL	    75

CUBE: Generates a result set that includes subtotals for each combination of grouping columns.

    SELECT StudentName, Subject, AVG(Marks) AS AverageMarks
    FROM ExamResult
    GROUP BY CUBE(StudentName, Subject);

    Output:
    StudentName	Subject	AverageMarks
    Kelden	    Maths	    65
    Kelden	    Science	    80
    Dechen	    Maths	    50
    Dechen	    Science	    70
    Dechen	    English	    90
    Tshering	Maths	    55
    Tshering	Science	    60
    Tshering	English	    89
    NULL	    NULL	    75
    NULL	    Maths	    57.5
    NULL	    Science	    70
    NULL	    English	    89
    Kelden	    NULL	    72.5
    Dechen	    NULL	    70
    Tshering	NULL	    64
    NULL	    NULL	    75