There are two main applications in this project.Druid and Grafana.
Apache Druid is a real-time analytics database designed for fast slice-and-dice analytics ("OLAP" queries) on large data sets. Most often, Druid powers use cases where real-time ingestion, fast query performance, and high uptime are important.
Grafana can Create, explore, and share beautiful dashboards that combine data from multiple sources to foster a data-driven culture within team and in an organization.
I have deployed in my local machine using docker which has three files.
**compose.yml**
Druid performs different services through different servers and this file contains services(which can be mapped as different containers in docker ) and their characteristics.
Since I am pulling the data from kafka and pushing to druid there are also some additional services and their properties related to kafka.
**environment-druid**
This file further configures properties of druid like deeep storage,metadata storage,extensions load list etc... 
**environment-grafana**
The configurations made in this file helps us to connect with Druid.

The use cases which powered these applications are Hourly sales report and Hourly trends report.Both use cases based on one common pipeline.
Kafka->Druid->Grafana.
Data is pushed to Kafka from QlikReplicate(tool). Druid connects with Kafka with the help of bootstrap servers and desired topic.Dashboards of desired format can be viewed with the help of Grafana since Druid-plugin is installed in Grafana.
One can derive insights by dashboards in grafana which can make in decision making.
