# Lab 01: Manage Microsoft Entra ID Identities

## Status

In Progress

## Objective

Provision and configure test identities in Microsoft Entra ID, invite an external guest user, create a security group, assign group ownership, and manage group membership in a non-production Azure environment.

## Scenario

A pre-production lab environment requires administrators to manage virtual machines and related services. This lab demonstrates how Microsoft Entra ID users and groups can be used to organize administrators, assign access, and reduce administrative overhead.

## Skills Practiced

- Creating Microsoft Entra ID user accounts
- Configuring user profile properties
- Inviting an external guest user
- Creating security groups
- Assigning group owners
- Adding assigned group members
- Reviewing static versus dynamic group membership options
- Applying least-privilege and test-data principles

## Environment

- Platform: Microsoft Entra ID
- Environment type: Personal non-production Azure lab
- Identity data: Test users and test group memberships only
- Data classification: No government, organizational, production, or sensitive data used

## Implementation Summary

I completed the following actions:

1. Created a test Microsoft Entra ID user account.
2. Configured user properties, including job title, department, and usage location.
3. Invited a test external guest user using a personal email address.
4. Created a security group for IT lab administrators.
5. Assigned a group owner.
6. Added the test user and guest user as assigned group members.
7. Reviewed group ownership and membership settings after deployment.

## Group Membership Design Considerations

This lab used assigned membership, which requires an administrator to manually add or remove users.

Dynamic group membership can reduce administrative effort by automatically updating membership based on user attributes, such as job title or department. Dynamic membership was not configured in this lab because availability depends on the licensing and features enabled in the Azure tenant.

## Validation

I validated the lab by confirming:

- The test user account appeared in Microsoft Entra ID.
- The guest invitation was successfully created.
- The security group was created successfully.
- The designated owner was listed for the group.
- The test user and guest user appeared as group members.
- The configured user properties were visible in the user account profile.

## Security Considerations

- Used test accounts and non-production resources only.
- Applied least-privilege principles when considering role and group assignments.
- Did not store passwords, access tokens, API keys, client secrets, or connection strings in this repository.
- Did not include personal email addresses, screenshots containing sensitive information, tenant details, or identifiers in public documentation.
- Group membership should be reviewed periodically to ensure access remains appropriate.

## Troubleshooting

- The guest invitation email did not appear immediately. I verified that the invitation was created in Microsoft Entra ID and checked the recipient email inbox and spam folder.

## Cleanup

- Retained the test group temporarily for future Azure RBAC l

## Lessons Learned

- Microsoft Entra ID user properties can support identity governance and group-management decisions.
- Assigned groups require manual membership management.
- Dynamic membership can automate group updates when tenant licensing and policy allow it.
- Group owners provide a way to delegate limited group-management responsibilities.
- Test environments should use non-production identities and should be cleaned up after use.
