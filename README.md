# Azure Infrastructure Operations Project: Deploying a scalable IaaS web server in Azure

### Introduction
For this project, you will write a Packer template and a Terraform template to deploy a customizable, scalable web server in Azure.

### Archtecture
![Project Archtecture](/images/1°projeto-arquitetura.png)

### Scenario
Your company's development team has created an application that they need deployed to Azure. The application is self-contained, but they need the infrastructure to deploy it in a customizable way based on specifications provided at build time, with an eye toward scaling the application for use in a CI/CD pipeline.

Although we’d like to use Azure App Service, management has told us that the cost is too high for a PaaS like that and wants us to deploy it as pure IaaS so we can control cost. Since they expect this to be a popular service, it should be deployed across multiple virtual machines.

To support this need and minimize future work, we will use Packer to create a server image, and Terraform to create a template for deploying a scalable cluster of servers—with a load balancer to manage the incoming traffic. We’ll also need to adhere to security practices and ensure that our infrastructure is secure.

### Getting Started
1. Clone this repository

2. Create your infrastructure as code

3. Update this README to reflect how someone would use your code.

### Dependencies
1. Create an [Azure Account](https://portal.azure.com) 
2. Install the [Azure command line interface](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
3. Install [Packer](https://www.packer.io/downloads)
4. Install [Terraform](https://www.terraform.io/downloads.html)

### Instructions
1. Deploy a Policy
    * Write a policy definition to deny the creation of resources that do not have tags.
    * Apply the policy definition to the subscription with the name "tagging-policy".
    * Use `az policy assignment list` to check the policy assigned.

### Output
**Your words here**