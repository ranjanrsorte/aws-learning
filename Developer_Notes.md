# AWS Developer Certification-

# Certified Developer Exam DVA-C01

# Notes:

# Section 1: Course Introduction - AWS Certified Developer Associate

Lecture 1:
1. AWS (Amazon Web Services) is a Cloud Provider.
2. AWS provides servers and services that can use 'on demand' and 'scale easily'.

# Section 3: Getting started with AWS

Lecture 1:
1. AWS Global Infrastructure
  - AWS Regions
  - AWS Availability Zones
  - AWS Data Centers
  - AWS Edge Locations / Points of Presence

2. AWS Regions
  - AWS has Regions all around the world
  - Names can be us-east-1, eu-west-3...
  - A region is a cluster of data centers
  - Most AWS services are region-scoped

Q. How to choose an AWS Region?
- Compliance with data governance and legal requirements: data never leaves a region without your explicit permission
- Proximity to customer: reduced latency
- Available services within a Region: new services and new features aren't available in every region
- Pricing: pricing varies region and is transparent in the service pricing page

3. AWS Availability Zones
  - Each region has availability zones (usually 3, min is 2, max is 6)
    - Example:
    	ap-southeast-2a
    	ap-southeast-2b
    	ap-southeast-2c
  - Each availabilty zone is one or more discrete data centers with redundant power, networking, and connectivity.
  - They're separate from each other, so that they're isolated from disaster
  - They're connected with high bandwidth, ultra-low latency networking and hence they form a region


# Section 4: IAM & AWS CLI

Lecture 1:
1. IAM: Users & Groups
  - IAM = Identity and Access Management, GLobal service
  - Root account created by default, shouldn't be used or shared
  - Users are people within you organization, and can be grouped
  - Groups only contain users, not other groups
  - Users don't have to belongs to a group, user can belong to multiple groups
  - For IAM Users & Groups are created as a global fashion

2. Users
  - For Security purpose it is very dangerous to use root user because root user has all the access. The Best practice is to create a new Administrator user and give all the access same as root user and if there is more need then and only then root user can be used.

3. Groups
  - Any user placed within the group will inherit all the permissions associated with that group.
  - Permissions are define through policies.
  - Giving 'AdministratorAccess' policy to a group will give all the administrator permission to the users belong to that group.

4. Multi Factor Authentication (MFA)
  - MFA devices options in AWS
    1. Virtual MFA device
      - Google Authenticator (Phone Only)
      - Authy (multi-device)
        - It can be used in the multiple devices like phone, laptops etc
        - Support for multiple tokens, means we can authenticate multiple users using a single Authy account.

    2. Universal 2nd Factor (U2F) Security Key
      - It is a physical device, for example YubiKey by Yubico.
      - Yubico is 3rd party to AWS.
      - It is a pen-drive like device which is easy to use. Just need to connect to the computer and we are good to go.
      - This YubiKey supports multiple roots and IAM users using a single security key, so we don't need as many keys.

    3. Hardware Key Fob MFA Device
      - Provided by Gemalto (3rd party)
    4. Hardware Key Forb MFA Device for AWS GovCloud (US)
      - Provided by SurePassID (3rd Party)
      - If we are using cloud of the government in the US then we will have a special Key Fob by the AWS GovCloud.

5. Three options to access the AWS
  - AWS Management Console (protected by password + MFA)
  - AWS Command Line Interface (CLI): protected by access keys
  - AWS Software Developer Kit (SDK): for code- protected by access keys
    - Enables to access and manage AWS services programmatically.
    - Language-specific APIs (set of libraries) are there to access the AWS services.
    - Embedded within the application.

  - Access Keys are generated through the AWS Consle
  - Users manage their own access keys
  - Access Keys are secret, just like password.
  - Access Key ID ~= username
  - Secret Access Key ~= password

6. Access Key
  - While creating a access key always use IAM user. Do not use root user.

7. AWS CloudShell
  - It is the embedded shell which provides the terminal for running all the commands to the AWS.

8. IAM Roles for Services
  - We can assign permissions to AWS with IAM Roles
  - Common roles:
    - EC2 Instance Roles
    - Lambda Function Roles
    - Roles for CloudFormation

9. IAM Security Tools
  (Can be seen in IAM -> Credential Report)
  - Downloading the report will download the csv file which will contains all the list of IAM users along with the root user and the activity for each user can be seen by that downloaded csv. So, if any user is have updated their password for longer period of time then we can find that user and give attention to that user.
  - In the User -> Edit User and we can see the 'Access Advisor' tab which shows the list of the AWS services that user is accessing. If the user is not accessing any service for longer period of time as that user does not need that service then simply we can remove the access for that service for the user.
  - IAM Security Tools have two types of reports:
    1. IAM Credentials Report (account-level)
      - A report that lists all your account's users and the status of their various credentials.
    2. IAM Access Advisor (user-level)
      - Access advisor shows the service permissions granted to a user and when those services were last accessed.
      - We can use this information to revice the policies.

10. IAM Guidelines & Best Practices
  - Don't use the root account except for new AWS acoount setup.
  - Don't give access to one account user to another user. Simply create a new user account for each user.
  - We can assign users to groups and assign permissions to group.
  - Create strong password policy.
  - Always make the use of MFA (Multi Factor Authentication).
  - Create and use Roles for giving the permissions to AWS services.
  - Use Access Keys for Programmatic Access (CLI / SDK).
  - Always Audit permissions of account with the IAM Credentials Report.
  - Never share IAM users & Access Keys.

11. IAM - Summary
  - Users: mapped to a physical user, has password for AWS console.
  - Groups: It is best practice to group all the users. Make sure groups only contains the users not other groups.
  - Policies: To give permission to either the users or the groups, we have to create IAM policies, which are JSON documents, that will outline the permissions that a user or a group can do.
  - Roles: If we are within AWS then we are using roles. So if we create an EC2 instance, or we want to give permissions, to an AWS service to do something else, on another AWS service, then we have to create IAM roles.
  - Security: For Security and making sure our users are completely safe, we must enable multi factor authentication along with a Strong password.
  - Access Keys: If we want to access AWS programmatically using AWS CLI/SDK then always generate access key ID and secret access key for accesing the AWS prgrammatically.
  - Audit: If we want to access the credential reports for all the users then we must generate the credential report. Or if we want to access a specific user then we can check that in Access Advisor for checking the user is accessing all the given services or not.

12. Setting up the Billing Dashboard for the IAM user
  - Step 1: Login as root user.
  - Step 2: Select on the user login name which is on top right column
  - Step 3: Select on 'Account' option from dropdown
  - Step 4: Scroll down and search for 'IAM User and Role Access to Billing Information' option and select 'Edit' option
  - Step 5: Select checkbox 'Activate IAM Access' and select 'Update' button.
  - Step 6: Login as a IAM user, select the user's name from the top right corner and from the dropdown select 'Biiling Dashboard' option

Q. Why do we create groups & Users?
  - Because we want to allow them to use our AWS accounts and allow them to do same permissions.

# Section 5: EC2 Fundamentals

Amazon EC2
- EC2 is one of the most popular of AWS offering
- EC2 = Elastic Compute Cloud which is called as Infrastructure as a Service
- It mainly consisits in the capacity of:
  - Renting cirtual machines (EC2)
  - Storing data on virtual drives (EBS)
  - Distributing load across machines (ELB)
  - Scaling the services using an auto-scaling group (ASG)
- EC2 User data
  - User data is a script that will be launched during the very and only first boot of the instance.

EC2 Instance Types

1. General Purpose
  - Great for a diversity of workloads such as web servers or code repositories.
  - It is Balance between Compute, Memory & Networking.
2. Compute Optimized
  - Great for compute-intensive tasks that require high performance processors:
    - Batch processing workloads
    - Media transcoding
    - High performance web servers
    - High performance computing (HPC)
    - Scientific modeling & machine learning
    - Dedicated gaming servers
  - All the compute type of instances are named as starting from 'c' i.e. C6g, C6gn, C5, C5a, C5n, C4 etc.
3. Memory Optimized
  - Fast performance for workloads that process large data sets in memory (RAM).
  - Use cases:
    - High performance, relational/non-relational databases.
    - Distributed web scale cache stores
    - In-memory databases optimized for Business Intelligence (BI)
    - Applications performing real-time processing of big structured data
  - All the Memory optimized instances are named as starting from 'r' i.e. R6g, R6i, R5, R5a etc
4. Accelerated Computing
5. Storage Optimized
  - Great for storage-intensive tasks that require high, sequential read and write access to large data sets on local storage.
  - Use cases:
    - High frequency online transaction processing (OLTP) systems
    - Relational & NoSQL databases
    - Cache for in-memory databases (ex Redis)
    - Data warehousing applications
    - Distributed file systems
6. Instance Features
7. Measuring Instance Performance

- We can find different types of instances that are optimised for different use cases on https://aws.amazon.com/ec2/instance-types/
- AWS has the following naming convention:
  - ex m5.2xlarge
    - m: instance class
    - 5: generation of instance (AWS improves them over time)
    - 2xlarge: size within the instance class

- Compare all the EC2 instances together on https://www.ec2instances.info/ which redirects to https://instances.vantage.sh/

Security Groups
- Security Groups are acting as a "firewall" on EC2 instances
- Security Groups control traffic is allowed into or out EC2 instances.
- Security groups rules can reference by IP or by security group
- They regulate:
  - Access to ports
  - Authorised IP ranges - IPv4 & IPv6
  - Control of inbound network (from other to the instance)
  - Control of outbound network (from the instance to other)
