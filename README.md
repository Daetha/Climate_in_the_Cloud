
# 🌦️ **Climate in the Cloud: Seamless Data Integration from Deutscher Wetterdienst to AWS** 🚀
*Author: Alex Torkhov*


# Abstract

   In a climate data market saturated with measurements but lacking scalability, the German Meteorological Service (DWD) stands as a heavyweight with high-quality, historical, and finely-granulated data. However, accessing this wealth of information for applications or near-real-time analytics poses a formidable challenge due to manual retrieval, complex APIs, and file-system storage. The solution? A database harmonizing diverse resources under the expansive umbrella of a cloud computing platform. I present an ETL script that breathes life into climate data on Amazon Web Services (AWS).
   The market size of cloud computing is predicted to reach 680 Billion U$D in 2024 according to Gartner at Statista, 2023. The size shows exponential growth since 2014. In such conditions climate data needs to follow the market and settle in a cloud. AWS is chosen as a representative platform. 
   I acknowledge the help and guidance given by my scientific supervisor, Dr. Prof. Iftikhar Ahmed. And format understanding generously provided by Dr. Prof. Talha Alik Khan. A wonderfoul course taught by Claudia Wittman helped me write clearly. I transitioned knowledge from learning German into writing a scientific text. Thanks to my teachers and staff personal at UE University (University of Europe for Applied Science).

**Choice of Data Product:** The dilemma between SQL and NoSQL unravels as climate data aligns seamlessly with the time-series database concept.    AWS Timestream emerges as the representative NoSQL solution, offering columnar storage prowess. A hybrid database approach, combining Timestream with MySQL, is explored for optimal performance.

*Welcome to explore and contribute to my final stride towards a Masters' in Data Science at UE.*

