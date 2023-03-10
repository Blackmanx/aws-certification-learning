<img src="../images/extra/banner_aws.png" alt="aws" width=80 height=50 /> [General Content AWS Cloud][1]

[1]: https://github.com/Blackmanx/aws-certification-learning

# [Module 6: Compute](https://aws.amazon.com/what-is/compute/)

## Contents
1. <a href="#section-1"> Amazon [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) </a>
2. <a href="#section-2"> Pricing </a>
3. <a href="#section-3"> Instance Types</a>
4. <a href="#section-4"> Amazon Elastic Container Service (ECS)</a>
5. <a href="#section-5"> AWS Lambda</a>
6. <a href="#section-6"> Amazon LightSail</a>
7. <a href="#section-7"> Amazon LightSail Databases</a>
8. <a href="#section-8"> AWS Elastic Beanstalk</a>
9. <a href="#section-9"> AWS Batch </a>
10. <a href="#section-10"> AWS Outposts </a>
11. <a href="#section-11"> AWS Serverless Application Repository </a>
12. <a href="#section-12"> VMware Cloud on AWS </a>
13. <a href="#section-13"> AWS Wavelength </a>
14. <a href="#section-14"> Amazon WorkSpaces Family </a>

***************************************************************************************************
## <a id="section-1"></a> **1 - Amazon EC2**

![Amazon EC2](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_Amazon-EC2_48.png "Amazon EC2")

