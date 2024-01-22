# SampleMERNwithMicroservices

[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FSwapnashreeTripathy%2FMERN-Microservices-EndtoEnd-Deployment&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)

## Object:
1.	Containerize your microservice application using docker
2.	Create 3 Repositories in AWS ECR to Push the docker images into it respectively.
3.	Push the MERN application source code to the CodeCommit repository.
4.	Create a Jenkins Job for building and pushing Docker images to ECR.
5.	Create an Amazon EKS cluster and Use Helm to deploy the code on EKS.
6.	Setting up CloudWatch monitoring and Alarms for your MERN application.

## Prerequisites
Create an EC2 and make below Configures in it.<br>
2. Install & configure aws-cli<br>
3. Install Jenkins<br>
4. Install docker<br>
5. [Install EKSCTL](https://eksctl.io/installation/)<br>
6. [Install Kubectl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html)<br>

## Containerize your microservice application using docker:
- Write Dockerfile for Frontend and Backend Microservices to create an Image.
  Dockerfile For Frontend code.
  ```
  ```
  Dockerfile for Backend code. Our Backend has 2 serives(/helloserive & /profileservice).
  ```
  ```
- Create an Docker-Compose.yml file.
  ```
  ```
  
## Create 3 Repositories in AWS ECR to Push the docker images into it respectively:
- *****************Add AWS ECR Full access policy to your IAM user account/User role, so that you can access ECR via your IAM User role.***************
- In AWS ECR, click on Create Repository & create 3 different Public Repositories.
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/b602739e-0ac7-47a2-8f65-b4efc33c984f)
## Push the MERN application source code to the CodeCommit repository:
- To Access AWS CodeCommit , add "AWSCodeCommitFullAccess" policy into your IAM Account "Users" From IAM(Identity and Access Management) service.<br>
  Users --> select your User --> Add permission --> Select AWS code commit Full Access.
![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/21e101fd-95b3-4cd9-87f2-b7a405bb1eed)
- Once Policy is added to the IAM account,  Download the “HTTPS Git credentials for AWS CodeCommit”.<br>
  IAM --> users --> Security Credentials --> HTTPS Git credentials for AWS CodeCommit
![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/2ceb3dca-f220-4d68-b378-40d7c446ffdd)
- Create a Repository in Codecommit. 
- Connect to EC2(Clone your codes from Github repo to EC2) & Push your MERN Application Code from EC2 to AWS Codecommit by following the below command.
  * Configure codecommit credentials on EC2 .
    ```
    git config --global credential.helper '!aws codecommit credential-helper $@'
    git config --global credential.UseHttpPath true
    git init<br>
    git  add .<br>
    git commit -m "comment"
    git remote add codecommit <httprepo-of-codcommit>
    git git push codecommit main(here,main refers to the branch)
    ```
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/a8039be7-76c1-48f8-ae74-fb8dc3f56ac6)
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/10333504-efe5-48ff-9e3b-4487a05784c0)
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/70eb78a4-ef1e-42d5-80ab-ecb32008837d)
## Create a Jenkins Job for building and pushing Docker images to ECR:
****************************************WRITE HERE SWAPNA*********************************************************************************************************
## Create an Amazon EKS cluster and Use Helm to deploy the code on EKS:
- 
  




