# AWS100 - Creating an Amazon RDS DB Instance (MySQL)

## Cloud Service Provider

- Amazon Web Services


## Difficulty

- Level 100 (Introductory)

## Objectives

### You need to complete the following:

- Setup a database instance on Amazon RDS
- Create a MySQL database instance on RDS
- Connect to RDS database instance from your local

### You need to answer the following:

### ***What is RDS?***

Amazon RDS (Relational Database Service) is a fully managed service by AWS that simplifies the process of setting up, operating, and scaling relational databases in the cloud. RDS supports various database engines, including:

- Amazon Aurora
- MySQL
- PostgreSQL
- MariaDB
- Oracle
- Microsoft SQL Server

With RDS, AWS handles the underlying infrastructure, such as backups, patching, and replication, allowing users to focus on database management and application development. It also offers features like automated backups, multi-AZ deployments for high availability, read replicas for scalability, and security using encryption at rest and in transit.

### ***How to create a database instance on RDS?***

To create a database instance on Amazon RDS, follow these steps:

**Step 1: Sign in to the AWS Management Console**

1. Navigate to the Amazon RDS Console.
2. From the dashboard, click on Create database.

**Step 2: Configure the Database Engine**

1. Choose a database creation method:
     - **Standard create:** Offers complete customization.
     - **Easy create:** Offers pre-configured settings for beginners.
2. Select a database engine (**MySQL**).
![alt text](<create database.png>)
3. Choose a version for the engine (Latest).
4. Select Templates 
    - **Standard create:** Use defaults for high availability and fast, consistent performance.
    - **Dev/Test:** This instance is intended for development use outside of a production environment.
    - **Free tier:** Use RDS Free Tier to develop new applications, test existing applications, or gain hands-on experience with Amazon RDS
    ![alt text](templates.png)

**Step 3: Availability and durability**
Deployment options
- **Multi-AZ DB cluster:** Creates a DB cluster with three DB instances. Each DB instance is in a different Availability Zone. A Multi-AZ DB cluster has one primary DB instance and two readable standby DB instances. Using a Multi-AZ DB cluster provides high availability, increased capacity for read workloads, and lower latency.
- **Multi-AZ DB instance:** Creates a primary DB instance with one standby DB instance in a different Availability Zone. Using a Multi-AZ DB instance provides high availability, but the standby DB instance doesn't support connections for read workloads.
- **Multi-AZ DB instance:** Creates a single DB instance with no standby instances.
![alt text](<availability and durability.png>)

**Step 4: Configure Database identifier and Credentials**
1. Specify a name that is unique for all DB instances
2. Set the master username and password for your database.
![alt text](settings.png)

**Step 4: Set up the Database Instance configuration**

1. **Instance Class:** Choose the size of the instance (`db.t3.micro`).
    - **Standard:** Standard instances provide a balance of compute, memory, and network resources. They are a good choice for many database workloads.
    - **Memory optimized classes:** Memory optimized instances accelerate performance for workloads that process large data sets in memory.
    - **Burstable classes:** Burstable performance instances provide a baseline level of CPU performance with the ability to burst above the baseline.
    ![alt text](instanceConfiguration.png)

2. **Storage:** Specify the storage type and allocated space (SSD).
    - **storage autoscaling:** Choose the dynamic storage scaling setting required by planned workload of this DB instance.
    ![alt text](settings.png)

3. **VPC and Subnet:** Select the VPC and subnet where you want to deploy the RDS instance.
   - Choose **Public accessibility** for the database to be publicly accessible.
    ![alt text](connectivity.png)
**Step 5: Advanced Settings**

1. **Backup:** Configure automatic backups and retention period.
    -  Choose the number of days that Amazon RDS should retain automatic backups of this DB instance.
        -   The backup retention period determines the period for which you can perform a point-in-time recovery
        -   Aurora offers 1-day backup retention for free!
    - **Backup replication:** You can replicate automated backups to another AWS Region to help with disaster recovery. Snapshots and transaction logs are replicated immediately after they are available in the source.
    ![alt text](connectivity.png)

2. **Encryption:** Enable encryption for the database instance (optional).
3. **Maintenance:** Configure maintenance windows, parameter groups, and more.
4. **Maintenance window:** select the period in which you want pending modifications (such as changing the DB instance class) or patches applied to the DB instance by Amazon RDS. Any such maintenance should be started and completed within the selected period. If you do not select a period, Amazon RDS will assign a period randomly. 
4. **Deletion protection:** Protects the database from being deleted accidentally. While this option is enabled, you can’t delete the database.
![alt text](image.png)

**Step 6: Review and Launch**
1. Review your configurations.
2. Click **Create Database**.

Once the RDS instance is launched, it will take a few minutes for the instance to be available.
![alt text](finish.png)

### ***How to connect to RDS database?***

To connect to an RDS database:

**Step 1: Get the Endpoint and Port**

- Go to the RDS Console.
- Select the RDS instance you want to connect to.
- Copy the endpoint and port from the Connectivity & Security section.

**Step 2: Configure Security Groups and Networking**

- Ensure that the security group attached to your RDS instance allows inbound connections on the database's port (e.g., 3306 for MySQL).
- If the RDS instance is in a private subnet, you will need a VPN or an EC2 instance within the same VPC to act as a bastion host for the connection.

**Step 3: Connect via Client Tools**
- MySQL: Use SQL Electron and connect with the endpoint, port, **username**, and **password**.

## References
- [What is RDS?](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)
- [Setting Up for Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_SettingUp.html)
- [Creating an Amazon RDS DB Instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateDBInstance.html)
- [Connecting to a DB Instance Running the Microsoft SQL Server Database Engine](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ConnectToMicrosoftSQLServerInstance.html)
- [Running SQL Server Databases on Amazon RDS for SQL Server - AWS Virtual Workshop](https://youtu.be/twOglkIFbXU)
- [Amazon RDS Free Tier](https://aws.amazon.com/rds/free/)

## Costs

- Included in the Free Tier


## Estimated time to complete
- 15 minutes


## Tips
- Having database knowledge is an added advantage
- 750 hours of Amazon RDS Single-AZ `db.t2.micro` included in free tier

# Output
![alt text](Image.png)