- Security Groups can be attached to multiple EC2 instances
- Locked down to a region/VPC combination, means it is not accessible outside of the region where security group is created. For each region we have to create a Security Group.
- Does live "outside" the EC2 instance, means if traffic is blocked the EC2 instance won't see it.
- It's good to maintain one separate security group for SSH access
- If application is not accessible(time out or site can't be reached) then it's a security group issue.
- If the application gives a "connection refused" error, then it's an application error or it's not launched.
- All inbound traffic is blocked by default.
- All outbound traffic is authorised by default.

Classic Ports to know
- 22 = SSH (Secure Shell) - log into a Linux instance
- 21 = FTP (File Transfer Protocol) - upload files into a file share
- 22 = SFTP (Secure File Transfer Protocol) - upload files using SSH
- 80 = HTTP - access unsecured websites
- 443 = HTTPS - access secured websites
- 3389 = RDP (Remote Desktop Protocol) - log into a Windows instance

SSH Overview
- SSH allow us to control a EC2 machine remotely.
- SSH is the Secure Shell to servers which connects to the EC2 instances for doing some maintenance operation.
- SSH is the command line utility which can be used on Mac & Linux as well as Windows 10 and above.
- For lower version of windows we can use Putty. Putty will exceed the exact same thing as SSH. We can use on any version of Windows.
- Putty use the SSH protocol to connect into the EC2 instances.
- EC2 instance connect use the web browser to connect to EC2 instances. It works with Amazon NX2.

Command for SSH to EC2 instance
` ssh -i C:\Work\AWS\Learning\Developer\Material\EC2MyInstance.pem ec2-user@15.206.75.32 `
- ssh : ssh command
- -i : identity
- C:\Work\AWS\Learning\Developer\Material\EC2MyInstance.pem : Path for .pem file
- ec2-user : name of user from the EC2 (It can be any, here we are taking 'ec2-user')
- 15.206.75.32 : Public IPv4 Address (It will always change if EC2 instance is stopped or terminated)

EC2 Instances Purchasing Options (Q. How to find the best Instances?)
1. On-Demand Instances
  - These are the instances that we require for short workloads.
  - Pay for what we use:
    - For Linux or Windows - billing per second, after the first minute when On-Demand Instance is running.
    - All other operating systems - billing is per hour when On-Demand Instance is running.
    - Has the highest cost but no upfront payment.
    - No long-term commitment
    - Recommended for short-term and un-interrupted workloads, where we can't predict how the application will behave.
2. Reserved Instances
  - Reserved instances needs to be used for minimum 1 year, this is commitment to AWS.
  - Up to 75% discount compared to On-demand.
  - Reservation period: 1 year or 3 years (More the duration more will be the discount)
  - Purchasing options: No Upfront (Pay Monthly) or Partial Upfront or All Upfront (Pay all amount at the time of purchasing).
  - We have to Reserve a specific instance type. For example, I want t2.micro or I want C5.large.
  - Recommended for steady-state usage applications (like database)
  - There are three types of Reserved Instances:
    - Reserved Intances: These are used for longer workloads such as database.
    - Convertible Reserved Instances:
      - When we have flexible instances, so we want to change their type over time.
      - Up to 54% discount
    - Scheduled Reserved Instances (Deprecated):
      - Launch within reserved time window.
      - When we require only for fraction of time within day / week / month
      - Need commitment over 1 to 3 years.
3. Spot Instances
  - These are used for short workloads, cheap and we can lose them, they're less reliable.
  - Can get a discount of upto 90% compared to On-demand.
  - Instances that we can lose at any point of time if max price is less than the current spot price.
  - The most cost-efficient instances in AWS.
  - Useful for workloads like Batch jobs, Data analysis (One time analysis), Image processing, Any distributed workloads, Workloads with flexible start and stop time.
  - Not suitable for critical jobs or databases.
4. Dedicated Host Instances
  - If we want to book an entire physical server and control the instance placement.
  - Dedicated Hosts can help us address compliance requirements and reduce costs by allowing us to use our existing server-bound licenses.
  - Allocated for our account for a 3 years period reservation.
  - More expensive.
  - Useful for software that have complicated licensing model (BYOL - Bring Your Own License) or for companies that have strong regulatory or compliance needs.
  - So as we know AWS servers all of it's servers. If we don't want any other user to use our server then there we must have a physical server(Dedicated host server) for ourself.
  - Per host billing.
5. Dedicated Instances
  - Instances running on hardware that's dedicated to us.
  - May share hardware with other instances in same account.
  - No control over instance placement.
  - Per instance billing.

# Section 6: EC2 Instance Storage
- EBS Volume
  - EBS stands for Elastic Book Store
  - It is a network drive which can be attached to the instances while they run.
  - It allows instances to persist data, even after their termination.
  - They can only be mounted to one instance at a time.
  - They are bound to specific availability zone. That means we cannot have a EBS volume created in us-east and bound to instance from us-west or some other region.
  - Free tier: 30GB of free EBS storage of type General Purpose (SSD) or Magnetic per month.
  - It uses the network to communicate with the instance, which means there might be a bit of latency.
  - It can be detached from an EC2 instance and attached to another one quickly.
  - It is locked on Availability zones, to move a volume across the zones we first need to snapshot(backup) it.
  - Must have a provisioned capacity (size in GB)
    - Billed as per provisioned capacity.
    - We can increase the capacity of drive over time.

- EBS Snapshots
  - Make a backup (snapshot) of EBS volume at any point of time.
  - Not necessary to detach volume from instance for snapshot, but it is recommended.
  - We can copy snapshot across Availability Zones or regions.

- AMI
  - AMI: Amazon Machine Image
  - AMI are a customization of an EC2 instance
    - We can add our own software, configuration, operating system, monitoring etc
    - Faster boot / configuration time because all our software are pre-packaged
  - AMI are build for specific region and can be copied across the regions.
  - We can launch EC2 instances from:
    - A public AMI: AWS provided
    - Own AMI: We can make and maintain them ourself
    - An AWS Marketplace AMI: An AMI made by someone else and available in marketplace to purchase.

- EC2 Instance Store
  - EBS volumes are network drives with good but "limited" performance.
  - If we need high performance hardware disk, use EC2 Instance Store.
  - Q. Why to use EC2 Instance Store?
    - Better I/O performance
    - EC2 Instance Store loss their storage if they're stopped or If EC2 instance is stopped which has EC2 Store connected then also EC2 Instance Store lost.
    - Good for buffer data / cache / scratch data / temporary content.
    - Risk of data loss if harware fails.
    - Backups and Replication needs to be implemented for preventing the data.

- EBS Volume Types
  - EBS Volumes come in 6 types:
    1. gp2 / gp3 (SSD): General purpose SSD volume that balances price and performance for a wide variety of workloads.
    2. io1 / io2 (SSD): Highest-performance SSD volume for mission-critical low-latency or high-throughput workloads.
    3. st1 (HDD): Low cost HDD volume designed for frequently accessed, throughput-intensive workloads.
    4. sc1 (HDD): Lowest cost HDD volume designed for less frequently accessed workloads.
  - EBS volumes are characterized in size | Throughput | IOPS (I/O Ops Per Sec).
  - Only gp2/gp3 and io1/io2 can be used as boot volumes.
  - Use Cases:
    1. General Purpose SSD
      - Cost effective storage, low-latency
      - Can be used as a System Boot volumes, Virtual desktops, Development and test environments.
      - Has size between 1GB to 16TB. 
      - gp3:
        - Is the new generation type of volume.
        - It has a baseline of 3000 IOPS and throughput of 124 MB/s
        - IOPS can be increase up to 16000 and throughput up to 1000MB/s independently.
      - gp2:
        - It is the older type of volume.
        - Small gp2 volumes can burst IOPS to 3000.
        - Size of the volume and IOPS are linked, max IOPS is 16000.
        - 3 IOPS per GB, means at 5334 GB we are at the max IOPS.
    2. Provisioned IOPS (PIOPS) SSD
      - Good for Critical business applications with sustained IOPS performance
      - Or for the application that needs the more than 16000 IOPS
      - Great for database workloads (sensitive to storage perf and consistency)
      - io1 / io2 (4GB - 16GB):
        - Max PIOPS: 64000 for Nitro EC2 instance & if we don't have Nitro instance then it will give 32000 PIOPS for other.
        - Can increase PIOPS independently from storage size
        - io2 have more durability and more IOPS per GB (at the same price as io1)
      - io2 Block Express (4GB - 64TB):
        - Gives the higher performance type of volume which gives sub-milisecond latency. 
        - Max PIOPS: 256000 with an IOPS:GB ratio of 1000:1
      - Supports EBS Multi-attach
    3. Hard Disk Drives (HDD)
      - Cannot be a boot volume
      - Has size 125MB to 16TB
      - Two kinds of volumes
        - Throughput Optimized HDD (st1)
          - Good for Big Data, Data Warehousing & Log Processing
          - Which gives Max throughput of 500MB/s to max IOPS 500
        - Cold HDD (sc1):
          - For data that is infrequently accessed
          - Can be used in a scenarios where lowest cost is important
          - Max throughput 250MB/s to max IOPS of 250

- EBS Multi-Attach - io1/io2 family
  - This feature will give the ability to attach the same EBS volume to multiple EC2 instances in the same Availabilty Zone
  - We can attach a EBS volume to multiple instances if that volume is from io1/io2 family
  - Each attached instance to the volume has full read & write permissions to the volume
  - Use Case:
    - Achieve higher application availability clustered Linix applications (ex: Teradata)
    - Applications must manage concurrent write operations
  - Must use a file system that's cluster-aware (not XFS, EX4m etc...)

- EFS - Elastic File System
  - It is a managed NFS (Network File System) that can be mounted on many EC2 instances across many different Availabilty zone.
  - EFS works with EC2 instances in mutiple availability zones
  - Highly available, scalable & expensive (3x gp2), bill is calculated per use.
  - Use cases: content management web serving data sharing, wordpress
  - Uses NFSv4.1 protocol to mount a network drive
  - Uses security group to control access to EFS
  - Compatible with Linux based AMI (not Windows)
  - To encrypt the EFS, we can use KMS keys.
  - EFS is used only for POSIX file system (~Linux) that has a standard file API
  - File system scales automatically, pay-per-use, no capacity planning

- EFS - Performance & Storage Classes
  - EFS Scale
    - 1000s of concurrent NFS client, 10GB+ /s throughput
    - Can grow to Petabyte-scale network file system, and that will be automatic
  - Performance mode (set as EFS creation time)
    - General Purpose(default): latency-sensitive use cases (web server, CMS etc)
    - Max I/O - higher latency, throughput, highly parellel (big data, media processing)
  - Throughput mode
    - By default we are in bursting throughput mode.
    - That means Bursting (1TB = 50MB/s + burst of up to 100MB/s)
    - If we have very small file system, but we need very high throughput then we need to move into "provision throughput mode" for EFS.
  - Storage Tiers (lifecycle management feature - move file after N days)
    - It is a lifecycle management feature for the files to move a file into a new tier after may be some N days.
    - So the standard is for frequently accessed files.
    - Infrequent access (EFS-1A): cost to retrieve files, lower price to store

- EFS - Demo Steps
  1. Create a Security Group for EFS
  2. Create a EFS by adding the Security group which is created in above step.
  3. Create two instances on different availabilty zone with same security group.
  4. SSH to both EC2 instances
  5. For running the efs command we need to install the 'amazon-efs-utils'. Run below command on both instances for efs
    `sudo yum install -y amazon-efs-utils`
  6. Create a 'efs' directory on both instances using command
    `mkdir efs`
  7. Create a .txt file inside 'efs' folder on 1st instance using command
    ```
    cd efs
    sudo touch hello-world.txt
    ```
  8. Check file is created or not inside 'efs' folder of 1st instance using command
    `ls`
  9. Check same file is created or not inside 'efs' folder of 2nd instance using command
    ```
    cd efs
    ls
    ```
  10. Write something in the hello-world.txt file from 1st instance using below command
    `sudo nano hello-world.txt`
  11. Check same data is updated in the file from the 2nd instance using below command
    `cat hello-world.txt`

# Section 7: AWS Fundamentals: ELB + ASG

- Scalability & High Availability
  - Scalability means that an application / system can handle greater loads by adapting.
  - There are two kinds of scalability:
    1. Vertical Scalability
      - Vertical Scalability means increasing the size of the instance
      - For example, application runs on a t2.micro and we can upscale that application vertically means running it on t2.large
      - Vertical Scalability is very common for non distributed systems, such as database.
      - RDS, ElastiCache are services that can scale vertically.
      - There's usually a limit to how much we can scale vertically. i.e hardware limit
      - 
    2. Horizontal Scalability (= elasticity)
      - Horizontal Scalabilty means increasing the number of instances / systems for the application.
      - Horizontal scaling implies to distributed systems.
      - This is very common for web applications / modern applications.
      - It's easy to horizontally scale because of the cloud offerings such as Amazon EC2. Just right click on instance and we can create number of same instance with some clicks.
  - Scalibility is linked but different to High Availability
  - High Availabilty means running application / system in at least 2 data centers (== Availability Zones)
  - The goal of high availability is to survive a data center loss
  - The high availability can be passive (for RDS Multi AZ)
  - The high availability can be active (for horizontal scaling)

- Load Balancing
  - Q. What is load balancer?
    - Load Balances are servers that forward traffic to multiple servers (e.g. EC2 instances) downstream.
  - Q. Why use a load balancer?
    - Spread load across multiple downstream instances
    - Expose a single point of access (DNS) to your application
    - Seamlessly handle failures of downstream instances
    - Do regular health checks to instance
    - Provide SSL termination (HTTPS) to websites
    - Enforce stickiness with cookies
    - High availability across zones
    - Separate public traffic from private traffic
  - Q. Why use an Elastic Load Balancer?
    - An Elastic Load Balancer is a managed load balancer
      - AWS guarantees that it will be working
      - AWS takes care of upgrades, maintenance, high availability
      - AWS provides only a few configuration knobs
    - It costs less to setup own load balancer but it will take a lot more effort to setup.
    - It is integrated with many AWS offerings / services
      - EC2, EC2 Auto Scaling Groups, Amazon ECS
      - AWS Certificate Manager (ACM), CloudWatch
      - Route 53, AWS WAF, AWS Global Accelerator
  - Health Checks
    - Health Checks is a way for elastic load balancer to verify whether not an EC2 instance is properly working, because if it is not working properly, then we don't have to send any traffic to that instance.
    - Health Checks are crucial for Load Balancers
    - They enable the load balancer to know if instances it forwards traffic to are available to reply to requests or not.
    - The Health Check is done on a port and a route (/health is common).
    - If the response is not 200, then the instance is unhealthy.
  - Types of load balancer on AWS
    - AWS has 4 kinds of managed Load Balancers
      - Classic Load Balancer (v1 - old generation) - 2009 - CLB (Deprecated, but available to use)
        - Supports HTTP, HTTPS, TCP, SSL(secure TCP)
      - Application Load Balancer (v2 - new generation) - 2016 - ALB
        - Supports HTTP, HTTPS, Web Socket
      - Network Load Balancer (v2 - new generation) - 2017 - NLB
        - Supports TCP, TLS (secure TCP), UDP
      - Gateway Load Balancer - 2020 - GWLB
        - Operates at layer 3 (Network Layer) - IP Protocol
    - Recommended to use newer generation load balancers as they provide more features
    - Some load balancers can be setup as internal (private) or external (public) ELBs
  - Load Balancer Security Groups
    - The users can access the load balancer from anywhere using HTTP or HTTPS.
    - Therefore the security group rule will be having the port range between 80 or 443 and the source will be 0.0.0.0/0, which means anywhere. And so we allow the users to connect to our load balancer.
    - But the EC2 instances only allow traffic coming directly from the load balancer.
    - Therefore the security group rule will be allowing the HTTP traffic on port 80 and source of it is not going to be an IP range, it is going to be a security group.
    - So we need to link the security group of EC2 instance, to the security group of the load balancer. And effectively what it will do is that it will say that the EC2 instance is only allowing traffic if the traffic originates from the load balancer, which is an enhanced security mechanism.

- Classic Load Balancer (v1) (CLB)
  - Supports TCP (Layer 4), HTTP & HTTPS (Layer 7)
  - Health checks are TCP or HTTP based
  - It has fixed hostname XXX.region.elb.amazon.com

- Application Load Balancer (v2) (ALB)
  - Application load balancers is Layer 7 (HTTP)
  - Load balancing to multiple HTTP applications across machines (target groups)
  - Load balancing to multiple applications the same machine (ex. containers)
  - Support for HTTP/2 and WebSocket
  - Support redirects (from HTTP to HTTPS) automatically at load balancer level
  - Supports Route Routing
    - Different Routing based on different target group
      - Routing based on path in URL (example.com/users & example.com/posts)
      - Routing based on hostname in URL (one.example.com & other.example.com)
      - Routing based on query string, headers (example.com/users?id=123&order=false)
  - ALB are great when we have microservices and container based application (Ex. Docker & Amazon ECS)
  - It has a port mapping feature to redirect to a dynamic post in Amazon ECS
  - In Classic Load Balancer we need multiple Classic Load Balancer for each application & in Application Load Balancer we need only one load balancer for all the applications.
  - Target Groups
    - EC2 instances (can be managed by an auto scaling group) - HTTP
    - ECS tasks (managed by ECS itself) - HTTP
    - Lambda functions - HTTP request is translated into a JSON event
    - IP Addresses - must be private IPs
    - ALB can route to multiple target groups
    - Health checks are at the target group level
  - ALB has fixed hostname (XXX.region.elb.amazonaws.com)
  - The application servers don't see the IP of the client directly.
    - The true IP of the client is inserted in the header X-Forwarded-For
    - We can also get Port (X-Forwarded-Port) and proto (X-Forwarded-Proto)

- Network Load Balancer (v2) (NLB)
  - Network load balancer (layer 4) allows to:
    - Forward TCP & UDP traffic to instances. It is lower level load balancer.
    - Handle millions of request per seconds, so they are extremely high performance.
    - Network latency is lower than ALB approximate 100ms compare to ALB which has network latency around 400ms
    - NLB expose one static IP per availability zone on the outside. And this is very helpful while white-listing specific IP.
    - NLB also supports elastic IPs instead of getting the ones given by the NLB itself.
    - It means we can use NLB when we want to have two entry points, i.e dedicated specific IP for the application, and then the NLB will forward that traffic to EC2 instances.
  - This is different from ALB & CLB which does not have static IP, but had a static host name.
  - Only Network Load Balancer provides both static DNS name and static IP. While, Application Load Balancer provides a static DNS name but it does NOT provide a static IP. The reason being that AWS wants your Elastic Load Balancer to be accessible using a static endpoint, even if the underlying infrastructure that AWS manages changes.
  - Use Cases:
    - When we want extremely high performance
    - Or If we want TCP or UDP layer traffic.
  - NLB is not included in the AWS free-tier
  - Target Groups
    1. EC2 instances
      - We can register EC2 instances with the target groups and then the network load balancer will know how to send traffic to instances.
    2. IP Addresses -- must be private IPs
      - We can specify fixed, static, private IP addresses, and have the NLB send traffic directly to instances.
    3. Application Load Balancer
      - It is possible to chain together a Network Load Balancer and an Application Load Balancer for leverage the feature of the NLB to have fixed static IPs.

- Gateway Load Balancer (GWLB)
  - It is used to deploy scale, and manage a fleet of 3rd party network virtual appliances in AWS.
  - Use a gateway load balancer if we want to have all traffic of the network to go through a firewall that we have, or an instrusion detection and prevention system, deep packet inspection systems, payload manipulation.
  - It operates at lower level than other load balancer that is on layer 3 which is network layer, IP Packets.
  - Gateway load balancer combines the following functions:
    - Transparent Network Gateway - Single entry/exit for all traffic
    - Load Balancer - distributes traffic to your virtual appliances
  - Uses GENEVE protocol on port 6081
  - Target Groups:
    1. EC2 instances
    2. IP Addresses

- Elastic Load Balancer (ELB)
  - Sticky Sessions (Session Affinity)
    - It is possible to implement stickiness so that the same client is always redirected to the same instance behind a load balancer.
    - This works for Classic Load Balancer & Application Load Balancers
    - The "cookie" used for stickiness has expiration date that we can control
    - Use case: make sure the user doesn't load his session data.
    - Enabling stickiness may bring imbalance to the load over the backend EC2 instances.
    - For Example:
      - Let's say we have 2 EC2 instances and a load balancer attached to it. We have 3 users who are making request. Load Balancer stickiness will take care of the each request made by the same user will always go to the same EC2 instance. It can be handled by the Session storage data and the Stickiness.
  - Sticky Session (Cookie Name)
    - There are two types of Cookie:
      1. Application based cookie
        - Custom cookie: 
          - It is a custom cookie generated by the target that means by application, and we can include any custom attributes that we require for our application.
          - The Cookie name must be specified individually for each target group
          - Must not use the names AWSALB, AWSALBAPP and AWSALBTG (reserved for used by the ELB)
        - Application Cookie:
          - It is generated by the load balancer itself.
          - Cookie name used by the ALB will be AWSALBAPP.
        - Duration for Application based cookie is specified by the application itself.
      2. Duration based cookie
        - It is the cookie generated by the load balancer.
        - Cookie name is AWSALB for ALB, AWSELB for CLB
        - It will be having a expiry based on specific duration and the duration is generated by a load balancer.

- Cross-Zone Load Balancing
  - With Cross-Zone Load Balancing each load balancer instance distributes the traffic evenly across all the registered EC2 instances in all Availability Zone.
  - Without Cross-Zone Load Balancing requests are distributed in the instances of the node of the Elastic Load Balancer.
  - For Application Load Balancer
    - Cross-Zone Balancing is always-on and we cannot disable it.
    - Usually when data goes from one Availability Zone to other Availability Zone we have to pay for it. But as in ALB Cross-Zone load balacing is always enable and we cannot disable it, so we do not have to pay for it.
  - For Network Load Balancer
    - Cross-Zone Balancing is disabled by default.
    - We can pay charges for inter Availabilty zone data transfer if we want to enable.
  - Classic Load Balancer
    - Disabled by default
    - No charges for inter Availability Zone data transfer if enabled

- SSL/TLS - Basics
  - An SSL certificate allows the traffic between your client and your load balancer to be encrypted in the transit. This is called as in-flight encryption.
  - SSL refers Secure Socket Layer, used to encrpyt the connection.
  - TLS refers Transport Layer Security and this is the newer version of the SSL.
  - Nowadays, TLS certificates are the one that are mainly used, but people mainly refers it as SSL.
  - Public SSL certificate is issued by the Certificate Authority (CA)
  - Comodo, Symantec, GoDaddy, GlobalSign, Digicert, Letsencrypt are the examples and using this public SSL certificates attach to our load balancer, we're able to encrypt the connection between the client and the load balancer.
  - SSL certificate have an expiration date which is set by us and we must renewed.
  - The Load Balancer uses an X.509 certificate (SSL/TLS certificate)
  - We can manage the certificates using ACM (AWS Certificate Manager)
  - We can create upload our own certificate alternatively
  - HTTPS listeners:
    - We must specify default certificate
    - We can add a optional list of certs to support multiple domains
    - Client can use SNI(Server Name Indication) to specify the hostname they reach
    - Ability to specify a security policy to support older versions of SSL/TLS (legacy clients)

- SNI - Server Name Indication
  - SNI solves the problem of loading multiple SSL certificates onto one web server (to serve multiple websites)
  - It's a newer protocol, and requires the client to indicate the hostname of the target server in the initial SSL handshake.
  - The server will then find the correct certificate or return the default one.
  - Note:
    - Only works with ALB, NLB & CloudFront
    - Does not work for CLB

- Elastic Load Balancers - SSL Certificates
  - Classic Load Balancer (v1)
    - Supports only one SSL certificate
    - Must use multiple CLB for multiple hostname with multiple SSL certificates
  - Application Load Balancer (v2) and Network Load Balancer
    - Supports multiple listeners with multiple SSL certificates
    - Uses server name indication (SNI) to make it work

- Connection Draining
  - Feature naming
    - Connection Draining for CLB
    - Deregistration delay for NLB & ALB
  - The idea behind this concept is that it will give some time for our instances to complete the in-flight request or the active request while the instance being in the de-register or unhealthy.
  - Once connection is being drained then the ELB stops sending request to the EC2 instance which is de-registering
  - We can parameterized the connection draining parameter between 1 to 3600 seconds (default: 300 seconds) and we can disable it by setting value 0 which means that there is no connection draining happening.
  - Set to low value if requests are short.

- Auto Scaling group (ASG)
  - In real-life, the load on our websites and application can change.
  - The goal of an Auto-Scaling Group (ASG) is to:
    - Scale out (add EC2 instances) to match the increase load
    - Scale In (remove EC2 instances) to match the decrease load
    - Ensure we have minimum and maximum number of machines running in an ASG.
    - It has feature of Automatically register new instances to a load balancer
  - ASG attributes:
    - Launch Configuration
      - Has AMI and an Instance Type
      - EC2 User data
      - EBS Volumes
      - Security Groups
      - SSH key pair
    - We also set Minimum size, Maximum size, Initial capacity as well as desired capacity.
    - We can define the networks and the subnets in which our ASG will be able to create instances
    - We can define Load Balancer Information or target group information based on which load balancer we use.
    - When we create ASG we have to define Scaling Policies, so what would trigger the Scale Out or What would trigger the scale in.
  - Auto Scaling Alarms:
    - It is possible to scale an ASG based on CloudWatch alarms
    - An alarms monitor a metric (such as Average CPU)
    - Metrics are computed for the overall ASG instances
    - Based on the alarm:
      - We can create scale-out policies (increase the number of instances)
      - We can create scale-in policies (decrease the number of instances)
  - Auto Scaling Rules:
    - It is now possible to define "better" auto scaling rules that are directly managed by EC2 instances.
    - We can add rules for,
      - Target Average CPU Usage
      - Number of requests on the ELB per instance
      - Average Network In/Out
    - These rules are easier to setup from ELB
  - Auto Scaling Custom Metric:
    - The ASG isn't tied to the metrics AWS exposes, it's also be any metric we want.
    - We can auto scale based on custom metric (ex. number of connected users)
      1. Send custom metric from the application on EC2 to CloudWatch (using PutMetric API)
      2. Create CloudWatch alarm to react to low/high values
      3. Use the CloudWatch alarm as the scaling policy for ASG
  - To update an ASG, we must provide a new launch configuration / launch template
  - IAM rules attached to an ASG will get assigned to EC2 instances
  - ASG are free. We pay for underlying resources being launched
  - Having instances under an ASG means that if they get terminated for whatever reason, the ASG will automatically create new ones as replacement.
  - ASG can terminate the instances marked as unhealthy by an Load Balancer.

- Dynamic Scaling Policy
  1. Target Tracking Scaling
    - Most simple and easy to set-up
    - Example: I want the average ASG CPU to stay at around 40%
  2. Simple / Step Scaling
    - When a CloudWatch alarm is triggered (example CPU > 70%), then increase the number of units as per requirement
    - When a CloudWatch alarm is triggered (example CPU < 30%), then remove the unit as per requirement
  3. Scheduled Actions
    - Anticipate a scaling based on known usage patterns
    - Example: Increase the min capacity to 10 to 5pm on Fridays

- Predictive Scaling Policy
  - Continuosly forecast the load and schedule scaling ahead
  - That means, the historical load is going to be analyze over time and then a forecast is going to be created. And then based on that forecast, there will be scaling actions being scheduled ahead of time. Which is a quite a good way to scaling.

- Good metrics to Scale On
  1. CPU Utilization: Average CPU utilization across the instances
  2. RequestCountPerTarget: to make sure that number of requests per EC2 instances is stable
  3. Average Network In/Out (If application is network bound)
  4. Any Custom Metric (that we push using CloudWatch)
  - and based on above metrics we can setup our scaling policies.

- Scaling Cooldown
  - After a scaling activity happens, we are in a cooldown period (default 300 seconds)
  - During the cooldown period, the ASG will not launch or terminate additional instances (to allow for metrics to stabilize)
  - Always use ready-to-use AMI to reduce configuration time in order to be serving request fasters and reduce the cooldown period.

- Hands On
  - Create a dynamic auto scaling policy with Target value = 40
  - Run below commands to increase the CPU utilization
  ```
  sudo amazon-linux-extras install epel -y
  sudo yum install stress -y
  stress -c 4
  ```

Q. You are using an Application Load Balancer to distribute traffic to your website hosted on EC2 instances. It turns out that your website only sees traffic coming from private IPv4 addresses which are in fact your Application Load Balancer's IP addresses. What should you do to get the IP address of clients connected to your website?
  - When using an Application Load Balancer to distribute traffic to your EC2 instances, the IP address you'll receive requests from will be the ALB's private IP addresses. To get the client's IP address, ALB adds an additional header called X-Forwarded-For contains the client's IP address.

Q. You hosted an application on a set of EC2 instances fronted by an Elastic Load Balancer. A week later, users begin complaining that sometimes the application just doesn't work. You investigate the issue and found that some EC2 instances crash from time to time. What should you do to protect users from connecting to the EC2 instances that are crashing?
  - Enable ELB Health Checks, because When you enable ELB Health Checks, your ELB won't send traffic to unhealthy (crashed) EC2 instances.

# Section 8: AWS Fundamentals: RDS + Aurora + ElastiCache

- Amazon RDS
  - RDS stands for Relational Database Service
  - It's a managed DB service for DB use SQL as a query language
  - It allows to create databases in the cloud that are managed by the AWS
  - Types of database managed by AWS
    1. Postgres
    2. MySQL
    3. MariaDB
    4. Oracle
    5. Microsoft SQL Server
    6. Aurora (AWS Proprietary database)
  
  - Advantage over using RDS versus deploying DB on EC2
    - RDS is a managed service and as such AWS provides a lot of services on top of just giving us a database. For Example,
      - The provisioning of the database is fully automated and so is the underlying operating system patching.
      - Continuous backups being made and we can restore to specific timestamp
      - We can have Monitoring Dashboards to view performance of the database
      - We can have read replicas for improved read performance
      - We can setup multiple Availability Zones that will be helpful for disaster recovery
      - We can have maintenance windows for upgrades
      - And we can have both vertical & horizontal scaling capacity
      - Storage is backed by EBS (gp2 or io1)
      - We cannot do SSH to database RDS instances because it is a managed service AWS provides us a service, and we don't have access to the underlying EC2 instances

  - RDS backups
    - Backups are automatically enabled in the RDS
    - Automated backups:
      - Daily full backups of the database (during the maintenance window)
      - Transaction logs are backed-up by RDS every 5 minutes
      - It gives the ability to restore any point backup (from oldest to 5 mins ago)
      - There is 7 days retention for this automatic backup by default and it can be increased to 35 days
    - DB Snapshots: Snapshots are slightly different from the database backups
      - Snapshots are the backups that are manually triggered by the user
      - Snapshot retention can be as long as we want

  - RDS - Storage Auto Scaling
    - Helps to increase storage on the RDS database instance dynamically.
    - When RDS detects that database instance is running out of the free database storage, it will automatically increase the storage size.
    - Avoid manually scaling the database storage
    - We have to set maximum storage threshold (maximum limit for DB storage)
    - Automatically modify storage if:
      - Free storage is less than 10% allocated storage
      - Low-storage lasts atleast 5 minutes
      - 6 hours have passed since last modification
    - Useful for applications with unpredictable workloads
    - Supports all RDS database engines (MariaDB, MySQL, PostgreSQL, SQL Server, Oracle)

  - RDS Read Replicas vs Multi Availability Zones
    - Read replicas as name indicates helps to scale your reads
    - We can add upto 5 read replicas
    - Within Availabilty Zone, Cross Availabilty Zone, or Cross Region
    - Replication is async, so read are eventually consistent
    - Replicas can be promoted to their own DB
    - Applications must update the connection string to leverage read replicas
    - Use case:
      - You have a production database that is taking on normal load
      - You want to load a reporting application to run some analytics
      - You create a new replica for that RDS database. As running other application on the same database will cause the main application slower down because of increasing in the load on the main database.
      - Creating a new replica will sync with the main database and the other application can run on the replica without affecting the production application
      - Read replicas are used for SELECT (read) only kind of statements (not INSERT, UPDATE and DELETE)
    - Network Cost:
      - We have to pay for data transfer in AWS if data is transferring from one Availabilty Zone to another except for managed services.
      - RDS is a managed services and for RDS read replicas within same region, we don't have to pay.
      - But if we are using cross region replica, then will have replication that will go across regions and this will incur a replication fee for the network.
    - From Single - AZ to Multi - AZ
      - Zero downtime operation (no need to stop the DB)
      - The following things happen internally:
        - A snapshot is taken
        - A new DB is restored from the snapshot in a new Availabilty Zone
        - Synchronisation is established between the two databases.
  
  - RDS Security
    - Encryption
      - At-rest encryption
        - Possibility to encrypt the master & read replicas with AWS KMS - AES-256 encryption
        - Encryption has to be defined at launch time
        - If the master is not encrypted, the read replicas cannot be encrypted
        - Transparent Data Encryption (TDE) available for Oracle and SQL Server
      - In-flight encryption
        - SSL certificates to encrypt data to RDS in flight
        - Provide SSL option with trust certificate when connecting to database
        - To enforce SSL:
          - PostgreSQL: Need to set Parameter Groups rds.force_ssl=1 in the AWS RDS console
          - MySQL: Within the DB need to run command ` GRANT USAGE ON *.* TO 'mysqluser'@'%' REQUIRE SSL;`
    
    - RDS Encryption Operations
      - Encrypting RDS backups:
        - Snapshots of un-encrypted RDS databases are un-encrypted
        - Snapshots of encrypted RDS databases are encrypted
        - Can copy a snapshot into an encrypted one
      - To Encrypt an un-encrypted RDS database:
        - Create a snapshot of the un-encrypted database
        - Copy the snapshot and enable encryption for the snapshot
        - Restore the database from the ecrypted snapshot
        - Migrate application to the encrypted new database and delete the old un-encrypted database.
    
    - Network & IAM
      - Network Security
        - RDS databases are usually deployed with private subnet, not in a public one
        - RDS security works by leveraging security groups (the same concept as for EC2 instances) - it controls which IP / security group can communicate with RDS
      - Access Management
        - IAM policies help control who can manage AWS RDS (through RDS API)
        - Traditional Username & Password can be used to login into the database
        - IAM-based authentication can be used to login into RDS MySQL & PostgreSQL
    
    - IAM Authentication
      - IAM database authentication works with MySQL and PostgreSQL
      - We don't need a password, just an authentication token obtained through IAM & RDS API calls
      - Auth token has a lifetime of 15 mins
      - Benefits:
        - Network in/out must be encrypted using SSL
        - IAM to centrally manage users instead of DB
        - Can leverage IAM Roles and EC2 Instance profiles for easy integration
  
  - Amazon Aurora
    - Aurora is a proprietary technology from AWS (not open sourced)
    - Postgres and MySQL are both supported as Aurora DB (that means drivers will work as if Aurora was a Postgres or MySQL database)
    - Aurora is "AWS cloud optimized" and claims 5x preformance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS
    - Aurora storage automatically grows in increments of 10GB, up to 64TB
    - Aurora can have 15 replicas while MySQL has 5, and the replication process is faster (sub 10ms replica lag)
    - Failover in AUrora is instantaneous. It's High Availability native.
    - Aurora costs more than RDS (20% more) - but is more efficient
    - Aurora High Availability and Read Scaling
      - It has 6 copies of the data across 3 Availabilty Zones:
        - It needs 4 copies out of 6 for writes
        - It needs 3 copies out of 6 for reads
        - It has self-healing process which is that if some data is corrupted or bad, then it does self-healing with peer-to-peer replication in the backend.
        - We can rely on 100s of storage volumes
      - One Aurora instance takes writes i.e master
      - It has automated failover for master in less than 30 seconds
      - Master + up to 15 Aurora Read replicas serve reads
      - It supports Cross Region Replication
    - Aurora DB cluster
      - Master will be the only thing that will writes to the storage. And because the master can change in the failover Aurora provides a Writer Endpoint.
      - Writer Endpoint is the DNS name and it always points to the master. If the master fails in the failover still client talks to it and it automatically redirected to the right instance.
      - There are multiple read replicas, and we have auto-scaling out of all these read replicas. So, we can have 1 up to 15 read replicas and we can setup auto-scaling such as we can have right number of read replicas.
      - To track all these read replicas, we have Reader Endpoint. It helps with connection load balancing, and it connects automatically to all the read replicas.
      - So anytime client connects to the reader endpoint, it will get connected to one of the read replicas and there will be load balancing. Load balancing happens at the connection level, not the statement level.
    - Aurora Features
      - Automatic fail-over
      - Backup and Recovery
      - Isolation and security
      - Industry compliance
      - Push-button scaling
      - Automated patching with Zero Downtime
      - Advanced Monitoring
      - Routine Maintenance
      - Backtrack: restore data at any point of time without using backups
    - Aurora Security
      - It has similar security ro RDS because it uses the same engines
      - Encryption at rest using KMS
      - Automated backups, snapshots and replicas are also encrypted
      - Encryption in flight using SSL (same process as MySQL or Postgres)
      - Possibility to authenticate using IAM token (same method as RDS)
      - We are responsible for protecting the instance with security groups
      - We can't SSH

  - Amazon ElastiCache
    - Overview:
      - The way we get RDS to have managed Relational Databases, ElastiCache hepls to get managed Redis or Memcached which are cache technologies.
      - Caches are in-memory databases with really high performance and low latency.
      - Caches helps to reduce load off of the databases for read intensive workloads
      - Cache helps application to be stateless by putting the state of the application into Amazon ElastiCache.
      - AWS takes care of OS maintenance / patching, optimizations, setupm configuration, monitoring, failure recovery and backups
      - Using ElastiCache involves heavy application code changes
    - ElastiCache Solution Architecture - DB Cache
      - The application will make queries to the ElastiCache. If query is aleady made and it is already stored in the ElastiCache then it's called cache hit.
      - In case if data is not present in the ElastiCache then the query directly reads from the database.
      - It helps to relieve load in RDS database
      - There is cache invalidation strategy to make sure only the most current data is used in there.
    - ElastiCache Solution Architecture - User Session Store
      - User logs into any of the application and the application writes the session data into ElastiCache
      - The user hits another instance of the application
      - The instance retrieves the data and the user is logged in
      - By this we can make our application stateless by writing the session data of the user into Amazon ElastiCache.
    - ElastiCache - Redis vs Memcached
    ```
                    REDIS                                         MEMCACHED
          1. Multi AZ with Auto-Failover                  1. Multi-node for partitioning of data (sharding)
          2. Read replicas to scale reads and have        2. No high availabilty (replication)
          high availability
          3. Data Durability using AOF persistence        3. Non persistent
          4. Backup and restore feature                   4. No backup and restore, Multi-threaded architecture
    ```
  
    - Caching Implementation Considerations
      1. Read about it more on: https://aws.amazon.com/caching/
      2. Is it safe to cache data?
        - Yes, but data may be out of date so you may have eventually consistent.
      3. Is caching effective for that data?
        - Yes if data changing slowly, and few keys are frequently needed.
        - It is not effective if data changing rapidly, and all large key space frequently needed
      4. Is data structured well for caching?
        - If the data is in key value pair and properly organized then it will be a proper structured data and requires less time to execute queries.
      5. Which caching design pattern is the most appropriate?
        1. Lazy Loading / Cache-Aside / Lazy Population
          - An application first make the request to the Amazon ElastiCache. If the data found then that is called as Cache hit. If data not found in ElastiCache then that is called as Cache miss. And in this case application read data from the database and one write operation is done on the backend to store the data to ElastiCache.
            - Pros:
              1. Only requested data is cached (The cache isn't filled up with unused data)
              2. Node failures are not fatal (just increased latency to warm the cache)
            - Cons:
              - If cache miss occurs then that results in 3 round trips, noticeable delay for that request. Because first round to check data in ElastiCache, second round to read data from the database and third round for writing the data in ElastiCache.
              - Data can be updated in the database and outdated in the cache.
        2. Write Through - Add or update cache when database is updated
          - When cache miss happens then data which is going to update in the database is also updates in the ElastiCache. That is why it is called the Write Through
          - Pros:
            1. Data in cache is never stale, reads are quick
            2. Each write requires 2 calls, one for writing in the database and another call for writing in the ElastiCache. It means writing the data in the database may take longer time than reading the data.
          - Cons:
            1. Missing Data until it is added/updated in the Database. Mitigation is to implement Lazy Loading strategy as well
            2. Cache churn - a lot of the data will never be read. So it will create problem if cache is very small.
    
    - Cache Evictions and Time-to-live (TTL)
      - Cache eviction can occur in three ways:
        - You can delete the item explicitly in the cache
        - Items is evicted because the memory is gull and it's not recently used i.e Least Recently Used
        - We can set an item time-to-live which will set a time for the cache and that can be removed after specific setted time
      - TTL are helpful for any kind of data like,
        - Leaderboards
        - Comments
        - Activity streams
      - TTL can range from few seconds to hours or days
      - If too many evictions happen due to memory, then we should scale up or out
    
    - Summary
      1. Lazy Loading / Cache aside is easy to implement and works for many situations as a foundation, especially on the read side.
      2. Write-through is usually combined with lazy loading as targeted for the queries or workloads that benefit from this optimization
      3. Setting a TTL is usually not a bad idea, except when you're using Write-through. Set it to a sensible value for the application
      4. Only cache the data that makes sense (user profiles, blogs etc)
      ` Quote: There are only two hard things in Computer Science: cache invalidation and naming things `
    
    - ElastiCache Replication
      1. Cluster Mode Disabled
        - It has one primary node and can have up to 5 replicas cache node
        - The replication is asynchronous between the caches
        - The primary node is used for read/write
        - The other nodes are read-only. So in disaster recovery we can enable other read replicas of ElastiCache for Redis.
        - We have one shard so all the nodes have all the data will in the same redis cluster.
        - Guarding against the data loss if there is node failures. And we can also enable multi AZ it is enabled by default in case we don't have multi AZ failover.
      2. Cluster Mode Enabled
        - Data is partitioned across all the shards
        - Each shard has a primary and up to 5 replica nodes
        - Muti-AZ capability
        - Up to 500 nodes per cluster:
          - 500 shards with single master, that means if we don't set any replicas then we will have 500 shards with single master
          - 250 shards with 1 master and 1 replica
          - 83 shards with one master and 5 replicas

# Section 9: Route 53

- DNS
  - DNS is Domain Name System which translates the human friendly hostnames into machine IP addresses
  - For example: www.google.com => 172.217.18.36
  - DNS is the backbone of the internet
  - DNS uses hierarchical naming structure- .com, example.com, www.example.com, api.example.com

- DNS Terminology
  - DNS Registrar: Amazon Route 53, GoDaddy etc
  - DNS Records: A, AAAA, CNAME, NS etc
  - Zone File: contains DNS records
  - Name Server: resolves DNS queries (Authoritative or Non-Authoritative)
  - Top Level Domain (TLD): .com, .us, .in, .gov, .org etc
  - Second Level Domain (SLD): amazon.com, google.com etc

- Route 53
  - Overview:
    - A highly available, scalable, fully managed and Authoritative DNS
      1. Authoritative = the customer can update the DNS records
    - Route 53 is also a Domain Registrar
    - Ability to check the health of the resources
    - The only AWS service which provides 100% availability SLA
    - Why Route 53? 53 referencee to traditional DNS port used by DNS services
  
  - Route 53 - Records
    - In Route 53 we are going to define a bunch of DNS records and the records define how we want to route traffic to a specific domain
    - Each record contains:
      1. Domain/subdomain name - e.g. example.com
      2. Record Type - e.g. A or AAAA
      3. Value - e.g. 12.34.56.78
      4. Routing Policy - how Route 53 responds to queries
      5. TTL - amount of time the record cached at DNS resolvers
    - Route 53 supports the following DNS record types:
      1. (must know) A / AAAA / CNAME / NS
      2. (advanced) CAA / DS / MX / NAPTR / PTR / SOA / TXT / SPF / SRV
  
  - Route 53 - Record Types
    1. A - maps a hostname to IPv4
    2. AAAA - maps a hostname to IPv6
    3. CNAME - maps a hostname to another hostname
      - The target is a domain name which must have an A or AAAA record
      - Can't create a CNAME record for the top node of a DNS namespace (Zone Apex)
      - Example: you can't create for example.com, but you can create for www.example.com
    4. NS - Name Servers for the Hosted Zones
      - Control how traffic is routed for domain
  
  - Route 53 - Hosted Zones
    - A container for records that define how to route traffic to a domain and its subdomains
    - Public Hosted Zones - contains records that specify how to route traffic on the internet (public domain names) e.g. application1.mypublicdomain.com
    - Private Hosted Zones - contain records that specify how you route traffic within one or more VPCs (private domain names)
      - e.g application1.company.internal
      - We have seen that some URL's are only accessible through the office network are in the pricate domain names
    - We pay $0.40 per month per hosted zone & $12 per year

  - Route 53 - Records TTL (Time to Live)
    - A client sends the DNS request to Route 53 to get the record for the requested DNS. The response from the Route 53 will the requested record with TTL. TTL is cached and until the TTL is not expired client use same cached record received from Route 53 for HTTP Request & Response to Web Server.
    - Caching the DNS records will reduce the traffic from the Route 53.
    - Keeping high TTL value e.g. 24 hrs
      - Results low traffic on Route 53
      - Possibility of outdated records
    - Keeping low TTL value e.g. 60sec
      - Results more traffic on Route 53 ending up on more cost
      - Records are outdated for less time
      - Easy to change records
    - TTL is mandatory for each DNS records except the Alias records
  
  - Route 53 - CNAME vs Alias
    - AWS Resources like Load Balancer or CloudFront exposes the hostname and to map those hostname to domain we own (e.g myapp.domain.com). For this we have two options:
      1. CNAME Records
        - CNAME allows us to point a hostname to any other hostname (e.g. app.mydomain.com => blabla.anything.com)
        - It only works when we have non root domain name. e.g. If we have "aka.something.mydomain.com" it will not work with "mydomain.com" domain.
      2. Alias Records
        - It is specific to Route 53
        - It allows us to point a hostname to a specific AWS resource (e.g app.mydomain.com => blabla.amazonaws.com)
        - It works with both root domain and non root domain name (e.g. we have mydomain.com which can be work with any mydomain.com with any alias)
        - It is Free of charge
        - It has native health check capability
  
  - Route 53 - Alias Records
    - It maps the hostname to AWS resources
    - It is an extension to DNS functionality
    - Automatically rrecognizes changes in the resource's IP addresses
    - Unlike CNAME, it can be used for the top node of a DNS namespace
    - Alias records is always of type A/AAAA for AWS resources (IPv4 / IPv6)
    - TTL is set automatically by Route 53, alias records does not set TTL
    - Records Targets:
      1. Elastic Load Balancers
      2. CloudFront Distributions
      3. API Gateway
      4. ELastic Beanstalk environments
      5. S3 Websites
      6. VPC interface endpoints
      7. Global Accelerator accelerator
      8. Route 53 record in the same hosted zone
    - We cannot set an ALIAS record for an EC2 DNS name
  
  - Route 53 - Routing Policies
    - Routing policy is helps to respond to the DNS queries
    - DNS does not route any traffic, it only responds to the DNS queries
    - Route 53 supports the following Routing Policies
      1. Simple
        - Typically, route traffic to a single resource
        - Can specify multiple values in the same record
        - If multiple values are returned by the DNS then a random one is chosen by the client or in the client-side
        - If we have enabled Alias in the simple policy then we can only specify one AWS resource as a target
        - Can't be associated with Health Checks
      2. Weighted
        - We can control some % of the request that go to specific resource
        - We have to assign relative weight to each record and then the traffic percentage is going to be send to each record, as just the weight of the record divided by the sum of all the weights of all the records and it will give the traffic percentage.
            ```
            traffic (%) = Weight for a specific record / Sum of all the weights for all records
            ```
        - Weights don't need to sum up to 100, they're just indicative of how much we want to send to the instance compared to all the other records in the DNS name.
        - DNS records must have the same name and type
        - Can be associated with Health Checks
        - Use Cases: Load balancing between regions, testing new application versions and so on
        - Assign a weight of 0 to record to stop sending traffic to a resource
        - If all records have weight of 0, then all records will be returned equally to the instance
      3. Failover
        - Let's say we have two EC2 instances one is primary instance and secondary instance for disaster recovery. Route 53 mandatorily do health checks on the primary instance by default and hence if the response for health check comes unhealthy from the primary instance it will switch to secondary instance and send response to the DNS server from secondary instance.
        - When Client sends the DNS requests Route 53 will give response only from the healthier EC2 instance.
      4. Latency based
        - Redirect to the resource that has the east latency close to the user
        - Super helpful when latency for users is a priority
        - Latency is based on traffic between users and AWS Regions
        - Germany users may be directed to the US (if that's the lowest latency)
        - Can be associated with Health Checks (has a failover capability)
      5. Geolocation
        - Different from latency-based policy
        - This is based on where the user is actually located
        - We have to create a default record for the case if no IP is matched for the location of the user
        - Use cases: website localization, restrict content distribution, load balancing
        - Can be associated with the Health Checks
        - e.g. If a user from the Germany requests then it will get response IP address which is associated with Germany and if the user requests from France then it will get response IP of France. But if there is no match found for the user's location in Route 53 then the default one which is set by us will sends as a response to the user.
      6. Multi-Value answer
        - This is going to be used when we want to route traffic to multiple resources and hence Route 53 will return multiple values and resources
        - Can be associated with Health Checks (return only values for healthy resources)
        - Up to 8 healthy records are returned for each Multi-Value query
      7. Geoproximity (using Route 53 Traffic Flow feature)
        - It is very useful when we want to shift the traffic from one region to another region by increasing the bias value.
        - It allows route traffic to resources based on the geographic location of users and resources
        - By this idea we can able to use a number called bias to shift more traffic to resources based on specific location
        - To change the size of the geographic region, we need to specify the bias value
          - To increase the traffic we can expand the bias value between 1 to 99 - more traffic to the resource
          - To decrease the traffic we can shrink the bias value to the negative number between -1 to -99 - less traffic to the resource
        - Resources can be:
          1. Resources from the AWS, need to specify the AWS region for calculating the correct routing
          2. resources can be Non-AWS, such as on premises data center then need to specify the latitude and longitude, so the AWS knows where they are right now.
        - Must use Route 53 Traffic Flow (advanced) to use this feature
  
  - Route 53 - Health Checks
    - Health Checks are the way to check the health of mainly public resources
    - Health Check => Automated DNS Failover:
      1. Health checks that monitor an endpoint which is the public endpoint (It could be an Application, server, other AWS resource)
        - About 15 global health checkers will check the endpoint health
          - We can set a threshold for Healthy / Unhealthy - 3 is default value
          - We can set interval of regular health checks. It could be 30 seconds or every 10 seconds, which is higher in the cost, which is called fast health check.
          - It supports multiple protocols: HTTP, HTTPS and TCP
          - The rule is if more than 18% of health checkers report the endpoint is healthy then Route 53 considers it Healthy. Otherwise, it's unhealthy.
          - We have ability to choose which locations we want Route 53 to use health checks
        - Health Checks pass only when the endpoint responds with the 2XX and 3XX status codes from the load balancer
        - Health Checks can be setup to pass / fail based on the text in the first 5120 bytes of the response from the load balancer to look for the specific text in the response itself.
        - Configure the router/firewall to allow incoming requests from Route 53 Health Checkers
      2. Health Checks that monitor other health checks also called as Calculated Health Checks
        - If we have 3 EC2 instances, then we can create three health checks for each in the Route 53 and this health checks are called as Child Health Check and they all can monitor each EC2 instance one-by-one.
        - Combine the results of the multiple Health Checks into a single Health Check and we can define the parent health check which will define all the child health checks
        - Conditions to combine all the child health checks could be an OR, AND, or a NOT
        - We can monitor up to 256 child health checks
        - We can specify how many of the health checks need to pass to make the parent pass
        - Use case: If we want to have a parent health check to perform maintenance on website without causing all the health checks to fail
      3. Heath Checks that monitor CloudWatch Alarms which gives us more control and is helpful for private resources
        - Route 53 health checkers are outside the VPC
        - They can't access private endpoints (private VPC or on-premises resource)
        - Use case: Create a CloudWatch metric and associate a CloudWatch Alaem, then create a Health Check that checks the alarm itself. So by this we can monitor the health of the EC2 instance in private subnet with a CloudWatch metric and then if the metric is breached, then CloudWatch alarm which we have created goes into alarm state and health checker is going to be automatically unhealthy.
    - Health Checks are integrated with CloudWatch metrics
  
  - Route 53 - Traffic flow
    - We can create this complex geoproximity records using a feature called as Traffic flow.
    - This is not only applys to Geoproximity but applys to everything.
    - We have a visual editor to manage complex routing decision trees.
    - Geoproximity rule configurations can be saved as Traffic Flow Policy
      - Can be applied to different Route 53 Hosted Zones (different domain names)
      - We can add multiple domain names with versions - Supports versioning

  - 3rd Party Registrar with Amazon Route 53
    - If we buy our domain on a 3rd party registrar, we can still use Route 53 as the DNS Service provider
    - Steps:
      1. Create a Hosted Zone in Route 53
      2. Update Name Server Records on 3rd party website to use Route 53 Name servers
        - For this create a public Hosted Zone on AWS Route 53 and copy the Name servers from Route 53 to our 3rd party name server (e.g. GoDaddy)
    - Domain registrar is not a DNS service
    - But every Domain Registrar usually comes with some DNS features

# Section 10: VPC Fundamentals

- VPC
  - Stands for Virtual Private Cloud
  - In AWS Certified Developer Level following points are important:
    1. VPC, Subnets, Internet Gateways & NAT Gateways
    2. Security Groups, Network ACL (NACL), VPC Flow Logs
    3. VPC Peering, VPC Endpoints
    4. Site to Site VPN & Direct Connect
  
  - VPC & Subnets
    - VPC is the private network in AWS cloud which allows us to deploy resources within it. And VPC is a regional resource
    - If we have two different AWS regions then we have two different VPC's
    - Inside VPC we have subnets. Subnets allow us to partition our network inside our VPC. And subnets are defined at the availability zone level
    - A public subnet is the subnet that is accessible from the internet. This subnet can access world wide web and can be access in world wide web
    - A private subnet is a subnet which is not accessible through the internet.
    - To define access to the internet and between the subnets, we use Route Tables.
    - VPC has number of IP ranges which is called as CIDR Range
    - We have one public subnets per AZ and we have one VPC in each and every region that's created for us. It's called default VPC.
    - Subnets are tied to a specific AZ and this is where we have been launching our EC2 instances and they represent the network partition of the VPC.
  
  - Internet Gateway & NAT Gateways
    - Internet Gateways helps our VPC instances connect with the internet
    - Public Subnets have a route to the internet gateway
    - NAT Gateways (AWS-managed) & NAT instances (self-managed) allow instances in the Private subnets to access the internet while remaining private
  
  - Network ACL & Security Groups
    - NACL (Network ACL)
      1. It is the first mechanism of defence of our public subnet and at the subnet levels
      2. Before the network traffic reaches to EC2 instance it has to go through Network ACL
      3. It is the firewall which controls traffic from and to subnet
      4. It can have ALLOW and DENY rules
      5. It is attached at the Subnet level
      6. It will allow only those IP addessed which are registered in the Rules
    - Security Groups
      1. Security groups are the firewall that controls traffic to and from an Elastic Network Interface(ENI) or an EC2 Instance
      2. It can have only ALLOW rules
      3. It will allow Rules which are includes for IP addresses and other security groups as well
      4. Security groups are stateful and if traffic can go out, then it can go back in.

  ```
                        Security Groups                                                         Network ACL
          1. Operates at the instance level                                       1. Operates at the subnet level
          2. Supports allow rules only                                            2. Supports allow rules and deny rules
          3. Is stateful: Return traffic is automatically allowed,                3. Is stateless: Return traffic must be explicitly allowed by
          regardless of any rules                                                     rules
          4. We evaluate all rules before deciding whether to allow               4. We process rules in number order when deciding whether to allow
          traffic                                                                     traffic
          5. Applies to an instance only if someone specifies the                 5. Automatically applies to all instances in the subnets it's associated
          security group when launching the instance, or associates the             with (therefore, you don't have to rely on the users to specify the
          security group with the instance later on                                 security group)
  ```

  - VPC Flow Logs
    - This capture all the information about IP traffic going into the interfaces that includes,
      - VPC Flow Logs
        - anytime network going through VPC it would be logged in a Flow Log
        - It will give all the allowed and denied traffic logs
      - Subnet Flow Logs
      - Elastic Network Interface Flow Logs
    - This is to help in monitoring and troubleshooting connectivity issues.
    - e.g. Why subnets are not talking to the internet? Or Why subnets are not talking to other subnets? Or Why Internet is not talking to the subnet? etc
    - It will capture all the network information from the AWS managed interfaces too: Elastic Load Balancers, ElastiCache, RDS, Aurora, etc
    - VPC Flow Logs data can go to S3 / CloudWatch Logs
  
  - VPC Peering
    - It connects to VPC privately using AWS network virtually
    - VPC Peering make all the VPC behave as if they were in the same network
    - If we want to talk two different VPC in the network then we need to establish a VPC peering connection from one VPC to Another VPC
    - Let's say we have two VPC's A & B and if we want to connect both the VPC's we need to create VPC peering between A to B.
    - Let's say we have a third VPC called C, and we have established connection between A to C for the communication. But here in this case VPC B & VPC C will not communicate each other as there is no connection between B & C. For this we need to create a connection between B & C and they can able to connect
    - We have to make sure that IP ranges that is defined for each VPC are not overlapping CIDR.
    - VPC Peering connection is not trasitive, so it is must be established for each VPC that needs to communicate with one another.
  
  - VPC Endpoints
    - Endpoints allow us to connect to AWS services using a private network instead of the public internet network.
    - All the AWS services are public, so they publically access the internet.
    - This gives us Enhanced security and lower latency to access AWS services
    - If we want to access the database S3 / DynamoDB (which are in the public network) privately then we need VPC Endpoint Gateway.
    - Example for VPC Endpoint Interface (which is used only within VPC) is CloudWatch
  
  - Site to Site VPN & Direct Connect
    - To connect on-premises datacenter and the VPC following are the methods which can be used,
      1. Site to Site VPN
        - Connect an on-premises VPN to AWS services
        - The connection is automatically encrypted
        - Goes over the public internet
      2. Direct Connect (DX)
        - Establish a physical connection between the on-premises and AWS services
        - The connection is private, secure and fast
        - It goes over a private network
        - Takes at least a month to establish
    - Note: Site-to-Site VPN and Direct Connect cannot access VPC endpoints. Because VPC Endpoints are just to access AWS services privately within the VPC not by connecting to on-premises data center

# Section 11: Amazon S3 Introduction

  - Amazon S3 allows people to store objects (files) in buckets (directories)
  - Buckets
    - Buckets are defined at the region level
    - Buckets must have a globally unique name
    - Naming Convention: No uppercase, No underscore, 2-63 characters long, Not an IP, Must start with lowercase letter or number

  - Objects
    - Objects are files and they must have a key
    - Key is the Full path of that file
      - e.g. s3://my-bucket/my_file.txt   =>  Here the key is "my_file.txt"
      - e.g. s3://my-bucket/my_folder1/another_folder/my_file.txt   =>  Here the key is "my_folder1/another_folder/my_file.txt"
    - The key is composed of prefix + object name
      - s3://my-bucket/my_folder1/another_folder/my_file.txt
        - prefix: my_folder1/another_folder/
        - object name: my_file.txt
    - S3 Object values are the content of the body
      - Maximum object size is 5TB (~5000GB)
      - We can upload 5GB at once. If uploading more than 5GB then must use "multi-part upload"
    - Each values in the S3 bucket has Metadata, list of key-value pairs that could be system or user metadata.
    - We can have Tags which is useful when we don't have security on the objects or lifecycle policies

  - Versioning
    - The files in the Amazon S3 can be versioned but that has to be enable first at bucket level
    - If we try to upload file in the Amazon S3 with the same key overwrite will increment the version
    - It is best practice to version the S3 buckets. Because,
      - Protect against unintended deletes (we can restore the previous version file)
      - Easy roll back to previous version
    - Notes:
      - Any file that is not versioned prior to enabling versioning will have version "null"
      - Suspending versioning does not delete the previous versions
  
  - S3 Encryption for Objects
    - There are 4 methods of encrypting objects in S3
      1. SSE-S3 (Server Side Encryption - S3)
        - Encrypts S3 objects using keys handled & managed by AWS
        - This is the encryption where the keys used to encrypt the data are handled and managed by Amazon S3
        - The object is going to be encrypted at server side
        - It uses AES-256 encryption type
        - For uploading any file to S3 we must set header called "x-amz-server-side-encryption":"AES-256", where "x-amz" stands for X Amazon
      2. SSE-KMS (Server Side Encryption - Key Management System)
        - Leverage AWS Key Management Service to manage encryption keys
        - When you have your encryption keys that are handled and managed by the KMS service
        - Advantage: It will give full access to the keys and also gives an audit trail
        - Each object is going to be encrypted at server side
        - For uploading any file to S3 we must set header called "x-amz-server-side-encryption":"AES-KMS", where "x-amz" stands for X Amazon
      3. SSE-C (Server Side Encryption - C)
        - When we want to manage our own encryption keys
        - This is the encryption where it encrypts the data using the keys that we provide to ourself outside of AWS
        - Amazon S3 does not store the encryption key that we provide
        - For transmit the data into AWS we must use HTTPS
        - Encryption key must provided in HTTP headers, for every HTTP request made
      4. Client Side Encryption
        - We upload the object before uploading to Amazon S3
        - We can use client library such as the Amazon S3 Encryption Client for encrpting the files before upload to S3
        - Client must encrpt data themselves before sending to S3
        - Client must decrypt data themselves when retrieving from S3
        - Customer fully manages the keys and encryption cycle

  - Encryption in transit (SSL/TLS)
    - Amazon S3 is a HTTP service that exposes HTTP endpoints which is non-encrypted
    - It exposes HTTPS endpoint which is encrypted and provide encryption in flight which relies on SSL & TLS certificates
    - We can use any HTTP or HTTPS but HTTPS is recommended
    - Most clients use the HTTPS endpoint by default
    - If we are using SSE-C and the key is provided by the client then HTTPS is mandatory
    - Encryption in flight is also called as SSL/TLS, because it uses SSL/TLS certificates.
  
  - S3 Security
    1. User Based
      - IAM policies - which API calls should be allowed for a specific user from IAM console
    2. Resource Based
      - Bucket Policies - bucket wide rules from the S3 console - allows cross account
      - Object Access Control List (ACL) - finer grain
      - Bucket Access Control List (ACL) - less common
    - Note: an IAM pricipal can access an S3 object if,
      - the user IAM permissions allow it OR the resource policy ALLOWS it
      - AND there's no explicit deny from the resource policy
  
  - S3 Bucket Policies
    - JSON based policies
      - Resources: buckets and objects
      - Actions: Set of API to Allow or Deny
      - Effect: Allow/Deny
      - Principal: The account or user to apply the policy to
    - Use S3 bucket for policy to:
      - Grant public access to the bucket
      - Force objects to be encrypted at upload
      - Grant access to another account (Cross account)
  
  - Bucket settings for Block Public Access
    - This is the setting that is created to block objects from being public if the account had some restrictions
    - We have 4 different Block Public Access settings,
      1. new access control list (ACL)
      2. any access control list (ACL)
      3. new public bucket
      4. access point policies
    - Block public and cross-account access to buckets and objects through any public bucket or access point policies
    - These settings were created to prevent company data leaks
    - If we know our bucket should never be public, leave these setting on
    - It can be set at the account level
  
  - S3 Security - Other
    - Networking
      - Supports VPC Endpoints (for instance in VPC without internet)
    - Logging and Audit
      - S3 access logs can be stored in other S3 bucket
      - API calls can be logged in AWS CloudTrail
    - User Security
      - MFA Delete: MFA (multi factor authentication) can be required in versioned buckets to delete objects
      - Pre-signed URLs: URLs that are valid only for a limited time (e.g. premium video service for logged in users)
  
  - https://docs.aws.amazon.com/AmazonS3/latest/userguide/example-bucket-policies.html
  - For generating the encryption policy - https://awspolicygen.s3.amazonaws.com/policygen.html
  - https://aws.amazon.com/blogs/security/how-to-prevent-uploads-of-unencrypted-objects-to-amazon-s3/

  - S3 Websites
    - S3 can host static websites and have them accessible on the internet
    - The website URL will be <bucket-name>.s3-website-<AWS-region>.amazonaws.com OR <bucket-name>.s3-website.<AWS-region>.amazonaws.com
    - If we get the a 403 (Forbidden) error, make sure the bucket policy allows public reads!

  - CORS (Cross Origin Resource Sharing)
    - It means we want to get resources from a different origin
    - Q. What is an origin?
      - An origin is a scheme (protocol), host (domain) and port
      - e.g. https://www.example.com
        - This is an origin where the scheme is HTTPS
        - the host is www.example.com
        - and port is 443
    - The web browser are having this security in place CORS basically saying as soon as we visit a website, we can make request to other origins only if the other origins allow us to make these request. This is a browser based security
    - Same origin: http://example.com/app1 & http://example.com/app2
    - Different origin: http://www.example.com & http://www.other.com
    - The requests won't be fulfilled unless the other origin allows for the requests, using CORS Headers (e.g. Access-Control-Allow-Origin)
  
  - S3 Cors
    - If a client does a cross-origin request on our S3 bucket, we need to enable the correct CORS headers
    - We can allow for a specific origin or for * (all origins)
  
  - Amazon S3 - Consistency Model
    - There are strong consitency in the Amazon S3 for all the operations. All operations are strongly consistent
      - Successful write of new object or an overwrite or delete of an existing object, after doing any of this operations,
      - any subsequent read request immediately receives the latest version of the object (read after write consistency)
      - any subsequent list request immediately reflects changes (list consistency)
    - This is available at no additional cost, without any performance impact
      