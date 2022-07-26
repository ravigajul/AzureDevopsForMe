# AzureDevopsForMe
## Create a free account 
https://azure.microsoft.com/en-us/services/devops/
## Two type of pipelines in Azure
1. Build Pipelines
2. Release Pipelines
3. Create Release
## Copy artificats from 'S' (source) to 'a' (artifacts) and then push to azure pipelines
By default after building the project the artifacts will be created in 'S' location of agent
Use copy task to copy the artifacts from 'c:\agent_work\1\S' to 'c:\agent_work\1\a' folder in agent and from there use 'publish build artifacts' task to push to azure pipelines.
pre defined enviornment variable $(Build.ArtifactStagingDirectory) refers to c:\agent_work\1\a
## Trigger to automatically run the job
trigger:
 -master
this in yaml file is responsible for triggering the job automatically

## The artificats on Azure pipeline is represented by below environment variable
$(System.DefaultWorkingDirectory)

## Enable Continous Deployment Trigger in Release pipeline
Everytime there is a code checked in , build pipeline will be trigger and generates the new artifacts.
If the continuous deployment trigger is enabled in release pipeline against artifacts, the continuous deployment happens by running release pipeline.
