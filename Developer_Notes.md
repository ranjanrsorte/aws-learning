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
      - Verical Scalability is very commin for non distributed systems, such as database.
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