---
Title: DBS101 Flipped Class 8
categories: [DBS101, Flipped_Class8]
tags: [DBS101]
---

## Indexing of Spatial and Temporal Data
### Spatial Indexing:

This is a technique where we use geometry to save and recover spatial data thus using the physical properties(like points, lines, and polygons). 
 
Types of Spatial Indexing:
 
R-Tree:R-Tree is a data structure which is used for indexing spatial data. It orders the spatial objects arranged in a nested hierarchy of get bounded cuboids. Beneficial for spatial queries types including range search and nearest neighbour search. 
 
Quadtree:Quadtree is a tree data structure in which each internal node has exactly four children. Recursively into 4 quadrants partition the two-dimensional space. Suitable for spatial indexing of points and objects. 
 
Grid Indexing:The grid indexing technique divides the spatial domain into a set of equal-sized cells. Every cell of the matrix consists of a catalog of spatial objects that are overlapping the area. It is straight and you can implement it quickly that may lead to the inefficiency of which the cells are vacant or the inputs are not evenly distributed. 

### Temporal Indexing:

Temporal B-Tree:Temporal B-Tree is an extension of traditional B-Tree data structure and it happens in time. It enables data to be time stamped and categorized very fast. Adequate enough to smooth over the temporal queries such as time range query and time intervals in its wake. 
 
Temporal Hashing:By temporal hashing, the temporal attributes are hashed using a specific hash function that produces a hash code, a mapping operation between temporal attributes and their corresponding hash value is performed. It provides the fast extraction of the temporal data by the direct access to the hash bucket, which is the corresponding one. Endowed with characteristics suitable for handling the queries about timestamps points and limits. 

## Bitmap Indices

A bitmap index is a type of index that provide fast seeking by the presence or the absence of attribute values during the retrieval of records. For bitmap indexing each discretized values of each attribute is assigned a bit in a bitmap, which indicates whether or not a particular value exists in a given record. The indices are also very effective for low-cardinality attributes that consume less space than other indexing techniques. Bit map indexes facilitate quick query performance for such operations as AND/OR/NOT, as these actions can be completed through bitwise operations that run fast. Because of that, they are not appropriate for large numbers of attributes, exhausting memory and eventually turning quite inefficient. Bitmap indices are often employed in data warehouses for OLAP systems and are ideal for optimizing queries which involve multiple attribute conditions. 

## Buffer Tree

The B-Tree, or buffer tree, is a self-balancing tree data structure; which can be applied to deal with non-ordinary data (i. e.  spatial, temporal data) accurately, speedily and with minimum memory needs. When it comes to indexing, Buffer Tree divides the data into a hierarchical structure with nodes which contain the keys in the sorted order. Each node can accommodate both keys and children with variable numbers facilitating you to deal lots of the data. Buffer Tree lets you speed-up search, insert, deletion, and sequential access into huge datasets that especially work for case where the work needs to be done on disk. This is why, it is the best option for indexing large amounts of spatial and temporal data in databases and file systems where speed and efficiency of accessing data are crucial. 