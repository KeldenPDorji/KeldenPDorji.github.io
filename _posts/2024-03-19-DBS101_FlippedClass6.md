---
Title: DBS101 Flipped Class 6
categories: [DBS101, Flipped_Class6]
tags: [DBS101]
---

## Topic: Exploring the Evolution of Database Management Systems: From Relational to Non-relational Paradigms 

### Document-based Databases:

Store and retrieve semi-structured data as documents, often in JSON or BSON format.
Pros:
Design of flexible schema that can handle various data structures within documents.
Perfect for applications with hierarchical data structures.
Scalable and high performance.
Cons:
Lack of ACID transactions in some implementations.
Limited support for complex queries compared to relational databases.

Applications: Content management systems, blogging platforms, e-commerce websites.

### Key-Value based Databases:

The simplest form of NoSQL databases that store data as key-value pairs.
Pros:
Read and write operations are very fast. 
Can be scaled horizontally easily. 
Data retrieval is low in latency. 
Cons:
Querying capabilities are limited, normally only allowing retrieval by key. 
Not appropriate for complex data relationships. 

Applications: Caching systems, session management, real-time analytics.

### Graph Databases:

Human representation and storage of data relationships between data points is their core design.
Pros:
Efficient at exploring relationships among entities.
Natural match for applications with complex interconnections.
Schema flexibility enables evolving data models.
Cons:
They may be less performant at simple data retrieval compared to other types of databases.
Maintaining consistency and integrity in the highly connected datasets is quite a task.

Applications: Social networks, recommendation engines, fraud detection.

### Vector Databases:

Vectors or embeddings having high dimensions can be stored and queried with these databases that are optimized for this purpose.
Pros:
Efficient similarity searches and nearest neighbor queries.
Well-suited for applications involving machine learning and AI.
Scalable to large-scale datasets
Cons:
The traditional database operations such as joins and complex transactions are not supported to a great extent
It involves high complexity in managing vector indexes.

Applications: Content-based recommendation systems, image and text similarity search, anomaly detection.

### Time-series Databases:

Time-series Databases are designed to handle time-stamped data points. 
Advantages:
It is the best option for rapid ingestion and retrieval of time-series data.
Compression techniques make it possible to store large volumes of data effectively.
Time-based operations such as aggregations and windowing functions are supported.
Disadvantages:
Outside the domain of time-series, there is very limited flexibility. 
If not properly optimized, query performance can degrade with increasing data volume. 

Applications: IoT sensor data storage, monitoring systems, financial trading platforms.

### Column-oriented Databases:

Stores data in columns rather than rows, optimizing for analytical queries. 
Advantages:
Great performance in terms of analytical queries that involve aggregates and filtering. 
Data can be compressed effectively to reduce storage requirements. 
These databases are scalable enough to handle large datasets. 
Disadvantages:
They do not work well with transactional workloads with frequent updates or inserts.  
Real-time analytics is less supported compared to other types.

Applications: Data warehousing, business intelligence, reporting systems.