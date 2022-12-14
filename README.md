# Data Warehousing/BI Analytics with IBM DB2 / IBM Cognos Analytics

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

This [lab](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20PostgreSQL%20using%20pgAdmin/instructional-labs.md.html?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDB0260ENSkillsNetwork27338483-2022-01-01) will guide you to understand how to Create Tables and Load Data in PostgreSQL using pgAdmin

OR

You need access to a cloud instance of IBM DB2 to proceed with this assignment.

If you do not have an instance of IBM DB2 on cloud, follow the instructions in this [lab](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Sign%20up%20for%20IBM%20Cloud%20-%20Create%20Db2%20service%20instance%20-%20Get%20started%20with%20the%20Db2%20console/instructional-labs.md.html?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDB0260ENSkillsNetwork27338483-2022-01-01) to create one.

You need access to Cognos Analytics.

This [lab](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/AnalyzingDataWithCognos/HandsOn_DB2CognosAnalytics.md.html?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDB0260ENSkillsNetwork27338483-2021-01-01) will guide to get your access to Cognos Analytics, and also get you started with how to use it to analyze the data.

## Exercise 1 - Design a Data Warehouse

The solid waste management company has provied you the sample data they wish to collect.

![Table](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/images/solid-waste-trips-new.png)

You will start your project by designing a Star Schema warehouse by identifying the columns for the various dimension and fact tables in the schema.

Task 1 - Design the dimension table MyDimDate
Write down the fields in the MyDimDate table in any text editor one field per line. The company is looking at a granularity of day. Which means they would like to have the ability to generate the report on yearly, monthly, daily, and weekday basis.

Here is a partial list of fields to serve as an example:

dateid
month
monthname
...
...

Take a screenshot of the fieldnames for the table MyDimDate.

Name the screenshot 1-MyDimDate.jpg. (Images can be saved with either the .jpg or .png extension.)

