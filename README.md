# SampleMERNwithMicroservices

[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FSwapnashreeTripathy%2FMERN-Microservices-EndtoEnd-Deployment&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)

## Object:
1.	Containerize your microservice application using docker
2.	Create 3 Repositories in AWS ECR to Push the docker images into it respectively.
3.	Push the MERN application source code to the CodeCommit repository.
4.	Create a Jenkins Job for building and pushing Docker images to ECR.
5.	Create an Amazon EKS cluster and Use Helm to deploy the code on EKS.
6.	Try to connect with Frontend and backend services using the DNS of Load Balancer from browser.
7.	Setting up CloudWatch monitoring and Alarms for your MERN application.

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
- Use the below `deployment.yml` code or `helm chart code` to Create EKS cluster in your AWS region.
  *****************Give here link of deployment.yml file********************************************************************************************************
  ***********************Give here helm.yaml file**************************************************************************************************************
- in this yaml file, We are creating 2 different PODs with 2 Replicas of each. Our Backend POD will have 2 containers running inside it and Frontend POD will have 1 Container.
- We are also creating 2 different `load balancer` services for backend and fronetend PODS to connect with the outside traffic.
- Now let's run the below commands to create the EKS cluster with region as `Oregeon`.
  
 ```
  eksctl create cluster --name swapna-eks-mern-deployment --region us-west-2 --nodegroup-name swapna-eks-workernodess --node-type t3.medium --nodes 2 --nodes-min 1 --nodes-max 3

  ################################defining the command################################
  eksctl create cluster 
  --name swapna-eks-mern-deployment <name of your Cluster>
  --region us-west-2  <aws region where you want your cluster to create>
  --nodegroup-name swapna-eks-workernodess<define nodegroup/workernode name> 
  --node-type t3.medium <type of EC2 instance/workernode>
  --nodes 2 <desired number of nodes to run>
  --nodes-min 1 
  --nodes-max 3
```
- To update kube-config file.
  ```
  aws eks --region us-west-2 update-kubeconfig --name swapna-eks-mern-deployment
  ```
- To run the Deployment.yml file.
  ```
  kubctl Apply -f deploy.yml
  ```
- EKS takes some time to create EKS cluster and all the reatled nodes , so you can view them by going to AWS EKS dashboard or you can run following command to view the same information.
  ```
  kubctl get deployments = to check created deployment
  kubectl get nodes -o wide   = To Check the information about the “NODE”
  kubectl get po -w = check pods
  kubectl get services --watch = check services
  ```
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/a5a3e143-b668-4629-a566-1b2ed5188801)
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/eb1ce8b0-abda-4618-9185-b36c2c7f0775)
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/0b8e70e4-6621-40e6-a9c5-6433952e7be8)
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/b06357aa-0c69-4426-a2da-002855a1ae96)

## Try to connect with Frontend and backend services using the DNS of Load Balancer from browser:
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/fe07f8b6-2b9d-47e4-afd0-1aef5244fbec)
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/48b9b1e4-f693-46aa-9d63-c1a82708f7fc)
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/77aa23c5-5ea6-4c12-b475-cc1031d635fe)
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/7b6dfa24-6d2b-4cf8-8a3b-4b54238144de)


## Setting up CloudWatch monitoring and Alarms for your MERN application:
- To have logs monitored by Cloudwatch for all of the componets of the EKS cluster, let's install Cloudwatch from "Add-ons" on EKS this Cluster.<br>
  so, `CloudWatch` Agent will get installed in each Node running iside the Cluster & it’ll also `Enable Container Insights` in the Cluster so that Cloudwatch will monitor all the Container   
  Insights.<br>
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/dfd53508-39ed-4316-bad4-2d555ee5c9c3)
  ![image](https://github.com/SwapnashreeTripathy/MERN-Microservices-EndtoEnd-Deployment/assets/139486876/c64bd93f-1f4f-41ce-a8a6-cf506884cec1)

