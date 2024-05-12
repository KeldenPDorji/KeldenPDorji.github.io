---
Title: DBS101 Flipped Class 7
categories: [DBS101, Flipped_Class7]
tags: [DBS101]
---

## Topic: Relational Database Storage and Buffer Management

### Disk Storage Management:

The allocation as well as the deallocation of disk blocks should be well-performed maneuvers to avoid the database consuming unnecessary storage space in an inappropriate way, reduce the fragmentation, and improve the performance of its database.

Continuity of disk block transfer operations sets the importance of a file system as it ensures credible and trustworthy data.

A series of consistent units of data, mainly for reading and writing, are streamline operations.

### RAID Configuration:

RAID level selection is the main factor in finding an optimal balance between performance, duplicity and cost.

These are the plus sides of RAID striping and parity: availability, fault tolerance, and increased performance during reading and writing.

It is mandatory to implement proper procedures to be able to process scenarios such as disk failure and separate specific logical volumes to preserve the data integrity while simultaneously minimizing or reducing the time for which the service would be down.

### Buffer Pool Management:

An efficient in-memory buffer pool should be introduced which will cache the data that is required frequently and may not fit into the memory at once, thus the disk I/Os are reduced for a better performance in general. Deciding on an appropriate buffer size that complies with a balance of utilization of memory, just as performance, is a must. Buffer Pool Replacement strategies, including LRU (Recently Used), or Clock are utilised in such a way to efficiently use memory by evicting the least useful data. The good buffer pool management in reading and writing operations is crucial for keeping data consistency and preventing data corruption. Summarizing all the major points discussed in regard to buffer pool, they are important for the data integrity maintenance in CAS.

### Transaction Management:

This is even more important because the system should be ACID-compliant (Atomicity, Consistency, Isolation, Durability) and that it cannot crash if two different time zones make requests at the same time.

The transaction log files, which together with the recovery log, are the most important log files as they are responsible for failure recovery after crashes/events and restoring the operation into the condition of the highest consistency and integrity after failures

Woven with locks or sequences of controlling concurrency, provided in the form of the basic principle that is the measure of the provision of non-disturbance of the building system data from various users and their damages created by third parties.

### Index Management:

The resolution of this problem relies upon the applications of two logical hashings of binary B-Tree or Hash index. (The Hash index is the one that is most popularly used as an index). This in addition means that with this option just useful processes will be chosen. And therefore it is just easy to perform other processes.

In addition, the function of the indices takes place during query using as well as during run time. These indices are constructed and kept up to date. Processing is done simultaneously on the entire group of data and is triggered when the query is run.

Manage both time and date sync with the functionality similar to a typical data management approach. Nevertheless, the problem of data continuity and consistency in the multiuser environment is permanently solved.

### Query Processing:

In my opinion, the query parser and the optimizer that are being constructed are very vital components, which also play a role of boosters for the whole system to work properly. But the optimizer that is written so that it is resource-efficient and is able to get maximal performance as possible the best.

It is a smart technology that plans the legal action whenever the users are looking for and analyzing the data (for instance, a table or an index) for a search and manipulation operationally.

The Buffer Pool system conjoins these units to execute the coding which is associated with the output of Non-Uniform and Consistent logical data that is accessed and manipulated either as an input or output.

### Concurrency Control:

It is recommended to care to rear the order not to exceed the data number requests, as this may lead to the wrong information loss in a fast flow of the requests entries. The deadlock might be reviewed, the trick and the solutions to it should be handled, that is to avoid reworking of the system and the resources shortage. Such a can be carried out by a program of various isolation levels that cope with the problems of read committed as well as repeatable read among others that take care of concurrent data processing. With a method of ensuring that the data stay consistent even in multiple users' computer networks.

### Recovery and Backup:

The most vital features of any transactional system are checkpoint, and write-ahead technologies which solve consistency and recovery problems that would be there if these were not present in the system to deal with system crashes or failures.

Absolutely, to approach such an option, first of all, data protection and a disaster recovery plan should come on first priority.

The threat of losing entire files in the system in the middle of working process should definitely keep data backup and recovery activities busy during the system management and at least to some extent get some bits of work already done.

### Performance Monitoring and Tuning:

The monitoring approach not only should know the tricks of the trade to avoid the failure with the updated collection metrics, but also the potential of others.

The perfection of analytic processes involves the creation of an arrest list, with an attractive look, readiness of index concatenation and good searchability. System adequacy is one of the main factors of the system health. Nevertheless, this main requirement is opposed by the performance and resource which don’t match with these requirements.
