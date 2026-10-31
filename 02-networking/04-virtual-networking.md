# Lab 04: Implement Azure Virtual Networking

## Status

Completed

## Architecture Diagram

[View the Lab 04 Azure Virtual Networking architecture diagram](../diagrams/lab-04-virtual-networking-diagram.md)

## Objective

Create and configure Azure virtual networks, subnets, network security groups, application security groups, public DNS zones, and private DNS zones in a non-production Azure environment.

## Skills Practiced

- Creating Azure virtual networks
- Designing non-overlapping IP address spaces
- Creating and configuring subnets
- Exporting Azure Resource Manager templates
- Deploying virtual networks through ARM templates
- Creating Application Security Groups
- Creating Network Security Groups
- Associating NSGs with subnets
- Configuring inbound NSG rules
- Configuring outbound NSG rules
- Using service tags in security rules
- Creating public Azure DNS zones
- Creating public DNS A records
- Creating private Azure DNS zones
- Linking private DNS zones to virtual networks
- Creating private DNS A records
- Validating DNS name resolution

## Environment

- Platform: Microsoft Azure
- Environment type: Personal non-production Azure lab
- Networking services: Azure Virtual Network, subnets, Network Security Groups, Application Security Groups, Azure DNS, and Private DNS Zones
- Data used: Test resources and test IP addressing only

## Scenario

A growing organization required a scalable virtual-network design to support core services and manufacturing systems. The objective was to create separate virtual networks with non-overlapping address ranges, apply network-security controls, and configure public and private DNS name resolution.

## Implementation Summary

I completed the following actions:

1. Created a Core Services virtual network through the Azure portal.
2. Configured a non-overlapping virtual-network address space.
3. Created separate subnets for shared services and database resources.
4. Exported the Core Services virtual-network configuration as an Azure Resource Manager template and parameter file.
5. Modified the exported template to create a second virtual network for manufacturing resources.
6. Configured the manufacturing virtual network with a separate non-overlapping address space.
7. Created two manufacturing sensor subnets through the modified ARM template.
8. Created an Application Security Group for web-tier workloads.
9. Created a Network Security Group and associated it with the shared-services subnet.
10. Configured an inbound NSG rule allowing TCP web traffic on ports 80 and 443 from the Application Security Group.
11. Configured an outbound NSG rule denying internet access from the protected subnet.
12. Created a public Azure DNS zone and added a test A record.
13. Validated public DNS resolution using a DNS lookup query.
14. Created a private Azure DNS zone.
15. Linked the private DNS zone to the manufacturing virtual network.
16. Created a private DNS A record for a test manufacturing resource.
17. Deleted test resources after completing validation.

## Virtual Network Design

The lab used separate virtual networks and non-overlapping private address spaces to support growth, simplify troubleshooting, and reduce the risk of network conflicts.

The Core Services virtual network included dedicated subnets for:

- Shared services
- Database resources

The Manufacturing virtual network included dedicated subnets for:

- Sensor workloads
- Future manufacturing-device growth

## Network Security Controls

An Application Security Group was created to logically represent web-tier resources.

A Network Security Group was associated with the shared-services subnet and configured with:

- An inbound rule allowing TCP traffic on ports 80 and 443 from the web Application Security Group.
- An outbound deny rule preventing traffic to the Internet service tag.
- Default NSG rules reviewed to understand baseline inbound and outbound behavior.

## DNS Configuration

### Public DNS

A public Azure DNS zone was created with a test A record to validate public-domain name resolution.

### Private DNS

A private Azure DNS zone was created and linked to the manufacturing virtual network. A private A record was added to support internal name resolution for a test manufacturing resource.

## Validation

I validated the lab by confirming:

- The Core Services virtual network was created with the intended address space and subnets.
- The Manufacturing virtual network was successfully deployed through a modified ARM template.
- The virtual networks used non-overlapping address spaces.
- The Application Security Group and Network Security Group were created successfully.
- The NSG was associated with the intended subnet.
- The inbound web-traffic rule allowed traffic from the Application Security Group on ports 80 and 443.
- The outbound rule denied traffic to the Internet service tag.
- The public DNS zone successfully resolved the test A record.
- The private DNS zone was linked to the manufacturing virtual network.
- The private DNS zone contained the configured test record.

## Security Considerations

- Used non-overlapping IP address ranges to support future growth and reduce network-conflict risk.
- Segmented resources into dedicated subnets based on workload purpose.
- Used an Application Security Group to represent web-tier workloads.
- Applied an NSG to control inbound and outbound traffic at the subnet level.
- Restricted outbound internet access through an explicit deny rule.
- Used private DNS for internal name resolution within a linked virtual network.
- Used a personal, non-production Azure environment and test data only.
- Did not upload credentials, public IP addresses, tenant identifiers, subscription identifiers, screenshots with sensitive information, or course-provided templates to GitHub.

## Troubleshooting

No issues were encountered during this lab. Virtual-network deployment, ARM template deployment, NSG configuration, Application Security Group configuration, public DNS validation, and private DNS configuration were completed as expected.

## Cleanup

- Deleted test virtual networks, subnets, NSGs, Application Security Groups, DNS zones, and associated records.
- Deleted the test resource group after completing validation.
- Confirmed that no unnecessary Azure resources remained active.

## Lessons Learned

- Azure virtual networks provide isolated network environments for cloud resources.
- Non-overlapping IP address ranges are important for scalability, connectivity, and troubleshooting.
- Subnets segment workloads and support security boundaries within a virtual network.
- ARM templates enable repeatable infrastructure deployment.
- Application Security Groups simplify security-rule management by grouping workloads by function.
- Network Security Groups control inbound and outbound network traffic.
- Public Azure DNS supports internet-facing name resolution.
- Private Azure DNS supports internal name resolution for linked virtual networks.
- DNS zones, NSGs, ASGs, and subnet design work together to support secure Azure networking.
