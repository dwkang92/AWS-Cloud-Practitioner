# 01. Udemy_Cloud Computing

## 1. What is Cloud Computing?

---

### 1) IT Terminology

- Network: cables, routers and servers connected with each other.
- Router: A networking device that forwards data packets between computer networks.

    They know where to send your packets on the internet.

- Switch: Takes a packet and send it to the correct server / client on your network.

### 2) Traditional IT Overview

- What is a server composed of ?
    1. CPU (Compute) + RAM (Memory) = Brain
    2. Storage Data
    3. Database: Store Data in a structured way (RDBS, etc)
    4. Network: Routers, switch, DNS Server
- Problems with traditional IT approach
    1. Pay for the rent for the data center.
    2. Pay for power supply, cooling, maintenance.
    3. Adding and replacing hardware takes time.
    4. Scaling is limited.
    5. Hire 24/7 team to monitor the infrastructure
    6. How to deal with disasters? (Earthquake, power shutdown, fire, etc)

### 3) Cloud Computing

- Cloud computing is the **On-demand Delivery** of compute power, database storage, applications, and other IT resources.
- Through a cloud services platform with **Pay-as-you-go Pricing.**
- You can **Provision exactly the right type and size of computing** resources you need
- You can access as many resources as you need, almost **INSTANTLY.**
- Simple way to access servers, storage, databases and a set of application services.
- Cloud Services near us: Gmail, Dropbox, Netflix

### 4) The Deployment Models of the Cloud

- **Private**
    1. Cloud services used by a single organization, not exposed to the public.
    2. Complete control.
    3. Security for sensitive applications.
    4. Meet specific business needs.
- **Public**
    1. Cloud resources owned and operated by a third-party cloud service provider over the Internet.
    2. Six Advantages of Cloud Computing
- **Hybrid**
    1. Keep some servers on premises and extend some capabilities to Cloud.
    2. Control over sensitive assets in your private infrastructure.
    3. Flexibility and cost-effectiveness of the public cloud

### 5) The 5 Characteristics of Cloud Computing

- On-demand self service
    1. Users can provision resources and use them without human interaction from the service provider
- Broad network access
    1. Resources available over the network, and can be accessed by diverse client platforms.
- Multi-tenancy and resource pooling
    1. Multiple customers can share the same infrastructure and applications with security and privacy.
    2. Multiple customers are serviced from the same physical resources.
- Rapid elasticity and scalability
    1. Automatically and quickly acquire and dispose resources when needed.
- Measured service
    1. Usage is measured, users pay correctly for what they have used.

### 6) Six Advantages of Cloud Computing

- **Trade Capital Expense (CAPEX) for operational expense (OPEX)**
    1. Pay On- Demand: don't own hardware.
    2. Reduced Total Cost of Ownership (TCO) & Operational Expenses (OPEX)
- Benefit from massive economies of scale
    1. Prices are reduced as AWS is more efficient due to large scale.
- Stop guessing capacity
    1. Scale based on actual measured usage.
- Increase speed and agility
- Stop spending money running and maintaining data centers.
- Go global in minutes
    1. Leverage the AWS Global Infrastructure.

### 7) Problems solved by the Cloud

- Flexibility
    1. Change resource types when needed.
- Cost-Effectiveness
    1. Pay as you go, for what you use
- Scalability
    1. Accommodate larger loads by making hardware stronger or adding additional nodes.
- Elasticity
    1. Ability to scale out and scale-in when needed.
- High-availability and fault-tolerance
    1. build across data centers

### 8) Types of Cloud Computing

- Infrastructure as a Service (IaaS)
    1. Provide building blocks for cloud IT.
    2. Provides networking, computers, data storage space.
    3. Highest level of flexibility.
    4. Easy parallel with traditional on-premises IT.
- Platform as a Service (PaaS)
    1. Removes the need for your organization to manage the underlying infrastructre.
    2. Focus on the deployment and management of your applications.
- Software as a Service (SaaS)
    1. Completed product that is run and managed by the service provider.

### 9) Example of Cloud Computing Types

- Infrastructure as a Service (Iaas)
    1. Amazon EC2 (on AWS)
    2. GCP, Azure, Rackspace, Digital Ocean, Lincode
- Platform as a Service (PaaS)
    1. Elastic Beanstalk (on AWS)
    2. Heroku, Google App Engine, Windows Azure (Microsoft)
- Software as a Service (SaaS)
    1. Many AWS Services
    2. Google Apps (Gmail), Dropbox, Zoom

    ![Untitled](01%20Udemy_Cloud%20Computing%2001e92cb417b24a2c8250327ab184f6ff/Untitled.png)

    Udemy Course: Ultimate AWS Certified Cloud Practitioner -2021 by Stephane Maarek.

    ![Untitled](01%20Udemy_Cloud%20Computing%2001e92cb417b24a2c8250327ab184f6ff/Untitled%201.png)

    Udemy Course: Ultimate AWS Certified Cloud Practitioner -2021 by Stephane Maarek.

### 10) AWS Global Infrastructure

- AWS has Regions all around the world
- Names can be us-east- 1, eu-west-3, etc.
- A region is a cluster of Data Centers
- Most AWS services are region-scoped
- Each region has many availability zones (usually 3, minimum is 2, maximum is 6)
- Each AZ is one or more discrete data centers with redundant power, networking, and connectivity. Composed of one or more discrete data centers with redundant power, networking, and connectivity, and are used to deploy infrastructure is AZ.
- There are separate from each other, so that they are isolated from disaster
- They are connected with high bandwidth, ultra-low latency networking
- Amazon has 216 points of presence = Content is delivered to end users with low latency
- AWS has GLOBAL SERVICES
    1. IAM
    2. Route 53 (DNS Service)
    3. CloudFront (CDN Service)
    4. WAF (Web Application Firewall)
- Most AWS services are Region-Scoped
    1. EC2 (IaaS)
    2. Elastic Beanstalk (PaaS)
    3. Lambda (FaaS)
    4. Rekognition (SaaS)

### 11) How to choose an AWS Region?

- Compliance with data governance and legal requirements
    1. Data never leaves a region without your explicit permission from Government.
- Proximity to customers to reduce latency
- Available services within a Region
    1. New services and new features are not available in every Region.
- Pricing varies region to region and is transparent in the service pricing page.

### 12) Shared Responsibility Model & AWS Acceptable Policy

- IN THE CLOUD = Customer
- OF THE CLOUD = AWS
- No illegal, harmful, or offensive use or content
- No security violations
- No network abuse
- No e-mail or other message abuse

### 2. Additional Explain for this Chapter

---

- Compute, Storage, and data transfer out of the AWS Cloud are the 3 pricing fundamentals of the AWS Cloud.
- Capacity is unlimited in the cloud, you do not need to worry about it. The 4 points of considerations when choosing an AWS Region are: compliance with data governance and legal requirements, proximity to customers, available services and features within a Region, and pricing.
- AWS Regions consist of multiple, isolated, and physically separate Availability Zones within a geographic area.
- Global Scope Services or not = Important!! FYI, EC2, Lambda, Rekognition is not the global scope services.
- Definition of Cloud Computing: On-Demand availability of computer system resources, especially data storage (cloud storage) and computing power, without direct active management by the user.
- The Shared Responsibility Model defines who is responsible for what in the AWS Cloud.
- Using a Hybrid Cloud deployment model allows you to benefit from the flexibility, scalability and on-demand storage access while keeping security and performance of your own infrastructure.
- You can run analytics on AWS, but you cannot run analytics on fraudulent content. Refer to the AWS Acceptable Use Policy to see what is not authorized to do on AWS.