---
title: "Prerequisites"
date: 2020-11-18T09:16:09-04:00
chapter: false
weight: 2
pre: "<b>1. </b>"
---

## Working with existing clusters

To take advantage of Graviton based Amazon OpenSearch Service instances, your existing x86-based cluster must be running Amazon OpenSearch Service version 7.9 and above. For the latest updates of this information, see [Supported instance types in Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/supported-instance-types.html). For upgrade considerations, compatibilities, and instructions, see [Upgrading Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/version-migration.html).

## Upgrade Amazon OpenSearch Service Versions

You can confirm the Amazon OpenSearch Service version via the AWS CLI or Amazon OpenSearch Service console, as in the following screenshot.

![OpenSearch Version Upgrade](/Sustainability/100_migrating_opensearch_to_graviton/Images/OpenSearchVersion.png)

To upgrade your domain, choose Upgrade on the Actions menu. You can then choose what version to upgrade to, or verify your cluster can be upgraded. The upgrade process takes some time depending on the size of your cluster. For more information, see [Why is my Amazon OpenSearch Service domain upgrade taking so long?](https://repost.aws/knowledge-center/opensearch-domain-upgrade)

The same can be accomplished with the AWS CLI using the following commands:

Get the configuration details for a given domain using the [describe-elasticsearch-domain](https://docs.aws.amazon.com/cli/latest/reference/es/describe-elasticsearch-domain.html) command:

```
aws es describe-elasticsearch-domain --domain-name my-domain
```

If the cluster version is less than 7.9, use the [upgrade-elasticsearch-domain](https://docs.aws.amazon.com/cli/latest/reference/es/upgrade-elasticsearch-domain.html) command to upgrade your domain:

```
aws es upgrade-elasticsearch-domain --domain-name my-domain --target-version 7.9
```



{{< prev_next_button link_prev_url="../" link_next_url="../2_create_cluster" />}}
