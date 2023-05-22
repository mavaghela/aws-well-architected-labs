---
title: "Level 100: Migrating Amazon OpenSearch to Graviton"
menutitle: "Migrating Amazon OpenSearch to Graviton"
date: 2020-11-18T09:00:08-04:00
chapter: false
weight: 1
hidden: false
---
## Author

- **Mansi Vaghela**, Partner Solutions Architect.


## Introduction

Amazon OpenSearch Service is a distributed search and analytics suite derived from Elasticsearch, that makes it easy for you to search, analyze, visualize, and secure up to petabytes of text and unstructured data.

[AWS Graviton processors](https://aws.amazon.com/ec2/graviton/) are custom custom built by Amazon Web Services using 64-bit Arm Neoverse cores.

AWS Graviton CPUs have excellent energy efficiency, switching to Graviton EC2 instances can reduce energy usage by as much as 60% for the same performance as comparable x86-64 instances.

AWS controls the end to end lifecycle of the chip, from design to consumption, enhancing overall efficiency. [Read more here.](https://aws.amazon.com/ec2/graviton/)

This lab focuses on how to upgrade your existing Amazon OpenSearch instances to Graviton with minimal downtime.

## Why move to Graviton?

While running an OpenSearch Service domain, you can choose from a variety of instances for your primary nodes and data nodes suitable for your workload: general purpose, compute optimized, memory optimized, or storage optimized. With the release of each new generation, Amazon OpenSearch Service has brought even better price performance.

Amazon OpenSearch Service now supports AWS Graviton instances: 

* General purpose (M6g)
* Compute optimized (C6g)
* Memory optimized (R6g)
* Memory optimized with attached disk (R6gd)

AWS Graviton instances offer the following benefits:

* Up to 38% improvement in indexing throughput, 50% reduction in indexing latency, and 40% improvement in query performance depending upon the instance family and size compared to the corresponding intel-based instances from the current generation (M5, C5, R5).
* Up to 44% price/performance improvement over previous generation instances.
* Includes support for all recently launched features like encryption at rest and in flight, role-based access control, cross-cluster search, Auto-Tune, Trace Analytics, Kibana Reporting, and UltraWarm.
* The AWS Graviton instance family also includes several new performance optimizations, such as larger caches per core, higher Amazon Elastic Block Store (Amazon EBS) throughput than comparable x86 instances, fully encrypted RAM, and many others.

You can benefit from these optimizations with minimal effort by provisioning or migrating your OpenSearch Service instances to Graviton.



<!--
Amazon OpenSearch Service Graviton2 instances provide up to 44% price/performance improvement over previous generation instances.

Graviton2 instances include support for all recently launched features like encryption at rest and in flight, role-based access control, cross-cluster search, Auto-Tune, Trace Analytics, Kibana Reporting, and UltraWarm. The AWS Graviton2 instance family also includes several new performance optimizations, such as larger caches per core, higher Amazon Elastic Block Store (Amazon EBS) throughput than comparable x86 instances, fully encrypted RAM, and many others. You can benefit from these optimizations with minimal effort by provisioning or migrating your OpenSearch Service instances today. -->

## Goals

At the end of this lab you will:

* Understand how to upgrade an existing Amazon OpenSearchService Cluster so it is compatible with Graviton instances.
* Have practical hands on experience migrating an Amazon OpenSearchService Cluster from x86-64 based instances to Graviton with minimal downtime.
* Learn how to roll back to previous instance types if compatibility issues are discovered.

<!--
In this workshop module, we’ll start by creating a cluster running on x86-based processors, and then we’ll upgrade it to Graviton2-based instances accomplishing this with minimal downtime. In order to minimize downtime while upgrading the instance type to a Graviton2-based one, Amazon OpenSearch Service deploys a new cluster, and shifts traffic to it once it is ready. This is called a Blue/Green deployment strategy, and is a common technique to minimize or avoid downtime when deploying new software versions. While the change takes place, you will still be able to read from and write to the cluster.

We will walk through the following steps:

* Upgrade an existing Amazon OpenSearch Service cluster (if needed):
    * Determine if the current cluster version meets the minimum required version (7.9 or later) for moving to Graviton2.
    * Upgrade the Amazon OpenSearch Service domain to the required minimum version.
* Modify the instance type of your cluster nodes to use Graviton
* Confirm that your applications work correctly with the upgraded cluster.
* Roll back to the previous instance types if compatibility issues are discovered.


* Create a sample Amazon OpenSearch Service cluster (called a domain) with version 7.9
* Cluster will include 3 data nodes and 2 primary nodes of the m5.large.elasticsearch instance type, which is an x86-based instance
* Modify the instance type of your cluster nodes
* Confirm that your applications work correctly with the upgraded cluster
* Roll back to the previous instance types if compatibility issues are discovered

-->



## Prerequisites

* The lab is designed to run in your own AWS account.
* It can be run in any region that supports OpenSearch and Graviton but us-east-1 is recommended.

{{% notice note %}}
As a general best practice, we recommend testing the process in a non-production environment followed by validation tests to make sure everything is configured and operating as per your expectations before making changes to the production environment. We also recommend creating a snapshot of your cluster before performing upgrades or modifying the instance type to minimize the risk of data loss.
{{% /notice %}}

## Costs

With Amazon OpenSearch Service, you pay only for what you use. There is no minimum fee or usage requirement. You are charged based on three dimensions: instance hours, which are the number of hours an instance is available to you for use; the amount of storage you need; and data transferred in and out of Amazon OpenSearch Service. Storage pricing depends on the storage tier and type of instance you choose.

See [Amazon OpenSearch pricing](https://aws.amazon.com/opensearch-service/pricing/) for more details.

During blue/green deployment, you’re charged for both instance types, and then only the new instance type going forward.

{{% notice note %}}
**NOTE:** You will be billed for any applicable AWS resources used if you complete this lab that are not covered in the [AWS Free Tier](https://aws.amazon.com/free/).
{{% /notice %}}
* [AWS Pricing](https://aws.amazon.com/pricing/)

## Lab Duration
Estimated time required to complete this lab is 40 minutes.




{{< prev_next_button link_next_url="./1_prerequisites/" button_next_text="Start Lab" first_step="true" />}}

## Steps:
{{% children  /%}}
