
ambari:
  HiveServer2  /  Hive  
  Metrics Collector  /  Ambari Metrics  
  Standby NameNode  /  HDFS  
  Oozie Server  /  Oozie  
  WebHCat Server  /  Hive  
  ZooKeeper Server  /  ZooKeeper  
  Metrics Monitor  /  Ambari Metrics  
  ZKFailoverController  /  HDFS  

Clients /
HCat Client, HDFS Client, Hive Client, Kerberos Client, MapReduce2 Client, Oozie Client, Pig, Sqoop, Tez Client, YARN Client, ZooKeeper Client


master1:

  Hive Metastore  /  Hive  
  Active NameNode  /  HDFS  
  ResourceManager  /  YARN  
  ZooKeeper Server  /  ZooKeeper  
  Metrics Monitor  /  Ambari Metrics  
  ZKFailoverController  /  HDFS  

Clients /
HDFS Client, Kerberos Client, MapReduce2 Client, Sqoop, Tez Client, YARN Client

Kerberos server



master2:

  App Timeline Server  /  YARN  
  History Server  /  MapReduce2  
  ZooKeeper Server  /  ZooKeeper  
  
Clients /
HDFS Client, Kerberos Client, MapReduce2 Client, Sqoop, Tez Client, YARN Client


data1:

  DataNode  /  HDFS  
  JournalNode  /  HDFS  
  Metrics Monitor  /  Ambari Metrics  
  NodeManager  /  YARN  

Clients /
HDFS Client, Kerberos Client, MapReduce2 Client, Sqoop, YARN Client


data2:
  DataNode  /  HDFS  
  JournalNode  /  HDFS  
  Metrics Monitor  /  Ambari Metrics  
  NodeManager  /  YARN     
 
 Clients /
HDFS Client, Kerberos Client, MapReduce2 Client, Sqoop, YARN Client

data3:

 DataNode  /  HDFS  
  JournalNode  /  HDFS  
  Metrics Monitor  /  Ambari Metrics  
  NodeManager  /  YARN  

Clients /
HDFS Client, Kerberos Client, MapReduce2 Client, Sqoop, YARN Client