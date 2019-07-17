# Building blocks of Hadoop - HDFS, MapReduce and Yarn

## Need for distributes computing
- 
### Big data system requirement
- Store 
- Process 
- Scale

## Two ways to build system
- Monolothic
- Distributed

Distributed system 
- Nodes together to form a cluster
- Doubling the nodes in the cluster increases the performance >2x , storage 2x

Single co-ordinating software for nodes
- partition data
- co-ordinate computing tasks
- handle fault tolerance and recovery
- allocate capacity to process

Distributed computing makes for a lot of complexity as it has to takecare of the above things

This is where Hadoop comes into picture
- Software to co-ordinate 

Objectives 
- Store millions of records on multiple machines
- Run processes on all these machines to crunch data

HDFS - To solve distributed storage
MapReduce - Framework to Define a data processing task
YARN- Framework to run data processing task

popular tech on hadoop
- Hive - Sql like query to access data on hadoop 
- Hbase - A database management system on hadoop.
low latency operations on key value pair
- Pig - convert unstructured data to structured data
scripting language to manipulate data into a structured format
- Oozie - a work flow management system
A tool to schedule workflows on all hadoop system.
- Sqoop/Flume - put and get data from hadoop
- Spark - perform tasks in a functional way
A distributed computing engine used along with hadoop
Interactive shell to quickly process datasets
built in libraries for machine learning , stream processing, graph processing etc.

---------------------------------------

Installing Hadoop
- 3 ways to run hadoop
    - <i>standalone mode</i> - single node hadoop
    mainly used when you want to checng your mapreduce logics. Here yarn is not used as ther is no distribution happening w.r.t resource
    - <i>Pseudo Distribution mode</i>- Runs on single node but 2 jvm processes to simulate 2 nodes
    HdFS for storage.
    Yarn for managing tasks.
    Used as a fully-fledged test env
    - <i>Fully distributed</i> - production mode . Runs on a cluster of machines. 


    




