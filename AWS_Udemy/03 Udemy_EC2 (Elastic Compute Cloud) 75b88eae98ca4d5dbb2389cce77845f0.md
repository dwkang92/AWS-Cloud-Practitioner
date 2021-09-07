# 04 Udemy_EC2 (Elastic Compute Cloud)

## EC2 Basics

---

- EC2 is one of the most popular of AWS's offering
- EC2 = Elastic Compute Cloud = Infrastructure as a Service (IaaS)
- It mainly consists in the capability of:
    1. Renting virtual machines (Virtual Server)
    2. Storing data on virtual drives (EBS vs Instance store)
    3. Distributing load across machines (ELB)
    4. Scaling the services using an auto-scaling group (ASG)
- On demand, security group!

### EC2 Sizing & Configuration Options

---

- OS : Linux, Windows, Mac OS
- CPU, RAM
- How much storage space:
    1. Network-attached (EBS & EFS)
    2. Hardware (EC2 Instance Store)
- Network card: speed of the card, Public IP address
- Firewall rues: security group
- Bootstrap script (EC2 User Data)

## EC2 User Data

---

- It is possible to bootstrap our instances using an EC2 User data script
- Bootstrapping means launching commands when a machine starts
- That script is only run once at the instance first start
- EC2 user data is used to automate boot tasks such as:
    1. Installing updates, software
    2. Downloading common files from the internet
    3. Anything you can think of
- The EC2 User Data Script runs with the root user

## EC2 Instance Types

---

- Can use different types of EC2 instances depends on my situation.
- **General Purpose**
    1. Great for diversity of workloads such as web servers or code repositories.
    2. Balance between "Compute & Memory & Networking".
- **Compute Purpose**
    1. Great, optimized for compute-intensive tasks require high performance processors
        1. Batch processing workloads
        2. Media transcoding
        3. High performance web servers, computing
        4. Scientific modeling & machine learning
        5. Dedicated gaming servers
- **Memory optimized**
    1. Fast performance for workloads that process large data sets in memory
        1. High performance, relational / non-relational databases
        2. Distributed web scale cache stores
        3. In-memory databases optimized for BI (Business Intelligence)
        4. Applications performing real-time processing of big unstructured data.
- **Storage optimized**
    1. Great for storage-intensive tasks that require high, sequential read and write access to large data sets on local storage
        1. High frequency online transaction processing systems
        2. Relational & NoSQL databases
        3. Cache for in-memory databases (Redis)
        4. Data warehousing applications
        5. Distributed file systems

    ## Security Groups

    ---

- Fundamental of network security in AWS
- They control how traffic is allowed into or out of EC2 Instances
- Only contain allow rules
- rules can reference by IP or by security group
- Firewall on EC2 instances
- They regulate
    1. Access to Ports
    2. Authorised IP ranges - IPv4 and IPv6
    3. Control of inbound network (from other to the instance)
    4. Control of outbount network (from the instance to other)
- Can be attached to multiple instances
- Locked down to a region / VPC combination
- Good to maintain one separate security group for SSH access
- Key Pair
- 新規作成する際、インバウンドルールはないため、インバウンドルールをセキュリティグループに追加するまで、別のホストからインスタンスに送信されるインバウンドトラフィックは拒否される。
- デフォルトでは、セキュリティグループには全てのアウトバウンドトラフィックを許可するアウトバウンドルールが含まれている。
- ステートフルであり、インスタンスからリクエストを送信する場合、そのリクエストのレスポンストラフィックは、インバウンドセキュリティグループルールにかかわらず許可される。

## EC2 Instance Launch Types

---

- On-demand Instances: short workload, predictable pricing.
    1. Pay for what i use.
    2. Billing per Hour (Linux, OS, etc.)
    3. Linux, Ubuntu will be billing per seconds (minitues)
    4. Has the highest cost but no upfront payment
    5. No long-term commitment
    6. Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave.

- Reserved Instance (MINIMUM 1 YEAR)
    1. Up to 75% discount compared to On-demand
    2. 1 or 3 Years
    3. Convertible Reserved Instance (can change instance type, Up to 54% discount)
    4. Scheduled Reserved Instances

- Spot Instancess: Short workloads, cheap, can lose instances (Less reliable)
    1. Can get a discount of up to 90% compared to On-demand
    2. Instances that you can "lose" at any point of time if your max price is less than the current spot price
    3. The MOST cost-efficient instances in AWS
    4. Useful for workloads that are resilient to failure
        1. Batch jobs, Data analysis, image processing, any distributed workload.

- Dedicated Hosts: Book an entire pyhsical server, control instances placement.
    1. An AWS EC2 Dedicated Host is a physical server with EC2 instance capacity fully dedicated to your use. Dedicated Hosts can help you address compliance requirements and reduce costs by allowing you to use your existing server-bound software licenses.
    2. Allocated for your account for a 3-year period reservation
    3. Expensive
    4. Useful for software that have complicated licensing model
    5. Or for companies that have strong regulatory or compliance needs

## Shared Responsibility Model for EC2

---

![Untitled](04%20Udemy_EC2%20(Elastic%20Compute%20Cloud)%2075b88eae98ca4d5dbb2389cce77845f0/Untitled.png)

[https://www.udemy.com/course/aws-certified-cloud-practitioner-new/learn/quiz/4900306#overview](https://www.udemy.com/course/aws-certified-cloud-practitioner-new/learn/quiz/4900306#overview)

## Summary

---

![Untitled](04%20Udemy_EC2%20(Elastic%20Compute%20Cloud)%2075b88eae98ca4d5dbb2389cce77845f0/Untitled%201.png)

[https://www.udemy.com/course/aws-certified-cloud-practitioner-new/learn/quiz/4900306#overview](https://www.udemy.com/course/aws-certified-cloud-practitioner-new/learn/quiz/4900306#overview)