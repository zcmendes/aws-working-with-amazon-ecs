# AWS Working with Amazon ECS

Hands-on lab demonstrating container orchestration using Amazon Elastic Container Service (ECS).

## Architecture

![Architecture](architecture/ecs-lab-architecture.png)

## Architecture Overview

This lab environment consists of:

- Amazon VPC
- Two Public Subnets
- Internet Gateway
- Network Load Balancer
- Amazon ECS Cluster
- Amazon EC2 Container Instances
- Auto Scaling Group

Traffic flow:

```text
Internet
    ↓
Network Load Balancer
    ↓
ECS Service
    ↓
ECS Tasks
```

## AWS Services Used

- Amazon ECS
- Amazon EC2
- Auto Scaling Group
- Network Load Balancer
- Amazon VPC
- AWS CloudFormation

## Lab Objectives

- Create ECS Task Definitions
- Deploy ECS Services
- Update Applications
- Scale Running Services

## ECS Task Definition

The application is composed of two containers:

### simple-app

- Image: `httpd:2.4`
- Exposes port 80
- Serves web content through Apache HTTP Server

### busybox

- Image: `busybox`
- Generates dynamic HTML content
- Updates the application page continuously

Both containers share a Docker volume, demonstrating the Sidecar Container Pattern.

## Deployment Workflow

1. Create Task Definition Revision 1
2. Deploy ECS Service
3. Validate application through Network Load Balancer
4. Create Task Definition Revision 2
5. Perform rolling deployment update
6. Scale service from 1 to 2 tasks


## ECS Service Deployment

An ECS Service named `myFirstService` was created using the EC2 launch type.

Configuration highlights:

- Cluster: ECSCluster
- Launch Type: EC2
- Scheduling Strategy: Replica
- Desired Tasks: 1
- Running Tasks: 1
- Load Balancer: Network Load Balancer
- Deployment Status: Completed

The ECS scheduler automatically maintained the desired task count and distributed workloads across the available container instances.

## Screenshots

### Task Definition Revision 1

![Task Definition](screenshots/01-task-definition-v1.png)

### ECS Service Creation

![Service Creation](screenshots/02-service-created.png)

### Task Definition Revision 2

![Task Definition V2](screenshots/06-task-definition-v2.png)


### Running Tasks

![Running Tasks](screenshots/03-running-task.png)


### Application Version 1

![Application V1](screenshots/05-application-v1.png)

### Task Definition Revision 2

![Task Definition V2](screenshots/06-task-definition-v2.png)

### Rolling Deployment

![Deployment Update](screenshots/07-deployment-update.png)

### Application Version 2

![Application V2](screenshots/08-application-v2.png)

### Service Scaling

![Service Scaling](screenshots/09-service-scaled.png)

## Skills Demonstrated

- Container Orchestration
- Amazon ECS
- Docker Concepts
- Sidecar Container Pattern
- Rolling Deployments
- Load Balancing
- High Availability
- Horizontal Scaling
- Infrastructure as Code (CloudFormation)

## Learning Outcomes

By completing this lab, I gained practical experience with:

- Creating and managing ECS Task Definitions
- Deploying applications using ECS Services
- Integrating ECS with a Network Load Balancer
- Performing rolling application updates
- Scaling ECS services horizontally
- Understanding container communication through shared volumes
- Reviewing Infrastructure as Code (IaC) using AWS CloudFormation

## Author

Ze Mendes

Cloud | Cybersecurity | DevOps
