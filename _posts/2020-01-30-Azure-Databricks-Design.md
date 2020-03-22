# Databricks

Azure Databricks is an Apache Spark-based analytics platform optimized for the Microsoft Azure cloud services platform. Designed with the founders of Apache Spark, Databricks is integrated with Azure to provide one-click setup, streamlined workflows, and an interactive workspace that enables collaboration between data scientists, data engineers, and business analysts.

## Service Description

This post will look at the Azure Databricks service and associated tools.  It will cover how to provision an Azure Databricks workspace, create a Spark cluster in the Databricks workspace, create a notebook, write data processing (ETL or ELT) in your favorite language and execute the code interactively, one cell at a time right in the notebook.

## Agenda

* Overview of Azure Databricks
* Provision Azure Databricks workspace & Create a cluster
* Extract Data from Azure DataLake, Transform the data and Load into Azure SQL DW
* Use Cognitive Services to perform Sentiment Analysis on Streaming data via Event Hub (Optional)
* Creating a Machine Learning Pipeline with Databricks (Optional)

## Prerequisites

* Azure subscription with permissions to create an Azure Databricks cluster.


## Delivery Guide

In this Delivery you have multiple choices of POC depending on what the customer is trying to achieve.  ETL from Datalake to SQL DW is the standard data wrangling POC used in the course and is the most expected POC to be run.  There are POCs for Cognitive Services and ML if the customers is more interested in an AI solution with Databricks vs other Azure AI technologies.

Title | Source format | Deliver from | Delivery/Readiness Resources
------------ | -------------| ------------ | -------------
What is Azure Databricks | Docs | -----> | [https://docs.microsoft.com/en-us/azure/azure-databricks/what-is-azure-databricks](https://docs.microsoft.com/en-us/azure/azure-databricks/what-is-azure-databricks)
Creating a Databricks Cluster | Docs | -----> | [https://docs.microsoft.com/en-us/azure/azure-databricks/quickstart-create-databricks-workspace-portal](https://docs.microsoft.com/en-us/azure/azure-databricks/quickstart-create-databricks-workspace-portal)
ETL From DataLake to Azure DW | POC | -----> | [https://docs.microsoft.com/en-us/azure/azure-databricks/databricks-extract-load-sql-data-warehouse](https://docs.microsoft.com/en-us/azure/azure-databricks/databricks-extract-load-sql-data-warehouse)
Sentiment Analysis with Cognitive Services via Event Hub | POC | -----> | [https://docs.microsoft.com/en-us/azure/azure-databricks/databricks-sentiment-analysis-cognitive-services](https://docs.microsoft.com/en-us/azure/azure-databricks/databricks-sentiment-analysis-cognitive-services)
Using Machine Learning with Databricks | POC | -----> | [https://docs.azuredatabricks.net/getting-started/spark/machine-learning.html#machine-learning](https://docs.azuredatabricks.net/getting-started/spark/machine-learning.html#machine-learning)


# Readiness

This online video course will give you an overview and introduction to Databricks and Spark if you are new to the technology.  This will help you understand the concepts in the POCs listed above Pluralsight Reference [Apache Spark Fundamentals](https://app.pluralsight.com/library/courses/apache-spark-fundamentals/table-of-contents)

In addition, the following public GitHub documentation (co-authored by Microsoft and Databricks) is extremely useful. [Best Practises](https://github.com/Azure/AzureDatabricksBestPractices/blob/master/toc.md)

# Architecture Design

Planning, deploying, and running Azure Databricks (ADB) at scale requires many architectural decisions.  The following discussion provides some topics that should be considered during the design stage.

## Deployment
You can deploy ADB using Azure Portal or using ARM templates. One successful ADB deployment produces exactly one Workspace, a space where users can log in and author analytics apps. It comprises the file browser, notebooks, tables, clusters, DBFS storage, etc. More importantly, Workspace is a fundamental isolation unit in Databricks. All workspaces are completely isolated from each other.

Portal

ARM

Terraform
[Terraform](https://www.terraform.io/docs/providers/azurerm/r/databricks_workspace.html) can be used for provision workspaces 
### 

## Workspace
The first user to login and initialize the workspace is the workspace owner, and they are automatically assigned to the Databricks admin group. This person can invite other users to the workspace, add them as admins, create groups, etc. The ADB logged in user’s identity is provided by AAD, and shows up under the user menu in Workspace

## Identity
Azure Databricks uses Azure Active Directory (AAD) as the exclusive Identity Provider and there’s a seamless out of the box integration between them. This makes ADB tightly integrated with Azure just like its other core services. Any AAD member assigned to the Owner or Contributor role can deploy Databricks and is automatically added to the ADB members list upon first login. 

[!NOTE]
If a user is not a member of the Active Directory tenant, they can’t login to the workspace.

## Networking

## DevOps

## 

## Workload Considerations

The flexibility of the Databricks platform means it can be used for a number of different workload types; ETL, Machine Learning, BI Analytics, Streaming.

### Streaming


### Machine Learning
Databricks supports MLlib, a set of Spark-based machine learning libraries.  In addition, Microsoft MMLSpark can also be used in Azure Databricks.  However, there are additional aspects of machine learning that need to be considering, such as:
- Tracking: track experiments to record and compare parameters and results.
- Models: manage and deploy models from a variety of ML libraries to a variety of model serving and inference platforms.
- Projects: package ML code in a reusable, reproducible form to share with other data scientists or transfer to production.

We recommend customers use Azure Machine Learning services to provide this functionality.  However, Azure Databricks also provides a fully managed and hosted version of [MLflow](https://docs.microsoft.com/en-us/azure/databricks/applications/mlflow/) integrated with enterprise security features, high availability, and other Azure Databricks workspace features such as experiment and run management and notebook revision capture.


