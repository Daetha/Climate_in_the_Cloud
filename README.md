
# Data Integration from Deutscher Wetterdienst to AWS
author: Alex Torkhov


# Abstract
The market of climate data is full of measurements but unscalable. Big old institutions supply data with high quality, long history and awesome granularity. However, you won't be able to use it in your application or near-real-time analytics. German Meteorological Service (DWD) has wonderful data, but it is so hard to consume. 
The problem is with manual data retrieval, sophisticated API structure and file-system storage. A solution is going to be a database that would integrate sparse resources under a cloud computing platform. I, therefore, designed an ETL script to enjoy climate data on Amazon Web Services
Which data product to use: SQL or NoSQL? Climate data fits under the idea of a time-series database, so I focus on AWS Timestream as a representative of columnar storage NoSQL. If we compare it with a relational database like MySQL, the performance depends on native functions. 
Timestream has capability to work with sparse data of time-series origin. Operations that work rates of change, interpolation, max_by are quite efficient. Timestream is found to be slower than MySQL on the most basic operations. So, hybrid database can be a valuable addition. 

You are welcome to use and contribute to my last step towards Masters' in Data Science at UE

# Table of Contents

- [Introduction](#introduction)
- [Literature Review](#literature-review)
- [Methodology](#methodology)
- [Architecture](#architecture)
- [Challenges and Solutions](#challenges-and-solutions)
- [Results](#results)
- [Discussion](#discussion)
- [Conclusion](#conclusion)
- [References](#references)
- [Appendices](#appendices)

# Introduction

## Background

From a business standpoint, adding climate data can inform many decisions. The importance of climate indicators does not seem to stop growing. What is more, the project does not limit itself to DWD, but can be used for other countries and data sources. If IoT device follows a similar schema, it can be also connected to AWS using this code. 

## Objectives

the goal of my data integration project is to create a middle layer between legacy file storage and AWS. Transitioning data is important to let data data access technologies. Technologies for BI, databases and automation.
 
## Scope

The scope of my work covers weather sensing data and IoT data that are connectable to the cloud. Either accessible through API or AWS IoT connector. Timestream presumes that data are stored as they are produced, so historical data or long-time series do not fall under the scope. Python is used as a programming language and computational loads as well as database access are configured using python. ![image](https://github.com/Daetha/Climate_in_the_Cloud/assets/72041798/9459a021-d6fa-420d-aa50-042da6109c82)


# Literature Review

Let me highlight the top articles in the research area. In my opinion, these 3 articles will give you the best glimpse into the research field. For simply access I provide doi links, and for academic integrity i attach citations in Harvard style. 

My favorite literature review of NoSQL research is written by Khan, and colleagues in 2023. As a good SRL this one makes you admire how much has been done in the field. And choose yourself an area of focus. Lian, J., McGuire, M.P. and Moore, T.W. (2017) ‘FunnelCloud: a cloud-based system for exploring tornado events’, International Journal of Digital Earth, 10(10), pp. 1030–1054. Available at: https://doi.org/10.1080/17538947.2017.1279235.![image](https://github.com/Daetha/Climate_in_the_Cloud/assets/72041798/0e339fef-b3ac-431e-a606-b2d63fe62656)

Application in form of software regarding very dangerous events is called FunnelCloud. It's a cloud-based system for exploring tornado events. FunnelCloud: a cloud-based system for exploring tornado events. Scientists integrate sparce data into a MongoDB NoSQL database. Scientist can explore spacio-temporal patterns via is connected web interface.

![image](https://github.com/Daetha/Climate_in_the_Cloud/assets/72041798/5bacfcf5-ebff-4ef0-bf89-c1d513476a8e)

A very inspiring example that uses deep learning predicts urban climate in New York city. For me as a data engineer it is especially inteesting how authors augment existing temperature data with IoT data of higher granularity. The resulting model trained on an aggregated dataset outperforms alternatives. 
From AWS standpoint, Sagemaker provides a platform to integrate data and train models like a notebook that can connect to AWS infrastructure and internet.

https://doi.org/10.1080/17538947.2017.1279235![image](https://github.com/Daetha/Climate_in_the_Cloud/assets/72041798/d21aadb2-2a65-44a9-ba44-1155b5f6cad7)


# Methodology

## Data Collection

the question What dimensions of data do we want to access corresponds to the questions What aspects of ETL are we going to modify. A sampling of stations occurs in changing metadata file, that serves as a knowledge layer of ETL pipeline. Selection of measurements occurs when preparing a set of directories. ETL prepare script is capable to automatically parse data of all categories of selected granularity. The default is 1 hour. To modify this behaviour, coder can restructure the target url. 

## Data Transformation

First of all, on dwd data is supplied in zip archives. ISo, the ETL unarchives them, selects sta(https://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/hourly/![image](https://github.com/Daetha/Climate_in_the_Cloud/assets/72041798/19e2aa77-73fc-4bb0-a04a-f8eacfc2cd0a)
)
Then, files for each tipe of measurement -- essentially type of sensors -- be it air temperature, humidity or cloudiness -- are written into respectful folder. At the end we have the same folder structure as in DWD filestorage, but unarchived and without unnecessary metadata. Metadata is stored separately. only txt files from 


## AWS Integration

Detail the steps taken to integrate the data into AWS services.

## Tools and Technologies

List the tools and technologies used in the integration process.

# Architecture

Provide a high-level overview of the architecture you implemented for data integration.

# Challenges and Solutions

Discuss any challenges encountered during the integration process and the solutions you implemented.

# Results

Present the outcomes of your data integration, including any improvements achieved.

# Discussion

Analyze the results in the context of your objectives. Discuss the implications of your findings and any recommendations for future work.

# Conclusion

Summarize the key points and restate the significance of your work.

# References

Cite all the sources, tools, and frameworks you referred to in your documentation.

# Appendices

Include any supplementary materials, code snippets, or additional information that supports your documentation.
