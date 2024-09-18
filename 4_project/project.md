# Project 1: Programming fundamentals for health data__

For this project, you will have to work on a provided dataset and give a description of the informations given in this dataset. You will have to manipulate the dataset and use different kind of Python data types that were presented to you during this class. You will also have to use some Python functions or some function that you implemented yourself.

The dataset is at the address: https://github.com/lrnv/inf-prof/blob/main/4_project/Chicago_Cimes_2008_to_2011.csv

**You have to** use the pandas library but you are free to use other libraries in addition to pandas. If so please indicate clearly which one you are using.


**Context** You will study the Crimes in Chicago dataset. This dataset reflects reported incidents of crime that occurred in the City of Chicago from 2008 to 2011. Data is extracted from the Chicago Police Department's CLEAR (Citizen Law Enforcement Analysis and Reporting) system. In order to protect the privacy of crime victims, addresses are shown at block level only and specific locations are not identified. Disclaimer: These crimes may be based upon preliminary information supplied to the Police Department by reporting parties that have not been verified. The preliminary crime classifications may be changed at a later date based upon additional investigation and there is always the possibility of mechanical or human error.

**Dataset content:** The dataset contains the following variables: 
*   `ID` - Unique identifier for the record.
*   `Case Number` - The Chicago Police Department RD Number (Records Division Number), which is unique to the incident.
*   `Date` - Date when the incident occurred. This is sometimes a best estimate.
*   `Block` - The partially redacted address where the incident occurred, placing it on the same block as the actual address.
*   `IUCR` - The Illinois Uniform Crime Reporting code. This is directly linked to the Primary Type and Description. See the list of IUCR codes at https://data.cityofchicago.org/d/c7ck-438e.
*   `Primary type` - The primary description of the IUCR code.
*   `Description` - The secondary description of the IUCR code, a subcategory of the primary description.
*   `Location Description` - Description of the location where the incident occurred.
*    `Arrest` - Indicates whether an arrest was made.
*    `Domestic` - Indicates whether the incident was domestic-related as defined by the Illinois Domestic Violence Act.
*   `Beat` - Indicates the beat where the incident occurred. A beat is the smallest police geographic area - each beat has a dedicated police beat car. Three to five beats make up a police sector, and three sectors make up a police district. The Chicago Police Department has 22 police districts. See the beats at https://data.cityofchicago.org/d/aerh-rz74.
*   `District` - Indicates the police district where the incident occurred. See the districts at https://data.cityofchicago.org/d/fthy-xz3r.
*   `Ward` - The ward (City Council district) where the incident occurred. See the wards at https://data.cityofchicago.org/d/sp34-6z76.
*   `Community Area` - Indicates the community area where the incident occurred. Chicago has 77 community areas. See the community areas at https://data.cityofchicago.org/d/cauq-8yn6.
*   `FBI Code` - Indicates the crime classification as outlined in the FBI's National Incident-Based Reporting System (NIBRS). See the Chicago Police Department listing of these classifications at http://gis.chicagopolice.org/clearmap_crime_sums/crime_types.html.
*   `X Coordinate` - The x coordinate of the location where the incident occurred in State Plane Illinois East NAD 1983 projection. This location is shifted from the actual location for partial redaction but falls on the same block.
*   `Y Coordinate` - The y coordinate of the location where the incident occurred in State Plane Illinois East NAD 1983 projection. This location is shifted from the actual location for partial redaction but falls on the same block.
*   `Year` - Year the incident occured.
*   `Updated On` - Date and time the record was last updated.
*   `Latitude` - The latitude of the location where the incident occurred. This location is shifted from the actual location for partial redaction but falls on the same block.
*   `Longitude` - The longitude where the incident occurred. This location is shifted from the actual location for partial redaction but falls on the same block.
*   `Location` - The location where the incident occurred in a format that allows for creation of maps and other geographic operations on this data portal. This location is shifted from the actual location for partial redaction but falls on the same block.


**First Part:**

