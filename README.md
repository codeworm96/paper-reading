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

They make their modification on [Shore Storage Manager](http:// www.cs.wisc.edu/shore/).
The workload they use for evaluation is (modified) TPC-C.
