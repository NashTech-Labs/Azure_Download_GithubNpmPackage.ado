# Azure_Download_GithubNpmPackage.ado
Use this template for installing the npm packages from GitHub in Azure Devops Pipeline. Package Name &amp; Package version need to be specified.

## Parameters:

The pipeline requires the following parameters to be defined:


| Name  | Displayname | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | :-------------: | :-------------: | ------------- | :-------------: | ------------- |
| packageName | Package Name | string |  | | Required | Specifies the name of the package to download from GitHub |
| version | Package Version | string |  | stable, edge, test, nightly | Required | Specifies the version of the package to download from GitHub |
| externalRegistryCredentials | Credentials for registry from GitHub | string |  | | Required | Specifies the credentials to use for external registry from GitHub i.e. externalEndpoints |
| installDirectory | Destination directory or packagesDirectory | string |  | | Optional | Specifies the folder where packages are installed. If no folder is specified, packages are restored into the default system working directory |
--------------------------------------------------------------------------------------------------------------------------------------------------

These parameters provide multiple use case options for the template, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

 ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/Azure_Download_GithubNpmPackage.ado
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: Azure_Download_GithubNpmPackage.yml
    parameters:
      packageName: '${{parameters.packageName}}' 
      version: '${{parameters.version}}' 
      externalRegistryCredentials: '${{parameters.externalRegistryCredentials}}' 
      installDirectory: '${{parameters.installDirectory}}' 
  ```
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.
