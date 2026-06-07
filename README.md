
Project Overview: This project demonstrates the deployment of a highly available web application infrastructure on AWS using core networking and compute services.

The architecture was designed to provide:

* High Availability
* Load Balancing
* Automatic Scaling
* Secure Network Segmentation
* Health Monitoring

## AWS Services Used

* Amazon VPC
* Public and Private Subnets
* Route Tables
* Internet Gateway
* NAT Gateway
* Network ACLs (NACL)
* Security Groups
* Application Load Balancer (ALB)
* Target Groups
* Launch Templates
* Auto Scaling Groups (ASG)
* Amazon EC2
* Bastian Host

## Architecture

Internet >>> Application Load Balancer >>> Target Group >>> Auto Scaling Group >>> EC2 Instances

## Key Learnings

* Configured Security Groups and NACLs
* Implemented Application Load Balancer health checks
* Deployed EC2 instances using Auto Scaling Groups
* Learned the difference between Security Groups and NACLs
* Troubleshot failed health checks
* Understood the role of ephemeral ports (1024-65535) in NACL configurations

## Project Status

Completed as a hands-on AWS infrastructure learning project.
