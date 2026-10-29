# Lab 02b: Manage Governance with Azure Policy

## Status

Completed

## Objective

Implement Azure governance controls by applying resource tags, enforcing tag requirements with Azure Policy, automatically inheriting tags through policy remediation, and protecting resources with resource locks.

## Skills Practiced

- Creating Azure resource groups
- Applying resource tags
- Reviewing Azure Policy definitions
- Assigning Azure Policy at resource-group scope
- Enforcing required resource tags
- Validating denied resource deployments
- Configuring policy remediation
- Using managed identities for policy remediation
- Applying inherited tags to resources
- Creating and testing Azure resource locks
- Distinguishing Azure Policy, Azure RBAC, and resource locks

## Environment

- Platform: Microsoft Azure
- Environment type: Personal non-production Azure lab
- Governance services: Azure Policy, resource tags, and resource locks
- Data used: Test resources and test metadata only

## Scenario

A growing cloud environment contained resources without consistent ownership, project, or cost-center information. This lab implemented governance controls to improve resource identification, enforce metadata standards, automatically apply missing tags, and prevent accidental deletion of configured resources.

## Implementation Summary

I completed the following actions:

1. Created a test resource group in a personal Azure subscription.
2. Applied a Cost Center tag to the resource group.
3. Reviewed available Azure built-in policy definitions.
4. Assigned a policy requiring resources in the test resource group to include a specified Cost Center tag and value.
5. Tested policy enforcement by attempting to deploy a storage account without the required tag.
6. Confirmed that Azure Policy denied the non-compliant deployment.
7. Removed the initial deny-policy assignment after validation.
8. Assigned an Azure Policy that inherited the Cost Center tag from the resource group when child resources did not include the tag.
9. Configured a remediation task and managed identity to support policy-based tag inheritance.
10. Created a storage account without manually specifying the Cost Center tag.
11. Confirmed that the storage account inherited the tag from the resource group.
12. Created a delete lock on the resource group.
13. Attempted to delete the locked resource group and confirmed that the deletion was denied.
14. Removed lab resources and governance controls after completing validation.

## Governance Controls Implemented

### Resource Tags

A Cost Center tag was applied to the resource group to provide consistent metadata for tracking, reporting, ownership, and cost-management purposes.

### Azure Policy Enforcement

A built-in Azure Policy was assigned to require resources in the test resource group to include the required Cost Center tag and value.

The policy was validated by attempting to create a storage account without the required tag. Azure denied the deployment because the resource did not meet the configured policy requirement.

### Policy-Based Tag Inheritance

A second Azure Policy was assigned to inherit the Cost Center tag from the resource group when child resources did not include the tag.

The policy used a Modify effect and remediation configuration to apply the required tag automatically to non-compliant resources.

### Resource Lock

A delete lock was configured on the test resource group to prevent accidental removal of the resource group and its dependent resources.

The lock was validated by attempting to delete the resource group. Azure denied the deletion attempt until the lock was removed.

## Validation

I validated the lab by confirming:

- The test resource group was created with the required Cost Center tag.
- The initial Azure Policy assignment denied deployment of a storage account without the required tag.
- The policy error identified the tag-compliance requirement as the reason for the denied deployment.
- The inherited-tag policy allowed deployment of a storage account without manually specifying the Cost Center tag.
- The deployed storage account inherited the Cost Center tag from the resource group.
- The resource-group delete lock prevented deletion of the protected resource group.
- The resource group could be removed only after the delete lock was removed.

## Security and Governance Considerations

- Applied consistent metadata through resource tags to improve visibility, reporting, and accountability.
- Used Azure Policy to enforce governance requirements before resource deployment.
- Used policy remediation to bring resources into compliance automatically.
- Applied a delete lock to protect configured resources from accidental deletion.
- Used a personal, non-production Azure environment and test data only.
- Did not upload credentials, access keys, tenant identifiers, subscription identifiers, personal information, or sensitive screenshots to GitHub.

## Azure Policy, RBAC, and Resource Locks

Azure Policy, Azure RBAC, and resource locks serve different governance and security purposes.

- **Azure Policy** evaluates and enforces resource configuration standards.
- **Azure RBAC** controls which identities can perform actions on Azure resources.
- **Resource locks** protect resources from deletion or modification, even when an identity otherwise has sufficient permissions.

## Troubleshooting

No issues were encountered during this lab. Policy assignments, tag validation, remediation, inherited tagging, and resource-lock validation were completed as expected.

## Cleanup

- Removed the delete lock from the test resource group.
- Deleted test storage resources created during validation.
- Removed Azure Policy assignments and remediation resources where applicable.
- Deleted the test resource group after completing the lab.

## Lessons Learned

- Azure resource tags provide metadata that supports resource ownership, reporting, governance, and cost management.
- Azure Policy can enforce organizational standards during resource deployment.
- Policy assignments can be scoped at the management-group, subscription, resource-group, or resource level.
- Deny policies can prevent non-compliant resource deployment.
- Modify policies can remediate non-compliant resources by applying required configuration changes.
- Managed identities can support policy remediation tasks.
- Resource locks provide an additional safeguard against accidental deletion or modification.
- Azure Policy, Azure RBAC, and resource locks work together but address different governance and security requirements.