Amazon Elastic Compute Cloud (Amazon [EC2](https://aws.amazon.com/ec2/?nc1=h_ls)) is a web service that provides resizable compute capacity in the cloud.

With Amazon [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) you launch virtual server instances on the AWS cloud.

Each virtual server is known as an “instance”.

You use preconfigured templates for your instances known as Amazon Machine Images (AMIs).

Each AMI includes the information needed to launch your [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) instance (including the operating system and any included software packages).

**Amazon [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) currently supports a variety of operating systems including:**
- Amazon Linux.
- Ubuntu.
- Windows Server.
- MacOS.
- Red Hat Enterprise Linux.
- SUSE Linux Enterprise Server.
- Fedora.
- Debian.
- CentOS.
- Gentoo Linux.
- Oracle Linux.
- FreeBSD.

[EC2](https://aws.amazon.com/ec2/?nc1=h_ls) compute units (ECUs) provide the relative measure of the integer processing power of an Amazon [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) instance.

With [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) you have full control at the operating system layer (root/admin access).

**Key pairs are used to securely connect to [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) instances:**
- A key pair consists of a public key that AWS stores, and a private key file that you store.
- For Windows AMIs, the private key file is required to obtain the password used to log into your instance.
- For Linux AMIs, the private key file allows you to securely SSH (secure shell) into your instance.

**Metadata and User Data:**
- User data is data that is supplied by the user at instance launch in the form of a script.
- Instance metadata is data about your instance that you can use to configure or manage the running instance.
- User data is limited to 16KB.
- User data and metadata are not encrypted.
- Instance metadata is available at http://169.254.169.254/latest/meta-data/ (the trailing “/” is required).
- Instance user data is available at: http://169.254.169.254/latest/user-data.
- The IP address 169.254.169.254 is a link-local address and is valid only from the instance.
- On Linux you can use the curl command to view metadata and user data, e.g.“curl http://169.254.169.254/latest/meta-data/”.
- The Instance Metadata Query tool allows you to query the instance metadata without having to type out the full URI or category names.

**Launching EC2 Instances options**

- Operating System
- How much compute power & cores (CPU)
- How much random-access memory (RAM)
- How much storage-space
    - Network storage (EBS or EFS)
    - Hardware (EC2 Instance Store)
- Network card: Speed of the card, public IP (default is to use the subnet setting)
- Firewall rules/**security group**
- Bootscrap script: EC2 User Data (only run once at the instance first start, useful for installing packages or setting up some services)

**Instance types**

|               **General Purpose**              |                                                                     **Compute Optimized**                                                                    |                                                                                                            **Memory Optimized**                                                                                                           |                                                                                             **Storage Opimized**                                                                                             |
|:----------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| Balance between compute, memory and networking | High performance processors                                                                                                                                  | Fast performance for processing large data sets in memory                                                                                                                                                                                 | Great for storage-intensive tasks that require high sequential read and write access to large data sets on local storage                                                                                     |
| Labeled with Tx, Mx and A1 (and Mac)           | Labeled with Cx                                                                                                                                              | Labeled with Rx, Xx, High Memory and z1d                                                                                                                                                                                                  | Labeled as Ix, Dx and H1                                                                                                                                                                                     |
| <h4>Great for:</h4> Web servers or code repositories      | <h4>Great for:</h4> Tasks like HPC <br><br> HP web servers <br><br> Media transcoding <br><br> Batch processing workloads <br><br> Dedicated gaming servers <br><br> Scientific modeling <br><br> Machine learning | <h4>Great for:</h4> High performance, relational or non-relational databases <br><br> Distributed web scale cache stores <br><br> In-memory databases optimized for BI (business intelligence) <br><br> Applications performing real-time processing of  big unstructured data | <h4>Great for</h4> <br><br> High frequency online transaction processing (OLTP) systems <br><br> Relational & NoSQL databases <br><br> Cache for in-memory databases (for example, Redis) <br><br> Data warehousing applications Distributed file systems |

**Nice to know**

- Instances can be assigned to IAM roles which configures them with credentials to access AWS resources.

- Termination protection can be enabled and prevents you from terminating an instance.

- Basic monitoring is enabled by default (5-minute periods), detailed monitoring can be enabled (1-minute periods, chargeable).

- Can define shared or dedicated tenancy.

- T2 unlimited allows applications to burst past CPU performance baselines as required (chargeable).

- Windows instances can join to a directory and enable an Elastic GPU.

- Use Amazon Elastic File System (EFS) for mounting a shared filesystem to multiple EC2 instances.

- Non-root volumes can be encrypted.

- Root volumes can be encrypted **at launch.**

- Tags can be assigned

- You must create or use an existing key pair – this is required if you want to access your instances via SSH. However, you can also attach the ‘AmazonEC2RoleforSSM’ IAM role to your EC2 instance to allow connection to your instance via Systems Manager (Session Manager).


### **Amazon Machine Images**

An Amazon Machine Image (AMI) provides the information required to launch an instance.

### **An AMI includes the following:**
- A template for the root volume for the instance (for example, an operating system, an application server, and applications).
- Launch permissions that control which AWS accounts can use the AMI to launch instances.
- A block device mapping that specifies the volumes to attach to the instance when it’s launched.

AMIs are regional. You can only launch an AMI from the region in which it is stored. However, you can copy AMIs to other regions using the console, command line, or the API.

### **Volumes attached to the instance are either EBS or Instance store:**

- Amazon Elastic Block Store (EBS) provides persistent storage. EBS snapshots, which reside on Amazon S3, are used to create the volume.
- Instance store volumes are ephemeral (non-persistent). That means data is lost if the instance is shut down. A template stored on Amazon S3 is used to create the volume.

### **Security Groups**

Security Groups are the fundamental of network security in AWS, as they control how traffic is allowed into or out of our EC2 instances (as well as some other services) within a region/VPC combination.
They can only contain **allow** rules, and they can reference IP or other security groups. If your application is not accessible by a time out error, it's a security
group issue. Otherwise, if it's a connection refused error, it's the app's fault.

They regulate:
- Access to Ports
- Authorised IP ranges – IPv4 and IPv6
- Control of inbound network (from other to the instance)
- Control of outbound network (from the instance to other)

> All inbound traffic is **blocked** by default and all outbound traffic is **allowed**
> by default.

### **EC2 Instance Connect**

Instance Connect lets you connect to your EC2 Instance within your browser.
In order to do this, AWS uploads a temporary key onto your EC2 instance, and it
requires port 22 to be open.

It only works on **Amazon Linux 2** instances.

### **Rehost**

`A company is planning to move a number of legacy applications to the AWS Cloud. The solution must be cost-effective.`

The most cost-effective solution that works is to use Amazon EC2 instances that are right-sized with the most optimum instance types. Right-sizing is the process of ensuring that the instance type selected for each application provides the right amount of resources for the application.

### **Placement Groups**

There are three placement strategies for EC2 instances:

- `Cluster`: Cluster instances into a low-latency group in a single Availability Zone
  - **Pros**: Great network
  - **Cons**: If the rack fails, all the instances fail
  - **Use case**: Big Data job that needs to complete fast or apps that need extremely low latency and high network throughput
- `Spread`: Spread instances across underlying hardware (7 instances per group per AZ)
  - **Pros**: Can span across AZs, reduced risk in simultaneous failure and EC2 instances are in different physical hardware
  - **Cons**: Limited to 7 instances per AZ per placement group
  - **Use case**: Application that needs to maximize high availability or critical apps where instances must be isolated from failure from each other
- `Partition`: Spreads instances across many different partitions on different sets of racks within an AZ. Scales to hundreds of EC2 instances per group (Suited for Hadoop, Cassandra, Kafka)
  - **Pros**: Up to 7 partitions per AZ, can span across AZs, supports hundreds of EC2 instances, a partition failure won't affect other partitions as they don't share racks with the instances in the other partitions
  - **Cons**: A failure can still affect a lot of EC2 instances
  - **Use case**: HDFS, HBase, Cassandra, Kafka


**Cheat Sheets**

https://digitalcloud.training/aws-compute-services/

https://digitalcloud.training/architecting-for-the-cloud/

**References:**

https://d1.awsstatic.com/whitepapers/cost-optimization-right-sizing.pdf

https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.concept.horizontal-scaling.en.html



**Videos**

***************************************************************************************************
## <a id="section-2"></a> **2 - Pricing**
### **Billing and provisioning**

There are several options for how you consume and pay for Amazon EC2 instances.
|                                                          **On Demand**                                                         |                                                                                                                                                                                                                                                                                                               **Spot Instances**                                                                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                       **Reserved Instances**                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                          **Dedicated Hosts**                                                                                                                                                                                                                                                          |                                                                                                                                    **Saving Plans**                                                                                                                                   |
|:------------------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <br>Pay for what you use:<br><br>Linux or Windows: Billing per second, after the first<br>minute<br>Other OS: Billing per hour | <br>Can get a 90% discount compared to On-Demand<br><br>Instances can be lost at any point of time if your<br>max price is lower than current spot price, or<br>interrupted when AWS needs the EC2 capacity back<br><br>You can use the RequestSpotFleet API operation to launch thousands<br>of Spot Instances and diversify resources automatically.<br><br>To further reduce the impact of interruptions, you can also <br>set up Spot Instances and Spot Fleets (Spot Instances + On-Demand)<br>to respond to aninterruption notice by stopping or hibernating rather <br>than terminating instances when capacity is no longer available. | Up to 72% discount compared to On-Demand<br><br>Specific instance attributes (Instance Type, Region, Tenancy, OS)<br>Those instance attributes can be changed in convertible<br>reserved instances, for a bit higher price.<br><br>Reservation Period: 1 Year or 3 years (the longer, the cheaper)<br><br>Reserved Instance Scope: Regional or Zonal<br><br>Payment options: No upfront, Partial Upfront or All Upfront<br>(The more you pay upfront, the cheaper) | A physical server with EC2 instance capacity fully<br>dedicated to your use<br><br>Allows you to address **compliance requirements** and<br>**use your existing server-bound software licenses**<br><br>**On-demand**: Pay per second for active Dedicated Host<br>**Reserved**: 1 or 3 years (No upfront payments)<br><br>**Dedicated Instances**<br>Instances that run on hardware that's dedicated<br>to you and may share hardware with other instances<br>in the same account, and there's no control over instance<br>placement | <br><br>Get a discount based on long-term usage (up to 72% - same as RIs)<br><br>Commit to a certain type of usage ($10/hour for 1 or 3 years)<br><br>Usage beyond EC2 Savings Plans is billed at the On-Demand price<br><br>It's locked to a specific instance family and AWS Region |
| Has high cost, but no upfront payment and no<br>long-term commitment                                                           | Most cost-efficient instances in AWS                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Cheaper than On-Demand if you need complete uptime                                                                                                                                                                                                                                                                                                                                                                                                                 | The most expensive option                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | It's a good option for long-term usage                                                                                                                                                                                                                                                |
| <br><br>Recommended for short-term and un-interrupted workloads,<br>unpredictable applications                                 | Useful for workloads that are resilient to<br>failure, or doesn't need to be up all the time:<br><br>Distributed Workloads<br><br>Batch jobs<br><br>Data analysis<br><br>**It's not suitable for critical jobs or databases**                                                                                                                                                                                                                                                                                                                                                                                                                  | <br><br><br>Useful for stead-state usage applications like databases.                                                                                                                                                                                                                                                                                                                                                                                              | <br><br>Useful for software that have complicated licensing model<br>(Bring Your Own License) or companies with strong<br>regulatory or compliance needs                                                                                                                                                                                                                                                                                                                                                                              | You need to stay a lot of time in a specific instance                                                                                                                                                                                                                                 |
### **Comparing Amazon EC2 Pricing Models**


**The following table describes some of the differences between dedicates instances and dedicated hosts:**

|Characteristic	|Dedicated Instances	|Dedicated Hosts|
|---------------|-----------------------|---------------|
|Enables the use of dedicated physical servers	|YES	|YES|
|Per instance billing (subject to a $2 per region fee)	|YES|	NO|
|Per host billing	 |	NO|YES|
|Visibility of sockets, cores, host ID|NO	| 	YES|
|Affinity between a host and instance	|NO |	YES|
|Targeted instance placement	|NO 	|YES|
|Automatic instance placement	|YES	| YES|
|Add capacity using an allocation request| 	NO| 	YES|

************************************************************
Partial instance-hours consumed are billed based on instance usage.

Instances are billed when they’re in a running state – need to stop or terminate to avoid paying.

Charging by the hour or second (by the second with Linux instances only).

Data between instances in different regions is charged (in and out).

Regional Data Transfer rates apply if at least one of the following is true, but are only charged once for a given instance even if both are true:
- The other instance is in a different Availability Zone, regardless of which type of address is used.
- Public or Elastic IP addresses are used, regardless of which Availability Zone the other instance is in.

**Capacity‌ ‌Reservations‌‌** ‌
–‌ Allows‌ ‌you‌ ‌to‌ ‌reserve‌ ‌capacity‌ ‌for‌ ‌your‌ ‌EC2‌ ‌instances‌ ‌in‌ ‌a‌ ‌specific‌ ‌Availability‌‌
- Zone‌ ‌for‌ ‌any‌ ‌duration.‌ ‌No‌ ‌commitment‌ ‌required.‌ ‌

**Cost optimization** can include using Auto Scaling groups to scale the number of EC2 instances according to actual demand. Also, using Amazon EC2 reserved instances for suitable workloads is a good way of optimizing costs over the longer term.

* "Implement Auto Scaling groups to add and remove instances based on demand" is a correct answer.

* "Purchase Amazon EC2 Reserved Instances" is also a correct answer.


**Cheat Sheets**

https://digitalcloud.training/aws-billing-and-pricing/

**References:**

https://aws.amazon.com/aws-cost-management/aws-cost-optimization/

**Videos**


***************************************************************************************************
## <a id="section-3"></a> **3 - Instance Types**

### **EC2 Instance types**

Amazon EC2 provides a wide selection of instance types optimized to fit different use cases.
Instance types comprise varying combinations of CPU, memory, storage, and networking capacity and give you the flexibility to choose the appropriate mix of resources for your applications.

Each instance type includes one or more instance sizes, allowing you to scale your resources to the requirements of your target workload.

<img src="../images/extra/ec2_instance_types.png" alt="ec2_instance_types" width=80% />


***************************************************************************************************
## <a id="section-4"></a> **4 - Amazon Elastic Container Service (ECS)**

![Amazon-Elastic-Container-Service](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_Amazon-Elastic-Container-Service_48.png "Amazon-Elastic-Container-Service")

Amazon Elastic Container Service is Amazon's own container platform. It's the equivalent of launching docker containers on AWS, but you launch ECS Tasks on ECS clusters instead.

Each EC2 instance must run the ECS Agent to register in the ECS cluster, and AWS takes care of starting and stopping containers.
We'll see more about this service later.

**References**

[AWS ECS](https://github.com/Blackmanx/aws-certification-learning/tree/main/module-18#section-02)
***************************************************************************************************
## <a id="section-5"></a> **5 - AWS Lambda**

![AWS Lambda](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_AWS-Lambda_48.png "AWS Lambda")

AWS Lambda is a serverless service (where we just deploy code).
In Lambda, we deploy virtual functions limited by time with short executions that run **on-demand** and where scaling is **automated**. We'll see more about this later.

**References**

[AWS Lambda](https://github.com/Blackmanx/aws-certification-learning/tree/main/module-14#section-1)

***************************************************************************************************
## <a id="section-6"></a> **6 - Amazon LightSail**

![Amazon LightSail](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_Amazon-Lightsail_48.png "Amazon Lightsail")

[Amazon LightSail](https://aws.amazon.com/lightsail/features/)

Amazon LightSail Instances

[Amazon LightSail](https://aws.amazon.com/lightsail/features/) is one of the newest services in the AWS Compute suite of products. Amazon LightSail is great for users who do not have deep AWS technical expertise as it makes it very easy to provision compute services.

[Amazon LightSail](https://aws.amazon.com/lightsail/features/) provides developers compute, storage, and networking capacity and capabilities to deploy and manage websites, web applications, and databases in the cloud.

[Amazon LightSail](https://aws.amazon.com/lightsail/features/) includes everything you need to launch your project quickly – a virtual machine, SSD-based storage, data transfer, DNS management, and a static IP.

[Amazon LightSail](https://aws.amazon.com/lightsail/features/) provides preconfigured virtual private servers (instances) that include everything required to deploy and application or create a database.

The underlying infrastructure and operating system is managed by Amazon LightSail.

Best suited to projects that require a few dozen instances or fewer.

Provides a simple management interface.

Good for blogs, websites, web applications, e-commerce etc.

Can deploy load balancers and attach block storage.

Public API.

**Limited to:**
    - 20 Amazon LightSail instances
    - 5 static IPs
    - 3 DNS zones
    - 20 TB block storage
    - 40 databases
    - 5 load balancers per account.

Up to 20 certificates per calendar year.

Can connect to each other and other AWS resources through public Internet and private (VPC peering) networking.

Application templates include WordPress, WordPress Multisite, Drupal, Joomla!, Magento, Redmine, LAMP, Nginx (LEMP), MEAN, Node.js, and more.

Amazon LightSail currently supports 6 Linux or Unix-like distributions: Amazon Linux, CentOS, Debian, FreeBSD, OpenSUSE, and Ubuntu, as well as 2 Windows Server versions: 2012 R2 and 2016.

***************************************************************************************************
## <a id="section-7"></a> **7 - Amazon LightSail Databases**

### **Amazon LightSail Databases**
Amazon LightSail databases are instances that are dedicated to running databases.

An Amazon LightSail database can contain multiple user-created databases, and you can access it by using the same tools and applications that you use with a stand-alone database.

**Amazon LightSail** managed databases provide an easy, low maintenance way to store your data in the cloud.

**Amazon LightSail** manages a range of maintenance activities and security for your database and its underlying infrastructure.

**Amazon LightSail** automatically backs up your database and allows point in time restore from the past 7 days using the database restore tool.

**Amazon LightSail databases** support the latest major versions of MySQL. Currently, these versions are 5.6, 5.7, and 8.0 for MySQL.

**Amazon LightSail databases** are available in Standard and High Availability plans.

High Availability plans add redundancy and durability to your database, by automatically creating standby database in a separate Availability Zone.

**Amazon LightSail** is very affordable.

**Amazon LightSail** plans are billed on an on-demand hourly rate, so you pay only for what you use.

For every **Amazon LightSail** plan you use, we charge you the fixed hourly price, up to the maximum monthly plan cost.

***************************************************************************************************
## <a id="section-8"></a> **8 - AWS Elastic Beanstalk**
[AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/)

AWS Elastic Beanstalk can be used to quickly deploy and manage applications in the AWS Cloud.

Developers upload applications and Elastic Beanstalk handles the deployment details of capacity provisioning, load balancing, auto-scaling, and application health monitoring.

You can use multiple availability zones to improve application reliability and availability.

Considered a Platform as a Service (PaaS) solution.

Supports the following platforms:
- [Docker](https://docs.aws.amazon.com/elasticbeanstalk/latest/platforms/platforms-supported.html#platforms-supported.docker)
- Multicontainer Docker
- Preconfigured Docker
- Go
- Java SE
- Tomcat
- .NET Core on Linux
- .NET on Windows Server
- Node.js
- PHP
- Python
- Ruby

Developers can focus on writing code and don’t need to worry about deploying infrastructure.

You pay only for the resources provisioned, not for Elastic Beanstalk itself.

Elastic Beanstalk automatically scales your application up and down.

You can select the [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) instance type that is optimal for your application.

Can retain full administrative control or have Elastic Beanstalk do it for you.

The Managed Platform Updates feature automatically applies updates for your operating system and platform.

Elastic Beanstalk monitors and manages application health and information is viewable via a dashboard.

Integrated with CloudWatch and X-Ray for performance data and metrics.

Integrates with Amazon VPC and AWS IAM.

Can provision most database instances.

Stores your application files and, optionally, server log files in Amazon S3.

Application data can also be stored on S3.

Multiple environments are supported to enable versioning.

Changes from Git repositories are replicated.

Linux and Windows AMI support.

Code is deployed using a WAR file or Git repository.

Can use the AWS toolkit for Visual Studio and the AWS toolkit for Eclipse to deploy Elastic Beanstalk.

Fault tolerance within a single region.

By default applications are publicly accessible.

Can access logs without logging into application servers.

Provides ISO, PCI, SOC 1, [SOC 2](https://docs.aws.amazon.com/audit-manager/latest/userguide/SOC2.html), and SOC 3 compliance along with the criteria for HIPAA eligibility.

Supports AWS Graviton arm64-based processors.

### **Elastic Beanstalk Layers**

There are several layers that make up Elastic Beanstalk and each layer is described below:

**Application:**
- Within Elastic Beanstalk, an application is a collection of different elements, such as environments, environment configurations, and application versions.
- You can have multiple application versions held within an application.

**Application version:**
- An application version is a very specific reference to a section of deployable code.
- The application version will point typically to an Amazon s3 bucket containing the code.

**Environment:**
- An environment refers to an application version that has been deployed on AWS resources.
- The resources are configured and provisioned by AWS Elastic Beanstalk.
- The environment is comprised of all the resources created by Elastic Beanstalk and not just an [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) instance with your uploaded code.

### Elastic Beanstalk Applications Environments and Versions
<br/><br/>
<img src="../images/extra/elastic-beanstalk-applications-environments-and-ve.jpeg" alt="elastic-beanstalk-applications-environments-and-ve" width=80% />
<br/><br/>

**Environment tier:**
- Determines how Elastic Beanstalk provisions resources based on what the application is designed to do.
- Web servers are standard applications that listen for and then process HTTP requests, typically over port 80.
- Workers are specialized applications that have a background processing task that listens for messages on an Amazon SQS queue.

**Environment configurations:**
- An environment configuration is a collection of parameters and settings that dictate how an environment will have its resources provisioned by Elastic Beanstalk and how these resources will behave.

**Configuration template:**
- This is a template that provides the baseline for creating a new, unique environment configuration.

**Deployment Options**
AWS Elastic Beanstalk provides several options for how deployments are processed, including deployment policies and options that let you configure batch size and health check behavior during deployments.
Deployment options

Single instance: great for development.

High availability with load balancer: great for production.
Deployment policies

The deployment policies are: All at once, Rolling, Rolling with additional batch, and Immutable.

**All at once:**
- Deploys the new version to all instances simultaneously.
- All your instances are out of service while the deployment takes place.
- Fastest deployment.
- Good for quick iterations in the development environment.
- You will experience an outage while the deployment is taking place – not ideal for mission-critical systems.
- If the update fails, you need to roll back the changes by re-deploying the original version to all your instances.
- No additional cost.

**Rolling:**
- Update a few instances at a time (batch), and then move onto the next batch once the first batch is healthy (downtime for 1 batch at a time).
- The application is running both versions simultaneously.
- Each batch of instances is taken out of service while the deployment takes place.
- Your environment capacity will be reduced by the number of instances in a batch while the deployment takes place.
- Not ideal for performance-sensitive systems.
- If the update fails, you need to perform an additional rolling update to roll back the changes.
- No additional cost.
- Long deployment time.

**Rolling with additional batch:**
- Like Rolling but launches new instances in a batch ensuring that there is full availability.
- The application is running at capacity.
- You can set the bucket size.
- The application is running both versions simultaneously.
- Small additional cost.
- Additional batch is removed at the end of the deployment.
- Longer deployment.
- Good for production environments.

**Immutable:**
- Launches new instances in a new ASG and deploys the version update to these instances before swapping traffic to these instances once healthy.
- Zero downtime.
- New code is deployed to new instances using an ASG.
- High cost as double the number of instances running during updates.
- Longest deployment.
- Quick rollback in case of failures.
- Great for production environments.

**Additionally, Elastic Beanstalk supports blue/green deployment.**

- **Blue / Green deployment:**
    - This is not a feature within Elastic Beanstalk
    - You create a new “staging” environment and deploy updates there.
    - The new environment (green) can be validated independently, and you can roll back if there are issues.
    - Route 53 can be set up using weighted policies to redirect a percentage of traffic to the staging environment.
    - Using Elastic Beanstalk, you can “swap URLs” when done with the environment test.
    - Zero downtime.

The following tables summarizes the different deployment policies:
<br/><br/>
<img src="../images/extra/deployBeanStalk.png" alt="deployBeanStalk" width=80% />
<br/><br/>

**Golden AMIs**

When deploying code to Amazon [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) using Beanstalk, Elastic Beanstalk must resolve application dependencies which can take a long time.

A golden AMI is a method of reducing this time by packaging all dependencies, configuration, and software into the AMI before deploying.


**Elastic Beanstalk CLI**

There is an additional CLI called “eb cli”.

The EB CLI is a command-line interface for AWS Elastic Beanstalk that provides interactive commands that simplify creating, updating, and monitoring environments from a local repository.

You can use the EB CLI as part of your everyday development and testing cycle as an alternative to the Elastic Beanstalk console.

**Lifecycle Policies**

Elastic Beanstalk can store at most 1000 application versions.

### **To phase out old versions use a lifecycle policy:**
- Time-based – specify max age.
- Count based – specify max number to retain.

Versions that are in use will not be deleted.

Option to not delete the source bundle in S3 to prevent data loss.
Worker environments

If an application performs tasks that take a long time to complete (long-running tasks), offload to a worker environment.

It allows you to decouple your application tiers.

Can define periodic tasks in the cron.yaml file.

<br/><br/>
<img src="../images/extra/elastic-beanstalk-worker-environment.jpeg" alt="elastic-beanstalk-worker-environment" width=80% />
<br/><br/>

### **Elastic Beanstalk Extensions**

You can add AWS Elastic Beanstalk configuration files (.ebextensions) to your web application’s source code to configure your environment and customize the AWS resources that it contains.

Customization includes defining packages to install, create Linux users and groups, running shell commands, specifying services to enable, configuring a load balancer, etc.

Configuration files are YAML- or JSON-formatted documents with a .config file extension that you place in a folder named .ebextensions and deploy in your application source bundle.

The .ebextensions folder must be included in the top-level directory of your application source code bundle.

All the parameters set in the UI can be configured in the code.

**Requirements:**
- Must be in the .ebextensions/ directory of the source code.
- YAML or JSON format.
- .config extensions can be included (e.g. logging.config).
- You can modify some default settings using “option_settings”.
- You can add resources such as RDS, ElastiCache, and DynamoDB.

Resources managed by .ebextensions get deleted if the environment is terminated.

### **Elastic Beanstalk with Amazon Relational Database Service (RDS)**

You can deploy Amazon RDS within an Elastic Beanstalk environment as in the diagram below:

<img src="../images/extra/elastic-beanstalk-environment-with-rds.jpeg" alt="elastic-beanstalk-environment-with-rds.jpeg" width=80% />


However, if you terminate your Elastic Beanstalk environment you also lose the database.

The use case is only for development environments, typically not suitable for production.

For production, it is preferable to create the Amazon RDS database outside of Elastic Beanstalk as in the diagram below:
<br/><br/>
<img src="../images/extra/elastic-beanstalk-environment-with-rds.jpeg" alt="elastic-beanstalk-environment-with-rds.jpeg" width=80% />
<br/><br/>

**Steps to migrate from RDS within a Beanstalk environment to standalone RDS:**
- Take a snapshot of the RDS DB.
- Enable deletion protection on the RDS DB.
- Create a new environment without an RDS DB and point applications to the existing RDS DB.
- Perform a blue/green deployment and swap the new and old environments.
- Terminate the old environment (RDS will not be deleted due to termination protection).
- Delete the CloudFormation stack (will be in the DELETE_FAILED state).

**Connecting to an Amazon RDS database**

When the environment update is complete, the DB instance’s hostname and other connection information are available to your application through the following environment properties:
- RDS_HOSTNAME – The hostname of the DB instance.
- RDS_PORT – The port on which the DB instance accepts connections. The default value varies among DB engines.
- RDS_DB_NAME – The database name, ebdb.
- RDS_USERNAME – The user name that you configured for your database.
- RDS_PASSWORD – The password that you configured for your database.

**Custom Domain Names**

If you’re using AWS Elastic Beanstalk to deploy and manage applications in the AWS Cloud, you can use Amazon Route 53 to route DNS traffic for your domain, such as example.com, to a new or an existing Elastic Beanstalk environment.

You create either a CNAME record or an alias record, depending on whether the domain name for the environment includes the Region, such as us-east-2, in which you deployed the environment. New environments include the Region in the domain name; environments that were created before early 2016 do not.

If the domain name does NOT include the Region: create a CNAME record.

If the domain name DOES include the Region: create an Alias record.

### **Security**

**Elastic Beanstalk works with HTTPS:**
- Load the SSL certificate onto the load balancer.
- Can be performed from the console or in code (.ebextensions/securelistener-alb.config).
- SSL certificate can be provisioned using ACM or CLI.

**For redirecting HTTP to HTTPS:**
- Configure in the application.
- Configure the ALB with a rule.
- Ensure health checks are not redirected.

**Monitoring and Reporting**

Elastic Beanstalk automatically uses Amazon CloudWatch to help you monitor your application and environment status.

You can navigate to the Amazon CloudWatch console to see your dashboard and get an overview of all your resources as well as your alarms.

You can also choose to view more metrics or add custom metrics.

**Logging and Auditing**

With CloudWatch Logs, you can monitor and archive your Elastic Beanstalk application, system, and custom log files from Amazon [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) instances of your environments.

You can also configure alarms that make it easier for you to react to specific log stream events that your metric filters extract.

The CloudWatch Logs agent installed on each Amazon [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) instance in your environment publishes metric data points to the CloudWatch service for each log group you configure.

Each log group applies its own filter patterns to determine what log stream events to send to CloudWatch as data points.

Log streams that belong to the same log group share the same retention, monitoring, and access control settings.

In addition to instance logs, if you enable enhanced health for your environment, you can configure the environment to stream health information to CloudWatch Logs.

### **Authorization and Access Control**

AWS Elastic Beanstalk supports **[identity-based policies](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.html)**.

AWS Elastic Beanstalk does not support **[resource-based policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html)**.

AWS Elastic Beanstalk has partial support for **[resource-level](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)** permissions.

When you create an environment, AWS Elastic Beanstalk prompts you to provide two AWS Identity and Access Management (IAM) roles: a service role and an instance profile.

The **[service role](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-roles-service.html)** is assumed by Elastic Beanstalk to use other AWS services on your behalf.

The [instance profile](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-roles-instance.html) is applied to the instances in your environment and allows them to retrieve [application versions](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.html#concepts-version) from Amazon Simple Storage Service (Amazon S3), upload logs to Amazon S3, and perform other tasks that vary depending on the environment type and platform.

You can also create [user policies](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-roles-user.html) and apply them to IAM users and groups in your account to allow users to create and manage Elastic Beanstalk applications and environments. Elastic Beanstalk provides managed policies for full access and read-only access.

***************************************************************************************************
## <a id="section-9"></a> **9 - AWS Batch**

![AWS-Batch](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_AWS-Batch_48.png "AWS-Batch")

**Cheat Sheets**

https://tutorialsdojo.com/aws-batch/

**References:**

https://aws.amazon.com/batch/

https://aws.amazon.com/elasticbeanstalk/

https://docs.aws.amazon.com/batch/latest/userguide/

https://aws.amazon.com/batch/features/

https://aws.amazon.com/batch/pricing/

https://aws.amazon.com/batch/faqs/

**Videos**

https://www.youtube.com/results?search_query=aws+batch+

https://www.youtube.com/watch?v=T4aAWrGHmxQ

https://www.youtube.com/watch?v=H8bmHU_z8Ac


***************************************************************************************************
## <a id="section-10"></a> **10 - AWS Outposts**


![AWS Outposts Server](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_AWS-Outposts-servers_48.png "AWS Outposts Server")
![AWS Outposts Family](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_AWS-Outposts-family_48.png "AWS Outposts Family")
![AWS Outposts Rack](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_AWS-Outposts-rack_48.png "AWS Outposts Rack")

**Definitions**

AWS Outposts is a fully managed service that offers the same AWS infrastructure, AWS services, APIs, and tools to virtually any datacenter, co-location space, or on-premises facility for a truly consistent hybrid experience. With AWS Outposts you can extend your VPC into the on-premises data center as in the following diagram:

![AWS Outposts](../images/extra/AwsOutposts.jpg)

#### **Monitoring**
- You can use Amazon Cloudwatch to retrieve Outposts metrics.
- To capture API actions from services on an Outpost, you can use AWS CloudTrail.
- Use VPC Flow Logs to get detailed information about traffic to and from your Outpost, as well as traffic within your Outpost.
- You can also use Traffic Mirroring for content inspection, threat monitoring, troubleshooting, or copying and forwarding network traffic.
- To see changes in the health of AWS resources, you can use AWS Health Dashboard.

#### **Pricing**
- You are charged for Outposts rack capacity for a 3-year term: All, Partial, or No Upfront.
- You are charged for the following:
   - AWS services running on Outposts
   - AWS Marketplace AMIs
   - Outposts and Outpost resources that you share
   - Data transfer associated with Outpost’s service link VPN traffic from AWS Region
- You are not charged for data transfers from Outpost to the parent AWS Region.


**Cheat Sheets**

https://tutorialsdojo.com/aws-outposts/

https://digitalcloud.training/aws-networking-services/

**References:**

https://aws.amazon.com/outposts/

https://aws.amazon.com/outposts/

https://docs.aws.amazon.com/outposts/latest/userguide/what-is-outposts.html


**Videos**

https://www.youtube.com/results?search_query=AWS+Outposts

https://www.youtube.com/watch?v=2cQncaijRoY


**Hands On**

https://www.youtube.com/results?search_query=AWS+Outposts+hands+on

***************************************************************************************************
## <a id="section-11"></a> **11 - AWS Serverless Application Repository**

![AWS-Serverless-Application-Repository](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_AWS-Serverless-Application-Repository_48.png "AWS-Serverless-Application-Repository")

**Definitions**

- The AWS Serverless Application Repository is a managed repository for deploying and publishing serverless applications.
- You can also use pre-built applications instead of cloning, building, packaging, and publishing source code to AWS before deploying it.
- Each application includes an AWS SAM template that specifies the AWS resources that will be used.


### **AWS Serverless Application Repository Monitoring**

Create a trail in AWS CloudTrail to capture all API calls.

Even if you haven’t configured a trail, you can still view the most recent events in the CloudTrail console’s Event history.

### **Pricing**
You are charged for AWS resources used in the applications you deploy.


**Cheat Sheets**

https://tutorialsdojo.com/aws-serverless-application-repository/

**References:**

https://aws.amazon.com/serverless/serverlessrepo/

https://docs.aws.amazon.com/serverlessrepo/latest/devguide/what-is-serverlessrepo.html

**Videos**

https://www.youtube.com/results?search_query=AWS+Serverless+Application+Repository

**Hands On**

https://www.youtube.com/results?search_query=AWS+Serverless+Application+Repository+hands+on

***************************************************************************************************
## <a id="section-12"></a> **12 - VMware Cloud on AWS**

![VMware-Cloud-on-AWS](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_VMware-Cloud-on-AWS_48.png "VMware-Cloud-on-AWS")

**Definitions**

VMware Cloud on AWS provides dedicated, single-tenant cloud infrastructure with support multiple SDDC per organization, with up to 16 hosts per cluster, delivered on the next-generation bare metal AWS infrastructure based on the latest Amazon EC2 Storage Optimized high I/O instances and featuring low-latency Non-Volatile Memory Express (NVMe) based SSDs.

You can quickly create new VMware SDDC clusters on AWS Cloud through a web-based console or by utilizing a RESTful API. VMware manages and operates the service including VMware SDDC software components and the modern web-based console.

VMware delivers service status with notifications, enterprise-grade 24x7 service support & site reliability operations, and support center with FAQs, forums & chat support. VMware delivers scheduled SDDC software updates and emergency software patches with notifications, and auto-remediation of hardware failures.

**Cheat Sheets**

**References:**

https://aws.amazon.com/vmware/features/?nc1=h_ls

https://aws.amazon.com/vmware/faqs/

https://aws.amazon.com/vmware/resources/?blog-posts-cards.sort-by=item.additionalFields.modifiedDate&blog-posts-cards.sort-order=desc

**Videos**

https://www.youtube.com/results?search_query=VMware+Cloud+on+AWS

**Hands On**

https://www.youtube.com/results?search_query=VMware+Cloud+on+AWS+hands+ON
***************************************************************************************************
## <a id="section-13"></a> **13 - AWS Wavelength**

![AWS-Wavelength](../images/Architecture-Service-Icons_01312022/Arch_Compute/48/Arch_AWS-Wavelength_48.png "AWS-Wavelength")

**Definitons**

- A service that allows developers to create applications with ultra-low latencies for mobile devices and end users.
- Wavelength Zones can be used to extend an Amazon VPC in order to run ultra-low latency applications that use the same AWS services, APIs, tools, and functionalities.

### **Features**
- Wavelength Zones support a wide range of compute instances for general purpose, gaming, and machine learning inference.
- Supports persistent block storage to provide a snapshot, encryption, and restore capabilities without any performance impact.
- Connectivity to 5G networks using VPC and Carrier Gateway.
- Various AWS management and monitoring tools to run and manage workloads in Wavelength Zones.

**Use cases:**
- Create and distribute augmented/virtual reality (AR/VR) apps, as well as HD live video streaming.
- Use AI and ML-powered video and image analytics at the edge to accelerate 5G applications in medical diagnostics, retail, and smart manufacturing settings.
- With near-real-time communication between automobiles and the cloud, you’ll be able to create advanced driver assistance, autonomous driving, and in-vehicle entertainment experiences.

### **Concepts**

- Wavelength is the AWS infrastructure used to run workloads that require ultra-low latencies over mobile networks.

**Wavelength Zone (WZ)**
- A logical extension of the Region. It is where the Wavelength infrastructure is deployed and is managed by the Region’s control plane.
- Use WZs for application components that require ultra-low latency, enhanced bandwidth, or improved service quality across 5G mobile networks.
- To give the most scalable, robust, and cost-effective alternatives for components, AWS recommends that you design the edge applications in a hub and spoke model with the Region.
- For latency-sensitive applications, you need to have multiple WZs.
- To discover the closest WZ endpoint, you must register the EC2 instance with a discovery service such as AWS Cloud Map.
- For data and app replication, AWS recommends you use an AZ in a different Region as a failover zone.
- Apps running on 4G/LTE mobile phones and devices connected to 4G/LTE networks can also connect to Wavelength Zones’ application servers.

An application that you run on an AWS resource in a WZ is called **Wavelength Application**.


**Carrier Gateway**
- Provides connectivity between WZ and telecommunication carrier.
- Enables inbound traffic from a carrier network in a specific location, as well as outbound traffic to the carrier network and the internet.
- Supports IPv4 traffic.
- Only available for VPCs with WZ subnets.
- To assign a network interface, use a carrier IP address from the network border group.

- You can create AWS compute, storage services, and carrier gateways in WZs.
- You’ll also need VPC, Subnet, and Network Border Group to be able to leverage the 5G edge computing infrastructure of AWS Wavelength.

To manage your resources and WZs, you can use the following interfaces:
- AWS Management Console
- AWS CLI
- AWS SDKs

### **Pricing**
- Prices for AWS resources in WZs will differ from those in the parent region.
- In WZs, EC2 instances are only available on demand.
- Wavelength Zones can be used with your Instance Savings Plan.

**Cheat Sheets**

https://tutorialsdojo.com/aws-wavelength/

**References:**

https://aws.amazon.com/wavelength/

https://docs.aws.amazon.com/wavelength/latest/developerguide/what-is-wavelength.html

**Videos**

https://www.youtube.com/results?search_query=AWS+Wavelength

**Hands On**

https://www.youtube.com/results?search_query=AWS+Wavelength+hands+on


***************************************************************************************************
## <a id="section-14"></a> **14 - Amazon WorkSpaces Family**

![Amazon-WorkSpaces](../images/Architecture-Service-Icons_01312022/Arch_End-User-Computing/64/Arch_Amazon-WorkSpaces_64.svg "Amazon-WorkSpaces")

**Definition**

### Why Amazon WorkSpaces Family?

The Amazon WorkSpaces Family solutions provide the right virtual workspace for varied worker types, from any location. Improve IT agility and maximize user experience, while only paying for the infrastructure that you use.

**Cheat Sheets**

**References:**

https://aws.amazon.com/workspaces/?nc1=h_ls

**Videos**

https://www.youtube.com/results?search_query=amazon+WorkSpaces

**Hands On**

https://www.youtube.com/results?search_query=amazon+WorkSpaces+hands+on


