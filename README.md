<H1> COVID-19 Data Engineering Project Using Azure Cloud</H1>
The COVID-19 pandemic has underscored the criticality of effective data management and analysis in public health crises. Amidst the deluge of information, creating a robust data pipeline is essential to derive insights crucial for decision-making. 
This personal project embarks on constructing a comprehensive data pipeline within the Azure Cloud environment, utilizing Azure Data Factory, Azure Databricks, and Azure Synapse Analytics, to process and analyze various COVID-19 datasets sourced from AWS S3. 
The AWS data lake team penned a blog that explains that they are making COVID-19 data freely available to anyone. 
<a href = "https://aws.amazon.com/blogs/big-data/a-public-data-lake-for-analysis-of-covid-19-data">AWS Data Lake Blog</a> 

<h3>Project Scope:</h3>

The project revolves around harnessing COVID-19-related datasets housed in an AWS S3 bucket. By integrating Azure's powerful data engineering services, namely Data Factory for orchestration, Databricks for data transformation and processing, and Synapse Analytics for analytics and reporting, the goal is to build an end-to-end data pipeline that enables seamless extraction, transformation, and analysis of this critical information.

<h3>Dataset Overview:</h3>

The project centers on ten datasets hosted in AWS S3: 

1. John's Hopkins provided COVID-19 testing dataset showing insights into testing results, and mortality information per location
2. COVID-19 Tracking Project provided testing for all of US
3. COVID-19 Tracking Project provided testing per state in US
4. COVID-19 Tracking Project provided total testing for all US
5. NY Times Testing and hospitalization separated by state
6. NY Times Testing and hospitalization for all of US
7. Definitive Healthcare provided Hospital Bed Utilization in the US
8. Lookup table for State Abbreviations and names
9. Lookup table for county population
10. Lookup table for country codes

<h3>Data Engineering Architecture:</h3>

![data_flow](https://github.com/toddmaisano/covid-19-data-engineering-project/assets/75994948/a2281eab-01b6-4879-975d-5bd10832e2e1)

<h3>DATA MODEL:</h3>

<u>Ingested schema:</u>
![COVID19_Project drawio (4)](https://github.com/toddmaisano/covid-19-data-engineering-project/assets/75994948/1db46c53-8f96-4b80-9781-e0f20815cb8b)

<u>Star Schema Model:</u>

Dimension Tables:
`dimRegion`
`dimHospital`
`dimDate`

Fact Tables:
`fact_covid`

![Model_Covid drawio (1)](https://github.com/toddmaisano/covid-19-data-engineering-project/assets/75994948/5fd93432-dbdf-44a2-bab7-48ef525be662)


<h2>Key Objectives:</h2>

<h3>Data Ingestion: </h3>
Establishing a reliable mechanism using Azure Data Factory to ingest the COVID-19 datasets from AWS S3 into the Azure Data Lake Storage (ADLS) Gen 2 storage. There was no access points to directly push the data from the S3 bucket to Data Factory, so the CSV files were uploaded to Github and pulled into Data Factory via the HTTP link.

<h3>Data Transformation:</h3>
Leveraging Databricks to preprocess, cleanse, and structure the datasets for analytical purposes, ensuring data quality and consistency and storing resulting tables on ADLS Gen 2 storage. Data cleaning always consists of many points. What do you do with null values, how do you handle data types? Here, the null values for the 'fips' columns were removed directly. Other columns may have imputed values, such as median, or mean.

<h3>Data Storage and Integration</h3>
The resulting Fact and Dimension tables were stored back into ADLS Gen 2 and using Azure Synapse Analytics, it enables high-performance analytics, visualization, and reporting. The tables can then be utilized in an external visualization software such as PowerBi.

<h3>Expected Impact:</h3>
This project seeks to showcase the effectiveness of Azure's data engineering services in handling real-world datasets critical to public health. By constructing a streamlined pipeline, the aim is to facilitate efficient data processing, comprehensive analysis, and visualization, ultimately empowering stakeholders with actionable insights to better understand and respond to the COVID-19 crisis.

