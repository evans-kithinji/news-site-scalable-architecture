# Scalable and Secure AWS Architecture for a WordPress News Platform
A three-tier, scalable, and secure architecture on AWS for the [Daily Scope News](https://dailyscope.online) WordPress platform, supporting growth and high traffic.

## Project Overview
This repository reveals the design and planned implementation of a three-tier architecture on AWS for a scalable Wordpress-baed news website. Starting with a prototype hosted on AWS Lightsail, this project has evolved to address the anticipated growth in users, advertisers and content contributors for our future Daily Scope News platform.

The solution emphasizes on scalability, security and high availability to ensure timely content delivery and robust protection against potential threats.

## Current Prototype on Lightsail
![Alt Text](https://github.com/evans-kithinji/news-site-scalable-architecture/blob/main/monolythicStructureEC2Lightsail.png?raw=true)
Our initial setup was a straightforward monolithic architecture hosted on a single Lightsail instance, using a Bitnami WordPress stack:
- Single instance setup: Combines web server, application logic, and database, accessible via a static public IP.
- Limitations: Limited scalability, single point of failure, and restricted security configurations.
While suitable for development, this monolithic setup is not ideal for scaling with future traffic and content demands.
