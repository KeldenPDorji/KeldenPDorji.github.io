---
Title: DBS101 Flipped Class 9
categories: [DBS101, Flipped_Class9]
tags: [DBS101]
---

## Topic: Materialised Views and Advanced Topics in Query Optimization

### Materialized view

A materialized view is also known as a snapshot: it is formally defined as a physical representation of a query that is stored in memory, so that subsequent queries can be optimally executed against it. Upon creation, the developer may use several optional parameters to specify more precisely how the materialized view is to be created. There are two ways to specify how a materialized view is created: whether or not it is available for querying and whether it is immediately available. The BUILD IMMEDIATE parameter implies that the materialized view is built immediately, while BUILD DEFERRED ensures that the materialized view is created after the first refresh. As for when the data is refreshed, two options exist: REFRESH ON COMMIT means that the data in the materialized view is refreshed just before data in the source table is written if the result of the query doe not already exist, essentially meaning that the materialized view will always contain the most recently inserted data, while REFRESH ON DEMAND means that the developer can specify a condition when the data in the materialized view is refreshed.

### Difference Between Materialized View And View :

| **Views**                                                                                               | **Materialized Views (Snapshots)**                                                                         |
|---------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| Views are simply logical structures that do the retrieval of data from one or more tables.             | Materialized views are logical structures, but data is physically materialized in the database.           |
| You can create simple or complex views with the CREATE VIEW privilege.                                   | The CREATE MATERIALIZED VIEW privilege should be required to create materialized views.                   |
| Data access is not as quick as for a materialized view because the data is fetched from the underlying tables anytime a view is accessed. | Retrieval of data is faster than simple views due to the fact that the data is accessed directly from where it is physically stored. |
| Type of views : <br> - Simple Perspective <br> - Expanded View                                           | Materialized views can be classified into several types: <br> - Refresh on Auto <br> - Activate on Request |
| Applications generally use views to provide limited access to the database.                               | Materialized views find application mainly in data warehousing.                                            |


### Advanced Topics in Query Optimization

#### Query Optimization Techniques:

1. **Cost-Based Optimization:**
   - It looks into different execution plans for a query and then chooses the one with the minimum cost estimated.
   - Cost factors, for example, disk I/O, CPU time, and memory use.

2. **Indexing:**
   - Proper indexing will provide for query performance by making the query need to call the disk I/O operation as few times as possible to retrieve data.
   - This includes setting up indexes on columns most frequently used in WHERE clauses and JOIN conditions.

3. **Join Strategies:**
   - The optimizer decides the best strategy for joining based on the table sizes, available indexes, and join conditions.
   - Strategies include nested-loop join, merge join, and hash join.

4. **Parallel Query Execution:**
   - Some database systems support parallel query execution, wherein a single query is divided into many tasks that can be done at the same time in multiple processor cores.
   - Parallel execution can help a lot in decreasing the response time of queries that are CPU-intensive.

5. **Query Rewriting:**
   - Query rewriting is a process where a given user query is transformed into an equivalent but at the same time more effective form.
   - Techniques include sub-query un-nesting, view merging, and predicate pushdown.

6. **Materialized Views:**
   - Materialized views can be used to help optimize queries, whereby results of frequently executed queries are pre-computed and stored.

#### More Advanced Optimization Techniques:

1. **Partitioning:**
   - Partitioning refers to the breaking down of a big table into smaller, more manageable parts called partitions.
   - Query performance with respect to a specific query can be improved through partitioning of data.

2. **Advanced Indexing Techniques:**
   - Advanced indexing techniques use bitmap indexes, function-based indexes, and index-organized tables.
   - These techniques can further improve query performance in specific scenarios.

3. **Statistics Collection:**
   - The query optimizer uses statistics to prepare the best execution plans. Collection and regular updating of statistics are among the very important activities for the proper working of queries.

4. **Query Plan Caching:**
   - Some database systems cache the query execution plan so that it does not need to be re-optimized for the query a few times, to save the cost of that.
   - Query plan caching can achieve performance by firing the same query repeatedly with a common set of parameters.

5. **Query Hint:**
   - Developers can influence the query optimizer via query hinting to get a desired execution plan. 
   - As a general practice, query hinting must be avoided but ought to be useful up to some extent in very narrow cases where optimizer decisions are bad.
