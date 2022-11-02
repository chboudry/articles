---
metadata-title: Azure Landing Zone review 
metadata-image: 
metadata-description: This is a cheatsheet checkpoints list to review Azure Landing Zone review.
metadata-createddate: 02/11/2022
metadata-updateddate: 02/11/2022
metadata-tag: architecture
metadata-author: Charles Boudry
---

# Azure Landing Zone Review

## Context
This is a quick list to remember not to forget any topic during a landing zone review.

This is very high level.

For more pin point Microsoft recommendations on Azure Services, go to https://github.com/Azure/review-checklists

## The list 

- Requirements
	- Business Requirement
	- Technical Requirements
	- Assumptions
- Solution Overview
	- Project Name Platform.
	- High Level Design
	- Overview
- Design Description
	- Governance
		- Azure Tenant
		- Azure Resource Naming Convention
		- Subscriptions
		- Management Groups
		- Resource Groups
		- Azure Policies
		- Locks
		- Azure Blueprint
		- Azure Tags
	- Identity
		- AD + ADFS + AAD Connect
		- AADDS
		- RACI + Role Based Access Control
		- Multi Factor Authentication
		- Block Legacy Authentication
		- Security Defaults
		- Privileged Identity Management (PIM)
	- Networking
		- Topology
		- Address Spaces / On-premises IP range(s)
		- Virtual Network
		- Virtual Network Peering.
		- Azure Route Tables (User Defined Routes)
		- Azure Private Endpoint
		- Virtual Network Gateway
		- Express Route
		- Load Balancer
		- Network Security Groups
		- Azure Firewall
		- Application Gateway
		- Traffic Manager
		- Network Virtual Appliances
		- Azure Virtual WAN
		- DDOS
		- DNS
	- Deployment
		- Infrastructure as code
		- Application - Devops
		- Machine learning - Mlops
	- Security misc
		- Microsoft Defender For Cloud ( Azure Security Center) basic + standard
		- SIEM - Azure Sentinel
	- Compute
		- Virtual Machines
		- Virtual Machine Scale Sets
		- Availability Sets.
		- Availability Zones
		- Hard Disk Storage
		- AKS
		- Compute Licensing
		- Pay as You Go
		- Hybrid Use Benefit
		- Reserved Instances
		- Bring Your Own License – Network Virtual Appliances
	- PaaS
		- Storage Accounts
		- Web Apps
		- App Service Plan
	- SQL
		- SQL on Azure Virtual Machines
		- Azure SQL Database
		- Azure SQL Database Managed Instance
	- Serverless
		- Functions
		- Event Grid

