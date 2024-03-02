
---
title: "Data Integration from Deutscher Wetterdienst to AWS"
author: "Alex Torkhov"
date: "Date"
output:
  pdf_document: default
  html_document:
    theme: cosmo
---

# Abstract
The market of climate data is full of measurements but unscalable. Big old institutions supply data with high quality, long history and awesome granularity. However, you won't be able to use it in your application or near-real-time analytics. German Meteorological Service (DWD) has wonderful data, but it is so hard to consume. 
The problem is with manual data retrieval, sophisticated API structure and file-system storage. A solution is going to be a database that would integrate sparse resources under a cloud computing platform. I, therefore, designed an ETL script to enjoy climate data on Amazon Web Services
Which data product to use: SQL of NoSQL? Climate data fits under the idea of a time-series database, so I focus on AWS Timestream as a representative of columnar storage NoSQL. If we compare it with a relational database like MySQL, the performance depends on native functions. 
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

Clearly state the goals of your data integration project.

## Scope

Define the scope and limitations of your work.

# Literature Review

Survey existing literature related to data integration, AWS, and meteorological data.

# Methodology

## Data Collection

Explain how you collected data from the Deutscher Wetterdienst.

## Data Transformation

Describe the process of transforming the data for compatibility with AWS.

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
