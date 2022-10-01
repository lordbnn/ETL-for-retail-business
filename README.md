# EVENT BASED ETL WITH AWS LAMBDA CONTAINER IMAGE
Data2bots Technical assessment


#### Table of contents 

   - [Table of contents](#table-of-contents)
  - [overview](#overview)
    - [Functional requirements of the data pipeline](#functional-requirements-of-the-data-pipeline)


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



