I work with a lot of customers that want to experiment with Machine Learning in Azure.  Often they have a business problem, but .

This post will guide through a suggested workflow that enables an organisation to start with a simple model/hypothesis and build out functionality until you have an enterprise ML platform.

1) Start the learning journey.
2) Your first ML experiment.
3) Training with Enterprise data stores.
4) Integrating with an orchestration tool
5) Publishing your model through a REST API 
6) Fully operational Deathstar

## Creating an Azure ML Workspace
Like all Azure resources, there a number of ways to create an Azure Machine Learning service Workspace; Portal, and ARM Deployment.

When you create an Azure ML service, there are a number of different resources that are provisioned:

* Azure Resource Group
* Azure Storage Account
* Azure Key Vault
* Azure Application Insights
* Azure Container Registry
* Azure Machine Learning workspace

### Portal
https://github.com/Azure/azure-quickstart-templates/tree/master/101-machine-learning-create

### Azure Resource Manager template
