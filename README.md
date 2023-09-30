# Microsoft Azure: From Zero to Hero

**Microsoft Azure** is one of the most popular public clouds in the industry, and it gets bigger and bigger by the day. Thousands of organizations, from all sizes and shapes, are moving to the cloud, and being able to work with it is one of the most important skills for every developer, architect, or IT admin. In this project, we will study the major and most up-to-date cloud services services in Azure, such as:
- Azure Compute - Virtual Machines, App Services, AKS, Azure Functions and more
- Azure Networking - VNets, Subnets, NSG, Application Gateway and more
- Data in Azure - Azure SQL, CosmosDB, Azure MySQL, Storage Account and more
- Messaging in Azure - Event Grid, Queues, Service Bus, Event Hubs
- Azure Active Directory (also known as Azure AD)
- Logging and Monitoring in Azure
- Securing systems in Azure
- Cost Management
- Disaster Recovery (DR)


## Azure Compute

### Creating virtual machine

- create VM
<img src="/pictures/vm.png" title="virtual machine"  width="900">

### ARM Templates

- create template
<img src="/pictures/vm1.png" title="virtual machine"  width="500">

- deploy
```
az deployment group create --resource-group alexeirg --template-file "ARMTemplates\template.json" --parameters "ARMTemplates\parameters.json"
```

- once the deployment is done, you should have the following result
<img src="/pictures/vm2.png" title="virtual machine"  width="900">

### Virtual Machine Scale Set

- create VMSS
<img src="/pictures/vmss.png" title="virtual machine scale set"  width="900">

- add *Custom Autoscale*
<img src="/pictures/vmss2.png" title="virtual machine scale set"  width="900">
