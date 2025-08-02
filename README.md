<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a CI/CD Pipeline with AWS

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codepipeline-updated)

**Author:** Rahman Hashmi  
**Email:** rahmanhashmi53@gmail.com

---

![Image](http://learn.nextwork.org/energetic_lavender_silly_sow/uploads/aws-devops-codepipeline-updated_fbdetger)

---

## Introducing Today's Project!

In this project, I will demonstrate how to build a complete CI/CD pipeline using AWS CodePipeline. I'm doing this project to learn how to connect GitHub, CodeBuild, and CodeDeploy into one automated workflow that builds and deploys my web app whenever I push code.

### Key tools and concepts

Services I used were AWS CodePipeline, CodeBuild, CodeDeploy, S3, EC2, IAM, CloudFormation, CodeArtifact, and GitHub.

Key concepts I learnt include how to build a fully automated CI/CD pipeline using AWS services, connect source control with GitHub, trigger builds automatically using webhooks, package and store build artifacts in S3, deploy applications to EC2 using CodeDeploy, enable rollbacks in case of deployment failures, and monitor the end-to-end flow of deployments. I also understood the importance of permissions (IAM roles), infrastructure cleanup, and disaster recovery strategies in real-world DevOps workflows.

### Project reflection

This project took me approximately 4 hours to complete.The most challenging part was dealing with rollback errors and CodeDeploy failures, especially understanding why the rollback wasn’t working as expected and how CodeDeploy handles previous artifacts.
It was most rewarding to see the entire CI/CD pipeline trigger automatically from a simple GitHub push and deploy the application to EC2 without any manual steps. That moment made all the debugging worth it!

---

## Starting a CI/CD Pipeline

AWS CodePipeline is a fully managed service that automates my entire CI/CD workflow. It connects my GitHub repo, CodeBuild, and CodeDeploy together, so whenever I push new code, it automatically builds and deploys my app — making deployments faster, consistent, and error-free.

CodePipeline offers different execution modes based on how you want to handle multiple pipeline runs. I chose Superseded, which cancels any ongoing run if a new one starts — this way, only the latest code gets deployed. Other options include Queued, where runs wait their turn, and Parallel, where multiple runs happen at the same time.

A service role gets created automatically during setup so that CodePipeline can access and manage other AWS resources like S3, CodeBuild, and CodeDeploy on my behalf. It's how AWS gives the pipeline the right permissions to run properly.

![Image](http://learn.nextwork.org/energetic_lavender_silly_sow/uploads/aws-devops-codepipeline-updated_gdnhtm)

---

## CI/CD Stages

The three stages I've set up in my CI/CD pipeline are:

Source Stage – This stage connects to my GitHub repo and automatically detects changes when I push code. I learned about how webhooks allow CodePipeline to respond in real-time to updates in my master branch.

Build Stage – This stage uses AWS CodeBuild to compile my source code into a deployable artifact. I learned about input/output artifacts and how the buildspec.yml controls the build process.

Deploy Stage – This stage uses AWS CodeDeploy to deploy the latest artifact to my EC2 instance. I learned about deployment groups, lifecycle events, and how automatic rollback can help recover from deployment failures.

While setting up each part, I learned how AWS services work together to automate the entire development lifecycle, making code updates faster, more reliable, and hands-free.

CodePipeline organizes the three stages into Source, Build, and Deploy, and shows their progress visually with colors and statuses.

In each stage, you can see more details on:
Status (like In progress, Succeeded, or Failed).
Timestamps for when the stage started and finished.
Execution logs or artifacts that were used or created.
Errors (if any) with detailed messages to help troubleshoot.
Links to connected services like CodeBuild logs or CodeDeploy lifecycle events.

This helps me quickly understand what's working, what failed, and where to look if something goes wrong in the CI/CD pipeline.

![Image](http://learn.nextwork.org/energetic_lavender_silly_sow/uploads/aws-devops-codepipeline-updated_fbdetger)

---

## Source Stage

In the Source stage, the default branch tells CodePipeline which branch of the GitHub repository to monitor for changes. I chose the master branch because it holds my production-ready code, so whenever I push a new commit to that branch, the pipeline will automatically get triggered.

The source stage is also where you enable webhook events, which allow CodePipeline to automatically detect changes in your GitHub repository. This is important because it removes the need for manual builds — every time I push code to the master branch, the pipeline is instantly triggered. Webhooks make the CI/CD process truly continuous by ensuring that code changes are always followed by automatic builds and deployments.

![Image](http://learn.nextwork.org/energetic_lavender_silly_sow/uploads/aws-devops-codepipeline-updated_sergt)

---

## Build Stage

The Build stage sets up the compilation and packaging of our source code. I configured it to use AWS CodeBuild, which needs the latest version of the code to work with. The input artifact for the build stage is SourceArtifact, which comes directly from the Source stage and contains the ZIP file of our code from GitHub. This ensures that CodeBuild always uses the most recent code changes to create a deployable build artifact.

![Image](http://learn.nextwork.org/energetic_lavender_silly_sow/uploads/aws-devops-codepipeline-updated_j1k2l3m4)

---

## Deploy Stage

The Deploy stage is where my application gets pushed to the EC2 instance. I configured it to use AWS CodeDeploy with my existing CodeDeploy application and deployment group. I also selected BuildArtifact as the input artifact so CodeDeploy knows what to deploy. To make things safer, I enabled automatic rollback, which means if the deployment fails, CodePipeline will automatically switch back to the last working version.

![Image](http://learn.nextwork.org/energetic_lavender_silly_sow/uploads/aws-devops-codepipeline-updated_m4n5o6p7)

---

## Success!

Since my CI/CD pipeline gets triggered by code changes in GitHub, I tested my pipeline by editing the index.jsp file and adding a new line inside the <body> tag. This small change allowed me to verify that CodePipeline automatically detected the update, triggered a new build and deployment, and reflected the change in the live application.

The moment I pushed the code change to GitHub, CodePipeline automatically detected the update and triggered a new execution of the pipeline. The Source stage showed the correct commit message, and I could see the Commit ID linked directly to my GitHub repo. The Build and Deploy stages turned green, confirming that the pipeline successfully built the new artifact and deployed it to the EC2 instance. The commit message under each stage reflects the exact update I made to the index.jsp file.

Once my pipeline executed successfully, I checked the Public IPv4 DNS of my EC2 instance from the CodeDeploy console. I pasted it into a new browser tab, and I immediately saw the latest version of my web application displayed, including the exact line I added in index.jsp. This confirmed that my CI/CD pipeline successfully automated the deployment of my code changes everything worked perfectly!

![Image](http://learn.nextwork.org/energetic_lavender_silly_sow/uploads/aws-devops-codepipeline-updated_e1f2g3h4)

---

## Testing the Pipeline

In a project extension, I initiated a rollback on the Deploy stage of my CI/CD pipeline. Automatic rollback is important for quickly reverting to a previous, stable version of the application if something goes wrong during deployment, minimizing downtime, and ensuring reliability. By practicing this rollback procedure, I gained hands-on experience in critical disaster recovery techniques crucial for managing real-world production systems.

During the rollback, the source and build stages are unaffected because a rollback specifically targets only the deployment itself, reverting to the previously successful deployment without altering the original source code or the artifacts produced during the build stage.

I could verify this by comparing the commit messages displayed in each stage: the Deploy stage showed the older commit from the previously successful deployment (indicating rollback), while the Source and Build stages continued to reflect the latest commit unchanged. This confirms that rolling back in CodePipeline doesn't modify or undo the previous stages; it simply redeploys an earlier known-good version of the application.

After rollback, the live web app reverted to its previous state specifically, the line I added to test the CI/CD pipeline (<p>If you see this line, that means your latest changes are automatically deployed into production by CodePipeline!</p>) was no longer present. This confirmed that the rollback successfully restored the application to the last stable version, demonstrating that my pipeline's rollback capability is working correctly and can be relied upon for disaster recovery scenarios.

![Image](http://learn.nextwork.org/energetic_lavender_silly_sow/uploads/aws-devops-codepipeline-updated_sdfgsdfgdf)

---

---
