# Deploying .NET Core Applications using Azure DevOps CI/CD Pipelines in Real Time

Most industries would like to use CI/CD pipelines for their applications because it allows them to utilize the same pipeline benefits as those using the visual designer. It is easy to build CI/CD for any project by simply adding their source file to the root’s repository. Using Azure DevOps, you can utilize multiple templates for project execution. in this project, we will study the process of how a web application is deployed and pushed to Azure DevOps in real-time.


## Initialize project

### Create Azure Devops project

<img src="/pictures/azure_devops_project.png" title="azure devops project"  width="900">

- Push an existing repository from command line
```
git remote add originazure https://alexviseo@dev.azure.com/alexviseo/Deploying%20NET%20Core%20Applications%20using%20Azure%20DevOps%20CICD%20Pipeline/_git/Deploying%20NET%20Core%20Applications%20using%20Azure%20DevOps%20CICD%20Pipeline
git push -u originazure --all --force
```
<img src="/pictures/azure_devops_project2.png" title="azure devops project"  width="900">


### Create Web App

Create three web apps for dev, prod and uat. For prod, add a staging deployment slot.

<img src="/pictures/web_app.png" title="web app"  width="900">


### Create .NET Project

- create the project
```
dotnet new sln --name "TodoApp"
dotnet new mvc -n TodoApp.Web
dotnet sln TodoApp.sln add TodoApp.Web\TodoApp.Web.csproj
```

- build it
```
dotnet build
```
<img src="/pictures/build_app.png" title="build app"  width="900">


- run the application
```
dotnet .\src\TodoApp.Web\bin\Debug\net7.0\TodoApp.Web.dll
```
<img src="/pictures/run_app.png" title="run app"  width="900">


## Create CI Pipeline

- choose classic editor
<img src="/pictures/create_pipeline.png" title="create pipeline with classic editor"  width="900">

- choose azure repo and then ASP.NET core as a template and disable the *Test* task
<img src="/pictures/create_pipeline2.png" title="create pipeline with azure repo"  width="900">
<img src="/pictures/create_pipeline3.png" title="create pipeline with azure repo"  width="900">

- Run pipeline
<img src="/pictures/run_pipeline.png" title="run pipeline "  width="900">
 
 At this time, you can retrieve the artifact.

 - edit the pipeline so that it runs automatically when a commit is done on a branch :
<img src="/pictures/trigger_pipeline.png" title="trigger the pipeline "  width="900">

 Now the pipeline is automatically triggered. This is called **continuous integration**.


## Create CD Pipeline

This section corresponds to the release pipeline.

- create **Release Pipeline**. Choose **App Service Deployment**
<img src="/pictures/release_pipeline.png" title="release pipeline"  width="900">

- add artifact. Enable **continuous deployment trigger**
<img src="/pictures/release_pipeline1.png" title="release pipeline"  width="900">

- add **dev** stage
<img src="/pictures/release_pipeline2.png" title="release pipeline"  width="900">

- now, on each push, the release pipeline is automatically triggered :
<img src="/pictures/release_pipeline3.png" title="release pipeline"  width="900">


At this time, I get this error :
Error: Failed to get resource ID for resource type 'Microsoft.Web/Sites' and resource name 'cicd-helloworld-dev'. Error: connect ENETUNREACH 169.254.169.254:80