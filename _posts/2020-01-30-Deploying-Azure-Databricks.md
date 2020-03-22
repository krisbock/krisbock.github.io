## Deployment
You can deploy Azure Databricks using the Azure Portal or using ARM templates. One successful ADB deployment produces exactly one Workspace, a space where users can log in and author analytics apps. It comprises the file browser, notebooks, tables, clusters, DBFS storage, etc. More importantly, Workspace is a fundamental isolation unit in Databricks. All workspaces are completely isolated from each other.

### Deployment Considerations
There are a number of aspects to consider when deploying Azure Databricks, which will be covered by subsequent blog posts.

### Terraform


### References
1. [Terraform](https://www.terraform.io/docs/providers/azurerm/r/databricks_workspace.html)
2. [Databricks] (https://databricks.com/blog/2019/05/07/efficient-databricks-deployment-automation-with-terraform.html)
3. 