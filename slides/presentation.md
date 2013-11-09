# Pain Points in Big Data
## And an Introduction to the Lambda Architecture

- Alex Robbins
- Chris Risenhoover
- Clifton King

---

# Pain Points in Big Data

---

# Pain Points in Data

<!-- Pain points aren't big data specifc -->

---

Data issues - solved by append-only db schemes
- Corrupted data
- Lost data (Where did they live before their current location)
Data size breaking processes - solved by hadoop batch processing
- append only databases cause big data
- sharding
- inconsistent copies
Real-time queries on data (easy in db, hard in hadoop)

Lambda Architecture
explain what it is - for each part, explain the pain points it addreses
batch layer
- data format
-- thrift
-- edn/json?
- data storage
-- hdfs
-- append only
- cascalog/hadoop?
serving layer
- s3/file system
- riak/cassandra/any kv store
- elephantdb
speed layer
- storm
- relational db?
ingestion
- write data into speed layer and into batch layer
- storm?

---

# Big Pain
## Pain Points in Big Data

- Alex Robbins - alexander.j.robbins@gmail.com
- Chris Risenhoover - chrisrisenhoover@gmail.com
- Clifton King - cliftonk@gmail.com

- https://github.com/alexrobbins/lambda-intro
