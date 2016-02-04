Elasticsearch Docker Image
======================

This repository contains Dockerfiles to run Elasticsearch under OpenShift v3.
Current Elasticsearch version is 1.1.

There are sample Image Stream and Template files on https://github.com/getupcloud/origin-templates.

Configuring
-----------

The following environment variables are available to configure your Elasticsearch instance:

* CLUSTER_NAME: Cluster name (default: default-cluster)
* INSTANCE_RAM: Max memory to reserve for Elasticsearch (default: 1G)
* LOGLEVEL: Log level (default: INFO)
* JAVA_OPTS: Append options to java bin (default: "")

Running Locally
---------------

To build and run locally, execute:

    git clone https://github.com/getupcloud/elasticsearch.git
    docker build -t elasticsearch:<version>-getup <version>
    docker run -d elasticsearch:<version>-getup
