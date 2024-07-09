# Jenkins END-TO-END CI-CD-Pipeline
An end-to-end Continuous Integration and Continuous Deployment (CI/CD) pipeline for a Netflix application using Jenkins, GitHub, Maven, SonarQube, and Tomcat. This project automates the process of building, testing, analyzing, and deploying a Java web application, ensuring code quality and streamlined deployment.

## Project Overview

The pipeline performs the following steps:
1. **Checkout**: Fetches the code from a GitHub repository.
2. **Build**: Compiles the code using Maven.
3. **Test**: Runs tests on the compiled code.
4. **Code Quality**: Analyzes the code quality using SonarQube.
5. **Artifact**: Packages the application into a WAR file.
6. **Deploy**: Deploys the WAR file to a Tomcat server.

## Tomcat Setup
## Installation
### Download and extract Tomcat:
```
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.80/bin/apache-tomcat-9.0.80.tar.gz
tar -zxvf apache-tomcat-9.0.80.tar.gz && cd apache-tomcat-9.0.80
```
## Configuration
### Configure Tomcat:

Edit
vim apache-tomcat-9.0.90/webapps/manager/META-INF/context.xml to delete line 21 and 22.

Edit 
```
vim apache-tomcat-9.0.90/conf/tomcat-users.xml
```
add the following lines at the end
```
<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<user username="tomcat" password="raham123" roles="manager-gui,manager-script"/>
```
## Start Tomcat:
```
sh apache-tomcat-9.0.90/bin/startup.sh
```
### Access the Tomcat manager app at http://<public-ip>:8080/manager, using:

Username: tomcat
Password: raham123
Jenkins Configuration
Download the Plugin: Install the "Deploy to container" plugin in Jenkins.

## Add Credentials:

Go to Manage Jenkins -> Manage Credentials -> Global -> Add Credentials.
Select Username with password and enter:
Username: tomcat
Password: raham123
Save the credentials.

## Troubleshooting
### SonarQube
Ensure the SonarQube server and service are running.
Update the public IP in the pipeline script if necessary.

### Deployment
Check Tomcat logs for deployment issues:
```
tail -100f /root/apache-tomcat-9.0.80/logs/catalina.out
```
Edit
```
vim apache-tomcat-9.0.90/root/apache-tomcat-9.0.80/conf/server.xml:
```
Change 8080 to 8090 on line 69.

## Restart Tomcat:
```
sh apache-tomcat-9.0.90/bin/shutdown.sh
sh apache-tomcat-9.0.90/bin/startup.sh
```
## Viewing the Deployed Application
After deploying the application, you can view it by navigating to the following URL in your web browser:

http://<public-ip>:8090/netflix/
Replace <public-ip> with the public IP address of your Tomcat server.
