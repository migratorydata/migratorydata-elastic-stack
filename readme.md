# Monitoring MigratoryData with Elastic Stack

This repository shows how to use Elastic Stack (Filebeat, Elasticsearch, and Kibana) for monitoring a MigratoryData cluster.

## Features

* Collecting and parsing MigratoryData logs by using Filebeat (access logs, message logs, and statistics)
* Indexing MigratoryData logs into Elasticsearch
* Building Kibana searches for analyzing data and dashboards for visualizing data

## Setup

For current purposes our setup consists in a MigratoryData cluster of three nodes. Each node runs one instance 
of MigratoryData Server and one instance of Filebeat. Filebeat is an agent which collects access logs, message logs and 
statistics logs produced by the MigratoryData server. The logs are collected on the fly, as soon as they are produced by 
the MigratoryData server. The collected logs are sent to the Elasticsearch server over the network.

Users use web browsers to visualize and analyze the data. Users connect to the Kibana server and make queries that are 
automatically forwarded to the Elasticsearch server. 

![setup](diagrams/setup-migratorydata-elasticstack.png)

## Elastic Stack Installation

The installation of Elasticsearch and Kibana is straightforward. Simply download the installation package in zip or tar 
format, uncompress it, and run the script `elasticsearch`or `kibana` available in the folder `bin`. Other installation 
formats such as `deb` and `rpm` are available too.

You can start by installing one instance of Elasticsearch and one instance of Kibana on the **same machine** and using their 
respective **default configurations**. Advanced Elastic Stack configurations and settings are available, including 
high availability clustering, but these are beyond the scope of this tutorial.

With the default configuration, Elasticsearch uses the port `9200` to accept connections and communicate both with 
the FileBeat agents and Kibana. With the default configuraton, Kibana uses the port `5601` to accept connections from users.

## FileBeat Installation and Configuration

