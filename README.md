# Deployment of node.js application using Jenkins CICD with GitHub Integration
 	 
Objective	- Deploy Basic node.js app using Jenkins CICD with GitHub Integration
- Trigger Jenkins pipeline automatically once the code is pushed on GitHub
Approach	- Using Amazon's Elastic Compute Cloud (EC2) for running application on the Amazon Web Services (AWS) infrastructure
- Containerize application by creating Dockerfile
- Integrate GitHub with Jenkins using Webhook
Impact	- Jenkins pipeline triggers automatically once the code is pushed on GitHub
- Accomplish faster quality releases by automating CI/CD pipelines





Primary Technology: Github, Docker, Jenkins, aws EC2 service
![image](https://github.com/malakMkh/Simple-CICD-using-jenkins/assets/123992427/532579d5-5ecd-4351-9d1d-b81fc9f34c31)

configuration de  projet Jenkins avec un script shell directement dans la configuration du projet (plutôt que d'utiliser un fichier Jenkinsfile dans votre dépôt Git),
Steps:
1. Creating an AWS ec2 instance with ubuntu AMI.
2. Accesing the ec2 over SSH by PUTTY.
3. Installing the Java and then Jenkins server.
4. Configuration of the Jenkins with default settings and plugins.
5. Integration  of  Github from EC2 and  Jenkins server.
6. Installation of Nodejs and NPM.
7. Installation of Docker.
8. Basic Dockerfile creation and adminstration.
9. Basic Jenkins administartion for creating freestyle projects .
10. Creating Webhooks for auto triggering the build process when any       change is made on GitHub repository.
11. Testing the CICD PIPELINE.

12. --------------------------------------------------------------------------------------------------------------------------------------------------------------
 1. Creating a Node App
Before we write any CI/CD pipeline we need an application to test and deploy. We are going to build a simple to-do application in node.js
2. Creating AWS EC2 instance
2.1 Creating AWS EC2 instance
After logging into your AWS account, search for EC2
2.2 Connecting AWS EC2 instance using putty/public adress add ssh private key
3. Installing Jenkins on AWS
3.1 Installing Java
Install Java using following commands:
sudo apt update
sudo apt install openjdk-22-jre
java -version
3.2 Start Jenkins
Start jenkins using following commands:
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
3.3 Open port 8080 from AWS Console
 3.4 Unlock Jenkins
3.5 Connect GitHub and Jenkins
Create new job by clicking New item
3.6 Get code in jenkins
In jenkins, click on Build Now on the left pane
3.7 Change permission of inbound traffic of port 8000
Click Add rule and enter port number 8000 and select Anywhere IPv4 it can be accessed by anyone. Click Save rules
3.8 Run node.js application
4. Automating using Docker
4.1 Install Docker
Remove Dockerfile and install Docker using following command:
sudo rm Dockerfile
sudo apt install docker.io
4.2 Create Dockerfile
Edit Dockerfile using the command sudo vim Dockerfile and add following commands within it:
FROM node:12.22.9-alpine
WORKDIR app
COPY . .
RUN npm install
EXPOSE 4000
CMD ["npm", "start"]
4.3 Build Docker
On console, enter the following commands: sudo usernod -a -G docker $USER
sudo reboot
To give permission to docker and reboot the system
4.4 Run Docker
5. Automating using Jenkins (CICD pipelines)
5.1 Automating commands using Jenkins (Execute shell)
On console, enter the following commands to terminate a container:
docker ps
docker kill
6. Trigger Jenkins pipelines automatically once the code is pushed on GitHub (Webhooks)
6.1 Install plugin
6.2 Configure webhook in GitHub
   Testing
Go to GitHub project repository and edit the project. Click Commit changes
