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


## Resource List
<img src="/pictures/resources.png" title="resources"  width="500">


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

- add *Custom Autoscale* for adding a VM
<img src="/pictures/vmss2.png" title="virtual machine scale set"  width="900">

- add *Custom Autoscale* for removing a VM
<img src="/pictures/vmss3.png" title="virtual machine scale set"  width="900">

### Azure Instance Metadata Service

- inside your VM, install Postman
<img src="/pictures/ims.png" title="instance metadata service"  width="900">

- in postman, add in the headers
```
Metadata : true
```

- query that link
```
http://169.254.169.254/metadata/instance?api-version=2021-12-13
```

- you will get all the infos for the VM
<img src="/pictures/ims2.png" title="instance metadata service"  width="900">

- query that link
```
http://169.254.169.254/metadata/scheduledevents?api-version=2020-07-01
```

- you will get all the scheduled events for the VM
<img src="/pictures/ims3.png" title="instance metadata service"  width="900">



