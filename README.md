# Overview

This repo is to create and manage Apigee api proxy environment configurations. 

## Getting Started

### Folder Structure

Here's the folder structure:

- `resources`
  - `edge` - The edge folder contains all configurations
    - `env` - The env folder contains environment configurations
      - `common` 
        - `aliases.json` - config entity for aliases
        - `caches.json` - config entity for cache
        - `flowhooks.json` - config entity for flowhooks
        - `keystores.json` - config entity for keystores
        - `kvms.json` - config entity for kvms
        - `targetServers.json` - config entity for targetservers
    - `org` - The org folder contains org configurations
      - `specs.json` - config entity for specs
  - `specs` - The specs folder contains openapi specs file
    - `api-proxy.yaml` - openapi specs file
- `vars` - variable templates
  - `vars-global.yml` - global variables for all environments
  - `vars-dev.yml` - variables for `dev` environment
  - `vars-int.yml` - variables for `int` environment
  - `vars-qa.yml` - variables for `qa` environment
  - `vars-prod.yml` - variables for `prod` environment
- `azure-pipelines.yml` - pipeline for build and deployment
- `pom.xml` - contains information about the project and configuration details used by maven
- `shared-config-pom.xml` - contains maven profile configurations

## Build and Deploy
To run the pipeline, follow the steps below:
1. Create an environment branches for (dev,int,qa) based on `master`.

   Below is the recommended naming convention of the environment branches:
    - Use kebab-case in naming the branches
    - `<repository-name>-<environment>`
     <br /><br />
      ```
      eg. shared-it-apigee-env-sample-dev
          shared-it-apigee-env-sample-int
          shared-it-apigee-env-sample-qa
      ```
   For more instructions on how to create environment branches, please see [this guide](https://dev.azure.com/SempraUtilities/SempraUtilities/_wiki/wikis/SempraUtilities.wiki/2595/Create-environment-branches)

1. [Create a feature branch](https://dev.azure.com/SempraUtilities/SempraUtilities/_wiki/wikis/SempraUtilities.wiki/2279/Create-a-feature-branch)

1. Open the `vars` folder, go to `vars-global.yaml` and change the values for the following variables:

    - `orgName`: provide the name of the organization
    - `apiName`: provide the name of the api proxy (must be unique across the organization)
    - `azureEnv`: provide the name of the azure environment without environment suffix
<br /><br />

1. Go to `azure-pipelines.yml` and change the values for the following pipeline definitions:
    
    -   ```yaml
        branches:
        include:
        - '<place the dev branch name here>'
        - '<place the int branch name here>'
        - '<place the qa branch name here>'
        ```

1. Update the openapi spec file located in the `resources/specs/api-proxy.yaml`. For more instructions on how to create a OpenAPI spec, please see [this guide](https://dev.azure.com/SempraUtilities/SempraUtilities/_wiki/wikis/SempraUtilities.wiki/2118/OpenAPI-Specs-Guide)

1. After changing the values and updating the openapi spec, commit your changes to reflect into pipeline.

1. Create a pull request or follow [this guide](https://dev.azure.com/SempraUtilities/SempraUtilities/_wiki/wikis/SempraUtilities.wiki/2280/Create-a-pull-request) here on how to create and submit the request.

1. Pipeline will be triggered once the pull request is complete.

## To modify configuration entities
Refer to the docs below for more details on how to setup the config schema:
* [Cache](https://apidocs.apigee.com/docs/caches/1/types/Cache)
* [Aliases](https://apidocs.apigee.com/docs/keystores-and-truststores/1/types/Alias)
* [Flowhook](https://apidocs.apigee.com/docs/shared-flows/1/types/FlowHook)
* [Keystores](https://apidocs.apigee.com/docs/keystores-and-truststores/1/types/KeystoreTrustore)
* [Kvms](https://apidocs.apigee.com/docs/key-value-maps/1/types/KVMs)
* [TargetServer](https://apidocs.apigee.com/docs/targetservers/1/types/TargetServer)

