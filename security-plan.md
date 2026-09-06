# Secure Cloud Architecture Plan

## Architecture

The proposed secure cloud architecture for the Student Management Application follows this structure:

Users
↓
CDN
↓
Load Balancer
↓
Application Servers
↓
Private Database

The application servers should be placed in a private subnet, while the database should remain private and should not be directly accessible from the Internet.

## CDN

The Content Delivery Network (CDN) delivers cached copies of static website content from locations closer to users. This improves website loading speed and reduces the amount of traffic handled by the application servers.

## Load Balancer

The load balancer receives incoming requests from users and distributes them across multiple application servers. This improves application performance, availability, and reliability.

## Application Servers

Application servers process user requests and handle the application logic. The application servers should be placed in a private subnet and should only accept connections from the load balancer.

Using multiple application servers also improves availability because another server can continue handling requests if one server becomes unavailable.

## Database

The database stores student records and other application information. The database should remain in a private subnet and should not be directly accessible from the Internet.

Only authorized application servers should be allowed to connect to the database.

# Public and Private Resources

| Resource | Public or Private? | Explanation |
|---|---|---|
| CDN | Public | The CDN is public because users need to access website content through the Internet. |
| Load Balancer | Public | The load balancer is public because it receives incoming requests from users and forwards them to the application servers. |
| Application Server | Private | Application servers should be private so users cannot directly access them from the Internet. |
| Database | Private | The database should be private because it stores student information and should not be directly accessible from the Internet. |

# Security Controls

## IAM

Identity and Access Management (IAM) controls who can access the cloud environment and what actions they are allowed to perform.

Only authorized users should have access to the cloud environment. Administrators should have permissions to manage the cloud infrastructure and security settings. Instructors, students, and developers should only receive the permissions required for their specific roles.

## MFA

Multi-Factor Authentication (MFA) should be enabled for administrator accounts and other accounts with access to sensitive resources.

MFA provides an additional layer of security because users must provide more than just a password to authenticate.

## Firewall / Security Group

Firewalls and security groups should restrict network traffic and only allow necessary connections.

The following rules should be applied:

Internet → Load Balancer = Allowed

Load Balancer → Application Server = Allowed

Application Server → Database = Allowed

Internet → Application Server = Blocked

Internet → Database = Blocked

Users should only communicate with the application through the load balancer.

## Encryption

Student information should be encrypted to protect it from unauthorized access.

Data should be encrypted while being transmitted over the network and while stored in the database. This helps protect sensitive information such as student names, student numbers, and email addresses.

## Logging

Logging should record important activities within the system.

Examples include:

- Successful and failed login attempts
- Access to student records
- Changes to user accounts
- Changes to IAM permissions
- Administrative activities
- Database access
- Security-related events

Logs can help administrators investigate security incidents and identify unauthorized activities.

## Monitoring

Monitoring should be used to identify suspicious or unusual activities.

Examples include:

- Repeated failed login attempts
- Unauthorized access attempts
- Unusual network traffic
- Unexpected changes to security settings
- Unusual database activity
- Suspicious administrator activity

Monitoring helps administrators respond to potential security threats quickly.

## Backup

The database should have regular backups to protect student information from data loss.

Backups can be used to recover information after accidental deletion, database corruption, system failure, or a security incident.

# Principle of Least Privilege

The Principle of Least Privilege means that each user should only receive the permissions required to perform their responsibilities.

| User | Allowed Access |
|---|---|
| Administrator | Full access to manage the cloud environment, application, security settings, and database permissions. |
| Instructor | Access to view and manage student records required for teaching responsibilities. |
| Student | Access to view their own permitted student information through the application. |
| Developer | Access to application code and development resources. Developers should not have unnecessary access to production student data or administrative settings. |

Administrator access should not be given to everyone because excessive permissions increase the risk of unauthorized changes, data exposure, and security incidents.

# Shared Responsibility Model

The Shared Responsibility Model divides security responsibilities between the cloud provider and the customer.

| Responsibility | Cloud Provider or Customer? |
|---|---|
| Physical data center | Cloud Provider |
| Physical servers | Cloud Provider |
| User accounts | Customer |
| Student data | Customer |
| IAM permissions | Customer |
| Application security | Customer |
| Database access rules | Customer |
| Backups | Customer |

## 1. What does Security OF the Cloud mean?

Security OF the Cloud refers to the security responsibilities handled by the cloud provider. This includes protecting the physical data centers, physical servers, networking infrastructure, and underlying cloud infrastructure.

## 2. What does Security IN the Cloud mean?

Security IN the Cloud refers to the security responsibilities handled by the customer. This includes protecting user accounts, student data, applications, IAM permissions, database access rules, and backups.

# Architecture Questions

## 3. Which resource should be directly accessible from the Internet?

The load balancer should be directly accessible from the Internet because it receives requests from users and forwards those requests to the application servers.

The CDN may also be publicly accessible because it delivers website content to users.

## 4. Why should the database remain private?

The database should remain private because it stores student information. Keeping the database private reduces the risk of unauthorized access, data theft, and data modification.

## 5. Why should users not connect directly to the database?

Users should not connect directly to the database because doing so could expose sensitive student information and increase the risk of unauthorized access or data manipulation.

Users should access the application through the load balancer and application servers instead.

## 6. What is the purpose of a load balancer?

A load balancer distributes incoming requests across multiple application servers. This improves performance, reliability, and availability.

## 7. What happens if one application server fails?

If one application server fails, the load balancer can redirect requests to another available application server. This allows the application to continue operating.

## 8. What is the purpose of a CDN?

A CDN delivers cached static content from locations closer to users. This improves website loading speed and reduces the workload on the application servers.

## 9. Why should administrator accounts use MFA?

Administrator accounts should use MFA because they have powerful permissions. MFA provides an additional layer of protection if an administrator's password is stolen or compromised.

## 10. Why should administrator access not be given to every employee?

Administrator access should not be given to every employee because administrators have powerful permissions. Giving unnecessary administrative access increases the possibility of accidental changes, unauthorized access, and security incidents.

## 11. Why are logging and monitoring important?

Logging and monitoring are important because they help detect suspicious activities, unauthorized access, failed login attempts, and other security problems.

Logs can also help administrators investigate security incidents and determine what happened.

## 12. Why are backups important?

Backups are important because they provide a way to recover student information if data is accidentally deleted, corrupted, lost, or affected by a security incident.
