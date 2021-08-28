**DB Sharding**

https://www.youtube.com/watch?v=5faMjKuB9bc

Consistency and availabilty of DB are key NFR attributes
Horizontal partitioning based on the data attributes stored in DB
Vertical partiotioning uses columns to partiton data
Use case - What should I shard my data on ?

shard on user id
Applications like TINDER shard based on location
Problems

#1 Joins across shards

#2 Fixed no. of shards - cannot have more or less shards

#3 #2 can be solved by Hierachical sharding

#4 Shard failure - Use master / Slave architecture for Shards

Create an Index on the shards. e.g. index all the people in NY ,age > 50 index on age for above e.g.

**DB Locks** - https://www.youtube.com/watch?v=R-iX1r_7UY0

Pessimistic Lock - acquire lock and release lock E.g. Locking a row and not allowed others to update - holds resource during concurrency, will not be liked distributed systems - suitable when More conflicts - Make sure deadlocks do not occur and assure TIMEOUTS for locks - Makes persistent connections with DB

Optimistic Lock - Locking is a strategy where . E.g. Editor like WIKIPEDIA for concurrent updates - read a record - take a note of version number or timestamps or checksums / hashes - and check that the version hasn't changes before you write the record back - holds resource during concurrency, is liked distributed systems - suitable when Few conflicts - Works with versioning ,Makes asynchronous connections and need not require persistent connections

Unlike Pessimistic lock we are not locking the data from the time read the data to the time we update it back !!

**Database as Scale** - How databases scale writes: The power of the log

https://www.youtube.com/watch?v=_5vrfuwhvlQ
