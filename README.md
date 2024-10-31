# Scalable and Secure AWS Architecture for a WordPress News Platform
A three-tier, scalable, and secure architecture on AWS for the [Daily Scope News](https://dailyscope.online) WordPress platform, supporting growth and high traffic.

## Project Overview
This repository reveals the design and planned implementation of a three-tier architecture on AWS for a scalable Wordpress-baed news website. Starting with a prototype hosted on AWS Lightsail, this project has evolved to address the anticipated growth in users, advertisers and content contributors for our future Daily Scope News platform.

The solution emphasizes on scalability, security and high availability to ensure timely content delivery and robust protection against potential threats.

## Current Prototype on Lightsail
![Current Prototype for Daily Scope News on Lightsail](https://github.com/evans-kithinji/news-site-scalable-architecture/blob/main/monolythicStructureEC2Lightsail.png?raw=true)

My initial setup was a straightforward monolithic architecture hosted on a single Lightsail instance, using a Bitnami WordPress stack:
- Single instance setup: Combines web server, application logic, and database, accessible via a static public IP.
- Limitations: Limited scalability, single point of failure, and restricted security configurations.
While suitable for development, this monolithic setup is not ideal for scaling with future traffic and content demands.

## DNS Records Configuration
![Route 53 Daily Scope News initial configuration](https://github.com/evans-kithinji/news-site-scalable-architecture/blob/main/route53Records.png?raw=true)

In addition to managing our A and WWW alias records, we also host our email services with Zoho. This requires the configuration of several additional DNS records, including MX (Mail Exchange) and TXT (Text) records. These records ensure proper email delivery and verification. The created email can be used later in configuring wordpress.


## Planned AWS Architecture
![Daily Scope News proposed AWS Architecture](https://github.com/evans-kithinji/news-site-scalable-architecture/blob/main/threeTierArchitectureDailyNewsOnline.png?raw=true)

The new multi-tier architecture is designed to overcome these challenges by decoupling components, allowing for independent scaling, and providing a highly secure environment. Below is a breakdown of the architecture:

1. Content Delivery and DNS:
   - Route 53 manages DNS, routing users to the nearest servers.
   - CloudFront (CDN) caching static content (images, videos) across multiple edge locations to reduce latency.
2. Storage:
   - Amazon S3 stores static assets, offering seamless scalability for growing content volume. S3 is accessed only through CloudFront via Origin Access Control for enhanced security.
3. Application Layer:
   - EC2 Auto Scaling with Elastic Load Balancer (ELB) hosts the WordPress application, distributing traffic across instances in multiple Availability Zones for reliability and scalability.
   - Private subnets house the application servers, restricting public internet access for added security.
4. Database Layer:
   - Amazon RDS (Relational Database Service) in a Multi-AZ configuration provides data redundancy and high availability.
5. Network Security:
   - AWS Network Firewall and NAT Instances in public subnets will manage inbound and outbound traffic to private subnets.
   - AWS WAF to integrate with CloudFront to guard against web-based threats.
  
## Benefits of This Architecture
- **Scalability**: Elasticity in the application layer and CloudFront’s caching ensure smooth handling of traffic spikes and content growth.
- **High Availability**: Multi-AZ deployments for both application and database layers reduce the risk of downtime.
- **Enhanced Security**: Private subnets, NAT gateways, and WAF protect the environment from unauthorized access and cyber threats.

## Future Implementation: Daily Scope News Platform
Looking ahead, I plan to implement this architecture for Daily Scope News, a rapidly growing news website that will serve a larger audience, including advertisers and content producers. This platform will rely on AWS’s robust infrastructure to deliver content securely and efficiently, regardless of spikes in demand or content expansion.

## Acknowledgment
This project is part of Challenge 1 of the CloudForceSky Weekly Challenges.
![CloudForce Sky Weekly Challlenge One](https://github.com/evans-kithinji/news-site-scalable-architecture/blob/main/CloudForceSky_Challenge_1.pdf)

I am grateful for the hands-on learning and guidance provided by CloudForceSky, enabling myself and others to design solutions for real-world scalability and security needs.
