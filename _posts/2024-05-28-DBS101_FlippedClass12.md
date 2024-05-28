---
Title: DBS101 Flipped Class 12
categories: [DBS101, Flipped_Class12]
tags: [DBS101]
---

# ARIES (Algorithm for Recovery and Isolation Exploiting Semantics)
ARIES is an algorithm choice that is implemented in DBMS for carrying out the recovery of lost data and using the techniques of multiple failure versions for recovery as well as ensuring that the consistency of data is maintained at all times. It was invented by C. Mohan and his group at IBM in the early 1990’s Periodically issued local checkpoints StoreCheckpoint, LastLocalCheckpoint, GCcounter, and GCmarks are new tables introduced in this formulation in addition to the existing ones. Here's an overview of its key concepts:Here's an overview of its key concepts:

## Key Concepts
### Write-Ahead Logging (WAL):

There is always record of any change made to the database before it is effected.
This makes it possible to have the database brought to a particular state in case it is in a failed state according to the log.

### Physiological Logging:

It involves both the physical and the logical logging in order to enhance the optimal results as well as the recovery options.
Physical logging maintains manifestation changes at the page level while the logical logging maintain changes at some other level of abstraction such as the row level.

### Three Phases of Recovery:

Analysis Phase: It looks through the log for which transactions were current at the time of the crash and then determines the status of all the database pages.

Redo Phase: Holds all the changes captured in the log since the last checkpoint and makes all committed transactions’ changes are reflected in the database.

Undo Phase: Undoes the work of a transaction making sure that the database does not contain any half-way processed data..

### Checkpointing:

From time to time a checkpoint is made and this displays the state of the database together with that of the log at a given time.
These are used precisely to in the tasks of reduction of the amount of log which has to be processed during recovery.

### Log Sequence Number (LSN):

Every log record has an LSN that is unique.
Completing the conversion of a TxL, LSNs are employed to mark the order and to define the place to start with the recovery.

### Page LSN and Dirty Page Table:

Every page of the database has two pieces of information namely a Page LSN which will be the LSN of the last log record to have modified the database page in question.
The concept of the Dirty Page Table (DPT) is maintained at the OS kernel level and records those page that have been written, but not flushed to disk yet.

## Steps in ARIES Recovery
### Crash Occurs: 
Database system experience a failure.

### Analysis Phase:
Review the checkpoint log to identify the place to begin from.
Then, continue to the next log entry in the clockwise direction to check for active transactions and update the DPT.

### Redo Phase:
Beginning from the initial entry of the log that was identified in the Analysis Phase.
All the committed data is reapplied, so redo all operations.

### Undo Phase:
Determine uncommitted transactions by looking at the Transaction Table.
It is advisable to compare the levels of uncommitted transactions in the above-mentioned tables and assess the differences in order to identify if there were any spikes during the week.
At the end, the effects of the above transactions can be reversed by applying compensating log records (CLR).

## Database Logging
Database logging is important in making it possible to make durable and consistent Database System. It entails writing activities made on the database to a log file that can help in restoring the consistency of the database in the event of a failure.

## Types of Logs
### Transactional Log:

Accumulates all the changes that are made by transactions.
Businesses, for example, use it in transactions and contain information similar to the transaction ID, operation type, modified data before and after the change, and log sequence number (LSN).

### Redo Log:

Utilized in redo part of the recovery processes.
Makes certain that all changes, for which a project is committed, are reflected in the database.

### Undo Log:

Will be incorporated during the undo phase of recovering.
Responsible for making sure that any changes performed by a transaction that has not executed a commit statement are undone.

## Logging Techniques
### Physical Logging:

Records the new values that are in fact attempted to be modified.
Example: Old values and new values of a particular row or new page that has just been added to the website.

### Logical Logging:

Logs higher-level operations.
Example: A command in the form of an SQL statement like the INSERT or the UPDATE.

### Physiological Logging:

Integrates concept of physical and logical log review.
The types of information vary from the purely physical, such as recording changes at the page level, to the logical.

## Log Management

### Checkpointing:

By taking periodic backups of the database state, the time taken to recover it will be lowered.
Has data about transactions progressing and the position in the log where recovery must begin.

### Archiving Logs:

Logs are grouped into old log files, again to free space, while the database can be restored to any point in time.
Useful for point-in-time recovery.

### Log Buffering:

The first is the case of logs where the information is initially recorded in a buffer in memory for efficiency.
Flushing occurs periodically, as a way of persisting changes to disk.

If you understand ARIES and database logging, then you will be in a position to make sure that in the event of failures in your database systems, it is possible to recover really quickly and do all that is required to ensure the data remains correct and consistent.