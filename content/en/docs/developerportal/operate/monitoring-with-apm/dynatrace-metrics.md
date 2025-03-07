---
title: "Dynatrace for Mendix Cloud"
url: /developerportal/operate/dynatrace-metrics/
weight: 25
description: "How to configure Mendix Cloud to enable monitoring and analysis with Dynatrace."
tags: ["Dynatrace", "Mendix Cloud", "monitoring", "analysis"]
#To update these screenshots, you can log in with credentials detailed in How to Update Screenshots Using Team Apps.
---

## 1 Introduction

[Dynatrace](https://www.dynatrace.com/) is a monitoring and analysis tool for cloud applications. It is a SaaS-based data analytics platform that provides monitoring for servers, databases, tools, and services. This document explains how to configure your Mendix Cloud app to send data to Dynatrace to provide additional monitoring.

For Dynatrace monitoring, [Dynatrace OneAgent](https://www.dynatrace.com/platform/oneagent/) is used to collect metrics.

In addition to auto-instrumented built-in metrics collected by OneAgent, Mendix apps can also collect custom application metrics. Custom application metrics are supported in Mendix 9.7 and above. For more information on the custom metrics you can send to Dynatrace, see [Monitoring Your Mendix Apps with an APM Tool](/developerportal/operate/monitoring-with-apm/).

## 2 Prerequisites

To use Dynatrace and send data to Dynatrace from your Mendix app, you need the following:

* Access to a Saas or Managed Dynatrace environment
* The following information about Dynatrace:
    * The Dynatrace environment URL
    * The [Dynatrace environment ID](https://www.dynatrace.com/support/help/get-started/monitoring-environment/environment-id)
    * An access token for integrating your Dynatrace environment with your Mendix app; for details on how to obtain this, see Dynatrace's [Generate an Access Token](https://www.dynatrace.com/support/help/get-started/access-tokens#create-api-token) documentation
* A licensed Mendix app of which you are the [Technical Contact](/developerportal/general/app-roles/#technical-contact)

## 3 Connect Node to Dynatrace {#connect-node}

To start sending your Mendix app's metrics to Dynatrace, you need to set some environment variables in the Developer Portal. Follow these steps:

1. Go to the **Environments** page of your app in the Developer Portal.
2. Click **Details** on the environment you wish to monitor with Dynatrace. 
3. Switch to the [**Runtime** tab](/developerportal/deploy/environments-details/#runtime-tab).
4. Add the following **Custom Environment Variables**.
    | Variable | Required? | Description | Details |
    | --- | --- | --- | --- |
    | `DT_SAAS_URL` | Yes | The URL of Dynatrace environment | The format when using the Dynatrace SaaS environment is similar to `https://<your-environment-id>.live.dynatrace.com`. If you are using a Dynatrace managed environment, just provide the full URL of the Dynatrace domain, like  `https://<your-dynatrace-domain>`. |
    | `DT_TENANT` | Yes | The Dynatrace Environment ID | For more information, see the [Environment ID](https://www.dynatrace.com/support/help/get-started/monitoring-environment/environment-id) Dynatrace documentation. |
    | `DT_PAAS_TOKEN` | Yes | The access token for integrating your Mendix app with Dynatrace | Create this on the Dynatrace environment. For more information, see [Generate an Access Token](https://www.dynatrace.com/support/help/get-started/access-tokens#create-api-token). The token must include the `PaaS integration - Installer download` and `Ingest metrics` scopes. |
    | `DT_IS_MANAGED` | No | Set this to `true` if you are using Dynatrace Managed. The default is assumed to be Dynatrace SaaS and set to `false`. | This variable is only needed for custom application metrics ingestion. |
    | `DT_CLUSTER_ID` | No | You can use this to tag your cluster, process group, or deployment group. |
    | `DT_CUSTOM_PROP` | No | This can be used to provide metadata for your process group. | For more information, see [Define Your Own Process Group Metadata](https://www.dynatrace.com/support/help/platform-modules/infrastructure-monitoring/process-groups/configuration/define-your-own-process-group-metadata). |

5. Return to the **General** tab and restart your environment.

## 4 Additional Information {#additional-info}

### 4.1 Dimensions (Only Valid for Custom Metrics)

If you use Dynatrace to monitor more than one app and environment, you need some dimensions to be able to tell which app or environment these metrics apply to. To identify the metrics for your app and environment in Dynatrace, Mendix provides some default dimensions. You can also add extra dimensions.

{{% alert color="info" %}}
What Dynatrace calls "dimensions," other monitoring tools call "tags." The Mendix Developer Portal therefore refers to a "tag" when it is setting up a Dynatrace "dimension."
{{% /alert %}}

#### 4.1.1 Default Dimensions

For metrics that are pushed to Dynatrace, Mendix attaches these default dimensions:

* `app` – The environment ID of your Mendix environment
* `instance_index` – Instance index that the metrics belong to

#### 4.1.2 Extra Dimensions

You can set extra dimensions as tags in the Developer Portal. Mendix recommends at least setting an `env:{environment_name}` tag (for example, `env:accp`). This tag enables you to identify metrics sent from a particular environment so you can separate out production metrics from test metrics. 

To set this tag, do the following:

1. Go to the **Environments** page of your app in the *Developer Portal*.
2. Click **Details** on an environment you are monitoring with Dynatrace. 
3. Switch to the **Tags** tab.
4. Click **Add** and type in a string to be sent to Dynatrace as a dimension. For more information, see the [**Tags** tab](/developerportal/deploy/environments-details/#tags) documentation in *Environment Details*.
5. Restart the application.

Setting this value for your app causes all metrics from this environment of your app to have these tags. For example, the tags for `mx.microflow.time.avg` for this set of metrics include `env:accp`.

### 4.2 Dynatrace Issues

If you have any issues related to accessing Dynatrace, contact their support at [Dynatrace Support](https://one.dynatrace.com/hc/en-us/requests). You will need a Dynatrace account to request support.

## 5 Read More

* [Metrics](/developerportal/operate/metrics/)
