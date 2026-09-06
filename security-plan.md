# Secure Cloud Architecture Plan

## Architecture

Users
↓
CDN
↓
Load Balancer
↓
Application Servers
↓
Private Database

## CDN

The CDN stores cached copies of static content closer to users to improve loading speed and reduce the load on the application servers.

## Load Balancer

The load balancer receives incoming requests and distributes them across multiple application servers. This improves performance, availability, and reliability.

## Application Servers

The application servers process requests from users and handle the application logic. They should be placed in a private subnet so they are not directly exposed to the Internet.

## Database

The database stores student records and other application data. It should remain private and should not be directly accessible from the Internet.
