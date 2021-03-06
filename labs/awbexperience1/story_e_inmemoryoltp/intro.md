<page title="Intro"/>

IN-MEMORY OLTP
====

MyExpenses is an application that aims to provide a comprehensive expense tracking system for companies all over the world. Every employee can log expenses using the MyExpenses web portal and get them reimbursed in either cash or company points, which can be spent in the company store without leaving MyExpenses. Managers can do everything an employee can, but also review, approve or reject the expense reports submitted by team members. 

![](img/0.png)

MyExpenses is built on top of a SQL Server 2016 database, with a frontend in AngularJS and a backend using Node.js. SQL Server allows us to easily scale the services offered to our clients and provide a good performance. There are thousands of users of MyExpenses all over the world, and for most of them performance is a really important feature: sometimes a deal-breaker. In our web appliccation, for security reasons, every request and response is logged into an auditory table.

Using this table "as is" is leading us into big performance problem. Since this is a table where each and every request and response is stored, there are lots of concurrent operations generated by the web application. The more the web is used, the more traffic hits this table. This is a performance problem, because it can impact the entire database due the IO operations, and lead to degraded performance across the whole site. We've decided to migrate the auditory table to an In-Memory OLTP table in order to support the high concurrency operations in the production environment.

IN-MEMORY OLTP IN SQL SERVER
------------------
SQL Server 2016 has the In-Memory OLTP feature for in memory tables. It improves throughput and reduces latency for transaction processing, and can help improve performance of transient data scenarios such as temp tables and ETL. In-Memory OLTP is a memory-optimized database engine integrated into the SQL Server engine, optimized for transaction processing. Some of the features are:

 - Eliminate contention and logging in a high data insertion scenarios 
 - Require low latency business transactions which typical database solutions cannot achieve.
 - Efficient data retrieval.

 Check the following [link](https://msdn.microsoft.com/en-us/library/dn133186.aspx) for further info about the In-Memory OLTP feature.