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
  endpoint:
    description: 'The URL of the CSPM panel to push the scan results to.'
    required: true
    default: 'cspm.demo.accuknox.com'
  token:
    description: 'The token for authenticating with the CSPM Panel.'
    required: true
  tenant_id:
    description: 'The ID of the tenant associated with the AccuKnox SaaS.'
    required: true
  repository_name: 
     description: 'Docker image repository name'
     required: true
  tag:
     description: 'Add version tag to the repository'
     required: true
     default: '${{ github.run_id }}'
  severity:
     description: "Allows selection of severity level for the scan. Options include UNKNOWN, LOW, MEDIUM, HIGH, CRITICAL. If specified, the scan will target vulnerabilities of the selected severity level."
     required: false
     default: 'UNKNOWN,LOW,MEDIUM,HIGH,CRITICAL'
```

## Usage

Steps for using Install-action in a workflow yaml file 
- Checkout into the repo using checkout action.
- Utilize the udit-uniyal/Install-action repository with version tag v1.

### Token Generation from Accuknox SaaS and Viewing Tenant ID

Navigate to Tokens within the Settings section in the sidebar:
![image](https://github.com/udit-uniyal/Install-action/assets/115368361/2d3d0854-de77-4b51-87cd-7e284904bff4)

Click on Create Token: 
After clicking on 'Create Token,' the Tenant ID will be visible.
![image](https://github.com/udit-uniyal/Install-action/assets/115368361/20680bb9-fd35-4653-9106-d1ff8018cadb)

Click on Generate:
![image](https://github.com/udit-uniyal/Install-action/assets/115368361/918aac30-4289-4fcf-b6ff-c6fb116f3266)

### workflow steps:

```yaml
 - name: Run AccuKnox CSPM Scan
        uses: udit-uniyal/Install-action@v1
        with:                      
          token: 
          tenant_id: 
          repository_name:
          endpoint:                        #Optional
          tag:                             #Optional
          severity:                        #Optional
          dockerfile_context:              #Optional
```


## Minimalist Sample Configuration 

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
        uses: udit-uniyal/Install-action@v1
        with:
          token: 
          tenant_id: 
          repository_name: 
```
