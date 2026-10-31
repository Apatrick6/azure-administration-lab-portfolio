# Lab 03: Deploy Azure Resources with ARM Templates and Bicep

## Status

Completed

## Architecture Diagram

[View the Lab 03 ARM Templates and Bicep deployment architecture diagram](../diagrams/lab-03-arm-templates-bicep-diagram.md)

## Objective

Deploy Azure resources by using Azure Resource Manager templates, parameter files, Azure PowerShell, Azure CLI, Azure Cloud Shell, and Azure Bicep.

## Skills Practiced

- Creating Azure managed disks
- Exporting Azure Resource Manager templates
- Reviewing ARM template JSON
- Reviewing ARM parameter files
- Editing template parameters
- Deploying templates through the Azure portal
- Deploying templates with Azure PowerShell
- Deploying templates with Azure CLI
- Using Azure Cloud Shell
- Using Azure PowerShell subscription context
- Using Azure CLI subscription context
- Deploying Azure resources with Bicep
- Reviewing Azure resource-group deployment history
- Validating Azure resource deployments

## Environment

- Platform: Microsoft Azure
- Environment type: Personal non-production Azure lab
- Deployment technologies: ARM templates, JSON parameter files, Azure PowerShell, Azure CLI, and Bicep
- Resources deployed: Azure managed disks
- Data used: Test resources only

## Scenario

The lab environment required a repeatable method for deploying Azure resources while reducing manual effort, configuration errors, and deployment inconsistency.

This lab demonstrated how Infrastructure as Code can be used to deploy the same resource type through multiple deployment methods.

## Implementation Summary

I completed the following actions:

1. Created an Azure managed disk through the Azure portal in a test resource group.
2. Exported the deployed managed disk configuration as an Azure Resource Manager template and parameter file.
3. Reviewed the exported JSON template and parameter-file structure.
4. Modified the ARM template and parameter values to deploy an additional managed disk with a new name.
5. Deployed the modified ARM template through the Azure portal custom-deployment interface.
6. Configured Azure Cloud Shell for PowerShell and verified the active Azure subscription context.
7. Uploaded the template and parameter files to Cloud Shell.
8. Modified the template to deploy an additional managed disk through Azure PowerShell.
9. Validated the PowerShell deployment and confirmed the resource provisioning state.
10. Switched Cloud Shell to Bash and verified the active Azure CLI subscription context.
11. Modified the template and deployed an additional managed disk through Azure CLI.
12. Reviewed a Bicep template defining an Azure managed disk.
13. Modified the Bicep configuration to deploy a managed disk with updated name, size, and storage-performance settings.
14. Deployed the Bicep template through Azure CLI.
15. Verified deployed managed disks and reviewed deployment details in the Azure resource group.

## Deployment Methods Used

### Azure Portal

Created an initial managed disk through the Azure portal and exported the resource configuration as an ARM template and parameter file.

### Azure Resource Manager Templates

Modified the exported JSON template and parameter file to deploy additional managed disks with updated resource names and configuration values.

### Azure PowerShell

Used Azure Cloud Shell in PowerShell mode to deploy an ARM template at resource-group scope and validate the provisioning state of deployed managed disks.

### Azure CLI

Used Azure Cloud Shell in Bash mode to deploy an ARM template through Azure CLI and confirm deployed resources.

### Azure Bicep

Modified and deployed a Bicep template defining an Azure managed disk. The Bicep deployment demonstrated a more concise declarative approach to Azure resource deployment.

## Validation

I validated the lab by confirming:

- The initial managed disk was successfully created through the Azure portal.
- The exported ARM template and parameter file were available for review and reuse.
- The modified ARM template successfully deployed an additional managed disk through the Azure portal.
- The Azure PowerShell deployment completed successfully.
- The Azure CLI deployment completed successfully.
- The Bicep deployment completed successfully.
- Deployed managed disks were visible in the test resource group.
- Deployment details and provisioning states were visible in the resource-group deployment history.

## Security and Operational Considerations

- Used a personal, non-production Azure subscription and test resources only.
- Verified the active subscription context before deploying through Azure PowerShell and Azure CLI.
- Used parameterized templates to support repeatable deployments and reduce manual configuration errors.
- Reviewed resource-group deployment history to validate deployment success.
- Did not upload subscription identifiers, tenant identifiers, credentials, access keys, tokens, or course-provided template files to GitHub.
- Deleted test resources after validation to avoid unnecessary cost.

## Troubleshooting

No issues were encountered during this lab. ARM template deployments, Azure PowerShell deployment, Azure CLI deployment, Bicep deployment, and resource validation were completed as expected.

## Cleanup

- Deleted the test resource group and managed disks after completing validation.
- Confirmed that no unnecessary lab resources remained active.
- Removed locally stored test files containing environment-specific resource details where applicable.

## Lessons Learned

- Azure Resource Manager templates use JSON to define and deploy Azure resources declaratively.
- Parameter files separate deployment values from template logic and support template reuse.
- ARM templates can be deployed through the Azure portal, Azure PowerShell, and Azure CLI.
- Azure Cloud Shell provides browser-based access to Azure PowerShell and Azure CLI.
- Subscription context should be verified before executing deployments in Cloud Shell.
- Bicep provides a more concise and readable syntax for deploying Azure resources.
- Infrastructure as Code improves deployment consistency, repeatability, and operational efficiency.
- Resource-group deployment history can be used to validate and troubleshoot Azure deployments.
