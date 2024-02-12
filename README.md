# install-action

Github actions to install vulnerability scanner.

## Learn More

- [About Accuknox](https://www.accuknox.com/)

## Inputs

```yaml
inputs:
  dockerfile_context:
    description: 'The context of the Dockerfile to use for building the image.'
    required: true
    default: 'Dockerfile'
  cspm_url:
    description: 'The URL of the CSPM panel to push the scan results to.'
    required: true
  cspm_token:
    description: 'The token for authenticating with the CSPM panel.'
    required: true
  tenant_id:
    description: 'The ID of the tenant associated with the CSPM panel.'
    required: true
  repository_name: 
     description: 'The name of the Docker image repository.'
     required: true
  tag:
     description: 'The version tag to be added to the repository.'
     required: true
  severity:
     description: "Select Severity from UNKNOWN,LOW,MEDIUM,HIGH,CRITICAL if you want to scan for specific severity"
     required: false

```

## Usage

Steps for using install-action in a workflow yaml file 
- Checkout into the repo using checkout action.
- Using vulnerability-scanner action install vulnerability scanner and run scan.
  
### User Input's sample in workflow

```yaml
 - name: Run AccuKnox CSPM Scan
        uses: ./
        with:
          cspm_url: 
          cspm_token: 
          tenant_id: 
          repository_name: 
          tag:                             #Optional
          severity:                        #Optional
          DOCKERFILE_CONTEXT: 
             
```


## Sample Configuration

```yaml

name: AccuKnox Scan Workflow

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  accuknox-cicd:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@main  
     
      - name: Run AccuKnox CSPM Scan
        uses: ./
        with:
          cspm_url: 
          cspm_token: 
          tenant_id: 
          repository_name: 
          tag: 
          severity: 
          DOCKERFILE_CONTEXT: 

```
