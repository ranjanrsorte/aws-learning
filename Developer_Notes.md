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