1. Import the dataset and display the first and last 5 lines. Give the type object for each column. Display the number of rows and columns
2. Display if there is any missing value in the dataset. If so display the total number of missing values per column and the proportion of missing value for each column.
3. Some of the rows are duplicated, use the ID column to identify some duplicated rows. How many rows are duplicated in total ? Drop all the duplicated rows and use the ID as an index of the dataset.
4. One of the row was poorly reported in the file and has many mistakes. The ID of the row is a string instead of digits. Find a way to identify this row and delete it from the dataset.
5. Use the `Date` column to create 2 new columns that you will add to the dataset. The first column will be the calendar date of the incident with the following format dd-mm-yyyy (example 3rd of October 2023 will become 03-10-2023). The second column will be the time the incident happened with the following format hh:mm:ss with the hour of the day displayed with the 24h format. (example 5:54:35 will become 17:54:35). Then answer the following questions:
    a. Which hour of the day had the most number of homicides ?
    b. Which day of the week had the lowest number of theft ?
    c. What was the most common crime reported on christmas day (25th December) ?
6. The description of the location can sometimes be too specific. For instance,  with airports, each part of the airport is considered as a distinct location. Use Python commands to detect all the locations (in column Location.Description) that involved Airport and replace all the values by 'AIRPORT' in the DataFrame.
7. We want to compare criminality of all the districts for the year 2008. For that question you will compute the criminality rate of each district. It is computed by dividing the total number of incidents by the total population of the district for the year 2008. You can multiply the results by 100 then to get a number of incidents per 100 habitants. Compute this rate and then present your result by giving a barplot of all the criminality rates computed and use the district name as a label of each bar. _N.B. To help you with this task, this is the population of Chicago Districts reported in the annual report of the Chicago Police Department https://home.chicagopolice.org/wp-content/uploads/2014/12/2008-Annual-Report.pdf_

```python
| District Number || District Name || Population in 2008|
|----------||:-----------:||:-----------|
|District 1||Central||25 613|
|District 2||Wentworth||50 957|
|District 3||Grand Crossing||93 384|
|District 4||South Chicago||141 422|
|District 5||Calumet||92 729|
|District 6||Gresham||105 360|
|District 7||Englewood||91 600|
|District 8||Chicago Lawn||244 470|
|District 9||Deering||165 457|
|District 10||Ogden||137 120|
|District 11||Harrison||82 392|
|District 12||Monroe||69 677|
|District 13||Wood||60 517|
|District 14||Shakespeare||132 459|
|District 15||Austin||72 736|
|District 16||Jefferson Park||199 898|
|District 17||Albany Park||156 859|
|District 18||Near North||110 995|
|District 19||Belmont||107 516|
|District 20||Lincoln||102 512|
|District 21||Pairie||78 111|
|District 22||Morgan Park||111 545|
|District 23||Town Hall||98 391|
|District 24||Rogers Park||151 435|
|District 25||Grand Central||212 535|
|__Total__  || __Population__ || __2 895 700__
```


```python
district = pd.DataFrame({'District_Number':[i for i in range(1, 26)],
                 'District_Name': ['Central', 'Wentworth', 'Grand Crossing', 'South Chicago', 'Calumet', 'Gresham',
                                   'Englewood', 'Chicago Lawn', 'Deering', 'Ogden', 'Harrison', 'Monroe',
                                   'Wood', 'Shakespeare', 'Austin', 'Jefferson Park', 'Albany Park', 'Near North',
                                   'Belmont', 'Lincoln', 'Prairie', 'Morgan Park', 'Town Hall', 'Rogers Park', 'Grand Central'],
                 'Population': [25613, 50957, 93384, 141422, 92729, 105360, 91600, 244470, 165457, 137120, 82392, 69677, 60517, 132459, 72736, 199898, 156859, 110995, 107516, 102512, 78111, 111545, 98391, 151435, 212535]})
district.set_index('District_Name', inplace = True)
```

8. Give for each type of crime reported the proportion of arrests. You can answer this question with a graphic or a table.

**Second Part:**

For the second part of the project, you will have to chose one specific type of crime reported in the dataframe. Give the type of crime that you have selected and use the DataFrame object to generate descriptive information about this specific type of crime, it is up to you to describe what you want to generate and to show the code that you implemented. For instance you can:

* Plot a monthly report of the number of time this crime was committed.
* Give a spatial repartition of where the crime was committed on a specific year.
* Plot on a map each location the crime was reported with a specific color/shape for the arrests.
* Use the `Description` column to add more information about the type of crime you selected.
* Use the `Location.Description` to give insight on where the crime was committed.

Choose at least 3 information to display (not necesseraly from the above list).