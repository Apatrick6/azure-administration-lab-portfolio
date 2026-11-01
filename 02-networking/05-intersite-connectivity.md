# Lab 05: Implement Azure Intersite Connectivity

## Status

Completed

## Architecture Diagram

[View the Lab 05 Azure intersite connectivity architecture diagram](../diagrams/lab-05-intersite-connectivity-diagram.md)

## Objective

Create virtual machines in separate Azure virtual networks, test network connectivity, configure virtual network peering, validate communication between peered virtual networks, and implement a custom route through a future network virtual appliance.

## Skills Practiced

- Creating Azure virtual machines
- Creating Azure virtual networks and subnets
- Configuring non-overlapping address spaces
- Using Azure Network Watcher
- Running connection troubleshooting tests
- Creating Azure virtual network peerings
- Validating virtual network peering status
- Testing TCP connectivity with PowerShell
- Using Test-NetConnection
- Configuring Windows Firewall rules
- Creating Azure route tables
- Creating user-defined routes
- Associating route tables with subnets
- Routing traffic through a virtual appliance

## Environment

- Platform: Microsoft Azure
- Environment type: Personal non-production Azure lab
- Networking services: Azure Virtual Network, virtual network peering, Network Watcher, route tables, and user-defined routes
- Compute resources: Test Windows Server virtual machines
- Data used: Test resources only

## Scenario

Core IT services and manufacturing services were deployed in separate virtual networks to maintain workload segmentation. The objective was to securely enable communication between the two virtual networks through virtual network peering and configure a custom route for future traffic inspection through a network virtual appliance.

## Implementation Summary

I completed the following actions:

1. Created a test Core Services virtual machine and virtual network.
2. Created a separate test Manufacturing virtual machine and virtual network.
3. Configured non-overlapping address spaces for the two virtual networks.
4. Used Azure Network Watcher Connection Troubleshoot to test connectivity between the virtual machines before peering.
5. Confirmed that connectivity between the separate virtual networks was initially unavailable.
6. Created bidirectional virtual network peering between the Core Services and Manufacturing virtual networks.
7. Verified that both peering connections displayed a connected status.
8. Enabled the Windows Firewall rule required for Remote Desktop connectivity on the Core Services virtual machine.
9. Used Azure PowerShell Run Command and Test-NetConnection to validate TCP connectivity from the Manufacturing virtual machine to the Core Services virtual machine.
10. Created a perimeter subnet in the Core Services virtual network.
11. Created an Azure route table.
12. Created a user-defined route directing traffic destined for the Core Services virtual network through a future network virtual appliance.
13. Associated the route table with the perimeter subnet.
14. Deleted test resources after completing validation.

## Virtual Network Peering

Virtual network peering was configured between the Core Services and Manufacturing virtual networks to enable private connectivity between resources in separate virtual-network address spaces.

The peering configuration enabled:

- Core Services virtual network access to Manufacturing virtual network resources
- Manufacturing virtual network access to Core Services virtual network resources
- Forwarded traffic support between the peered virtual networks
- Private connectivity without exposing the virtual machines through public inbound ports

## Connectivity Validation

Before peering was configured, Azure Network Watcher showed that the test virtual machines were unreachable because they were located in separate virtual networks.

After virtual network peering was configured, PowerShell connectivity testing confirmed that the Manufacturing virtual machine could reach the Core Services virtual machine over TCP port 3389.

## Custom Route Configuration

A perimeter subnet was created in the Core Services virtual network.

A route table was then created and associated with the perimeter subnet. The route directed traffic for the Core Services virtual-network address range to a future virtual appliance.

The virtual appliance was not deployed during this lab. The user-defined route was created to demonstrate how traffic can be directed through a future network-security or inspection device.

## Validation

I validated the lab by confirming:

- The Core Services and Manufacturing virtual machines were successfully deployed.
- The virtual networks used separate, non-overlapping address ranges.
- Azure Network Watcher showed that connectivity was unavailable before peering.
- Bidirectional virtual network peering was created successfully.
- Both peering connections displayed a connected status.
- PowerShell Test-NetConnection successfully validated TCP connectivity after peering.
- The perimeter subnet was created successfully.
- The route table and user-defined route were created successfully.
- The route table was associated with the perimeter subnet.

## Security Considerations

- Used separate virtual networks to segment core-service and manufacturing workloads.
- Used non-overlapping address spaces to support connectivity and simplify troubleshooting.
- Kept public inbound ports disabled on test virtual machines.
- Used private virtual network peering for communication between virtual networks.
- Applied a user-defined route to support future traffic inspection through a network virtual appliance.
- Used a personal, non-production Azure environment and test data only.
- Did not upload passwords, public IP addresses, tenant identifiers, subscription identifiers, screenshots containing sensitive information, or course-provided files to GitHub.

## Troubleshooting

No issues were encountered during this lab. Virtual-machine deployment, Network Watcher validation, virtual network peering, PowerShell connectivity testing, and route-table configuration were completed as expected.

## Cleanup

- Deleted test virtual machines and associated network interfaces.
- Deleted test virtual networks, peerings, route tables, and user-defined routes.
- Deleted the test resource group after completing validation.
- Confirmed that no unnecessary Azure resources remained active.

## Lessons Learned

- Resources in separate Azure virtual networks cannot communicate by default.
- Virtual network peering enables private connectivity between separate Azure virtual networks.
- Network Watcher can identify and troubleshoot connectivity issues between Azure resources.
- PowerShell Test-NetConnection can validate connectivity to a specific destination and TCP port.
- User-defined routes can override or supplement default Azure system routes.
- Route tables can direct traffic through a network virtual appliance for inspection or security enforcement.
- Network segmentation, peering, and routing work together to support secure Azure network design.
