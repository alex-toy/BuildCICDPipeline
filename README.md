# Deploying .NET Core Applications using Azure DevOps CI/CD Pipelines in Real Time

Most industries would like to use CI/CD pipelines for their applications because it allows them to utilize the same pipeline benefits as those using the visual designer. It is easy to build CI/CD for any project by simply adding their source file to the root’s repository. Using Azure DevOps, you can utilize multiple templates for project execution. in this project, we will study the process of how a web application is deployed and pushed to Azure DevOps in real-time.


## Create Azure Devops project

<img src="/pictures/azure_devops_project.png" title="azure devops project"  width="900">

- Push an existing repository from command line
```
git remote add originazure https://alexviseo@dev.azure.com/alexviseo/Deploying%20NET%20Core%20Applications%20using%20Azure%20DevOps%20CICD%20Pipeline/_git/Deploying%20NET%20Core%20Applications%20using%20Azure%20DevOps%20CICD%20Pipeline
git push -u originazure --all --force
```