- “column” exist in both rational and noSQL but have different meanings.
 
-  Cassandra is based on Dynamo or Bigtable source papers ??

- 

## bottom-up approch for understanding cassandra's data model

* column = name/value pair ( column key / column value )
* row = set of columns

* column name can be : string , uuid , integer , long

*  we don’t need to store a value for every column every time we store a new entity
    * in relational world we need a value for every column at least we put a null. ( which would waste space )

* timestamp Columns in Cassandra
    * last time the column was updated
    * This is not an automatic metadata property
    * You cannot query by the timestamp
    * Rows do not have timestamps ( only columns )

* super column:

* super column family 

## Clusters:

* Cassandra database is specifically designed to be distributed over several machines operating together that appear as a single instance to the end user

* the outermost structure in Cassandra is the cluster ( ring )

* A node holds a replica for different ranges of data

* peer-to-peer protocol allows the data to replicate across nodes

## keyspaces :

* keyspace is corresponding closely to a relational database

* A column family is roughly analagous to a table in the relational model

* attributes for a keyspace :
    1. replication factor : number of replication for each data
    2. column families : equivalent to tables in relational world
    3. replica placement strategy:
        * SimpleStrategy
        * OldNetworkTopologyStrategy
        * NetworkTopologyStrategy

* the only time you would want to split your application into multiple keyspaces is if you wanted a different replication factor or replica placement strategy for some of the column families.
    * For example, if you have some data that is of lower priority, you could put it in its own keyspace with a lower replication factor


## Column families

* A column family is a container for an ordered collection of rows, each of which is itself an ordered collection of columns

* column family, which is a container for rows that have similar, but not identical, column sets

* why table and column family are diffrent
      1. Cassandra is considered schema-free because although the column families are defined, the columns are not
      2. Column family have two attributes: a name and a comparator
      3. column families are each stored in separate files | all tables are stored in single file.
      4. tables can hold only row | column family can be super columns 
* 


