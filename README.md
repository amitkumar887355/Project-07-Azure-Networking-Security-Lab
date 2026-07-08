# Project-07-Azure-Networking-Security-Lab
# Project Overview  
This project demonstrates the implementation of a secure Azure network using Virtual Networks, Network Security Groups, Azure Bastion, Azure DDoS Protection, Azure Firewall, User Defined Routes (UDR), and DNAT rules.
# Architecture

# Virtual Network
  VNet: Vnet01

# Subnets
  S01-Jump
  S02-Prod
  AzureBastionSubnet
  AzureFirewallSubnet

# Virtual Machines
# JUMP-VM
  Windows Server
  Public IP assigned
  Used as the administrative jump server
# PROD-VM
  Windows Server
  Private IP only

# Accessible through:
  JUMP-VM
  Azure Bastion

# Network Security Group
  Created NSG01 and associated it with the Jump subnet.
  Inbound Rules
  Allow TCP 3389 (RDP)
  Outbound Rules
  Deny Internet access

# Validation
  RDP to JUMP-VM works successfully.
  Internet browsing from JUMP-VM is blocked.

# Azure DDoS Protection
  Created an Azure DDoS Protection Plan.
  Associated the plan with Vnet01.

# Azure Firewall
  Configuration
  Deployed Azure Firewall
  Created AzureFirewallSubnet
  Configured a User Defined Route (UDR) to direct Production subnet traffic through Azure Firewall
  Application Rules

  Allowed only:
  google.com
  tcs.com
  ibm.com

# Validation
  Approved websites are accessible.
  All other websites are blocked.

# DNAT Rule
  Configured Azure Firewall DNAT:
  Source: Any
  Destination: Azure Firewall Public IP
  Destination Port: 8080
  Translated Address: JUMP-VM Private IP
  Translated Port: 3389

# Validation
  Successfully connected to JUMP-VM using the Azure Firewall Public IP on port 8080.

# Azure Services Used
  Azure Virtual Network
  Subnets
  Windows Virtual Machines
  Network Security Groups (NSG)
  Azure Bastion
  Azure Firewall
  User Defined Routes (UDR)
  Azure DDoS Protection
  Public IP Addresses
  DNAT Rules

# Skills Demonstrated
  Azure Networking
  Cloud Security
  Secure Remote Administration
  Network Segmentation
  Traffic Routing
  Firewall Policy Configuration
  Network Access Control
  Azure Infrastructure Administration
# Future Enhancements
  Azure VPN Gateway
  Azure Application Gateway
  Azure Load Balancer
  Azure Monitor
Log Analytics
Microsoft Defender for Cloud
Azure Policy
