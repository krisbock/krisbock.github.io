I was recently asked by a customer to help them trigger a Data Factory 

Some organisations have separate Azure Data Factory services for Production and other environments such as Development/UAT.

This article will show two different ways a Pipeline in one Data Factory service can trigger a Pipeline in another Data Factory service.  To fill out the scenario, we'll have a Pipeline in our Production Data Factory that copies an extract of data from our Production SQL 



1. Calling the Pipeline using the REST API.



2. Using Trigger Files.
This is a fairly straightforward approach, the main benefit is that it can work if your resources are in different Subscriptions without too much effort.  The flip-side is that, as using this approach grows within an organisation, you start maintaining a filesystem or blob store full of dummy files.