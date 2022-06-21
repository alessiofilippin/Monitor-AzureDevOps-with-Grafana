# Monitor-AzureDevOps-with-Grafana

Azure DevOps is the tool of choice from Microsoft to administer your DevOps workflow: from Tasks to CI/CD to Tests.

It does have a huge choice of features and out-of-the-box functionalites. Unfortunatly, it does lack of a proper way to set up monitoring or analytics around your Azure DevOps Org.

One way to monitor Azure DevOps is to create custom dashboards for it using the widgets (https://docs.microsoft.com/en-us/azure/devops/report/dashboards/overview?view=azure-devops) - this is a good solution but the widget are limited and some of the most valuable informations are accessible only trough the APIs.

# Solution?

For enhance the monitoring capabilities of Azure DevOps, I tried to place Grafana on top of it. __Grafana__ is a well know visualization tool, it's openSource and it does have hundreds of features ... also, it does make some good looking kickass dashboards.

## Requirments

1) Grafana Installaed somewhere as PaaS or on a VM.
2) Connectivity from Grafana to Azure DevOps.
3) A User with read access to Azure DevOps.
4) Install the "infinity" plugin for Grafana. (https://grafana.com/grafana/plugins/yesoreyeram-infinity-datasource/)

__We are going to use the infinity plugin for Grafana, this plugin allow us to scrape any API endpoint and manipulate data using JSON or UQL language, quite powerful.__

## STEPS

### 1) Install Infinity plugin on Grafana

![image](https://user-images.githubusercontent.com/47082128/174770722-2c2ef059-703a-4a3d-812a-bfdbfb2a180a.png)

![image](https://user-images.githubusercontent.com/47082128/174770730-2b688e56-f724-4c33-8ebe-442fd775e62a.png)

### 2) Create a PAT for the Azure DevOps user / SP

__The PAT requires only read access to all the resources on Azure DevOps__

![image](https://user-images.githubusercontent.com/47082128/174771029-461118f0-07d1-4696-8b35-7a1efe6908a0.png)

### 3) Create an infinity datasource using the user's PAT as auth method

__use the PAT as password__

![image](https://user-images.githubusercontent.com/47082128/174771415-2ea8d4f6-81ba-43ea-b65b-1ffd0dc922b3.png)

### 4) Create your dashboards!

it's now possible scrape any azuredevops API url in your org and retrieve any kind of info that you require.
This is the reference to the AzureDevOps API docs (https://docs.microsoft.com/en-us/rest/api/azure/devops/?view=azure-devops-rest-7.1)

__you can find an example json file in this repo__

For example:

__Get details about the executed tests__

![Capture1](https://user-images.githubusercontent.com/47082128/174772332-e2982cfc-25df-476d-a1ea-da1a3f54b16b.PNG)

__Insights about the waiting times in the queue and agent pools which they wait the most.__

![Capture2](https://user-images.githubusercontent.com/47082128/174772692-3528b051-f825-4a88-94e4-6dff64366c27.PNG)

__Insights about the execution times and agent pools which they have the bigger execution time.__

![Capture3](https://user-images.githubusercontent.com/47082128/174773015-bd0e94e6-b1c4-48fc-a16a-9c39d56358a4.PNG)

