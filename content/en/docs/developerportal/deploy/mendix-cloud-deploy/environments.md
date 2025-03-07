---
title: "Environments"
url: /developerportal/deploy/environments/
weight: 5
description: "Lists the environments in which your app is deployed. Also the starting point for managing existing environments and further deployments."
tags: ["Deploy","App","Developer Portal"]
#To update these screenshots, you can log in with credentials detailed in How to Update Screenshots Using Team Apps.
---

## 1 Introduction

You can use the **Environments** page to access information about your environments, deploy packages, manage certificates and access restrictions, and more.

The **Environments** page has the following tabs:

* **Deploy**
* **Custom Domains**
* **Access Restriction Profiles**
* **Permissions**
* **Services**
    
## 2 Deploy

In the **Deploy** tab, you can view information about your environments. You can also create, upload, delete, and deploy packages.

### 2.1 Deployment Package Repository{#package-repository}

The **Deployment Package Repository** section has an overview of the available deployment packages.

{{< figure src="/attachments/developerportal/deploy/mendix-cloud-deploy/environments/deployment-package.png" alt="The Deployment Package Repository section" >}}

You can perform the following actions in this section:

* Use the **Search** field to search the deployment packages by name, version, or creator
* Click **Upload** to upload a deployment package from your local device
* Click **Create Deployment Package** to create a deployment package based on a specific branch

You can also see information and perform actions on the existing deployment packages. For each deployment package, the table contains the following details:

* Deployment package name
* Version of the deployment package
* Date that the deployment package was created
* Creator account
* Expiry date of the deployment package, if one is set

To deploy a package, transporting it from the Team Server to the selected environment, click the **Deploy** icon.

{{< figure src="/attachments/developerportal/deploy/mendix-cloud-deploy/environments/deploy-icon.png" alt="" >}}

If you click **More Options** ({{% icon name="three-dots-menu-horizontal" %}}) on a package, you can do the following:

* View details, including the package size, description, build output, and an overview of the environments that are running the package
* Delete the package

{{< figure src="/attachments/developerportal/deploy/mendix-cloud-deploy/environments/deployment-package-options.png" alt="More Options" >}}

### 2.2 Environments

The **Environments** section has an overview of all the available environments. The contents of the **Environments** section differ based on whether or not your node supports flexible environments.

#### 2.2.1 Standard Environments

For standard plans, your node has production and acceptance environments. It can also include a test environment.

{{< figure src="/attachments/developerportal/deploy/mendix-cloud-deploy/environments/deploy-environments.png" alt="The Environments section for standard environments" >}}

For standard plans, the **Environments** section shows the following information:

* Environment name (Acceptance, Production, or Test)
* Environment status, indicated by the icon next to the environment name:
    * Green check mark – the application in this environment is running
    * Gray dash – no application has been started yet in this environment, or it has been turned off
    * Red cross – the application in this environment is unstable and probably not usable anymore

* Name of the deployment package
* Version of the deployment package
* Runtime, the Studio Pro version with which the app was built
* URL of the app
    
{{% alert color="info" %}}The environment status is cached; there can be a delay of up to five minutes before the status icon displays a change of status. For information on the details of any alerts, see [Alerts](/developerportal/operate/monitoring-application-health/).{{% /alert %}}

You can perform the following actions in this section:

