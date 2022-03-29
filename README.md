# AWS-Certified-Solutions-Architect-Associate-Notes
AWS Certified Solutions Architect Associate Exam Notes

## EC2 Summary

### EC2 Instances Purchasing Options
- On-Demand Instances: Short-term and un-interrupted workloads
- Reserved Instances: Convertible Reserved Instance and Schedule Reserved Instances
- Spot Instances: Useful for workloads that are resilent to failure and Not suitable for critical jobs or databases
- Dedicated Hosts: Compliance requirements and Use your existing server-bound software licenses

### Placement Groups
- Cluster: Low latency group in a single AZ; Big Data job and Application that needs extremely low latecncy and high network throughput
- Spread: Application that needs High Availability; Critical Applications where must be isolated from faiulre from each other
- Partition: Up to 7 partitions per AZ; HDFS, HBase, Cassandra, Kafka

**Elastic Network Interfaces (ENI)** - Logical component in a VPC that represents a **Virtual Network Card**

### EC2 Capacity Reservations
- Manual or planned end-date for the reservation
- No need for 1 or 3 year commitment
- Capacity access is immediate, you get billed as soon as it starts
- Combined with Reserved Instances and Savings Plans to do cost saving

### AMI Overview
- AMI are built for a **specific region** (and can be copied across regions)

### EBS Volume Type Use cases
- **General Purpose SSD**: 1GB - 16TB; 3000 - 16000 IOPS
- gp3: 3000 IOPS and throughput of 125 MiB/s; can increase up to 16,000 IOPS and htroughput up to 1000 MiB/s independently
- gp2: 3000 IOPS; Size aof the volume and IOPS are linked; 3 IOPS per GB; max IOPS is 16,000

- **Provisioned IOPS SSD**: Great for databases workloads
- io1/io2: 4 GiB - 16 TiB; Max 64,000 PIOPS for Nitro & 32,000 for other
- io2 Block Express: Sub-millisecond latency; Max PIOPS 256,000


## AWS Database

### Amazon RedShift
- RedShift is a **SQL based data warehouse** used for analytics applications.
- RedShift is an **Online Analytics Processing (OLAP)** type of DB.
- RedShift is ideal for **processing** large amounts of data for business intelligence.
- Option to query directly from data files on S3 via **RedShift Spectrum**.
- RedShift can store huge amounts of data but **cannot ingest huge amounts of data in real time**.
- RedShift **uses EC2 instances** so you need to choose your instance type/size for scaling compute vertically, but you can also scale horizontally by adding more nodes to the cluster.
- Amazon Redshift provides the **fastest query performance** for enterprise reporting and business intelligence workloads, particularly those involving extremely complex SQL with multiple joins and sub-queries.
- Amazon RedShift	(**Primary Use Case	Data Warehouse**); Pull data from many sources, format and organize it, store it, and support complex, high speed queries that produce business reports.

### Amazon ElastiCache
- Fully managed implementations of two popular **in-memory data stores – Redis and Memcached**
- Best for scenarios where the DB load is based on Online Analytics Processing (OLAP) transactions.
- **Memcached** – simplest model, can run large nodes with multiple cores/threads, can be scaled in and out, can cache objects such as DBs.
- **Redis** – complex model, supports encryption, master / slave replication, cross AZ (HA), automatic failover and backup/restore.
- Exam tip: the key use cases for ElastiCache are offloading reads from a database and storing the results of computations and session state. Also, remember that ElastiCache is an in-memory database and it’s a managed service (so you can’t run it on EC2).

### Amazon DynamoDB
- Amazon DynamoDB is a **fully managed NoSQL database service** that provides fast and predictable performance with seamless scalability.
- DynamoDB is a **serverless** service – there are no instances to provision or manage.
- Amazon DynamoDB Accelerator (DAX) is a fully managed, highly available, **in-memory cache for DynamoDB** that delivers up to a 10x performance improvement.
- DynamoDB Streams captures a time-ordered sequence of item-level modifications in any DynamoDB table and stores this information in a log for up to 24 hours.

### Amazon Aurora
- Amazon Aurora is a **relational database service** that combines the speed and availability of high-end commercial databases with the simplicity and cost-effectiveness of open-source databases.
- Amazon Aurora **Multi-Master** is a new feature of the Aurora MySQL-compatible edition that adds the ability to scale out write performance across multiple Availability Zones, allowing applications to direct read/write workloads to multiple instances in a database cluster and operate with higher availability.
- Aurora Auto Scaling dynamically adjusts the number of Aurora Replicas provisioned for an Aurora DB cluster using single-master replication.
- When the connectivity or workload decreases, Aurora Auto Scaling removes unnecessary Aurora Replicas so that you don’t pay for unused provisioned DB instances.


## AWS Analytics

