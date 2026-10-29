# Lab 02a: Manage Azure Subscriptions and Role-Based Access Control

## Status

Completed

## Objective

Configure Azure management groups and role-based access control to organize subscriptions, delegate permissions through groups, apply least-privilege principles, create a custom role, and review role-related events in the Azure Activity Log.

## Skills Practiced

- Creating Azure management groups
- Understanding Azure management-group hierarchy
- Reviewing Azure RBAC built-in roles
- Assigning Azure roles to security groups
- Managing access at management-group scope
- Applying least-privilege access principles
- Creating a custom Azure RBAC role
- Reviewing RBAC role-definition JSON
- Using Actions, NotActions, and AssignableScopes
- Reviewing role-management events in Azure Activity Log

## Environment

- Platform: Microsoft Azure
- Environment type: Personal non-production Azure lab
- Access-control service: Azure Role-Based Access Control
- Data used: Test users, test groups, and test resources only

## Scenario

A pre-production environment required centralized subscription management and delegated support capabilities. The objective was to organize subscriptions under a management group, assign virtual machine management permissions to a support group, and create a custom role that allowed support-request management while restricting unnecessary provider-registration permissions.

## Implementation Summary

I completed the following actions:

1. Reviewed Microsoft Entra ID settings related to Azure resource access.
2. Created a test Azure management group to support centralized subscription organization and access management.
3. Reviewed the management-group hierarchy and the role of the root management group.
4. Reviewed Azure built-in role definitions, permissions, JSON configuration, and assignment details.
5. Assigned the Virtual Machine Contributor role to a Help Desk security group at the management-group scope.
6. Verified the role assignment through the Access Control (IAM) role-assignment view.
7. Created a custom support-request role by cloning an existing built-in support role.
8. Modified the custom role by excluding unnecessary support-resource-provider registration permissions.
9. Reviewed the custom role JSON configuration, including Actions, NotActions, and AssignableScopes.
10. Reviewed Azure Activity Log events to identify role-management activity.
11. Removed test management-group resources after completing validation.

## Access-Control Design

The lab demonstrated assigning permissions to a security group rather than directly to individual users. Group-based role assignments simplify administration, improve consistency, and support least-privilege access management.

The Virtual Machine Contributor role was selected to allow management of virtual machines without granting unnecessary access to operating systems, virtual networking, storage configuration, or broad subscription administration.

## Custom Role Design

A custom support-request role was created by cloning a built-in support-related role and excluding provider-registration permissions that were not required for the support scenario.

The custom role configuration included:

- Allowed actions required for support-request management
- Excluded actions defined through NotActions
- An assignable scope limited to the test management group
- A JSON role-definition format for reviewing and maintaining permissions

## Validation

I validated the lab by confirming:

- The test management group was successfully created.
- The management group was visible in the Azure portal hierarchy.
- The Help Desk security group received the Virtual Machine Contributor role assignment.
- The role assignment was visible in the Access Control (IAM) role-assignment list.
- The custom support-request role was successfully created.
- The custom role displayed the expected Actions, NotActions, and AssignableScopes values.
- Role-related activity was visible in the Azure Activity Log.

## Security Considerations

- Used a security group rather than assigning permissions directly to individual users.
- Applied least-privilege access by selecting a limited built-in role.
- Created a custom role to remove an unnecessary provider-registration permission.
- Limited the custom role's assignable scope to the test management group.
- Used a personal, non-production Azure environment and test data only.
- Did not upload credentials, tokens, keys, personal information, tenant identifiers, or sensitive screenshots to GitHub.

## Troubleshooting

No issues were encountered during this lab. All management-group, role-assignment, custom-role, and Activity Log validation steps were completed as expected.

## Cleanup

- Deleted the test management group after completing the lab.
- Removed test role assignments and test resources where applicable.
- Confirmed that no unnecessary lab resources remained active.

## Lessons Learned

- Management groups provide a way to organize subscriptions and apply governance or RBAC at scale.
- Azure RBAC permissions can be assigned at different scopes, including management groups, subscriptions, resource groups, and individual resources.
- Assigning roles to groups is more scalable and manageable than assigning roles directly to individual users.
- Built-in roles should be evaluated before creating custom roles.
- Custom roles support least-privilege access by allowing only the permissions required for a specific task.
- Azure role definitions use JSON and include Actions, NotActions, and AssignableScopes.
- Azure Activity Log can be used to review role-management events and support auditing.
