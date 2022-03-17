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

### #BS Volume Type Use cases
- **General Purpose SSD**: 1GB - 16TB; 3000 - 16000 IOPS
- gp3: 3000 IOPS and throughput of 125 MiB/s; can increase up to 16,000 IOPS and htroughput up to 1000 MiB/s independently
- gp2: 3000 IOPS; Size aof the volume and IOPS are linked; 3 IOPS per GB; max IOPS is 16,000

- **Provisioned IOPS SSD**: Great for databases workloads
- io1/io2: 4 GiB - 16 TiB; Max 64,000 PIOPS for Nitro & 32,000 for other
- io2 Block Express: Sub-millisecond latency; Max PIOPS 256,000
