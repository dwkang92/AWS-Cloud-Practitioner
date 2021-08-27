# 02. Udemy_IAM

## 1. What is IAM?

---

### 1) IAM: Users & Groups

- IAM = Identity and Access Management, Global Service
- Root account created by default, shouldn't be used or shared
- Users are people within your organization, and can be grouped.

    ![Untitled](02%20Udemy_IAM%20f0fd5e50e48f44669c8ce5aa40d7fc1e/Untitled.png)

    Udemy Course: Ultimate AWS Certified Cloud Practitioner -2021 by Stephane Maarek.

### 2) IAM: Permissions

- Users or Groups can be assigned JSON documents called policies
- These policies defined the permissions of the users
- As a security concept, AWS you apply the least privilege principle: don't give more permissions than a user needs.

## 2. IAM Policies Inheritance

---

### 1) IAM Policies and its structure

- IAM Policies consists of
    1. Version : Policy language version, always include "2012-10-17"
    2. Id: an identifier for the policy (optional)
    3. Statement: one or more individual statements (required)

- Statements consists of
    1. Sid: an identifier for the statement (optional)
    2. Effect: whether the statement allows or denies access (Allow, Deny)
    3. Principal: account / User / role to which this policy applied to
    4. Action: list of actions this policy allows or denies
    5. Resource: list of resources to which the actions applied to
    6. Condition: conditions for when this policy is in effect (optional)

        ![Untitled](02%20Udemy_IAM%20f0fd5e50e48f44669c8ce5aa40d7fc1e/Untitled%201.png)

        Udemy Course: Ultimate AWS Certified Cloud Practitioner -2021 by Stephane Maarek.

## 3. IAM - Password Policy

---

- Strong passwords = higher security for your account
- In AWS, you can setup a password policy:
    1. Set a minimum password length
    2. Require specific character types:
        1. Including uppercase letters
        2. Lowercase letters
        3. numbers
        4. non-alphanumeric characters
    3. Allow all IAM users to change their own passwords
    4. Require users to change their password after some time (password expiration)
    5. Prevent password re-use

## 4. Multi Factor Authentication - MFA

---

### 1) How it works?

---

- Users have access to your account and can possibly change configurations or delete resources in your AWS account
- You want to protect your Root Accounts and IAM Users
- MFA = Password you know + security device you own
- Main benefit is that, if a password is stolen or hacked, the account is not compromised

### 2) MFA devices options in AWS

---

- Virtual MFA Devices
    1. Looks like "인증번호 (認証番号)" in Korea.
    2. Google Authenticator (Mobile phone only)
    3. Authy (Multi-device)
    4. Support for multiple tokens on a single device
- Universal 2nd Factor (U2F) Security Key (USB)
    1. Support for multiple root and IAM Users using a single security key.
- Hardware Key Fob MFA Device
- Hardware key Fodb MFA Device for AWS GovCloud (US)

## 5. How can users access AWS?

---

- To access AWS, you have 3 options:
    1. AWS Management Console: protected by password + MFA
    2. AWS Command Line Interface (CLI): protected by access keys
    3. AWS Software Developer Kit (SDK): for code; protected by access keys
- Access Keys are generated through the AWS Console
- Users manage their own access keys
- Access Keys are secret, just like a password. Don't share them
- Access Key ID ≠ Username

## 6. What's the AWS CLI?

---

- A tool that enables you to interact with AWS services using commands in your commnd-line shell
- Direct access to the public APIs of AWS services
- Can develop scripts to manage own resources
- It has open-source
- Access Key

## 7. What's the AWS SDK?

---

- AWS Software Development Kit (AWS SDK)
- Language-specific APIs (set of libraries)
- Enables to access and manage AWS services programmatically
- Embedded within your application
- Supports multiple programming language
- Mobile SDKs
- IoT Device SDKs
- Example: AWS CLI is built on AWS SDK for python

## 8. AWS Cloudshell: Region Availability

---

- It is not yet available in all regions.

## 9. IAM Roles for Services

---

- Some AWS Service will need to perform actions on your behalf
- To do so, we will assign permissions to AWS services with IAM Roles.
- Common Roels
    1. EC2 Instance Roles
    2. Lambda Function Roles
    3. Roles for CloudFormation

## 10. IAM Security Tools

---

- IAM Credentials Report (account-level)
    1. A report that lists all your account's users and the status of their various credentials
- Access advisor shows the service permissions granted to a user and when those services were last accessed.
- You can use this information to revise your policies.

## 11. IAM Best Practice

---

- Do not use the root account except for AWS account setup
- One physical user = One AWS user
- Assign users to groups and assign permissions to groups
- Create a strong password policy
- Use and enforce the use of Multi Factor Authentification (MFA)
- Create and use Roles for giving permissions to AWS services
- Use Access Keys for programmatic Access (CLI / SDK)
- Audit permissions of your account with the IAM Credential Report
- Never share IAM users & Access Keys

## 12. Shared Responsibility Model for IAM

---

- AWS
    1. Infrastructure (global network security).
    2. Configuration and vulnerability analysis.
    3. Compliance validation.
- Customers (How i use this service?)
    1. Users, Groups, Roles, Policies management and monitoring.
    2. Enable MFA on all accounts.
    3. Rotate all your keys often.
    4. Use IAM tools to apply appropriate permissions.
    5. Analyze access patterns & review permissions.

## Review

---

- IAM Roles permissions are not assigned to Users.
- Some AWS service will need to perform actions on your behalf. To do so, you assign permissions to AWS services with IAM Roles.
- IAM Credentials report lists all your account's users and the status of their various credentials. The other IAM Security Tool is IAM Access Advisor. It shows the service permissions granted to a user and when those services were last accessed.
- IAM Users don't necessarily have to belong to a group.
- You can assign policies to IAM Users to give them permissions.
- IAM Users can belong to multiple groups (if a user is part of different teams for example).
- You only want to use the root account to create your first IAM user, and for a few account and service management tasks. For every day and administration tasks, use an IAM user with permissions.
- An IAM policy is an entity that, when attached to an identity or resource, defines their permissions.
- Customers are responsible for defining and using IAM policies.
- The AWS CLI can interact with AWS using commands in your command-line shell, while the AWS SDK can interact with AWS programmatically.
- You want to enable MFA in order to add a layer of security, so even if your password is stolen, lost or hacked your account is not compromised.

→ IAM Roles for AWS Services, 

→ IAM Introduction: Users, Groups, Policies.