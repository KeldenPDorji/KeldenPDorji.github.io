---
Title: DBS101 Flipped Class 11
categories: [DBS101, Flipped_Class11]
tags: [DBS101]
---

## Concurrency Control 
Definition: Concurrency is the control of the database system that allows many transactions to work at the same time without conflict and still retain the database’s coherence and accuracy. 

Objectives: 

Data Consistency: It makes sure that transactions are processed in such a way that the database state will be maintained. 
Isolation: The intermediary states of a transaction are thus hidden from other transactions. 
Serializability: It means to ensure that when transactions are executed simultaneously their effect is same as if all the transactions where executed one after the other. 

Types of Concurrency Control: 

### Optimistic Concurrency Control: 
Beliefs that conflicts are not very frequent and lets transactions to go through without restrictions only verifying for conflict at the end. 

### Pessimistic Concurrency Control: 
Averts problem of contention by giving a lock to the resource before it is accessed. 

## Two-Phase Locking (2PL) 
Definition: Two-phase locking is a concurrency control technique that makes sure that a transaction constitutes a serial schedule by dividing the execution of the transaction into two phases only, which are the growing phase and shrinking phase. 

Phases: 

Growing Phase: It can acquire locks, but it cannot unlock any of the records. 
Shrinking Phase: It can only commit the transaction or rollback it whereas it cannot make any new locks for the transaction. 

Types of 2PL: 

### Growing Phase: 
Retains all locks until the end of a transaction’s execution or the point at which the transaction has to rollback, so that all information can be recovered. 

### Rigorous Two-Phase Locking: 
A strong version where all locks are held until the transaction is committed, to achieve strict two phase locking. 
Advantages: 

Guarantees serializability. 
Ensures data consistency. 
Disadvantages: 

Can lead to deadlocks. 
May cause a lower degree of concurrency because of the lock and key used. 

## Timestamp Ordering Concurrency Control 
Definition: Timestamp ordering is a concurrency control technique for ordering transactions and is not based on locks; however, it guaranteed serializability. 

### Key Concepts: 

Timestamp: Every transaction is allocated with a specific time stamp to its beginning of the transaction. 
Read and Write Timestamps: Each data item has read and write timestamps to keep the time stamp a record of the last read and the last write made on this particular item. 
Rules: 

Read Rule: A transaction can read a data item if its timestamp is greater than the item’s write timestamp. 
Write Rule: A transaction is allowed to write a data item if its timestamp is more than both the read and write timestamp of the data item. 
Advantages: 

Avoids deadlocks. 
Cuts a clear sequence of the transaction completion. 
Disadvantages: 

The main adverse effects can be seen in the aspect of higher abort rates. 
Possibly needs more storage for timestamp information. 

## Locks and Latches 
### Locks: 

Definition: Access control systems that regulate the facility to the databases to enhance data authenticity and accuracy. 
Types: 
Shared Lock (S): DML: this enables one or many transactions to read a data item but not to write. 
Exclusive Lock (X): Enables a single transaction to simultaneously access a data item in both, the reading and writing mode. 
Granularity: Can be used on row level, on page level or with the entire table. 

### Latches: 

Definition: Locks which were applied to provide short-term mutual exclusion for the in-memory data structures. 
Difference from Locks: Latches are usually employed for a short while, in memory only but locks are employed for a larger number of database transactions. 
Usage Scenarios: 

Locks: Applied in Transactional systems to ensure that data is in the same state before beginning of the transactions and after end of transactions. 
Latches: Employed in database environments to shield the inside data structures for instance, buffer pools. 
