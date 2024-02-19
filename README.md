# SolarPower-SQL-Portfolio-Project
The SolarPower SQL Portfolio Project delves into the fusion of generation and weather sensor data from two distinct power plants, presenting a comprehensive analysis framework for insights and informed decision-making.

# SolarPower SQL Portfolio Project
# Table of Contents

1. [Introduction](#introduction)
2. [Project Objectives](#project-objectives)
    - [Data Acquisition and Preparation](#data-acquisition-and-preparation)
    - [Data Integration and Table Creation](#data-integration-and-table-creation)
    - [Data Analysis](#data-analysis)
    - [Analysis and Insights](#analysis-and-insights)
3. [Project Execution](#project-execution)
    - [Data Acquisition and Preparation](#data-acquisition-and-preparation-1)
    - [Data Integration and Table Creation](#data-integration-and-table-creation-1)
    - [Data Analysis](#data-analysis-1)
4. [Recommendation](#recommendation)
5. [Limitations](#limitations)
6. [Conclusion](#conclusion)


## Introduction:

In the realm of renewable energy, effective data management and analysis play a pivotal role in optimizing performance and enhancing efficiency. The SolarPower SQL Portfolio Project delves into the fusion of generation and weather sensor data from two distinct power plants, presenting a comprehensive analysis framework for insights and informed decision-making.

## Project Objectives:

1. **Data Acquisition and Preparation:**
   - I retrieved datasets from Kaggle, comprising "Generation Data" and "Weather Sensor Data" for two power plants.
   - I created a new dataset named "SolarPower" within BigQuery for storage and analysis.
   - I uploaded and organized datasets into individual tables within the SolarPower dataset.

2. **Data Integration and Table Creation:**
   - I constructed queries to merge generation and weather sensor datasets for Plant 1 and Plant 2.
   - I created two distinct tables, "Generation_Data" and "Weather_Sensor_Data," using the results of the UNION operation.
   - I established a unified and structured data representation within the SolarPower dataset.

3. **Data Analysis:**
   - I determined the count of inverters (source_key) present in each plant to assess equipment distribution and capacity.
   - I calculated the duration of observations for each plant, providing insights into data coverage and monitoring periods.
   - I identified the inverter associated with the highest total yield, considering aggregation functions and dataset descriptions for accuracy.

4. **Analysis and Insights:**
   - I determined the count of inverters (source_key) present in each plant to assess equipment distribution and capacity. Each plant has 22 inverters.
   - I calculated the duration of observations for each plant, providing insights into data coverage and monitoring periods. We have 34 days of data.
   - I identified the inverter associated with the highest total yield, considering appropriate aggregation functions and dataset descriptions for accurate analysis. Plant ID 4136001 generates more yields in 17 inverters than Plant ID 4135001.

## Project Execution:

1. **Data Acquisition and Preparation:**
   - I accessed the Kaggle page hosting the designated datasets for the two power plants.
   - I downloaded the CSV files encompassing "Generation Data" and "Weather Sensor Data" for comprehensive analysis.
   - I unzipped the downloaded folder to access individual CSV files containing pertinent data.

2. **Data Integration and Table Creation:**
   - I navigated to BigQuery and established a new dataset named "SolarPower" for centralized data management.
   - I uploaded the four CSV files into distinct tables within the SolarPower dataset, naming each table correspondingly to the file it represents.
   - I utilized SQL queries to combine generation and weather sensor datasets for Plant 1 and Plant 2.
   - I executed the UNION operation to merge datasets and create two distinct tables: "Generation_Data" and "Weather_Sensor_Data."

3. **Data Analysis:**
   - Including some interesting code/features worked with
   - How many inverters are there in each plant?
     ```SQL
     SELECT plant_id, count(distinct source_key) as nr_inverters
     FROM SolarPower.Generation_Data
     GROUP BY plant_id;

   - How many days of observations do we have for each plant?
     ```SQL
     SELECT plant_id, count(distinct extract(date from date_time)) as nr_days
     FROM SolarPower.Generation_Data
     GROUP BY plant_id;
   - Which inverter generated the highest total yield? Which plant does it belong to?
     ```SQL
     SELECT plant_id, source_key, max(total_yield) as total_yield
     FROM SolarPower.Generation_Data
     GROUP BY plant_id, source_key
     ORDER BY total_yield desc;


## Recommendation:

Based on the analysis conducted, it is recommended to further investigate the factors contributing to the variations in yield between Plant ID 4136001 and Plant ID 4135001. Understanding the underlying factors driving these differences can inform targeted strategies for optimizing performance and maximizing yield across both plants. Further investigation should explore factors such as maintenance and cleaning schedules, geographical location, and environmental conditions to determine potential sources of suboptimal performance within each plant.


## Limitations:

The dataset comprises only 34 days of observations, which may limit the depth and breadth of analysis, especially when assessing long-term trends or seasonality effects. Additionally, the dataset may not capture all relevant variables that could influence power generation and weather patterns, potentially constraining the scope of insights derived from the analysis.



## Conclusion:

My SolarPower SQL Portfolio Project embodies a comprehensive endeavor to amalgamate and analyze data from multiple sources, enabling stakeholders to derive meaningful insights and optimize operational efficiencies within the renewable energy domain. Through meticulous data management, integration, and analysis, this project exemplifies my ability to drive informed decision-making and performance enhancement within the renewable energy sector.

