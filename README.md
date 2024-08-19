# Data Engineer TASK
PEI Group

## Prerequisite:
### Databricks
* Databricks Community Edition.
* crealytics package to read excel files.
* Store input files for in DBFS.

### Install Spark excel reading packge:
1. To read data from excel into a Pyspark dataframe
2. Go to the Cluster configurations
3. Select libraries then Install new and select Maven
4. Enter "com.crealytics:spark-excel_2.12:3.3.2_0.19.0" in the Coordinate field and click Install
5. above dependency is for spark 3.3 and Make sure to install compatible package for other spark versions 


## Project Flow:
1. Import packages
2. Read Order data from json 
    * Format price column: remove invalid characters 
    * DataType Casting and schema validation
3. Read Customer data from xlsx
    * Format customer name: Remove invalid characters and extra whitespaces
    * Format phone number: Extract numbers only, remove leading country code 001
    * DataType Casting and schema validation
5. Read Product data from csv
    * Verify state: Check if US state information is correct
    * DataType Casting and schema validation
7. Save order, customer, product dataframes into delta table
8. Create enriched tables for each use case as per the requirement
9. Run SQL queries on the saved delta tables with Spark SQL commands


## Observations:
1. Duplicate data 
    * No duplicates in customer table
    * Identified duplicate records in order and product tables and it create ambiguity to fetch product information based on ID column.
2. When data grows we need to think of optimizations like partitions, resolve skew data issues, Optimal join stretagey (brodcast, bucketing),using delta features to store data optimally.


==


# Data Engineer Task
PEI Group

## Prerequisite:
### Databricks
* Databricks Community Edition.
* Crealytics package to read Excel files.
* Store input files in DBFS.

### Install Spark Excel Reading Package:
1. To read data from Excel into a PySpark dataframe.
2. Go to the Cluster configurations.
3. Select libraries, then Install New and select Maven.
4. Enter "com.crealytics:spark-excel_2.12:3.3.2_0.19.0" in the Coordinate field and click Install.
5. The above dependency is for Spark 3.3. Make sure to install a compatible package for other Spark versions.

## Project Flow:
1. Import packages.
2. Read Order data from JSON.
    * Format price column: remove invalid characters.
    * Data type casting and schema validation.
3. Read Customer data from XLSX.
    * Format customer name: Remove invalid characters and extra whitespaces.
    * Format phone number: Extract numbers only, remove leading country code 001.
    * Data type casting and schema validation.
4. Read Product data from CSV.
    * Verify state: Check if US state information is correct.
    * Data type casting and schema validation.
5. Save order, customer, product dataframes into delta tables.
6. Create enriched tables for each use case as per the requirement.
7. Run SQL queries on the saved delta tables with Spark SQL commands.

## Observations:
1. Duplicate data.
    * No duplicates in the customer table.
    * Identified duplicate records in order and product tables which create ambiguity in fetching product information based on the ID column.
2. When data grows, we need to think of optimizations like partitions, resolving skew data issues, optimal join strategy (broadcast, bucketing), and using delta optimization features to store data optimally.
3. Input files has PII data and need to handle it properly using data governance rules.
4. More inputs towards business requirements will help to add more test cases.
