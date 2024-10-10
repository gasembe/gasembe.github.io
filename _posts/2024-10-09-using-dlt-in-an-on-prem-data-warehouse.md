## Using dlt for Extraction and Load in Your Data Warehouse

I was recently engaged in a project at a clients site that required porting one data mart from oracle to Microsoft SQL server. First a little background, 
the client currently runs an on-prem oracle analytics platform. The entire datawarehouse implementation is based on oracle business intelligence stack and set of tools. 

For some reasons the business felt that the oracle platform was not serving their needs and cited issues to do with reports dashbords performance, visualization aesthetics among others. The client was thefore contemplating on replacing their oracle datawarehouse platform with Microsoft Power BI server, which is an onprem versio of the cloud microsoft power BI service. However before arriving such a decision the client needed a POC for one of their foundational usecases data-mart on Microsoft 
Power BI server. They wanted to run the two on-prem business intelligence platforms in parallel to decide on which platform serves their business intelligence needs better. They needed the Power BI server up and running as soon as possible.

### PROBLEM

AS the consultant my task was to set up the Power BI server on prem, develop the data models for the selected subject area, implement etl pipelines to load data to SQL server, which was to be used as the reports and dashboards source for Power BI. Typically executing these tasks would consume alot of time with the most of the time going into the ETL phase of the project.
It is estimated that in a datawarehouse project 70% of development time goes into ETL development. Given that the subject area 
implementation was in place in the Oracle datawarehouse and I didnt have the luxery of time, redeveloping the datamart in SQL server was not going to be a good spend of my time. The question I needed to answer thefore was "How do move/port the subject area datamart from oracle to MS SQL server with minimal development effort and delover the POC on time". Some of the approaches in considerations were
<ul>
  <i>Create the required data mart objects for the subject area in SQL server, then use Oracle data integrator to develop   
     ETL package to load the fact and dimensions from oracle datawarehouse to SQL server.</i>
  <i>Use microsoft data migration assistant for oracle tool to migrate the data mart from Oracle to SQL server</i>
</ul>

Option 1 was going to take longer to implement given that it involved actual development effort. Option 2 seemed viable, but the only problem for me was, it's a new tool I had not used before therefore i needed to learn how to use it, experiment before i could use it for the POC, I didnt have that time!.
