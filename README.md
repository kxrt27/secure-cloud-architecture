# Secure Cloud Architecture

## Student Information

Name: Kurt M. Paguirigan  
Section: CCIS 7E  
Course: Cloud Computing  
Date: September 6, 2026

## Project Description

This activity demonstrates a proposed secure cloud architecture for a Student Management Application.

The application allows users to view student information through a simple web interface. The proposed architecture focuses on basic cloud networking, security controls, resource access, and the Shared Responsibility Model.

## Architecture

Users → CDN → Load Balancer → Application Servers → Private Database

## Security Controls

- IAM
- MFA
- Firewall / Security Groups
- Private Subnets
- Encryption
- Logging
- Monitoring
- Backups

## Public and Private Resources

The CDN and Load Balancer are public-facing resources because they receive requests from users through the Internet.

The Application Servers and Database should remain private. The database should never be directly accessible from the Internet.

## Security Approach

The architecture follows the principle of least privilege. Users and employees should only receive the permissions required for their responsibilities.

Sensitive student information should be protected using encryption, access controls, logging, monitoring, and regular backups.

## Shared Responsibility Model

The cloud provider is responsible for security of the cloud infrastructure, such as physical data centers and physical servers.

The customer is responsible for security in the cloud, including user accounts, student data, application security, IAM permissions, database access rules, and backups.
