# EVENT BASED ETL WITH AWS LAMBDA CONTAINER IMAGE
Data2bots Technical assessment


#### Table of contents 

   - [Table of contents](#table-of-contents)
  - [overview](#overview)
    - [Functional requirements of the data pipeline](#functional-requirements-of-the-data-pipeline)
  - [Why containerized lambda?](#why-containerized-lambda?)
  - [Components and Pricing](#Components-and-Pricing)


## Overview
[Back to top](#table-of-contents)

<p align='center'>
     <img src="figs/architecture.png"
     alt='Figure 1: Completed data pipeline'
     width=1000px/>
     <br>
     <em>Figure 1: A representation of the completed pipeline.</em>
</p>

Raw data, given in the form of orders, reviews, and shipments `csv` snapshots gathered by my client. requires to be moved to the data warehouse and analyzed. As an initial effort in this movement of data, ABC company has homed in on the transactional data of thousands of records over the past seven years and requires them to be migrated and analyzed to the cloud in an automated manner.  

With the above requirements, my role as the sole data engineer is to create a robust data pipeline that can extract, transform, and load the `csv` datasets from the source data system to a SQL-based database, saving a back up of the analytics details as CSV in a data lake.

### Functional requirements of the data pipeline
[Back to top](#table-of-contents)

The formed data pipeline exhibits the following functionality: 

 - **Pipeline input:** The pipeline is capable of *ingesting and processing 3 `csv` files* per workflow run.
 - **Pipeline output:** The raw data is *stored within a PostgreSQL staging DB schema * and the resulting processed data in a postgreSQL analytics DB schema.   
 - **Monitoring:** The pipeline provides an *email-based success or failure notification* following an attempted run.  
 - **Automation:** The pipeline is *event-driven*, triggering based on a specific time. The pipeline will not be invoked more than once per day. 


## Why containerized lambda?
[Back to top](#table-of-contents)

The decision of my ETL pipeline components and processes are based these major considerations:
- ABC company would be recieving data from transactional activities on daily basis. The flux of these activities cannot be forecasted by an exact number of, for example: expected orders in a day/week/month, hence the project has to be considered as a memory intensive workload.
- Since ABC is an E-commerce company, it is expected that reports on the activities are expected within a minimum timeline of 24 hours to get accurate state of budiness.
- The data is expected to rapidly grow considering the expanding plans the company would have.
- All online activities are free

Based on these considerations, ABC data pipeline would require a rapid scaling, high availability, and secured process that is invoked once a day to extract and transform their data in a very cost effective manner.

Lambda serverless computing offers this and more, with a highly effective autoscaling capability (from 0 to 3,000 concurrent executions in seconds) and a unique billing process that's based on just what is used and scales itself to zero when it is not used.
The container image bolsters the agility of the lambda function by being able to accomodate larger lambda functions with a 10GB package deployment size compared to 50mb zip deployment if using just Lambda.


## Components and pricing
[Back to top](#table-of-contents)


   <br>

    | Major components | Appx cost | 
    | :-------------------- | :---- | 
    | AWS ECR       | $0.10/GB/Month | 
    | AWS SNS           |$2/100k notifications |
    | AWS EventBridge                   | $1.00/million custom events published |  
    | AWS Lambda                   |~ $0.0000063/day|  


