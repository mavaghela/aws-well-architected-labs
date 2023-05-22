---
title: "Update OpenSearch Cluster to use Graviton"
date: 2020-11-18T09:16:09-04:00
chapter: false
weight: 4
pre: "<b>3. </b>"
---

Currently, you can't mix x86 and Graviton based Amazon OpenSearch Service instances with the primary and data nodes. As such, both data nodes and primary nodes are modified at the same time. To modify your nodes, complete the following steps:

1. Nagivate to the [Amazon OpenSearch Service console](https://console.aws.amazon.com/aos/home), go to the domain you want to upgrade.

2. Under actions, click **Edit cluster configuration**.

![Edit Cluster Configuration](/Sustainability/100_migrating_opensearch_to_graviton/Images/EditClusterConfiguration.png)

3. In the Data nodes section, for Instance type, change your data nodes to Graviton instance types. In our case, we upgrade from r5.large.search to r6g.large.search.

![Edit Cluster Configuration](/Sustainability/100_migrating_opensearch_to_graviton/Images/DataNodeChange.png)

4. In the Dedicated master nodes section, for Instance type, change your dedicated primary nodes to Graviton instance types. In our case, we upgrade from r5.large.search to r6g.large.search.

![Edit Cluster Configuration](/Sustainability/100_migrating_opensearch_to_graviton/Images/MasterNodeChange.png)

5. Click **Save changes**.

The cluster goes into a processing state. During this time, you can monitor the Cluster health tab to see your number of nodes increase. In our case, our cluster has three dedicated primary nodes and three data nodes (six total).

![Processing Cluster Update](/Sustainability/100_migrating_opensearch_to_graviton/Images/Processing6Nodes.png)

During deployment, Amazon OpenSearch Service performs a [blue/green deployment](https://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-managedomains-configuration-changes.html). This ensures any errors encountered during modification can be rolled back. You can continue to use the cluster during this time, however there may be a brief service interruption when the cluster switches to the new dedicated primary nodes. During blue/green deployment, you’re charged for both instance types, and then only the new instance type going forward.

![Processing Cluster Update](/Sustainability/100_migrating_opensearch_to_graviton/Images/Processing12Nodes.png)

After the modification finishes successfully, you can verify both the primary and data nodes are using Graviton instances.

![Graviton Cluster Configuration](/Sustainability/100_migrating_opensearch_to_graviton/Images/GravitonClusterConfiguration.png)

## Validate and confirm the application works correctly

You can now validate Amazon OpenSearch Service is performing as expected with your application. You can check the Cluster health tab for metrics related to cluster performance and observe if you’re not seeing the expected performance.


## Rollback in case of Issues

In the rare scenario in which issues are discovered with the Graviton based Amazon OpenSearch Service cluster, such as application compatibility or data issues, you can perform the same steps to change the cluster back to the original node type.

{{< prev_next_button link_prev_url="../2_create_cluster" link_next_url="../cleanup" />}}
