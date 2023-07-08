# Deploy a Java based Application with CICD in k8s using Jenkins, GitHub Pipeline, Docker, SonarQube and ArgoCD


In this project i did an end to end deployment of a spring-boot-app in kubernetes cluster using; **ArgoCD**, **Jenkins**, **Docker pipeline**, **SonarQube** and **GitHub Pipeline**

## Project Overview


![argocd cicd](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/45e0d379-be7a-4e17-b91d-5baa511a8843)





The Project is divided into two sections; **Continous Integration(CI)** and **Continous Deployment(CD)**

Below are the steps taken to complete this project.

## STEPS for Continous Integration(CI)
1. Launch an ubuntu ec2 machine and ssh into it.
1. update package manager
2. install java openjdk-11
3. add and save jenkins package sign-in key
4. add and save jenkins package repository
5. update package manager
6. install jenkins 
7. locate the jenkins admin password
8. access jenkins with server public IP on port 8080
9. enter admin password and allow suggested plugin download
10. setup username and password (jenkins default username:password is admin:admin)
11. navigate to manage jenkins and select plugins
12. add docker pipeline and sonarqube scanner plugins from the available plugins tab
13. install and restart jenkins
14. on the cli, update the package manager and install docker so we can pull and use our maven image as our jenkins effemeral slave
15. after docker installation, navigate to root and add jenkins and ubuntu (in this case) users to the docker group and restart docker daemon
16. Create a sonarqube user who own sonarqube package in the server
17. Change to our sonarqube user and install sonarqube for scanning our code
18. we can now access sonarqube on the web browser and login with admin/admin…thereafter you can change your username and password…access is via server publicIP on port 9000.
19. now lets integrate our SCM (github), our container registry (dockerhub) and our code analysis tool (sonarqube) with jenkins…restart jenkins after this.
20. we can now build our jenkins pipeline using the pipeline option
21. we will also update our jenkinsfile to reflect the sonarqube ip address before we run the job.
22. now lets run the job… our expected outcome is the final artifact is containerized as a docker image and pushed to dockerhub with the build number as the tag.
23. we should also check our SCM (github) repo to confirm that the manifest file has been updated to reflect the new image tag.



## Launch an EC2 machine and SSH into it.


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/b99f397d-9388-4bbd-ab88-45e66b6c622c)


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/ce1d7f7d-6c60-4997-b8b2-909a5cbcb39d)


## Install Jenkins, configure Docker as agent, set up cicd, deploy applications to k8s and much more.

To run any specific installation command click on this link; [Project Installation Commands](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/blob/main/Project%20Installation%20Commands)



## Login to Jenkins using the below URL:
http://:8080 [You can get the ec2-instance-public-ip-address from your AWS EC2 console page]

Note: If you are not interested in allowing All Traffic to your EC2 instance 1. Delete the inbound traffic rule for your instance 2. Edit the inbound traffic rule to only allow custom TCP port 8080

After you login to Jenkins, - Run the command to copy the Jenkins Admin Password - sudo cat /var/lib/jenkins/secrets/initialAdminPassword - Enter the Administrator password



![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/a145234d-80e5-4429-bbcb-c1bf6956762e)



## Click on Install suggested plugins


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/875e75c2-593e-4102-bbbc-b8e4f64857f8)

Wait for the Jenkins to Install suggested plugins

![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/ce852f5a-35ff-40d4-9306-c2f827ab46ac)



Create First Admin User or Skip the step [If you want to use this Jenkins instance for future use-cases as well, better to create admin user]


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/5a046df9-4112-46d0-b446-41182545d7f1)


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/5eeb3bfb-3a53-4225-ae86-c51e13b034aa)


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/58b8bdaa-c604-4fef-a1e0-376a40025ac2)




## Install docker pipeline and Sonarqube plugin

![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/933e00d1-5827-4637-97e2-5e5c22ebf5af)

![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/0e756195-5743-4c29-a0a6-a4f02c224142)


## Configure a Sonar Server

To do this,  Click on this link; [Project Installation Commands](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/blob/main/Project%20Installation%20Commands)


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/abc0a457-6c12-4a7d-b4f0-784c30f6c914)



## Integrate our SCM (github), our container registry (dockerhub) and our code analysis tool (sonarqube) with jenkins using credentials


##  Build jenkins pipeline using the pipeline option


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/d2c2c5f7-8e5b-4d4a-8065-65dcd4085a4b)



##  now lets run the job

Before this, ensure to update the jenkinsfile to reflect the sonarqube ip address



![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/3e19cffb-5d6e-4239-b1c2-0e22f64a7420)


Hurraaaaaaay!!!!

The Job succeeded after the 3rd attempt.


## Check the sonar server to see if the sonar configuration has passed


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/ec637a0d-a34f-4fa0-84c6-0880bc59a67a)



Yes it has.



## Check the SCM (github) and docker repo to confirm that the manifest file has been updated to reflect the new image tag


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/cbf0c84b-03dd-40d5-90ce-20bcd601e9bb)

![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/6795ac1d-278a-43a9-869d-8bc1908999f0)

![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/208c90a3-2aec-4c74-b473-2de6fdb7244b)



That does it for the **Continous integration(CI)** part of the project, next is to proceed to the **Continous Deployment(CD)** part




## Set up ArgoCD on Kubernetes cluster to deploy our spring boot app

For my ArgoCD set up, i used terraform to provision AWS EKS cluster and installed the argocd server. Click on this link; [ArgoCD installation using Terraform with AWS EKS](https://github.com/georgeonalo/aws-eks-terraform)



![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/1fc0ef42-d6a8-4954-b909-23d5d22b3e12)




## Create Application

Click on create application in the ArgoCD home page and enter **Application name**, **Project name**, enter 'Automatic' for **SYNC POLICY**, scroll down and provide the **Repository URL, Path, Cluster URL** and enter default for **NAMESPACE**, then click **Create**


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/8635eaf3-97fa-4e7f-b054-762f8fff7f42)

![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/fe2c1ede-02b9-4218-af26-2148429ed81c)

![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/ecf0d38d-98e8-42f3-9e42-ec76f40e529f)

![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/2ace7c12-b908-4269-93ac-50d2bb93dc2c)


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/42dabb82-6970-41bb-bba1-ffd3d84586e8)


![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/73b23a59-9853-42f2-90cc-2633b56e702a)


So there you have it, our application is deployed.

## Run the commands below to see the deployments and pods

```
kubectl get deploy
kubectl get pod
```

![image](https://github.com/georgeonalo/CICD-Jenkins-ArgoIM-ArgoCD-Pipeline/assets/115881685/fc92f8e3-7eb9-40a5-84d0-367c82d8ec97)


They are all running



Resources: https://youtu.be/JGQI5pkK82w
https://youtu.be/tYExh_tNRvk
































