# SampleMERNwithMicroservices

[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FSwapnashreeTripathy%2FMERN-Microservices-EndtoEnd-Deployment&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)

## Object:
1.	Containerize your microservice application using docker
2.	Push the Images to the AWS ECR repository.
3.	Push the MERN application source code to the CodeCommit repository.
4.	Create a Jenkins Job for building and pushing Docker images to ECR.
5.	Create an Amazon EKS cluster and Use Helm to deploy the code on EKS.
6.	Setting up CloudWatch monitoring and Alarms for your MERN application.

## Prerequisites
Create an EC2 and make below Configures in it. 
2. Install & configure aws-cli
3. Install Jenkins
4. Install docker
5. Install EKSCTL
6. Install Kubectl

# Containerize your microservice application using docker:
- Write Dockerfile for Frontend and Backend Microservices to create an Image.
Dockerfile For Frontend code.
```
```
Dockerfile for Backend code. Our Backend has 2 serives(/helloserive & /profileservice).

