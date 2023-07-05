# Deploy a java spring-boot-app in kubernetes with ArgoCD


In this project i did an end to end deployment of a spring-boot-app in kubernetes cluster using; **ArgoCD**, **Jenkins**, **Docker pipeline**, **SonarQube** and **GitHub Pipeline**

The Project is divided into two sections; **Continous Integration(CI)** and **Continous Deployment(CD)**

Below are the steps taken to complete this project, please note to run any specific command click on this link; [Project Installation Commands]()

## STEPS
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
14. on the cli, lets update the package manager and install docker so we can pull and use our maven image as our jenkins effemeral slave
15. after docker installation, navigate to root and add jenkins and ubuntu (in this case) users to the docker group and restart docker daemon
16. we now need to create a sonarqube user who own sonarqube package in the server
17. now lets change to our sonarqube user and install sonarqube for scanning our code
18. we can now access sonarqube on the web browser and login with admin/admin…thereafter you can change your username and password…access is via server publicIP on port 9000.
19. now lets integrate our SCM (github), our container registry (dockerhub) and our code analysis tool (sonarqube) with jenkins…restart jenkins after this.
20. we can now build our jenkins pipeline using the pipeline option
21. we will also update our jenkinsfile to reflect the sonarqube ip address before we run the job.
22. now lets run the job… our expected outcome is the final artifact is containerized as a docker image and pushed to dockerhub with the build number as the tag.
23. we should also check our SCM (github) repo to confirm that the manifest file has been updated to reflect the new image tag.





