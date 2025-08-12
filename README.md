# 7-Day DevOps Challenge: CI/CD Pipeline with AWS

**Author:** Rahman Hashmi  
**Email:** rahmanhashmi53@gmail.com

---


## Introduction

In this 7-Day DevOps Challenge, I built a complete CI/CD pipeline using AWS services. Each day, I learned new tools and techniques, gaining hands-on experience with DevOps concepts and AWS cloud infrastructure.

I dedicated myself to spending 3 hours daily to build a practical CI/CD pipeline.

- **Key Concepts:**
  - DevOps practices
  - CI/CD pipeline foundations

---

## Architecture Overview

![End-to-end CI/CD architecture on AWS](https://github.com/rahmanhashmi53/nextwork-web-project/blob/master/Diagrams/Project_%20Architecture.png?raw=true)
:--:
**Architecture Overview**

---

## Day 1: Set Up a Web App in the Cloud

- **Tools & Technologies:** AWS EC2, VS Code, SSH, Maven, Java
- **Activities:**
  - Launched EC2 instances
  - SSH connections
  - Created Java web application with Maven archetypes 
 
![Day 1 focus: EC2 provisioning and app setup](https://github.com/rahmanhashmi53/nextwork-web-project/blob/master/Diagrams/Set%20Up%20a%20Web%20App%20in%20the%20Cloud.png?raw=true) 
:--:
*Day 1 — EC2 provisioning & app setup* 
---

## Day 2: Connect a GitHub Repository

- **Tools & Technologies:** Git, GitHub
- **Activities:**
  - Initialized local Git repository
  - Git commands (`add`, `commit`, `push`)
  - GitHub authentication using Personal Access Tokens
  - Created README file in Markdown

![Day 2 focus: Git & GitHub source integration](https://github.com/rahmanhashmi53/nextwork-web-project/blob/master/Diagrams/Connect%20a%20GitHub%20Repo%20with%20AWS.png?raw=true)
:--:
*Day 2 — Git & GitHub source integration*


---

## Day 3: Secure Packages with CodeArtifact

- **Tools & Technologies:** AWS CodeArtifact, IAM, EC2, Maven
- **Activities:**
  - Created artifact repositories with CodeArtifact
  - Configured IAM roles and policies
  - Connected Maven with CodeArtifact
  - Published custom packages to the repository

![Day 3 focus: CodeArtifact for dependency management](https://github.com/rahmanhashmi53/nextwork-web-project/blob/master/Diagrams/Store%20Dependencies%20in%20CodeArtifact.png?raw=true)
:--:
*Day 3 — CodeArtifact for dependencies*

---

## Day 4: Continuous Integration with CodeBuild

- **Tools & Technologies:** AWS CodeBuild, CodeConnection, CodeArtifact, S3, EC2, GitHub
- **Activities:**
  - Set up automated build process
  - Integrated CodeBuild with GitHub using CodeConnections
  - Created `buildspec.yml`
  - Automated testing scripts
  - Stored build artifacts in S3

![Day 4 focus: CodeBuild CI stage](https://github.com/rahmanhashmi53/nextwork-web-project/blob/master/Diagrams/Package%20an%20App%20with%20CodeBuild.png?raw=true)
:--:
*Day 4 — CodeBuild (CI)*

---

## Day 5: Deploy a Web App with CodeDeploy 

- **Tools & Technologies:** AWS CodeDeploy, CloudFormation, EC2, S3
- **Activities:**
  - Automated deployment process
  - Developed deployment scripts (`install_dependencies.sh`, `start_server.sh`, `stop_server.sh`)
  - Defined deployment phases using `appspec.yml`
  - Set up rollback strategies and deployment configurations
  - Handled intentional errors for disaster recovery testing

![Day 5 focus: CodeDeploy to EC2](https://github.com/rahmanhashmi53/nextwork-web-project/blob/master/Diagrams/Deploy%20a%20Web%20App%20with%20CodeDeploy.png?raw=true) 
:--:
*Day 5 — CodeDeploy to EC2*

---

## Day 6: Infrastructure as Code with CloudFormation

- **Tools & Technologies:** AWS CloudFormation, CodeBuild, CodeDeploy, CodeArtifact, S3, IAM, EC2
- **Activities:**
  - Defined all CI/CD resources (EC2, S3, IAM, etc.) in a single CloudFormation template
  - Fixed race conditions and circular dependency issues using `DependsOn`
  - Manually added missing CodeBuild and CodeDeploy resources to template
  - Used parameters for reusable templates
  - Deployed full stack from template and verified through AWS console

![Day 6 focus: CloudFormation resources and IaC](https://github.com/rahmanhashmi53/nextwork-web-project/blob/master/Diagrams/Infrastructure%20as%20Code%20with%20CloudFormation.png?raw=true) 
:--:
*Day 6 — CloudFormation (IaC)*


---

## Day 7: Build a CI/CD Pipeline with CodePipeline

- **Tools & Technologies:** AWS CodePipeline, CodeBuild, CodeDeploy, GitHub, IAM
- **Activities:**
  - Connected GitHub, CodeBuild, and CodeDeploy in one automated workflow
  - Configured pipeline stages: Source, Build, Deploy
  - Enabled webhook triggers for automatic pipeline execution
  - Tested and verified pipeline automation
  - Practiced rollback and disaster recovery strategies

![Day 7 focus: CodePipeline orchestration](https://github.com/rahmanhashmi53/nextwork-web-project/blob/master/Diagrams/Build%20a%20CI-CD%20Pipeline%20with%20AWS.png?raw=true) 
:--:
*Day 7 — CodePipeline orchestration*

---

## Project Reflection

Completing the 7-Day DevOps Challenge enhanced my practical skills in building CI/CD pipelines and automated deployments. Troubleshooting and resolving pipeline errors deepened my understanding of AWS services and DevOps practices. It was rewarding to see the automated pipeline reliably handling code changes from GitHub through deployment on AWS EC2.

---

## View Detailed Projects

- [CI/CD Pipeline Overview](http://learn.nextwork.org/projects/aws-devops-cicd)
- [Setup Web App](http://learn.nextwork.org/projects/aws-devops-vscode)
- [Connect GitHub](http://learn.nextwork.org/projects/aws-devops-github)
- [Secure with CodeArtifact](http://learn.nextwork.org/projects/aws-devops-codeartifact-updated)
- [Continuous Integration with CodeBuild](http://learn.nextwork.org/projects/aws-devops-codebuild-updated)
- [Deploy with CodeDeploy](http://learn.nextwork.org/projects/aws-devops-codedeploy-updated)
- [Infrastructure as Code with CloudFormation](http://learn.nextwork.org/projects/aws-devops-cloudformation-updated)
- [Build CI/CD with CodePipeline](http://learn.nextwork.org/projects/aws-devops-codepipeline-updated)

---

Thank you for joining my journey in the 7-Day DevOps Challenge!
