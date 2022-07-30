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
## Trigger to automatically run the job where there is a commit in master branch
```yaml
trigger:
 -master
```
this in yaml file is responsible for triggering the job automatically

## The artificats on Azure pipeline is represented by below environment variable
```yaml
$(System.DefaultWorkingDirectory)
```

## Enable Continous Deployment Trigger in Release pipeline
Everytime there is a code checked in , build pipeline will be trigger and generates the new artifacts.
If the continuous deployment trigger is enabled in release pipeline against artifacts, the continuous deployment happens by running release pipeline.

## Configure self hosted agent vms
1. Go to Project Settings -> Agent Pools - >Default - > Agents -->New Agent
2. Download the agent from the popup displayed
3. Follow the powershell command instructions displayed.
4. Powershell needs to be opened as an administrator
5. You will be promoted to enter PAT (Personal Access Token) which can be generated from Azure usersettings - > Personal Access Token -->New Token.
5. Make the below change in yaml file as per the pool/image names
```yml
pool:
  name: 'Default'
  vmImage: 'DESKTOP-SAMG2C9'
```

## Vulnerability Scans
'White Source bolt' or 'Black Duck Detect' extension can be added to Azure Devops to show any security vulnerabilities on the project repo.
OrganizationSettings-->Extensions->Browse Market Place -> Search for above extensions and add it to Azure
Add white source bolt task to the azure-pipeline.yaml
Now when the pipeline is run, we would see extra tab "WhiteSourceBoltBuildReport' that shows security vulnerability score and suggestions.
