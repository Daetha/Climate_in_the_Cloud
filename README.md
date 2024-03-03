
# 🌦️ **Climate in the Cloud: Seamless Data Integration from Deutscher Wetterdienst to AWS** 🚀
*Author: Alex Torkhov*


# Abstract

In a climate data market saturated with measurements but lacking scalability, the German Meteorological Service (DWD) stands as a heavyweight with high-quality, historical, and finely-granulated data. However, accessing this wealth of information for applications or near-real-time analytics poses a formidable challenge due to manual retrieval, complex APIs, and file-system storage. The solution? A database harmonizing diverse resources under the expansive umbrella of a cloud computing platform. I present an ETL script that breathes life into climate data on Amazon Web Services (AWS).

**Choice of Data Product:** The dilemma between SQL and NoSQL unravels as climate data aligns seamlessly with the time-series database concept. AWS Timestream emerges as the representative NoSQL solution, offering columnar storage prowess. A hybrid database approach, combining Timestream with MySQL, is explored for optimal performance.

*Welcome to explore and contribute to my final stride towards a Masters' in Data Science at UE.*

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
Detailing the steps taken to seamlessly integrate data into AWS services.

## Tools and Technologies
List of tools and technologies employed in the integration process.

# Architecture
A high-level overview of the implemented architecture for data integration.

# Challenges and Solutions
Navigate through encountered challenges and innovative solutions implemented during the integration process.

# Results
Unveiling the outcomes of the data integration, showcasing any enhancements achieved.

# Discussion
Analyzing results within the context of project objectives, discussing implications, and presenting recommendations for future endeavors.

# Conclusion
A succinct summary, reiterating the significance of the work undertaken.

# References
Citations and references to sources, tools, and frameworks referred to in this documentation.

# Appendices
Supplementary materials, code snippets, and additional information to support and enrich the documentation.
