# Graph Ranking Algorithms in PySpark

## Overview

Distributed implementation of PageRank and HITS algorithms using PySpark on a randomly generated graph (1,000 nodes, 8,192 edges).

## Algorithms Implemented

### PageRank
- Iterative power method with teleportation (β=0.8, 40 iterations)
- Random jump probability to ensure convergence
- **Results**: Top 5 nodes [263, 537, 965, 243, 187]

### HITS (Hyperlink-Induced Topic Search)
- Mutual reinforcement of authority and hub scores
- Vector normalization at each iteration to prevent score explosion
- Comparative ranking with PageRank

### Analysis
- Algorithm differences: authority vs. popularity measures
- Use case implications for different graph structures

## Technical Stack

- **Framework**: PySpark RDDs
- **Optimization**: RDD caching, lineage management, join optimization
- **Data Structure**: Sparse matrix (edge list representation)

## Key Challenges & Solutions

**RDD Lineage Explosion**  
40 iterations created 40-level deep dependencies → Used `.cache()` and `.unpersist()` to checkpoint lineage

**Join Performance**  
Repeated matrix joins were slow → Cached transition matrix outside iteration loop

## Learning Outcomes

- Distributed graph processing in MapReduce paradigm
- Sparse matrix operations at scale
- Iterative algorithm optimization in Spark
- Performance trade-offs: recomputation vs. memory

## Potential Extensions

- Personalized PageRank with custom teleportation
- Topic-sensitive HITS for query-dependent ranking
- Scalability benchmarking (10K-100K nodes)

---

**Chien-Wei WENG**  
MSc Data Sciences and Business Analytics  
CentraleSupélec × ESSEC Business School

*Academic Project | Scalable Data Algorithms (Fall 2025)*  
*Instructor: Prof. Mohamed Ndaoud (ESSEC Business School)*
**Note**: Academic materials and assignment data are not included in this repository.
