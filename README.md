# Data Warehousing

In this lab, you will use PostgreSQL/mySQL Database. PostgreSQL/mySQL is a Relational Database Management System (RDBMS) designed to efficiently store, manipulate, and retrieve data.

### Scenario

You are a data engineer hired by a solid waste management company. The company collects and recycles solid waste across major cities in the country of Brazil. The company operates hundreds of trucks of different types to collect and transport solid waste. The company would like to create a data warehouse so that it can create reports like

- total waste collected per year per city
- total waste collected per month per city
- total waste collected per quarter per city
- total waste collected per year per trucktype
- total waste collected per trucktype per city
- total waste collected per trucktype per station per city

You will use your data warehousing skills to design and implement a data warehouse for the company.

### Objectives

In this lab you will:

- Design a Data Warehouse
- Load data into Data Warehouse
- Write aggregation queries
- Create MQTs
- Create a Dashboard

### About the dataset

The dataset you would be using in this assignment is not a real life dataset. It was programmatically created for this assignment purpose.

### Prerequisites

You need use PostgreSQL Database to proceed with this assignment.

This [lab](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/AnalyzingDataWithCognos/HandsOn_DB2CognosAnalytics.md.html?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDB0260ENSkillsNetwork27338483-2021-01-01) will guide you to understand how to Create Tables and Load Data in PostgreSQL using pgAdmin

OR

You need access to a cloud instance of IBM DB2 to proceed with this assignment.

If you do not have an instance of IBM DB2 on cloud, follow the instructions in this [lab](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Sign%20up%20for%20IBM%20Cloud%20-%20Create%20Db2%20service%20instance%20-%20Get%20started%20with%20the%20Db2%20console/instructional-labs.md.html?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDB0260ENSkillsNetwork27338483-2022-01-01) to create one.

You need access to Cognos Analytics.

This [lab](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/AnalyzingDataWithCognos/HandsOn_DB2CognosAnalytics.md.html?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDB0260ENSkillsNetwork27338483-2021-01-01) will guide to get your access to Cognos Analytics, and also get you started with how to use it to analyze the data.