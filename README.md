On what basis u will choose a DB ?
  1. Structure 
  2. Query
  3. Scale

Types -   
  1. Cache - key/value  - Redis , Memcache , Hazelcast
  2. FileStore - S3 with CDN
		Use case -  e.g. Storing Image , Videos , Blobs for Online shopping like Amazon , Instagram.
  
  3. Text Search - Elastic Search , Solr (Primary data source should be different as they are not DB but search engine )
  
     Use case - fuzzy search 		

										- DB gives guaranteed no data loss but search engines do not.
										- Search engine comes gives redundancy and availiabilty but does not guarantee data loss so they never become primary .
  
		Uber - fuzzy search 
		Netflix search on movie , genre , artist

  4. Metrics - 	 OpenTSDB , Influx DB
  
     Use case - Applications metrics 		
     Time Series Data bases - 
			- tHese kind of data bases does not require random updates but sequential updates
							
			- Extension of regular databases with few reduced functionality

			- append write
            
      - no random read but a bulk read in a range
            
  5. Analytics on TXN , orders, geo ,revenues  - Hadoop

	 - Dump all data
	 - non transactional
	 - offline reporting
	 
Flowchart - When to choose relational and non relational DB

		Structural data -----YES-----> Need ACID-------YES-------> RE                             | E.g. Amazon Inventory & Payment 
		|
		|
		|
		NO
		|
    |
		NOSQL
		|
		|---> Lot of Data Types & Attributes|
		|---> Variety Queries               |------------> Document --------> MongoDB , Couchbase | E.g. Amazon Catalogue - lot of product information & info about its attributes 
    |
    |
    |
    |
		|---> Ever Increasing Data          | 
		|---> Finite Queries                |------------> Columnar--------> Cassandra , Hbase    | E.g. Uber Driver location information
    
    Ecommerce platforms using hybrid approach - when querying for attributes they can query data from a document store 
                                              - For live system they can store data in Relational and move to Columnar when job is done for analytics 
