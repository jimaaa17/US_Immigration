# U.S. Immigration
# ETL Pipeline for Immigration and Temperature Data
### Data Engineering Capstone Project

#### Project Summary
The goal of this project is to create an ETL pipeline using I94 immigration data and city temperature data to form a database that is optimized for queries on immigration events. This database can be used to answer questions relating immigration behavior to destination temperature e.g., do people tend to immigrate to warmer places?

The project follows the follow steps:
* Step 1: Scope the Project and Gather Data
* Step 2: Explore and Assess the Data
* Step 3: Define the Data Model
* Step 4: Run ETL to Model the Data
* Step 5: Complete Project Write Up
#### Scope
In this project, we will aggregate I94 immigration data by destination city to form our first dimension table. Next we will aggregate city temperature data by city to form the second dimension table. The two datasets will be joined on destination city to form the fact table. The final database is optimized to query on immigration events to determine if temperature affects the selection of destination cities. Spark will be used to process the data.
#### Explore the data and Cleaning step

- **I94 Immigration Data**: This data comes from the US National Tourism and Trade Office. A data dictionary is included in the workspace. This is where the data comes from. immigration_data_sample.csv contains the sample data.
- **U.S. City Demographic Data**: This data comes from [OpenSoft](https://public.opendatasoft.com/explore/dataset/us-cities-demographics/export/). This dataset contains information about the demographics of all US cities and census-designated places with a population greater or equal to 65,000. This data comes from the US Census Bureau's 2015 American Community Survey.
- **Airport Code Table**: This data comes from [ourairports](http://ourairports.com/data/airports.csv). It is a simple table of airport codes and corresponding cities. It contains the list of all airport codes, the attributes are identified in datapackage description. Some of the columns contain attributes identifying airport locations, other codes (IATA, local if exist) that are relevant to identification of an airport.

##### Data Dictionary
Name | Description
-----|-------------
I94YR|4 digit year
I94MON|Numeric month
I94CIT|This format shows all the valid and invalid codes for processing
I94RES|This format shows all the valid and invalid codes for processing
I94PORT|This format shows all the valid and invalid codes for processing
ARRDATE|is the Arrival Date in the USA. It is a SAS date numeric field that a permament format has not been applied.  Please apply whichever date format works for you.
I94MODE|There are missing values as well as not reported (9)
I94ADDR|There is lots of invalid codes in this variable and the list below shows what we have found to be valid, everything else goes into 'other'
DEPDATE| is the Departure Date from the USA. It is a SAS date numeric field that  a permament format has not been applied.  Please apply whichever date format works for you.
I94BIR|Age of Respondent in Years
I94VISA|Visa codes collapsed into three categories
COUNT|Used for summary statistics
DTADFILE|Character Date Field - Date added to I-94 Files - CIC does not use
VISAPOST|Department of State where where Visa was issued - CIC does not use
OCCUP|Occupation that will be performed in U.S. - CIC does not use
ENTDEPA|Arrival Flag - admitted or paroled into the U.S. - CIC does not use
ENTDEPD|Departure Flag - Departed, lost I-94 or is deceased - CIC does not use
ENTDEPU|Update Flag - Either apprehended, overstayed, adjusted to perm residence - CIC does not use
MATFLAG|Match flag - Match of arrival and departure records
BIRYEAR|4 digit year of birth
DTADDTO|Character Date Field - Date to which admitted to U.S. (allowed to stay until) - CIC does not use
GENDER|Non-immigrant sex
INSNUM|INS number
AIRLINE|Airline used to arrive in U.S.
ADMNUM|Admission Number
FLTNO|Flight number of Airline used to arrive in U.S.
VISATYPE|Class of admission legally admitting the non-immigrant to temporarily stay in U.S.