* View an environment's details – Click **Details** ({{% icon name="notes-paper-edit" %}}) to go to the [Environment Details](/developerportal/deploy/environments-details/) page.
* Transport an environment – If you have [Transport rights](/developerportal/deploy/node-permissions/#transport-rights) enabled, you will see a **More Options** icon that you can click to stage an environment to acceptance or production.

    {{< figure src="/attachments/developerportal/deploy/mendix-cloud-deploy/environments/transport-to.png" alt="" >}}

* Set up deployment – If you are the [Technical Contact](/developerportal/general/app-roles/#technical-contact), you will see a **Setup Studio Pro Deployment** button. You can use this to set the target environment to which apps are deployed from Studio Pro; for more information, see [Studio Pro Deployment Settings](/developerportal/deploy/studio-deployment-settings/).

#### 2.2.2 Flexible Environments{#flexible-environments}

If your Mendix license supports flexible environments, you can define the number and type of environments that you have. You must define at least two environments, one of which must be a production environment. The other environment (or environments) may be designated according to your requirements. For example, you can have a production environment and multiple staging environments if your deployment process requires it.

{{< figure src="/attachments/developerportal/deploy/mendix-cloud-deploy/environments/deploy-flex-environments.png" alt="The Environments section with flexible environments" >}}

For flexible environments, the **Environments** section shows the following information:

* Environment status, indicated by the icon next to the environment name:
    * Green check mark – the application in this environment is running
    * Gray dash – no application has been started yet in this environment, or it has been turned off
    * Red cross – the application in this environment is unstable and probably not usable anymore
* Name of the environment
* Version of the deployment package
* Runtime, the Studio Pro version with which the app was built
* Plan for the environment
* URL of the app

{{% alert color="info" %}}The environment status is cached; there can be a delay of up to five minutes before the status icon displays a change of status. For information on the details of any alerts, see [Alerts](/developerportal/operate/monitoring-application-health/).{{% /alert %}}

You can perform the following actions in this section:

* Search for an environment – Find a specific environment using the **Search** field.
* View an environment's details – Go to the environment's [Details](/developerportal/deploy/environments-details/) page by clicking **Details** ({{% icon name="notes-paper-edit" %}}).
* Set up deployment – If you are the [Technical Contact](/developerportal/general/app-roles/#technical-contact), you will see a **Setup Studio Pro Deployment** button. You can use this to set the target environment to which apps are deployed from Studio Pro; for more information, see [Studio Pro Deployment Settings](/developerportal/deploy/studio-deployment-settings/).
* Reorder environments – If you are the [Technical Contact](/developerportal/general/app-roles/#technical-contact), you can reorder the environments by clicking **More Options** ({{% icon name="three-dots-menu-horizontal" %}}) and selecting **Move Up** or **Move Down**.

    {{< figure src="/attachments/developerportal/deploy/mendix-cloud-deploy/environments/reorder-environments.png" alt="" >}}

    {{% alert color="info" %}}The button to transport an environment is not available when flexible environments are enabled. This is because you must choose your deployment target each time you deploy when you have flexible environments. To deploy, click **Deploy** in the [Deployment Package Repository](https://docs.mendix.com/developerportal/deploy/environments/#package-repository) section, as described above.{{% /alert %}}

### 2.3 Activity

In the **Activity** section, you can view a log of deployment activities performed on your environments.

{{< figure src="/attachments/developerportal/deploy/mendix-cloud-deploy/environments/activity.png" alt="Sample activity log" >}}

{{% alert color="info" %}}
Operations performed on a customer's behalf through an authorized Mendix support ticket are not logged in the activity log.
{{% /alert %}}

If you are the [Technical Contact](/developerportal/general/app-roles/#technical-contact), you can download a copy of the activity log by following these steps:

1. Click **Download to CSV**. (This button is only visible if you are the Technical Contact.)
2. Select the period for which you want to download log entries.
3. Click **Download**.

## 3 Custom Domains

In the **Custom Domains** tab, you can manage your custom domain certificates at the application level. You can also see an overview of linked custom domains.

When you need your Mendix app to be accessible via your own URL (for example, `https://myapp.mycompany.com/`), you must provide a custom SSL/TLS certificate for your domain. This enables your Mendix app to be accessible via a secure connection. For more information, see [Custom Domains](/developerportal/deploy/custom-domains/).

## 4 Access Restriction Profiles{#asp}

In the **Access Restriction Profiles** tab, you can manage custom access restriction profiles. These profiles can combine IP range filters and client certificate verification, so that any match on either the IP range or the client certificate will grant access. You can apply access restriction profiles to path-based access restrictions in specific environments of the application.

For details on setting up access restriction profiles, see [Restrict Access for Incoming Requests](/developerportal/deploy/access-restrictions/).

## 5 Permissions{#permissions}

In the **Permissions** tab, the [Technical Contact](/developerportal/general/app-roles/#technical-contact) and other team members who have **Manage Permissions** enabled can manage various permissions to the environments for each team member. Team members who have a role with **Cloud Access** can view the permissions.

For details on managing node permissions, see [Node Permissions](/developerportal/deploy/node-permissions/).

## 6 Services{#services}

In the **Services** tab, the Technical Contact can determine which custom services can be used in the app's environments.

### 6.1 Available Services

One custom service is available: **Mendix Event Broker**. This service is required to use [Mendix Business Events](/appstore/modules/business-events/) on production apps.

### 6.2 Enabling Custom Services

The Technical Contact can only see services that have been licensed for their company. If the Technical Contact cannot enable the service, this means that the service has previously been licensed, but the license has expired.

Team members who have a role with **Cloud Access** can see which services are enabled or disabled.

Once a service has been enabled for an app, Technical Contacts can selectively enable it for each environment. For more information, see the [Services](/developerportal/deploy/environments-details/#services) section of the *Environment Details* page.

## 7 Read More

* [Deploy and Manage](/developerportal/deploy/)
* [Environment Details](/developerportal/deploy/environments-details/)
* [How to Receive Environment Status Alerts](/developerportal/operate/receive-alerts/)
* [How to Restrict Access for Incoming Requests](/developerportal/deploy/access-restrictions/)
