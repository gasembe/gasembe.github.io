## Using dlt for Extraction and Load in Your Data Warehouse

Ever wondered how you can move an entire database or a set of database objects from one database platform to another. For example Oracle to SQL server, SQL server to PostgreSQL or MySQL to Oracle, without recreating the source database and its objects in the destination database system?. 

I was recently engaged in a project at a client's site that required porting analytics data mart from Oracle to Microsoft SQL server. You might be wondering why this was necessary, so first some background. 

### THE BUSINESS CASE
The client had an on-prem oracle data warehouse and analytics platform, meaning the entire implementation was based on oracle business intelligence stack(Oracle data warehouse, ODI, OAS) running on oracle engineered systems hardware.

For some reasons the business felt that the oracle platform was not serving their BI needs and cited issues ranging from reports performance, visualization aesthetics among others. They were thefore contemplating on replacing their oracle analytics platform with Microsoft Power BI server, an on-premise version of the Microsoft Azure Power BI service. However before arriving on such a decision they needed to explore the capabilities of Power BI server. We decided a POC using one of their foundational use-cases subject area data mart would be the best approach. They would therefore run the two on-prem business intelligence platforms in parallel to decide on which platform best serves their business intelligence needs better. Since consultants are somewhat perceived to be magicians they needed the Power BI server up and running as soon as possible.

### PROBLEM

AS the consultant my task was to set up the Power BI server on prem, develop the data models for the selected subject area, implement etl pipelines to load data to SQL server, which was to be used as the reports and dashboards source for Power BI. Typically executing these tasks would consume alot of time with the most of the time going into the ETL phase of the project.
It is estimated that in a datawarehouse project 70% of development time goes into ETL development. Given that the subject area 
implementation was in place in the Oracle datawarehouse and I didnt have the luxery of time, redeveloping the datamart in SQL server was not going to be a good spend of my time. The question I needed to answer thefore was "How do move/port the subject area datamart from oracle to MS SQL server with minimal development effort and delover the POC on time". Some of the approaches in considerations were

* Create the required data mart objects for the subject area in SQL server, then use Oracle data integrator to develop   
     ETL package to load the fact and dimensions from oracle datawarehouse to SQL server.
* Use microsoft data migration assistant for oracle tool to migrate the data mart from Oracle to SQL server


Option 1 was going to take longer to implement given that it involved actual development effort. Option 2 seemed viable, but the only problem for me was, it's a new tool I had not used before therefore i needed to learn how to use it, experiment before i could use it for the POC, I didnt have that time!.