![1-MyDimDate](https://i.imgur.com/OepyNuz.jpg)

Task 2 - Design the dimension table MyDimWaste
Write down the fields in the MyDimWaste table in any text editor one field per line.

Take a screenshot of the fieldnames for the table MyDimWaste.

Name the screenshot 2-MyDimWaste.jpg. (Images can be saved with either the .jpg or .png extension.)

![2-MyDimWaste](https://i.imgur.com/Bkxo5KF.jpg)

Task 3 - Design the dimension table MyDimZone
Write down the fields in the MyDimZone table in any text editor one field per line.

Take a screenshot of the fieldnames for the table MyDimZone.

Name the screenshot 3-MyDimZone.jpg. (Images can be saved with either the .jpg or .png extension.)

![3-MyDimZone.jpg](https://i.imgur.com/h2QP1uR.jpg)

Task 4 - Design the fact table MyFactTrips
Write down the fields in the MyFactTrips table in any text editor one field per line.

Take a screenshot of the fieldnames for the table MyFactTrips.

Name the screenshot 4-MyFactTrips.jpg. (Images can be saved with either the .jpg or .png extension.)

![4-MyFactTrips](https://i.imgur.com/rRv6kTe.jpg)

## Exercise 2 - Create schema for Data Warehouse on DB2

In this exercise you will create the tables, you have designed in the previous exercise.

Task 5 - Create the dimension table MyDimDate

Create the MyDimDate table.

Take a screenshot of the sql statement you used to create the table MyDimDate.

Name the screenshot 5-MyDimDate.jpg. (Images can be saved with either the .jpg or .png extension.)

![5-MyDimDate](https://i.imgur.com/21CejFQ.jpg)

Task 6 - Create the dimension table MyDimWaste

Create the MyDimWaste table.

Take a screenshot of the sql statement you used to create the table MyDimWaste.

Name the screenshot 6-MyDimWaste.jpg. (Images can be saved with either the .jpg or .png extension.)

![6-MyDimWaste](https://i.imgur.com/zjd4cim.jpg)

Task 7 - Create the dimension table MyDimZone

Create the MyDimZone table.

Take a screenshot of the sql statement you used to create the table MyDimZone.

Name the screenshot 7-MyDimZone.jpg. (Images can be saved with either the .jpg or .png extension.)

![7-MyDimZone](https://i.imgur.com/4mV8j17.jpg)

Task 8 - Create the fact table MyFactTrips
Create the MyFactTrips table.

Take a screenshot of the sql statement you used to create the table MyFactTrips.

Name the screenshot 8-MyFactTrips.jpg. (Images can be saved with either the .jpg or .png extension.)

![8-MyFactTrips](https://i.imgur.com/hWN198K.jpg)

## Exercise 3 - Load data into the Data Warehouse

In this exercise you will load the data into the tables.

After the initial schema design, you were told that due to opertional issues, data could not be collected in the format initially planned.

You will load the data provided by the company in csv format.

Task 9 - Load data into the dimension table DimDate

Download the data from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/DimDate.csv

Load this data into DimDate table.

Take a screenshot of the first 5 rows in the table DimDate.

Name the screenshot 9-DimDate.jpg. (Images can be saved with either the .jpg or .png extension.)

![9-DimDate](https://i.imgur.com/Dui5mSO.jpg)

Task 10 - Load data into the dimension table DimTruck

Download the data from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/DimTruck.csv

Load this data into DimTruck table.

Take a screenshot of the first 5 rows in the table DimTruck.

Name the screenshot 10-DimTruck.jpg. (Images can be saved with either the .jpg or .png extension.)

![10-DimTruck](https://i.imgur.com/EQIvq5A.jpg)

Task 11 - Load data into the dimension table DimStation

Download the data from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/DimStation.csv

Load this data into DimStation table.

Take a screenshot of the first 5 rows in the table DimStation.

Name the screenshot 11-DimStation.jpg. (Images can be saved with either the .jpg or .png extension.)

![11-DimStation](https://i.imgur.com/osaCziJ.jpg)

Task 12 - Load data into the fact table FactTrips

Download the data from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/FactTrips.csv

Load this data into FactTrips table.

Take a screenshot of the first 5 rows in the table FactTrips.

Name the screenshot 12-FactTrips.jpg. (Images can be saved with either the .jpg or .png extension.)

![12-FactTrips](https://i.imgur.com/1at7vY8.jpg)

## Exercise 4 - Write aggregation queries and create MQTs

In this exercise you will query the data you have loaded in the previous exercise.

Task 13 - Create a grouping sets query

Create a grouping sets query using the columns stationid, trucktype, total waste collected.

Take a screenshot of the sql and the output rows.

Name the screenshot 13-groupingsets.jpg. (Images can be saved with either the .jpg or .png extension.)

![13-groupingsets](https://i.imgur.com/N6jr4bj.jpg)

Task 14 - Create a rollup query

Create a rollup query using the columns year, city, stationid, and total waste collected.

Take a screenshot of the sql and the output rows.

Name the screenshot 14-rollup.jpg. (Images can be saved with either the .jpg or .png extension.)

![14-rollup](https://i.imgur.com/PLrAeY3.jpg)

Task 15 - Create a cube query

Create a cube query using the columns year, city, stationid, and average waste collected.

Take a screenshot of the sql and the output rows.

Name the screenshot 15-cube.jpg. (Images can be saved with either the .jpg or .png extension.)

![15-cube](https://i.imgur.com/V0L8wQE.jpg)

Task 16 - Create an MQT

Create an MQT named max_waste_stats using the columns city, stationid, trucktype, and max waste collected.

Take a screenshot of the sql.

Name the screenshot 16-mqt.jpg. (Images can be saved with either the .jpg or .png extension.)

![16-mqt](https://i.imgur.com/edqS7Mg.jpg)

## Exercise 5 - Create a dashboard using Cognos Analytics

Download the data from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/DataForCognos.csv

Use the DataForCognos.csv file to generate the following charts.

Task 17 - Create a pie chart in the dashboard

Create a pie chart that shows the waste collected by truck type.

Take a screenshot of the pie chart.

Name the screenshot 17-pie.jpg. (Images can be saved with either the .jpg or .png extension.)

![17-pie](https://i.imgur.com/CzBt2dX.jpg)

Task 18 - Create a bar chart in the dashboard

Create a bar chart that shows the waste collected station wise.

Take a screenshot of the bar chart.

Name the screenshot 18-bar.jpg. (Images can be saved with either the .jpg or .png extension.)

![18-bar](https://i.imgur.com/1aMNFE3.jpg)

Task 19 - Create a line chart in the dashboard

Create a line chart that shows the waste collected by month wise.

Take a screenshot of the line chart.

Name the screenshot 19-line.jpg. (Images can be saved with either the .jpg or .png extension.)

Hint: Use Extract function in Create Calculation to collect the data month wise.

![19-line](https://i.imgur.com/FhARUOH.jpg)

Task 20 - Create a pie chart in the dashboard

Create a pie chart that shows the waste collected by city.

Take a screenshot of the pie chart.

Name the screenshot 20-pie.jpg. (Images can be saved with either the .jpg or .png extension.)

![20-pie](https://i.imgur.com/xl5Mu8Q.jpg)
