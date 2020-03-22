## MLOps on Databricks

This article is a walkthrough of a [GitHub repository](https://github.com/Azure-Samples/MLOpsDatabricks) that demonstrates how to build and deploy a Machine Learning Pipeline using Azure.  It's targeted towards Data Engineers, Data Scientists, and Data Architects who need to build and deploy Machine Learning workloads using DevOps processes within Enterprise Azure environments.

By the end of this article, you will have worked with the following Azure services:

| Azure Service  | Function |
| :- | :-  |
| Machine Learning Python SDKs | Manage Machine Learning models |
| Azure Databricks | Use its compute power as a Remote Compute for training models | 
| Azure DevOps | The platform to help you implement DevOps practices on your scenario |
| Azure Container Instance | Deploy Machine Learning models as Docker containers |

To get started, we need to deploy the base resources:

* Azure Devops

Within an Enterprise, you should already have an Azure DevOps service up and running.  If not, you can sign up [here](https://docs.microsoft.com/en-us/azure/devops/user-guide/sign-up-invite-teammates?view=azure-devops)

1. From the DevOps Dashboard, create a project 
{% include screenshot url="databricks-devops/new-project.png" %}
![](/images/databricks-devops/new-project.png)

Select the option for Visibility - Public for anyone on the Internet, Enterprise for anyone in your Azure DevOps organisation, and Private for invite-only access.  The advanced tab gives you the option of Git or TFS for version control (we want Git), and what process to use for work items (Agile, Basic, CMMI, and Scrum).  As this is only for a demonstration, we can leave the default (Basic).  Once you click Create, processing takes a few moments to set everything up.

{% include screenshot url="databricks-devops/project-details.png" %}
![](/images/databricks-devops/project-details.png)

2. Import the repository into your DevOps project
**Alternatively, your Pipelines can directly connect to GitHub Repositories - however additional configration is required to authorise Azure DevOps with your GitHub account**
You should now be inside your new DevOps Project.  We now need to import the repo into the DevOps project.  In future, you can create a template specific for your organisation and import that.  In the Repos->Files window, click on Import and use https://github.com/Azure-Samples/MLOpsDatabricks as the Clone URL, and then Import.

{% include screenshot url="databricks-devops/clone-url.png" %}
![](/images/databricks-devops/clone-url.png)

The code base isn't large, so the clone should only take a couple of seconds, after which you will see your repo populated with the cloned files.

{% include screenshot url="databricks-devops/files-repo.png" %}
![](/images/databricks-devops/files-repo.png)

3. Integration between Azure DevOps and the Azure subscription.
For Azure DevOps to be able to deploy Azure resources, your Project must have a connection established to your Azure subscription.  There are a couple of ways to establish the connection, all dependant on how much permission you have to within Azure Active Directory (Azure AD).  For this demo, we'll assume that our IT Infrastructure team has created a [Service Principal](https://docs.microsoft.com/en-us/azure/devops/pipelines/library/connect-to-azure?view=azure-devops#create-an-azure-resource-manager-service-connection-with-an-existing-service-principal) in Azure AD, and provided us with the details.  This allows IT to manage a separation of between user and system roles.  For alternative approaches, further details are included in this [article](https://docs.microsoft.com/en-us/azure/devops/pipelines/library/connect-to-azure?view=azure-devops#create-an-azure-resource-manager-service-connection-using-automated-security).  

    3.1 In Azure DevOps, open the Service connections page from the project settings page (in the Pipeline heading). The project settings page is at the bottom of the left panel from the main project dashboard.
    {% include screenshot url="databricks-devops/project-settings.png" %}
    ![](/images/databricks-devops/project-settings.png)

    3.2 {% include screenshot url="databricks-devops/create-service-connection.png" %} ![](/images/databricks-devops/create-service-connection.png) and select Azure Resource Manager.
    3.3 If you have the appropriate permissions, you can automatically create a Service Principal, otherwise click the text "use the full version of the service connection dialog" to display additional fields for entering the Service Principal ID and key (provided by IT).  Make sure to check **Allow all pipelines to use this connection**.

    {% include screenshot url="databricks-devops/azure-subscription.png" %}
    ![](/images/databricks-devops/azure-subscription.png)

4. Configure an Azure DevOps pipeline for the infrastructure

5.  In the cluster.py script, there are some hard coded values for spark-version.  Not current.  Also torch not installed. Need to update library.json to include torch.                                                                                                                                                                                                                                                                                    `                        








                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        