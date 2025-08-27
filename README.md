# Snowflake-MiniProject-1
SCD1 Using Snowflake Stream and Task
Project Overview
In this mini project, :

**Learned how we can ingest the data from an internal stage to a table in snowflake

Capture incremental data using stream

Perform SCD1 logic using snowflake Task automatically**

Objectives
L**earn how to work with Snowflake's internal stages for file storage.

Use the COPY INTO to load structured data into the Snowflake table .

Setup snowflake stream to capture the incremental data

Create snowflake task to automate the SCD1 logic using merge statement
**
Tools/Technologies Used
Snowflake: Cloud-based data warehouse

Snowflake Web UI: SQL execution environment

 

High Level Step-by-Step Implementation
Create a Database & Schema

Database : PRODUCT_DB

Schema : PRODUCT_DATA

Create PRODUCT_SRC Table in the PRODUCT_DATA schema

Table : 

Database: PRODUCT_DB

Schema: PRODUCT_DATA

Name: PRODUCT_SRC

Table structure

PRODUCTID STRING

PRODUCTNAME STRING

CATEGORY STRING

PRICE FLOAT

STOCKQUANTITY FLOAT

SUPPLIER STRING

RATING FLOAT

 

Create the PRODUCT_TGT table within the PRODUCT_DATA schema.

Table : 

Database: PRODUCT_DB

Schema: PRODUCT_DATA

Name: PRODUCT_TGT

Table structure

PRODUCTID STRING

PRODUCTNAME STRING

CATEGORY STRING

PRICE FLOAT

STOCKQUANTITY FLOAT

SUPPLIER STRING

RATING FLOAT

 

Create a stream named PRODUCT_STREAM on the PRODUCT_SRC table to track incremental changes in the data

Stream: 

Database: PRODUCT_DB

Schema: PRODUCT_DATA

Name: PRODUCT_STREAM 

 

Create a task named PRODUCT_TASK that runs a MERGE statement every 1 minute to implement Slowly Changing Dimension Type 1 (SCD1) logic. 

Task: 

Database: PRODUCT_DB

Schema: PRODUCT_DATA

Name: PRODUCT_TASK 

Merge Logic:

Primary Key:  PRODUCTID

Source Table: PRODUCT_DB.PRODUCT_DATA.PRODUCT_STREAM

Target Table: PRODUCT_DB.PRODUCT_DATA.PRODUCT_TGT 

 

Create an Internal Stage

Create an Internal Stage in the PRODUCT_DATA schema

Database: PRODUCT_DB  

Schema: PRODUCT_DATA

Name: PRODUCT_STAGE

 

Upload the product_fulldata.csv file to the Internal Stage

Upload the product_fulldata.csv data file in the internal stage PRODUCT_STAGE

List the file in the internal stage

 

Load product_fulldata.csv Data from the Stage into the PRODUCT_SRC Table

To load the product_fulldata.csv  into the PRODUCT_SRC table, use the COPY INTO command

 

Verify that the product_fulldata.csv file is automatically loaded into the PRODUCT_TGT table using the configured stream and task after 1 min

Upload the product_changedata.csv file to the Internal Stage

Upload the product_changedata.csv data file in the internal stage PRODUCT_STAGE

List the file in the internal stage

 

Load product_changedata.csv Data from the Stage into the PRODUCT_SRC Table

To load the product_changedata.csv  into the PRODUCT_SRC table, use the COPY INTO command

 

Confirm that the product_changedata.csv file is automatically loaded into the PRODUCT_TGT table using the configured stream and task, and verify the implementation of SCD1 logic after 1 min

