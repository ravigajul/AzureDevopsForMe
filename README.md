# AzureDevopsForMe
## Create a free account 
https://azure.microsoft.com/en-us/services/devops/

## Copy artificats from 'S' (source) to 'a' (artifacts) and then push to azure artifacts
By default after building the project the artifacts will be created in 'S' location of agent
Use copy task to copy the artifacts from 'c:\agent_work\1\S' to 'c:\agent_work\1\a' folder in agent and from there publish to azure artifacts.
pre defined enviornment variable ${Build.ArtifactStagingDirectory} refers to c:\agent_work\1\a
