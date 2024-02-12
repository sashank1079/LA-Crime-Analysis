# LA-Crime-Analysis
Create a data-driven overview of Los Angeles crimes, emphasizing dashboard building, data profiling, staging pipelines, and safety insights for residents and visitors.

# Talend Workflow

![talend workflow](https://github.com/sashank1079/LA-Crime-Analysis/assets/122720872/c24a26eb-a8c7-4bac-a1c7-81c47bbce7f2)

# Data Observations

Alteryx Workflow

![image](https://github.com/sashank1079/LA-Crime-Analysis/assets/122720872/0b4e264f-7c21-42f5-a5d4-28c80cf0844a)


Observations made in data provided:

1.	DR_NO:
Division of Records Number: Official file number made up of a 2-digit year, area ID, and 5 digits. It has been observed that there are some discrepancies in the data. There are some Dr_No values which have only 4 digits as opposed to the standard 9-digit format. 
The data is from 2020 to present day, therefore the first 2 digits can only be 20, 21, 22 or 23. However, there are some values which have values apart from what’s mentioned.

![image](https://github.com/sashank1079/LA-Crime-Analysis/assets/122720872/ce0cfbd2-6aa2-4813-85c9-22cc40c22c5a)

 
3.	Vict_Age
Vict_Age is a 2 digit numeric ranging from 0 to 99. It is logical to assume that age cannot be negative. However, in the data, there are values present which are negative. 
 
![image](https://github.com/sashank1079/LA-Crime-Analysis/assets/122720872/49220105-7999-4c64-9a0b-8d23ebe15925)


4.	Vict_Sex	
F - Female M - Male X – Unknown
These are the accepted values in this column. However, there is another value which is present, “H”. This should be eliminated.

![image](https://github.com/sashank1079/LA-Crime-Analysis/assets/122720872/7af88f0a-cea9-4420-912a-8e4e1fabb791)

  
6.	LAT and LON
The values of latitude and Longitude seem to be ranging from 33 to 35 for LAT and -118 for LON. (Ignoring decimal points

![image](https://github.com/sashank1079/LA-Crime-Analysis/assets/122720872/35d8966c-526a-488d-9a44-df5a0e1413c1)
![image](https://github.com/sashank1079/LA-Crime-Analysis/assets/122720872/941f5dc3-6a54-4af7-aa73-497518865066)

  
7.	Null values:
There are null values present throughout the dataset. To prevent data ambiguity and to prevent issues in the future, these null values should be eliminated by replaces these with blank strings.
Here are the changes suggested to the data:
1.	Replace all null string values with blank and null numeric values in the database:
For all string columns, if a value is null, replace it with an empty string ("").
For all numeric columns, if a value is null, replace it with 0.
2.	Ensure that the "victim sex" column does not include the value "H" and that the "victim age" is not null:
•	Check the "victim sex" column for the value "H" and replace it with an empty string ("") if found.
•	Ensure that the "victim age" is not null; if it is null, replace it with an empty string ("").
3.	Ensure that the "victim age" is within a valid range:
•	Make sure that the "victim age" is greater than or equal to 0.
•	Make sure that the "victim age" is less than or equal to 99.
4.	Ensure that the "DR_NO" column has a length of 9 digits and that every "DR_NO" starts with the digit 2:
•	Check the "DR_NO" column for each record:
•	If the length is not 9 digits, take appropriate action (e.g., replace with an empty string or discard the record).
•	If the "DR_NO" does not start with the digit 2, take appropriate action (e.g., replace with an empty string or discard the record).
5.	Ensure that the "LAT" and "LON" columns do not have values of 0:
•	Check the "LAT" and "LON" columns for each record:
•	If either "LAT" or "LON" is equal to 0, take appropriate action (e.g., replace with an empty string or discard the record).

These data changes can be implemented using the necessary logic and conditions in your data processing or ETL (Extract, Transform, Load) tool, such as Talend, by applying these rules to the  dataset during transformation or data cleansing processes, A sample is given below:
![image](https://github.com/sashank1079/LA-Crime-Analysis/assets/122720872/0c5d90b0-9983-455e-80a3-b6c9be53530a)

Here, the data is cleansed and all the filters are applied, after which it is sorted in ascending order. 



