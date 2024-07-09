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
