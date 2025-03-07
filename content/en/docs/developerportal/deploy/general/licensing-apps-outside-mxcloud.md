---
title: "Licensing Apps"
url: /developerportal/deploy/licensing-apps-outside-mxcloud/
weight: 5
description: "How to apply licenses to apps which are outside Mendix Cloud"
tags: ["App", "Developer Portal", "License", "Subscription Secret", "Upgrade", "SAP", "MindSphere", "Insights Hub"]
#To update these screenshots, you can log in with credentials detailed in How to Update Screenshots Using Team Apps.
#NB have left out AWS and Azure Marketplace offerings for now, pending further research.
---

{{% alert color="info" %}}
<img src="/attachments/china.png" class="d-inline-block" /> For the Simplified Chinese translation, click [中文译文](https://cdn.mendix.tencent-cloud.com/documentation/developerportal/licensing-apps-outside-mxcloud.pdf).
{{% /alert %}}

## 1 Introduction

On Mendix Cloud, you can build [Free Apps](/developerportal/deploy/mendix-cloud-deploy/#free-app), which let you try things out and build and test apps using all the functionality of Mendix.

You can also deploy apps without a license to another public or private cloud of your choice, such as SAP Business Technology Platform (SAP BTP). This gives you the opportunity to try things out and to build and test apps using both the functionality of Mendix and your target cloud.

Unlicensed apps, running outside Mendix Cloud, have some restrictions. These restrictions are listed in the table below.

| Feature | Unlicensed App | Licensed App |
| --- | --- | --- |
| **Number of Concurrent Users** | 6 | Depends on your pricing plan.¹ ² |
| **Time limitation** | Runtime stops after 2-4 hours (randomly chosen) regardless of user activity.³ | Does not have a time limitation. |
| **Number of Named Users** | No limit | Depends on your pricing plan.¹ |

¹ More information on the capabilities of different license options is available on [Mendix Platform Pricing](http://www.mendix.com/pricing).

² End-users of your app are classified as either internal or external. You will need to report this for licensing purposes using either the [`USAGE_METRICS_EMAIL_FIELDS` custom variable](/developerportal/deploy/environments-details/#custom-environment-variables) (if you are using email domain to distinguish between them) or by [populating the user type](/howto/monitoring-troubleshooting/populate-user-type/) for each end-user of your app. Only end-users whose Mendix accounts are marked as **Active** are counted towards the number of end-users of the app.

³ Depending on the configuration of your chosen cloud, a container and runtime may be restarted if it appears unhealthy because the runtime has stopped.

For each environment for which you want to remove the restrictions placed on an unlicensed app, you need a license. The method for applying a license differs depending on where you are deploying your app.

The app checks for a license each time it is started. If the license expires while the app is running, it will continue to run until the next time it is started, when the license will be checked again.

## 2 Obtaining a Mendix License

You can obtain a Mendix license from Mendix support. 

If you want to create a new licensed node in Mendix Cloud but your contract does not allow for more licensed nodes, contact your Customer Success Manager (CSM) first.

For all other license requests and **Subscription Secrets** to deploy to SAP BTP and Mendix for Private Cloud, do the following:

1. Open the [Request New App Node](https://newnode.mendix.com/) app.

2. Fill in the basic information, such as app name and hosting type.

3. Provide additional information about your app, if required by the type of hosting. For example, you need to provide the server ID if you are deploying the app locally on a Virtual Machine.

4. Save the app details.

Mendix Support will contact the Technical Contact via a ticket in the Support Portal.

If you are hosting your app somewhere else, such as on Cloud Foundry, Mendix Support will provide you with two parts to your key:

* **LicenseId** – a unique identifier for your license, based on where it is being deployed
* **LicenseKey** – a base64 string

An example **LicenseId** is `aab8a0a1-1370-467e-918d-3a243b0ae160`. The **LicenseKey** is a very long base64 string.

## 3 Activating a Mendix License

### 3.1 Mendix Cloud

For Mendix apps to run in production on Mendix Cloud, they must be linked to a licensed node in Mendix Cloud. This process is described in [Licensing Mendix Cloud Apps](/developerportal/deploy/licensing-apps/).

### 3.2 SAP BTP

To license a Mendix app on SAP BTP, you need to supply a **Subscription Secret** that is linked to your app.

You can add this subscription secret as part of creating an environment on SAP BTP. You can also add or change the subscription secret on the [Environment Details](/developerportal/deploy/environments-details/) page of the environment you wish to license.

For more information, see [SAP Business Technology Platform](/developerportal/deploy/sap-cloud-platform/).

### 3.3 Siemens Insights Hub

To license an Insights Hub app, you need to provide your **License ID** and **License Key** as Cloud Foundry environment variables. See [Cloud Foundry](#cloudfoundry), below, for instructions on how to do this.

### 3.4 Mendix for Private Cloud

To license a Mendix app on Mendix for Private Cloud, you need to supply a **Subscription Secret** or license credentials for your app. See below for how it can be added to either a Connected or Standalone cluster.

In addition to the licenses for your apps, you will also need to license the Mendix Operator which helps deploy your app to a Private Cloud environment. For details on the Mendix Operator license, see [Licensing Mendix for Private Cloud](/developerportal/deploy/private-cloud/#licensing).

#### 3.4.1 Mendix for Private Cloud Connected

You can add the subscription secret as part of creating an environment on Mendix for Private Cloud. You can also add or change the subscription secret on the **Environment Details** page of the environment you wish to license. For more information, see the [Change Subscription Secret](/developerportal/deploy/private-cloud-deploy/#license-mendix) section of *Deploying a Mendix App to a Private Cloud Cluster*.

#### 3.4.2 Mendix for Private Cloud Standalone

You will need to add the license credentials and configure the license in the Mendix Custom Resource (CR) for your Private Cloud environment. For more information, see the [Editing the CR](/developerportal/deploy/private-cloud-operator/#edit-cr) section of *Using Command Line to Deploy a Mendix App to a Private Cloud Cluster*.

### 3.5 Cloud Foundry{#cloudfoundry}

To activate a license on your app running on Cloud Foundry, you need the license credentials provided by Mendix Support.

The two environment variables `LICENSE_ID` and `LICENSE_KEY` need to be set to the values of the **LicenseId** and **LicenseKey** provided by Mendix Support. Do this by running the following two commands, replacing `<YOUR_APP>` with the name of your app.

```bash
cf set-env <YOUR_APP> LICENSE_ID <LicenseId>
cf set-env <YOUR_APP> LICENSE_KEY <LicenseKey>
```

Then restart the app so that the environment variables are read and the license goes into effect.

### 3.6 Docker

To activate a license on your app running in a Docker container, you need the license credentials provided by Mendix Support.

Two additional environment variables, `LICENSE_ID` and `LICENSE_KEY`, need to be set to the values of the **LicenseId** and **LicenseKey** provided by Mendix Support. To do this, add them to the startup command for your container.

```bash
docker run -it \
  … \
  -e LICENSE_ID=<LicenseId> \
  -e LICENSE_KEY=<LICENSE_KEY> \
  mendix/mendix-buildpack:…
```

### 3.7 Kubernetes

To activate a license on your app running on Kubernetes, you need the license credentials provided by Mendix Support.

Two additional environment variables, `LICENSE_ID` and `LICENSE_KEY`, need to be set to the values of the **LicenseId** and **LicenseKey** provided by Mendix Support. To do this, add them to the deployment command for your app.

For full instructions on how to do this and how to supply the keys using a **Secrets** file, see the [Deploying the Application](/developerportal/deploy/run-mendix-on-kubernetes/#deploy) section of *Use Docker with Minikube*.

### 3.8 Windows Server

To license a Mendix app on Microsoft Windows, follow these steps:

1. Obtain your server ID.
2. Request a license key from Mendix Support.
3. Insert the license key on the server.

For full instructions on how to do this, see [Activate a Mendix License on Microsoft Windows](/developerportal/deploy/activate-a-mendix-license-on-microsoft-windows/).

### 3.9 Unix-Like Server

To license a Mendix app on Linux, or another Unix-like operating system, follow these steps:

1. Open the interactive m2ee console.
2. Use the command `show_license_information` to obtain your server ID.
3. Request a license key from Mendix Support.
4. Activate your license on the server, using the m2ee command `activate_license`.

For more instructions on how to do this, see [Unix-Like Deployment](/developerportal/deploy/unix-like/).

## 4 Read More

* [Submit a Support Request](/developerportal/support/submit-support-request/)
