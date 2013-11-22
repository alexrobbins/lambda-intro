# Pain Points in Big Data
## &nbsp;&nbsp;&nbsp;&nbsp;And
# Lambda Architecture

&nbsp;

DFW-Clojure Meetup

---
# Pain Points in Big Data

---
## Pain Point:
# Data Persistence

---
## Data Persistence
Disk failure

---
## Data Persistence
Human failure

---
## Data Persistence
Overwritten data (design failure)

---
# Fixing Persistence
- Append-only data storage
- Never delete input
- Never overwrite input
- Redundant storage

---
## Pain Point:
# Data Size

---
## Data Size
Too much data to fit on one drive

---
## Data Size
Not helped by append-only policies

---
## Data Size
Sharding

---
## Data Size
Inconsistency after sharding/replication

---
# Fixing Data Size
- Use a distributed file system
- HDFS
- S3

---
## Pain Point:
# Queries

---
## Queries
Data lives in many places

---
## Queries
Data is too big to process in real time

---
## Queries
Data keeps coming in

---
# Fixing Queries
# &nbsp;

---
# Fixing Queries
# ???

---
# Options:

---
# Give Up?
## Go back to smaller data

---
# Press Forward
## Gird your loins

---
# Lambda Architecture
## The Solution to Our Problems

&nbsp;

Caveat: This is how I understand the Lambda Architecture from Nathan Marz's excellent, half-completed book *Big Data*.

---
# **Batch Layer**
# Serving Layer
# Speed Layer
# Data Ingestion
# Answer Queries

---
# Batch Layer
- Data format
- Data storage
- Data processing

---
# Data Format
- Thrift
- Json
- edn

---
# Data Storage
- HDFS
- S3
- Append only!
- Redundant

---
# Data Processing
- Hadoop
- Cascalog
- Dump output as something the serving layer understands.
- Make functions idempotent on input, so that receiving the same input twice doesn't break things.

---
# Batch Layer
# **Serving Layer**
# Speed Layer
# Data Ingestion
# Answer Queries

---
# Serving Layer
- Read-only database
- Answer queries for the range from the beginning of time until the last batch job
- elephantdb

---
# Batch Layer
# Serving Layer
# **Speed Layer**
# Data Ingestion
# Answer Queries

---
# Speed Layer
- Accumulate temporary state
- Answer queries for the time since the last batch job
- Drop state once a batch job makes it redundant.
- If corrupt, nuke it, slightly degrading service for a short while.

---
# Batch Layer
# Serving Layer
# Speed Layer
# **Data Ingestion**
# Answer Queries

---
# Data Ingestion
- Accept data from $SOURCE, send it to both the Speed and the Batch Layers.
- Storm could handle this, splitting the input stream to both Speed and Batch.

---
# Batch Layer
# Serving Layer
# Speed Layer
# Data Ingestion
# **Answer Queries**

---
# Answer Queries
- To answer a query you need to merge the responses from the Speed Layer and the Batch Layer.
- Make sure you aren't double counting data that is somehow in both places.
- Storm provides a DRPC server that makes this easier.

---
# Batch Layer
# Serving Layer
# Speed Layer
# Data Ingestion
# Answer Queries

---
# The Plan

- Work through the different parts of the Lambda Architecture
- Learn the different technologies at each layer
- Develop a sample application
- ???
- Profit

---
# Pain Points in Big Data
## &nbsp;&nbsp;&nbsp;&nbsp;And
# Lambda Architecture

- alexander.j.robbins@gmail.com
- Clifton King cliftonk@gmail.com

- https://github.com/alexrobbins/lambda-intro
- http://www.databasetube.com/database/big-data-lambda-architecture/
