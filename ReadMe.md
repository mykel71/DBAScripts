# 1. Sample for use of Always Encrypted in WideWorldImportersDW

This script demonstrates the use of Always Encrypted to encrypt sensitive data in the database.


### Contents

[About this sample](#about-this-sample)<br/>
[Before you begin](#before-you-begin)<br/>
[Running the sample](#run-this-sample)<br/>
[Sample details](#sample-details)<br/>
[Disclaimers](#disclaimers)<br/>
[Related links](#related-links)<br/>


<a name=about-this-sample></a>

## About this sample

<!-- Delete the ones that don't apply -->
1. **Applies to:** SQL Server 2016 (or higher), Azure SQL Database
1. **Key features:** Always Encrypted
1. **Workload:** OLTP
1. **Programming Language:** T-SQL, C#
1. **Authors:** Greg Low, Jos de Bruijn
1. **Update history:** 26 May 2016 - initial revision

<a name=before-you-begin></a>

## Before you begin

To run this sample, you need the following prerequisites.

**Software prerequisites:**

<!-- Examples -->
1. SQL Server 2016 (or higher) or Azure SQL Database.
2. SQL Server Management Studio
3. Visual Studio 2015
4. The WideWorldImporters database.

<a name=run-this-sample></a>

## Running the sample

1. Build the solution to create the data population app.

2. Open both scripts in different windows or tabs in Management Studio.

3. Follow the instructions in the main script DemonstrateAlwaysEncrypted.sql.

## Sample details

The sample adds a new table with sensitive data about suppliers. This sensitive data is always encrypted.

As part of the sample you create an encryption key that is saved locally (where you run SSMS). The client application inserts data into the table. With the sample scripts you will see how the data is encrypted in the table and cannot be viewed, even by a sysadmin, unless you have the encryption key.

<a name=disclaimers></a>

## Disclaimers
The code included in this sample is not intended to be used for production purposes.

<a name=related-links></a>

## Related Links
<!-- Links to more articles. Remember to delete "en-us" from the link path. -->
For more information, see these articles:
- [Always Encrypted documentation](https://msdn.microsoft.com/library/mt163865.aspx)
- [Keep Sensitive Data Secure with Always Encrypted](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/AlwaysEncrypted)




# 2. Sample performance with In-Memory OLTP in WideWorldImporters

This script simulates an insertion workload for vehicle location in the WideWorldImporters sample database. Note that this script is single-threaded. For a multi-threaded variant, see the [vehicle-location-insert](../../workload-drivers/vehicle-location-insert) workload driver.

The main purpose is to compare the performance of data insertion into traditional disk-based tables compared with memory-optimized tables. For a more comprehensive sample demonstrating the performance of In-Memory OLTP see the [in-memory/ticket-reservations](/samples/features/in-memory/ticket-reservations) sample.

### Contents

[About this sample](#about-this-sample)<br/>
[Before you begin](#before-you-begin)<br/>
[Running the sample](#run-this-sample)<br/>
[Sample details](#sample-details)<br/>
[Disclaimers](#disclaimers)<br/>
[Related links](#related-links)<br/>


<a name=about-this-sample></a>

## About this sample

<!-- Delete the ones that don't apply -->
1. **Applies to:** SQL Server 2016 (or higher), Azure SQL Database
1. **Key features:** Core database features
1. **Workload:** single-threaded insert
1. **Programming Language:** T-SQL
1. **Authors:** Greg Low, Jos de Bruijn
1. **Update history:** 25 May 2016 - initial revision

<a name=before-you-begin></a>

## Before you begin

To run this sample, you need the following prerequisites.

**Software prerequisites:**

<!-- Examples -->
1. SQL Server 2016 (or higher) or Azure SQL Database.
2. The WideWorldImporters database.

<a name=run-this-sample></a>

## Running the sample

1. Execute the script in SSMS.

2. Observe the time taken for the inserts in disk-based and memory-optimized tables.

## Sample details

This script creates comparable disk-based and memory-optimized tables, as well as corresponding stored procedures, for vehicle location insertion.

It then compares the performance of single-threaded insert of 500,000 row:
 - into a disk-based table
 - into a memory-optimized table
 - into a memory-optimized table, with rows generated in a natively compiled stored procedure

The script outputs the time taken for each

<a name=disclaimers></a>

## Disclaimers
The code included in this sample is not intended to be used for production purposes.

<a name=related-links></a>

## Related Links
<!-- Links to more articles. Remember to delete "en-us" from the link path. -->
For more information, see these articles:
- [In-Memory OLTP documentation](https://msdn.microsoft.com/library/dn133186.aspx)
- [In-Memory OLTP quick start](https://msdn.microsoft.com/library/mt694156.aspx)
- [In-Memory OLTP in SQL Server 2016 (video)](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/InMemoryOLTP)
- [Get started with In-Memory in SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-in-memory/)



# 3. Sample performance with Operational Analytics in WideWorldImporters

This script shows the performance of analytics queries in the operational database. It relies on the [Order Insert](../../workload-drivers/vehicle-location-insert/) workload driver.

The main purpose is to show the performance benefits of using nonclustered columnstore indexes for analytics queries on operational systems, and how they limit the impact on the operational workload.

### Contents

[About this sample](#about-this-sample)<br/>
[Before you begin](#before-you-begin)<br/>
[Running the sample](#run-this-sample)<br/>
[Sample details](#sample-details)<br/>
[Disclaimers](#disclaimers)<br/>
[Related links](#related-links)<br/>


<a name=about-this-sample></a>

## About this sample

<!-- Delete the ones that don't apply -->
1. **Applies to:** SQL Server 2016 (or higher), Azure SQL Database
1. **Key features:** nonclustered columnstore index
1. **Workload:** Operational Analytics
1. **Programming Language:** T-SQL
1. **Authors:** Greg Low, Jos de Bruijn
1. **Update history:** 26 May 2016 - initial revision

<a name=before-you-begin></a>

## Before you begin

To run this sample, you need the following prerequisites.

**Software prerequisites:**

<!-- Examples -->
1. SQL Server 2016 (or higher) or Azure SQL Database.
2. SQL Server Management Studio
3. The WideWorldImporters database (Full version).

<a name=run-this-sample></a>

## Running the sample

1. Run the [Order Insert](../../workload-drivers/vehicle-location-insert/) workload for a while. When starting from the vanilla WideWorldImporters database the recommendation is to run at least 20 minutes, to ensure that enough data is generated and that compression kicks in (the sample has a COMPRESSION_DELAY of 10 minutes for the columnstore indexes).

2. Execute the sample script.

3. Open the Messages pane in SSMS and observe the time taken to run the query with and without columnstore index.

## Sample details

The [Order Insert](../../workload-drivers/vehicle-location-insert/) workload driver is used to simulate an order processing workload. The queries in the sample script are reporting queries run with and without columnstore index.

<a name=disclaimers></a>

## Disclaimers
The code included in this sample is not intended to be used for production purposes.

<a name=related-links></a>

## Related Links
<!-- Links to more articles. Remember to delete "en-us" from the link path. -->
For more information, see these articles:
- [Get started with Columnstore for real time operational analytics](https://msdn.microsoft.com/library/dn817827.aspx)
- [Real-Time Operational analytics with SQL Server 2016 (video)](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/Real-Time-Operational-analytics)




# 4. Sample Querying of External Data Source in WideWorldImportersDW

This script demonstrates the use of PolyBase to query an external data source.

Demographics data is available in Azure blob storage. This data is joined with sales data recorded in the local database to determine which would be good candidates for future expansion of the business.

### Contents

[About this sample](#about-this-sample)<br/>
[Before you begin](#before-you-begin)<br/>
[Running the sample](#run-this-sample)<br/>
[Sample details](#sample-details)<br/>
[Disclaimers](#disclaimers)<br/>
[Related links](#related-links)<br/>


<a name=about-this-sample></a>

## About this sample

<!-- Delete the ones that don't apply -->
1. **Applies to:** SQL Server 2016 (or higher), Azure SQL Database
1. **Key features:** PolyBase
1. **Workload:** Analytics
1. **Programming Language:** T-SQL
1. **Authors:** Greg Low, Jos de Bruijn
1. **Update history:** 26 May 2016 - initial revision

<a name=before-you-begin></a>

## Before you begin

To run this sample, you need the following prerequisites.

**Software prerequisites:**

<!-- Examples -->
1. SQL Server 2016 (or higher) with PolyBase, connected to the internet.
2. SQL Server Management Studio
3. The WideWorldImportersDW database (Full version).

<a name=run-this-sample></a>

## Running the sample

1. Execute the sample script.

2. Inspect external tables in the database.

3. Review query results.

## Sample details

The sample script performs a configuration and runs three queries:

1. An external table `dbo.CitePopulationStatistics` is created in the database, pointing to a data set in Azure blob storage.

2. The data in Azure storage is queried through Transact-SQL, showing all the data in the data source.

3. Cities with a significant growth rate (>= 20%) are identified.

4. Top cities for potential expansion are identified based on external data as well as sales data in the local database.

<a name=disclaimers></a>

## Disclaimers
The code included in this sample is not intended to be used for production purposes.

<a name=related-links></a>

## Related Links
<!-- Links to more articles. Remember to delete "en-us" from the link path. -->
For more information, see these articles:
- [Get started with PolyBase](https://msdn.microsoft.com/library/mt163689.aspx)
- [PolyBase: Gaining insights from HDFS and relational data in SQL Server 2016 (video)](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/PolyBase)



# 5. Sample for use of Row-Level Security in WideWorldImporters

This script demonstrates the use of Row-Level Security to restrict access to certains rows in the table to certain users.


### Contents

[About this sample](#about-this-sample)<br/>
[Before you begin](#before-you-begin)<br/>
[Running the sample](#run-this-sample)<br/>
[Sample details](#sample-details)<br/>
[Disclaimers](#disclaimers)<br/>
[Related links](#related-links)<br/>


<a name=about-this-sample></a>

## About this sample

<!-- Delete the ones that don't apply -->
1. **Applies to:** SQL Server 2016 (or higher), Azure SQL Database
1. **Key features:** Row-Level Security
1. **Workload:** OLTP
1. **Programming Language:** T-SQL
1. **Authors:** Greg Low, Jos de Bruijn
1. **Update history:** 26 May 2016 - initial revision

<a name=before-you-begin></a>

## Before you begin

To run this sample, you need the following prerequisites.

**Software prerequisites:**

<!-- Examples -->
1. SQL Server 2016 (or higher) or Azure SQL Database.
 - With SQL Server, make sure SQL authentication is enabled.
2. SQL Server Management Studio
3. The WideWorldImporters database.

<a name=run-this-sample></a>

## Running the sample

1. Open both scripts in different windows or tabs in Management Studio.

2. Follow the instructions in the main script DemonstrateRLS.sql.

## Sample details

The sample enables row-level security in the database, for the table `Sales.Customers`. Users of the database can only see the customers they are allowed to see.

The user 'Great Lakes Sales' is allowed to see only the customers in the Great Lakes sales territory.

The Website user, which is used by the Web front-end in this scenario, configures the sales territory, and RLS takes care of the required filtering based on the information provided by the Web app.

<a name=disclaimers></a>

## Disclaimers
The code included in this sample is not intended to be used for production purposes.

<a name=related-links></a>

## Related Links
<!-- Links to more articles. Remember to delete "en-us" from the link path. -->
For more information, see these articles:
- [Row-Level Security documentation](https://msdn.microsoft.com/library/dn765131.aspx)
- [Row-Level Security SQL Server 2016 (video)](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/Row-Level-Security)
