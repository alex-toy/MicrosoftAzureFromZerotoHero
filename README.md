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


## Setting up

In order to quickly delete all resources, run
```
./delete_resources.ps1
```

### Setting up the catalog app

- create resource group
```
az group create -l northeurope -n readit-app-rg
```

- create catalog VM
```
az deployment group create --resource-group readit-app-rg --template-file "ARMTemplates\catalog\template.json" --parameters "ARMTemplates\catalog\parameters.json"
```
<img src="/pictures/catalog_app.png" title="catalog app"  width="900">

- connect to it by RDP

- turn off *Enhanced Security Configuration*
<img src="/pictures/catalog_app2.png" title="catalog app"  width="900">

- install IIS
<img src="/pictures/catalog_app3.png" title="catalog app"  width="900">
<img src="/pictures/catalog_app4.png" title="catalog app"  width="900">
<img src="/pictures/catalog_app5.png" title="catalog app"  width="900">
<img src="/pictures/catalog_app6.png" title="catalog app"  width="900">

- install .NET 6 *Hosting Bundle*
<img src="/pictures/catalog_app7.png" title="catalog app"  width="900">

- create a *catalog* folder to host the app
<img src="/pictures/catalog_app8.png" title="catalog app"  width="900">

- publish the app to a local folder
<img src="/pictures/catalog_app9.png" title="catalog app"  width="900">

- copy all the published files to the VM in the *catalog* folder

- open IIS Manager and add web site
<img src="/pictures/catalog_app10.png" title="catalog app"  width="900">
<img src="/pictures/catalog_app11.png" title="catalog app"  width="900">

- you should now be able to start the app inside the VM
<img src="/pictures/catalog_app12.png" title="catalog app"  width="900">

- turn off the firewalls in the VM
<img src="/pictures/catalog_app13.png" title="catalog app"  width="900">

### Setting up the weather API

- create weather VM
```
az deployment group create --resource-group readit-app-rg --template-file "ARMTemplates\weather\template.json" --parameters "ARMTemplates\weather\parameters.json"
```

- connect to the VM through *Putty* and run commands
```
sudo apt install git
sudo apt update
sudo apt install nodejs
sudo git clone https://github.com/memilavi/weatherAPI.git
cd weatherAPI
sudo apt install npm
npm start
```

- in the catalog VM, paste the private IP of the weather VM. The two apps are able to communicate since they are on the same subnet.
<img src="/pictures/weather_app.png" title="weather app"  width="900">

### Setting up Inventory App Service

- create Web App
```
az deployment group create --resource-group readit-app-rg --template-file "ARMTemplates\web_app\template.json"
```
<img src="/pictures/ias.png" title="inventory app service"  width="900">
<img src="/pictures/ias2.png" title="inventory app service"  width="900">

- upload the code
<img src="/pictures/ias3.png" title="inventory app service"  width="900">

- see that it's running
<img src="/pictures/ias31.png" title="inventory app service"  width="900">

### Setting up Cart

- run locally
<img src="/pictures/cart.png" title="cart"  width="900">

- create container registry
<img src="/pictures/cart1.png" title="cart"  width="500">

- enable admin user
<img src="/pictures/cart2.png" title="cart"  width="900">

- add role assignment
<img src="/pictures/cart21.png" title="cart"  width="900">

- publish to ACR
<img src="/pictures/cart3.png" title="cart"  width="900">
<img src="/pictures/cart31.png" title="cart"  width="900">
<img src="/pictures/cart32.png" title="cart"  width="900">
<img src="/pictures/cart33.png" title="cart"  width="900">

- see the container in the repository
<img src="/pictures/cart4.png" title="cart"  width="900">

- create a kubernetes cluster
<img src="/pictures/cart5.png" title="cart"  width="500">
<img src="/pictures/cart51.png" title="cart"  width="500">

- run commands
```
az aks install-cli
```