# Table of Contents
- [Introduction](#introduction)
- [Literature Review](#literature-review)
- [Methodology](#methodology)
- [Architecture](#architecture)
- [Challenges and Solutions](#challenges-and-solutions)
- [Results](#results)
- [Discussion](#discussion)

# Introduction

## Background
From a business perspective, integrating climate data can be a game-changer, informing a myriad of decisions. This project's scope extends beyond DWD, envisioning applicability to other countries and data sources. Whether it's weather sensing data or IoT data connectable to the cloud, this project serves as a bridge, leveraging Python for configuration and connectivity.

![Climate in the Cloud](https://github.com/Daetha/Climate_in_the_Cloud/assets/72041798/9459a021-d6fa-420d-aa50-042da6109c82)

## Objectives
The goal is clear: forge a middle layer between legacy file storage and AWS, facilitating seamless data access for BI, databases, and automation technologies.

## Scope
Encompassing weather sensing and IoT data connectable to the cloud, the project is a gateway to AWS, accessible through APIs or the AWS IoT connector. Python orchestrates the computational loads and database access.

# Literature Review
Embark on a journey through the top articles in the field:

1. **Khan et al., 2023:** A comprehensive review of NoSQL research, guiding readers to choose their area of focus.
   [Read More](https://doi.org/10.1080/17538947.2017.1279235)
   ![Image1](https://github.com/Daetha/Climate_in_the_Cloud/assets/72041798/0e339fef-b3ac-431e-a606-b2d63fe62656)

2. **FunnelCloud: A Cloud-Based System for Exploring Tornado Events:** Scientists integrate sparse data into a MongoDB NoSQL database, exploring spacio-temporal patterns through a connected web interface.
   ![Image2](https://github.com/Daetha/Climate_in_the_Cloud/assets/72041798/5bacfcf5-ebff-4ef0-bf89-c1d513476a8e)

3. **Urban Climate Prediction with Deep Learning:** Augmenting temperature data with IoT data of higher granularity, this study predicts urban climate in New York City using deep learning, showcasing the power of AWS Sagemaker.
   [Read More](https://doi.org/10.1080/17538947.2017.1279235)
   ![Image3](https://github.com/Daetha/Climate_in_the_Cloud/assets/72041798/d21aadb2-2a65-44a9-ba44-1155b5f6cad7)

# Methodology

## Data Collection
Answering the question of what dimensions of data to access translates to modifying ETL aspects. A sampling of stations occurs by changing the metadata file, serving as the knowledge layer of the ETL pipeline. A sampling of measurements occurs in the call of function. While granularity selection is selected in a url. 

## Data Transformation
DWD data, supplied in zip archives, undergoes unarchiving and station selection. Files for each type of measurement are categorized into respective folders, resulting in a structured hierarchy mirroring DWD file storage. Metadata is stored separately.

![DWD Data](https://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/hourly/![image](https://github.com/Daetha/Climate_in_the_Cloud/assets/72041798/19e2aa77-73fc-4bb0-a04a-f8eacfc2cd0a))

## AWS Integration
If you are familiar with Jupyter notebooks, you can seamlessly start writing code in AWS Sagemaker. 
After setting up databases, I achieved a hybrid database format. 

## Tools and Technologies

Overall, in the project I used:
1. Sagemaker
2. Timestream
3. RDS
4. S3
5. Lambda

Timestream is the least popular technology in the stack. Let me briefly describe it:
   Timestream treats metadata and data differently. In the present weather sensor application, sensor information is called dimension (longitude, latitude, station name). While the actual weather observations are called measures (humidity, temperature). A quintessential part of any record is the timestamp. AWS Timestream promises to speed up data selection based on timestamp while preserving data control from SQL: filtering on dimensions (e.g. WHERE location = Potsdam') and aggregating measures (e.g. SELECT MIN (temperature)). 
   AWS Timestream is a good example of a NoSQL cloud database. It’s a column storage database tailored for time-series analysis. It supports SQL but joins between tables are not allowed. Schema flexibility means that the same dimension might receive measures of different types. Partitioning is done based on one of dimensions. Data modelling can reflect data usage patterns by allocating data that are frequently retrieved together into a same partition.
   Cloud availability gives Timestream more features. Among them Timestream utilizes Data lifecycle management: In-memory and Magnetic storage. The architecture is analogous to short- and long-term memory, so the database writes a record first in memory and later keeps the record magnetic. User sets retention rules, so a record can travel from in-memory storage to magnetic and be deleted automatically when time passes. Cloud environment enables Timestream encryption in-transit and at-rest. Data safety comes in handy when integrating open-source databases with internal company data. Finally, cloud infrastructure enables customized interaction between client organization and climate service provider. Data stored in cloud database can be used for multiple purposes in outsourced projects. 


# Architecture


# Challenges and Solutions

In short, DWD data is a big challenge. My ambition is to make it more accessible.

- **Challenge - Data Accessibility**: The data from the German Meteorological Service (DWD) was difficult to access due to manual retrieval, complex APIs, and file-system storage.
    - **Solution - Automated Data Retrieval**: Scripts have been written in Python to automate the process of data retrieval from DWD. This includes fetching data from different subfolders and handling different types of measurements.
- **Challenge - Data Integration**: Integrating diverse climate data sources into a unified, easily accessible format was a challenge.
    - **Solution - Data Integration**: Python has been used to create a middle layer between the legacy file storage and AWS, facilitating seamless data access for BI, databases, and automation technologies.
- **Challenge - Data Transformation**: The raw data from DWD came in zip archives and needed to be unarchived, categorized, and stored in a structured hierarchy.
    - **Solution - Data Transformation**: An ETL pipeline has been implemented to transform the raw data into a structured format. This includes unarchiving the data, selecting stations, categorizing files into respective folders, and storing metadata separately.
# Results
Novelties:
- **Cloud-Based Climate Data**: The climate data has been moved to AWS, making it more accessible and scalable. This aligns with the growing trend of cloud computing.
- **Hybrid Database Approach**: A hybrid database approach has been explored, combining AWS Timestream (a NoSQL solution) with MySQL for optimal performance.
- **Data Sampling**: A method has been introduced to sample stations and measurements by modifying the metadata file and function calls.
- **Granularity Selection**: A feature has been provided to select granularity in a URL, allowing for more precise data retrieval.

Now the user (you and I) are in control of database. Not vice versa. Control which data you want to ETL and then query it. For NA-immune retrieval, interpolation and derivatives use Timestream, for more general purpose - MySQL

# Discussion

Next up we'll automate data assimilation and introduce ML on top of database!
