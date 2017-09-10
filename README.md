# Yey another elasticsearch presentation

_Elastich usefull searches and queries_

## WAIAWDID

Which means "Who Am I And What Do I Do ?"

Vincent DAGOURY - CTO @eAttestations.com

## What is elasticsearch a.k.a 'ELK' ?

'Elasticsearch' has been developped by Shay Banon (@kimshy) and it's now a company who can also provide support and services.

In his core it uses Lucene [https://lucene.apache.org/core/](https://lucene.apache.org/core/)
also used by Apache Solr, one of the best 'search' plateform.
[http://lucene.apache.org/solr/](http://lucene.apache.org/solr/)


A ELK stack is composed of :

- *Elasticsearch*  is an indexing systems build on a cluster that keeps in files and cache all the information we need and serves them through REST/JSON interface.
- *Logstash* is one tool for getting data (from files, db, Web etc...), read, apply mappings or change to the data and then put it where we want (to elasticsearch cluster for instance).
- *Kibana* is the tool for visiualisation of the content

This is the ELK stack which is full OpenSource and ready to be installed here : https://www.elastic.co

Many many many users, great development team around the world : 
- well maintened
- good doc
- many plugins
- easy to use and install
- easy to manage 

###  Elasticsearch comes with tools

#### *Beats*

Little agent to install
It pushes to Logstash or directly to elasticsearch. It's a plateform so you can develop your own. It cans read files (logs) which is the most commun one, system metrics for monitoring, Network packets, Windows logs, do heartbeats.

#### *X-Pack*

Package of plugins to install.
It provides and it's quiet mandatory, plugins for security, alerting, Monitoring, Reporting, Graph, Machine Learning. It needs to be installed on elasticsearch nodes (Master, Data and Client) AND on Kibana to get all the visualization.
Of course each of this plugins can be installed separatly.

#### On security

'Security' plugin allows you to put a user/password within Kibana and Elasticsearch.

The REST/JSON interfaces will be protected by Security and you'll need to provide HTTP Headers auth information.

### Cloud Services
You can also benefits from the Cloud with an assistant that wil create and ELK cluster for you in Google Cloud Plateforme or Amazon Web Services.



## Configuration


## How to Query against 'elasticsearch'

All this need to be run agains a elasticsearch query runner (Sense)
The best one is within Kibana "Development tools" where you'll find "Sense".

It's possible to interact with elasticsearch server with many languages such Java, Python, JavaScript (like Kibana) etc...

First of all : it's all REST/JSON interface !
Actions are GET/PUT/POSTS/DELETE/HEAD etc...

## General searches

GET /_search
{
  "query": {
    "match_all": {}
  }
}


## Healthchecks

### Get All we need to know if everything is allright

GET _all

### Get Cluser Health
GET _cluster/health

### Get Master Node
GET _cluster/state/master_node

### Get Nodes
GET _cluster/state/nodes

### Get shards information on specific index
GET logstash-*/_search_shards