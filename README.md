   Azure Resource Organization and Resource Groups
   Overview
This project demonstrates the principles of cloud governance and resource organization in Microsoft Azure. It focuses on how Subscriptions and Resource Groups act as the foundation for billing, security, and operational management. The goal is to design a scalable architecture that maintains control over costs and access as environments grow.

   Naming Convention
To ensure consistency and clarity, the following naming convention was used:
    • Subscription: sub-[environment]-[region]
    • Resource Group: rg-[application]-[environment]-[region]
    • Resource: res-[service]-[application]-[environment]-[region]
Example:
    • sub-prod-ukwest
    • rg-webapp-dev-ukwest
    • res-vm-webapp-prod-ukwest

   Resource Groups
Two Resource Groups were defined to separate environments:
    • Development RG: rg-webapp-dev-ukwest
    • Production RG: rg-webapp-prod-ukwest

   Deployed Resources (Simulated)
    • Virtual Machine (Linux) in Dev RG
    • Storage Account in Prod RG
    • SQL Database in Prod RG

   Tagging Strategy
Tags applied to resources for cost allocation and automation:
    • environment=production
    • owner=teamA
    • project=cloudlearning

   RBAC Permissions
Role assignments were simulated as follows:
    • Dev RG: Developers → Contributor role
    • Prod RG: Operators → Reader role, Admins → Owner role
This ensures least privilege access and separation of duties.

   Lifecycle Management
Tested bulk operations by deleting the temporary Dev RG.
All resources inside were removed collectively.

   Infrastructure as Code
Example Azure CLI commands:
az group create --name rg-webapp-dev-ukwest --location ukwest
az group create --name rg-webapp-prod-ukwest --location ukwest


Tenant (Azure Active Directory)
│
└── Management Group: mg-cloudlearning
    │
    └── Subscription: sub-prod-ukwest
        │
        ├── Resource Group: rg-webapp-dev-ukwest
        ├── Resource Group: rg-webapp-prod-ukwest
        ├── Resource Group: rg-database-test-ukwest
        └── Resource Group: rg-network-staging-ukwest
