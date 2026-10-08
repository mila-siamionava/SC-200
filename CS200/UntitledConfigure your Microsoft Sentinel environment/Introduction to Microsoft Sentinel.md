
Traditional security information and event management (SIEM) systems typically take a long time to set up and configure. They're also not necessarily designed with cloud workloads in mind. Microsoft Sentinel enables you to start getting valuable security insights from your cloud and on-premises data quickly. This module helps you get started.

# Introduction
Imagine that you work as a security operations center (SOC) analyst. Your organization wants to advance its security-management capabilities. The business already started moving some workloads to the public cloud.

You've been asked to evaluate _security information and event management_ (SIEM) solutions that can help in both an on-premises and a multicloud environment. You've heard about Microsoft Sentinel and want to find out whether it could be the right SIEM solution for your business.

Ideally, you'd select a service that provides the features and functionality that you need, with minimal administration and a flexible pricing model.

Microsoft Sentinel offers exactly those benefits.

In this module, you'll explore Microsoft Sentinel and discover why and when to use it. You'll investigate the key features and capabilities of Microsoft Sentinel, including how and when to deploy it.

## Learning objectives

By the end of this module, you're able to:

- Identify the various components and functionality of Microsoft Sentinel.
- Identify use cases where Microsoft Sentinel would be a good solution.

## Prerequisites

- Familiarity with security operations in an organization
- Basic experience with Microsoft Defender and Azure services
# What is Microsoft Sentinel?
Let's start with a few definitions and a look at _security information and event management_ (SIEM) systems and Microsoft Sentinel.

## What is security information and event management (SIEM)?

A SIEM system is a tool that an organization uses to collect, analyze, and perform security operations on its computer systems. Those systems can be hardware appliances, applications, or both.

In its simplest form, a SIEM system allows you to:

- Collect and query logs.
- Do some form of correlation or anomaly detection.
- Create alerts and incidents based on your findings.

A SIEM system might offer functionality such as:

- **Log management**: The ability to collect, store, and query the log data from resources within your environment.
    
- **Alerting**: A proactive look inside the log data for potential security incidents and anomalies.
    
- **Visualization**: Graphs and dashboards that provide visual insights into your log data.
    
- **Incident management**: The ability to create, update, assign, and investigate incidents that have been identified.
    
- **Querying data**: A rich query language, similar to that for log management, that you can use to query and understand your data.
    

## What is Microsoft Sentinel?

Microsoft Sentinel is a cloud-native SIEM system that a security operations team can use to:

- Get security insights across the enterprise by collecting data from virtually any source.
- Detect and investigate threats quickly by using built-in machine learning and Microsoft threat intelligence.
- Automate threat responses by using playbooks and by integrating Azure Logic Apps.

Unlike with traditional SIEM solutions, you don't need to install any servers either on-premises or in the cloud to run Microsoft Sentinel. Microsoft Sentinel is a service that you deploy in Azure. You can get up and running with Sentinel in just a few minutes in the Azure portal.

Microsoft Sentinel is tightly integrated with other cloud services. Not only can you quickly ingest logs, but you can also use other cloud services natively (for example, authorization and automation).

Microsoft Sentinel helps you enable end-to-end security operations including collection, detection, investigation, and response:

![Diagram showing the end-to-end functionality of Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/02-end-to-end.svg)

Let's take a look at the key components in Microsoft Sentinel.
# How Microsoft Sentinel works
Microsoft Sentinel helps you enable end-to-end security operations. It starts with log ingestion and continues through to automated response to security alerts.

Here are the key features and components of Microsoft Sentinel.

## Data connectors

The first thing to do is to have your data ingested into Microsoft Sentinel. Data connectors let you do just that. You connect Data connectors by first installing _Content hub_ solutions. Once installed, you can add some services, such as Azure activity logs, just by selecting a button. Others, such as syslog, require more configuration. There are data connectors that cover all scenarios and sources, including but not limited to:

- syslog
- Common Event Format (CEF)
- Trusted Automated eXchange of Indicator Information (TAXII) (for threat intelligence)
- Azure Activity
- Microsoft Defender services
- Amazon Web Services (AWS) and Google Cloud Platform (GCP)

