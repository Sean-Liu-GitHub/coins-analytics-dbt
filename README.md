# <img width="50" alt="image" src="https://www.getdbt.com/ui/img/logos/dbt-logo.svg"> dbt project - Crypto Currencies Analysis part2: Data Transformation
In my previous[ GCP Data Engineering Project - Crypto Currencies Analysis part1: Data Ingestion with Cloud Composer built on Apache Airflow](https://github.com/Sean-Liu-GitHub/crypto-analytics-workflow) project, I describe how to ingest crypto currency data from [CoinCap API](https://docs.coincap.io/) to Google Cloud Storage and to BigQuery.
However, the staging data in BigQuery needs to be transformed so we can use it for reporting purpose. This is where dbt comes to help.

## What is dbt?
According to https://www.getdbt.com/product/what-is-dbt,
"dbt™ is a SQL-first transformation workflow that lets teams quickly and collaboratively deploy analytics code following software engineering best practices like modularity, portability, CI/CD, and documentation. Now anyone on the data team can safely contribute to production-grade data pipelines."
For me, dbt is a good tool to organize my SQL codes. It makes the best practices in software engineering accessible to data analytics world.
It is giving data analysts the ability to contribute versioned, tested, documented code to production data warehouses.

## dbt Core v.s. dbt cloud
* dbt Core
A set of open source Python packages, running in the command line, that helps you transform, document, and test your data.
* dbt Cloud 
A web based UI that allows you to both develop and deploy data pipelines (built on top of dbt Core)

With dbt Core, it is free but you need a server to run dbt build, for example, you can run build in airflow.
With dbt Cloud, it provides version control, deploy, CI/CD and scheduling so you can focus on develop your SQL codes. One thing needs to be mentioned that it is not free.

## Details about dbt Cloud
In this project, I use dbt Cloud to help me save time and energy. I will describe some features of dbt Cloud in below.

#### Cloud IDE
![image](https://hackmd.io/_uploads/rJKnFplYA.png)
I really like the cloud IDE because I can seamlessly write SQL codes and test it in testing environment. After the testing completed, I can push new commits to the feature branch on GitHub(or other version control system) via the IDE and create a PR in GitHub so other developers can review it.

#### Dashboard
![image](https://hackmd.io/_uploads/S1Xfi6xK0.png)
It simply shows the recent activities and deployment environments of this project.

#### Deploy Jobs
![image](https://hackmd.io/_uploads/BJBqsTgY0.png)
It shows all the scheduled or manual jobs of this project. You can create a new job via clicking the button.

#### Explore
![image](https://hackmd.io/_uploads/Byq-TaxFA.png)
This page provides an overview of the current selected project including models, sources and tests...etc.


## Models
The cloud IDE also provides a lineage view to help developers quickly find out the relationships among sources and models.
In this project, the only source is the **coins_data_raw** table in BigQuery. The staging table **stg_coinsdata** is a bridge between the source and the core models. There are two core models dim_coins and facts_coins which are referenced by the report in Looker Studio.
![image](https://hackmd.io/_uploads/HkM66axKR.png)


## The report
[Looker report link
](https://lookerstudio.google.com/s/rOIkZtuIGys)
This is a screenshot of the report. Please note that this report is only for testing purpose and do not use it for making any investment decisions.
![image](https://hackmd.io/_uploads/HJCbeAgKA.png)
