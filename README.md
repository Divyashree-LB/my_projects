                                                       My CICD project

This app will be used for your CI/CD Pipeline with Jenkins + Docker + ArgoCD.

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/cd9bafe2-956d-4e6b-95a5-040d978ec0c7" />


--------------------------------Step1: Building application-----------------------------------------------------------------
project structure
myspringapp/
 ├─ k8/                         # Kubernetes manifests
 │   ├─ deployment.yaml
 │   └─ service.yaml
 ├─ src/
 │   └─ main/
 │       ├─ java/com/example/myspringapp/
 │       │    ├─ MySpringAppApplication.java
 │       │    └─ HelloController.java
 │       └─ resources/
 │            └─ application.properties
 ├─ target/                      # Maven build output (JARs)
 ├─ Dockerfile                   # Docker image build
 ├─ jenkinsfile                  # CI/CD pipeline
 ├─ argocd-svc-nodeport.yaml     # Expose ArgoCD server
 ├─ pom.xml                      # Maven config
 ├─ README / README.md           # Docs1. pom.xml

1. pom.xml
 :: This is a Maven configuration file.
   It tells Maven:  
•	This is a Spring Boot project" 
•	Download Spring Boot packages"
•	Build a JAR file"
2. MySpringAppApplication.java
 :: This is like the main function.
•	When the app starts, this file runs first.
•	It tells Spring Boot to start a web server on port 8080
3. HelloController.java
 ::  This file controls what message you see on browser
Spring Boot = Java framework to build APIs/websites
Maven = A tool that builds your Java project.Build and dependency manager
----------------------step2: Testing application on localmachine------------------------------------------------------
Pre-requisits: Install java and maven on ec2
sudo apt update
sudo apt install -y openjdk-17-jdk maven
java -version   # openjdk version "17.0.16" 2025-07-15
mvn -version  # Apache Maven 3.8.7
1.Build the project
mvn clean package    
•	if build is success target/folder created and inside target--> spring_demo-1.0.0.jar created
2.run jar file
java -jar target/spring_demo-1.0.0.jar
 
<img width="940" height="504" alt="image" src="https://github.com/user-attachments/assets/754b283a-6e0a-4ce2-af5c-e26cf78efb6b" />

3. open custom TCP 9090 port in inbound rules of AWS EC2 instance
4.copy the public IP and open browser and run http://<publicIP>:9090/

 <img width="817" height="300" alt="image" src="https://github.com/user-attachments/assets/36a719f0-408b-40f7-844c-a85432606303" />

4.Push your code to your Github repository
5.install Jenkins on ec2 and trigger pipleline from SCM
Optional: you can add webhook in git and enable trigger in your job

http://13.203.196.249:8080/github-webhook/




