**No SQL DB**
https://www.youtube.com/watch?v=xQnIN9bW0og

NoSQl DB works on the idea of distributed consensus ,one of the way acheive this is Quorum

	Advantages

	1. Insertions and retrievals are easier
	 - Insertions and retrievals required whole blobs 
	 - All data is contained together so expensive joins are not required
	
	2. Json Schema is very flexible and changeable
	 - doesn't care about addition of new attributes or emty values doesn't requires locks on tables and its rows for coulmn addition
	
	3. Build for scale
	
	4. Build for aggregation
		e.g. average age, total salary
		
	Disadvantages
	
	1. Not build for updates 
		- ACID is not guaranteed 
		- Issue with data consistency 
		- cannot be used for financial data
	
	2. Reads times are slower  
		- Not read optimized as cannot work on JSON's attribute while SQL can work on columns
	
	3. Relations are not implicit
	
	4. Joins are hard
	
	When do we use NoSQL ?
	
	1. Data is a block , wants to keep all together 
	
	2. Few updates and write optimized
	
	3. Inherent redundancy or aggregations
	
	Cassandra
		- Stores all key value pairs (data) in a in-memory in a log in a sequential fashion---------> dumped into SSTable (Sorted String Table,key is going to be sorted)
		- SSTable is a persistent storage and immutable
		- every new update on data is stored in new SSTable will have multiple records for the same Sorted key which leads to lot of data storage,
			use the timestamp to get latest data
		- to avoid lot of data storage ,Cassandra and Elastic Search comes with a concept like Data compaction
		- Data Compaction 
			- fast to be flushed to disk ,use a batch process to compact 
			- take different sorted tables and merge them For e.g. merging two sorted arrays for size n,m
			- Complexity - O(n) , Space - O(Min(m*n))
	Features
	
	1. Load Balancing
	
	2. Data Redundancy 	- Speed in reading 
	   Data Replication     - Data guarantee