### Amazon OpenSearch
- Amazon OpenSearch Service is an open source, **distributed search and analytics** suite based on Elasticsearch.
- Elasticsearch is a popular search engine commonly used for log analytics, full-text search, security intelligence, business analytics, and operational intelligence use cases.
- ELK is an acronym that describes a popular combination of projects: **Elasticsearch, Logstash, and Kibana**.
- OpenSearch Service supports authentication through SAML and Amazon Cognito.

### AWS Glue
- AWS Glue is a fully-managed, pay-as-you-go, **extract, transform, and load (ETL) service** that automates the time-consuming steps of data preparation for analytics.
- AWS Glue runs the ETL jobs on a fully managed, scale-out **Apache Spark** environment to load your data into its destination.
- Glue can automatically discover both structured and semi-structured data stored in data lakes on **Amazon S3**, data warehouses in **Amazon Redshift**, and various databases running on AWS.
- It provides a unified view of data via the Glue Data Catalog that is available for ETL, querying and reporting using services like **Amazon Athena**, **Amazon EMR**, and Amazon **Redshift Spectrum**.
- AWS Glue is **serverless**, so there are no compute resources to configure and manage.
- AWS Glue (Primary Use Case ETL Service); Transform and move data to various destinations. Used to prepare and load data for analytics. Data source can be S3, RedShift or another database. Glue Data Catalog can be queried by Athena, EMR and RedShift Spectrum

### Amazon Athena
- Amazon Athena is an interactive query service that makes it easy to analyze data in **Amazon S3** using standard **SQL**.
- Athena is **serverless**, so there is no infrastructure to manage, and you pay only for the queries that you run.
- While Amazon Athena is ideal for quick, ad-hoc querying and integrates with **Amazon QuickSight** for easy visualization, it can also handle complex analysis, including large joins, window functions, and arrays.
- Amazon Athena provides the **easiest way** to run ad-hoc queries for data in S3 without the need to setup or manage any servers.
- Amazon Athena (**Primary Use Case Query**); Run interactive queries against data directly in Amazon S3 without worrying about formatting data or managing infrastructure. Can use with other services such as Amazon RedShift

### Amazon Kinesis
- Amazon Kinesis makes it easy to collect, process, and analyze real-time, streaming data so you can get timely insights and react quickly to new information.
- Data is processed in “shards” – with each shard able to ingest 1000 records per second.
- **Kinesis Video Streams** makes it easy to securely stream video from connected devices to AWS for analytics, machine learning (ML), and other processing.
- Kinesis Data Streams enables you to build custom applications that process or analyze streaming data for specialized needs.
- Kinesis Data Streams is useful for rapidly moving data off data producers and then continuously processing the data.
- Kinesis Data Streams **stores data** for later processing by applications (key difference with Firehose which delivers data directly to AWS services).
- Kinesis Data Streams Destinations: **Amazon S3, Amazon DynamoDB, Amazon RedShift, Amazon EMR, Kinesis Firehose**
- **Kinesis Data Firehose** is the easiest way to load streaming data into data stores and analytics tools.
- With Kinesis Data Firehose you don’t need to write an application or manage resources.
- Firehose Destinations include: **Amazon S3, Amazon RedShift, Amazon Elasticsearch Service, Splunk**
- No shards, totally automated. Firehose can invoke an **AWS Lambda** function to transform incoming data before delivering it to a destination.
- **Kinesis Data Analytics** is the easiest way to process and analyze real-time, streaming data.
- Can ingest data from Kinesis Streams and Kinesis Firehose.
- Output to **S3, RedShift, Elasticsearch and Kinesis Data Streams**.

### Amazon EMR
- Amazon EMR is a web service that enables businesses, researchers, data analysts, and developers to **process vast amounts of data**.
- EMR utilizes a hosted **Hadoop** framework running on **Amazon EC2 and Amazon S3**.
- Most used for log analysis, financial analysis, or extract, translate and loading (ETL) activities.
- Amazon EMR makes it simple and cost effective to run highly distributed processing frameworks such as **Hadoop, Spark, and Presto** when compared to on-premises deployments. Amazon EMR is **flexible** – you can run custom applications and code, and define specific compute, memory, storage, and application parameters to optimize your analytic requirements.
- Amazon EMR (Primary Use Case Data Processing); Highly distributed processing frameworks such as Hadoop, Spark, and Presto. Run a wide variety of scale-out data processing tasks for applications such as machine learning, graph analytics, data transformation, streaming data.



## Important Topics

https://jayendrapatil.com/aws-global-vs-regional-vs-az-resources/

- S3: Global but Data is Regional
- EC2: Region
- VPC: Region
- ASG: Region
- RDS: Region
- EBS Snapshot: Region
- SQS: Region
- ELB: Region
- CloudFront: Global
- IAM: Global
- DynamoDB: Regional
- Lambda: Regional
- Route53: Global
- EC Instances / EBS Volumes: Availability Zone
- Cluster Placement Groups – Availability Zone