[![Screenshot that shows a partial list of data connectors in the Microsoft Sentinel UI in the Azure portal.](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-data-connectors.png)](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-data-connectors.png#lightbox)

## Log retention

After data is ingested into Microsoft Sentinel, the data is stored in the Log Analytics workspace. The benefits of using Log Analytics include the ability to use the Kusto Query Language (KQL) to query your data. KQL is a rich query language that gives you the power to dive into and gain insights from our data.

[![Screenshot showing the Log Analytics interface in the Azure portal.](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-log-analytics.png)](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-log-analytics.png#lightbox)

## Workbooks

You can use workbooks to visualize your data within Microsoft Sentinel. Think of workbooks as dashboards. Each component in the dashboard is built by using an underlying KQL query of your data. You can use the built-in workbooks within Microsoft Sentinel and edit them to meet your own needs, or create your own workbooks from scratch. If you've used Azure Monitor workbooks, this feature is familiar to you, because it's Sentinel's implementation of Monitor workbooks.

[![Screenshot showing an example of a workbook in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-workbooks.png)](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-workbooks.png#lightbox)

## Analytics alerts

So far, you have your logs and some data visualization. Now it would be great to have some proactive analytics across your data, so you're notified when something suspicious occurs. You can enable built-in analytics alerts within your Sentinel workspace. There are various types of alerts, some of which you can edit to your own needs. Other alerts are built on machine-learning models that are proprietary to Microsoft. You can also create custom, scheduled alerts from scratch.

[![Screenshot showing some of the built-in analytics alerts available in a Microsoft Sentinel workbook.](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-analytics-alerts.png)](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-analytics-alerts.png#lightbox)

## Threat hunting

We won't dive deeply into threat hunting in this module. However, if SOC analysts need to hunt for suspicious activity, many Content hub solutions provide built-in hunting queries that they can use. Analysts can also create their own queries. Sentinel also integrates with Azure Notebooks. It provides example notebooks for advanced hunters who want to use the full power of a programming language to hunt through their data.

[![Screenshot showing the threat-hunting interface in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-hunting.png)](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-hunting.png#lightbox)

## Incidents and investigations

An incident is created when an alerts are triggered. In Microsoft Sentinel, you can do standard incident management tasks like changing status or assigning incidents to individuals for investigation. Microsoft Sentinel also has investigation functionality, so you can visually investigate incidents by mapping entities across log data along a timeline.

[![Screenshot showing an incident-investigation graph within Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-investigate-incidents.png)](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-investigate-incidents.png#lightbox)

## Automation playbooks

With the ability to respond to incidents automatically, you can automate some of your security operations and make your SOC more productive. Microsoft Sentinel allows you to create automated workflows, or _playbooks_, in response to events. This functionality could be used for incident management, enrichment, investigation, or remediation. These capabilities are often referred to as _security orchestration, automation, and response (SOAR)_.

[![Screenshot showing a Microsoft Sentinel Automation, with the Create options highlighted.](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-logic-apps.png)](https://learn.microsoft.com/en-us/training/wwl-sci/intro-to-azure-sentinel/media/03-logic-apps.png#lightbox)

As the SOC Analyst, you now start to see how Microsoft Sentinel might help you achieve your goals. For example, you could:

- Ingest data from your cloud and on-premises environments.
- Perform analytics on that data.
- Manage and investigate any incidents that occur.
- Respond automatically by using playbooks.

In other words, Microsoft Sentinel gives you an end-to-end solution for your security operations.

# When to use Microsoft Sentinel
Microsoft Sentinel is a solution for performing security operations on your cloud and on-premises environments.

Use Microsoft Sentinel if you want to:

- Collect event data from various sources.
- Perform security operations on that data to identify suspicious activity.

Security operations could include:

- Visualization of log data
- Anomaly detection
- Threat hunting
- Security incident investigation
- Automated response to alerts and incidents

Microsoft Sentinel offers other capabilities that could help you decide whether it's the right fit for you:

- Cloud-native SIEM: with no servers to provision, scaling is effortless
- Integration with the Azure Logic Apps service and its hundreds of connectors
- Benefits of Microsoft research and machine learning
- Key log sources provided for free
- Support for hybrid cloud and on-premises environments
- SIEM and a data lake all in one

When you began investigating Microsoft Sentinel, your organization had some clear requirements:

- Support for data from multiple cloud environments
- Features and functionality required for a security operations center (SOC), without too much administrative overhead

You've found that Microsoft Sentinel could be a good fit. It offers data connectors for syslog, Amazon Web Services (AWS), and other sources, and the ability to scale effortlessly without provisioning servers. During your analysis, you also realized that your organization should make automation a key part of its SOC strategy. Automation wasn't something the organization had considered before, but now you'll look into using automation playbooks.

If you're collecting infrastructure or application logs for performance monitoring, consider also using Azure Monitor and Log Analytics for that purpose.

And perhaps you want to understand the security posture of your environment, make sure that you're compliant with policy, and check for security misconfigurations. If so, consider also using Microsoft Defender for Cloud. You can ingest Defender for Cloud alerts as a data connector for Microsoft Sentinel.

![[Pasted image 20261001145110.png]]

# Summary
You've learned how Microsoft Sentinel can meet the requirements of the SOC analyst's organization with:

- Support for data connectors for cloud and hybrid services.
- Features and functionality that you need, with minimal administration.

You explored what a SIEM solution is, and what Microsoft Sentinel and its key components have to offer. You also learned when to use Microsoft Sentinel and when other Azure products might complement Microsoft Sentinel to improve the security of your environment.

You now understand how Microsoft Sentinel helps you to perform end-to-end security operations.

## Learn more

Learn more about Microsoft Sentinel from the following articles:

- [Microsoft Sentinel documentation](https://learn.microsoft.com/en-us/azure/sentinel)
- [Quickstart: Onboard Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard)
- [Microsoft Sentinel pricing](https://azure.microsoft.com/pricing/details/azure-sentinel)
- [Roles and permissions in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/roles)
- [Use Azure Monitor workbooks to visualize and monitor your data](https://learn.microsoft.com/en-us/azure/sentinel/tutorial-monitor-your-data)
- [Visualize collected data](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-get-visibility)
- [Extend Microsoft Sentinel across workspaces and tenants](https://learn.microsoft.com/en-us/azure/sentinel/extend-sentinel-across-workspaces-tenants#cross-workspace-monitoring?azure-portal=true)

# Create and manage Microsoft Sentinel workspaces

Learn about the architecture of Microsoft Sentinel workspaces to ensure you configure your system to meet your organization's security operations requirements.

## Learning objectives

Upon completion of this module, the learner will be able to:

- Describe Microsoft Sentinel workspace architecture
- Onboard a Microsoft Sentinel workspace to Microsoft Defender
- Manage a Microsoft Sentinel workspace in Microsoft Defender

# Introduction
Deploying the Microsoft Sentinel environment involves designing a workspace configuration to meet your security and compliance requirements. The provisioning process includes creating a Log Analytics workspace and configuring the Microsoft Sentinel options.

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You're responsible for setting up the Microsoft Sentinel environment to meet the company requirement to minimize cost, meet compliance regulations, and provide the most manageable environment for your security team to perform their daily job responsibilities.

You start by understanding the Microsoft Sentinel workspace's architecture. After you've decided on your workspace implementation options, you create your first Microsoft Sentinel workspace.

After completing this module, you'll be able to:

- Describe Microsoft Sentinel workspace architecture
- Onboard a Microsoft Sentinel workspace to Microsoft Defender
- Manage a Microsoft Sentinel workspace in Microsoft Defender
# Plan for the Microsoft Sentinel workspace
Before deploying Microsoft Sentinel, it's crucial to understand the workspace options. The Microsoft Sentinel solution is installed in a Log Analytics Workspace, and most implementation considerations are focused on the Log Analytics Workspace creation. The single most important option when creating a new Log Analytics Workspace is the region. The region specifies the location where the log data resides.

The three implementation options:

- Single-Tenant with a single Microsoft Sentinel Workspace
    
- Single-Tenant with regional Microsoft Sentinel Workspaces
    
- Multiple tenants
    

## Single-tenant single workspace

The single-tenant with a single Microsoft Sentinel workspace is the central repository for logs across all resources within the same tenant.

This workspace receives logs from resources in other regions within the same tenant. Because the log data (when collected) travels across regions and stored in another region, this creates two possible concerns. First, it can incur a bandwidth cost. Second, if there's a data governance requirement to keep data in a specific region, the single workspace option wouldn't be an implementation option.

![Diagram of a Single Tenant Microsoft Sentinel Workspace.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/single-tenant-workspace.png)

Single-Tenants with a single workspace trade-off include:

|Pros|Cons|
|---|---|
|Central Pane of Glass|May not meet Data Governance Requirements|
|Consolidates all security logs and information|Can incur bandwidth cost for cross region|
|Easier to query all information||
|Azure Log Analytics RBAC to control data access||
|Microsoft Sentinel RBAC for service RBAC||

## Single-tenant with regional Microsoft Sentinel workspaces

The single-tenant with regional Microsoft Sentinel workspaces, have multiple Microsoft Sentinel workspaces requiring the creation and configuration of multiple Microsoft Sentinel and Log Analytics workspaces.

![Diagram of a Microsoft Sentinel Single Tenant Regional Workspace.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/single-tenant-regional-workspace.png)

|Pros|Cons|
|---|---|
|No cross-region bandwidth costs|No central pane of glass. You aren't looking in one place to see all the data.|
|May be required to meet Data Governance requirements|Analytics, Workbooks, etc. must be deployed multiple times.|
|Granular data access control||
|Granular retention settings||
|Split billing||

To query data across workspaces, use the workspace() function before the table name.

Kusto

```
TableName

| union workspace("WorkspaceName").TableName

```

## Multiple tenant workspaces

If you're required to manage a Microsoft Sentinel workspace, not in your tenant, you implement Multiple tenant workspaces using Azure Lighthouse. This security configuration grants you access to the tenants. The tenant configuration within the tenant (regional or multi-regional) is the same consideration as before.

![Diagram of Microsoft Sentinel Multiple tenant Workspaces.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/multi-tenant-workspaces.png)

## Use the same log analytics workspace for Microsoft Sentinel and Microsoft Defender for Cloud

To streamline security operations, use the same workspace for both Microsoft Sentinel and Microsoft Defender for Cloud. All logs collected by Microsoft Defender for Cloud can also be used by Microsoft Sentinel. The default workspace created by Microsoft Defender for Cloud won't appear as an available workspace for Microsoft Sentinel.

# Create a Microsoft Sentinel workspace
After designing the workspace architecture, sign-in to the Azure portal. At the search bar, search for Sentinel, then select **Microsoft Sentinel**. The Microsoft Sentinel Workspaces shows a list of the current workspaces. Select the **+ add** button to start the creation process.

 Note

If you choose to perform this exercise, be aware you might incur costs in your Azure Subscription. To estimate the cost, refer to [Microsoft Sentinel Pricing](https://azure.microsoft.com/pricing/details/azure-sentinel/). We have also included an interactive lab simulation after the exercise.

## Microsoft Sentinel installation prerequisites

To enable Microsoft Sentinel, you need contributor permissions to the subscription in which the Microsoft Sentinel workspace resides. To use Microsoft Sentinel, you need either contributor or reader permissions on the resource group that the workspace belongs.

## Create and configure a Log Analytics Workspace

1. The next page, **Add Microsoft Sentinel to a workspace** will display a list of available Log Analytics workspaces to add Microsoft Sentinel. Select the **+ create a new workspace** button to start the "Create Log Analytics workspace" process.
    
2. The Basics tab includes the following options:
    
    |Option|Description|
    |---|---|
    |Subscription|Select the Subscription|
    |Resource Group|Select or create a Resource Group|
    |Name|Name is the name of the Log Analytics workspace and is also the name of your Microsoft Sentinel Workspace|
    |Region|The region is the location the log data is stored.|
    
     Important
    
    The Name is the name of the Microsoft Sentinel workspace. The Microsoft Sentinel name defaults to the Log Analytics Workspace Name. The Region is the location where ingested data is stored. The data location impacts data governance requirements. Workspaces can't move from region to region; you'll need to recreate the workspace if the region option needs to be changed.
    
3. Select the **Review + Create** button and then select the **Create** button.
    

## Add Microsoft Sentinel to the workspace

The "Add Microsoft Sentinel to Workspace" screen will now appear after you've completed the previous steps.

1. Wait for the newly created "Log Analytics Workspace" to appear in the list. This operation could take a few minutes.
    
2. Select the newly created Log Analytics workspace. And select the **Add** button.
    

The new Microsoft Sentinel workspace is now the active screen. The Microsoft Sentinel left navigation has four areas:

- General
- Threat management
- Content management
- Configuration

The Overview tab displays a standard dashboard of information about the ingested data, alerts, and incidents.

## Interactive Lab Simulation

 Note

Select the thumbnail image to start the lab simulation. When you're done, be sure to return to this page so you can continue learning.

[![Screenshot of the lab simulation page.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/sc-200-lab-simulation-configure-your-microsoft-sentinel-environment.png)](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Configure%20your%20Microsoft%20Sentinel%20environment)

## Microsoft Sentinel sharing a Log Analytics Workspace

Considering that Microsoft Sentinel workspace uses a Log Analytics workspace, you have the option to enable the Microsoft Sentinel workspace in a Log Analytics workspace that is used by other solutions. The most common scenario is sharing the Log Analytics workspace used by Microsoft Defender for Cloud. Sharing the workspace enables one central workspace to query security data.

## Microsoft Defender for Cloud

When creating your Microsoft Sentinel workspace, you aren't allowed to use the **Default** Microsoft Defender for Cloud Log Analytics workspace. You need to manually create a Log Analytics workspace then update the Microsoft Defender for Cloud tier. Now you can select the manually created Log Analytics workspace for use with Microsoft Defender for Cloud.

# Manage workspaces across tenants using Azure Lighthouse

If you're required to manage multiple Microsoft Sentinel workspaces, or workspaces not in your tenant, you have two options:

- Microsoft Sentinel Workspace manager
- Azure Lighthouse

## Microsoft Sentinel Workspace manager

Microsoft Sentinel's Workspace manager enables users to centrally manage multiple Microsoft Sentinel workspaces within one or more Azure tenants. The Central workspace (with Workspace manager enabled) can consolidate content items to be published at scale to Member workspaces. Workspace manager is enabled in the `Configuration settings`.

![Diagram of Microsoft Sentinel Workspace manager architectures.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/microsoft-sentinel-workspace-manager-architectures.png)

## Azure Lighthouse

Implementing Azure Lighthouse provides the option to enable your access to the tenant. Once Azure Lighthouse is onboarded, use the directory + subscription selector on the Azure portal to select all the subscriptions containing workspaces you manage.

![Diagram of multiple tenants managed by Azure Lighthouse.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/azure-delegated-tenant.jpg)

Azure Lighthouse allows greater flexibility to manage resources for multiple customers without having to sign in to different accounts in different tenants. For example, a service provider may have two customers with different responsibilities and access levels. By using Azure Lighthouse, authorized users can sign in to the service provider's tenant to access these resources.

# Understand Microsoft Sentinel permissions and roles
Microsoft Sentinel uses Azure role-based access control (Azure RBAC) to provide built-in roles that can be assigned to users, groups, and services in Azure.

Use Azure RBAC to create and assign roles within your security operations team to grant appropriate access to Microsoft Sentinel. The different roles give you fine-grained control over what users of Microsoft Sentinel can see and do. Azure roles can be assigned in the Microsoft Sentinel workspace directly, or in a subscription or resource group that the workspace belongs to, which Microsoft Sentinel will inherit.

## Microsoft Sentinel-specific roles

All Microsoft Sentinel built-in roles grant read access to the data in your Microsoft Sentinel workspace:

- **Microsoft Sentinel Reader**: can view data, incidents, workbooks, and other Microsoft Sentinel resources.
    
- **Microsoft Sentinel Responder**: can, in addition to the above, manage incidents (assign, dismiss, etc.)
    
- **Microsoft Sentinel Contributor**: can, in addition to the above, create and edit workbooks, analytics rules, and other Microsoft Sentinel resources.
    
- **Microsoft Sentinel Automation Contributor**: allows Microsoft Sentinel to add playbooks to automation rules. It isn't meant for user accounts.
    

For best results, these roles should be assigned to the resource group that contains the Microsoft Sentinel workspace. The roles then apply to all the resources that deploy to support Microsoft Sentinel, if those resources are in the same resource group.

## Additional roles and permissions

Users with particular job requirements may need to be assigned other roles or specific permissions in order to accomplish their tasks.

- Working with playbooks to automate responses to threats
    
    Microsoft Sentinel uses playbooks for automated threat response. Playbooks are built on Azure Logic Apps, and are a separate Azure resource. You might want to assign to specific members of your security operations team the ability to use Logic Apps for Security Orchestration, Automation, and Response (SOAR) operations. You can use the Logic App Contributor role to assign explicit permission for using playbooks.
    
- Giving Microsoft Sentinel permissions to run playbooks
    
    Microsoft Sentinel uses a special service account to run incident-trigger playbooks manually or to call them from automation rules. The use of this account (as opposed to your user account) increases the security level of the service.
    
    In order for an automation rule to run a playbook, this account must be granted explicit permissions to the resource group where the playbook resides. At that point, any automation rule will be able to run any playbook in that resource group. To grant these permissions to this service account, your account must have Owner permissions on the resource groups containing the playbooks.
    
- Connecting data sources to Microsoft Sentinel
    
    For a user to add data connectors, you must assign the user write permissions on the Microsoft Sentinel workspace. Also, note the required other permissions for each connector, as listed on the relevant connector page.
    
- Guest users assigning incidents
    
    If a guest user needs to be able to assign incidents, then in addition to the Microsoft Sentinel Responder role, the user will also need to be assigned the role of Directory Reader. This role isn't an Azure role but a Microsoft Entra role, and that regular (non-guest) users have this role assigned by default.
    
- Creating and deleting workbooks
    
    To create and delete a Microsoft Sentinel workbook, the user requires either the Microsoft Sentinel Contributor role or a lesser Microsoft Sentinel role plus the Azure Monitor role of Workbook Contributor. This role isn't necessary for using workbooks, but only for creating and deleting.
    

## Azure roles and Azure Monitor Log Analytics roles

In addition to Microsoft Sentinel-dedicated Azure RBAC roles, other Azure and Log Analytics Azure RBAC roles can grant a wider set of permissions. These roles include access to your Microsoft Sentinel workspace and other resources.

- Azure roles grant access across all your Azure resources. They include Log Analytics workspaces and Microsoft Sentinel resources:
    
    - Owner
        
    - Contributor
        
    - Reader
        
- Log Analytics roles grant access across all your Log Analytics workspaces:
    
    - Log Analytics Contributor
        
    - Log Analytics Reader
        

For example, a user who is assigned with the Microsoft Sentinel Reader and Azure Contributor (not Microsoft Sentinel Contributor) roles can edit data in Microsoft Sentinel. If you want to only grant permissions to Microsoft Sentinel, you should carefully remove the user's prior permissions. Make sure you don't break any needed permission role for another resource.

## Microsoft Sentinel roles and allowed actions

The following table summarizes the roles and allowed actions in Microsoft Sentinel.

| Roles                                                    | Create and run playbooks | Create and edit workbooks, analytic rules, and other Microsoft Sentinel resources | Manage incidents such as dismissing and assigning | View data incidents, workbooks, and other Microsoft Sentinel resources |
| -------------------------------------------------------- | ------------------------ | --------------------------------------------------------------------------------- | ------------------------------------------------- | ---------------------------------------------------------------------- |
| Microsoft Sentinel Reader                                | No                       | No                                                                                | No                                                | Yes                                                                    |
| Microsoft Sentinel Responder                             | No                       | No                                                                                | Yes                                               | Yes                                                                    |
| Microsoft Sentinel Contributor                           | No                       | Yes                                                                               | Yes                                               | Yes                                                                    |
| Microsoft Sentinel Contributor and Logic App Contributor | Yes                      | Yes                                                                               | Yes                                               | Yes                                                                    |

## Custom roles and advanced Azure RBAC

If the built-in Azure roles don't meet the specific needs of your organization, you can create your own custom roles. Just like built-in roles, you can assign custom roles to users, groups, and service principals for management-group, subscription, and resource-group scopes.

# Manage Microsoft Sentinel settings

Microsoft Sentinel Environment Settings are managed in two areas. In Microsoft Sentinel and in the Log Analytics workspace where Microsoft Sentinel resides. In Microsoft Sentinel, the left navigation has an option for Settings. The Settings includes tabs for Pricing, Settings, and Workspace Settings—the Settings changes over time based on the current and in-preview feature set. Most Microsoft Sentinel Environment settings are managed in the Log Analytics workspace. Other areas within the Microsoft Sentinel portal will transfer you to the Log Analytics portal. An example would be specific data connector configurations that are performed in the log analytics workspace.

## Configure log retention

Data retention at the workspace level can be configured from 30 to 730 days (two years) for all workspaces unless they're using the legacy Free pricing tier. To adjust the retention days, select the workspace settings in the Microsoft Sentinel Settings area. The next screen is in the Log Analytics portal. Select the "Usage and estimated costs" tab. At the top of the page, select the "Retention" button. A window will open, allowing for the adjustment of the retention days.

![Screenshot of setting the data retention.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/retention.png)

# Configure logs
## Configure logs in Microsoft Sentinel workspaces

When configuring your Microsoft Sentinel workspaces, you have to plan for the two data states, the three table plans, and the two primary log tiers.

The two data states are:

- Analytics retention: For monitoring, troubleshooting, and near-real-time analytics
- Long-term retention: A low-cost state, not available in all table plans, but can be accessed through search jobs and restores

[![Diagram that shows analytics and long-term retention in Azure Monitor Logs.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/interactive-auxiliary-retention-log-analytics-workspace.png)](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/interactive-auxiliary-retention-log-analytics-workspace.png#lightbox)

Table plans in a Log Analytics workspace determine the features available for each table and the cost of storing data in that table. You can configure different tables in a workspace to use different plans.

There are three plans in a Log Analytics workspace:

- The **Analytics** plan is suited for continuous monitoring, real-time detection, and performance analytics. This plan makes log data available for interactive multi-table queries and use by features and services for 30 days to two years.
- The **Basic** plan is suited for troubleshooting and incident response. This plan offers discounted ingestion and optimized single-table queries for 30 days.
- The **Auxiliary** plan is suited for low-touch data, such as verbose logs, and data required for auditing and compliance. This plan offers low-cost ingestion and unoptimized single-table queries for 30 days.

![Diagram of different Workspace Tier Types.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/workspace-plan-overview.png)

### Log retention plans in Microsoft Sentinel

For Microsoft Sentinel workspaces connected to Defender, tiering and retention management must be done from the new table management experience in the Defender portal. If you have Basic logs in your workspace, convert them to analytics tier first from Log Analytics Tables experience before you can change tiering or retention from the Defender’s new table management experience.

Important

We recommend that users consider Microsoft Sentinel data lake as the preferred solution for storing secondary and long-term data. Microsoft Sentinel data lake is designed to offer enhanced scalability, flexibility, and integration capabilities for advanced security and compliance scenarios. Microsoft Sentinel data lake is currently in public preview and not yet generally available. We advise users to monitor updates and announcements regarding its availability status.

### Manage data tiers in Microsoft Sentinel

There are two primary tiers in Microsoft Sentinel and a default XDR tier:

- Analytics Tier
- Data lake Tier
- XDR default tier

### Analytics tier

This tier makes data available for alerting, hunting, workbooks, and all Microsoft Sentinel features. It retains data in two states:

- **Analytics retention**: In this "hot" state, data is fully available for real-time analytics - including high-performance queries and analytics rules - and threat hunting. By default, Microsoft Sentinel and Microsoft Defender XDR retain data in this tier for 30 days. You can extend the retention period of all tables to up to two years at a prorated monthly long-term retention charge. You can extend the retention period of Microsoft Sentinel solution tables to 90 days for free.
- **Total retention**: By default, all data in the analytics tier is mirrored to the data lake for the same retention period. You can extend the retention of your data in the lake beyond the analytics retention, for up to 12 years of total retention at a low cost.

### Data lake tier

In this low-cost "cold" tier, Microsoft Sentinel retains your data in the lake only. Data in the data lake tier isn't available for real-time analytics features and threat hunting. However, you can access data in the lake whenever you need it through KQL jobs, analyze trends over time by running scheduled KQL or Spark jobs, and aggregate insights from incoming data at a regular cadence by using summary rules

### XDR default tier

By default, Microsoft Defender XDR retains threat hunting data in the XDR default tier, which includes 30 days of analytics retention, included in the XDR license. This data isn't ingested into the analytics or data lake tiers. You can extend the retention period of supported Defender XDR tables beyond 30 days and ingest the data into the analytics tier.

This diagram shows the retention components of the analytics, data lake, and XDR default tiers, and which table types apply to each tier:

[![Diagram that depicts the analytics and data lake tiers in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/tiers-retention-defender-portal.png)](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/tiers-retention-defender-portal.png#lightbox)

### Which tables can you manage in the Defender portal?

This section describes the table types you can manage in the Defender portal.

[![Screenshot that shows the Table Management screen in the Defender portal.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/view-table-properties-microsoft-defender-portal.png)](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/view-table-properties-microsoft-defender-portal.png#lightbox)

|Table type|Description|Examples|Is in Microsoft Sentinel workspace?|
|---|---|---|---|
|**Microsoft Sentinel**|Built-in tables, including:- Azure tables, such as AzureDiagnostics and SigninLogs. Microsoft Sentinel tables. Supported Defender XDR advanced hunting tables, which are created in your Microsoft Sentinel workspace when you increase the retention period beyond 30 days. See the **XDR** table type for Defender XDR tables that are currently unsupported.|- Azure tables: `AzureDiagnostics`, `SigninLogs`- Microsoft Sentinel tables: `AWSCloudTrail`, `SecurityAlert`- XDR tables: `DeviceEvents`,`AlertInfo`|Yes|
|**Custom**|Tables you create manually or through jobs in your Microsoft Sentinel workspace, including summary rule and search job results tables, and custom data source tables.|Tables with `_CL` or `_SRCH` suffixes.|Yes|
|**XDR**|Tables in the XDR default tier, which have 30 days of analytics retention by default. You can view these tables, but you can't manage them from the Defender portal.|`IdentityInfo`|No|

Note

You can view Basic logs tables in your Microsoft Sentinel workspace from the Defender portal, but you can only currently manage them from your Log Analytics workspace. To manage these tables from the Defender portal, change the table plan from basic to analytics in your Microsoft Sentinel workspace.

### Manage table settings

To view and manage table settings in the Microsoft Defender portal:

1. Select **Microsoft Sentinel** > **Configuration** > **Tables** from the left navigation pane.
    
    The **Table** screen lists all the tables you can manage in the Microsoft Defender portal and the settings of each table.
    
    [![Screenshot that shows the Tables screen in the Defender portal.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/view-table-properties-microsoft-defender-portal.png)](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/view-table-properties-microsoft-defender-portal.png#lightbox)
    
    The workspace column shows the Microsoft Sentinel workspace in which a Microsoft Sentinel or custom table is stored.
    
2. To manage Microsoft Sentinel and custom tables in a different Microsoft Sentinel workspace, select the workspace name at the top left corner of the screen to switch between workspaces.
    
3. Select a table on the **Tables** screen.
    
    This opens the table details side panel with more information about the table, including the table description, tier, and retention details.
    
    [![Screenshot that shows the table details side panel for the CommonSecurityLog table on the Table Management screen in the Defender portal.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/table-management-microsoft-defender-portal.png)](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/table-management-microsoft-defender-portal.png#lightbox)
    
4. Select **Manage table**.
    
    The **Manage table** screen lets you modify the table's retention settings in the current tier, and change the storage tier, if necessary.
    
    [![Screenshot that shows the Manage table screen for the CommonSecurityLog table in the Defender portal.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/manage-table-settings-microsoft-defender-portal.png)](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/manage-table-settings-microsoft-defender-portal.png#lightbox)
    
    - **Analytics tier retention settings**:
        
        - **Analytics retention**: 30 days to two years.
            
        - **Total retention**: Up to 12 years of long-term storage in the data lake. By default, total retention is equal to analytics retention, which means long-term retention isn't applied. To enable long-term retention, set the total retention to a value greater than analytics retention.
            
            Example: To retain six months of data in long-term retention total and 90 days of data in analytics retention, set **Analytics retention** to 90 days and **Total retention** to 180 days.
            
    - **Data lake tier retention settings**: Set **Retention** to a value between 30 days and 12 years.
        
    - **Tier changes**: If necessary, you can change tiers at any time based on your cost management and data usage needs.
        
        Note
        
        Tier changes aren't available for all tables. For example, XDR and Microsoft Sentinel solution tables must be available in the analytics tier because Microsoft security services require the data in these tables for near-real-time analytics.
        
5. Review warnings and messages. These messages help you understand important implications of changing table settings.
    
    For example:
    
    - Increased retention is likely to lead to increased data cost.
    - Changing from the analytics to the data lake tier causes features that rely on analytics data to stop functioning such as:
        - Alerting
        - Advanced hunting
        - Analytics rules
        - Custom detection rules
6. Select **Save** to apply the new settings.
    

### Table support for Basic Logs & KQL language limits

All tables in your Log Analytics are Analytics tables, by default. You can configure particular tables to use Basic Logs. You can't configure a table for Basic Logs if Azure Monitor relies on that table for specific features.

You can currently configure the following tables for Basic Logs:

- All tables created with the Data Collection Rule (DCR)-based custom logs API.
- ContainerLogV2, which Container Insights uses and which include verbose text-based log records.
- AppTraces, which contain freeform log records for application traces in Application Insights.

Queries against Basic Logs are optimized for simple data retrieval using a subset of KQL language, including the following operators:

- where
- extend
- project
- project-away
- project-keep
- project-rename
- project-reorder
- parse
- parse-where

The following KQL isn't supported:

- join
- union
- aggregates (summarize)

![[Pasted image 20261005105033.png]]

![[Pasted image 20261005105053.png]]

![[Pasted image 20261005105112.png]]![[Pasted image 20261005105125.png]]

![[Pasted image 20261005105619.png]]

![[Pasted image 20261005105732.png]]

![[Pasted image 20261005110120.png]]

![[Pasted image 20261005110140.png]]

# Summary and resources
You should have learned how the Microsoft Sentinel provisioning process includes creating a Log Analytics workspace and configuring the Microsoft Sentinel options.

You should now be able to:

- Describe Microsoft Sentinel workspace architecture
- Provision a Microsoft Sentinel workspace
- Manage a Microsoft Sentinel workspace

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)


# Query logs in Microsoft Sentinel

# Introduction

Microsoft Sentinel collects log data that is stored in tables. The Logs page in Microsoft Sentinel provides a user interface to build and view query results using the Kusto Query Language (KQL). KQL is the query language used to perform data analysis to create analytics, workbooks, and perform hunting with Microsoft Sentinel.

You're a Security Operations Analyst working at a company that's implementing Microsoft Sentinel. You must explore the tables available in your workspace. You use the Logs page in Microsoft Sentinel in the [Azure portal](https://portal.azure.com/), and Advanced hunting, and Data lake pages available in the [Defender portal](https://security.microsoft.com/) to write Kusto Query Language (KQL) statements to view data stored in the tables. When you connect log data to the Microsoft Sentinel workspace, the connectors write data to specific tables.

You need to have a basic understanding of the provided tables and their intended purpose. For example, the "SecurityEvents" table is designed for Windows Security Event log data. With this knowledge, you're able to query the required tables to use in your search for malicious activity.

After completing this module, you'll be able to:

- Use the Logs page to view data tables with Microsoft Sentinel
- Query the most used tables using Microsoft Sentinel

## Prerequisites

Basic knowledge of operational concepts such as monitoring, logging, and alerting

Important

[Microsoft Sentinel is generally available in the Microsoft Defender portal](https://security.microsoft.com/), including for customers without Microsoft Defender XDR or an E5 license.

Starting in **July 2026**, all customers using Microsoft Sentinel in the Azure portal will be redirected to the Defender portal and will use Microsoft Sentinel in the Defender portal only. Starting in **July 2025**, many new customers are automatically onboarded and redirected to the Defender portal.

If you're still using Microsoft Sentinel in the Azure portal, we recommend that you start planning your transition to the Defender portal to ensure a smooth transition and take full advantage of the unified security operations experience offered by Microsoft Defender. For more information, see [It’s Time to Move: Retiring Microsoft Sentinel’s Azure portal for greater security](https://techcommunity.microsoft.com/blog/microsoft-security-blog/planning-your-move-to-microsoft-defender-portal-for-all-microsoft-sentinel-custo/4428613).

# Query logs in the logs page
KQL is the language used to query the log data in the Log Analytics workspace. You can enter KQL queries in Microsoft Sentinel and Microsoft Defender. In Microsoft Sentinel onboarded to the Defender portal, you can access the query window from the Advanced hunting page or the Data lake exploration page. In Microsoft Sentinel, in the Azure portal, the Logs page provides access to the query window.

In the [Defender portal](https://security.microsoft.com/), select **Investigation & response** > **Hunting** > **Advanced hunting**, or to run ad-hoc interactive KQL queries on long-term data, select **Microsoft Sentinel** > **Data lake exploration** > **KQL queries**. In the [Azure portal](https://portal.azure.com/), the **Search** page is listed under **General**.

- [Defender portal](https://learn.microsoft.com/en-us/training/modules/query-logs-azure-sentinel/2-query-logs-page?tabs=defender-portal#tabpanel_1_defender-portal)
- [Azure portal](https://learn.microsoft.com/en-us/training/modules/query-logs-azure-sentinel/2-query-logs-page?tabs=defender-portal#tabpanel_1_azure-portal)

For Microsoft Sentinel in the Defender portal, you have several options for running KQL queries. In this unit we cover the two following options:

- Advanced hunting page: The query window allows you to run queries, save queries, run saved queries, create a new alert rule, and export. You can also link a result to an incident. The left side provides a list of tables and related table fields. To run a query, enter the query text and press the run button. Query results appear in the bottom section of the form.
- Data lake exploration page: To run ad-hoc interactive KQL queries on long-term data.

1. To use _Advanced hunting_, select **Investigation & response** > **Hunting** > **Advanced hunting**.
    
    [![Screenshot of the Advanced hunting page in the Defender portal.](https://learn.microsoft.com/en-us/training/wwl-sci/query-logs-azure-sentinel/media/advanced-hunting.png)](https://learn.microsoft.com/en-us/training/wwl-sci/query-logs-azure-sentinel/media/advanced-hunting.png#lightbox)
    
2. To use _Data lake exploration_, select **Microsoft Sentinel** > **Data lake exploration** > **KQL queries**.
    
    [![Screenshot of the Data lake exploration page in the Defender portal.](https://learn.microsoft.com/en-us/training/wwl-sci/query-logs-azure-sentinel/media/data-lake-kql-queries.png)](https://learn.microsoft.com/en-us/training/wwl-sci/query-logs-azure-sentinel/media/data-lake-kql-queries.png#lightbox)
    
3. Select the appropriate workspace from the workspace selector in the top menu.
    
    [![Screenshot of the workspace selector in the Azure portal.](https://learn.microsoft.com/en-us/training/wwl-sci/query-logs-azure-sentinel/media/workspace-selector.png)](https://learn.microsoft.com/en-us/training/wwl-sci/query-logs-azure-sentinel/media/workspace-selector.png#lightbox)

# Understand Microsoft Sentinel tables
Microsoft Sentinel has Analytic Rules that generate Alerts and Incidents based on querying the tables within Log Analytics. The primary tables to manage alerts and incidents are SecurityAlert and SecurityIncident. Microsoft Sentinel provides tables to be a repository of indicators and watchlists.

Note

Some of the Sentinel Data Connectors ingest alerts directly.

The table below is the Microsoft Sentinel feature related tables.

|Table|Description|
|---|---|
|`SecurityAlert`|Contains Alerts Generated from Sentinel Analytical Rules. Also, it could include Alerts created directly from a Sentinel Data Connector|
|`SecurityIncident`|Alerts can generate Incidents. Incidents are related to Alert(s).|
|`ThreatIntelligenceIndicator`|Contains user-created or data connector ingested Indicators such as File Hashes, IP Addresses, Domains|
|`Watchlist`|A Microsoft Sentinel watchlist contains imported data.|

# Understand common tables
When Sentinel ingests data from the Data Connectors, the following table lists the most commonly used tables.

|Table|Description|
|---|---|
|`AzureActivity`|Entries from the Azure Activity log that provides insight into any subscription-level or management group level events that occurred in Azure.|
|`AzureDiagnostics`|Stores resource logs for Azure services that use Azure Diagnostics mode. Resource logs describe the internal operation of Azure resources.|
|`AuditLogs`|Audit log for Microsoft Entra ID. Includes system activity information about user and group management, managed applications, and directory activities.|
|`CommonSecurityLog`|Syslog messages using the Common Event Format (CEF).|
|`McasShadowItReporting`|Microsoft Defender for Cloud Apps logs|
|`OfficeActivity`|Audit logs for Office 365 tenants collected by Microsoft Sentinel. Including Exchange, SharePoint and Teams logs.|
|`SecurityEvent`|Security events collected from windows machines by Azure Security Center or Microsoft Sentinel|
|`SigninLogs`|Azure Activity Directory Sign-in logs|
|`Syslog`|Syslog events on Linux computers using the Log Analytics agent.|
|`Event`|Sysmon Events collected from a Windows host.|
|`WindowsFirewall`|Windows Firewall Events|

# Understand Microsoft Defender XDR tables
The Microsoft Defender XDR Sentinel Data Connector can populate tables with raw data collected from the Microsoft Defender XDR solutions.

|Table name|Description|
|---|---|
|`AlertEvidence`|Files, IP addresses, URLs, users, or devices associated with alerts|
|`CloudAppEvents`|Events involving accounts and objects in Office 365 and other cloud apps and services|
|`DeviceEvents`|Multiple event types, including events triggered by security controls such as Windows Defender Antivirus and exploit protection|
|`DeviceFileCertificateInfo`|Certificate information of signed files obtained from certificate verification events on endpoints|
|`DeviceFileEvents`|File creation, modification, and other file system events|
|`DeviceImageLoadEvents`|DLL loading events|
|`DeviceInfo`|Machine information, including OS information|
|`DeviceLogonEvents`|Sign-ins and other authentication events on devices|
|`DeviceNetworkEvents`|Network connection and related events|
|`DeviceNetworkInfo`|Network properties of devices, including physical adapters, IP and MAC addresses, as well as connected networks and domains|
|`DeviceProcessEvents`|Process creation and related events|
|`DeviceRegistryEvents`|Creation and modification of registry entries|
|`EmailEvents`|Microsoft 365 email events, including email delivery and blocking events|
|`EmailPostDeliveryEvents`|Security events that occur post-delivery, after Microsoft 365 has delivered the emails to the recipient mailbox|
|`EmailUrlInfo`|Information about URLs on emails|
|`EmailAttachmentInfo`|Information about files attached to Office 365 emails|
|`IdentityDirectoryEvents`|Events involving an on-premises domain controller running Active Directory (AD). This table covers a range of identity-related events and system events on the domain controller.|
|`IdentityLogonEvents`|Authentication events on Active Directory and Microsoft online services|
|`IdentityQueryEvents`|Queries for Active Directory objects, such as users, groups, devices, and domains|
![[Pasted image 20261005111736.png]]

# Summary and resources
You should have a basic understanding of the provided tables and their intended purpose in Microsoft Sentinel.

You should now be able to:

- Use the Logs page to view tables with Microsoft Sentinel
- Query the most used tables with Microsoft Sentinel

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)


# Use watchlists in Microsoft Sentinel
# Introduction
Microsoft Sentinel provides a table to store list data accessible to Kusto Query Language (KQL) queries. The Watchlists page in Microsoft Sentinel provides the management options to maintain the lists.

You're a Security Operations Analyst working at a company that deployed Microsoft Sentinel. The Security Operations team members need to prioritize alerts that are impacting high-value target servers.

You must import a list of server names into Microsoft Sentinel, which is used by detection queries to set a priority field. You import a list of servers into the Watchlist page of Microsoft Sentinel. Once created, you instruct the Security Operations team to use the watch list in their KQL queries.

After completing this module, you'll be able to:

- Create a watchlist with Microsoft Sentinel
- Use KQL to access the watchlist with Microsoft Sentinel

# Plan for watchlists
Microsoft Sentinel watchlists enable collecting data from external data sources for correlation with the events in your Microsoft Sentinel environment. Once created, you can use watchlists in your search, detection rules, threat hunting, and response playbooks. Watchlists are stored in your Microsoft Sentinel workspace as name-value pairs and are cached for optimal query performance and low latency.

Common scenarios for using watchlists include:

- Investigating threats and responding to incidents quickly with the rapid import of IP addresses, file hashes, and other data from CSV files. Once imported, you can use watchlist name-value pairs for joins and filters in alert rules, threat hunting, workbooks, notebooks, and general queries.
    
- Importing business data as a watchlist. For example, import user lists with privileged system access, or terminated employees, and then use the watchlist to create allowlists and blocklists used to detect or prevent those users from logging in to the network.
    
- Reducing alert fatigue. Create allowlists to suppress alerts from a group of users, such as users from authorized IP addresses that perform tasks that would normally trigger the alert, and prevent benign events from becoming alerts.
    
- Enriching event data. Use watchlists to enrich your event data with name-value combinations derived from external data sources.

# Create a watchlist
To create a watchlist from the Azure portal perform these steps:

1. Go to **Microsoft Sentinel > Configuration > Watchlist** and select **Add new**.
    
    ![Screen shot of creating a Microsoft Sentinel Watchlist List.](https://learn.microsoft.com/en-us/training/wwl-sci/use-watchlists-azure-sentinel/media/watchlist-create.png)
    
2. On the General page, provide the name, description, and alias for the watchlist, then select **Next**.
    
3. On the Source page, select the dataset type, upload a file, then select **Next**.
    
    Note
    
    File uploads are currently limited to files of up to 3.8 MB in size.
    
4. Review the information, and verify that it's correct. Then select **Create**. A notification appears once the watchlist is ready.
    

To use the watchlist data in KQL, use the KQL function _GetWatchlist('watchlist name').

Kusto

```
_GetWatchlist('HighValueMachines')

```

# Manage watchlists
We recommend you edit an existing watchlist instead of deleting and recreating a watchlist. Log analytics has a five-minute SLA (Service Level Agreement) for data ingestion. If you delete and recreate a watchlist, you might see both the deleted and recreated entries in Log Analytics during this five-minute window. If you see these duplicate entries in Log Analytics for a longer period of time, submit a support ticket.

## Edit a watchlist item

Edit a watchlist to edit or add an item to the watchlist.

1. In the Azure portal, go to Microsoft Sentinel and select the appropriate workspace.
    
2. Under Configuration, select **Watchlist**.
    
3. Select the watchlist you want to edit.
    
4. On the details pane, select **Update watchlist > Edit watchlist items**.
    
5. To edit an existing watchlist item,
    
    1. Select the checkbox of that watchlist item.
        
    2. Edit the item.
        
    3. Select Save.
        
    4. Select Yes at the confirmation prompt.
        
6. To add a new item to your watchlist,
    
    1. Select Add new.
        
    2. Fill in the fields in the Add watchlist item panel.
        
    3. At the bottom of that panel, select Add.
        

## Bulk update a watchlist

When you have many items to add to a watchlist, use bulk update. A bulk update of a watchlist appends items to the existing watchlist. Then, it deduplicates the items in the watchlist where all the value in each column match.

If you deleted an item from your watchlist file and upload it, bulk update won't delete the item in the existing watchlist. Delete the watchlist item individually. Or, when you have many deletions, delete and recreate the watchlist.

The updated watchlist file you upload must contain the search key field used by the watchlist with no blank values.

To bulk update a watchlist,

1. In the Azure portal, go to Microsoft Sentinel and select the appropriate workspace.
    
2. Under Configuration, select **Watchlist**.
    
3. Select the watchlist you want to edit.
    
4. On the details pane, select **Update watchlist > Bulk update**.
    
5. Under Upload file, drag and drop or browse to the file to upload.
    
6. If you get an error, fix the issue in the file. Then select Reset and try the file upload again.
    
7. Select **Next: Review and update > Update**.
![[Pasted image 20261005112809.png]]

# Summary and resources
You learned how Microsoft Sentinel provides a table to store list data accessible to Kusto Query Language (KQL) queries. And that the Watchlists page in Microsoft Sentinel provides the management options to maintain the lists.

You should now be able to:

- Create a watchlist with Microsoft Sentinel
- Use KQL to access the watchlist with Microsoft Sentinel


# Utilize threat intelligence in Microsoft Sentinel

# Introduction
Microsoft Sentinel provides a table to store indicator data accessible to Kusto Query Language (KQL) queries. The Threat intelligence page in Microsoft Sentinel provides the management options to maintain the indicators.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You receive threat indicators from threat intelligence providers and your threat hunting team. The Indicators include IP addresses, domains, and file hashes that can be utilized by many components within Microsoft Sentinel.

The indicators from the threat intelligence providers are automatically imported into the workspace using connectors. You're tasked with adding the indicators from the threat hunting team. You use the Threat Intelligence page to add the indicators for use by the detection KQL queries.

After completing this module, you'll be able to:

- Manage threat indicators in Microsoft Sentinel
- Use KQL to access threat indicators in Microsoft Sentinel


# Define threat intelligence
Cyber threat intelligence (CTI) can come from many sources. Sources include open-source data feeds, threat intelligence-sharing communities, paid intelligence feeds, and security investigations within organizations. CTI can range from written reports on a threat actor's motivations, infrastructure, and techniques, to specific observations of IP addresses, domains, and file hashes. CTI provides essential context for unusual activity, so security personnel can act quickly to protect people and assets.

The most utilized CTI in SIEM solutions like Microsoft Sentinel is threat indicator data, sometimes called Indicators of Compromise (IoCs). Threat indicators associate URLs, file hashes, IP addresses, and other data with known threat activity like phishing, botnets, or malware. This form of threat intelligence is often called tactical threat intelligence, because security products and automation can use it in large scale to protect and detect potential threats. Microsoft Sentinel can help detect, respond to, and provide CTI context for malicious cyber activity.

You can integrate threat intelligence (TI) into Microsoft Sentinel through the following activities:

- Use Data connectors to various TI platforms to import threat intelligence into Microsoft Sentinel.
    
- View and manage the imported threat intelligence in Logs and the new Threat Intelligence area of Microsoft Sentinel.
    
- Use the built-in Analytics rule templates to generate security alerts and incidents using your imported threat intelligence.
    
- Visualize critical information about your threat intelligence in Microsoft Sentinel with the Threat Intelligence workbook.
    
- Perform threat hunting with your imported threat intelligence.
    

![Screenshot of Threat Intelligence uses in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/utilize-threat-intelligence-azure-sentinel/media/sentinel-data-flow.png)

# Manage your threat indicators
With the Threat Intelligence area, accessible from the Microsoft Sentinel menu, you can also view, sort, filter, and search your imported threat indicators without even writing a Logs query. This area also allows you to create threat indicators directly within the Microsoft Sentinel interface and perform everyday threat intelligence administrative tasks. These tasks include indicator tagging and creating new indicators related to security investigations. Let's look at two of the most common tasks, creating new threat indicators and tagging indicators for easy grouping and reference.

- [Defender portal](https://learn.microsoft.com/en-us/training/modules/utilize-threat-intelligence-azure-sentinel/3-manage-threat-indicators?tabs=defender-portal#tabpanel_1_defender-portal)
- [Azure portal](https://learn.microsoft.com/en-us/training/modules/utilize-threat-intelligence-azure-sentinel/3-manage-threat-indicators?tabs=defender-portal#tabpanel_1_azure-portal)

1. Open the [Defender portal](https://security.microsoft.com/) and navigate to Microsoft Sentinel.
    
2. From the **Threat management** section of the Microsoft Sentinel menu, select **Threat intelligence**.
    
3. If you see the _This page has a new home_ message. Select the **Open Intel management** button.
    
    ![Screenshot of the this page has a new home message for Threat Intelligence in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/utilize-threat-intelligence-azure-sentinel/media/threat-intelligence-new-home.png)
    
4. You're redirected to the _Intel management_ page under the _Threat Intelligence_ section of the Defender portal navigation menu.
    
    ![Screenshot of the Defender Intel management page.](https://learn.microsoft.com/en-us/training/wwl-sci/utilize-threat-intelligence-azure-sentinel/media/intel-management.png)
    
    Tip
    
    As the _Threat intelligence_ capabilities in Microsoft Sentinel are being consolidated into the Defender portals _Threat intelligence_ section, you can go directly to _Intel management_ from there.
    
5. On the Select the **Add new** button from the top menu of the page.
    
6. Choose the indicator type, then complete the required fields marked with a red asterisk (*) on the New indicator panel. Select **Apply**.
    

Tagging threat indicators is an easy way to group them to make them easier to find. Typically, you might apply a tag to indicators related to a particular incident or indicators representing threats from a known actor or a well-known attack campaign. You can tag threat indicators individually or multi-select indicators and tag them all at once. Since tagging is free-form, a recommended practice is to create standard naming conventions for threat indicator tags. You can apply multiple tags to each indicator.


# View your threat indicators with KQL
The indicators reside in the _ThreatIntelligenceIndicator_ table. This table is the basis for queries performed by other Microsoft Sentinel features such as Analytics and Workbooks. Here's how to find and view your threat indicators in the ThreatIntelligenceIndicator table.

To view your threat indicators with KQL. Select **Logs** from the General section of the Microsoft Sentinel menu. Then run a query on the ThreatIntelligenceIndicator table.

Kusto

```
`ThreatIntelligenceIndicator`

```

Important

On April 3, 2025, we publicly previewed two new tables to support STIX indicator and object schemas: `ThreatIntelIndicators` and `ThreatIntelObjects`. Microsoft Sentinel will ingest all threat intelligence into these new tables, while continuing to ingest the same data into the legacy `ThreatIntelligenceIndicator` table until July 31, 2025. **Be sure to update your custom queries, analytics and detection rules, workbooks, and automation to use the new tables by July 31, 2025.** After this date, Microsoft Sentinel will stop ingesting data to the legacy `ThreatIntelligenceIndicator` table. We're updating all out-of-the-box threat intelligence solutions in Content hub to leverage the new tables. For more information about the new table schemas, see [ThreatIntelIndicators](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/threatintelindicators) and [ThreatIntelObjects](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/threatintelobjects).

![[Pasted image 20261005113939.png]]

# Summary and resources
You should have learned how Microsoft Sentinel provides a table to store indicator data accessible to Kusto Query Language (KQL) queries. And how the Threat intelligence page in Microsoft Sentinel provides the management options to maintain the indicators.

You should now be able to:

- Manage threat indicators in Microsoft Sentinel
- Use KQL to access threat indicators in Microsoft Sentinel

# Integrate Microsoft Defender XDR with Microsoft Sentinel

# Introduction
This module covers the topic of Microsoft Sentinel's integration into the Microsoft Defender portal. This integration simplifies operations by reducing the need for managing multiple tools and enhances hunting capabilities by allowing queries across different data sets from a single portal.

Imagine you're a security Operations Manager in a large multinational corporation. You're tasked with streamlining your team's operations and enhancing their hunting capabilities. Your team currently uses multiple tools for different tasks, which often lead to complexity and errors. You also want to enable automatic attack disruption for your SAP applications and provide unified entity pages for devices, users, IP addresses, and Azure resources. The solution lies in integrating Microsoft Sentinel into the Microsoft Defender portal.

Note

If you onboard Microsoft Sentinel to the Defender portal and are licensed for Defender XDR, Microsoft Sentinel is automatically connected to Defender XDR. The data connector for Defender XDR is automatically set up for you.

The topics covered in this module include:

- Understanding the Integration of Microsoft Sentinel and Defender XDR in the Defender Portal
- Understanding Capability Differences between Azure and Defender Portals in Microsoft Sentinel
- Onboarding Microsoft Sentinel to Microsoft Defender XDR: Prerequisites and Steps
- Navigating Microsoft Sentinel Features in the Defender Portal

## Learning objectives

By the end of this module, you're able to:

- Understand the differences between Microsoft Sentinel capabilities in Azure and Defender portals.
- Know the prerequisites for integrating Microsoft Defender XDR with Microsoft Sentinel.
- Connect a Microsoft Sentinel workspace to Microsoft Defender XDR.

## Prerequisites

- Familiarity with security operations in an organization
- Experience installing and configuring Microsoft Sentinel services
- Experience with using and navigating the Microsoft Defender portal

# Understand the benefits of integrating Microsoft Sentinel with Defender XDR
Microsoft Sentinel is now generally available in the Microsoft Defender portal. The following benefits and new or improved capabilities are available in the Defender portal with the integration of Microsoft Sentinel and Defender XDR.

## Microsoft Sentinel integration with Microsoft Defender XDR

Use one of the following methods to integrate Microsoft Sentinel with Microsoft Defender XDR services:

- Ingest Microsoft Defender XDR service data into Microsoft Sentinel and view Microsoft Sentinel data in the Azure portal. Enabled by installing the Defender XDR connector in Microsoft Sentinel.
    
- Integrate Microsoft Sentinel and Defender XDR into a single portal. In this case, view Microsoft Sentinel data directly in the Microsoft Defender portal with the rest of your Defender incidents, alerts, vulnerabilities, and other security data. Enabled by installing the Defender XDR connector in Microsoft Sentinel and then onboarding Microsoft Sentinel to the unified operations platform in the Defender portal.
    

Select the appropriate tab to see what the Microsoft Sentinel integration with Defender XDR looks like depending on which integration method you use.

- [Azure portal](https://learn.microsoft.com/en-us/training/modules/integrate-microsoft-defender-xdr-with-microsoft-sentinel/2-benefits-of-integration?tabs=azure-portal#tabpanel_1_azure-portal)
- [Defender portal](https://learn.microsoft.com/en-us/training/modules/integrate-microsoft-defender-xdr-with-microsoft-sentinel/2-benefits-of-integration?tabs=azure-portal#tabpanel_1_defender-portal)

The following illustration shows how Microsoft's XDR solution seamlessly integrates with Microsoft Sentinel.

[![Diagram of Microsoft Sentinel in Azure and in Microsoft Defender XDR.](https://learn.microsoft.com/en-us/training/wwl-sci/integrate-microsoft-defender-xdr-with-microsoft-sentinel/media/sentinel-xdr.png)](https://learn.microsoft.com/en-us/training/wwl-sci/integrate-microsoft-defender-xdr-with-microsoft-sentinel/media/sentinel-xdr.png#lightbox)

In this diagram:

- Insights from signals across your entire organization feed into Microsoft Defender XDR and Microsoft Defender for Cloud.
- Microsoft Defender XDR and Microsoft Defender for Cloud send SIEM log data through Microsoft Sentinel connectors.
- SecOps teams can then analyze and respond to threats identified in Microsoft Sentinel and Microsoft Defender XDR.
- Microsoft Sentinel provides support for multicloud environments and integrates with third-party apps and partners.


# Explore the capability differences between Microsoft Defender XDR and Microsoft Sentinel portals
Most Microsoft Sentinel capabilities are available in both the Azure and Defender portals. In the Defender portal, some Microsoft Sentinel experiences open out to the Azure portal for you to complete a task.

This section covers the Microsoft Sentinel capabilities or integrations in Microsoft Defender that are only available in either the Azure portal or Defender portal or other significant differences between the portals. It excludes the Microsoft Sentinel experiences that open the Azure portal from the Defender portal.

### Capability differences between portals

|Capability|Availability|Description|
|---|---|---|
|Advanced hunting using bookmarks|Azure portal only|Bookmarks aren't supported in the advanced hunting experience in the Microsoft Defender portal. In the Defender portal, they're supported in the **Microsoft Sentinel > Threat management > Hunting**.|
|Attack disruption for SAP|Defender portal only|This functionality is unavailable in the Azure portal.|
|Automation|Some automation procedures are available only in the Azure portal. And Other automation procedures are the same in the Defender and Azure portals.|The differences in the Azure portal are between workspaces that are onboarded to the Microsoft Defender portal and workspaces that aren't.|
|Data connectors: visibility of connectors used by Microsoft Defender|Azure portal only|In the Defender portal, after you onboard Microsoft Sentinel, the following data connectors that are part of Microsoft Defender aren't shown in the **Data connectors** page:- Microsoft Defender for Cloud Apps<br>- Microsoft Defender for Endpoint<br>- Microsoft Defender for Identity<br>- Microsoft Defender for Office 365 (Preview)<br>- Microsoft Defender XDR<br>- Subscription-based Microsoft Defender for Cloud (Legacy)<br>- Tenant-based Microsoft Defender for Cloud (Preview)  <br>      <br>    In the Azure portal, these data connectors are still listed with the installed data connectors in Microsoft Sentinel.|
|Entities: Add entities to threat intelligence from incidents|Azure portal only|This functionality is unavailable in the Microsoft Defender portal.|
|Fusion: Advanced multistage attack detection|Azure portal only|The Fusion analytics rule, which creates incidents based on alert correlations made by the Fusion correlation engine, is disabled when you onboard Microsoft Sentinel to Microsoft Defender.  <br>  <br>Microsoft Defender uses Microsoft Defender XDR's incident-creation and correlation functionalities to replace those of the Fusion engine.|
|Incidents: Adding alerts to incidents /  <br>Removing alerts from incidents|Defender portal only|After onboarding Microsoft Sentinel to the Microsoft Defender portal, you can no longer add alerts to, or remove alerts from, incidents in the Azure portal.  <br>  <br>You can remove an alert from an incident in the Defender portal, but only by linking the alert to another incident (existing or new).|
|Incidents: editing comments|Azure portal only|After onboarding Microsoft Sentinel to the Microsoft Defender portal, you can add comments to incidents in either portal, but you can't edit existing comments.  <br>  <br>Edits made to comments in the Azure portal don't synchronize to the Microsoft Defender portal.|
|Incidents: Programmatic and manual creation of incidents|Azure portal only|Incidents created in Microsoft Sentinel through the API, by a Logic App playbook, or manually from the Azure portal, aren't synchronized to the Microsoft Defender portal. These incidents are still supported in the Azure portal and the API.|
|Incidents: Reopening closed incidents|Azure portal only|In the Microsoft Defender portal, you can't set alert grouping in Microsoft Sentinel analytics rules to reopen closed incidents if new alerts are added.  <br>Closed incidents aren't reopened in this case, and new alerts trigger new incidents.|
|Incidents: Tasks|Azure portal only|Tasks are unavailable in the Microsoft Defender portal.|
|Multiple workspace management for Microsoft Sentinel|Defender portal: Limited to one primary Microsoft Sentinel workspace  <br>  <br>Azure portal: Centrally manage multiple Microsoft Sentinel workspaces for tenants|Only one primary Microsoft Sentinel workspace can be connected in the Microsoft Defender portal. So, Microsoft Defender multitenant management supports one primary Microsoft Sentinel workspace per tenant.|

For more information, see [Capability differences between portals](https://learn.microsoft.com/en-us/azure/sentinel/microsoft-sentinel-defender-portal?toc=%2Fdefender-xdr%2Ftoc.json&bc=%2Fdefender-xdr%2Fbreadcrumb%2Ftoc.json)

# Onboarding Microsoft Sentinel to Microsoft Defender XDR
Now that you understand the benefits of integrating Microsoft Defender XDR with Microsoft Sentinel, and know the capability differences, you can onboard Microsoft Sentinel to Microsoft Defender XDR.

But, before you begin, make sure you have completed the following steps and have the resources and access required.

## Prerequisites

The Microsoft Defender portal supports a single Microsoft Entra tenant and the connection to a primary workspace and multiple secondary workspaces. In the context of this article, a workspace is a Log Analytics workspace with Microsoft Sentinel enabled.

To onboard and use Microsoft Sentinel in the Microsoft Defender portal, you must have the following resources and access:

- A Log Analytics workspace that has Microsoft Sentinel enabled
- The data connector for Microsoft Defender XDR (formerly named Microsoft 365 Defender) enabled in Microsoft Sentinel for incidents and alerts. For more information, see [Connect data from Microsoft Defender XDR to Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender).
- Access to Microsoft Defender XDR in the Defender portal
- Microsoft Defender XDR onboarded to the Microsoft Entra tenant
- An Azure account with the appropriate roles to onboard, use, and create support requests for Microsoft Sentinel in the Defender portal. The following table highlights some of the key roles needed.

| Task                                                              | Azure built-in role required                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Scope                                                                                                                                                           |
| ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Connect or disconnect a workspace with Microsoft Sentinel enabled | [Owner](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#owner) or  <br>[User Access Administrator](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#user-access-administrator) and [Microsoft Sentinel Contributor](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#microsoft-sentinel-contributor)                                                                                                                                                                                                                                                                                                                                                                 | - Subscription for Owner or User Access Administrator roles  <br>  <br>- Subscription, resource group, or workspace resource for Microsoft Sentinel Contributor |
| View Microsoft Sentinel in the Defender portal                    | [Microsoft Sentinel Reader](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#microsoft-sentinel-reader)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Subscription, resource group, or workspace resource                                                                                                             |
| Query Sentinel data tables or view incidents                      | [Microsoft Sentinel Reader](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#microsoft-sentinel-reader) or a role with the following actions:  <br>- Microsoft.OperationalInsights/workspaces/read  <br>- Microsoft.OperationalInsights/workspaces/query/read  <br>- Microsoft.SecurityInsights/Incidents/read  <br>- Microsoft.SecurityInsights/incidents/comments/read  <br>- Microsoft.SecurityInsights/incidents/relations/read  <br>- Microsoft.SecurityInsights/incidents/tasks/read                                                                                                                                                                                                                                            | Subscription, resource group, or workspace resource                                                                                                             |
| Take investigative actions on incidents                           | [Microsoft Sentinel Contributor](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#microsoft-sentinel-contributor) or a role with the following actions:  <br>- Microsoft.OperationalInsights/workspaces/read  <br>- Microsoft.OperationalInsights/workspaces/query/read  <br>- Microsoft.SecurityInsights/incidents/read  <br>- Microsoft.SecurityInsights/incidents/write  <br>- Microsoft.SecurityInsights/incidents/comments/read  <br>- Microsoft.SecurityInsights/incidents/comments/write  <br>- Microsoft.SecurityInsights/incidents/relations/read  <br>- Microsoft.SecurityInsights/incidents/relations/write  <br>- Microsoft.SecurityInsights/incidents/tasks/read  <br>- Microsoft.SecurityInsights/incidents/tasks/write | Subscription, resource group, or workspace resource                                                                                                             |
| Create a support request                                          | [Owner](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#owner) or  <br>[Contributor](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#contributor) or  <br>[Support request contributor](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#support-request-contributor) or a custom role with Microsoft.Support/*                                                                                                                                                                                                                                                                                                                                                     | Subscription                                                                                                                                                    |

After you connect Microsoft Sentinel to the Defender portal, your existing Azure role-based access control (RBAC) permissions allow you to work with the Microsoft Sentinel features that you have access to. Continue to manage roles and permissions for your Microsoft Sentinel users from the Azure portal. Any Azure RBAC changes are reflected in the Defender portal. For more information about Microsoft Sentinel permissions, see [Roles and permissions in Microsoft Sentinel | Microsoft Learn](https://learn.microsoft.com/en-us/azure/sentinel/roles) and [Manage access to Microsoft Sentinel data by resource | Microsoft Learn](https://learn.microsoft.com/en-us/azure/sentinel/resource-context-rbac).

## Onboard Microsoft Sentinel

How you integrate Defender XDR depends on whether you plan to onboard Microsoft Sentinel to the Defender portal or continue to work in the Azure portal. If you want to sync Defender XDR data to Microsoft Sentinel in the Azure portal, you must enable the Microsoft Defender XDR connector in Microsoft Sentinel. To connect a workspace to Defender XDR, complete the following steps:

Important

Before you connect your workspace, make sure you installed the **Microsoft Defender XDR** solution for Microsoft Sentinel from the **Content hub**. And then, enabled the **Microsoft Defender XDR** data connector to collect incidents and alerts.

[![Screen shot of the Get your SIEM and XDR in one place banner message.](https://learn.microsoft.com/en-us/training/wwl-sci/integrate-microsoft-defender-xdr-with-microsoft-sentinel/media/defender-xdr-connect-sentinel-workspace.png)](https://learn.microsoft.com/en-us/training/wwl-sci/integrate-microsoft-defender-xdr-with-microsoft-sentinel/media/defender-xdr-connect-sentinel-workspace.png#lightbox)

1. Go to the [Microsoft Defender portal](https://security.microsoft.com/) and sign in.
    
2. In Microsoft Defender XDR, select **Home** (Overview).
    
3. Select **Connect a workspace** in the _Get your SIEM and XDR in one place_ banner.
    
4. Choose the workspace you want to connect and select **Next**.
    
5. Read and understand the product changes associated with connecting your workspace. These changes include:
    
    - Log tables, queries, and functions in the Microsoft Sentinel workspace are also available in advanced hunting within Defender XDR.
    - The Microsoft Sentinel Contributor role is assigned to the Microsoft Threat Protection and WindowsDefenderATP apps within the subscription.
    - Active [Microsoft security incident creation rules](https://learn.microsoft.com/en-us/azure/sentinel/threat-detection#microsoft-security-rules) are deactivated to avoid duplicate incidents. This change only applies to incident creation rules for Microsoft alerts and not to other analytics rules.
    - All alerts related to Defender XDR products are streamed directly from the main Defender XDR data connector to ensure consistency. Make sure you have incidents and alerts from this connector turned on in the workspace.
6. Select **Connect**.
    

After your workspace is connected, the banner on the **Home** (Overview) page shows that your unified security information and event management (SIEM) and extended detection and response (XDR) is ready. The **Home** page is updated with new sections that include metrics from Microsoft Sentinel like the number of data connectors and automation rules.

[![Screen shot of Microsoft Sentinel onboarded to Defender XDR.](https://learn.microsoft.com/en-us/training/wwl-sci/integrate-microsoft-defender-xdr-with-microsoft-sentinel/media/onboarded-defender-portal.png)](https://learn.microsoft.com/en-us/training/wwl-sci/integrate-microsoft-defender-xdr-with-microsoft-sentinel/media/onboarded-defender-portal.png#lightbox)

## Offboard Microsoft Sentinel

You can only have one workspace connected to the Defender portal at a time. If you want to connect to a different workspace that has Microsoft Sentinel enabled, disconnect the current workspace and connect the other workspace.

1. Go to the [Microsoft Defender portal](https://security.microsoft.com/) and sign in.
    
2. In the Defender portal, under **System**, select **Settings** > **Microsoft Sentinel**.
    
3. On the **Workspaces** page, select the connected workspace and **Disconnect workspace**.
    
4. Provide a reason why you're disconnecting the workspace.
    
5. Confirm your selection.
    
    When your workspace is disconnected, the **Microsoft Sentinel** section is removed from the left-hand side navigation of the Defender portal. Data from Microsoft Sentinel is no longer included on the Overview page.
    

If you want to connect to a different workspace, from the **Workspaces** page, select the workspace and **Connect a workspace**.


# Explore Microsoft Sentinel features in Microsoft Defender XDR
## Explore Microsoft Sentinel features in the Defender portal

After you connect your workspace to the Defender portal, **Microsoft Sentinel** is on the left-hand side navigation pane. Pages like **Overview**, **Incidents**, and **Advanced Hunting** have unified data from Microsoft Sentinel and Defender XDR. For more information about the unified capabilities and differences between portals, see [Microsoft Sentinel in the Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2263690).

Many of the existing Microsoft Sentinel features are integrated into the Defender portal. For these features, notice that the experience between Microsoft Sentinel in the Azure portal and Defender portal are similar. Use the following articles to help you start working with Microsoft Sentinel in the Defender portal. When using these articles, keep in mind that your starting point in this context is the [Defender portal](https://security.microsoft.com/) instead of the Azure portal.

- Search
    - [Search across long time spans in large datasets](https://learn.microsoft.com/en-us/azure/sentinel/search-jobs?tabs=defender-portal)
    - [Restore archived logs from search](https://learn.microsoft.com/en-us/azure/sentinel/restore)
- Threat management
    - [Visualize and monitor your data by using workbooks](https://learn.microsoft.com/en-us/azure/sentinel/monitor-your-data?tabs=defender-portal)
    - [Conduct end-to-end threat hunting with Hunts](https://learn.microsoft.com/en-us/azure/sentinel/hunts)
    - [Use hunting bookmarks for data investigations](https://learn.microsoft.com/en-us/azure/sentinel/bookmarks)
    - [Use hunting Livestream in Microsoft Sentinel to detect threat](https://learn.microsoft.com/en-us/azure/sentinel/livestream)
    - [Hunt for security threats with Jupyter notebooks](https://learn.microsoft.com/en-us/azure/sentinel/notebooks-hunt)
    - [Add indicators in bulk to Microsoft Sentinel threat intelligence from a CSV or JSON file](https://learn.microsoft.com/en-us/azure/sentinel/indicators-bulk-file-import?tabs=defender-portal)
    - [Work with threat indicators in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/work-with-threat-indicators?tabs=defender-portal)
    - [Understand security coverage by the MITRE ATT&CK framework](https://learn.microsoft.com/en-us/azure/sentinel/mitre-coverage)
- Content management
    - [Discover and manage Microsoft Sentinel out-of-the-box content](https://learn.microsoft.com/en-us/azure/sentinel/sentinel-solutions-deploy?tabs=defender-portal)
    - [Microsoft Sentinel content hub catalog](https://learn.microsoft.com/en-us/azure/sentinel/sentinel-solutions-catalog)
    - [Deploy custom content from your repository](https://learn.microsoft.com/en-us/azure/sentinel/ci-cd)
- Configuration
    - [Find your Microsoft Sentinel data connector](https://learn.microsoft.com/en-us/azure/sentinel/data-connectors-reference)
    - [Create custom analytics rules to detect threats](https://learn.microsoft.com/en-us/azure/sentinel/create-analytics-rules?tabs=defender-portal)
    - [Work with near-real-time (NRT) detection analytics rules in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/create-nrt-rules?tabs=defender-portal)
    - [Create watchlists](https://learn.microsoft.com/en-us/azure/sentinel/watchlists-create?tabs=defender-portal)
    - [Manage watchlists in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/watchlists-manage)
    - [Create automation rules](https://learn.microsoft.com/en-us/azure/sentinel/create-manage-use-automation-rules)
    - [Create and customize Microsoft Sentinel playbooks from content templates](https://learn.microsoft.com/en-us/azure/sentinel/use-playbook-templates)

Find Microsoft Sentinel settings in the Defender portal under **System** > **Settings** > **Microsoft Sentinel**.

## Quick reference

Some Microsoft Sentinel capabilities, like the unified incident queue, are integrated with Microsoft Defender XDR in the Microsoft Defender portal. Many other Microsoft Sentinel capabilities are available in the **Microsoft Sentinel** section of the Defender portal.

The following image shows the **Microsoft Sentinel** menu in the Defender portal:

[![Screenshot of the Defender portal left navigation menu with the Microsoft Sentinel section.](https://learn.microsoft.com/en-us/training/wwl-sci/integrate-microsoft-defender-xdr-with-microsoft-sentinel/media/navigation-defender-portal.png)](https://learn.microsoft.com/en-us/training/wwl-sci/integrate-microsoft-defender-xdr-with-microsoft-sentinel/media/navigation-defender-portal.png#lightbox)

# Exercise - Connect Microsoft Sentinel to Microsoft Defender XDR

Completed100 XP

- 25 minutes

You're a Security Operations Analyst working at a company that deployed both Microsoft Defender XDR and Microsoft Sentinel. You need to prepare for Microsoft Sentinel in the Microsoft Defender portal by connecting Microsoft Sentinel to Defender XDR.

In this exercise, you use _Interactive Guides_ to simulate performing the following tasks:

- Connect a new Microsoft Sentinel workspace to Microsoft Defender XDR.
- Connect an existing Microsoft Sentinel workspace to Microsoft Defender XDR.
- Explore the Microsoft Sentinel capabilities in the Microsoft Defender XDR portal.

Note

The environment for this exercise is a simulation generated from the product. As a limited simulation, links on a page may not be enabled and text-based inputs that fall outside of the specified script may not be supported. A pop-up message displays stating, "This feature isn't available within the simulation." When this occurs, select OK and continue the exercise steps.

### Task 1: Connect a new Microsoft Sentinel workspace to Defender XDR

In this interactive guide, which takes approximately 10 minutes to complete, you onboard a new Microsoft Sentinel workspace to Defender XDR.

Select the image below to get started.

[![Thumbnail for Connecting Microsoft Sentinel to Defender XDR.](https://learn.microsoft.com/en-us/training/wwl-sci/integrate-microsoft-defender-xdr-with-microsoft-sentinel/media/interactive-guide-sentinel-new.png)](https://microsoftlearning.github.io/click-throughs/docs/IG/interactive_guide_connect_microsoft_sentinel_with_microsoft_defender_xdr_web/story.html)

### Task 2: Connect an existing Microsoft Sentinel workspace to Defender XDR

In this Interactive Guide, which takes approximately 10 minutes to complete, you connect an existing Microsoft Sentinel workspace to Defender XDR.

Select the image below to get started.

[![Thumbnail for Connecting an existing Microsoft Sentinel to Defender XDR.](https://learn.microsoft.com/en-us/training/wwl-sci/integrate-microsoft-defender-xdr-with-microsoft-sentinel/media/interactive-guide-sentinel-existing.png)](https://microsoftlearning.github.io/click-throughs/docs/IG/interactive_guide_connect_microsoft_sentinel_to_microsoft_defender_xdr_existing/story.html)

You have completed the simulation exercises to connect Microsoft Sentinel to Microsoft Defender XDR. You can now explore the Microsoft Sentinel capabilities in the Microsoft Defender portal.

Note

Feel free to explore and compare the other Microsoft Sentinel capabilities, but as this is a simulation, your ability to explore Microsoft Sentinel in the Microsoft Defender portal is limited. In a real environment, you would be able to explore the full Microsoft Sentinel capabilities in the Microsoft Defender portal.


![[Pasted image 20261005135017.png]]

![[Pasted image 20261005135030.png]]

# Summary
In this module, you learned about the integration of Microsoft Sentinel into the Microsoft Defender portal. This integration simplifies operations by reducing the complexity of managing multiple tools, enhancing hunting capabilities, enabling automatic attack disruption for SAP applications, and providing unified entity pages. You also learned about the differences in managing multiple Microsoft Sentinel workspaces between the Azure and Defender portals. Additionally, the module covered the prerequisites for integrating Microsoft Defender XDR with Microsoft Sentinel, including having a Log Analytics workspace with Microsoft Sentinel enabled and access to Microsoft Defender XDR in the Defender portal.

The main takeaways from this module include understanding the benefits of integrating Microsoft Sentinel into the Microsoft Defender portal, such as streamlined operations and enhanced hunting capabilities. You also learned about the unique features available in each portal and the steps to integrate Microsoft Defender XDR with Microsoft Sentinel. Furthermore, the module introduced the concept of a storage account using the example of a chocolate manufacturer, explaining how to create a storage account suitable for holding mission-critical business data.

## Additional Reading

- [Microsoft Sentinel in the Microsoft Defender portal](https://learn.microsoft.com/en-us/azure/sentinel/microsoft-sentinel-defender-portal)
- [Frequently asked questions about the unified security operations platform](https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/frequently-asked-questions-about-the-unified-security-operations/ba-p/4212048)

# Connect data to Microsoft Sentinel using data connectors

The primary approach to connect log data is using the Microsoft Sentinel provided data connectors. This module provides an overview of the available data connectors.

## Learning objectives

Upon completion of this module, the learner is able to:

- Describe how to install Content Hub Solutions to provision Microsoft Sentinel Data connectors
- Explain the use of data connectors in Microsoft Sentinel
- Describe the Microsoft Sentinel data connector providers
- Explain the Common Event Format and Syslog connector differences in Microsoft Sentinel

# Introduction


Data is ingested to the Microsoft Sentinel workspace by configuring data connectors. The data connectors are included in Content Hub solutions for Microsoft services and products, and third-party solutions.

## Microsoft Sentinel and Defender XDR

Use one of the following methods to integrate Microsoft Sentinel with Microsoft Defender XDR services:

- Ingest Microsoft Defender XDR service data into Microsoft Sentinel and view Microsoft Sentinel data in the Azure portal. Enable the Defender XDR connector in Microsoft Sentinel.
    
- Integrate Microsoft Sentinel and Defender XDR directly in the Microsoft Defender portal. In this case, view Microsoft Sentinel data directly with the rest of your Defender incidents, alerts, vulnerabilities, and other security data. To do this, you must onboard Microsoft Sentinel to the Defender portal.
    

## Scenario

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You need to learn how to connect log data from the many different data sources in your organization. The organization has data from Microsoft 365, Microsoft Defender XDR, Azure resources, non-azure virtual machines, and network appliances.

You plan on using the Microsoft Sentinel Content Hub solutions that include the data connectors to integrate the log data from the various sources. You need to document a connector plan for management that maps each of the organization's data sources to the proper Microsoft Sentinel data connector.

After completing this module, you'll be able to:

- Describe how to install Content Hub Solutions to provision Microsoft Sentinel Data connectors
- Explain the use of data connectors in Microsoft Sentinel
- Describe the Microsoft Sentinel data connector providers
- Explain the Common Event Format and Syslog connector differences in Microsoft Sentinel

## Prerequisites

Basic experience with Microsoft Azure or Microsoft Defender operations.

## Interactive lab simulation

Note

Select the thumbnail image to start the lab simulation. You may find slight differences between this interactive simulation and this modules content, but the core concepts and ideas being demonstrated are the same. When you're done, be sure to return to this page so you can continue learning.

[![Screenshot of the lab simulation page.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-data-to-azure-sentinel-with-data-connectors/media/sc-200-lab-simulation-connect-data-to-microsoft-sentinel-with-data-connectors.png)](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Connect%20data%20to%20Microsoft%20Sentinel%20using%20data%20connectors)

# Ingest log data with data connectors
To collect log data, you need to connect your data sources with Microsoft Sentinel Data Connectors. The Data Connectors are included with Content Hub Solutions provided by Microsoft Sentinel.

![Screen shot of Microsoft Sentinel Content Hub page.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-data-to-azure-sentinel-with-data-connectors/media/02-azure-activity-content-hub-solution.png)

After you install a Content Hub Solution, installed Data Connectors are displayed in Microsoft Sentinel under the `Configuration | Data connectors` menu section. When you select the Open connector page, the detailed connector page is split and has a left half and a right half.

![Screen shot of Microsoft Sentinel Detailed Connector Page.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-data-to-azure-sentinel-with-data-connectors/media/02-azure-activity-data-connector-page.png)

The left half provides information about the connector, the connector's status, and the last time a log was received if connected. On the bottom section of the left side is the Data Types. The `Data Types` lists the table(s) that the connector writes to.

The right half has an Instructions tab. The Instructions tab can vary based on the connector. In general, there are Prerequisites and Configuration. Follow the Configuration to connect to the data source. The Next steps tab provides a quick reference to workbooks, query samples, and analytical templates. Data Connectors can only be disconnected/deactivated, not deleted.

Note

Content Hub solutions may also install Workbooks, Analytics rules and Hunting queries. Workbooks and Analytic rule templates for out of the box connectors are already available in the Sentinel environment.

# Understand data connector providers
### Microsoft Defender XDR

The Microsoft Defender XDR data connector provides alerts, incidents, and raw data from the Microsoft Defender XDR products including (but aren't limited to):

- Microsoft Defender for Endpoint
    
- Microsoft Defender for Identity
    
- Microsoft Defender for Office 365
    
- Microsoft Defender for Cloud Apps
    

### Microsoft Azure Services

The connectors for Microsoft and Azure-related services include (but aren't limited to):

- Microsoft Entra ID
    
- Azure Activity
    
- Microsoft Entra ID Protection
    
- Azure DDoS Protection
    
- Microsoft Defender for IoT
    
- Azure Information Protection
    
- Azure Firewall
    
- Microsoft Defender for Cloud
    
- Azure Web Application Firewall (WAF) (formerly Microsoft WAF)
    
- Domain name server
    
- Office 365
    
- Windows Firewall
    
- Security Events
    

### Vendor connectors

Microsoft Sentinel provides an ever-growing list of vendor-specific data connectors. These connectors primarily use the CEF and Syslog connector as their foundation.

Tip

Remember to check the connector page to see the Data Type (table) that the connector writes to.

### Custom connectors using the Log Analytics API

You can use the Log Analytics Data Collector API to send log data to the Microsoft Sentinel Log Analytics workspace.

### Logstash plugin

Using Microsoft Sentinel's output plugin for the Logstash data collection engine, you can send any log you want through Logstash directly to your Log Analytics workspace in Microsoft Sentinel. The logs are written to a custom table that you define using the output plugin.

## Common Event Format and Syslog connector

If there's no vendor-provided connector, you can use the generic Common Event Format(CEF) or Syslog Connector.

Syslog is an event logging protocol that is common to Linux. Applications send messages that may be stored on the local machine or delivered to a Syslog collector.

Common Event Format (CEF) is an industry-standard format on top of Syslog messages, used by many security vendors to allow event interoperability among different platforms.

### Syslog vs. Common Event Format

CEF is always a superior choice because the log data is parsed into predefined fields in the CommonSecurityLog table. Syslog provides header fields, but the raw log message is stored in a field named SyslogMessage in the Syslog table. For the Syslog data to be queried, you need to write a parser to extract the specific fields. The process to create a Parser for a Syslog message is demonstrated in a later module.

### Connector architecture options

To connect the CEF or Syslog Collector to Microsoft Sentinel, the agent must be deployed on a dedicated Azure virtual machine (VM) or an on-premises system to support the appliance's communication with Microsoft Sentinel. You can deploy the agent automatically or manually. Automatic deployment is only available if your dedicated machine is connected to Azure Arc or is a Virtual Machine in Azure.

The following diagram illustrates on-premises systems sending Syslog data to a dedicated Azure VM running the Microsoft Sentinel agent.

![Diagram of Common Event Format architecture using Syslog on a dedicated Azure VM.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-data-to-azure-sentinel-with-data-connectors/media/common-event-format-forwarder-diagram-azure.png)

Alternatively, you can manually deploy the agent on an existing Azure VM, on a VM in another cloud, or an on-premises machine. The following diagram illustrates on-premises systems sending Syslog data to a dedicated on-premises system running the Microsoft Sentinel agent.

![Diagram of Common Event Format architecture for sending Linux log data using Syslog on a dedicated on-premises system.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-data-to-azure-sentinel-with-data-connectors/media/common-event-format-forwarder-diagram-on-premises.png)

# View connected hosts
To view your Windows and Linux hosts connected with an agent, you can do so in the Log Analytics workspace. To see your connected hosts do the following steps:

## Microsoft Sentinel and Defender XDR

Select the appropriate tab to see the connected hosts depending on which integration method you use.

- [Defender portal](https://learn.microsoft.com/en-us/training/modules/connect-data-to-azure-sentinel-with-data-connectors/4-view-connected-hosts?tabs=defender-portal#tabpanel_1_defender-portal)
- [Azure portal](https://learn.microsoft.com/en-us/training/modules/connect-data-to-azure-sentinel-with-data-connectors/4-view-connected-hosts?tabs=defender-portal#tabpanel_1_azure-portal)

1. In the Microsoft Defender portal navigation menu, expand **System**, and select **Settings**.
    
2. Select **Microsoft Sentinel**.
    
3. Select the appropriate Microsoft Sentinel workspace.
    
4. In the side panel that opens, select **Log Analytics settings**, and **Configure Log Analytics work**.
    
    ![Screen shot of Microsoft Defender Microsoft Sentinel workspace configuration page.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-data-to-azure-sentinel-with-data-connectors/media/04-view-connected-hosts-defender.png)
    
5. In the Log Analytics workspace, select **Settings** from the navigation menu, and then select **Agents**.
    
6. Select either the **Windows** or **Linux** tab to view the connected hosts.
    
    ![Screen shot of Log Analytics Agents page.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-data-to-azure-sentinel-with-data-connectors/media/04-log-analytics-connected-hosts.png)
![[Pasted image 20261005193601.png]]

# Summary and resources
You should have learned how data is sent to the Microsoft Sentinel workspace by configuring the provided data connectors. And how the included data connectors are for Microsoft 365 services, Azure, and third-party specific.

You should now be able to:

- Explain the use of data connectors in Microsoft Sentinel
- Understand how data connectors are installed from Microsoft Sentinel Content Hub Solutions
- Describe the Microsoft Sentinel data connector providers
- Explain the Common Event Format and Syslog connector differences in Microsoft Sentinel
# Connect Microsoft services to Microsoft Sentinel

# Introduction
You connect Microsoft 365 and Azure services to the Microsoft Sentinel workspace using the provided data connectors. The data connectors are included in out-of-the-box (OOTB), or built-in Content Hub solutions.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You'll connect Microsoft 365 and Azure services to Microsoft Sentinel.

Based on your previously documented connector plan, you use the Content Hub to install the solutions that include the specific connectors. As you activate the connectors, you notice the option to have incidents created from the Microsoft Entra ID Protection service. You don’t follow the recommended option to create incidents as you plan to activate the incident creation rule with custom options later in your implementation process.

After completing this module, you'll be able to:

- Connect Microsoft service connectors
- Explain how connectors autocreate incidents in Microsoft Sentinel

## Prerequisites

Basic experience with Microsoft Azure operations.

# Plan for Microsoft services connectors
Once you installed the Content Hub solutions, you can connect Microsoft 365 and Azure-related services in the Data Connector page configuration section in just a few mouse clicks. It's easy to overlook specific considerations for each connector. This module demonstrates the connecting of four services. Each service sends data to different Data Types (tables).

First is the Microsoft 365 connector. The Configuration option allows for the sending of Exchange, SharePoint, and Teams data. Based on your organization's specific needs, you can decide which data to ingest. The Data types show that the data resides in the OfficeActivity table.

The second is Microsoft Entra ID, which supports multiple log types. You can independently select which log types to stream into Microsoft Sentinel, and each writes to a separate Log Analytics table. Available log types include interactive and non-interactive user sign-in logs, service principal sign-in logs, managed identity sign-in logs, provisioning logs, AD FS sign-in logs, and Audit logs.

Third is Microsoft Entra ID Protection. This connector sends data to the SecurityAlert table. The SecurityAlert table holds the alert data only without the underlying data that caused the alert. A second option is to Create Incidents, which is Recommended! This process automatically creates an Incident based on and connected to the alert ingested to the SecurityAlert table from Microsoft Entra ID Protection. You can also activate the incident creation rule on the Analytics page.

The final connector is the Azure Activity. The Azure Activity Log is a subscription log that provides insight into subscription-level events that occur in Azure. Including events from Azure Resource Manager operational data, service health events, write operations taken on the resources in your subscription, and the status of activities performed in Azure.


Connect the Microsoft 365 connector
The Microsoft 365 connector provides insight into ongoing user activities. You collect data like file downloads, access requests sent, changes to group events, set-mailbox, and details of the user who performed the actions.

Install the solution
Start by installing the Microsoft 365 solution that contains the data connector.

For Microsoft Sentinel in the Azure portal, under Content management, select Content hub.
For Microsoft Sentinel in the Defender portal, select Microsoft Sentinel > Content management > Content hub.
Search for and select Microsoft 365.
On the right-hand side pane, select Install.
Configure the data connector
After the solution is installed, connect the data connector.

In the Microsoft Sentinel left navigation menu expand Configuration, and select Data connectors.

Select Microsoft 365.

Then select the Open connector page on the preview pane.

Review the Description and Data types tabs to understand the data that is ingested.

In the Instructions tab, verify that you meet the Prerequisites.

In the Instructions tab, under the section labeled Configuration, select the record types to collect and Apply Changes.

Wait until validation is complete and the button changes to Disconnect.


# Connect the Microsoft Entra connector
Gain insights into Microsoft Entra ID by connecting Audit and Sign-in logs to Microsoft Sentinel to gather insights around Microsoft Entra scenarios. You can learn about app usage, conditional access policies, and legacy auth related details using our Sign-in logs. You can get information on your Self-Service Password Reset (SSPR) usage, Microsoft Entra Management activities like user, group, role, and app management in the Audit logs table.

## Install the solution

Start by installing the solution that contains the data connector.

1. For Microsoft Sentinel in the Azure portal, under **Content management**, select **Content hub**.  
    For Microsoft Sentinel in the Defender portal, select **Microsoft Sentinel** > **Content management** > **Content hub**.
2. Search for and select **Microsoft Entra ID**.
3. On the right-hand side pane, select **Install**.

## Configure the data connector

After the solution is installed, connect the data connector.

1. In the Microsoft Sentinel left navigation menu expand **Configuration**, and select **Data connectors**.
    
2. Select **Microsoft Entra ID**.
    
3. Then select the **Open connector** page on the preview pane.
    
4. Mark the checkboxes next to the logs you want to stream into Microsoft Sentinel, and select **Connect**.
    

![Screenshot of the Microsoft Entra ID data connector page in Microsoft Sentinel, showing log type checkboxes for sign-in and audit logs.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-microsoft-services-to-azure-sentinel/media/microsoft-entra-id.png)

### Available log types

When you configure the connector, you can independently select which log types to stream into Microsoft Sentinel. Each log type writes to a separate Log Analytics table:

|Log type|Table|
|---|---|
|Interactive user sign-in logs|SigninLogs|
|Non-interactive user sign-in logs|AADNonInteractiveUserSignInLogs|
|Service principal sign-in logs|AADServicePrincipalSignInLogs|
|Managed identity sign-in logs|AADManagedIdentitySignInLogs|
|Provisioning logs|AADProvisioningLogs|
|AD FS sign-in logs|ADFSSignInLogs|
|Audit logs|AuditLogs|

Enabling only the log types relevant to your use cases helps manage Log Analytics ingestion costs.

# Connect the Microsoft Entra ID Protection connector
Microsoft Entra ID Protection provides a consolidated view of at-risk users, risk events, and vulnerabilities, with the ability to remediate risk immediately and set policies to autoremediate future events.

## Install the solution

Start by installing the solution that contains the data connector.

1. For Microsoft Sentinel in the Azure portal, under **Content management**, select **Content hub**.  
    For Microsoft Sentinel in the Defender portal, select **Microsoft Sentinel** > **Content management** > **Content hub**.
2. Search for and select **Microsoft Entra ID Protection**.
3. On the right-hand side pane, select **Install**.

## Configure the data connector

After the solution is installed, connect the data connector.

1. In the Microsoft Sentinel left navigation menu expand **Configuration**, and select **Data connectors**.
    
2. Select **Microsoft Entra ID Protection**.
    
3. Then select the **Open connector** page on the preview pane.
    
4. Select **Connect** to start streaming the Microsoft Entra ID Protection alerts.
    
5. Select whether alerts from Microsoft Entra ID Protection automatically generate incidents by selecting **Enable**.
    

![Screen shot of the Microsoft Entra ID Protection connector page.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-microsoft-services-to-azure-sentinel/media/microsoft-entra-id-protection.png)

If you enable creating incidents, the default analytics rule "Create incidents based on Microsoft Entra ID Protection alerts" is enabled with default values. You can edit this analytical rule on the Analytics page.

# Connect the Azure Activity connector
The Azure Activity Log is a subscription log that provides insight into subscription-level events that occur in Azure. The events included are from Azure Resource Manager operational data, service health events, write operations taken on the resources in your subscription, and the status of activities performed in Azure. The Azure Activity Data connector uses Azure Policy to apply an Azure Subscription log-streaming pipeline that sends the event data to Log Analytics.

Important

Prerequisites require your user to be assigned the owner role on the relevant subscription.

## Install the solution

Start by installing the solution that contains the data connector.

1. For Microsoft Sentinel in the Azure portal, under **Content management**, select **Content hub**.  
    For Microsoft Sentinel in the Defender portal, select **Microsoft Sentinel** > **Content management** > **Content hub**.
2. Search for and select **Azure Activity**.
3. On the right-hand side pane, select **Install**.

## Configure the data connector

After the solution is installed, connect the data connector.

1. In the Microsoft Sentinel left navigation menu expand **Configuration**, and select **Data connectors**.
    
2. Select the **Azure Activity** Data connector.
    
3. Select **Open connector page**.
    
4. In the _Instructions/Configuration_ area, scroll down and under _2. Connect your subscriptions..._ select **Launch Azure Policy Assignment Wizard**.
    
5. In the **Basics** tab, select the ellipsis button (...) under **Scope** and select your "Azure subscription" from the drop-down list and select **Select**.
    
6. Select the **Parameters** tab, choose your _yourName-sentinel_ workspace from the **Primary Log Analytics workspace** drop-down list.
    
7. Select the **Remediation** tab and select the **Create a remediation task** checkbox. This action applies the subscription configuration to send the information to the Log Analytics workspace.
    
    Note
    
    To apply the policy to your existing resources, you need to create a remediation task.
    
8. Select the **Review + Create** button to review the configuration.
    
9. Select **Create** to finish.
![[Pasted image 20261006062345.png]]
# Summary and resources
You learned how to connect Microsoft 365 and Azure services to the Microsoft Sentinel workspace using the provided data connectors.

You should now be able to:

- Connect Microsoft services connectors
- Explain how connectors autocreate incidents in Microsoft Sentinel

# Connect Microsoft Defender XDR to Microsoft Sentinel

# Introduction
You connect Microsoft Defender XDR security solutions to the Microsoft Sentinel workspace using the provided data connectors.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. As you continue your process to activate data connectors in Microsoft Sentinel, you now need to focus on the Microsoft Defender XDR solutions, including Microsoft Defender for Endpoint and Microsoft Defender for Office 365.

By the end of this module, you're able to connect Microsoft Defender XDR security solutions to the Microsoft Sentinel workspace using the provided data connectors.

After completing this module, you'll be able to:

- Install and configure the Microsoft Defender XDR Content Hub solution
- Activate the Microsoft Defender XDR connector in Microsoft Sentinel
- Activate the Microsoft Defender for Cloud connector in Microsoft Sentinel
- Activate the Microsoft Defender for IoT connector in Microsoft Sentinel

## Prerequisites

- Intermediate understanding of Microsoft Defender XDR services
- Fundamental understanding of Microsoft Azure operations

Plan for Microsoft Defender XDR connectors
The Microsoft Defender portal is a unified, natively integrated, pre-, and post-breaches enterprise defense suite. It protects endpoint, identity, email, and cloud app threats. You can detect, prevent, investigate, and automatically respond to sophisticated threats in a central place. It includes the following services:

Microsoft Defender for Office 365

Microsoft Defender for Endpoint

Microsoft Defender for Identity

Microsoft Defender for Cloud Apps

The Microsoft Defender XDR integration with Microsoft Sentinel currently provides these data connectors for those services:

Microsoft Defender XDR

Microsoft Defender for Cloud Apps

Microsoft Defender for Endpoint

Microsoft Defender for Identity

Microsoft Defender for Office 365

Other relevant Microsoft Defender data connectors include:

Microsoft Defender for IoT

Microsoft Purview Insider Risk Management

It's important to understand how data is ingested by each connector. Does the connector support bi-directional syncing of Incidents? Should you ingest the raw log data for hunting and entity analysis? Once you've decided the required data from each log source, then enable the connectors.

 Note

These connectors are now considered Legacy connectors:

Microsoft Defender for Cloud Apps, Microsoft Defender for Endpoint, Microsoft Defender for Identity and Microsoft Defender for Office 365.

# Connect the Microsoft Defender XDR connector
The Microsoft Defender extended detection and response (XDR) connector enables you to stream all Microsoft Defender XDR incidents, alerts, and advanced hunting events into Microsoft Sentinel. The connector keeps incidents synchronized between both portals and enriches them with alerts from Microsoft Defender XDR's component services:

- Microsoft Defender for Endpoint
- Microsoft Defender for Identity
- Microsoft Defender for Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Cloud

Other services whose alerts are included:

- Microsoft Purview Data Loss Prevention
- Microsoft Entra ID Protection
- Microsoft Purview Insider Risk Management

Connecting the Microsoft Defender XDR connector is a prerequisite for configuring the Unified Security Operations Platform or unified security information and event management (SIEM) and XDR experience in Microsoft Defender XDR.

## Integration methods

There are two methods to integrate Microsoft Defender XDR with Microsoft Sentinel:

**Defender portal integration**: If you onboard Microsoft Sentinel to the Defender portal and are licensed for Defender XDR, Microsoft Sentinel is automatically connected to Defender XDR. The data connector for Defender XDR is automatically set up for you. This provides a unified security operations experience directly in the Microsoft Defender portal.

**Azure portal integration**: If you want to sync Defender XDR data to Microsoft Sentinel in the Azure portal, you must enable the Microsoft Defender XDR connector in Microsoft Sentinel.

- [Defender portal integration](https://learn.microsoft.com/en-us/training/modules/connect-microsoft-defender-365-to-azure-sentinel/3-connect-microsoft-365-defender-connector?tabs=defender-portal-integration#tabpanel_1_defender-portal-integration)
- [Azure portal integration](https://learn.microsoft.com/en-us/training/modules/connect-microsoft-defender-365-to-azure-sentinel/3-connect-microsoft-365-defender-connector?tabs=defender-portal-integration#tabpanel_1_azure-portal-integration)

If you onboard Microsoft Sentinel to the Defender portal and are licensed for Defender XDR, Microsoft Sentinel is automatically connected to Defender XDR. The data connector for Defender XDR is automatically set up for you, and any data connectors for the alert providers included in the Defender XDR connector are automatically disconnected. This includes:

- Microsoft Defender for Cloud Apps (alerts)
- Microsoft Defender for Endpoint
- Microsoft Defender for Identity
- Microsoft Defender for Office 365
- Microsoft Entra ID Protection

In this integration method, you view Microsoft Sentinel data directly with the rest of your Defender incidents, alerts, vulnerabilities, and other security data in the Microsoft Defender portal. Defender XDR incidents appear in the Microsoft Sentinel incidents queue with the product name Microsoft Defender XDR, and each incident contains a link back to the parallel incident in the Microsoft Defender portal.

Changes made to certain fields or attributes of a Defender XDR incident in either portal are synchronized immediately to the other, with no delay. The following fields are synchronized between the Defender portal and Microsoft Sentinel:

- Title
- Description
- ProductName
- Severity
- Custom tags
- AdditionalData
- Comments (new only)
- LastModifiedBy

## Important considerations

**Microsoft incident creation rules**: To avoid creating duplicate incidents for the same alerts, the Microsoft incident creation rules setting is turned off for Defender XDR-integrated products when connecting Defender XDR. Microsoft incident creation rules aren't supported in the Defender portal because it has its own incident creation engine. To preserve alert filtering capability, configure alert tuning in the Microsoft Defender portal or use automation rules to suppress or close incidents you don't want.

Note

If you uncheck the _Turn off all Microsoft incident creation rules for these products. Recommended_ checkbox, you may receive duplicate incidents in the incidents queue.

# Connect Microsoft Defender for Cloud connector
Microsoft Defender for Cloud is a security management tool that allows you to detect and quickly respond to threats across Azure, hybrid, and multicloud workloads. This connector allows you to stream your security alerts from Microsoft Defender for Cloud into Microsoft Sentinel. Then you can view Defender data in workbooks, query it to produce alerts, and investigate and respond to incidents.

To view the connector page, do the following steps:

1. Select Data connectors page in Microsoft Sentinel.
    
2. Select **Microsoft Defender for Cloud**
    
3. Then select the **Open connector** page on the preview pane.
    
4. Select the **Connect** toggle for the subscription.
    
5. Select the **Bi-directional** sync option.

# Connect Microsoft Defender for IoT
Gain insights into your IoT security by connecting Microsoft Defender for IoT alerts to Microsoft Sentinel. You can get out-of-the-box alert metrics and data, including alert trends, top alerts, and alert breakdown by severity. You can also get information about the recommendations provided for your IoT hubs including top recommendations and recommendations by severity.

To view the connector page, do the following steps:

1. Select Data connectors page in Microsoft Sentinel.
    
2. Select **Microsoft Defender for IoT**
    
3. Then select the **Open connector** page on the preview pane.
    
4. Select the **Connect** toggle the subscription.

# Connect Microsoft Defender legacy connectors
Microsoft Sentinel originally connected the Microsoft Defender XDR solutions with individual connectors:

- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity

These connectors had a limitation of only sending Alerts to Microsoft Sentinel. You would then have the option to generate an Incident from the Alert. Setting this option created the following limitations:

- Raw data wouldn't be ingested.
- A new Incident would be created that caused Incidents in both the Microsoft Defender portal and Microsoft Sentinel that would need to be managed independently.

The newer **Microsoft Defender XDR** connector removes the limitations and should be used instead of the legacy connectors.

![[Pasted image 20261006064018.png]]

# Summary and resources
You should have learned how to connect Microsoft Defender XDR security solutions to the Microsoft Sentinel workspace using the provided data connectors.

You should now be able to:

- Activate the Microsoft Defender XDR connector in Microsoft Sentinel
- Activate the Microsoft Defender for Cloud connector in Microsoft Sentinel

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)

## Get started with Azure

Choose the Azure account that's right for you. Pay as you go or try Azure free for up to 30 days.[Sign up.](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn_14e03e21-6fa2-525a-e239-39247e83961f)

# Connect Windows hosts to Microsoft Sentinel

Two of the most common logs to collect are Windows security events and Sysmon. Learn how Microsoft Sentinel makes this easy with the Microsoft Windows Events data connectors.

## Learning objectives

Upon completion of this module, the learner is able to:

- Connect Azure Windows Virtual Machines to Microsoft Sentinel
- Connect non-Azure Windows hosts to Microsoft Sentinel
- Install and configure a data connector to collect Sysmon events

# Introduction
You connect Windows devices to the Microsoft Sentinel workspace using the provided data connectors. The connector offers options to control which events to collect.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You must collect event log data from Windows Hosts. The hosts could be located on-premise or as a virtual machine in Azure.

Your Security Operations team relies on event data created by the Sysmon tool installed on some of the Windows Hosts. You'll configure the Windows hosts to send event data to Microsoft Sentinel. You also need to ensure that the Sysmon events are available to be used in detection rules.

By the end of this module, you'll be able to connect Windows devices to the Microsoft Sentinel workspace using the provided data connector.

After completing this module, you'll be able to:

- Connect Azure Windows Virtual Machines to Microsoft Sentinel
- Connect non-Azure Windows hosts to Microsoft Sentinel
- Configure Log Analytics agent to collect Sysmon events

## Prerequisites

Basic knowledge of operational concepts such as monitoring, logging, and alerting.

# Plan for Windows hosts security events connector
You have two Windows security events Content Hub solution options to stream events from Windows devices to Microsoft Sentinel.

The first option is to install the _Windows Security Events_ Content Hub solution. You can choose either of the two agent data connectors available:

- Windows Security Events via AMA Connector
- Security Events via Legacy Agent Connector

The second option is to install the _Windows Forwarded Events_ Content Hub solution and configure a Windows Event Collector device to receive events from the Windows devices. The Windows Event Collector device would then forward events to Microsoft Sentinel with the _Windows Forwarded Events_ data connector.

Note

Microsoft recommends installation of Windows Security Events via AMA Connector. The Legacy connector uses the Log Analytics agent which was deprecated Aug 31, 2024, and thus should only be installed where AMA isn't supported.

## Windows Security Events via AMA Connector vs. Security Events via Legacy Agent Connector

The Windows Security Events via AMA Connector has the following differences from the Security Events via Legacy Agent Connector:

Benefits:

- Manage collection settings at scale
- Azure Monitoring Agent shared with other solutions
- Performance improvements
- Security improvements

Limitations:

- None.

Requirements:

- non-Azure VM's/devices require Azure Arc.

### Azure Arc

Azure Arc uses the _Azure Connected Machine_ agent (azcmagent) installed on the device or VM that allows the device to be managed the same as an Azure VM. Azure Arc provides other functionality including running Azure based services in a hybrid environment.

# Connect using the Windows Security Events via AMA Connector


The Windows Security Events via AMA Connector uses Data Collection Rules (DCRs) to define the data to collect from each agent. Data collection rules offer you two distinct advantages:

- **Manage collection settings at scale** while still allowing unique, scoped configurations for subsets of machines. They're independent of the workspace and independent of the virtual machine, which means they can be defined once and reused across machines and environments.
    
- **Build custom filters** to choose the exact events you want to ingest. The Azure Monitor Agent uses these rules to filter the data at the source and ingest only the events you want, while leaving everything else behind.
    

## Prerequisites

- You must have read and write permissions on the Microsoft Sentinel workspace.
    
- To collect events from any system that isn't an Azure virtual machine, the system must have **Azure Arc** installed and enabled before you enable the Azure Monitor Agent-based connector.
    

These include:

- Windows servers installed on physical machines
- Windows servers installed on on-premises virtual machines
- Windows servers installed on virtual machines in non-Azure clouds

## Connect Windows Hosts

1. From the Microsoft Sentinel navigation menu, select Data connectors.
    
2. Select the Windows Security Events via AMA connector from the list, and then select Open connector page on the details pane.
    
3. Verify that you have the appropriate permissions as described under the Prerequisites section on the connector page.
    
4. Under Configuration, select +Add data collection rule. The Create data collection rule wizard opens.
    
5. Under Basics, enter a Rule name and specify a Subscription and Resource group where the data collection rule (DCR) will be created. This doesn't have to be the same resource group or subscription the monitored machines and their associations are in, as long as they are in the same tenant.
    
6. In the Resources tab, select +Add resource(s) to add machines to which the Data Collection Rule will apply. The Select a scope dialog opens, and you see a list of available subscriptions. Expand a subscription to see its resource groups, and expand a resource group to see the available machines. You see Azure virtual machines and Azure Arc-enabled servers in the list. You can mark the check boxes of subscriptions or resource groups to select all the machines they contain, or you can select individual machines. Select Apply when you've chosen all your machines. At the end of this process, the Azure Monitor Agent is installed on any selected machines that don't already have the agent.
    
7. On the Collect tab, choose the events you would like to collect. Select:
    
    - All security events
    - Common
    - Minimal
    - Custom
    
    Note
    
    Custom allows you to specify other logs or to filter events using XPath queries. For XPath queries you can enter up to 20 expressions in a single box, and up to 100 boxes in a rule. The Azure Monitor agent supports XPath queries for XPath version 1.0 only.
    
8. When you add all the filter expressions you want, select Next: Review + create.
    
9. When you see the "Validation passed" message, select Create.
    

You'll see all your data collection rules (including those created through the API) under Configuration on the connector page. From there you can edit or delete existing rules.

### Test the validity of an XPath query

Use the PowerShell cmdlet Get-WinEvent with the -FilterXPath parameter to test the validity of an XPath query. The following script shows an example:

PowerShell

```
$XPath = '*[System[EventID=1035]]'
Get-WinEvent -LogName 'Application' -FilterXPath $XPath
```

- If events are returned, the query is valid.
- If you receive the message "No events were found that match the specified selection criteria," the query may be valid, but there are no matching events on the local machine.
- If you receive the message "The specified query is invalid," the query syntax is invalid.
# Connect using the Security Events via Legacy Agent Connector
The _Windows Security Events via AMA_ connector lets you stream all security events from the Windows machines connected to your Microsoft Sentinel workspace using the Windows agent. This connection enables you to view dashboards, create custom alerts, and improve investigation. These events give you more insight into your organization’s network and improve your security operation capabilities.

- All Security Events - All Windows security and AppLocker events.
    
- Common - A standard set of events for auditing purposes. A full user audit trail is included in this set. For example, it contains both user sign-in and user sign-out events (event IDs 4624, 4634). There are also auditing actions such as security group changes, key domain controller Kerberos operations, and other types of events in line with accepted best practices.
    
- The Common event set can contain some types of events that aren't so common. This is because the main point of the Common set is to reduce the volume of events to a more manageable level while still maintaining full audit trail capability.
    
- Minimal - A small set of events that might indicate potential threats. This set doesn't contain a full audit trail. It covers only events that might indicate a successful breach and other significant events with low rates of occurrence. For example, it contains successful and failed user logons (event IDs 4624, 4625). Still, it doesn't contain sign-out information (4634), which, while important for auditing, isn't meaningful for breach detection and has a relatively high volume. Most of this set's data volume comprises sign-in events and process creation events (event ID 4688).
    
- Custom - Custom allows you to specify other logs or to filter events using XPath queries.
    
    Note
    
    Query the _SecurityEvents_ table in Microsoft Sentinel _Logs_ to see the events collected by the connector.
    
- The _Windows Security Events via AMA_ connector uses Data Collection Rules (DCRs) to define the data to collect, and installs the Azure Monitor Agent (AMA) extension on the selected machines.
    

[![Screenshot of the Security Events Connector Page.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-windows-hosts-to-azure-sentinel/media/security-events-connector.png)](https://learn.microsoft.com/en-us/training/wwl-sci/connect-windows-hosts-to-azure-sentinel/media/security-events-connector.png#lightbox)

## Connect Azure Windows Virtual Machines

To view the connector page:

1. Select **Data connectors page**.
    
2. Select **Windows Security Events via AMA**.
    
3. Then select the **Open connector page** button on the preview pane.
    
4. Verify that you have the appropriate permissions as described under Prerequisites.
    
5. In the _Configuration_ section, select the **+Create data collection rule** button.
    
6. Enter a _Rule name_, select the appropriate _Subscription_ and _Resource group_ where the data collection rule (DCR) will be created.
    
7. Select **Next: Resources**.
    
8. Expand your _Subscription_ under _Scope_ on the _Resources_ tab.
    
    Tip
    
    You can expand the whole _Scope_ hierarchy by selecting the ">" before the _Scope_ column.
    
9. Expand the resource group, and then select Azure virtual machines.
    
10. Select **Next: Collect**.
    
11. Review the different Security Event collection option. The default is Keep _All Security Events_.
    
12. Select **Next: Review + create**.
    
13. Select **Create** to save the Data Collection Rule.
    
14. Wait a minute and then select **Refresh** to see the new data collection rule listed.
    

## Connect non-Azure Windows Machines

In this task, you add an Azure Arc connected, non-Azure Windows virtual machine to Microsoft Sentinel.

Note

The _Windows Security Events via AMA_ data connector requires Azure Arc for non-Azure devices.

To view the connector page:

1. Select **Data connectors** page.
    
2. Select **Windows Security Events via AMA**.
    
3. Then select the **Open connector** page on the preview pane.
    
4. Verify that you have the appropriate permissions as described under Prerequisites.
    
5. In the _Configuration_ section, edit the previously completed _data collection rule_ by selecting the _pencil_ icon.
    
6. Expand your _Subscription_ under _Scope_ on the _Resources_ tab.
    
    Tip
    
    You can expand the whole _Scope_ hierarchy by selecting the ">" before the _Scope_ column.
    
7. Expand the resource group, and then select Azure virtual machines.
    
    Important
    
    If you don't see any non-Azure Windows machines, open _Azure Arc_ to verify the machines are connected to Azure Arc.
    
8. Select **Next: Collect**.
    
9. Review the different Security Event collection option. The default is Keep _All Security Events_.
    
10. Select **Next: Review + create**.
    
11. Select **Create** to save the Data Collection Rule.
    
12. Wait a minute and then select **Refresh** to see the new data collection rule listed.

# Collect Sysmon event logs
System Monitor (Sysmon) is a Windows system service, and device driver that remains resident across system reboots to monitor and log system activity to the Windows event log once installed on a system. It provides detailed information about process creations, network connections, and changes to file creation time. By collecting the events it generates using Windows Event Collection or SIEM agents and then analyzing them, you can identify malicious or anomalous activity and understand how intruders and malware operate on your network.

Note

Installing and configuring Sysmon is out of the scope of this training. For more information on Sysmon, see [Sysinternals Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon).

After connecting the Sysmon agent to the windows machine, you install the _Windows Forwarded Events_ Content hub solution which includes the _Windows Forwarded Events_ data connector. The data connector allows you to stream all Windows Event Forwarding (WEF) logs from the Windows Servers connected to your Microsoft Sentinel workspace using Azure Monitor Agent (AMA). In the data connector configuration, you create _Data collection rules_ (DCRs) to collect metrics and logs from the client operating system. Perform the following steps to create a DCR and enable Microsoft Sentinel to query the logs:

## Install the solution

Start by installing the solution that contains the data connector.

1. For Microsoft Sentinel in the Azure portal, under **Content management**, select **Content hub**. For Microsoft Sentinel in the Defender portal, select **Microsoft Sentinel** > **Content management** > **Content hub**.
    
2. Search for and select **Windows Forwarded Events**.
    
3. On the details pane, select **Install**.
    

## Configure the data connector

After the solution is installed, connect the data connector.

1. In the Microsoft Sentinel navigation menu expand **Configuration**, and select **Data connectors**.
    
2. Select the **Windows Forwarded Events** Data connector.
    
3. Select **+Create data collections rule**.
    
    [![Screenshot that shows the Basics tab for a new data collection rule.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-windows-hosts-to-azure-sentinel/media/windows-forwarded-events.png)](https://learn.microsoft.com/en-us/training/wwl-sci/connect-windows-hosts-to-azure-sentinel/media/windows-forwarded-events.png#lightbox)
    
4. Fill in the following fields of the _Basic_ tab:
    
    |Setting|Description|
    |---|---|
    |**Rule Name**|A name for the DCR. The name should be something descriptive that helps you identify the rule.|
    |**Subscription**|The subscription to store the DCR. The subscription doesn't need to be the same subscription as the virtual machines.|
    |**Resource group**|A resource group to store the DCR. The resource group doesn't need to be the same resource group as the virtual machines.|
    
5. Select **Next:Resources >**.
    
6. In the _Resources_ tab, expand the **Scope** column, and expand the Microsoft Azure subscription.
    
7. Expand the resource group or groups, and select the virtual machines you want to connect to Microsoft Sentinel.
    
8. Select the **Next: Collect >** button, and select **Custom** radio button.
    
9. As an example, you can enter the following events log location (XPath format) to collect Sysmon events:
    
    XML
    
    ```
    Microsoft-Windows-Sysmon/Operational!*
    ```
    
10. Select the **Add** button to add the Sysmon events log location.
    
11. Select the **Next: Review + create >** button, after validation passes, select **Create**.
    
    [![Screenshot of Log Analytics Sysmon configuration.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-windows-hosts-to-azure-sentinel/media/sysmon-log-location.png)](https://learn.microsoft.com/en-us/training/wwl-sci/connect-windows-hosts-to-azure-sentinel/media/sysmon-log-location.png#lightbox)
    
    Note
    
    At the end of this process, the Azure Monitor Agent is installed on any selected machines that don't already have the agent.
    
12. After the DCR is created, select the **Refresh** button to see the rule. You can also edit or delete existing rules from the **Configuration** section of the connector page.
    

This connector can use the Advanced Security Information Model (ASIM). Microsoft recommends that you use the ASIM normalization. For more information on ASIM, see [Advanced Security Information Model (ASIM)](https://learn.microsoft.com/en-us/azure/sentinel/normalization).

1. On the **Windows Forwarded Events** connector page, **Configuration** section, select the **Deploy** button.
    
2. Fill-in the required fields of the **Custom deployment** ARM template, and select **Review + create**.
    
3. When validation passes, select **Create**

![[Pasted image 20261006142527.png]]
# Summary and resources
You should have learned how to connect Windows devices to the Microsoft Sentinel workspace using the provided data connectors. The connector offers options to control which events to collect.

You should now be able to:

- Connect Azure Windows Virtual Machines to Microsoft Sentinel
- Connect non-Azure Windows hosts to Microsoft Sentinel
- Configure Log Analytics agent to collect Sysmon events
# Connect Common Event Format logs to Microsoft Sentinel

Most vendor-provided connectors utilize the CEF connector. Learn about the Common Event Format (CEF) connector's configuration options.

## Learning objectives

Upon completion of this module, the learner is able to:

- Explain the Common Event Format connector deployment options in Microsoft Sentinel
- Run the deployment script for the Common Event Format connector
# Introduction
You want to send Common Event Format (CEF) log data to the Microsoft Sentinel workspace using the provided data connector.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You need to collect log data from on-premises network appliances. You can use the Common Event Format connector as the network appliances' data is provided in a structured format.

You install an on-premises Linux host used as a forwarder to send the log data. Next, follow the Common Event Format connector page's instructions to run the deployment script on the Linux host. The final step is to configure the network appliances to forward their logs to your Linux host. Now the network appliances send logs to the new Linux host; the Linux host is then forwarding the logs to the Microsoft Sentinel workspace.

By the end of this module, you'll be able to send Common Event Format (CEF) log data to the Microsoft Sentinel workspace using the provided data connector.

After completing this module, you'll be able to:

- Explain the Common Event Format connector deployment options in Microsoft Sentinel
- Run the deployment script for the CEF connector

## Prerequisites

Basic knowledge of operational concepts such as monitoring, logging, and alerting

# Plan for Common Event Format connector
The **Common Event Format (CEF) via AMA** connector uses the **Azure Monitor Agent (AMA)** on a dedicated Linux log forwarder to support communication between your network appliances and Microsoft Sentinel. Many vendor-specific Microsoft Sentinel data connectors use CEF via AMA as their collection mechanism.

The following diagram illustrates the setup when you use a Linux VM in Azure as the forwarder. On-premises Syslog sources securely send events to the Azure Linux VM. AMA on the Linux VM then forwards the logs to your Microsoft Sentinel workspace.

![Diagram of an Azure VM used as a Syslog forwarder to Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-common-event-format-logs-to-azure-sentinel/media/learn-path5-01.png)

Alternatively, you can use a VM in another cloud or an on-premises machine as the forwarder. Syslog sources securely send events to the Linux VM with AMA installed, which then securely forwards the logs to your Microsoft Sentinel workspace.

![Diagram of an on-premises machine used as a Syslog forwarder to Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-common-event-format-logs-to-azure-sentinel/media/learn-path5-02.png)

## Security considerations

Configure the machine's security according to your organization's security policy. For example, configure your network to align with your corporate network security policy and change the daemon's ports and protocols to align with your requirements.

To use TLS communication between the Syslog source and the Syslog forwarder, configure the Syslog daemon (rsyslog or syslog-ng) to communicate in TLS.

## Prerequisites

Make sure the Linux machine you use as a log forwarder is running one of the following 64-bit operating systems:

- Amazon Linux 2 or 2023
- Oracle Linux 8 or 9
- Red Hat Enterprise Linux (RHEL) Server 8 or 9
- Debian GNU/Linux 10, 11, or 12
- Ubuntu Linux 20.04 LTS, 22.04 LTS, or 24.04 LTS
- SUSE Linux Enterprise Server 15

Note

AMA supports only 64-bit operating systems.

Supported Syslog daemon versions:

- Syslog-ng: 2.1 - 3.22.1
- Rsyslog: v8

Supported Syslog RFCs:

- Syslog RFC 3164
- Syslog RFC 5424

Your machine must also meet these requirements:

**Permissions**

- You must have elevated permissions (sudo) on your machine.
# Connect your external solution using the Common Event Format connector
You need to designate and configure a Linux machine to forward logs from your security solution to your Microsoft Sentinel workspace. This machine can be physical or virtual in your on-premises environment, an Azure VM, or a VM in another cloud.

The **Common Event Format (CEF) via AMA** connector uses a **Data Collection Rule (DCR)** to configure the **Azure Monitor Agent (AMA)** on your Linux forwarder. AMA handles both agent installation and log forwarding — no manual script installation is required.

When configured, AMA on the Linux forwarder:

- Listens for CEF messages from the built-in Linux Syslog daemon on TCP port 514
- Forwards CEF messages to your Microsoft Sentinel workspace, where they're parsed and enriched

## Set up the CEF via AMA connector

To configure the connector:

1. In the Microsoft Sentinel portal, select **Data connectors**.
    
2. Search for and select **Common Event Format (CEF) via AMA**.
    
3. Select **Open connector page** on the details pane.
    
4. Under **Configuration**, select **+Create data collection rule**.
    
5. On the **Basic** tab, enter a name for the data collection rule, then select your subscription and resource group.
    
6. On the **Resources** tab, select the Linux machine you designated as the log forwarder.
    
7. On the **Collect** tab, confirm the CEF facility and log level settings.
    
8. Select **Review + create**, then select **Create**. AMA is automatically installed on the Linux forwarder if it isn't already present.
    
9. Configure each network appliance to forward its syslog events to your Linux forwarder on UDP or TCP port 514.
    

[![Screenshot of the Common Event Format via AMA connector page in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-common-event-format-logs-to-azure-sentinel/media/common-event-format-connector.png)](https://learn.microsoft.com/en-us/training/wwl-sci/connect-common-event-format-logs-to-azure-sentinel/media/common-event-format-connector.png#lightbox)

## Use the same machine to forward both plain Syslog and CEF messages

If you plan to use this log forwarder machine to forward both plain Syslog messages and CEF messages, edit the Syslog configuration file on each source machine that sends logs in CEF format. Remove the facilities used to send CEF messages to avoid duplicate events in the Syslog and CommonSecurityLog tables.

![[Pasted image 20261006143544.png]]

# Summary and resources
You learned how to send Common Event Format (CEF) log data to the Microsoft Sentinel workspace using the provided data connector.

You should now be able to:

- Explain the CEF Connector deployment options in Microsoft Sentinel
- Run the deployment script for the CEF connector
# Connect syslog data sources to Microsoft Sentinel

Learn about the Azure Monitor Agent Linux Syslog Data Collection Rule configuration options, which enable you to parse Syslog data.

## Learning objectives

Upon completion of this module, the learner is able to:

- Describe the Azure Monitor Agent Data Collection Rule (DCR) for Syslog
- Install and Configure the Azure Monitor Linux Agent extension with the Syslog DCR
- Run the Azure Arc Linux deployment and connection scripts
- Verify Syslog log data is available in Microsoft Sentinel
- Create a parser using KQL in Microsoft Sentinel


# Introduction
You send Syslog log data to the Microsoft Sentinel workspace using an Azure Monitor Agent Data Collection Rule (DCR).

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You need to collect log data from on-premises network appliances. The network appliances' data is provided in an unstructured format.

You install an on-premises Linux host used as a forwarder to send the log data. Next, you follow the instructions to install the Azure Connected Machine agent that enables you to manage your (Windows and) Linux machines hosted outside of Azure on your corporate network with Azure Arc. Once you have verified Azure Arc connectivity, you can install the Azure Monitor Linux Agent extension, and during that process you create an Azure Monitor Syslog Data Collection Rule. The final step is to configure the network appliances to forward their logs to your Linux host.

The network appliances are now sending logs to the new Linux host, and the Linux host is then forwarding the logs to the Microsoft Sentinel workspace via the Azure Monitor Agent Data Collection Rule. In Microsoft Sentinel, you create a parser using a KQL function to make it easier for the Security Operations team to query the log records containing the unstructured string data.

After completing this module, you'll be able to:

- Describe the Azure Monitor Agent Data Collection Rule (DCR) for Syslog
- Install and Configure the Azure Monitor Linux Agent extension with the Syslog DCR
- Run the Azure Arc Linux deployment and connection scripts
- Verify Syslog log data is available in Microsoft Sentinel
- Create a parser using KQL in Microsoft Sentinel

## Prerequisites

- Basic knowledge of operational concepts such as monitoring, logging, and alerting
- Familiarity with Linux operations and monitoring

# Plan for syslog data collection
This article references CentOS, a Linux distribution that is End Of Life (EOL) status. Consider your use and plan accordingly. For more information, see the [CentOS End Of Life guidance](https://learn.microsoft.com/en-us/azure/virtual-machines/workloads/centos/centos-end-of-life).

You can stream events from Linux-based, Syslog-supporting machines or appliances into Microsoft Sentinel using the Azure Monitor Agent for Linux and Data Collection Rules. You can do this streaming for any device that allows you to install the agent directly on the host. The host's native Syslog daemon collects local events of the specified types and forward them locally to the agent, which streams them to your Log Analytics workspace.

Log Analytics supports collecting messages sent by the **rsyslog** or **syslog-ng** daemons, where rsyslog is the default.

## How it works

**Syslog** is an event logging protocol that's common to Linux. When the agent is installed on your VM or appliance, the installation routine configures the local Syslog daemon (rsyslog or syslog-ng) to forward messages to the agent via a local Unix domain socket. The agent then sends the messages to your Log Analytics workspace over HTTPS, where they're parsed into event log entries in the Syslog table in **Microsoft Sentinel > Logs**.

# Collect data from Linux-based sources using syslog
Configuring the Azure Monitor Agent for Syslog on Linux machines:

- [Azure Linux VM](https://learn.microsoft.com/en-us/training/modules/connect-syslog-data-sources-to-azure-sentinel/3-collect-data-from-linux-based-sources-using-syslog?tabs=azure-linux-vm#tabpanel_1_azure-linux-vm)
- [Non-Azure Linux machine](https://learn.microsoft.com/en-us/training/modules/connect-syslog-data-sources-to-azure-sentinel/3-collect-data-from-linux-based-sources-using-syslog?tabs=azure-linux-vm#tabpanel_1_non-azure-linux-machine)

To install the agent on an Azure Linux virtual machine:

1. In the Azure portal, enter **Monitor** in the `Search resources, services, and docs` search bar.
    
2. In **Monitor**, scroll down the left menu to the **Settings** section and select `Data Collection Rules`.
    
3. In **Monitor | Data Collection Rules**, select **+ Create**.
    
    ![Screenshot of the Monitor Data Collection Rule create page.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-syslog-data-sources-to-azure-sentinel/media/03-data-collection-rules-updated.png)
    
4. On the `Data Collection Rule` **Basics** tab, enter a Rule name and specify a Subscription, Resource Group, Region, and Platform Type. For this exercise, select `Linux` for Platform Type.
    
5. Select **Next:Resources**
    
6. On the `Data Collection Rule` **Resources** tab, select **+ Add resources**.
    
7. In the **Select a scope** page, expand the **Scope** column for `Subscription` and `Resource group` types until your target VM is displayed.
    
8. Select the target VM and select **Apply**. You should see your Linux VM displayed as a Resource.
    
    ![Screenshot of the Monitor Data Collection Rule Add resources and Sect a scope pages](https://learn.microsoft.com/en-us/training/wwl-sci/connect-syslog-data-sources-to-azure-sentinel/media/03-data-collection-rule-add-resource.png)
    
9. Select **Next: Collect and deliver**.
    
10. On the `Data Collection Rule` **Collect and deliver** tab, select **+ Add data source**.
    
11. In the **Add data source** page, select **Linux Syslog** from the `Data source type*` drop-down menu, and select **Add data source**. You should see your `Linux Syslog` Data source and a `Destinations(s)` of `Azure Monitor Logs`displayed.
    
12. Select **Review + create**, and **Create** after **Validation passed** is displayed.
    
    Note
    
    This process initiates the Azure Monitor Linux Agent extension install.
    
13. After the process completes, locate **Virtual Machines** in the Azure portal and select the Linux VM you configured as a `Data Collection Rule` resource.
    
14. On the `Virtual machine` Overview, scroll down the left menu to the **Settings** section and select **Extensions + applications**.
    
15. Under the **Extensions** tab, you should see the **AzureMonitorLinuxAgent** displayed.
    
    [![Screenshot of the Azure Monitor Linux Agent on an Azure VM.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-syslog-data-sources-to-azure-sentinel/media/03-azure-monitor-linux-agent-azure-vm.png)](https://learn.microsoft.com/en-us/training/wwl-sci/connect-syslog-data-sources-to-azure-sentinel/media/03-azure-monitor-linux-agent-azure-vm.png#lightbox)
    
    Note
    
    If Microsoft Defender for Cloud Auto-provisioning is enabled, the Azure Monitor Linux Agent is installed by default as an extension using Azure Policy assignment.
# Configure the Data Collection Rule for Syslog Data Sources

The Data Collection Rule (DCR) only collects events with the facilities and severities that are specified in its Data sources configurations. For Syslog, you can modify the `Facility Minimum log level` and `Destination` in the **Add data source** page.

To configure the Syslog `Facility log level`and `Destination`:

1. Access the Data collection rule Data sources **Add data source** page:
    
    - Select **Configuration**, **Data sources**
        
    - Select **Linux Syslog**.
        
2. Select the **Minimum log level** drop-down menu to make changes for each `Facility`.
    
    ![Screenshot of Linux Syslog facilities selections and minimum log levels.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-syslog-data-sources-to-azure-sentinel/media/04-linux-syslog-facilities-log-level.png)
    
3. When completed select **Save**
    
    Note
    
    The default is "LOG_DEBUG" for each Facility, and changes are automatically pushed to all configured resources.
# Parse syslog data with KQL


The Syslog collector writes log data to the Syslog table. One difference from the CEF Collector is that the message's data is stored in a string field named SyslogMessage. The Common Event Format (CEF) Connector writes to the CommonSecurityLog with the fields already parsed. For Syslog, you need to parse fields on every query that uses the Syslog table or write a Parser. A Parser is a KQL Function that is a query saved as a function and then referenced with the function name. The reference to the function name is like accessing any other table. By creating parses, you only need to write the SyslogMessage parsing once.

In the Logs window, create a query, select the Save button, and select Function from the drop-down. Then specify function name and alias. For example, if you create a function named MyParser, you can then access the table using that name.

Kusto

```
Syslog
| where ProcessName contains "squid"
| extend URL = extract("(([A-Z]+ [a-z]{4,5}:\\/\\/)|[A-Z]+ )([^ :]*)",3,SyslogMessage), 
         SourceIP = extract("([0-9]+ )(([0-9]{1,3})\\.([0-9]{1,3})\\.([0-9]{1,3})\\.([0-9]{1,3}))",2,SyslogMessage), 
         Status = extract("(TCP_(([A-Z]+)(_[A-Z]+)*)|UDP_(([A-Z]+)(_[A-Z]+)*))",1,SyslogMessage), 
         HTTP_Status_Code = extract("(TCP_(([A-Z]+)(_[A-Z]+)*)|UDP_(([A-Z]+)(_[A-Z]+)*))/([0-9]{3})",8,SyslogMessage),
         User = extract("(CONNECT |GET )([^ ]* )([^ ]+)",3,SyslogMessage),
         RemotePort = extract("(CONNECT |GET )([^ ]*)(:)([0-9]*)",4,SyslogMessage),
         Domain = extract("(([A-Z]+ [a-z]{4,5}:\\/\\/)|[A-Z]+ )([^ :\\/]*)",3,SyslogMessage)
| extend TLD = extract("\\.[a-z]*$",0,Domain)

```

Kusto

```
MyParser
```

![[Pasted image 20261006150340.png]]

# Summary and resources
In this module, you learned how to send Syslog log data to the Microsoft Sentinel workspace using the Azure Monitor Agent and a Data Collection Rule.

You should now be able to:

- Describe the Azure Monitor Agent Data Collection Rule (DCR) for Syslog
- Run the Azure Arc Linux deployment and connection scripts
- Install and Configure the Azure Monitor Linux Agent extension with the Syslog DCR
- Verify Syslog log data is available in Microsoft Sentinel
- Create a parser using KQL in Microsoft Sentinel

# Connect threat indicators to Microsoft Sentinel

# Introduction
You connect Threat Intelligence Indicators to the Microsoft Sentinel workspace using the Threat Intelligence Content hub solution and the included data connectors.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. Your company has subscriptions to threat intelligence platform services that provide known malicious indicators for use in your detection rules. Threat indicators can include IP addresses, domains, URLs, and file hashes, etc.

You need to configure Microsoft Sentinel to import the indicators of compromise (IoCs) from these services automatically. The first service uses Microsoft Defender Threat Intelligence (MDTI).

The second service uses a TAXII server to allow indicators to be pulled. You configure the TAXII data connector to pull indicators from the service.

The third service, the upload API doesn't use a Microsoft Sentinel data connector, but allows you to directly input "Structured Threat Information Expression" or STIX data.

Now that the threat intelligence indicator data is flowing into Microsoft Sentinel, the SecOps teams can use the indicators as part of their detection queries.

By the end of this module, you're able to connect Threat Intelligence Indicators to the Microsoft Sentinel workspace using the provided data connectors.

After completing this module, you'll be able to:

- View threat indicators in Microsoft Sentinel

## Prerequisites- Configure the Defender Threat Intelligence connector in Microsoft Sentinel

- Configure the TAXII connector in Microsoft SentinelPlatforms connector
- Configure the Threat Intelligence Upload API in Microsoft Sentinel

General experience with Microsoft Defender and Microsoft Azure services

# Plan for threat intelligence connectors
Microsoft Sentinel provides you with data connectors that enable you to import Indicators of Compromise (IOCs) from Microsoft Defender Threat Intelligence (MDTI). The Content hub solutions include the data connectors and the following Microsoft Sentinel components:

- Analytic rules include a set of scheduled rule templates, and you can enable rules to generate alerts and incidents based on matches of log events from your threat indicators.
    
- Workbooks provide summarized information about the threat indicators imported into Microsoft Sentinel and any alerts generated from analytics rules that match your threat indicators.
    
- Hunting queries allow security investigators to use threat indicators within the context of common hunting scenarios.
    
- Playbooks run preconfigured sets of remediation actions to help automate and orchestrate your threat response.
    

You can stream threat indicators to Microsoft Sentinel by using an MDTI based connector, one of the integrated Threat Intelligence Platform (TIP) products, connecting to TAXII servers, or direct integration with the Microsoft Graph Security Indicators API.

There are five Threat Intelligence Data Connectors:

- Threat intelligence - TAXII
- Microsoft Defender Threat Intelligence
- Premium Microsoft Defender Threat Intelligence
- Threat Intelligence Platforms
- Threat Intelligence Upload API (Preview)

All the data connectors write to the _ThreatIntelligenceIndicator_ table, and the data connectors all have different configuration procedures.

# Connect the Defender Threat Intelligence connector
Bring public, open-source, and high-fidelity indicators of compromise (IOCs) generated by Microsoft Defender Threat Intelligence (MDTI) into your Microsoft Sentinel workspace with the Defender Threat Intelligence data connectors.

You're a Security Operations Analyst at a mid-sized organization tasked with improving your company's threat detection and response capabilities. Your manager asked you to integrate Microsoft's high-fidelity threat intelligence into your Microsoft Sentinel workspace. You enable and configure the Microsoft Defender Threat Intelligence data connector, verify its functionality, and use the ingested data to enhance security operations.

## Install the Threat Intelligence solution in Microsoft Sentinel using the Content hub

Install the Threat Intelligence solution in Microsoft Sentinel to enable the ingestion of threat intelligence data from Microsoft Defender Threat Intelligence.

1. Open the [Azure portal](https://portal.azure.com/) or the [Defender portal](https://security.microsoft.com/).
2. Navigate to **Microsoft Sentinel**.
3. Under **Content management**, select **Content hub**.
4. Search for the **Threat Intelligence** solution in the Content hub.
5. Select the **Threat Intelligence** solution from the search results.
6. Select the **Install/Update** button to install the solution.
7. Wait for the installation to complete.

## Enable the Microsoft Defender Threat Intelligence data connector in Microsoft Sentinel

Enable the Microsoft Defender Threat Intelligence data connector to start ingesting threat intelligence data into your Microsoft Sentinel workspace.

1. Open the [Azure portal](https://portal.azure.com/) or the [Defender portal](https://security.microsoft.com/).
    
2. Navigate to **Microsoft Sentinel**.
    
3. Under **Configuration**, select **Data connectors**.
    
4. Search for the **Defender Threat Intelligence** data connector (either standard or premium version).
    
    [![Screenshot that shows the Defender Threat Intelligence Data connectors.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-threat-indicators-to-azure-sentinel/media/premium-microsoft-defender-threat-intelligence-data-connector-config.png)](https://learn.microsoft.com/en-us/training/wwl-sci/connect-threat-indicators-to-azure-sentinel/media/premium-microsoft-defender-threat-intelligence-data-connector-config.png#lightbox)
    
5. Select the data connector and select the **Open connector page** button.
    
6. On the connector page, select the **Connect** button to enable the feed.
    
7. Confirm that the connector status changes to **Connected**.
    
    [![Screenshot that shows the Defender Threat Intelligence Data connector page and the Connect button.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-threat-indicators-to-azure-sentinel/media/premium-connect.png)](https://learn.microsoft.com/en-us/training/wwl-sci/connect-threat-indicators-to-azure-sentinel/media/premium-connect.png#lightbox)
# Connect the threat intelligence TAXII connector

Microsoft Sentinel integrates with TAXII 2.0 and 2.1 data sources to enable monitoring, alerting, and hunting using your threat intelligence. Use this connector to send threat indicators from TAXII servers to Microsoft Sentinel. Threat indicators can include IP addresses, domains, URLs, and file hashes.

In the Azure portal, navigate to Microsoft Sentinel > Data connectors and then select the Threat Intelligence - TAXII connector.

To view the connector page:

1. Select Data connectors page.
    
2. Select **Threat intelligence - TAXII**.
    
3. select the **Open connector** page on the preview pane.
    
4. Specify the required and optional information in the text boxes.
    
    - Friendly name (for server)
        
    - API root URL
        
    - Collection ID
        
    - Username
        
    - Password
        
5. Select **Add** to enable the connection.
    

The list of configure TAXII servers shows the currently connected TAXII servers and the last indicator received time. The ellipse at the end of the configured server provides the option to remove the server configuration.

[![Screenshot of the Sentinel T A X I I Connector page.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-threat-indicators-to-azure-sentinel/media/taxii-connectors.png)](https://learn.microsoft.com/en-us/training/wwl-sci/connect-threat-indicators-to-azure-sentinel/media/taxii-connectors.png#lightbox)

# Connect the threat intelligence Upload API connector
Your organization is using threat intelligence platform (TIP) solutions to aggregate threat intelligence feeds from various sources. The industry standard for describing cyberthreat information is called, "Structured Threat Information Expression" or STIX. By using the "Threat Intelligence Upload API" which supports STIX objects, your organization can ingest custom threat intelligence data into Microsoft Sentinel. The Threat Intelligence Upload API is installed as part of the Microsoft Sentinel Threat Intelligence solution, and managed like a data connector, but the upload API ingests threat intelligence into Microsoft Sentinel without the need for a data connector.

![Screenshot that shows the threat intelligence import path.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-threat-indicators-to-azure-sentinel/media/threat-intel-upload-api.png)

Important

The Microsoft Sentinel threat intelligence upload API is in preview. See the [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) for more legal terms that apply to Azure features that are in beta, preview, or otherwise not yet released into general availability.

### Prerequisites

- You must have read and write permissions to the Microsoft Sentinel workspace to store your threat intelligence STIX objects.
- You must be able to register a Microsoft Entra application.
- Your Microsoft Entra application must be granted the Microsoft Sentinel Contributor role at the workspace level.

### Configuring the Threat Intelligence Upload API

## Instructions

Follow these steps to import threat intelligence STIX objects to Microsoft Sentinel from your integrated TIP or custom threat intelligence solution:

1. Register a Microsoft Entra application, and then record its application ID.
2. Generate and record a client secret for your Microsoft Entra application.
3. Assign your Microsoft Entra application the Microsoft Sentinel Contributor role or the equivalent.
4. Configure your TIP solution or custom application.

## Register a Microsoft Entra application

The [default user role permissions](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions) allow users to create application registrations. If this setting was switched to **No**, you need permission to manage applications in Microsoft Entra. Any of the following Microsoft Entra roles include the required permissions:

- Application administrator
- Application developer
- Cloud application administrator

After you register your application, record its application (client) ID from the application's **Overview** tab.

## Assign a role to the application

The upload API ingests threat intelligence objects at the workspace level and requires the role of Microsoft Sentinel Contributor.

1. From the Azure portal, go to **Log Analytics workspaces**.
    
2. Select **Access control (IAM)**.
    
3. Select **Add** > **Add role assignment**.
    
4. On the **Role** tab, select the **Microsoft Sentinel Contributor** role, and then select **Next**.
    
5. On the **Members** tab, select **Assign access to** > **User, group, or service principal**.
    
6. Select members. By default, Microsoft Entra applications aren't displayed in the available options. To find your application, search for it by name.
    
    ![Screenshot that shows the Microsoft Sentinel Contributor role assigned to the application at the workspace level.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-threat-indicators-to-azure-sentinel/media/assign-role.png)
    
7. Select **Review + assign**.
    

## Configure your threat intelligence platform solution or custom application

The following configuration information is required by the upload API:

- Application (client) ID
- Microsoft Entra access token with [OAuth 2.0 authentication](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols)
- Microsoft Sentinel workspace ID

Enter these values in the configuration of your integrated TIP or custom solution where required.

1. Submit the threat intelligence to the upload API. For more information, see [Microsoft Sentinel upload API](https://learn.microsoft.com/en-us/azure/sentinel/stix-objects-api).
2. Within a few minutes, threat intelligence objects should begin flowing into your Microsoft Sentinel workspace. Find the new STIX objects on the **Threat intelligence** page, which is accessible from the Microsoft Sentinel menu.

# View your threat indicators with KQL
The indicators reside in the ThreatIntelligenceIndicator table. This table is the basis for queries performed by other Microsoft Sentinel features such as Analytics and Workbooks. Here's how to find and view your threat indicators in the ThreatIntelligenceIndicator table.

To view your threat indicators with KQL. Select Logs from the General section of the Microsoft Sentinel menu. Then run a query on the ThreatIntelligenceIndicator.

Kusto

```
`ThreatIntelligenceIndicator`

```

Important

On April 3, 2025, we publicly previewed two new tables to support STIX indicator and object schemas: `ThreatIntelIndicators` and `ThreatIntelObjects`. Microsoft Sentinel will ingest all threat intelligence into these new tables, while continuing to ingest the same data into the legacy `ThreatIntelligenceIndicator` table until July 31, 2025. **Be sure to update your custom queries, analytics and detection rules, workbooks, and automation to use the new tables by July 31, 2025.** After this date, Microsoft Sentinel will stop ingesting data to the legacy `ThreatIntelligenceIndicator` table. We're updating all out-of-the-box threat intelligence solutions in Content hub to leverage the new tables. For more information about the new table schemas, see [ThreatIntelIndicators](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/threatintelindicators) and [ThreatIntelObjects](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/threatintelobjects).

![[Pasted image 20261006152410.png]]

# Summary and resources
You learned how to connect Threat Intelligence Indicators to the Microsoft Sentinel workspace using the provided data connectors.

You should now be able to:

- Configure the Defender Threat Intelligence connector in Microsoft Sentinel
- Configure the TAXII connector in Microsoft SentinelPlatforms connector
- Configure the Threat Intelligence Upload API in Microsoft Sentinel
- View threat indicators in Microsoft Sentinel
# Explain threat hunting concepts in Microsoft Sentinel
# Introduction
Microsoft Sentinel provides the tools to perform Threat Hunting. Before starting the hunt, it's crucial to understand the Threat Hunting process.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You want to mature your Security Operations team to proactively hunt for malicious activity in your environment.

You suggest to management to create a threat hunting team. You must explain to management the benefit, processes, and tasks of a threat hunting team. You'll demonstrate how to develop a quality hypothesis for hunting.

After completing this module, you'll be able to:

- Describe threat hunting concepts for use with Microsoft Sentinel
- Define a threat hunting hypothesis for use in Microsoft Sentinel

## Prerequisites

Basic knowledge of operational concepts such as monitoring, logging, and alerting

# Understand cybersecurity threat hunts
The term "threat hunting" is defined differently by different people. The most commonly used definition is the idea that you're proactively hunting through your environment for a threat or a set of activities that you haven't previously detected. The "not previously detected" part is what differentiates threat hunting from incident response or alert triage.

Other uses of the term hunting include searching for threats with newly obtained indicators. If a Threat Intelligence Feed provides a new IP Address considered harmful, an analyst can then take the IP Address and search the logs to find if the new indicator was seen in the past. Technically this isn't threat hunting because you're using a known bad such as an IP Address. Microsoft Sentinel already provides hunting queries to facilitate this process. Next, hunt for more evidence-based threats from a current Incident or Alert as part of an Incident Analysis process. It's vital to explore data based on evidence found in a current incident. Both Microsoft Sentinel and Microsoft Defender XDR provide this type of hunting capability.

All of these approaches have one thing in common: using KQL queries to find threats.

Microsoft Defender and Microsoft Defender Endpoint are more focused on indicator and analysis types of hunting. Microsoft Sentinel provides more features to manage the threat hunting process.

## Proactive hunts

Why do proactive hunting? As you hunt for "not previously detected" threats, the concern is that if you wait for the threat to be detected, the compromise impact could be more significant. If we don't have a known indicator, then what are we hunting? We hunt based on a Hypothesis. The Hypothesis might start with "Operational Threat Intelligence," and then list the attackers' tactics and techniques. A Hypothesis can search for a specific technique, not an indicator like an IP address. If malicious activity is identified, we might have discovered the attacker earlier in the attack process before they have an opportunity to exfiltrate data.

## Process to hunt threats

![Diagram of the Cyber Threat Hunting Process.](https://learn.microsoft.com/en-us/training/wwl-sci/what-is-threat-hunting-azure-sentinel/media/learn-plan-8.png)

Threat hunting should be a continual process. We start at the top of our cycle with our Hypothesis. Our Hypothesis helps us plan out what we are going to hunt for, which requires us to understand where we're going to hunt and how we'll do it. This means we need to understand the data we have, the tools we have, the expertise we have, and how to work with them. The hunting cycle doesn't stop when we execute the hunt. There are still several phases we need to conduct throughout the life cycle, including responding to anomalies. Even if we don't find an active threat, there will be activities to perform.

Routine tasks should include:

- Setting up new monitoring.
    
- Improving our detection capabilities.
    

Everything done in Threat Hunting should be documented. Documentation for the hunt should include:

- What, How, and Why
    
- Input and Output
    
- How to replicate the hunt
    
- Next Steps
# Develop a hypothesis

Hunting starts with a Hypothesis. The idea of what we are going to hunt. Getting this right is critical because it drives our focuses on what we are going to do. What makes a good Hypothesis?

There are many factors, but here are the key ones:

**Keep it achievable**. Don't perform a hunt where you know you have no hope of finding results. It could be that you don't have the data available, or have insufficient knowledge about the threat to understand how to find it.

**Keep the scope narrow**. Avoid broad a hypothesis such as "I'm going to hunt for strange log-ons." Such a hypothesis fails to define what the results could mean.

**Keep it time-bound**. Are you looking for any sign-ins since the beginning of your logs? Are you looking for last week? The last day? The time-bounded also is used in documentation. You'll want Threat Hunting to be a continual process. If you don't time-bound your hunts, there's a chance that you'll end up just repeating the same hunt on the same dataset. You'll be able to say, "I did this hunt, at this time, covering this period." With this documented, your team members will know what period was hunted for with this Hypothesis.

**Keep it useful and efficient**. You want to target threats that maybe you don't have adequate coverage for in your detections. These might be things that you know that you've previously missed or that you haven't detected. A good SOC team typically has a good idea about where their coverage is good and where it may be weaker and needs improvement. You also want to make sure it relates to realistic threats. There's no point in hunting for an advanced threat that targets an industry you're not in or a platform you aren't using.

**Keep it related to the threat model that you are defending against**. Otherwise, you may spend much time threat hunting for things that you'll never find and which aren't a threat.

Don't start your Threat Hunting journey going after the most advanced threats. Start with the basics and incrementally mature your organization's Threat Hunting capabilities. Start with a simple Hunt Hypothesis. An example hypothesis could be that we have Threat Intel that a Threat Actor, has automated attacks that use the cmd.exe process.

Another Hypothesis could be; We want to check for the last day in which accounts have run cmd.exe, but that have not run cmd.exe during the past week.

# Explore MITRE ATT&CK
MITRE ATT&CK is a publicly accessible knowledge base of tactics, techniques, and procedures (TTP) that are commonly used by attackers, and is created and maintained by observing real-world observations. Many organizations use the MITRE ATT&CK knowledge base to develop specific threat models and methodologies that are used to verify security status in their environments.

Microsoft Sentinel analyzes ingested data, not only to detect threats and help you investigate, but also to visualize the nature and coverage of your organization's security status.

When developing a threat hunting hypothesis, it's critical to understand the tactics (why), techniques (how), and procedures (implementations) you're searching for. The MITRE ATT&CK framework is used throughout Microsoft Sentinel.

Use the MITRE ATT&CK selection under Threat Management in Microsoft Sentinel to view the detections already active in your workspace, and those available for you to configure, to understand your organization's security coverage, based on the tactics and techniques from the MITRE ATT&CK® framework.

## View current MITRE coverage

- [Defender portal](https://learn.microsoft.com/en-us/training/modules/what-is-threat-hunting-azure-sentinel/3a-explore-mitre-att-ck?tabs=defender-portal#tabpanel_1_defender-portal)
- [Azure portal](https://learn.microsoft.com/en-us/training/modules/what-is-threat-hunting-azure-sentinel/3a-explore-mitre-att-ck?tabs=defender-portal#tabpanel_1_azure-portal)

In Microsoft Sentinel, in the [Defender portal](https://security.microsoft.com/), select the _Threat management_ section of the navigation menu, select MITRE ATT&CK. By default, Active scheduled query, Active near real-time (NRT) rules, and Active anomaly query rules are indicated in the coverage matrix.

- **Use the legend at the top-right** to understand how many detections are currently active in your workspace for specific technique.
    
- **Use the search bar** at the top right to search for a specific technique in the matrix, using the technique name or ID, to view your organization's security status for the selected technique.
    
- **Select a specific technique** in the top row of the matrix to view in the details pane on the right. There, use the links to jump to any of the following locations:
    
    - Select _View full tactic or technique details_ links for more information in the MITRE ATT&CK framework knowledge base.
        
    - Select links to any of the _Active coverage_ rules to jump to the relevant area in Microsoft Sentinel.
        
- **View MITRE by threat scenarios** to view the coverage matrix by threat scenarios:
    
    - Drag the **View MITRE by threat scenarios** slider to the right to view the coverage matrix by threat scenarios. The matrix is filtered to show only the techniques that are relevant to the selected scenario.
        
        [![Screenshot of the MITRE ATT&CK threat scenarios drop down menu.](https://learn.microsoft.com/en-us/training/wwl-sci/what-is-threat-hunting-azure-sentinel/media/mitre-threat-hunting-scenario.png)](https://learn.microsoft.com/en-us/training/wwl-sci/what-is-threat-hunting-azure-sentinel/media/mitre-threat-hunting-scenario.png#lightbox)
        

## Simulate possible rules coverage

In the MITRE matrix, simulated coverage refers to detections that are available, but not currently configured, in your Microsoft Sentinel workspace. View your simulated coverage to understand your organization's possible security status, were you to configure all detections available to you.

Important

If you have the _View MITRE by threat scenarios_ slider enabled, and have selected a scenario, the Simulated rules (Product simulation) will be disabled.

- From the Microsoft Defender navigation menu, expand the Microsoft Sentinel section, and select _Threat management_, then select MITRE ATT&CK.
    
- Select items in the Simulated rules drop-down menu to simulate your organization's possible security status.
    
- For example, select **Hunting queries**, and then select _Hunting queries_ **View** link to jump to the Microsoft Sentinel Hunting page. There, you see a filtered list of the hunting queries that are associated with the selected technique, and available for you to configure in your workspace.
    

## Use the MITRE ATT&CK framework in analytics rules and incidents

Having a scheduled analytical rule with MITRE techniques applied running regularly in your Microsoft Sentinel workspace enhances the security status shown for your organization in the MITRE coverage matrix.

- **Analytics rules:**
    
    - When configuring analytics rules, select specific MITRE techniques to apply to your rule.
        
    - When searching for analytics rules, filter the rules displayed by technique to find your rules quicker.
        
        [![Screenshot of the MITRE ATT&CK analytics rules configuration.](https://learn.microsoft.com/en-us/training/wwl-sci/what-is-threat-hunting-azure-sentinel/media/mitre-analytic-rule-technique.png)](https://learn.microsoft.com/en-us/training/wwl-sci/what-is-threat-hunting-azure-sentinel/media/mitre-analytic-rule-technique.png#lightbox)
        
- **Incidents:**
    

When incidents are created for alerts that are surfaced by rules with MITRE techniques configured, the techniques are also added to the incidents.

- **Threat hunting:**
    
    - When creating a new hunting query, select the specific tactics and techniques to apply to your query.
        
    - When searching for active hunting queries, filter the queries displayed by tactics by selecting an item from the list above the grid. Select a query to see tactic and technique details on the right.
        
    - When creating bookmarks, either use the technique mapping inherited from the hunting query, or create your own mapping.
![[Pasted image 20261006154033.png]]

# Summary and resources
You should have learned how to use a threat hunting process to proactively hunt for threats in Microsoft Sentinel.

You should now be able to:

- Describe threat hunting concepts for use with Microsoft Sentinel
- Define a threat hunting hypothesis for use in Microsoft Sentinel

# Use Search jobs in Microsoft Sentinel
# Introduction
In Microsoft Sentinel, you can search across long time periods in large datasets by using a search job. You also have the option to restore archived logs to include in the search job.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You discover a new indicator of Compromise (IoC) and need to investigate if it has been previously seen in the logs. You need to restore archive logs and run a search job to discover previous instances of the IoC.

After completing this module, you'll be able to:

- Use Search Jobs in Microsoft Sentinel
- Restore archive logs in Microsoft Sentinel

## Prerequisites

Basic knowledge of operational concepts such as Kusto Query Language (KQL), logging, and archiving

Important

[Microsoft Sentinel is generally available in the Microsoft Defender portal](https://security.microsoft.com/), including for customers without Microsoft Defender XDR or an E5 license.

Starting in **July 2026**, all customers using Microsoft Sentinel in the Azure portal will be redirected to the Defender portal and will use Microsoft Sentinel in the Defender portal only. Starting in **July 2025**, many new customers are automatically onboarded and redirected to the Defender portal.

If you're still using Microsoft Sentinel in the Azure portal, we recommend that you start planning your transition to the Defender portal to ensure a smooth transition and take full advantage of the unified security operations experience offered by Microsoft Defender. For more information, see [It’s Time to Move: Retiring Microsoft Sentinel’s Azure portal for greater security](https://techcommunity.microsoft.com/blog/microsoft-security-blog/planning-your-move-to-microsoft-defender-portal-for-all-microsoft-sentinel-custo/4428613).

# Hunt with a Search Job
One of the primary activities of a security team is to search logs for specific events. For example, you might search logs for the activities of a specific user within a given time-frame.

In Microsoft Sentinel, you can search across long time periods in large datasets by using a search job. While you can run a search job on any type of log, search jobs are ideally suited to search archived logs. If you need to do a full investigation on archived data, you can restore that data into the hot cache to run high performing queries and analytics.

## Search large datasets

Use a search job when you start an investigation to find specific events in logs within a given time frame. You can search all your logs to find events that match your criteria and filter through the results.

Search in Microsoft Sentinel is built on top of search jobs. Search jobs are asynchronous queries that fetch records. The results are returned to a search table that's created in your Log Analytics workspace after you start the search job. The search job uses parallel processing to run the search across long time spans, in large datasets. So search jobs don't impact the workspace's performance or availability.

Search results remain in a search results table that has a ***_SRCH** suffix.

## Supported log types

Use search to find events in any of the following log types:

- Analytics logs (no charges apply)
- Basic logs
- Auxiliary logs

## Limitations of a search job

Before you start a search job, be aware of the following limitations:

- Optimized to query one table at a time.
- Search date range is up to one year.
- Supports long running searches up to a 24-hour timeout.
- Results are limited to one million records in the record set.
- Concurrent execution is limited to five search jobs per workspace.
- Limited to 100 search results tables per workspace.
- Limited to 100 search job executions per day per workspace.

## Start a search job

Go to Microsoft Sentinel in the Azure portal, or in the Microsoft Defender portal, to enter your search criteria. Depending on the size of the target dataset, search times vary. While most search jobs take a few minutes to complete, searches across massive data sets that run up to 24 hours are also supported.

1. For Microsoft Sentinel in the [Defender portal](https://security.microsoft.com/), select **Microsoft Sentinel** > **Data lake exploration** > **Search & restore**. For Microsoft Sentinel in the [Azure portal](https://portal.azure.com/), under **General**, select **Search**.
    
2. Select the **Table** menu and choose a table for your search.
    
3. In the **Search** box, enter a search term.
    
    - [Defender portal](https://learn.microsoft.com/en-us/training/modules/use-search-jobs-microsoft-sentinel/2-hunt-search-job?tabs=defender-portal#tabpanel_1_defender-portal)
    - [Azure portal](https://learn.microsoft.com/en-us/training/modules/use-search-jobs-microsoft-sentinel/2-hunt-search-job?tabs=defender-portal#tabpanel_1_azure-portal)
    
    [![Screenshot of search page with search criteria of administrator, time range last 90 days, and table selected.](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/search-job-defender-portal.png)](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/search-job-defender-portal.png#lightbox)
    
4. Enter a **keyword** for your search.
    
    Note
    
    A keyword is a word or phrase that you want to search for in the selected table. You can use operators such as AND, OR, and NOT to refine your search. For example, if you want to search for events related to a specific user, you can enter the user's name as the keyword.
    
5. Select the **Start** to open the advanced Kusto Query Language (KQL) editor and preview of the results for a set time range.
    
    Note
    
    This opens the advanced KQL editor in the Azure portal.
    
6. Change the KQL query as needed and select **Run** to get an updated preview of the search results.
    
    ![Screenshot of KQL editor with revised search.](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/search-job-advanced-kql-edit.png)
    
7. When you're satisfied with the query and the search results preview, select the ellipses **...** and toggle **Search job mode** on.
    
    [![Screenshot of KQL editor with revised search with ellipsis highlighted for Search job mode.](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/search-job-advanced-kql-ellipsis.png)](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/search-job-advanced-kql-ellipsis.png#lightbox)
    
8. Specify the search job date range using the **Time range** selector. If your query also specifies a time range, Microsoft Sentinel runs the search job on the union of the time ranges.
    
9. When you're ready to start the search job, select **Search job**.
    
10. Enter a new table name to store the search job results.
    
11. Select **Run a search job**.
    
12. Wait for the notification **Search job is done** to view the results.
    

## View search job results

View the status and results of your search job by going to the **Saved Searches** tab.

- [Defender portal](https://learn.microsoft.com/en-us/training/modules/use-search-jobs-microsoft-sentinel/2-hunt-search-job?tabs=defender-portal#tabpanel_2_defender-portal)
- [Azure portal](https://learn.microsoft.com/en-us/training/modules/use-search-jobs-microsoft-sentinel/2-hunt-search-job?tabs=defender-portal#tabpanel_2_azure-portal)

1. In Microsoft Sentinel in the Defender portal, select **Data lake exploration** > **Search & restore**> **Saved Searches**.
    
2. On the search card, select **View search results**.
    
    [![Screenshot that shows the link to view search results at the bottom of the search job card.](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/view-search-results.png)](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/view-search-results.png#lightbox)
    
3. This takes you to the Advanced Hunting page with the KQL query prepopulated.
    
    [![Screenshot that shows search results displayed in the Advanced Hunting page.](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/search-results-hunting-page.png)](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/search-results-hunting-page.png#lightbox)
    
4. Select **Run query** to see all the results that match your original search criteria.
    
5. To refine the list of results returned from the search table, select **Add filter**.
# Restore historical data
When you need to do a full investigation on data stored in archived logs, restore a table from the Search page in Microsoft Sentinel. Specify a target table and time range for the data you want to restore. Within a few minutes, the log data is restored and available within the Log Analytics workspace. Then you can use the data in high-performance queries that support full KQL.

A restored log table is available in a new table that has a ***_RST** suffix. The restored data is available as long as the underlying source data is available. But you can delete restored tables at any time without deleting the underlying source data. To save costs, we recommend you delete the restored table when you no longer need it.

## Limitations of log restore

Before you start to restore an archived log table, be aware of the following limitations:

- Restore data for a minimum of two days.
- Restore up to 60 TB.
- Restore is limited to one active restore per table.
- Restore up to four archived tables per workspace per week.
- Limited to two concurrent restore jobs per workspace.

Note

Tables with the Auxiliary table plan don't support data restore. Use a search job to retrieve data that's in long-term retention from an Auxiliary table.

## Restore archived log data

To restore archived log data in Microsoft Sentinel, specify the table and time range for the data you want to restore. Within a few minutes, the log data is available within the Log Analytics workspace. Then you can use the data in high-performance queries that support full Kusto Query Language (KQL).

Restore archived data directly from search or from a saved search.

1. In the [Defender portal](https://security.microsoft.com/), select **Microsoft Sentinel** > **Data lake exploration** > **Search & restore**. In the [Azure portal](https://portal.azure.com/), the **Search** page is listed under **General**.

- [Defender portal](https://learn.microsoft.com/en-us/training/modules/use-search-jobs-microsoft-sentinel/3-restore-historical-data?tabs=defender-portal#tabpanel_1_defender-portal)
- [Azure portal](https://learn.microsoft.com/en-us/training/modules/use-search-jobs-microsoft-sentinel/3-restore-historical-data?tabs=defender-portal#tabpanel_1_azure-portal)

1. Restore log data using one of the following methods:
    
    - Select ![](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/restore-button.png) **Restore** at the top of the page. In the **Restoration** pane on the side, select the table and time range you want to restore, and then select **Restore at the bottom of the pane**.
        
        ![Screenshot of restoring a specific site search.](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/restore-defender.png)
        
    - Select **Saved searches**, locate the search results you want to restore, and then select **Restore**. If you have multiple tables, select the one you want to restore and then select **Actions > Restore** in the side pane. For example:
        
        ![Screenshot of restoring a saved search in the Defender portal.](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/restore-defender-saved.png)
        
2. Wait for the log data to be restored. View the status of your restoration job by selecting on the **Restoration** tab.
    

## View restored log data

View the status and results of the log data restore by going to the **Restoration** tab. You can view the restored data when the status of the restore job shows **Data Available**.

1. In Microsoft Sentinel, select **Search** > **Restoration**.
    
2. When your restore job is complete and the status is updated, select the table name and review the results.
    
    In the [Azure portal](https://portal.azure.com/), results are shown in the **Logs** query page. In the [Defender portal](https://security.microsoft.com/), after you select the table name on the **Microsoft Sentinel** > **Data lake exploration** > **Search & restore** > **Restoration** tab, results are shown in the **Advanced hunting** page.
    
    For example:
    
    ![Screenshot that shows the logs query pane with the restored table results.](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/restored-data-logs-view-defender.png)
    
    The **Time range** is set to a custom time range that uses the start and end times of the restored data.
    

## Delete restored data tables

To save costs, we recommend you delete the restored table when you no longer need it. When you delete a restored table, the underlying source data isn't deleted.

1. In the [Defender portal](https://security.microsoft.com/), go to **Microsoft Sentinel** > **Data lake exploration** > **Search & restore** > **Restoration** and identify the table you want to delete.
    
2. Select **Delete** for that table row to delete the restored table.
    

For example:

[![Screenshot that shows the delete restored table page in the Defender portal.](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/delete-restore.png)](https://learn.microsoft.com/en-us/training/wwl-sci/use-search-jobs-microsoft-sentinel/media/delete-restore.png#lightbox)

![[Pasted image 20261006155708.png]]

# Summary and resources
You should have learned how to perform search on large datasets in Microsoft Sentinel.

You should now be able to:

- Create and view a Search Job in Microsoft Sentinel
- Restore archived logs in Microsoft Sentinel

# Threat hunting with Microsoft Sentinel

# Introduction


Use Microsoft Sentinel to hunt for security threats across on-premises and cloud environments by using interactive queries and other tools.

This module imagines a midsize financial services company called Contoso, Ltd., based in London with a New York branch office. Contoso uses Microsoft 365, Microsoft Entra ID, Microsoft Entra ID Protection, Microsoft Defender for Cloud Apps, Microsoft Defender for Identity, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Endpoint Protection, and Azure Information Protection.

As part of the Security Operations Center team, you've been tasked with using Microsoft Sentinel to identify security threats within Contoso's Azure environment.

By the end of this module, you'll be able to hunt for threats by using the tools available in Microsoft Sentinel. Specifically, you'll be able to proactively identify threat behaviors by using Microsoft Sentinel queries. You'll also be able to use hunts and bookmarks to identify specific account usage patterns for Contoso's Azure environment.

## Learning objectives

After completing this module, you'll be able to:

- Use queries to hunt for threats.
- Save key findings with bookmarks.
- Track threat-hunting investigations with hunts.

## Prerequisites

To get the best learning experience from this module, you should have the following:

- Familiarity with security operations in an organization.
- Basic experience with configuring Azure services, specifically Azure Policy.
- Basic knowledge of operational concepts such as monitoring, logging, and alerting.
- Basic Microsoft Sentinel functionality.
- Access to a Microsoft Azure subscription for exercise tasks.

Note

If you perform the exercises in this module, you might incur costs in your Azure subscription. To estimate the costs, see [Microsoft Sentinel pricing](https://azure.microsoft.com/pricing/details/microsoft-sentinel).

# Exercise setup
To complete this optional exercise, you need access to an Azure subscription to create Azure resources. If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn_d962b2a3-bada-e73a-9abb-f6fc9e258528) before you begin.

Note

If you perform the exercises in this module, you might incur costs in your Azure subscription. To estimate the costs, see [Microsoft Sentinel pricing](https://azure.microsoft.com/pricing/details/microsoft-sentinel).

To deploy the prerequisites for the exercise, perform the following tasks.

## Deploy the Azure Resource Manager template for the exercise environment

1. Select the following link:
    
    [![Deploy To Azure.](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftDocs%2Fmslearn-security-ops-sentinel%2Fmain%2Fmslearn-hunt-threats-sentinel%2Fsentinel-template.json?azure-portal=true)
    
    You're prompted to sign in to Azure.
    
2. On the **Custom deployment** page, provide the following information:
    
    |Name|Description|
    |---|---|
    |**Subscription**|Select your Azure subscription.|
    |**Resource Group**|Select **Create new** and provide a name for the resource group, such as `azure-sentinel-rg`.|
    |**Region**|Select an Azure region.|
    |**Workspace name**|Provide a unique name for the Microsoft Sentinel workspace, such as `<yourName>-sentinel`, where _<yourName>_ represents the workspace name that you chose in the previous task.|
    |**Location**|Accept the default value **[resourceGroup().location]**.|
    |**Simplevm Name**|Accept the default value **simple-vm**.|
    |**Simplevm Windows OS Version**|Accept the default value **2022-Datacenter**.|
    
3. Select **Review + create**, and then select **Create**.
    
    ![Screenshot of the Custom Deployment page.](https://learn.microsoft.com/en-us/training/wwl-sci/hunt-threats-sentinel/media/02-custom-deployment.png)
    
    Note
    
    Wait for the deployment to finish. The deployment should take less than five minutes.
    

## Check created resources

1. In the Azure portal, search for **Resource groups**.
    
2. Select your resource group.
    
3. Sort the list of resources by **Type**.
    
4. The resource group should contain the resources displayed in this table:
    
    |Name|Type|Description|
    |---|---|---|
    |`<yourName>-sentinel`|Log Analytics workspace|Log Analytics workspace used by Microsoft Sentinel, where _<yourName>_ represents the workspace name that you chose in the previous task.|
    |`simple-vmNetworkInterface`|Network interface|Network interface for the virtual machine (VM).|
    |`SecurityInsights(<yourName>-sentinel)`|Solution|Security insights for Microsoft Sentinel.|
    |`simple-vm`|Virtual machine|VM used in the demonstration.|
    |`st1<xxxxx>`|Storage account|Storage account used by the VM, where _<xxxxx>_ represents a random string generated to create a unique storage account name.|
    |`vnet1`|Virtual network|Virtual network for the VM.|
    

## Configure Azure Activity logs

In this task, you use a diagnostic setting to send the Azure Activity log to the Microsoft Sentinel workspace.

1. In the Azure portal, search for and select **Monitor**.
2. On the **Monitor** page, select **Activity log**, and then select **Export Activity Logs**.
3. Select the subscription that contains the exercise resources, and then select **Add diagnostic setting**.
4. Enter a name for the diagnostic setting.
5. Under **Categories**, select the activity log categories that you want to collect.
6. Under **Destination details**, select **Send to Log Analytics workspace**, and then select the subscription and workspace that you created for Microsoft Sentinel.
7. Select **Save**.

Note

Azure Activity log data can take up to 90 minutes to begin flowing to the workspace.

# Explore creation and management of threat-hunting queries
Microsoft Sentinel contains powerful query tools that can help you, as part of the Security Operations Center team, find and isolate security threats and unwanted activity in Contoso's environment.

## Hunt by using built-in queries

You can use the search and query tools in Microsoft Sentinel to hunt for security threats and tactics throughout your environment. These tools let you filter through large amounts of events and security data sources to identify potential threats or track down known or expected threats.

The **Hunting** page in Microsoft Sentinel has built-in queries that can guide your hunting process and help you pursue the appropriate hunting paths to uncover issues in your environment. Hunting queries can expose issues that aren't significant enough on their own to generate an alert but have happened often enough over time to warrant investigation.

[![Screenshot that shows the Hunting page in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/hunt-threats-sentinel/media/3-hunting-page.png)](https://learn.microsoft.com/en-us/training/wwl-sci/hunt-threats-sentinel/media/3-hunting-page.png#lightbox)

The **Hunting** page provides a list all hunting queries. You can filter and sort queries by name, provider, data source, results, and tactics. You can save queries by selecting the **Favorites** star icon for the query in the list.

Tip

When a query is selected as a favorite, it runs automatically each time you open the **Hunting** page.

### Manage hunting queries

When you select a query from the list, the query details appear on a new pane that contains a description, code, and other information about the query. That information includes related entities and identified tactics. You can run a query interactively by selecting **Run Query** on the details pane.

### Hunt for threats by using the MITRE ATT&CK framework

Microsoft Sentinel uses the [MITRE ATT&CK](https://attack.mitre.org/) framework to categorize and order queries by tactics. ATT&CK is a knowledge base of tactics and techniques that are used and observed in the global threat landscape. You can use MITRE ATT&CK to develop and inform your threat-hunting models and methods in Microsoft Sentinel. When you're threat hunting in Microsoft Sentinel, you can use the ATT&CK framework to categorize and run queries by using the MITRE ATT&CK tactics timeline.

Note

You can select individual MITRE ATT&CK tactics from the timeline on the **Hunting** page.

![Screenshot of the tactics timeline on the Hunting page in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/hunt-threats-sentinel/media/3-attack-timeline.png)

Selecting any tactic filters the available queries by the selected tactic. The following Hunting tactics are from the ATT&CK Enterprise and ICS (Industrial Control Systems) matrices:

- **Reconnaissance**. Tactics that the adversary uses to find information they can use to plan future operations.
- **Resource development**. Tactics that the adversary uses to establish resources they can use to support operations. Resources include infrastructure, accounts, or capabilities.
- **Initial access**. Tactics that the adversary uses to gain entry to a network, by exploiting vulnerabilities or configuration weaknesses in public-facing systems. An example is targeted spear-phishing.
- **Execution**. Tactics that result in an adversary running their code on a target system. For example, a malicious hacker might run a PowerShell script to download more attacker tools and/or scan other systems.
- **Persistence**. Tactics that allow an adversary to maintain access to a target system, even after restarts and credential changes. An example of a persistence technique is an attacker who creates a scheduled task that runs their code at a specific time or on restart.
- **Privilege escalation**. Tactics that an adversary uses to gain higher-level privileges on a system, such as local administrator or root.
- **Defense evasion**. Tactics that attackers use to avoid detection. Evasion tactics include hiding malicious code within trusted processes and folders, encrypting or obfuscating adversary code, or disabling security software.
- **Credential access**. Tactics deployed on systems and networks to steal usernames and credentials for reuse.
- **Discovery**. Tactics that adversaries use to obtain information about systems and networks that they want to exploit or use for their tactical advantage.
- **Lateral movement**. Tactics that allow an attacker to move from one system to another within a network. Common techniques include pass-the-hash methods of authenticating users and abuse of the Remote Desktop Protocol.
- **Collection**. Tactics that an adversary uses to gather and consolidate the information they were targeting as part of their objectives.
- **Command and control**. Tactics that an attacker uses to communicate with a system under their control. One example is an attacker communicating with a system over an uncommon or high-numbered port to evade detection by security appliances or proxies.
- **Exfiltration**. Tactics used to move data from the compromised network to a system or network that's fully under control of the attacker.
- **Impact**. Tactics that an attacker uses to affect the availability of systems, networks, and data. Methods in this category include denial-of-service attacks and disk-wiping or data-wiping software.
- **Impair Process Control**. Tactics the adversary uses to manipulate, disable, or damage physical control processes.
- **Inhibit Response Function**. Tactics the adversary uses to prevent your safety, protection, quality assurance, and operator intervention functions from responding to a failure, hazard, or unsafe state.
- **None**.

## Create custom queries to refine threat hunting

All Microsoft Sentinel hunting queries use Kusto Query Language (KQL) syntax used in Log Analytics. You can modify a query in the details pane and run the new query. Or you can save it as a new query that can be reused in your Microsoft Sentinel workspace.

You can also create your own custom queries by using KQL code to hunt for threats.

![Screenshot that shows the page for creating a custom query in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/hunt-threats-sentinel/media/3-create-custom-query-page.png)

Custom queries allow you to define the following:

|Query parameter|Description|
|---|---|
|Name|Provide a name for the custom query.|
|Description|Provide a description of your query's functionality.|
|Custom query|Your KQL hunting query.|
|Entity mapping|Map entity types to columns from your query result to populate your query results with more actionable information. You can also map entities by using code in your KQL query.|
|Tactics & techniques|Specify the tactics that your query is designed to expose.|

Custom queries are listed alongside built-in queries for management.

## Explore Microsoft Sentinel on GitHub

The [Microsoft Sentinel repository](https://github.com/Azure/Azure-Sentinel) contains out-of-the-box detections, exploration queries, hunting queries, workbooks, playbooks, and more to help you secure your environment and hunt for threats. Microsoft and the Microsoft Sentinel community contribute to this repo.

The repo contains folders with contributed content for several areas of Microsoft Sentinel functionality, including hunting queries. You can use the code from these queries to create custom queries in your Microsoft Sentinel workspace.

![[Pasted image 20261007110243.png]]

# Save key findings with bookmarks
To hunt for threats to Contoso's environment, you have to review large amounts of log data for evidence of malicious behavior. During this process, you might find events that you want to remember, revisit, and analyze as part of validating potential hypotheses and understanding the full story of a compromise.

## Hunt by using bookmarks

Bookmarks in Microsoft Sentinel can help you hunt for threats by preserving the queries you already ran, along with the query results that you deem relevant. You can also record your contextual observations and reference your findings by adding notes and tags. Bookmarked data is visible to you and your teammates for easy collaboration.

You can revisit your bookmarked data at any time on the **Bookmarks** tab of the **Hunting** page. You can use filtering and search options to quickly find specific data for your current investigation. Alternatively, you can review your bookmarked data directly in the **HuntingBookmark** table in your Log Analytics workspace.

Note

Bookmarked events contain standard event information but can be used in different ways throughout the Microsoft Sentinel interface.

## Create or add to incidents by using bookmarks

You can use bookmarks to create a new incident or add bookmarked query results to existing incidents. The **Incident actions** button on the _Hunt_ toolbar enables you to perform either of these tasks when a bookmark is selected.

![Screenshot of the drop-down menu for incident actions in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/hunt-threats-sentinel/media/4-incident-actions.png)

Incidents that you create from bookmarks can be managed from the **Incidents** page alongside other incidents created in Microsoft Sentinel.

## Use the investigation graph to explore bookmarks

You can investigate bookmarks in the same way that you'd investigate incidents in Microsoft Sentinel. From the **Hunting** page, select your _Hunt_ with a _Bookmark_ from the **Hunts (Preview)** tab. In the _Hunt_ details pane select **Bookmarks** (or select any _Related incidents_), select a specific _Bookmark_ and then select the **Investigate** button to open the investigation graph for the incident. The investigation graph is a visual tool that helps to identify entities involved in the attack and the relationships between those entities. If the incident involves multiple alerts over time, you can also review the alert timeline and correlations between alerts.

![Screenshot of the investigation graph page for a deleted virtual machine incident.](https://learn.microsoft.com/en-us/training/wwl-sci/hunt-threats-sentinel/media/4-investigation-graph.png)

### Review entity details

You can select each entity on the graph to observe complete contextual information about it. This information includes relationships to other entities, account usage, and data flow information. For each information area, you can go to the related events in Log Analytics and add the related alert data into the graph.

### Review bookmark details

You can select the bookmark item on the graph to observe important bookmark metadata related to the bookmark's security and environment context.

![[Pasted image 20261007110631.png]]

# Track threat-hunting investigations with hunts
Microsoft Sentinel hunts help you organize proactive investigations around a hypothesis. A hunt can contain multiple queries, bookmarks, entities, comments, related analytics rules, and incidents. This structure preserves investigation context and lets security analysts collaborate over time.

Note

Microsoft Sentinel livestreams are no longer available. To automate queries and notifications, use Kusto Query Language (KQL) jobs, analytics rules, or playbooks.

## Create a hunt

You can create a hunt from selected queries or start with a blank hunt:

1. In Microsoft Sentinel, select **Threat management** > **Hunting**.
2. To start from existing queries, select the queries on the **Queries** tab, and then select **Hunt actions** > **Create new hunt**. To start without queries, select the **Hunts** tab, and then select **New hunt**.
3. Enter a name and description that state the hypothesis that you want to investigate.
4. Select **Create**.

## Investigate with queries and bookmarks

Run the queries associated with the hunt and review their results. For example, the following query returns Azure Activity events that recorded a deleted resource:

Kusto

```
AzureActivity
| where OperationName has 'delete'
| where ActivityStatus == 'Accepted'
| extend AccountCustomEntity = Caller
| extend IPCustomEntity = CallerIpAddress
```

When you find important results, add them as bookmarks. Bookmarks preserve the result, query, and time range. You can also map entities, add tags and notes, investigate related entities, and use bookmarks to create or enrich an incident.

## Act on hunt results

If a hunt query produces reliable findings, create an analytics rule from the query. The rule can generate alerts or incidents when future activity matches the detection logic. You can also create incidents from hunt bookmarks and run playbooks on bookmarked entities.

As the investigation progresses, update the hunt's hypothesis and status. Close the hunt after you record the outcome and complete related actions.

Choose the best response for the following question.

![[Pasted image 20261007111132.png]]

# Exercise - Hunt for threats by using Microsoft Sentinel

As a security engineer working for Contoso, you recently noticed that a significant number of virtual machines (VMs) were deleted from your Azure subscription. You want to simulate a deleted VM, analyze this occurrence, and understand the key elements of the potential threat in Microsoft Sentinel.

In this exercise, you delete a VM, manage threat-hunting queries, and save key findings with bookmarks.

Note

To complete this exercise, you need to have completed the setup exercise earlier in the module. If you haven't done that, please do it now.

## Delete a VM

In this task, you delete a VM to test rule detection and incident creation.

1. In the Azure portal, search for and select **Virtual machines**.
2. On the **Virtual machines** page, select the check box beside the virtual machine labeled **simple-vm**, and then select **Delete** from the toolbar.
3. In the **Delete Resources** pane, confirm the deletion and then select **Delete**.

## Manage Microsoft Sentinel threat-hunting queries

In this task, you create and manage threat-hunting queries to review events related to deleting the VM in the previous task. It might take up to 5 minutes for the event to appear in Microsoft Sentinel after you delete the VM.

1. In the Azure portal, search for and select **Microsoft Sentinel**, and then select the previously created Sentinel workspace.
    
2. On the **Microsoft Sentinel** page, on the menu bar, in the **Threat management** section, select **Hunting**.
    
3. On the **Hunting** page, select the **Queries** tab. Then choose **New Query**.
    
4. On the **Create custom query** page, provide the following inputs, and then select **Create**.
    
    - **Name**: Enter **Deleted VMs**.
        
    - **Description**: Enter a detailed description that helps other security analysts understand what the rule does.
        
    - **Custom query**: Enter the following code.
        
        Kusto
        
        ```
          AzureActivity
          | where OperationName == 'Delete Virtual Machine'
          | where ActivityStatus == 'Accepted'
          | extend AccountCustomEntity = Caller
          | extend IPCustomEntity = CallerIpAddress
        ```
        
    - **Tactics**: Select **Impact**.
        
5. On the **Hunting** page, on the **Queries** tab, enter **Deleted VMs** in the **Search queries** field.
    
6. In the list of queries, select the star icon beside **Deleted VMs** to mark the query as a favorite.
    
7. Select the **Deleted VMs** query. In the details pane, select **View Results**.
    
    Note
    
    It might take up to 15 minutes for the deleted VM event to be sent to Microsoft Sentinel. You can periodically choose to run the query on the **Results** tab if the VM deletion event doesn't appear.
    
8. On the **Logs** page, in the **Results** section, select the listed event. It should have `"action": "Microsoft.Compute/virtualMachines/delete"` in the **Authorization** column. This is the event from the Azure Activity log that indicates that the VM was deleted.
    
9. Remain on this page for the next task.
    

## Save key findings with bookmarks

In this task, you use bookmarks to save events and do more hunting.

1. On the **Logs** page, in the **Results** section, select the check box beside the listed event. Then select **Add bookmark**.
2. On the **Add bookmark** pane, select **Create**.
3. At the top of the page, select **Microsoft Sentinel** on the breadcrumb trail.
4. On the **Hunting** page, select the **Bookmarks** tab.
5. In the list of bookmarks, select the bookmark that begins with **Deleted VMs**.
6. On the details page, select **Investigate**.
7. On the **Investigation** page, select **Deleted VMs** and observe the details of the incident.
8. On the **Investigation** page, select the entity on the graph that represents a user. This is your user account, which indicates that you deleted the VM.

## Results

In this exercise, you deleted a VM, managed threat-hunting queries, and saved key findings with bookmarks.

## Clean up Azure resources

After you finish using the Azure resources that you created in this exercise, delete them to avoid incurring costs:

1. In the Azure portal, search for **Resource groups**.
2. Select your resource group.
3. In the header bar, select **Delete resource group**.
4. In the **TYPE THE RESOURCE GROUP NAME** field, enter the name of the resource group and select **Delete**.
# Summary


As part of the Security Operations Center team, you need to protect Contoso's environment. To accomplish this goal, you first need to detect any threats to the environment.

In this module, you learned how to hunt for threats by using the tools available in Microsoft Sentinel. That activity included proactively identifying threat behaviors by using Microsoft Sentinel queries. You also learned to continue the investigation by using hunts and bookmarks to identify specific account-usage patterns for Contoso's Azure environment.

Now, you can lead your team in using Microsoft Sentinel to help protect Contoso's environment through threat detection.


# Hunt for threats using notebooks in Microsoft Sentinel

# Introduction
You can use notebooks in Microsoft Sentinel for advanced hunting.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You want to mature your Security Operations team to proactively hunt for malicious activity in your environment with advanced machine learning capabilities.

After developing your hunting hypothesis, you utilize a Jupyter notebook to integrate machine learning libraries, advanced visualizations, and external data to detect malicious activity patterns.

After completing this module, you'll be able to:

- Explore API libraries for advanced threat hunting in Microsoft Sentinel
- Describe notebooks in Microsoft Sentinel
- Create and use notebooks in Microsoft Sentinel

## Prerequisites

- Basic knowledge of operational concepts such as monitoring, logging, and alerting
- Familiarity deploying Azure services
- Familiarity with scripting and Python coding

# Access Azure Sentinel data with external tools
Before hunting with notebooks, it's essential to understand the foundation of Microsoft Sentinel is the Log Analytics data store, which combines high-performance querying, dynamic schema, and scales to massive data volumes. The Azure portal and all Microsoft Sentinel tools use a standard API to access this data store. The same API is also available for external tools such as Python and PowerShell. There are two libraries that you can use to simplify API access:

- Kqlmagic
    
- msticpy
    

### Kqlmagic

The Kqlmagic library provides an easy to implement API wrapper to run KQL queries.

### msticpy

Microsoft Threat Intelligence Python Security Tools is a set of Python tools intended to be used for security investigations and hunting. Many of the tools originated as code Jupyter notebooks written to solve a problem as part of a security investigation. Some of the tools are only useful in notebooks (for example, much of the nbtools subpackage), but many others can be used from the Python command line or imported into your code.

The package addresses three central needs for security investigators and hunters:

- Acquiring and enriching data
    
- Analyzing data
    
- Visualizing data
    

msticpy can query using KQL; the library also provides predefined queries for Microsoft Sentinel, Microsoft Defender XDR for Endpoint, and the Microsoft Security Graph. An example of a function is the list_logons_by_account, which retrieves the logon events for an account. For details about msticpy visit: [https://msticpy.readthedocs.io/](https://msticpy.readthedocs.io/)

# Hunt with notebooks


A Jupyter Notebook allows you to create and share documents that contain live code, equations, visualizations, and explanatory text. Uses include data cleaning and transformation, numerical simulation, statistical modeling, machine learning, and much more. Jupyter extends the scope of what you can do with Microsoft Sentinel data. It combines full programmability with a vast library collection for machine learning, visualization, and data analysis. These attributes make Jupyter a useful tool for security investigation and hunting.

![Sample Notebook output](https://learn.microsoft.com/en-us/training/wwl-sci/perform-threat-hunting-sentinel-with-notebooks/media/sentinel-notebooks-map.png)

Several notebooks, developed by some of Microsoft's security analysts, are packaged with Microsoft Sentinel. Some of these notebooks are built for a specific scenario and can be used as-is. Others are samples intended to illustrate techniques and features that you can copy or adapt for use in your own notebooks. Other notebooks may also be imported from the Microsoft Sentinel Community GitHub.

Notebooks have two components:

- The browser-based interface where you enter and run queries and code and where the execution results are displayed.
    
- The kernel is responsible for parsing and executing the code itself.
    

The Microsoft Sentinel notebook's kernel runs on an Azure virtual machine (VM). Several licensing options exist to use more powerful virtual machines if your notebooks include complex machine learning models.

The Microsoft Sentinel notebooks use many popular Python libraries such as pandas, matplotlib, bokeh, etc. There are a great many other Python packages for you to choose from, covering areas such as:

- Visualizations and graphics
    
- Data processing and analysis
    
- Statistics and numerical computing
    
- Machine learning and deep learning
    

The msticpy package is used in many of the included notebooks. Msticpy tools are explicitly designed to help with creating notebooks for hunting and investigation.

# Create a notebook

To get started with Notebooks, use the _Getting Started Guide For Microsoft Sentinel ML Notebooks_ notebook.

1. In the Microsoft Sentinel navigation menu, expand the _Threat Management_ section, and select **Notebooks**
    
2. You need to create an Azure Machine Learning (ML) Workspace. From the menu, select **Configure Azure Machine Learning**, then **Create new Azure ML workspace**.
    
3. In the Subscription box, select your subscription.
    
4. Select **Create a new Resource group** and choose a name for your new resource group.
    
5. In the Workspace details section:
    
    - Give your workspace a unique name.
        
    - Choose your Region
        
    - Keep the default Storage account, Key vault, and Application insights information.
        
    - The Container registry option can remain as None.
        
6. At the bottom of the page, select **Review + create**. Then on the next page, select **create**. It takes a moment to deploy the workspace.
    
    Note
    
    It takes a few minutes to deploy the Machine Learning workspace.
    
7. After _Your deployment is complete_ message appears, return to Microsoft Sentinel.
    
8. Navigate to the Threat Management section, and select **Notebooks**.
    
9. Select the **Templates** tab.
    
10. Select the **A Getting Started Guide For Microsoft Sentinel ML Notebooks** from the list.
    
11. Select **Create from template** button on the bottom of the detail pane.
    
12. Review the default options and then select **Save**.
    
13. Select the **Launch notebook** button.
    
14. Select **Close** if an informational window appears in the Microsoft Azure Machine Learning studio.
    
15. 1. In the command bar, to the right of the **Compute:** selector, select the **+** symbol to _Create Azure ML compute_ instance. **Hint:** It might be hidden inside the ellipsis icon **(...)**.
    
    Note
    
    You can have more screen space by hiding the Azure ML Studio left menu selections. Select the _Hamburger menu_ (3 horizontal lines on the top left), and by collapsing the Notebooks Files by selecting the **<<** icon.
    
16. Type a unique name in the _Compute name_ field. This identifies your compute instance.
    
17. Scroll down and select the first option available.
    
    Tip
    
    Workload type: Development on Notebooks (or other IDE) and lightweight testing.
    
18. Select the **Review + Create** button at the bottom of the screen, then scroll down and select **Create**. Close any feedback window that appears. This takes a few minutes. You see a notification (bell icon) when it completes and the _Compute instance_ left icon turns from blue to green.
    
19. Once the Compute is created and running, verify that the kernel to use is _Python 3.10 - Pytorch and Tensorflow_.
    
    Tip
    
    This is shown in the right of the menu bar. If that kernel isn't selected, select the _Python 3.10 - Pytorch and Tensorflow_ option from the drop-down list. You can select the **Refresh** icon on the far right to see the kernel options.
    
20. Select the **Authenticate** button and wait for the authentication to complete.
    
21. Clear all the results from the notebook by selecting the **Clear all outputs** (Eraser icon) from the menu bar and follow the _Getting Started_ tutorial.
    
    Tip
    
    This can be found by selecting the ellipsis (...) from the menu bar.
    
22. Review section _1 Introduction_ in the notebook and proceed to section _2 Initializing the notebook and MSTICPy_.
    
    Tip
    
    Section 1.2 _Running code in notebooks_ lets you practice running small lines of Python code.
    
23. In section _2 Initializing the notebook and MSTICPy_, review the content on Initializing the notebook and installing the MSTICPy package.
    
24. Run the _Python code_ to initialize the cell by selecting the **Run cell** button (Play icon) to the left of the code.
    
25. It should take >30 seconds to run. Once it completes, review the output messages and _disregard any warnings about the Python kernel version_ or other error messages.
    
26. The code ran successfully if _msticpyconfig.yaml_ was created in the _utils_ folder in the _file explorer_ pane on the left. It can take another 30 seconds for the file to appear. If it doesn't appear, select the **Refresh** icon in the _file explorer_ pane.
    
    Tip
    
    You can clear the output messages by selecting the ellipsis (...) on the left of the code window for the _Output menu_ and selecting the _Clear output_ (square with an x*) icon.
    
27. Select the **msticpyconfig.yaml** file in the _file explorer_ pane on the left to review the contents of the file and then close it.
    
28. Proceed to section _3 Querying data with MSTICPy_ and review the contents. Don't run the _Multiple Microsoft Sentinel workspaces_ code cell as it fails, but the other code cells can be run successfully.
    

Note

If you can't complete the steps above to access the Notebook, you can follow it on its GitHub viewer page instead. [Getting Started with Azure ML Notebooks and Microsoft Sentinel](https://nbviewer.org/github/Azure/Azure-Sentinel-Notebooks/blob/master/A%20Getting%20Started%20Guide%20For%20Azure%20Sentinel%20ML%20Notebooks.ipynb)

# Explore notebook code
The following code blocks provide a representative example of using notebooks to work with Microsoft Sentinel data.

**Code Block**

In this snippet of code:

- Create a new variable [test_query] that contains the KQL query.
    
- Next, you run the query [qry_prov.exec_query()]. This utilizes the msticpy library to execute the KQL query in the Microsoft Sentinel Log Analytics related workspace. The results are stored in the [test_df] variable.
    
- Next, display the first five rows with the xxx_xxxx.head() function.
    

![Screenshot of a Microsoft Sentinel Notebook Sample 1 Query.](https://learn.microsoft.com/en-us/training/wwl-sci/perform-threat-hunting-sentinel-with-notebooks/media/threat-hunt-1.png)

**Code Block**

In this snippet of code:

- You create a new function called lookup_res that takes a variable row.
    
- Next, you save the IP address stored in row to the variable [ip].
    
- The next line of code uses the msticpy function [ti.lookup_ioc()] to query the ThreatIntelligenceIndicator table for a row that is sourced from VirusTotal with a matching ip-address.
    
- Next, the msticpy function [ti.result_to_df()] will return a DataFrame representation of response.
    
- The new function returns the Severity of the IP address.
    

![Screenshot of a Microsoft Sentinel Notebook Sample 2 Query.](https://learn.microsoft.com/en-us/training/wwl-sci/perform-threat-hunting-sentinel-with-notebooks/media/threat-hunt-3.png)

**Code Block**

In this snippet of code:

- Create a new variable [vis_q] that contains the KQL query.
    
- Next, you run the query [qry_prov.exec_query()]. This utilizes the msticpy library to execute the KQL query in the Microsoft Sentinel Log Analytics related workspace. The results are stored in the [vis_data] variable.
    
- Then, [qry_prov.exec_query()] returns a pandas DataFrame that provides visualization features. You then plot a bar graph with the unique IP addresses and how many times they were used in the first five entries of the Dataframe.
    

![Screenshot of a Microsoft Sentinel Notebook Sample 3 Query.](https://learn.microsoft.com/en-us/training/wwl-sci/perform-threat-hunting-sentinel-with-notebooks/media/threat-hunt-2.png)

![[Pasted image 20261007120835.png]]
# Summary and resources

You should have learned how to perform advanced hunting in Microsoft Sentinel.

You should now be able to:

- Explore API libraries for advanced threat hunting in Microsoft Sentinel
- Describe notebooks in Microsoft Sentinel
- Create and use notebooks in Microsoft Sentinel
