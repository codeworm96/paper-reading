# Paper Reading

## [The Humble Programmer, Edsger W. Dijkstra](https://www.cs.utexas.edu/~EWD/transcriptions/EWD03xx/EWD340.html)

> One moral of the above story is, of course, that we must be very careful when we give advice to younger people; sometimes they follow it!

// TODO finish it

## [On the cruelty of really teaching computing science, EWD 1036](https://www.cs.utexas.edu/~EWD/ewd10xx/EWD1036.PDF)

// TODO

## WiscKey: Separating Keys from Values in SSD-Conscious Storage

Main idea: in LSM tree, separates keys and values to lower read & write
amplification

After separation, range queries require random reads -> utilize SSD parallel
random read

## The Bw-Tree: A B-tree for New Hardware Platforms

// TODO

## Bigtable: A Distributed Storage System for Structured Data

Depends on: Chubby


## The Chubby Lock Service for Loosely-Coupled Distributed Systems

// TODO

## OLTP Through the Looking Glass, and What We Found There

OLTP database systems design can date back to 1970's / 1980's.
This paper evaluates instruction-level breakdown of components in an OLTP database system,
which can be used as a guidance for making changes under situations now.

They make their modification on [Shore Storage Manager](http://www.cs.wisc.edu/shore/).
The workload they use for evaluation is (modified) TPC-C.

## Main Memory Database Systems: An Overview

A review for in-memory database systems, focusing on where in-memory databases should be different from
disk-oriented databases and why.

Covers in-memory database systems from pencil-and-paper designs (MM-DBMS, MARS, HALO) to
prototypes (OBE, TPK, System M) to commercial systems (Fast Path) at that time (1992).

## A Critique of ANSI SQL Isolation Levels

// TODO

## Staring into the Abyss: An Evaluation of Concurrency Control with One Thousand Cores

It is expected that in the future CPU will have many cores in a single chip.
This paper evaluates seven concurrency control schemes (deadlock detection, no wait,
wait die, timestamp, MVCC, OCC, H-store) and finds that neither of them scales well
on a 1024-core CPU for different reasons. It concludes that for many-core CPU in the
future, new concurrency control schemes
are needed and cooperation between software and hardware design may be needed.
They build their own main memory database system from scratch to reduce
the effect of specific legacy implementation and use Graphite to simulate
the many-core CPU.
The workloads used in this paper is based on YCSB and TPC-C.

## An Empirical Evaluation of In-Memory Multi-Version Concurrency Control

Currently, multi-version concurrency control is a popular concurrency control scheme in DBMSs,
but it has many design choices. This paper made the evaluation of MVCC's performance under
different design choices, including concurrency control protocol, version storage,
garbage collection, and index management. This paper highlights the trade-offs of
different design choices and their bottlenecks.
They implemented different MVCC approaches to be evaluated in the Peloton DBMS.
The workloads used for evaluation are modified YCSB and TPC-C.

## Fast Serializable Multi-Version Concurrency Control for Main-Memory Database Systems

MVCC is widely used in many DBMSs, but most systems only implement snapshot isolation, because
adding serializability guarantee could be expensive. In this paper, the authors propose an MVCC
implementation that has little overhead when adding serializability guarantee by precision
locking and checking writes of recently committed transactions. They also use VersionedPosition
column to provide high scan performance.
They implemented their MVCC in the HyPer main-memory database system.
The workloads used for evaluation include the SIBENCH benchmark, TPC-C,
The Telecommunication Application Transaction Processing (TATP) benchmark and TPC-H.

## Hybrid Garbage Collection for Multi-Version Concurrency Control in SAP HANA

In mixed OLTP and OLAP workloads, OLTP workloads will generate many versions, but long-running
OLAP query will block garbage collection. This paper contributes ideas to handle this problem,
including interval GC (using visible intervals to check for visibility), group GC (GC in the
unit of commit groups), table GC (using the information that some tables are irrelevant to
some transactions). Finally, the authors combined these ideas and created HybridGC.
Their HybridGC is implemented in SAP HANA in-memory database.
The workload used in the evaluation is modified TPC-C benchmark with additional
long-running queries.