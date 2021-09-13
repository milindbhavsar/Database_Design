**DB Sharding**

https://www.youtube.com/watch?v=5faMjKuB9bc

Consistency and availabilty of DB are key NFR attributes.

Partioning

  - Horizontal partitioning based on the data attributes stored in DB.

  - Vertical partitioning uses columns to partition data.

Use case - What should I shard my data on ?

  - Shards on user id 
    - Instagram - It is done by consistent hashing on userID
              - Gateway reads from the SS that which userfeed service box this request to be sent and f/w this requests.
              
  - Shards on location
    - TINDER - shards data based on the user's location 
    - UBER shard based on location 
      - Region Servers - Are part of Consistent hashing RING , handles the requests specific to location ranges when asked by SUPPLY service.
  
  - Shards on GroupID
    - Whatsapp - shards on GroupId for getting group information from Group MS.
  
  - Shards on Filenames
    - Netflix - Uses Consistent Hashing based on hash(filenames) to distribute load in Open Connect Cluster

Problems

  #1 Joins across shards

  #2 Fixed no. of shards - cannot have more or less shards

  #3 #2 can be solved by Hierachical sharding

  #4 Shard failure - Use master / Slave architecture for Shards

Create an Index on the shards. e.g. index all the people in NY ,age > 50 index on age for above e.g.

**DB Locks** - https://www.youtube.com/watch?v=R-iX1r_7UY0

  **Pessimistic Lock** - acquire lock and release lock 
  
  E.g. Locking a row and not allowed others to update 
  
  - Holds resource during concurrency, will not be liked by distributed systems .
  - Suitable when More conflicts. 
  - Make sure deadlocks do not occur and assure TIMEOUTS for locks. 
  - Makes persistent connections with DB.

  **Optimistic Lock** - Locking is a strategy where - 
  
  E.g. Editor like WIKIPEDIA for concurrent updates 
  
  - Read a record 
  - Take a note of version number or timestamps or checksums / hashes 
  - And check that the version hasn't changes before you write the record back.
  - Holds resource during concurrency, is liked by distributed systems 
  - Suitable when few conflicts. 
  - Works well with versioning, Makes asynchronous connections and need not require persistent connections.

  Unlike Pessimistic lock we are not locking the data from the time read the data to the time we update it back !!

**Database as Scale** - How databases scale writes: The power of the log

https://www.youtube.com/watch?v=_5vrfuwhvlQ
