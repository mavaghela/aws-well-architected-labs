---
title: "Create OpenSearch Cluster"
date: 2020-11-18T09:16:09-04:00
chapter: false
weight: 3
pre: "<b>2. </b>"
---

We’ll start by creating a cluster running on x86-based instances, and then we’ll update it to Graviton based instances, accomplishing this with minimal downtime.

1. Nagivate to the [Amazon OpenSearch Service console](https://console.aws.amazon.com/aos/home) and click **Create Domain**.
2. Under **Domain creation method** select **Standard create**. 
3. Under **Deployment options** select **Domain without standby**. This will allow us to select instances in the AWS Free Tier.

![Create Domain](/Sustainability/100_migrating_opensearch_to_graviton/Images/CreateDomain.png)

4. Under **Data nodes**, select instance type as **t3.small.search** and **EBS storage size per node** of **10**.

![Create Data Node](/Sustainability/100_migrating_opensearch_to_graviton/Images/CreateDataNode.png)

5. Similarly, under **Dedicated master nodes**, select instance type as **t3.small.search**.

![Create Master Node](/Sustainability/100_migrating_opensearch_to_graviton/Images/CreateMasterNode.png)

5. Under **Network** select a VPC, Subnets and Security Group to create the cluster in.

![Create Domain Network](/Sustainability/100_migrating_opensearch_to_graviton/Images/CreateDomainNetwork.png)

6. Leave all else as default and click **Create**. It will take a few minutes for the cluster to create. Once it has completed creation, you should see the below configuration.

![Domain Creation Complete](/Sustainability/100_migrating_opensearch_to_graviton/Images/DomainCreateComplete.png)



{{< prev_next_button link_prev_url="../1_prerequisites" link_next_url="../3_modify_cluster" />}}