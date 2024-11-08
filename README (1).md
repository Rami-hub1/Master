# Overview

This repo stores azure pipeline templates that contains reusable content, logic, and parameters.

## Getting Started

### Folder Structure  

- `env` The env folder contains the pipeline templates for environment pipeline
  - `jobs`
    - `jobs-build-environment-config.yml` - Build jobs for the environment configuration
    - `jobs-deploy-environment-config.yml` - Deploy jobs for the environment configuration
  - `pipeline`
    - `pipeline-environment-config.yml` - Root pipeline template for the api proxy
  - `stages`
    - `stages-build-environment-config.yml` - Build stage for the environment configuration
    - `stages-deploy-environment-config.yml` - Deploy stage for the environment configuration
  - `steps`
    - `steps-deploy-environment-config-proxy.yml` - Deploy steps for the environment configuration
    - `steps-generate-environments.yml` Steps for the environments folder creation
    - `steps-get-configurations.yml` Steps for getting all configuration files
    - `steps-replace-config-tokens.yml` Steps that replace tokens in config files with variable values  

- `images`
  - `api-proxy-control-flow.png` - Control flow of API Proxy Pipeline
  - `environment-control-flow` - Control flow of Environment Pipeline
  - `shared-flow-control-flow` - Control flow of Shared Flow Pipeline

- `policies` - The policies folder contains api proxy policies
  - `FC-Shared-Logging.xml` - Policy that reference to the Shared-Logging  
  
- `proxy` - The proxy folder contains the pipeline templates for API proxy pipeline
  - `jobs`
    - `jobs-build-api-proxy.yml` - Build jobs for the api proxy
    - `jobs-deploy-api-proxy.yml` - Deploy jobs for the api proxy
  - `pipeline`
    - `pipeline-api-proxy.yml` - Root pipeline template for the api proxy
  - `stages`
    - `stages-build-api-proxy.yml` - Build stage for the api proxy
    - `stages-deploy-api-proxy.yml` - Deploy stage for the api proxy
    - `stages-test-api-proxy.yml` - Test Automation stage for the api proxy
  - `steps`
    - `steps-build-maven-api-proxy.yml` - Build steps for the api proxy using maven
    - `steps-build-open-api-specs.yml` - Build steps for the api proxy using openapi2apigee
    - `steps-check-deploy-status.yml` - Build steps for checking the deploymen status
    - `steps-deploy-maven-api-proxy.yml` - Deploy steps for the api proxy using maven
    - `steps-deploy-open-api-specs.yml` - Deploy steps for the api proxy using apigeetool
    - `steps-detect-proxy-changes.yml` Steps for the api proxy build and deployment type
    detection
    - `steps-get-deployment-type.yml` Steps that read the variable from the file
    - `steps-replace-pom-tokens.yml` Steps that replace tokens in pom file with variable  
     
- `shared` - The shared folder contains reusable step template files that are used within this repo
  - `jobs-checkmarx-analysis.yml` - Jobs for checkmarx static code analysis
  - `steps-shared-copy-artifacts.yml` - Steps that copy files from source to artifact staging directory
  - `steps-shared-generate-token.yml` - Steps that generate access token
  - `steps-shared-install-apigee-lint.yml` - Steps for the apigeelint installation  
  - `steps-shared-publish-artifacts.yml` - Steps that publish build artifacts to azure pipelines  
  
- `sharedflow` - The sharedflow folder contains the pipeline templates for shared flow pipeline
  - `jobs`
    - `jobs-build-shared-flow.yml` - Build jobs for the shared flow
    - `jobs-deploy-shared-flow.yml` - Deploy jobs for the shared flow
  - `pipeline`
    - `pipeline-shared-flow.yml` - Root pipeline template for the shared flow
  - `stages`
    - `stages-build-shared-flow.yml` - Build stage for the shared flow
    - `stages-deploy-shared-flow.yml` - Deploy stage for the shared flow
  - `steps`
    - `steps-build-shared-flow.yml` - Build steps for the shared flow
    - `steps-deploy-shared-flow.yml` - Deploy steps for the shared flow
    - `steps-detect-shared-flows-changes.yml` Steps for the shared flow with changes detection
    - `steps-setup-parent-pom.yml` Steps that modify sub module in parent pom xml file

## Build and Deploy Guide

### Api Proxy Pipeline Control Flow
![pipeline](images/api-proxy-control-flow.png)

### Shared Flow Pipeline Control Flow
![pipeline](images/shared-flow-control-flow.png)

### Environment Pipeline Control Flow
![pipeline](images/environment-control-flow.png)