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


- Processes associated with HDFS 
    > Namenode, Datanode, SecondaryNameNode
- to check type <i>jps</i> in the command promt
- Processes associated with YARN
    > Nodemanager , ResourceManager

HDFS - Hadoop distributed file system
- Highly fault tolerant, hardware failure norm
- Suited for batch processing- data access has high throughput rather than low latency
- Supports very large data set
- NameNode is master node and slave nodes are termed as Datanode

NameNode
- Arbitrator of data
- any request is directed by namenode to respective datanode

DataNode
- stores the actual data

Storing Files in Hadoop
- Data is breaken into blocks
    - each block are of same size
    - Optimum size of block is 128MB
    - increase in block size reduces parallelism
    - decrease increases the overhead of block 
    - NameNode contains the info/tableOfContent of blocks distributd across the DataNodes

HDFS commands
> ```hdfs dfs``` command specific to hdfs<br>
>```hadoop fs``` command for entire hadoop supported file system<br>
> List files - ```hadoop fs -ls <path>``` or ```hdfs dfs -ls <path>``` <br>
> mkdir - ```hadoop fs -mkdir <path>``` or ```hdfs dfs -mkdir <path>```<br>
> CopyFromLocal - ```hadoop fs -copyFromLocal <from> <toPath>``` <br>
> put - same as copy from local it moves local files to hadoop fs - ```hadoop fs -put <from> <to>``` <br>
> CopyToLocal  - ```hadoop fs -copyToLocal <from> <toPath>```<br>
> get - same as CopyToLocal<br>
> copy files from one location to another - ```hadoop fs -cp <from> <to>```<br>
> cat - display content of file in hadoop system<br>
>remove -rm -r 

Hdfs Replication
- high fault tolerance of HDFS is achieved by replication factor
- Replication factor - determines how many replication you want to create
- Choosing replica location/stratergy
    - Maximize redundancy
    - Minimize write bandwidth
    - default uses 3 replication factor 1 is rack1 and 2 in rack2

- NameNode Failures
    - Metadata files or Secondary namenode strategy is used to mitigate namenode failure
        - Metadata Files - fsimage and edits - store the filesystem metadata and helps to reconstruct th NameNode mappings
        > configuring backup location of namenode mapping is set by property
        > fds.namenode.name.dir and value can be multiple location separated by , 
        
        ``` note cons is that the merging of fsimage and edits to rebuild namenode mapping requires high compute ```

        -  Seconday NameNode- Checkpointing is the concept used behind to sync up between two namenodes
            - dfs.namenode.checkpoint.check.period is used set the checkpoint frequency to sync between primary and secondary namenodes
            - dfs.namenode.checkpoint.txns - sync based on no of transactions instead of frequency 

