# Introduction
Microsoft Sentinel Analytics provides an intelligent solution that you can use to detect potential threats and vulnerabilities in your organizations.

Imagine that you work as Security Operations Center (SOC) analyst in Contoso, Ltd. Contoso is a midsize financial services company in London with a New York branch office. Contoso uses several Microsoft products and services to implement data security and threat protection for its resources. These products are:

- Microsoft 365
- Microsoft Entra ID
- Microsoft Entra ID Protection
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity
- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- System Center Endpoint Protection
- Microsoft Azure Information Protection

Contoso provides threat protection for its Azure-based and on-premises resources by using the paid version of Microsoft Defender for Cloud. The company also monitors and protects other non-Microsoft assets. Security analysts at Contoso face a huge triage burden. They deal with a high volume of alerts from multiple products. They correlate alerts in the following ways:

- Manually from different project dashboards
- By using a traditional correlation engine

Additionally, the time spent to set up and maintain IT infrastructure takes the SOC team away from its security tasks.

The IT director believes that Microsoft Sentinel Analytics will help the security analysts perform complex investigations faster and improve their Security Operations Center (SOC). As Contoso's lead system engineer and Azure administrator, you've been asked to set up analytics rules in Microsoft Sentinel so that the SecOps team can identify and analyze attacks to Contoso's resources.

In this module, you'll understand the importance of using Microsoft Sentinel Analytics, create, and implement analytics rules from existing templates, create new rules and queries using the wizard, and manage rules with modifications.

By the end of this module, you'll be able to set up analytics rules in Microsoft Sentinel to help the SecOps team identify and stop cyberattacks.

## Learning objectives

- Explain the importance of Microsoft Sentinel Analytics.
- Explain different types of analytics rules.
- Create rules from templates.
- Create new analytics rules and queries using the analytics rule wizard.
- Manage rules with modifications.

## Prerequisites

- Basic knowledge of Azure services
- Basic knowledge of operational concepts, such as monitoring, logging, and alerting
- Azure subscription
- Microsoft Sentinel instance in your Azure subscription

Note

If you choose to perform the exercise in this module, be aware you might incur costs in your Azure Subscription. To estimate the cost refer to [Microsoft Sentinel Pricing](https://azure.microsoft.com/pricing/details/azure-sentinel/)

# Exercise - Detect threats with Microsoft Sentinel analytics
The Threat detection with Microsoft Sentinel Analytics exercise in this module is an optional unit. However, if you want to perform this exercise, you need access to an Azure subscription where you can create Azure resources. If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn_9d2f8b5f-9f70-5b54-250a-082f7015d22f) before you begin.

To deploy the prerequisites for the exercise, perform the following tasks.

Note

If you choose to perform the exercise in this module, be aware you might incur costs in your Azure Subscription. To estimate the cost, refer to [Microsoft Sentinel Pricing](https://azure.microsoft.com/pricing/details/azure-sentinel/).

## Task 1: Deploy Microsoft Sentinel using ARM template

1. Select the following link:
    
    [![Deploy To Azure.](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftDocs%2Fmslearn-security-ops-sentinel%2Fmain%2Fmslearn-analyze-data-in-sentinel%2Fsentinel-template.json?azure-portal=true)
    
    You're prompted to sign in to Azure. The **Custom deployment** pane appears.
    
2. On the **Basics** tab, enter the following values for each setting.
    
    |Setting|Value|
    |---|---|
    |**Project details**||
    |Subscription|Select your Azure subscription.|
    |Resource group|Select **Create new**, and provide a name for the resource group, such as `azure-sentinel-rg`.|
    |**Instance details**||
    |Region|From the dropdown list, select the location where you want to deploy the Microsoft Sentinel.|
    |Workspace Name|Provide a unique name for the Microsoft Sentinel Workspace such as `<yourName>-sentinel`, where _<yourName>_ represents the workspace name that you chose in the previous task.|
    |Location|Accept the default value of **[resourceGroup().location]**.|
    |Simplevm Name|Accept the default value of **simple-vm**.|
    |Simplevm Windows OS Version|Accept the default value of **2022-Datacenter**.|
    
3. Select the **Review + create**. When validation passes, select **Create**.
    
    ![Screenshot of the Custom Deployment page.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/02-custom-deployment.png)
    
    Note
    
    Wait for the deployment to complete. The deployment should take less than five minutes.
    

## Task 2: Check the resources created

1. In the Azure portal, search for **Resource groups**.
    
2. Select **azure-sentinel-rg**.
    
3. Sort the list of resources by **Type**.
    
    The resource group should contain the resources listed in the following table.
    
    |Name|Type|Description|
    |---|---|---|
    |`<yourName>-sentinel`|Log Analytics workspace|Log Analytics workspace used by Microsoft Sentinel, where _<yourName>_ represents the workspace name that you chose in the previous task.|
    |`simple-vmNetworkInterface`|Network interface|Network interface for the VM.|
    |`SecurityInsights(<yourName>-sentinel)`|Solution|Security insights for Microsoft Sentinel.|
    |`simple-vm`|Virtual machine|Virtual machine (VM) used in the demonstration.|
    |`st1<xxxxx>`|Storage account|Storage account used by the VM, where _<xxxxx>_ represents a random string generated to create a unique storage account name.|
    |`vnet1`|Virtual network|Virtual network for the VM.|
    

Note

The resources deployed and configuration steps completed in this exercise are required in the next exercise. If you intended to complete the next exercise, don't delete the resources from this exercise.

## Task 3: Configure Microsoft Sentinel Data connectors

In this task, you deploy a Microsoft Sentinel Data connector to detect Azure Activity.

1. In the Azure portal, select **Home**, and then search for and select **Microsoft Sentinel**.
    
2. In the list of Sentinel workspace names, select the Microsoft Sentinel workspace you created in Task 2. The **Overview** pane for your Sentinel workspace appears.
    
3. In the menu pane, under **Content management**, select **Content hub**. The **Content hub** pane appears.
    
4. In the _Search_ box, search for and select the **Azure Activity** Solution. On the **Azure Activity** details pane, select **Install**.
    
5. Wait for the install to complete and then select **Manage**.
    
6. In the _Search_ box, search for and select the **Azure Activity** Data connector.
    
7. On the **Azure Activity** details pane, select **Open connector page**.
    
8. In the _Instructions_ tab, _Configuration_ area, scroll down and under "2. Connect your subscriptions..." select **Launch Azure Policy Assignment Wizard>**.
    
9. In the **Basics** tab, select the ellipsis button (...) under **Scope** and select your "Azure subscription" from the drop-down list and select **Select**.
    
10. Select the **Parameters** tab, choose your _yourName-sentinel_ workspace from the **Primary Log Analytics workspace** drop-down list.
    
11. Select the **Remediation** tab and select the **Create a remediation task** checkbox. This action applies the subscription configuration to send the information to the Log Analytics workspace.
    
    Note
    
    To apply the policy to your existing resources, you need to create a remediation task.
    
12. Select the **Review + Create** button to review the configuration.
    
13. Select **Create** to finish.
    
14. Once the deployment is complete, you see the **Connected** status (green bar) for the Azure Activity connector in the _Configuration/Data connectors_ pane.
    

[![Screenshot of the Microsoft Sentinel connector](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/07-azure-sentinel-connector.png)](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/07-azure-sentinel-connector.png#lightbox)

Note

The connector for Azure Activity could take 15 minutes to show **Connected** in Microsoft Sentinel. You can proceed with rest of the steps and with other units of this module.


# What is Microsoft Sentinel Analytics?

Microsoft Sentinel Analytics helps you detect, investigate, and remediate cybersecurity threats. The Contoso SOC team can use Microsoft Sentinel Analytics to set up analytics rules and queries to detect issues in your environment.

## What is Microsoft Sentinel Analytics?

Microsoft Sentinel Analytics provides several functionalities that you can use to implement security for the data and resources at Contoso.

You can analyze historical data collected from your workstations, servers, networking devices, firewalls, intrusion prevention, sensors, and so on. Microsoft Sentinel Analytics analyzes data from various sources to identify correlations and anomalies.

By using analytics rules, you can trigger alerts based on the attack techniques that are used by known malicious actors. You can set up these rules to help ensure your SOC is alerted to potential security incidents in your environment in a timely fashion.

## Why use analytics rules for security operations?

Although some of the other products that Contoso implemented can help you identify threats, Microsoft Sentinel Analytics plays an important part in the overall detection of the security threat by correlating and matching the signals that impact the presence of a cybersecurity threat. With the proper analytics rule, you can get insights into where an attack originated from, what resources were compromised, potential data lost, along with the timeline for the incident.

Common security analytics use cases include:

- Identification of compromised accounts
    
- User behavior analysis to detect potentially suspicious patterns
    
- Network traffic analysis to locate trends indicating potential attacks
    
- Detection of data exfiltration by attackers
    
- Detection of insider threats
    
- Investigation of incidents
    
- Threat hunting
    

You might not be able to detect some of the threats by using conventional protection tools, such as firewalls or anti-malware solutions. Certain threats can go undetected for months. Combining data, gathered by multiple tools and products, with the power of threat intelligence can help you to detect, analyze, and mitigate insider threats.

You can also use analytics rules to create custom alerts that use indicators of attack. These indicators can identify potential attacks that are in progress in real time.

Analytics helps the Contoso SOC team to improve the efficiency of their complex investigation and detect threats faster.

## Exploring the Analytics home page

You can create analytics rules from the **Analytics** home page. You can access the **Analytics** page in Microsoft Sentinel from the navigation pane.

![Screenshot of the Analytics rules and rule details page.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/03-analytics-screen-select-rule.png)

The **Analytics** home page has three main parts:

- The header bar contains information on the number of the rules that are currently in use.
    
- The list of rules and templates contains all the rule templates that Microsoft has preloaded from the Microsoft Sentinel GitHub repository.
    
- The details pane contains additional information that explains each template and rule that you can use in detection.
    

## Filter the rule templates

Currently Microsoft has preloaded over 150 template rules from the Microsoft Sentinel GitHub repository. To search these templates and to access the appropriate rule, you need to apply filters. For example, you might want to review only template rules that detect threats with a high severity level or rules from specific data sources.

To use filters, in the header bar, select the filters you want to use.

![Screenshot of filtering the Analytics home page.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/02-filter-the-rule-templates.png)

The **Analytics** home page provides the following filters:

- **Severity**. Use to filter the rules by levels of severity.
    
- **Rule Type**. There are currently seven types of rules: Scheduled, NRT (near real time), Fusion, Microsoft Security, ML (machine learning) Behavior Analytics, and Threat Intelligence.
    
- **Tactics**. Use to filter the rules based on 14 specific methodologies in ATT&CK model.
    
- **Data Sources**. Use to filter the rules by the data source connector that generates the alert.
    

Note

MITRE ATT&CK is a globally accessible knowledge base of adversary tactics and techniques based on real-world observations. The ATT&CK knowledge base is used as a foundation for the development of specific threat models and methodologies in the private sector, in government, and in the cybersecurity product and service community.

![[Pasted image 20261008130626.png]]

# Types of analytics rules
By using Microsoft Sentinel Analytics rules, you can configure notification and alerts based on data coming from the sources that are connected to Microsoft Sentinel. These alerts help ensure that the Contoso SOC team knows when a threat occurs, and the team can then appropriately react to prevent the threat from reaching your corporate assets.

## Types of analytics rules

You can search for potential threats by using the built-in analytics rules that Microsoft Sentinel Analytics provides, including the following types:

- Anomaly
    
- Fusion
    
- Microsoft security
    
- Machine learning (ML) behavior analytics
    
- Scheduled alerts
    
- NRT (Near Real Time) rules
    
- Threat Intelligence
    

![Screenshot of rule templates in the Analytics home page.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/03-rule-templates.png)

## Anomaly

Anomaly alerts are informational and identify anomalous behaviors.

## Fusion

Microsoft Sentinel uses the Fusion correlation engine, with its scalable machine learning algorithms, to detect advanced multistage attacks. The engine correlates many low-fidelity alerts and events across multiple products into high-fidelity and actionable incidents. Fusion is enabled by default. Because the logic is hidden and therefore not customizable, you can only create one rule with this template.

The Fusion engine can also correlate alerts from scheduled analytics rules with alerts from other systems, producing high-fidelity incidents as a result.

By default, Fusion detection is enabled in Microsoft Sentinel. Microsoft is constantly updating Fusion detection scenarios for threat detection. At the time of writing this article, for Anomaly and Fusion detection, you must configure the following data connectors:

- Out-of-the-box anomaly detections
    
- Alerts from Microsoft Products
    
    - Microsoft Entra ID Protection
        
    - Microsoft Defender for Cloud
        
    - Microsoft Defender for IoT
        
    - Microsoft Defender XDR
        
    - Microsoft Defender for Cloud Apps
        
    - Microsoft Defender for Endpoint
        
    - Microsoft Defender for Identity
        
    - Microsoft Defender for Office 365
        
- Alerts from scheduled analytics rules, both built-in and created by your security analysts. Analytics rules must contain kill-chain (tactics) and entity mapping information in order to be used by Fusion
    

Some of the common attack detection scenarios that Fusion alerts identify include:

- **Data exfiltration**. Suspicious activity detected, such as suspicious forwarding rule in Microsoft 365 mailbox, after a suspicious sign-in to Microsoft Entra account can indicate compromised user account.
    
- **Data destruction**. Anomalous number of unique files that were deleted after a suspicious sign-in to Microsoft Entra account can signal that a compromised user account was used to destroy data.
    
- **Denial of service**. Significant number of Azure virtual machines (VMs) deleted after a suspicious sign-in to Microsoft Entra account can signal a compromised user account that can be used to destroy the organization's assets.
    
- **Lateral movement**. Significant number of impersonation actions that occur after a suspicious sign-in to Microsoft Entra account can indicate a compromised user account that was used for malicious purposes.
    
- **Ransomware**. After a suspicious sign-in to a Microsoft Entra account, unusual user behavior used to encrypt data can trigger a ransomware execution alert.
    

Note

For more information on the Fusion technology in Microsoft Sentinel, see [Advanced multistage attack detection in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/fusion)

## Microsoft security

You can configure Microsoft security solutions that are connected to Microsoft Sentinel to automatically create incidents from all alerts generated in the connected service.

For example, you can configure for Contoso to be alerted when a user who is categorized as a high-risk threat attempts to sign in and access corporate resources.

You can configure the following security solutions to pass their alerts to Microsoft Sentinel:

- Microsoft Defender for Cloud Apps
    
- Microsoft Defender for Server
    
- Microsoft Defender for IoT
    
- Microsoft Defender for Identity
    
- Microsoft Defender for Office 365
    
- Microsoft Entra ID Protection
    
- Microsoft Defender for Endpoint
    

Note

Microsoft unifies security information and event management (SIEM) and extended detection and response (XDR) terminology across their security products.

You can filter these alerts by severity and by specific text that is contained in the alert name.

## ML behavior analytics

Microsoft Sentinel Analytics includes built-in machine learning behavior analytics rules. You can't edit these built-in rules or review the rule settings. These rules use Microsoft machine learning algorithms to detect suspicious activity. Machine Learning algorithms correlate several low-fidelity incidents into a high-fidelity security incident. This correlation saves hours that you might otherwise spend manually analyzing numerous alerts from different products and correlating them. Machine learning algorithms that analytics rules use also help reduce the noise around alerts by quickly ingesting and connecting important data.

For example, by using a machine learning behavior analytics rule, you can detect an anomalous secure shell protocol (SSH) sign-in or remote desktop protocol (RDP) sign-in activity.

## Scheduled alerts

Scheduled alerts analytics rules provide you with the highest level of customization. You can define your own expression using Kusto Query Language (KQL) to filter the security events, and you can set up a schedule for the rule to run.

![[Pasted image 20261008131442.png]]

# Create an analytics rule from templates
The Analytics section in Microsoft Sentinel contains rule templates that are preloaded from the Microsoft Sentinel GitHub repository. You can use these templates to create a rule to detect security threats.

## Exploring the existing rule templates

You can use some of the existing rule templates to create a single rule and others to create multiple rules with different customization options. Templates in use display the **IN USE** label on the template page as displayed in the following screenshot.

![Screenshot of the template in use.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/04-template-in-use.png)

By selecting one of the rules on the **Rule Templates** tab, you can observe the properties of the rule. For each rule, you can review:

**Severity level.** This indicates the importance of the alert. There are four severity levels:

- High
- Medium
- Low
- Informational

**Name of the rule.** This provides a meaningful name for the alert rule.

**Rule type.** This defines the type of the rule, which can be one of the following types:

- Anomaly
- Fusion
- Microsoft Security
- ML Behavior Analytics
- Scheduled
- NRT (Near Real Time)

**Data Source.** This specifies the data source connector that generated the alert.

**Tactics.** This specifies methodologies in MITRE ATT&CK model used by different kinds of malware.

Note

MITRE ATT&CK is a globally accessible knowledge base of adversary tactics and techniques based on real-world observations. The ATT&CK knowledge base provides a foundation for the development of specific threat models and methodologies in the private sector, in government, and in the cybersecurity product and service community.

When you select a rule from the list on either the Active rules tab or the Rule templates tab, the details pane provides more information for the selected rule.

## Creating an analytic rule from a rule template

When you select a predefined rule template, the details pane may display filters that can be used to define how that rule behaves. For Fusion and ML behavior analytics rules, Microsoft doesn't provide any editable information. However, for scheduled rules and Microsoft Security, you can view or edit the query, filters, and includes and excludes used in the threat detection. By selecting the **Create rule** button, you can define the analytics rule logic using a wizard that helps you customize a rule from the selected template.

For Fusion and ML behavior analytics templates, you can only enable or disable them as active rules.

A rule that you create from a Microsoft security template consists of the following elements:

## General tab

The following table lists the inputs on the **General** tab.

|Field|Description|
|---|---|
|Name|This is prepopulated from the name of the rule template.|
|Description|Provide more details about the creation of the alerts.|
|Status|This indicates whether the analytics rule is enabled or disabled.|
|Microsoft security service|This indicates the source of the alert from one of the Microsoft security services.|
|Filter by severity|Use to tune alerts from a source based on the severity level; if you select custom, you can specify High, Medium, Low, or Informational.|
|Include specific alerts|Add one or more words to include results of alerts that contain specific text in their name.|
|Exclude specific alerts|Add one or more words to exclude results of alerts that contain specific text in their name.|

## Automated response

On the **Automated response** tab, you can define automation rules. If you select **Add new**, the **Create new automation rule** pane opens. The following fields are inputs:

|Field|Description|
|---|---|
|Automation rule name|Choose a name that uniquely describes this automation rule|
|Trigger|Predefined value that can't be changed.|
|Conditions|Typical query filter construct that can be edited and sorted.|
|Actions|Selection list of actions; select which action you want to be performed if the query filter conditions are met.|
|Rule expiration|Date and time for rule to be disabled. Default is indefinite.|
|Order|If multiple rules are created, select sequential numbers to reorder the incident automation rules in the left pane.|

Note

When you implement filters to include or exclude specific alerts based on a text string, these alerts will not appear in Microsoft Sentinel.

The following screenshot presents an example of creating an incident from alerts generated by the Microsoft Defender for Cloud.

![Screenshot of the wizard used to create analytics rules from templates.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/04-create-analytics-rule.png)

For instructions on how to create an analytics rule from a scheduled rule type template, see **Create an analytics rule from a scheduled rule template** in next unit (Unit 6).

Note

For certain rule templates, the **Create rule** button might be disabled, which indicates that you can't create a rule from selected template because of a missing data source.

![[Pasted image 20261008132918.png]]
![[Pasted image 20261008132950.png]]
# Create an analytics rule from wizard


You can create a custom analytics rule to search for suspicious activities and threats at Contoso.

## Create a custom scheduled analytics rule

Creating a custom rule from a scheduled query rule type provides you with the highest level of customization. You can define your own KQL code, set a schedule to run an alert, and provide an automated action by associating the rule with a Microsoft Sentinel Playbook.

To create a scheduled query rule, in the Azure portal, under **Microsoft Sentinel**, select **Analytics**. In the header bar, select **+Create**, and then select **Scheduled query rule.**

Note

You can also create a scheduled rule by selecting a scheduled rule from the Rules and Templates list in the Analytics pane and then selecting **Create rule** in the details pane.

A scheduled query rule you create consists of the following elements:

## General tab

The following table lists the input fields on the **General** pane.

|Field|Description|
|---|---|
|Name|Provide a descriptive name to explain what type of suspicious activity the alert detects.|
|Description|Enter a detailed description that helps other security analysts understand what the rule does.|
|Tactics|From the **Tactics** dropdown list, choose one among the available categories of attacks to classify the rule following the MITRE tactics.|
|Severity|Select the **Severity** dropdown list to categorize the level of importance of the alert as one of four options: High, Medium, Low, or Informational.|
|Status|Specify the status of the rule. By default, the status is **Enable.** You can select **Disable** to disable the rule if it generates a large number of false positives.|

## Set rule logic tab

On the **Set rule logic** tab, you can define the detection method by specifying KQL code that runs against the Microsoft Sentinel workspace. The KQL query filters the security data that is used to trigger and create an incident.

When you enter the KQL query string in the **Rule query** field, you can use the **Results simulation (preview)** section to review the results of the query. The **Results simulation (preview)** section helps you determine whether your query returned the expected results.

![Screenshot of wizard used to create a scheduled analytics rule.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/05-create-scheduled-rule.png)

The following sample query alerts you when an anomalous number of resources is created in Azure Activity.

Kusto

```
AzureActivity
| where OperationName == "MICROSOFT.COMPUTE/VIRTUALMACHINES/WRITE"
| where ActivityStatus == "Succeeded"
| make-series dcount(ResourceId)  default=0 on EventSubmissionTimestamp in range(ago(7d), now(), 1d) by Caller
```

Tip

For assistance with KQL query language, see the [Kusto Query Language (KQL) overview](https://learn.microsoft.com/en-us/azure/kusto/query/).

### Alert enrichment (Preview)

Alert enrichment enables you to further customize the result of your query.

#### Entity mapping

In the **Entity mapping** section, you can define up to five entities from your query results, and then use these entities to perform in-depth analysis. By selecting **Add new entity** to add these entities in the query rule. These entities can help you perform a visual investigation because they'll appear as a group on the **Incident** tab. Some of the entities contain information that represents a user, a host, or an IP address.

#### Custom details

In the **Custom details** section, you can set key value pairs, which, if they appear in the query result, displays an event parameter in the results.

#### Alert details

In the **Alert details** section, you can enter free text as parameters that can be represented in each instance of the alert; these can also contain the tactics and severity assigned to that instance of the alert.

### Query Scheduling

In the **Query Scheduling** section, you can configure how often the query should run, and how far back in history the query should search the data. It's important that you don't search for data that is older than the query's run frequency because that can create duplicate alerts.

### Alert threshold

In the **Alert threshold** section, you can specify the number of a positive result that can be returned for the rule before it generates an alert. You can use the following logical operators to define an appropriate logical expression:

- Is greater than
- Is fewer than
- Is equal to
- Isn't equal to

### Event grouping

In the **Event grouping** section, you can select one of the following two options:

- **Group all events into a single alert**. This is the default option, and it creates a single alert if the query returns more results than that the specified alert threshold.
- **Trigger an alert for each event**. This option creates unique alerts for each event returned by the query.

### Suppression

In the **Suppression** section, you can set the **Stop running the Query after the alert is generated** option to **On** or **Off**. When you select **On**, Microsoft Sentinel pauses the creation of additional incidents if the rule is triggered again for the duration you want the rule to be suppressed.

## Incident settings (Preview)

Use the **Incident settings** tab to create incidents, which are generated by grouping alerts based on triggers and time frames.

In the **Alert grouping** section, you can reduce the noise from multiple alerts by grouping them into one incident. When you enable grouping of related alerts, you can choose from the following options:

- **Grouping alerts into a single incident if all the entities match (recommended)**
- **Grouping all alerts triggered by this rule into a single incident**
- **Grouping alerts into a single incident if the selected entities match** (for example, source or target IP addresses).

You can also **Reopen closed matching incidents** if another alert is generated that belongs to a previously closed incident.

## Automated response tab

Not used in this exercise.

## Set rule logic tab - Exercise

On the **Automated Response** tab, select an existing automation rule or create a new one. Automation rules can run playbooks based on the triggers and conditions you choose.

For more information about how to create a playbook and run the automated activity on an incident creation, see the "Threat response with Microsoft Sentinel Playbooks" module.”

## Review and create tab

On the **Review and create** tab, review the settings you've configured in the wizard before creating a new rule.

![[Pasted image 20261008134222.png]]

# Manage analytics rules
## Manage analytics rules

To adjust the noise and filter the more important threats detected, you should manage the analytics rules on an ongoing basis. This helps ensure that your rules remain useful and efficient in detecting potential security threats.

You can perform the following four actions on existing active rules:

- Edit
    
- Disable
    
- Duplicate
    
- Delete
    

## Edit rules

You can modify existing rules by selecting **Edit** in the details pane. To edit a rule, you navigate the same pages that you did in creating the rule. The previous inputs that you used to create the rule are preserved. You can change any properties of the rule to further tune the result of the threat detection.

A typical modification that you might want to implement is to attach an automated response to an already detected threat. To do this, on the **Automated Response** page, you can select one of the existing playbooks that defines the automated activity that will run if the threat is detected.

For example, your analytics rule might be detecting an incident that has already been resolved, and you want to reduce further alerts if similar activity occurs. By attaching a playbook that contains automated activity, you can change the incident status or add comments when a similar incident is detected.

[![Screenshot of the editing existing analytics rule.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/06-existing-rule-automated-response.png)](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/06-existing-rule-automated-response.png#lightbox)

## Disable rules

You can disable a rule when you're performing an activity that can trigger the rule alert. Disabled rules retain their configuration, and you can enable them again at a later time.

## Duplicate rules

When you duplicate a rule, the rule contains all the configuration provided from the original rule. You can further modify the configuration based on your requirements. Don't forget to change the name of the duplicated rule because by default, the duplicate rule has the same name as the original rule with the string **Copy** appended to it.

## Delete rules

Deleting the rule prompts you for confirmation before Microsoft Sentinel Analytics removes it from the set of active rules. For example, you can delete a rule about a service or a resource that isn't in use, which eliminates the need for the rule. Deleting a rule is permanent, and there isn't an undo feature. Therefore, we recommend you first disable the rule for a period of time until you're sure you don't need it.

![[Pasted image 20261008134557.png]]

# Exercise - Detect threats with Microsoft Sentinel analytics

As a security engineer working for Contoso, you recently noticed that a significant number of VMs were deleted from your Azure subscription. You want to analyze this occurrence and be alerted when a similar activity occurs in the future. You decide to implement an analytics rule to create an incident when someone deletes an existing VM.

## Exercise: Threat detection with Microsoft Sentinel Analytics

In this exercise, you'll explore a Microsoft Sentinel analytics rule and perform the following tasks:

- Create an incident rule from an existing template.
- Invoke an incident and review the associated actions.
- Create an analytics rule from a rule template.

Note

In order to complete this exercise, you must have completed **Exercise Setup unit** in Unit 2. If you have not done so, complete it now, and then continue with the exercise steps.

### Task 1: Create an analytics rule from the analytics rule wizard

1. In the Azure portal, search for and select **Microsoft Sentinel**, and then select the previously created Microsoft Sentinel workspace.
    
2. On the **Microsoft Sentinel** menu, under **Configuration** , select **Analytics**.
    
3. On the **Microsoft Sentinel | Analytics** header bar, select **Create** and then select **Scheduled query rule**.
    
4. On the **General** tab, enter the input values in the following table, and then select **Next: Set rule logic**
    
    |Name|Azure VM Deletion.|
    |---|---|
    |Description|A simple detection to alert when someone deletes Azure Virtual Machine.|
    |MITRE ATT&CK|From the **MITRE ATT&CK** drop-down menu, select **Impact**.|
    |Severity|Select the **Severity** drop-down menu select Medium.|
    |Status|Ensure the status is **Enabled**. You can select **Disabled** to disable a rule if it generates large numbers of false positives.|
    
    ![Screenshot Analytics Rule wizard-Create new rule.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/07-analytics-rule-wizard-create-new-rule.png)
    
5. On the **Set rule logic** tab, copy, and paste the following code into the **Rule query** text box:
    
    Kusto
    
    ```
    AzureActivity
    | where OperationNameValue == "MICROSOFT.COMPUTE/VIRTUALMACHINES/DELETE"
    | where ActivityStatusValue == "Success"
    ```
    
6. In the **Results simulation** pane, select **Test with current data**, and then observe the results.
    
    [![Screenshot of Analytics Rule Set Logic tab.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/07-set-rule-logic-page.png)](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/07-set-rule-logic-page.png#lightbox)
    
7. In the **Alert enhancement** section under **Entity Mapping**, map the entities that are returned as part of the query rule and that you can use to perform in-depth analysis.
    
8. In the **Query Scheduling** section, configure how often the query should run, and how far in history to search. Select query to run on every 5 minutes, and accept the default history of 5 hours.
    
9. In the **Alert threshold** section, specify the number of positive results that can be returned for the rule before an alert gets generated. Accept the default values.
    
10. In the **Event grouping** section, accept the default **Group all events into a single alert.**
    
11. In the **Suppression** section, set **Stop running the Query after the alert is generated** to **On**.
    
12. Accept the default values of 5 hours and then select **Next: Incident setting (Preview)**.
    
13. In the **Incident setting** tab, ensure that **Enabled** is selected for creation of incidents from alerts triggered by this analytics rule.
    
14. In the **Alert grouping** section, select **Enabled** to group related alerts into incidents, and ensure that **Grouping alerts into a single incident if all the entities match (recommended)** is selected.
    
15. Ensure that **Reopen closed matching incidents** is **Disabled**, and then select **Next: Automated response**.
    
    ![Screenshot Analytics Incident Settings.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-data-in-sentinel/media/07-incident-settings.png)
    
16. In the **Automated response** pane, select a playbook to run automatically when the alert is generated. Only the playbooks that contain Logic App Microsoft Sentinel connector are displayed.
    
17. Select **Next: Review**.
    
18. In the **Review and create** page, verify that the validation was successful, and then select **Save**.
    

### Task 2: Invoke an incident and review the associated actions

1. In the Azure portal, select **Home** and in the **Search** omnibox, enter **virtual machines**, and then select **Enter**.
2. On the **Virtual machines** page, locate and select the **simple-vm** virtual machine that you created in the resource group for this exercise, and then on the header bar, select **Delete**. In the Delete virtual machine prompt, select **Yes**.
3. In the **Delete virtual machine** prompt, select **OK** to delete the virtual machine.

Note

This task creates an incident based on the analytics rule that you created in Task 1. Incident creation can take up to 15 minutes. You can proceed with rest of the steps of this unit and then observe the results at later time.

### Task 3: Create an analytics rule from an existing template

1. In the Azure portal, select **Home**, select Microsoft Sentinel, and, then select the Microsoft Sentinel workspace you created in the Unit 2 of this module.
    
2. Open **Microsoft Sentinel**, in the left menu under **Configuration**, select **Analytics**.
    
3. On the **Analytics** pane, select **Rule templates** tab.
    
4. In the search field, enter **Create incidents based on Microsoft Defender for Cloud** and then select that rule template.
    
5. In the details pane, select **Create rule**.
    
6. In the **General** pane, observe the name of the analytics rule, and verify that the **Status** of the rule is **Enabled**.
    
7. In the **Analytics rule logic** section, verify that the Microsoft security service shows **Microsoft Defender for Cloud** is selected.
    
8. In the **Filter by severity** section, select **Custom**, and then in the drop-down menu, select **High** and **Medium**.
    
9. If you want additional filters for the alerts from Microsoft Defender for Cloud, you can add text in **Include specific alerts** and **Exclude specific alerts**.
    
10. Select **Next: Automated response** and then select **Next: Review**.
    
11. On the **Review and Create** page, select **Create**.
    

### Results

After completing this exercise, you'll have created an incident rule from an existing template and created a scheduled query rule using your own query code.

After you've finished with the exercise, you should delete resources to avoid incurring costs.

### Clean up the resources

1. In the Azure portal, search for **Resource groups**.
2. Select **azure-sentinel-rg**.
3. On the header bar, select **Delete resource group**.
4. In the **TYPE THE RESOURCE GROUP NAME:** field, enter the name of the resource group **azure-sentinel-rg** and select **Delete**.

# Summary
Contoso wanted to improve the efficiency of the investigation of the security incidents performed by their SecOps team.

The SecOps team was spending significant time investigating the high volume of alerts they were receiving from the various products and services used by Contoso.

By using Microsoft Sentinel Analytics, the SecOps team was able to detect and analyze potential threats more effectively. They could create analytics rules that would trigger alerts. The SecOps team was then able to effectively react to the threats based on the triggered alerts.

Without the help of Microsoft Sentinel Analytics, earlier the SecOps team wasn't able to use its time effectively on its other operations because it was spending time in manually correlating the threats and analyzing them.

In this module, you learned how Microsoft Sentinel Analytics can help SecOps to identify and stop cyberattacks.

# Automation in Microsoft Sentinel
# Introduction

Microsoft Sentinel, in addition to being a Security Information and Event Management (SIEM) system, is also a platform for Security Orchestration, Automation, and Response (SOAR). One of its primary purposes is to automate any recurring and predictable enrichment, response, and remediation tasks that are the responsibility of your Security Operations Center and personnel (SOC/SecOps)

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel in Microsoft Azure. You're preparing to onboard Sentinel workspaces into Microsoft Defender, and you need to understand any differences with Automation rules and Playbooks. You identified an analytical rule that generates incidents that are considered Benign Positive. You would like to implement automation that would automatically close these incidents after generation.

By the end of this module, you're able to use automation rules in Microsoft Sentinel in Azure and the Defender portal to automate incident management.

After completing this module, you'll be able to:

- Explain automation options in Microsoft Sentinel
- Create automation rules in Microsoft Sentinel in Azure and the Defender portal

# Understand automation options

Automation takes a few different forms in Microsoft Sentinel. From automation rules that centrally manage the automation of incident handling and response, to playbooks that run predetermined sequences of actions to provide powerful and flexible advanced automation to your threat response tasks.

## Automation rules

Automation rules allow users to centrally manage the automation of incident handling. Automation rules also allow you to automate responses for multiple analytics rules at once. Automatically tag, assign, or close incidents without the need for playbooks, and control the order of actions that are executed. Automation rules streamline automation use in Microsoft Sentinel and enable you to simplify complex workflows for your incident orchestration processes.

## Playbooks

A playbook is a collection of response and remediation actions and logic that can be run from Microsoft Sentinel as a routine. A playbook can help automate and orchestrate your threat response. It can integrate with other systems both internal and external, and it can be set to run automatically in response to specific alerts or incidents, when triggered by an analytics rule or an automation rule, respectively. It can also be run manually on-demand, in response to alerts, from the incidents page.

Playbooks in Microsoft Sentinel are based on workflows built in Azure Logic Apps, a cloud service that helps you schedule, automate, and orchestrate tasks and workflows across systems throughout the enterprise. This means that playbooks can take advantage of the power and customizability of Logic Apps' integration and orchestration capabilities and easy-to-use design tools, and the scalability, reliability, and service level of a Tier 1 Azure service.

# Create automation rules

Automation rules are a way to centrally manage the automation of incident handling, allowing you to perform simple automation tasks without using playbooks. For example, automation rules allow you to automatically assign incidents to the proper personnel, tag incidents to classify them, and change the status of incidents and close them. Automation rules can also automate responses for multiple analytics rules at once, control the order of actions that are executed, and run playbooks for those cases where more complex automation tasks are necessary. In short, automation rules streamline the use of automation in Microsoft Sentinel, enabling you to simplify complex workflows for your incident orchestration processes.

## Creating and managing automation rules

You can create and manage automation rules from different points in the Microsoft Sentinel experience, depending on your particular need and use case.

Note

Navigation paths differ by portal. In the **Azure portal**, go to your Microsoft Sentinel workspace and select **Automation** under **Configuration**. In the **Defender portal**, select **Microsoft Sentinel** from the left navigation, then select **Automation**.

### Automation page

Automation rules can be centrally managed in the **Automation** page, under the **Automation rules** tab. (You can also manage playbooks in this page, under the **Playbooks** tab.) From there, you can create new automation rules and edit the existing ones. You can also drag automation rules to change the order of execution, and enable or disable them.

In the **Automation** page, you see all the rules that are defined on the workspace, along with their status (Enabled/Disabled) and which analytics rules they're applied to.

When you need an automation rule that applies to many analytics rules, create it directly in the **Automation** page. From the top menu, select Create and Add new rule, which opens the Create new automation rule panel. From here, you have complete flexibility in configuring the rule: you can apply it to any analytics rules (including future ones) and define the widest range of conditions and actions.

### Analytics rule wizard

In the Automated response tab of the analytics rule wizard, you can see, manage, and create automation rules that apply to the particular analytics rule being created or edited in the wizard.

When you select Create and one of the rule types (Scheduled query rule or Microsoft incident creation rule) from the top menu in the Analytics blade, or if you select an existing analytics rule and select Edit, you open the rule wizard. When you select the Automated response tab, you see a section called Incident automation, under which the automation rules that currently apply to this rule will be displayed. You can select an existing automation rule to edit, or select Add new to create a new one.

You'll notice that when you create the automation rule from here, the Create new automation rule panel shows the analytics rule condition as unavailable, because this rule is already set to apply only to the analytics rule you're editing in the wizard. All the other configuration options are still available to you.

### Incidents blade

You can also create an automation rule from the Incidents blade, in order to respond to a single, recurring incident. This is useful when creating a suppression rule for automatically closing "noisy" incidents. Select an incident from the queue and select Create automation rule from the top menu.

You notice that the Create new automation rule panel has populated all the fields with values from the incident. It names the rule the same name as the incident, applies it to the analytics rule that generated the incident, and uses all the available entities in the incident as conditions of the rule. It also suggests a suppression (closing) action by default, and suggests an expiration date for the rule. You can add or remove conditions and actions, and change the expiration date, as you wish.

## Components of an Automation Rule

Automation rules are made up of several components:

- **Trigger:** Automation rules support three trigger types:
    
    - **When an incident is created** – the most common trigger; used for initial triage, assignment, and tagging.
    - **When an incident is updated** – fires when incident status, severity, owner, or other properties change; useful for escalation and synchronization workflows.
    - **When an alert is created** – fires when a Scheduled or NRT analytics rule generates an alert; used when responding to alerts that don't create incidents, or in Defender portal workspaces where incident creation is managed by Defender XDR.
    
    Note
    
    In the Defender portal, incident-trigger automation rules run on both Microsoft Sentinel and Defender XDR incidents. Alert-trigger rules run on Microsoft Sentinel alerts only.
    
- **Conditions:** Complex sets of conditions can be defined to govern when actions (see below) should run. These conditions are typically based on the states or values of attributes of incidents and their entities, and they can include AND/OR/NOT/CONTAINS operators.
    
- **Actions:** Actions can be defined to run when the conditions (see above) are met. You can define many actions in a rule, and you can choose the order in which they run (see below). The following actions can be defined using automation rules, without the need for the advanced functionality of a playbook:
    
    - **Changing the status of an incident**, keeping your workflow up to date.
        
        ```
        When changing to “closed,” specifying the closing reason and adding a comment. This helps you keep track of your performance and effectiveness, and fine-tune to reduce false positives.
        ```
        
    - **Changing the severity of an incident** – you can reevaluate and reprioritize based on the presence, absence, values, or attributes of entities involved in the incident.
        
    - **Assigning an incident to an owner** – this helps you direct types of incidents to the personnel best suited to deal with them, or to the most available personnel.
        
    - **Adding a tag to an incident** – this is useful for classifying incidents by subject, by attacker, or by any other common denominator.
        
        Also, you can define an action to **run a playbook**, in order to take more complex response actions, including any that involve external systems. Only playbooks activated by the incident trigger are available to be used in automation rules. You can define an action to include multiple playbooks, or combinations of playbooks and other actions, and the order in which they run.
        
        Playbooks using either version of Logic Apps (Standard or Consumption) will be available to run from automation rules.
        
- **Expiration date:** You can define an expiration date on an automation rule. The rule will be disabled after that date. This is useful for handling (that is, closing) "noise" incidents caused by planned, time-limited activities such as penetration testing.
    
- **Order:** You can define the order in which automation rules run. Later automation rules will evaluate the conditions of the incident according to its state after being acted on by previous automation rules.
    
    For example, if "First Automation Rule" changed an incident's severity from Medium to Low, and "Second Automation Rule" is defined to run only on incidents with Medium or higher severity, it won't run on that incident.

![[Pasted image 20261008144936.png]]

# Summary and resources
In this module, you learned how Microsoft Sentinel is also a platform for Security Orchestration, Automation, and Response (SOAR).

You should now be able to:

- Explain automation options in Microsoft Sentinel
- Create automation rules in Microsoft Sentinel

# Threat response with Microsoft Sentinel playbooks
# Introduction

A Microsoft Sentinel playbook is a collection of security procedures that you can run in response to alerts.

Contoso, Ltd. is a midsize financial services company in London with a New York branch office. Contoso uses several Microsoft products and services to implement data security and threat protection for its resources. These products are:

- Microsoft Office 365
    
- Microsoft Entra ID
    
- Microsoft Entra ID Protection
    
- Defender for Cloud Apps
    
- Microsoft Defender for Identity
    
- Microsoft Defender for Endpoint
    
- Microsoft Defender for Office 365
    
- System Center Endpoint Protection
    
- Microsoft Azure Information Protection
    

Contoso provides threat protection for its Azure-based and on-premises resources by using the paid version of Microsoft Defender for Cloud. The company also monitors and protects other non-Microsoft assets.

The Contoso Security Operations (SecOps) team didn't respond quickly enough to the organization's latest security incident. Contoso's IT director wants to implement Microsoft Sentinel playbooks to help the SecOps team identify and stop potential security threats. As Contoso's lead security engineer and Azure administrator, you've been tasked with setting up a Microsoft Sentinel playbook to respond to security incidents.

In this module, you'll learn about the Security Orchestration and the Automation and Response (SOAR) capabilities within Microsoft Sentinel. You'll examine how to create and edit Microsoft Sentinel playbooks, configure their workflow, and manage them.

By the end of this module, you'll be able to set up security playbooks in Microsoft Sentinel to help the SecOps team respond to alerts effectively.

## Learning objectives

- Explain Microsoft Sentinel SOAR capabilities.
    
- Explore the Microsoft Sentinel Logic Apps connector.
    
- Create a playbook to automate an incident response.
    
- Run a playbook on demand in response to an incident.
    

## Prerequisites

- Automation and monitoring
    
- Azure Monitor and its Log Analytics workspace
    
- Azure Logic Apps
    

## Interactive Lab Simulation

Note

Select the thumbnail image to start the lab simulation. When you're done, be sure to return to this page so you can continue learning.

[![Screenshot of the lab simulation page.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/sc-200-lab-simulation-create-a-playbook.png)](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20a%20playbook)


# Exercise - Create a Microsoft Sentinel playbook


The Create a Microsoft Sentinel playbook exercise in this module is an optional unit. However, if you want to perform this exercise, you need access to an Azure subscription where you can create Azure resources. If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn_a5845227-bcc3-38c7-0825-860c3dc7fc26) before you begin.

To deploy the prerequisites for the exercise, perform the following tasks.

Note

If you choose to perform the exercise in this module, be aware you might incur costs in your Azure Subscription. To estimate the cost, refer to [Microsoft Sentinel Pricing](https://azure.microsoft.com/pricing/details/azure-sentinel/).

## Task 1: Deploy Microsoft Sentinel

1. Select the following link:
    
    [![Deploy To Azure.](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftDocs%2Fmslearn-security-ops-sentinel%2Fmain%2Fmslearn-threat-response-sentinel-playbooks%2Fsentinel-template.json?azure-portal=true)
    
    You're prompted to sign in to Azure.
    
2. On the **Custom deployment** page, provide the following information:
    
    |Label|Description|
    |---|---|
    |Subscription|Select your Azure subscription.|
    |Resource Group|Select Create new and provide a name for the resource group such as `azure-sentinel-rg`.|
    |Region|From the drop-down menu, select the region where you want to deploy the Microsoft Sentinel.|
    |Workspace name|Provide a unique name for the Microsoft Sentinel workspace such as `<yourName>-Sentinel`, where _<yourName>_ represents the workspace name that you chose in the previous task.|
    |Location|Accept the default value of **[resourceGroup().location]**.|
    |Simplevm Name|Accept the default value of **simple-vm**.|
    |Simplevm Windows OS Version|Accept the default value of **2022-Datacenter**.|
    
    ![Screenshot of the custom deployment inputs for a Microsoft template.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/02-custom-deployment.png)
    
3. Select **Review + create**, and then, when the data has been validated select **Create**.
    
    Note
    
    Wait for the deployment to complete. The deployment should take less than five minutes.
    
    ![Screenshot of the successful custom deployment.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/02-custom-deployment-success.png)
    

## Task 2: Check the resources created

1. On the Deployment Overview page, select **Go to resource group**. The resources for your custom deployment appear.
    
2. Select **Home** and in **Azure services**, search for and select **Resource groups**.
    
3. Select **azure-sentinel-rg**.
    
4. Sort the list of resources by **Type**.
    
5. The resource group should contain the resources displayed in the following table.
    
    |Name|Type|Description|
    |---|---|---|
    |`<yourName>-Sentinel`|Log Analytics workspace|Log Analytics workspace used by Microsoft Sentinel, where _<yourName>_ represents the workspace name that you chose in the previous task.|
    |`simple-vmNetworkInterface`|Network interface|Network interface for the VM.|
    |`SecurityInsights(<yourName>-Sentinel)`|Solution|Security insights for Microsoft Sentinel.|
    |`st1<xxxxx>`|Storage account|Storage account used by the virtual machine.|
    |`simple-vm`|Virtual machine|Virtual machine (VM) used in the demonstration.|
    |`vnet1`|Virtual network|Virtual network for the VM.|
    

Note

The resources deployed and configuration steps completed in this exercise are required in the next exercise. If you intended to complete the next exercise, don't delete the resources from this exercise.

## Task 3: Configure Microsoft Sentinel Connectors

1. In the Azure portal, search for **Microsoft Sentinel**, and then select the previously created Microsoft Sentinel workspace.
    
2. On the **Microsoft Sentinel | Overview** pane, in the left menu, scroll down to **Content Management** and select **Content Hub**.
    
3. In the _Content Hub_ page, type _Azure Activity_ into the _Search_ form, and select the **Azure Activity** solution.
    
4. In the **Azure Activity** solution details pane, select **Install**.
    
5. In the center _Content name_ column, select the **Azure Activity** Data connector.
    
    Note
    
    This solution installs these Content types: 12 Analytic rules, 14 Hunting queries, 1 Workbook, and the Azure Activity Data connector.
    
6. Select **Open connector page**.
    
7. In the _Instructions/Configuration_ area, scroll down and under _2. Connect your subscriptions..._ select **Launch Azure Policy Assignment Wizard**.
    
8. In the **Basics** tab of the wizard, select the ellipsis _**...**_ under **Scope**. On the **Scopes** pane, select your subscription and then select **Select**.
    
9. Select the **Parameters** tab, and choose your Microsoft Sentinel workspace from the **Primary Log Analytics workspace** drop-down list.
    
10. Select the **Remediation** tab, and select the **Create a remediation task** checkbox. This action applies the policy assignment to already existing Azure resources.
    
11. Select the **Review + Create** button to review the configuration, and then select **Create**.
    
    Note
    
    The connector for Azure Activity uses policy assignments. You need to have role permissions that allow you to create policy assignments. And, it typically takes 15 minutes to display a status of **Connected**. While the connector deploys, you can continue performing the rest of the steps in this unit and subsequent units in this module.
    
    ![Screenshot that displays the Microsoft Sentinel Azure Activity Content Hub solution.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-azure-activity-content-hub-solution.png)
    

## Task 4: Create an analytics rule

1. In the Azure portal, search for and select **Microsoft Sentinel**, and then select the previously created Microsoft Sentinel workspace.
    
2. On the **Microsoft Sentinel** page, on the menu bar, in the **Configuration** section, select **Analytics**.
    
3. On the **Microsoft Sentinel | Analytics** page, select **Create** and then select **NRT Query Rule (Preview)**.
    
4. On the **General** page, provide the inputs in the following table, and then select **Next: Set rule logic >**.
    
    |Label|Description|
    |---|---|
    |Name|Provide a descriptive name, such as **Delete Virtual Machines**, to explain what type of suspicious activity the alert detects.|
    |Description|Enter a detailed description that helps other security analysts understand what the rule does.|
    |Tactics and Techniques|From the **Tactics and Techniques** drop-down menu, choose **Initial Access** category to classify the rule following the MITRE tactics.|
    |Severity|Select the **Severity** drop-down menu to categorize the level of importance of the alert as one of four options: High, Medium, Low, or Informational.|
    |Status|Specify the status of the rule. By default, the status is **Enabled.** You can select **Disabled** to disable the rule if it generates a large number of false positives.|
    
5. On the **Set rule logic** page, in the **Rule query** section, enter the following query:
    
    Kusto
    
    ```
      AzureActivity
      | where OperationNameValue == 'MICROSOFT.COMPUTE/VIRTUALMACHINES/DELETE'
      | where ActivityStatusValue == 'Success'
      | extend AccountCustomEntity = Caller
      | extend IPCustomEntity = CallerIpAddress
    ```
    
6. Accept the default values for all other settings and then select **Next: Incident setting**.
    
7. On the **Incident setting** tab, ensure that **Enabled** is selected for creation of incidents from alerts triggered by this analytics rule. And then select **Next: Automated response**.
    
8. On the **Automated response** tab, you can select a playbook to run automatically when the alert is generated. Only the playbooks that contain a Logic App Microsoft Sentinel connector are displayed.
    
9. Select **Next: Review**.
    
10. On the **Review and Create** page, verify that the validation passed, and then select **Create**.
    

Note

You can learn more about Microsoft Sentinel analytics rules in the "Threat detection with Microsoft Sentinel analytics" module.


# Exercise - Create a Microsoft Sentinel playbook

The Create a Microsoft Sentinel playbook exercise in this module is an optional unit. However, if you want to perform this exercise, you need access to an Azure subscription where you can create Azure resources. If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn_a5845227-bcc3-38c7-0825-860c3dc7fc26) before you begin.

To deploy the prerequisites for the exercise, perform the following tasks.

Note

If you choose to perform the exercise in this module, be aware you might incur costs in your Azure Subscription. To estimate the cost, refer to [Microsoft Sentinel Pricing](https://azure.microsoft.com/pricing/details/azure-sentinel/).

## Task 1: Deploy Microsoft Sentinel

1. Select the following link:
    
    [![Deploy To Azure.](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftDocs%2Fmslearn-security-ops-sentinel%2Fmain%2Fmslearn-threat-response-sentinel-playbooks%2Fsentinel-template.json?azure-portal=true)
    
    You're prompted to sign in to Azure.
    
2. On the **Custom deployment** page, provide the following information:
    
    |Label|Description|
    |---|---|
    |Subscription|Select your Azure subscription.|
    |Resource Group|Select Create new and provide a name for the resource group such as `azure-sentinel-rg`.|
    |Region|From the drop-down menu, select the region where you want to deploy the Microsoft Sentinel.|
    |Workspace name|Provide a unique name for the Microsoft Sentinel workspace such as `<yourName>-Sentinel`, where _<yourName>_ represents the workspace name that you chose in the previous task.|
    |Location|Accept the default value of **[resourceGroup().location]**.|
    |Simplevm Name|Accept the default value of **simple-vm**.|
    |Simplevm Windows OS Version|Accept the default value of **2022-Datacenter**.|
    
    ![Screenshot of the custom deployment inputs for a Microsoft template.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/02-custom-deployment.png)
    
3. Select **Review + create**, and then, when the data has been validated select **Create**.
    
    Note
    
    Wait for the deployment to complete. The deployment should take less than five minutes.
    
    ![Screenshot of the successful custom deployment.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/02-custom-deployment-success.png)
    

## Task 2: Check the resources created

1. On the Deployment Overview page, select **Go to resource group**. The resources for your custom deployment appear.
    
2. Select **Home** and in **Azure services**, search for and select **Resource groups**.
    
3. Select **azure-sentinel-rg**.
    
4. Sort the list of resources by **Type**.
    
5. The resource group should contain the resources displayed in the following table.
    
    |Name|Type|Description|
    |---|---|---|
    |`<yourName>-Sentinel`|Log Analytics workspace|Log Analytics workspace used by Microsoft Sentinel, where _<yourName>_ represents the workspace name that you chose in the previous task.|
    |`simple-vmNetworkInterface`|Network interface|Network interface for the VM.|
    |`SecurityInsights(<yourName>-Sentinel)`|Solution|Security insights for Microsoft Sentinel.|
    |`st1<xxxxx>`|Storage account|Storage account used by the virtual machine.|
    |`simple-vm`|Virtual machine|Virtual machine (VM) used in the demonstration.|
    |`vnet1`|Virtual network|Virtual network for the VM.|
    

Note

The resources deployed and configuration steps completed in this exercise are required in the next exercise. If you intended to complete the next exercise, don't delete the resources from this exercise.

## Task 3: Configure Microsoft Sentinel Connectors

1. In the Azure portal, search for **Microsoft Sentinel**, and then select the previously created Microsoft Sentinel workspace.
    
2. On the **Microsoft Sentinel | Overview** pane, in the left menu, scroll down to **Content Management** and select **Content Hub**.
    
3. In the _Content Hub_ page, type _Azure Activity_ into the _Search_ form, and select the **Azure Activity** solution.
    
4. In the **Azure Activity** solution details pane, select **Install**.
    
5. In the center _Content name_ column, select the **Azure Activity** Data connector.
    
    Note
    
    This solution installs these Content types: 12 Analytic rules, 14 Hunting queries, 1 Workbook, and the Azure Activity Data connector.
    
6. Select **Open connector page**.
    
7. In the _Instructions/Configuration_ area, scroll down and under _2. Connect your subscriptions..._ select **Launch Azure Policy Assignment Wizard**.
    
8. In the **Basics** tab of the wizard, select the ellipsis _**...**_ under **Scope**. On the **Scopes** pane, select your subscription and then select **Select**.
    
9. Select the **Parameters** tab, and choose your Microsoft Sentinel workspace from the **Primary Log Analytics workspace** drop-down list.
    
10. Select the **Remediation** tab, and select the **Create a remediation task** checkbox. This action applies the policy assignment to already existing Azure resources.
    
11. Select the **Review + Create** button to review the configuration, and then select **Create**.
    
    Note
    
    The connector for Azure Activity uses policy assignments. You need to have role permissions that allow you to create policy assignments. And, it typically takes 15 minutes to display a status of **Connected**. While the connector deploys, you can continue performing the rest of the steps in this unit and subsequent units in this module.
    
    ![Screenshot that displays the Microsoft Sentinel Azure Activity Content Hub solution.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-azure-activity-content-hub-solution.png)
    

## Task 4: Create an analytics rule

1. In the Azure portal, search for and select **Microsoft Sentinel**, and then select the previously created Microsoft Sentinel workspace.
    
2. On the **Microsoft Sentinel** page, on the menu bar, in the **Configuration** section, select **Analytics**.
    
3. On the **Microsoft Sentinel | Analytics** page, select **Create** and then select **NRT Query Rule (Preview)**.
    
4. On the **General** page, provide the inputs in the following table, and then select **Next: Set rule logic >**.
    
    |Label|Description|
    |---|---|
    |Name|Provide a descriptive name, such as **Delete Virtual Machines**, to explain what type of suspicious activity the alert detects.|
    |Description|Enter a detailed description that helps other security analysts understand what the rule does.|
    |Tactics and Techniques|From the **Tactics and Techniques** drop-down menu, choose **Initial Access** category to classify the rule following the MITRE tactics.|
    |Severity|Select the **Severity** drop-down menu to categorize the level of importance of the alert as one of four options: High, Medium, Low, or Informational.|
    |Status|Specify the status of the rule. By default, the status is **Enabled.** You can select **Disabled** to disable the rule if it generates a large number of false positives.|
    
5. On the **Set rule logic** page, in the **Rule query** section, enter the following query:
    
    Kusto
    
    ```
      AzureActivity
      | where OperationNameValue == 'MICROSOFT.COMPUTE/VIRTUALMACHINES/DELETE'
      | where ActivityStatusValue == 'Success'
      | extend AccountCustomEntity = Caller
      | extend IPCustomEntity = CallerIpAddress
    ```
    
6. Accept the default values for all other settings and then select **Next: Incident setting**.
    
7. On the **Incident setting** tab, ensure that **Enabled** is selected for creation of incidents from alerts triggered by this analytics rule. And then select **Next: Automated response**.
    
8. On the **Automated response** tab, you can select a playbook to run automatically when the alert is generated. Only the playbooks that contain a Logic App Microsoft Sentinel connector are displayed.
    
9. Select **Next: Review**.
    
10. On the **Review and Create** page, verify that the validation passed, and then select **Create**.
    

Note

You can learn more about Microsoft Sentinel analytics rules in the "Threat detection with Microsoft Sentinel analytics" module.

# What are Microsoft Sentinel playbooks?
In addition to assessing and addressing problems with their security configuration, Contoso must also monitor for new problems and threats, and then respond appropriately.

## Microsoft Sentinel as a SIEM and SOAR solution

Microsoft Sentinel is both a Security Information and Event Management (SIEM) and Security Orchestration, Automation and Response (SOAR) solution that's designed for hybrid environments.

Note

SIEM solutions provide storage and analysis of logs, events, and alerts that other systems generate. You can configure these solutions to raise their own alerts. SOAR solutions support the remediation of vulnerabilities and the overall automation of security processes.

Microsoft Sentinel uses built-in and custom detections to alert you to potential security threats such as attempts to access Contoso's resources from outside its infrastructure or when data from Contoso appears to be sent to a known malicious IP address. You can also create incidents based on these alerts.

## Microsoft Sentinel playbooks

You can create security playbooks in Microsoft Sentinel to respond to alerts. _Security playbooks_ are collections of procedures based on Azure Logic Apps that run in response to an alert. You can run these security playbooks manually in response to your investigation of an incident or you can configure an alert to run a playbook automatically.

With the ability to respond to incidents automatically, you can automate some of your security operations and make your Security Operations Center (SOC) more productive.

For example, to address Contoso's concerns, you can develop a workflow with defined steps that can block a suspicious username from accessing resources from a nonsecure IP address. Alternatively, you can configure the playbook to perform an operation such as notifying the SecOps team about a high-level security alert.

## Azure Logic Apps

Azure Logic Apps is a cloud service that automates the operation of your business processes. You use a graphical design tool called the _Logic Apps Designer_ to arrange prebuilt components into the sequence you need. You can also use the code view and write your automated process in the JSON file.

## Logic Apps Connector

Logic apps use connectors to connect to hundreds of services. A _connector_ is a component that provides an interface to an external service.

Note

A Microsoft Sentinel data connector and a Logic Apps connector aren't the same thing. A Microsoft Sentinel data connector connects Microsoft Sentinel with Microsoft security products and security ecosystems for non-Microsoft solutions. A Logic Apps connector is a component that provides an API connection for an external service and allows integration of events, data, and actions across other apps, services, systems, protocols, and platforms.

## What are triggers and actions

Azure Logic Apps use triggers and actions, which are defined as follows:

- A _trigger_ is an event that occurs when a specific set of conditions is satisfied. Triggers activate automatically when conditions are met. For example, a security incident occurs in Microsoft Sentinel, which is a trigger for an automated action.
    
- An _action_ is an operation that performs a task in the Logic Apps workflow. Actions run when a trigger activates, another action completes, or a condition is met.
    

## Microsoft Sentinel Logic Apps connector

A Microsoft Sentinel playbook uses a Microsoft Sentinel Logic Apps connector. It provides the triggers and actions that can start the playbook and perform defined actions.

Currently, there are two triggers from Microsoft Sentinel Logic Apps connector:

- When a response to a Microsoft Sentinel alert is triggered
    
- When Microsoft Sentinel incident creation rule is triggered
    

Note

Because Microsoft Sentinel Logic App connector is in preview, the features described in this module might change in the future.

The following table lists all the current actions for the Microsoft Sentinel connector.

|Name|Description|
|---|---|
|Add comment to incident|Adds comments to the selected incident.|
|Add labels to incident|Adds labels to the selected incident.|
|Alert - Get incident|Returns the incident associated with the selected alert.|
|Change incident description|Changes the description for the selected incident.|
|Change incident severity|Changes the severity for the selected incident.|
|Change incident status|Changes the status for the selected incident.|
|Change incident title (V2)|Changes the title for the selected incident.|
|Entities - Get Accounts|Returns a list of accounts associated with the alert.|
|Entities - Get FileHashes|Returns a list of File Hashes associated with the alert.|
|Entities - Get Hosts|Returns a list of hosts associated with the alert.|
|Entities - Get IPs|Returns a list of IPs associated with the alert.|
|Entities - Get URLs|Returns a list of URLs associated with the alert.|
|Remove labels from incident|Removes the labels for the selected incident.|

Note

Actions that have **(V2)** or a higher number provide a new version of the action and might differ from the old functionality of the action.

Some actions require integration with actions from another connectors. For example, if Contoso wants to identify all suspicious accounts returned in the alert from the defined entities, you must combine the **Entities - Get Accounts** action with the **For Each** action. Similarly, to get all individual hosts in an incident that detect suspicious hosts, you must combine the **Entities - Get Hosts** action with the **For Each** action.

![[Pasted image 20261008151516.png]]

# Trigger a playbook in real-time
You can configure Microsoft Sentinel playbooks at Contoso to respond to security threats.

## Explore the Playbooks page

You can automate responses to threats on the **Playbooks** page. On this page, you can observe all the playbooks that are created from Azure Logic Apps. The column **Trigger kind** presents what type of connectors are used in the logic app.

You can use the header bar, as displayed in the following diagram, to create new playbooks or to enable or disable existing playbooks.

![Screenshot of the header bar.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/04-playbooks-header.png)

The header bar provides the following options:

- Use the **Add Playbook** option to create a new playbook.
    
- Use the **Refresh** option to refresh the display, for example, after you create a new playbook.
    
- Use the drop-down time field to filter the status of the running of the playbooks.
    
- The **Enable**, **Disable**, and **Delete** option are only available if you select one or more logic apps.
    
- Use the **Logic Apps documentation** option to review links to official Microsoft documentation for more information on logic apps.
    

Contoso wants to use automated actions to prevent suspicious users from accessing their network. As their security administrator, you can create a playbook to implement this action. To create a new playbook, select **Add Playbook**. You'll be directed to the page where you should create a new logic app by providing inputs for the following settings:

- **Subscription**. Select the subscription that contains Microsoft Sentinel.
    
- **Resource Group**. You can use an existing resource group or create a new one.
    
- **Logic App name**. Provide a descriptive name for the logic app.
    
- **Location**. Select the same location as where your Log Analytics workspace is located.
    
- **Log Analytics**. If you enable Log Analytics, you can get information about playbook's runtime events.
    

After providing these inputs, select the **Review + Create** option, and then select **Create**.

## Logic Apps Designer

Microsoft Sentinel creates the logic app, and then you're directed to the **Logic App Designer** page.

The Logic App Designer provides a design canvas that you use to add a trigger and actions to your workflow. For example, you can configure the trigger to originate from the Microsoft Sentinel Connector when a new security incident is created. The Logic App Designer page provides many predefined templates that you can use. However, to create a playbook, you should start with the **Blank Logic App** template to design the logic app from scratch.

The automated activity in the playbook is initiated by the Microsoft Sentinel trigger. You can search for the Microsoft Sentinel trigger in the search box of the design canvas, and then select one of the following two available triggers:

- When a response to a Microsoft Sentinel alert is triggered
    
- When Microsoft Sentinel incident creation rule was triggered
    

Opening Microsoft Sentinel Connector for the first time prompts you to **Sign in** to your tenant either with a user account from Microsoft Entra ID or with Service Principal. This establishes an API connection to your Microsoft Entra ID. The API connections store variables and tokens that are required to access the API for the connection, such as Microsoft Entra ID, Office 365, or similar.

![Screenshot of sign-in to the Microsoft Entra tenant.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/04-sign-in-aad-tenant.png)

Each playbook starts with a trigger followed by actions that define the automated response on a security incident. You can combine actions from a Microsoft Sentinel connector with other actions from other Logic Apps connectors.

For example, you can add the trigger from a Microsoft Sentinel connector when an incident is triggered, follow it with an action that identifies the entities from the Microsoft Sentinel alert, and then another action that sends an email to an Office 365 email account. Microsoft Sentinel creates every action as a **New Step** and defines the activity that you're adding in the logic app.

The following screenshot displays the incident triggered by Microsoft Sentinel connector, which detects a suspicious account and sends an email to the administrator.

![Screenshot of the logic app with actions.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/04-log-app-designer.png)

Each step in the workflow design has different fields that you must fill. For example, the **Entities - Get Accounts** action requires you to provide the list of entities from a Microsoft Sentinel alert. An advantage of using Azure Logic Apps is that you can provide this input from the **Dynamic content** list, which is populated with the outputs of the previous step. For example, the Microsoft Sentinel connector trigger **When a response to Microsoft Sentinel Alert is triggered** provides dynamic properties such as **Entities, Alert Display name**, which you can use to fill the inputs.

![Screenshot that displays dynamic content.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/04-dynamic-content.png)

You can also add a control actions group that lets your logic app make decisions. The control actions group can include logical conditions, switch case conditions, or loops.

A **condition** action is an **if** statement that lets your app perform different actions based on the data you're processing. It consists of a Boolean expression and two actions. At runtime, the execution engine evaluates the expression and chooses an action based on whether the expression is true or false.

For example, Contoso receives a large volume of alerts, many of them with recurring patterns, which can't be processed or investigated. Using real-time automation, the Contoso SecOps teams can significantly reduce their workload by fully automating the routine responses to recurring types of alerts.

The following screenshot presents a similar situation, where based on the user input, the playbook can change the status of the alert. The control action intercepts the user input, and if the expression evaluates to be a true statement, the playbook changes the status of the alert. In case the control action evaluates the expression to be false, the playbook can run other activities, such as sending an email as depicted in the following screenshot.

![Screenshot that displays the logic app condition.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/04-condition.png)

After you provide all the steps in the Logic Apps Designer, save the logic app to create a playbook in Microsoft Sentinel.

## The Logic Apps page in Microsoft Sentinel

The playbooks you create appear on the **Playbooks** page, and you can further edit them. From the **Playbooks** page, you can select an existing playbook and that will open the Logic Apps page for that playbook in Microsoft Sentinel.

You can run several actions on the playbook from the Logic Apps header bar:

- **Run Trigger**. Use to run the logic app to test the playbook.
    
- **Refresh**. Use to refresh the status of the logic app to retrieve the status of the activity.
    
- **Edit**. Use to further edit the playbook in the **Logic Apps Designer** page.
    
- **Delete**. Use to delete the logic app if you don't need it.
    
- **Disable**. Use to temporarily disable the logic app to prevent the action from being performed even if the trigger is activated.
    
- **Update Schema**. Use to update the schema of the logic app after a significant change in the logic.
    
- **Clone**. Use to make a copy of the existing logic app, and then use that as a basis for further modification.
    
- **Export**. Use to export the logic app to Microsoft Power Automate and Microsoft Power Apps.
    

The **Essentials** section displays descriptive information about the logic app. For example, the logic app definition displays the number of triggers and actions that the logic app provides.

You can use the **Summary** section, to review summarized information about the logic app. From this section, you can select the logic app link to open it in the Logic Apps Designer or review the trigger history.

The **Runs history** section displays the previous runs of the logic app and whether they succeeded or failed.

## Automate response to an incident in Microsoft Sentinel

As a final step, you need to attach this playbook to an analytics rule to automate responses to an incident. You can use the **Automated Response** section in the analytics rule to select a playbook to run automatically when the alert is generated. For more information on how to create analytics rule, see the "Threat detection with Microsoft Sentinel analytics" module.

![[Pasted image 20261008153336.png]]

# Run playbooks on demand

Some incidents at Contoso might require further investigation before you run a playbook. Microsoft Sentinel allows you to run playbooks on demand to facilitate in-depth investigations.

## Run a playbook on demand

You can configure playbooks to run on demand based on incident details, to trigger specific steps as part of the investigation, or to conduct some remediation action.

Consider the scenario where suspicious users are prevented from accessing corporate resources. As the security administrator at Contoso, you find one false positive incident. Some users at Contoso were accessing resources over a virtual private network connection from remote computers while being connected to the office computers at the same time. Microsoft Cloud Security received signals and based on the vulnerability that detects potential threat from atypical travel locations, it tagged the users as medium risk.

You can use a playbook that can automatically dismiss this risky user property in Microsoft Entra ID.

## Microsoft Sentinel repository on GitHub

[Microsoft Sentinel repository on GitHub](https://github.com/Azure/Azure-Sentinel) contains ready-to-use playbooks to help you automate responses on incidents. These playbooks are defined with Azure Resource Manager (ARM template) that uses Logic App Microsoft Sentinel triggers.

For the scenario described earlier, you can use the **Dismiss-AADRiskyUser** playbook, which is located in the Microsoft Sentinel repository on GitHub, and deploy it directly in your Azure subscription.

For each deployment from GitHub, you first must authorize each connection in the playbook before you edit them in Logic Apps Designer. Authorization will create an API connection to the appropriate connector and store the token and variables. You can locate the API connection in the resource group where you created the logic app.

The name of each API connection is appended with the **azuresentinel** prefix. You can also edit the connection in the Logic Apps Designer when you edit the logic app.

![Screenshot that depicts the authorization of the API connection.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/05-api-connection.png)

## Attach a playbook to an existing incident

After your playbook is ready, you can open the **Incident** page in Microsoft Sentinel, and then select the existing incident. In the details pane, you can select **View full details** to explore the properties of the incident. From the **Alerts panel,** you can select **View playbooks**, and then you can run one of the existing playbooks.

The following screenshot depicts the suspicious user activity example for which you can attach the **Dismiss-AADRiskyUser** playbook.

![Screenshot of the Incident page.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/05-incident-page.png)

After you've investigated the incident, you can choose to run the playbook manually to respond to a security threat.

![[Pasted image 20261008153819.png]]

# Exercise - Create a Microsoft Sentinel playbook

As a Security Operations Analyst working for Contoso, you recently notice that a significant number of alerts are generated when someone deletes a virtual machine. You want to analyze such occurrences in the future and reduce the alerts generated for false positive occurrences.

## Exercise: Threat response using Microsoft Sentinel playbooks

You decide to implement a Microsoft Sentinel playbook to automate responses to an incident.

In this exercise, you'll explore the Microsoft Sentinel playbooks by performing the following tasks:

- Configure Microsoft Sentinel Playbook permissions.
    
- Create a playbook to automate an action to respond to incidents.
    
- Test your playbook by invoking an incident.
    

Note

You need to have completed the Exercise Setup unit, in order to be able to complete this exercise. If you have not done so, complete it now, and then continue with the exercise steps.

### Task 1: Configure Microsoft Sentinel Playbook permissions

1. In the Azure portal, search for and select Microsoft Sentinel, and select the previously created Microsoft Sentinel workspace.
    
2. In the **Microsoft Sentinel** page, on the menu bar, in the **Configuration** section, select **Settings**.
    
3. In the **Settings** page, select the **Settings** tab and scroll down and expand the **Playbook permissions**
    
4. In **Playbook permissions**, select the **Configure permissions** button.
    
    ![Screenshot of the Microsoft Sentinel Playbook permissions.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-sentinel-playbook-permissions.png)
    
5. In the **Manage permissions** page under the **Browse** tab, select the resource group that your Microsoft Sentinel workspace belongs to. Select **Apply**.
    
    ![Screenshot of the Microsoft Sentinel Playbook Manage permissions page.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-manage-permissions.png)
    
6. You should see the **Finished adding permissions** message.
    

### Task 2: Work with Microsoft Sentinel playbooks

1. In the Azure portal, search for and select Microsoft Sentinel, and select the previously created Microsoft Sentinel workspace.
    
2. In the **Microsoft Sentinel** page, on the menu bar, in the **Configuration** section, select **Automation**.
    
3. On the top menu, select **Create** and **Playbook with incident trigger**.
    
4. In the **Create Playbooks** page, on the **Basics** tab, specify the following settings:
    
    |**Settings**|**Value**|
    |---|---|
    |Subscription|Select your Azure subscription.|
    |Resource group|Select the resource group of your Microsoft Sentinel service.|
    |Playbook name|**ClosingIncident** _(you can choose any name)_|
    |Region|Select the same location as the location of Microsoft Sentinel.|
    |Log Analytics workspace|**Don't enable diagnostic logs**|
    
5. Select **Next:Connections >**, then select **Next: Review and Create >**
    
6. Select **Create and continue to designer**
    
    Note
    
    Wait for the deployment to complete. The deployment should take less than 1 minute. If it keeps running you may need to refresh the page.
    
7. In the **Logic Apps Designer** pane, you should see the **Microsoft Sentinel incident (preview)** displayed.
    
    ![Screenshot of the Microsoft Sentinel trigger.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-azure-sentinel-trigger.png)
    
8. On the **Microsoft Sentinel incident (preview)** page, select the **Change connection** link.
    
9. On the **Connections** page, select **Add new**.
    
10. On the Microsoft Sentinel page, select **Sign in**.
    
    ![Screenshot of the authorizing API connection.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-sign-in-aad-tenant.png)
    
11. On the **Sign in to your account** page, provide the credentials for your Azure subscription.
    
12. Back on the **Microsoft Sentinel incident (preview)** page, you should see you're connected to your account. Select **+ New step**.
    
13. In the **Choose an operation** window, in the search field, type **Microsoft Sentinel**.
    
14. Select the **Microsoft Sentinel** Icon.
    
15. On the **Actions** tab, locate and select **Get incident (Preview)**.
    
16. In the **Get Incident (Preview)** window, select the **Incident ARM ID field**. The **Add dynamic content** window opens.
    
    Tip
    
    When you select a field, a new window opens to help you fill these fields with dynamic content.
    
17. On the **Dynamic content** tab, in the search box, you can start entering **Incident ARM**, and then select the entry from the list, as the following screenshot displays.
    
    ![Screenshot of Get Incident.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-get-incident.png)
    
18. Select **+ New step**.
    
19. In the **Choose an operation** window, in the search field, type **Microsoft Sentinel**.
    
    Tip
    
    In the For you tab, Recent selections should display the Microsoft Sentinel Icon.
    
20. Select the **Microsoft Sentinel** Icon.
    
21. From the **Actions** tab, locate and select **Update incident (Preview)**.
    
22. In the **Update incident (Preview)** window, provide the following inputs:
    
    |Settings|Values|
    |---|---|
    |Specify Incident ARM id|**Incident ARM ID**|
    |Specify Owner Object Id / UPN|**Incident Owner Object ID**|
    |Specify Assign/Unassign owner|From the drop-down menu, select **Unassign**|
    |Severity|You can leave the default **Incident severity**|
    |Specify Status|From the drop-down menu, select **Closed**.|
    |Specify Classification reason|From the drop-down menu, select an entry like **Undetermined**, or select **Enter custom value**, and select IncidentClassification Dynamic content.|
    |Close reason text|Write descriptive text.|
    
    ![Screenshot of the Get Incident status.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-change-incident-status.png)
    
23. Select the **Incident ARM ID field**. The **Add dynamic content** window opens, in the search box, you can start entering **Incident ARM**. Select **Incident ARM ID** and then select the **Owner Object Id / UPN** field.
    
24. The **Add dynamic content** window opens, in the search box, you can start entering **Incident owner**. Select **Incident Owner Object ID** and then fill in the remaining fields using the table entries.
    
25. When done, choose **Save** from the Logic Apps Designer menu bar, and then close the Logic Apps Designer.
    

### Task 3: Invoke an incident and review the associated actions

1. In the Azure portal, in the **Search resources, services, and docs** text box, type **virtual machines**, and then select **Enter**.
    
2. On the **Virtual machines** page, locate and select the **simple-vm** virtual machine, and then on the header bar, select **Delete**.
    
3. On the **Delete simple-vm** page, select **Delete with VM** for both the **OS Disk** and the **Network Interface**.
    
4. Select the box to acknowledge **I have read and understand that this virtual machine as well as any selected resources will be deleted**, then select **Delete** to delete the virtual machine.
    
    ![Screenshot of the Delete simple-vm page.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-delete-simple-vm.png)
    
    Note
    
    This task creates an incident based on the analytics rule that you created earlier in the exercise setup unit. Incident creation can take up to 15 minutes. Wait for it to complete before proceeding to the next step.
    

### Task 4: Assign the playbook to an existing incident

1. In the Azure portal, search for and select Microsoft Sentinel, and then select the previously created Microsoft Sentinel workspace.
    
2. On the **Microsoft Sentinel | Overview** page, on the menu bar, in the **Threat management** section, select **Incidents**.
    
    Note
    
    As mentioned in the previous note, Incident creation can take up to 15 minutes. Refresh the page until incident appears in the **Incidents** page.
    
3. On the **Microsoft Sentinel | Incidents** page, select an incident that has been created based on the deletion of the virtual machine.
    
4. In the details pane, select **Actions** and **Run playbook (Preview)**.
    
    [![Screenshot of the Incident detail pane actions to run playbook.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-incident-run-playbook.png)](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-incident-run-playbook.png#lightbox)
    
5. On the **Run playbook on incident** page, in the **Playbooks tab,** you should see the **ClosingIncident** playbook, select **Run**.
    
6. Verify that you receive the message **Playbook was triggered successfully**.
    
7. Close the **Run playbook on incident** page, to return to the **Microsoft Sentinel | Incidents** page.
    
8. In the **Microsoft Sentinel | Incidents** page, on the header bar, select **Refresh**. You'll notice that the incident disappears from the pane. On the **Status** menu, select **Closed**, and then select **OK**.
    
    Note
    
    It could take up to 5 minute for Alerts to be shown as **Closed**
    
    ![Screenshot of the header bar.](https://learn.microsoft.com/en-us/training/wwl-sci/threat-response-sentinel-playbooks/media/06-header-refresh.png)
    
9. Verify that the incident displays again and notice the **Status** column to check that it's **Closed**.
    

### Clean up the resources

1. In the Azure portal, search for **Resource groups**.
    
2. Select **azure-sentinel-rg**.
    
3. On the header bar, select **Delete resource group**.
    
4. In the **TYPE THE RESOURCE GROUP NAME:** field, enter the name of the resource group **azure-sentinel-rg** and select **Delete**

# Summary
## Resolution of module problem

Contoso SecOps wanted to improve their response time to security incidents and prevent future incidents. Contoso decides to use Microsoft Sentinel playbooks, which are based on Logic Apps with a Microsoft Sentinel connector to provide near real-time responses. In this module, you learned how to create Sentinel playbooks that can respond in real time on a security thread. You also learned how to start a playbook on demand as response to investigation on a security alert.

# Security incident management in Microsoft Sentinel
# Introduction

Imagine that you're a security engineer for Contoso, Ltd., a midsize financial services company in London with a New York branch office. Contoso uses the following Microsoft security management products:

- Microsoft 365
- Microsoft Entra ID
- Microsoft Entra ID Protection
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity
- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- Intune Endpoint Protection
- Azure Information Protection

Contoso uses Microsoft Defender for Cloud as threat protection for resources that run on Azure and on-premises. The company also monitors and protects other non-Microsoft assets.

Recently, the company's Azure Activity log showed that a significant number of VMs were deleted from the Azure subscription. You need to analyze this occurrence and be alerted when similar activity occurs in the future.

Microsoft Sentinel is a cloud application that can help you protect Contoso's resources. In this module, you learn how to use Microsoft Sentinel to create and investigate an incident when a Contoso user deletes an existing VM.

## Learning objectives

- Learn about security incidents and Microsoft Sentinel incident management.
- Explore Microsoft Sentinel incident evidence and entities.
- Use Microsoft Sentinel to investigate security incidents and manage incident resolution.

## Prerequisites

- Familiarity with security operations in an organization.
- Basic experience with Azure services.
- Knowledge of operational concepts, such as monitoring, logging, and alerting.
- Basic knowledge of Microsoft Sentinel rules.
# Exercise - Set up the Azure environment

To set up the Azure environment for the optional incident management exercise, complete the following steps.

## Prerequisites

To complete this optional exercise, you need access to an Azure subscription. If you don't have a subscription, create a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn_c0d1360f-b1ac-5d40-89d6-b4bd3dc295e9).

Note

Be aware that this exercise creates resources that might incur costs in your Azure subscription. To estimate the costs, see [Microsoft Sentinel pricing](https://azure.microsoft.com/pricing/details/azure-sentinel/).

## Deploy the Azure Resource Manager template

1. Select the following button to deploy the Azure Resource Manager (ARM) template that creates the Azure resources. Sign in to Azure if prompted.
    
    [![Deploy To Azure.](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftDocs%2Fmslearn-security-ops-sentinel%2Fmain%2Fmslearn-incident-management-sentinel%2Fsentinel-template.json?azure-portal=true)
    
2. On the **Custom deployment** page, provide the following information:
    
    - **Subscription**: Select your Azure subscription if not already selected.
    - **Resource group**: Select **Create new**, and name the resource group _azure-sentinel-rg_.
    - **Location**: Select the Azure region where you want to deploy Microsoft Sentinel.
    - **Workspace name**: Provide a unique name for the Microsoft Sentinel workspace, such as _<yourName>-Sentinel_.
3. Leave the other settings as is, select **Review + create**, and then select **Create**.
    

Wait for the deployment to finish. The deployment should take less than five minutes.

## Verify deployed resources

1. When the deployment finishes, select **Go to resource group**, or search for **Resource groups** in the portal and then select **azure-sentinel-rg**.
    
2. On the **azure-sentinel-rg** page, sort the list of resources by **Type**.
    
3. Confirm that the resource group contains the following resources:
    
    |Name|Type|Description|
    |---|---|---|
    |**<yourName>-Sentinel**|Log Analytics workspace|Log Analytics workspace that Microsoft Sentinel uses, with the name you chose for the workspace.|
    |**simple-vmNetworkInterface**|Network interface|Network interface for the VM.|
    |**SecurityInsights(<yourName>-Sentinel)**|Solution|Security insights for Microsoft Sentinel.|
    |**st1<xxxxx>**|Storage account|Storage account used by the VM, where **<xxxxx>** represents a random string that's generated to create a unique storage account name.|
    |**simple-vm**|Virtual machine (VM)|VM to use in the demonstration.|
    |**vnet1**|Virtual network|Virtual network for the VM.|
    

## Configure the Microsoft Sentinel connector

Next, deploy the Azure Activity log connector for Microsoft Sentinel.

1. In the [Azure portal](https://portal.azure.com/), search for and select **Microsoft Sentinel**.
2. On the **Microsoft Sentinel** page, select the Microsoft Sentinel workspace you created.
3. On the workspace page, select **Data connectors** under **Configuration** in the left menu.
4. On the **Data connectors** page, search for and select **Azure Activity**, and then select **Open connector page** on the **Azure Activity** screen.
5. At the bottom of the **Azure Activity** page, select **Launch Azure Policy Assignment Wizard**.
6. In the **Basics** tab of the wizard, select the ellipsis _**...**_ under **Scope**. On the **Scopes** pane, select your subscription and then select **Select**.
7. Select the **Parameters** tab, and choose your Microsoft Sentinel workspace from the **Primary Log Analytics workspace** drop-down list.
8. Select the **Remediation** tab, and select the **Create a remediation task** checkbox. This action applies the subscription configuration to send the information to the Log Analytics workspace.
9. Select the **Review + Create** button to review the configuration, and then select **Create**.

The Azure Activity connector might take up to an hour to display a status of **Connected**. While the connector deploys, continue to the following units to learn about incidents in Microsoft Sentinel.


# Understand incidents
Technology-related threats to an organization are called _incidents_. Incident management is the complete process of incident investigation, from incident creation to in-depth investigation and resolution. Microsoft Sentinel can help your IT team organize, investigate, and track incidents from creation through resolution.

![[Pasted image 20261008155800.png]]

# Incident evidence and entities
Microsoft Sentinel uses various sources of security information to create incidents. You need to understand these sources to best utilize incident management in Microsoft Sentinel.

## Incident evidence

Incident _evidence_ consists of the security event information and related Microsoft Sentinel assets that identify threats in the Microsoft Sentinel environment. Evidence shows how Microsoft Sentinel has identified a threat, and links back to specific resources that can increase your awareness of incident details.

### Events

Events link you back to one or more specific events from the Log Analytics workspace associated with Microsoft Sentinel. On their own, these workspaces typically contain thousands of events that are too numerous to manually parse.

If a query attached to a Microsoft Sentinel analytics rule returns events, it attaches the events to the generated incident for potential further review. You can use these events to understand the scope and frequency of the incident before you investigate further.

### Alerts

Most incidents are generated because of an analytics rule alert. Examples of alerts include:

- Detection of suspicious files.
- Detection of suspicious user activities.
- Attempted elevation of privilege.

Analytics rules generate alerts based either on Kusto Query Language (KQL) queries or direct connection to Microsoft Security solutions like Microsoft Defender for Cloud or Microsoft Defender XDR. If you enable alert grouping, Microsoft Sentinel includes any related alert evidence for the incident.

### Bookmarks

While investigating an incident, you might identify events that you want to track or mark for later investigation. You can preserve the queries run in Log Analytics by choosing one or more events and designating them as bookmarks. You can also record notes and tags to better inform future threat-hunting processes. Bookmarks are available to you and your teammates.

## Incident entities

An incident _entity_ refers to a network or user resource that's involved with an event. You can use entities as entry points to explore all alerts and correlations associated with that entity.

Entity relationships are useful when you're investigating incidents. Instead of analyzing the identity alerts, network alerts, and data access alerts individually, you can use entities to observe any alerts associated with a particular user, host, or address in your environment.

Some entity types include:

- Account
- Host
- IP
- URL
- FileHash

For instance, entities could help you identify all the alerts associated with a specific user at Contoso, the user's host machine, and other hosts that the user has connected to. You can determine which IP addresses are associated with that user, exposing which events and alerts could be part of the same attack.

You can use Microsoft Sentinel to review detailed incident information, assign an incident owner, set and maintain incident severity, and manage incident status. Microsoft Sentinel provides a complete incident management environment to handle these steps.

## Key concepts

It's important to understand the following key Microsoft Sentinel incident management concepts:

- **Data connectors**. You can use Microsoft Sentinel data connectors to ingest and collect data from security-related services. Data connectors can collect events from Linux or Windows computers running the Log Analytics agent, from a Linux syslog server for devices like firewalls or proxies, or directly from Microsoft Azure services. These events forward to a Log Analytics workspace associated with Microsoft Sentinel.
- **Events**. Microsoft Sentinel stores events in a Log Analytics workspace. These events contain the details of security-related activity that you want Microsoft Sentinel to monitor.
- **Analytics rules**. Analytics rules detect important security events and generate alerts. You can create analytics rules by using built-in templates or by using custom Kusto Query Language (KQL) queries against Log Analytics workspaces in Microsoft Sentinel.
- **Alerts**. Analytics rules generate alerts when they detect important security events. You can configure alerts to generate incidents.
- **Incidents**. Microsoft Sentinel creates incidents from analytics rule alerts. Incidents can contain multiple related alerts. You use each incident as a starting point and tracking mechanism for investigation into security concerns in your environment.

### Microsoft Sentinel Overview page

Incident management in Microsoft Sentinel begins on the **Overview** page, where you can review the current Microsoft Sentinel environment. The **Overview** page shows a list of the most recent incidents, along with other important Microsoft Sentinel information. You can use this page to understand the general security situation before investigating incidents.

[![A screen capture of the Microsoft Sentinel Overview page.](https://learn.microsoft.com/en-us/training/wwl-sci/incident-management-sentinel/media/3-sentinel-overview.png)](https://learn.microsoft.com/en-us/training/wwl-sci/incident-management-sentinel/media/3-sentinel-overview.png#lightbox)

![[Pasted image 20261008160145.png]]

# Incident management

After you start using Microsoft Sentinel to generate incidents, you and the Contoso IT team can investigate the incidents. Microsoft Sentinel has advanced investigation and analysis tools you can use to gather information and determine remediation steps.

## Review incidents

To identify and resolve security issues, first investigate any incidents. The Microsoft Sentinel **Overview** page provides a list of the most recent incidents for quick reference. For more details and a complete overview of incidents, use the **Incidents** page, which displays all incidents in the current workspace and details about those incidents.

The **Incidents** page provides a complete list of incidents in Microsoft Sentinel. The page also provides basic incident information. Information includes severity, ID, title, alerts, product names, created time, last update time, owner, and status. You can sort by any incident column and filter the incident list by name, severity, status, product name, or owner.

[![Screenshot of a list of incidents in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/incident-management-sentinel/media/5-incidents-page.png)](https://learn.microsoft.com/en-us/training/wwl-sci/incident-management-sentinel/media/5-incidents-page.png#lightbox)

From this page, you can take various steps to investigate incidents.

Important

Microsoft Entra users who investigate incidents must be members of the Directory Reader role.

## Examine incident details

Select any incident on the **Incidents** page to display more information about the incident in the right pane. This pane provides a description of the incident and lists the related evidence, entities, and tactics. The pane also contains links to associated workbooks and the analytics rule that generated the incident. This information can help you clarify the nature, context, and course of action for the incident.

![Screenshot of the incident details pane.](https://learn.microsoft.com/en-us/training/wwl-sci/incident-management-sentinel/media/5-incident-details.png)

In the incident details pane, select **View full details** to open the **Incident** page and see more details about the incident. You can use these details to better understand the context of the incident. For example, in a brute force attack incident, you might go to the Log Analytics query for the alert to determine the number of attacks.

## Manage incident ownership, status, and severity

Each incident Microsoft Sentinel creates has attached metadata that you can view and manage. This information lets you:

- Assign and track incident ownership.
- Set and track the status of an incident from creation to resolution.
- Set and review severity.

![The screenshot displays the section of the Incidents page where you can assign ownership, status, and severity.](https://learn.microsoft.com/en-us/training/wwl-sci/incident-management-sentinel/media/5-incident-settings.png)

### Ownership

In a typical environment, each incident should be assigned an owner from the security team. The incident owner is responsible for overall incident management, including investigation and status updates. You can change ownership at any time to assign the incident to another security team member for further investigation or escalation.

### Status

Every new incident created in Microsoft Sentinel is assigned a status of **New**. As you review and respond to incidents, manually change the status to reflect the current state of the incident. For incidents under investigation, set the status to **Active**. When an incident is fully resolved, set the status to **Closed**.

When you set the status to **Closed**, you're prompted to choose one of the following resolutions:

- **True Positive - Suspicious activity**
- **Benign Positive - Suspicious but expected**
- **False Positive - Incorrect alert logic**
- **False Positive - Inaccurate data**
- **Undetermined**

### Severity

The rule or Microsoft security source that generated the incident initially sets the severity. In most cases, incident severity remains unchanged, but you might change the severity if you decide that the incident is more or less severe than initially classified. Severity options are **Informational**, **Low**, **Medium**, and **High**.

## Use the investigation graph

You can further investigate an incident by selecting **Investigate** on the **Incident** page. This action opens the investigation graph, a visual tool that helps to identify entities involved in the attack and the relationships between those entities. If the incident involves multiple alerts over time, you can also review the alert timeline and correlations between alerts.

[![The screenshot shows the investigation graph.](https://learn.microsoft.com/en-us/training/wwl-sci/incident-management-sentinel/media/5-investigation-graph.png)](https://learn.microsoft.com/en-us/training/wwl-sci/incident-management-sentinel/media/5-investigation-graph.png#lightbox)

### Review entity details

You can select each entity on the graph to observe more information about the entity. This information includes relationships to other entities, account usage, and data flow information. For each information area, you can go to the related events in Log Analytics and add the related alert data into the graph.

### Review incident details

You can select the incident item on the graph to observe incident metadata related to the incident's security and environment context.


![[Pasted image 20261008160917.png]]

# Exercise - Investigate an incident

Security operations analysts use Microsoft Sentinel to monitor and respond to security incidents in their organization. In these exercises we investigate security incidents using Microsoft Sentinel in Microsoft Azure, and in the Microsoft Defender portal Unified Security Operations Platform.

- [Azure portal](https://learn.microsoft.com/en-us/training/modules/incident-management-sentinel/6-exercise-investigate-incident?tabs=azure-portal#tabpanel_1_azure-portal)
- [Defender portal](https://learn.microsoft.com/en-us/training/modules/incident-management-sentinel/6-exercise-investigate-incident?tabs=azure-portal#tabpanel_1_defender-portal)

As a Contoso security operations analyst, you need to analyze the deletions of virtual machines (VMs) from the Contoso Azure subscription, and be alerted when a similar activity occurs in the future. You decide to implement an analytics rule to create an incident when someone deletes an existing VM. You can then investigate the incident to determine the details, and close the incident when you're finished.

In this exercise, you create a Microsoft Sentinel analytics rule to detect when a VM is deleted. You then delete the VM you created at the beginning of this module, and investigate and resolve the incident the rule created.

To complete this exercise, make sure you finished the setup exercise at the beginning of the module, and the Azure Activity connector now shows a status of **Connected**.

## Create an analytics rule from the wizard

Create an analytics rule that creates an incident when a VM is deleted in the Contoso Azure subscription.

1. In the Azure portal, search for and select **Microsoft Sentinel**, and then select the Microsoft Sentinel workspace you created.
2. On your Microsoft Sentinel page, select **Analytics** under **Configuration** in the left menu.
3. On the **Analytics** page, select **Create** > **Scheduled query rule**.

## General tab

1. On the **General** tab of the wizard, provide the following information.
    
    - **Name**: Enter _Deleted VMs_.
    - **Description**: Enter a description to help others understand what the rule does.
    - **Tactics and techniques**: Select **Initial Access**.
    - **Severity**: Select **Medium**.
    - **Status**: Select **Enabled**.
    
    ![Screenshot of the page for creating a new rule in the Analytics Rule wizard.](https://learn.microsoft.com/en-us/training/wwl-sci/incident-management-sentinel/media/6-analytics-rule-wizard-create-new-rule.png)
    
2. Select **Next: Set rule logic**.
    

## Set rule logic tab

1. On the **Set rule logic** tab, in the **Rule query** section, enter the following query:
    
    Kusto
    
    ```
    AzureActivity
    | where OperationNameValue == "MICROSOFT.COMPUTE/VIRTUALMACHINES/DELETE"
    | where ActivityStatusValue == 'Success'
    | extend AccountCustomEntity = Caller
    | extend IPCustomEntity = CallerIpAddress
    ```
    
2. Scroll down to view or set the following configuration options:
    
    - Expand the **Entity mapping** section to define the entities that return as part of the query rule, which you can use for in-depth analysis. For this exercise, use the default values.
    - In the **Query scheduling** section, configure how often the query should run, and how far back in history to observe. Set **Run query every** to **5 minutes**.
    - In the **Alert threshold** section, you can specify the number of positive results that can return for the rule before an alert is generated. Use the default value of **is greater than 0**.
    - In the **Event grouping** section, accept the default selection **Group all events into a single alert**.
    - In the **Suppression** section, for **Stop running the query after the alert is generated**, leave the default of **Off**.
    - In the **Results simulation** section, select **Test with current data**, and observe the results.
3. Select **Next: Incident settings**.
    

## Incident settings tab

1. On the **Incident settings** tab, ensure that **Create incidents from alerts triggered by this analytics rule** is set to **Enabled**.
2. In the **Alert grouping** section, select **Enabled** to group related alerts into incidents. Ensure that **Grouping alerts into a single incident if all the entities match (recommended)** is selected.
3. Ensure that **Reopen closed matching incidents** is **Disabled**.
4. Select **Next: Automated response**.

## Review and create

1. Select **Next: Review**.
2. On the **Review and create** tab, when validation is successful, select **Create**.

## Delete a VM

To test rule detection and incident creation, delete the VM you created during setup.

1. In the Azure portal, search for and select **Virtual machines**.
2. On the **Virtual machines** page, select the checkbox next to **simple-vm**, and then select **Delete** from the toolbar.
3. On the **Delete Resources** pane, enter _delete_ in the **Enter "delete" to confirm deletion** field, and then select **Delete**.
4. Select **Delete** again.

Give the operation several minutes to complete before you proceed to the next step.

## Investigate the incident

In this step, you investigate the incident Microsoft Sentinel created when you deleted the VM. It might take up to 30 minutes for the incident to appear in Microsoft Sentinel.

1. In the Azure portal, search for and select **Microsoft Sentinel**, and then select your Microsoft Sentinel workspace.
2. On your Microsoft Sentinel page, select **Incidents** under **Threat management** in the left navigation.
3. On the **Incidents** page, select the incident with the title **Deleted VMs**.
4. In the **Deleted VMs** details pane on the right, observe the details of the incident, including **Owner**, **Status**, and **Severity**. Apply the following updates:
    - Select **Owner** > **Assign to me** > **Apply**.
    - Select **Status** > **Active** > **Apply**.
5. Select **View full details**.
6. In the left pane of the **Incident** page, observe the totals for **Events**, **Alerts**, and **Bookmarks** in the **Evidence** section.
7. At the bottom of the pane, select **Investigate**.
8. On the **Investigation** page, select the following items in the investigation graph:
    - The **Deleted VMs** incident item in the center of the page showing the details of the incident.
    - The user entity representing your user account, indicating that you deleted the VM.
9. At the top of the **Investigate** page, select **Status** > **Closed**.
10. In the **Select classification** drop-down menu, select **Benign Positive - Suspicious but expected**.
11. In the **Comment** field, enter _Testing incident creation and resolution steps_, and then select **Apply**.
12. Select the close icons to close the **Investigate** and **Incident** pages.
13. On the **Incidents** page, observe that **Open incidents** and **Active incidents** now have values of **0**.

You successfully created a Microsoft Sentinel analytics rule, deleted a VM to create an incident, and investigated and closed the incident the rule created.

## Clean up resources

To avoid incurring costs, delete the Azure resources that you created in this module when you're finished with them. To delete the resources, complete the following steps:

1. In the Azure portal, search for **Resource groups**.
2. On the **Resource groups** page, select **azure-sentinel-rg**.
3. On the **azure-sentinel-rg** page, select **Delete resource group** from the top menu bar.
4. On the **Delete a resource group** page, under **Enter resource group name to confirm deletion**, enter _azure-sentinel-rg_.
5. Select **Delete**, and then select **Delete** again.

n this exercise you walk through the process of reviewing, modifying, investigating, and responding to a security incident within the Unified Security Operations Platform.

Note

When a lab instruction calls for opening a link to the simulated environment, it's recommended that you open the link in a new browser window so that you can simultaneously view the instructions and the exercise environment. To do so, select the right mouse key and select the option.

1. Open the simulated environment by selecting this link: **[Microsoft Defender portal](https://app.highlights.guide/start/1e5185e8-b314-48fe-b848-965232192baa?token=bba5e99b-3887-4a6c-b0d8-3099d15a4c23)**.
    
    Note
    
    The environment for this exercise is a simulation generated from the product. As a limited simulation, links on a page may not be enabled and text-based inputs that fall outside of the specified script may not be supported. A pop-up message displays stating, "This feature isn't available within the simulation." When this occurs, select OK and continue the exercise steps.
    
    ![Screenshot of pop-up screen indicating that this feature isn't available within the simulation.](https://learn.microsoft.com/en-us/training/wwl-sci/incident-management-sentinel/media/simulation-pop-up-error.png)
    

## Task: Review the Incident Queue and Apply Filters

1. In the Microsoft Defender portal navigation menu:
    
    1. Expand **Investigation & response**.
    2. Expand **Incidents & alerts**.
    3. Select **Incidents**.
2. Within the Incident Queue, filter the incidents for high severity and a status of active.
    
3. Select "add filter."
    
4. Set the filter to categories and set the value to **Ransomware**.
    
5. Select the "User account compromise identified from a known attack pattern" incident and view the summary on the right hand menu
    

## Task: Generate an Incident Summary with Copilot for Security

1. Continuing with the same incident from the previous task, select the name to enter the incident page.
2. After entering the incident, allow Copilot to review the incident and generate an incident summary.
3. Review the summary details to understand what took place in the incident.

## Task: Review an Alert

1. Within the alert timeline, select the "Malicious URL In Proxy logs."
2. Review the details under "what happened."
3. Check which analytic rule generated this alert.
4. Within the incident graph, select the IP address "10.50.0.16."
5. Select the node and choose "view details" to see related details to the IP.
6. In the alert timeline, select "Connection to a suspicious domain related to credential phishing."
7. Review the process tree to review the sequence of processes being performed on the workstation up until the incident.

## Task: Review the Incident Assets (Entities)

1. Within the incident, select the "assets" tab near the top.
2. Select "users."
3. Select the user’s name.
4. Review the details in the side menu.
5. Select "devices."
6. Select the first device.
7. Select "open device page."
8. Review the details shown on the page.

## Task: Review the Evidence and Response

1. Navigate back to the incident page.
2. Select the "Evidence and Response" tab near the top.
3. Select a few items of evidence and review the details in the side menu.

## Task: Review the Recommended Actions

1. Select the "Recommended actions" tab.
2. Review the list of listed actions.
3. Select through the list to see the details, implementation status, impact, implementation steps, and history.

## Task: Close an Incident

1. Within the incident, select "Manage Incident."
2. Set the status to resolved.
3. Within the classification, select a categorization.
4. Select save.


# Summary

In this module, you learned about using Microsoft Sentinel to detect and investigate security threats in your Microsoft Azure environment. You also practiced using rules and alerts to investigate and identify anomalies in Contoso's Azure Activity log, and how to use Kusto Query Language (KQL) to summarize and visualize data, which is essential for creating custom analytics rules and workbooks in Microsoft Sentinel. And, you learned how to investigate consolidated incidents in the Microsoft Defender portal.

You can now lead the IT team in helping Contoso protect its security environment by managing incidents with Microsoft Sentinel. Ongoing activities might include creating custom analytics rules, using playbooks for automated responses, and using workbooks to provide dashboards and visualizations.

# Identify threats with Behavioral Analytics

# Introduction

As Microsoft Sentinel collects logs and alerts from all of its connected data sources, it analyzes them. It builds baseline behavioral profiles of your organization’s entities (users, hosts, IP addresses, applications, etc.).

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. The threat hunting team has raised concerns about a specific user account based on discovered threat indicators and needs to see a profile containing historical and related entity data quickly. You have the threat hunting team member navigate to the Entity behavior page to perform further analysis on the account.

By the end of this module, you'll be able to use entity behavior analytics in Microsoft Sentinel to identify threats inside your organization.

After completing this module, you'll be able to:

- Explain Entity Behavior Analytics in Microsoft Sentinel
- Explore entities in Microsoft Sentinel
- Use entity behavior in Analytical rules

## Prerequisites

Knowledge of security incident management in Microsoft Sentinel

# Understand behavioral analytics

Identifying threats inside your organization and their potential impact - whether a compromised entity or a malicious insider - is a time-consuming and labor-intensive process. When you're sifting through alerts, connecting the dots, and actively hunting, it adds up to massive amounts of time and effort expended with minimal returns. And, the possibility of sophisticated threats evading discovery. Elusive threats like zero-day, targeted, and advanced persistent threats can be the most dangerous to your organization, making their detection all the more critical.

The Entity Behavior capability in Microsoft Sentinel eliminates the drudgery from your analysts’ workloads, and the uncertainty from their efforts. The Entity Behavior capability delivers high-fidelity and actionable intelligence, so they can focus on investigation and remediation.

As Microsoft Sentinel collects logs and alerts from all the connected data sources, it analyzes and builds baseline behavioral profiles of your organization’s entities (users, hosts, IP addresses, applications, etc.). The analysis is across the time and peer group horizon. Microsoft Sentinel uses various techniques and machine learning capabilities, and can then identify anomalous activity and help you determine if an asset is compromised. Not only that, but it can also figure out the relative sensitivity of particular assets, identify peer groups of assets, and evaluate the potential impact of any given compromised asset (its "blast radius"). Armed with this information, you can effectively prioritize your investigation and incident handling.

### Architecture overview

![Diagram of the UEBA architecture overview.](https://learn.microsoft.com/en-us/training/wwl-sci/use-entity-behavior-analytics-azure-sentinel/media/entity-behavior-1.png)

### Security-driven analytics

Microsoft adopted Gartner’s paradigm for UEBA solutions, Microsoft Sentinel provides an "outside-in" approach, based on three frames of reference:

**Use cases:** Microsoft Sentinel prioritizes for relevant attack vectors and scenarios based on security research aligned with the MITRE ATT&CK framework of tactics, techniques, and subtechniques. The prioritization identifies various entities as victims, perpetrators, or pivot points in the kill chain. Microsoft Sentinel focuses specifically on the most valuable logs each data source can provide.

**Data Sources:** While first and foremost supporting Azure data sources, Microsoft Sentinel thoughtfully selects third-party data sources to provide data that matches our threat scenarios.

**Analytics:** Microsoft Sentinel uses machine learning (ML) algorithms, and identifies anomalous activities that presents evidence clearly and concisely in the form of contextual enrichments. See the examples below.

![Diagram showing security-driven analytics enrichment examples in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/use-entity-behavior-analytics-azure-sentinel/media/entity-behavior-2.png)

Microsoft Sentinel presents artifacts that help your security analysts get a clear understanding of anomalous activities in context, and in comparison with the user's baseline profile. Actions performed by a user (or a host, or an address) are evaluated contextually, where a "true" outcome indicates an identified anomaly:

- Across geographical locations, devices, and environments.
    
- Across time and frequency horizons (compared to user's own history).
    
- As compared to peers' behavior.
    
- As compared to organization's behavior.
    

![Diagram showing the UEBA context rings used to evaluate user activity.](https://learn.microsoft.com/en-us/training/wwl-sci/use-entity-behavior-analytics-azure-sentinel/media/entity-behavior-3.png)

### Scoring

Each activity is scored with "Investigation Priority Score". The score determines the probability of a specific user performing a specific activity based on behavioral learning of the user and their peers. Activities identified as the most abnormal receive the highest scores (on a scale of 0-10).

# Explore entities

When alerts are sent to Microsoft Sentinel, they include data elements that Microsoft Sentinel identifies and classifies as entities, such as user accounts, hosts, IP addresses, and others. On occasion, this identification can be a challenge, if the alert doesn't contain sufficient information about the entity.

For example, user accounts can be identified in more than one way: using a Microsoft Entra account’s numeric identifier (GUID), or its User Principal Name (UPN) value, or alternatively, using a combination of its username and its NT domain name. Different data sources can identify the same user in different ways. Therefore, whenever possible, Microsoft Sentinel merges those identifiers into a single entity, so that it can be properly identified.

It can happen, though, that one of your resource providers creates an alert in which an entity isn't sufficiently identified - for example, a user name without the domain name context. In such a case, the user entity can't be merged with other instances of the same user account, which would be identified as a separate entity, and those two entities would remain separate instead of unified.

In order to minimize the risk of this happening, you should verify that all of your alert providers properly identify the entities in the alerts they produce. Additionally, synchronizing user account entities with Microsoft Entra ID may create a unifying directory, which is able to merge user account entities.

The following types of entities are currently identified in Microsoft Sentinel:

- User account (Account)
    
- Host
    
- IP address (IP)
    
- Malware
    
- File
    
- Process
    
- Cloud application (CloudApplication)
    
- Domain name (DNS)
    
- Azure resource
    
- File (FileHash)
    
- Registry key
    
- Registry value
    
- Security group
    
- URL
    
- IoT device
    
- Mailbox
    
- Mail cluster
    
- Mail message
    
- Submission mail
    

### Entity pages

When you encounter any entity (currently limited to users and hosts) in a search, an alert, or an investigation, you can select the entity and be taken to an **entity page**, a datasheet full of useful information about that entity. The types of information you find on this page include basic facts about the entity, a timeline of notable events related to this entity and insights about the entity's behavior.

Entity pages consist of three parts:

- The left-side panel contains the entity's identifying information, collected from data sources like Microsoft Entra ID, Azure Monitor, Microsoft Defender for Cloud, and Microsoft Defender XDR.
    
- The center panel shows a graphical and textual timeline of notable events related to the entity, such as alerts, bookmarks, and activities. Activities are aggregations of notable events from Log Analytics. The queries that detect those activities are developed by Microsoft security research teams.
    
- The right-side panel presents behavioral insights on the entity. These insights help to quickly identify anomalies and security threats. The insights are developed by Microsoft security research teams, and are based on anomaly detection models.
    

### The timeline

![Screenshot of an entity behavior timeline in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/use-entity-behavior-analytics-azure-sentinel/media/entity-behavior-4.png)

The timeline is a major part of the entity page's contribution to behavior analytics in Microsoft Sentinel. It presents a story about entity-related events, helping you understand the entity's activity within a specific time frame.

You can choose the **time range** from among several preset options (such as _last 24 hours_), or set it to any custom-defined time frame. Additionally, you can set filters that limit the information in the timeline to specific types of events or alerts.

The following types of items are included in the timeline:

Alerts - any alerts in which the entity is defined as a **mapped entity**. If your organization has created [custom alerts using analytics rules](https://learn.microsoft.com/en-us/azure/sentinel/tutorial-detect-threats-custom), you should make sure that the rules' entity mapping is done properly.

Bookmarks - any bookmarks that include the specific entity shown on the page.

Activities - aggregation of notable events relating to the entity.

### Entity Insights

Entity insights are queries defined by Microsoft security researchers to help your analysts investigate more efficiently and effectively. The insights are presented as part of the entity page, and provide valuable security information on hosts and users, in the form of tabular data and charts. Having the information here means you don't have to detour to Log Analytics. The insights include data regarding sign-ins, Group Additions, Anomalous Events and more, and include advanced ML algorithms to detect anomalous behavior. The insights are based on the following data types:

- Syslog
    
- SecurityEvent
    
- Audit Logs
    
- Sign-in Logs
    
- Office Activity
    
- BehaviorAnalytics (UEBA)

# Display entity behavior information

The Entity behavior page allows you to search for entities or select from the list of already displayed entities. Once selected the Entity page is displayed with information and timeline of alerts and activities

The Incident Investigation Graph includes an option for **Insights**. Insights display information from the Entity behavior data.

### How to use entity pages

Entity pages are designed to be part of multiple usage scenarios, and can be accessed from incident management, the investigation graph, bookmarks, or directly from the entity search page under **Entity behavior analytics** in the Microsoft Sentinel main menu.

![Diagram of connections to the Entity Page.](https://learn.microsoft.com/en-us/training/wwl-sci/use-entity-behavior-analytics-azure-sentinel/media/entity-behavior-5.png)

# Use Anomaly detection analytical rule templates


With attackers and defenders constantly fighting for advantage in the cybersecurity arms race, attackers are always finding ways to evade detection. Inevitably, though, attacks will still result in unusual behavior in the systems being attacked. Microsoft Sentinel's customizable, machine learning-based anomalies can identify this behavior with analytics rule templates that can be put to work right out of the box. While anomalies don't necessarily indicate malicious or even suspicious behavior by themselves, they can be used to improve detections, investigations, and threat hunting:

- **Additional signals to improve detection:** Security analysts can use anomalies to detect new threats and make existing detections more effective. A single anomaly isn't a strong signal of malicious behavior, but when combined with several anomalies that occur at different points on the kill chain, their cumulative effect is much stronger. Security analysts can enhance existing detections as well by making the unusual behavior identified by anomalies a condition for alerts to be fired.
    
- **Evidence during investigations:** Security analysts also can use anomalies during investigations to help confirm a breach, find new paths for investigating it, and assess its potential impact. These efficiencies reduce the time security analysts spend on investigations.
    
- **The start of proactive threat hunts:** Threat hunters can use anomalies as context to help determine whether their queries have uncovered suspicious behavior. When the behavior is suspicious, the anomalies also point toward potential paths for further hunting. These clues provided by anomalies reduce both the time to detect a threat and its chance to cause harm.
    

Anomalies can be powerful tools, but they're notoriously noisy. They typically require much tedious tuning for specific environments or complex post-processing. Microsoft Sentinel customizable anomaly templates are tuned by our data science team to provide out-of-the box value, but should you need to tune them further, the process is simple and requires no knowledge of machine learning. The thresholds and parameters for many of the anomalies can be configured and fine-tuned through the already familiar analytics rule user interface. The performance of the original threshold and parameters can be compared to the new ones within the interface and further tuned as necessary during a testing, or flighting, phase. Once the anomaly meets the performance objectives, the anomaly with the new threshold or parameters can be promoted to production with the click of a button. Microsoft Sentinel customizable anomalies enable you to get the benefit of anomalies without the hard work.

## Work with anomaly detection analytics rules

Microsoft Sentinel’s customizable anomalies feature provides built-in anomaly templates for immediate value out-of-the-box. These anomaly templates were developed to be robust by using thousands of data sources and millions of events, but this feature also enables you to change thresholds and parameters for the anomalies easily within the user interface. Anomaly rules must be activated before they'll generate anomalies, which you can find in the Anomalies table in the Logs section.

1. From the Microsoft Sentinel navigation menu, select Analytics.
    
2. On the Analytics page, select the Rule templates tab.
    
3. Filter the list for Anomaly templates:
    
    - Select the Rule type filter, then the drop-down list that appears below.
        
    - Unmark Select all, then mark Anomaly.
        
    - If necessary, select the top of the drop-down list to retract it, then select OK.
        

## Activate anomaly rules

When you select one of the rule templates, you'll see the following information in the details pane, along with a Create rule button:

- **Description** explains how the anomaly works and the data it requires.
    
- **Data sources** indicates the type of logs that need to be ingested in order to be analyzed.
    
- **Tactics and techniques** are the MITRE ATT&CK framework tactics and techniques covered by the anomaly.
    
- **Parameters** are the configurable attributes for the anomaly.
    
- **Threshold** is a configurable value that indicates the degree to which an event must be unusual before an anomaly is created.
    
- **Rule frequency** is the time between log processing jobs that find the anomalies.
    
- **Anomaly version** shows the version of the template that is used by a rule. If you want to change the version used by a rule that is already active, you must recreate the rule.
    
- **Template last updated** is the date the anomaly version was changed.
    

Complete the following steps to activate a rule:

- Choose a rule template that isn't already labeled IN USE. Select the Create rule button to open the rule creation wizard.
    
    The wizard for each rule template will be slightly different, but it has three steps or tabs: General, Configuration, Review and create.
    
    You can't change any of the values in the wizard; you first have to create and activate the rule.
    
- Cycle through the tabs, wait for the "Validation passed" message on the Review and create tab, and select the Create button.
    
    You can only create one active rule from each template. Once you complete the wizard, an active anomaly rule is created in the Active rules tab, and the template (in the Rule templates tab) will be marked IN USE.
    

Once the anomaly rule is activated, detected anomalies will be stored in the Anomalies table in the Logs section of your Microsoft Sentinel workspace.

Each anomaly rule has a training period, and anomalies won't appear in the table until after that training period. You can find the training period in the description of each anomaly rule.

### Assess the quality of anomalies

You can see how well an anomaly rule is performing by reviewing a sample of the anomalies created by a rule over the last 24-hour period.

- From the Microsoft Sentinel navigation menu, select Analytics.
    
- On the Analytics page, check that the Active rules tab is selected.
    
- Filter the list for Anomaly rules (as above).
    
- Select the rule you want to assess, and copy its name from the top of the details pane to the right.
    
- From the Microsoft Sentinel navigation menu, select Logs.
    
- If a Queries gallery pops up over the top, close it.
    
- Select the Tables tab on the left pane of the Logs page.
    
- Set the Time range filter to Last 24 hours.
    
- Copy the Kusto query below and paste it in the query window (where it says "Type your query here or..."):
    

KQL

```
Anomalies 
| where AnomalyTemplateName contains "________________________________"
```

```
Paste the rule name you copied above in place of the underscores between the quotation marks.
```

- Select Run.

When you have some results, you can start assessing the quality of the anomalies. If you don’t have results, try increasing the time range.

Expand the results for each anomaly and then expand the AnomalyReasons field. This will tell you why the anomaly fired.

The "reasonableness" or "usefulness" of an anomaly may depend on the conditions of your environment, but a common reason for an anomaly rule to produce too many anomalies is that the threshold is too low.

### Tune anomaly rules

While anomaly rules are engineered for maximum effectiveness out of the box, every situation is unique, and sometimes anomaly rules need to be tuned.

Since you can't edit an original active rule, you must first duplicate an active anomaly rule, and then customize the copy.

The original anomaly rule will keep running until you either disable or delete it.

This is by design, to give you the opportunity to compare the results generated by the original configuration and the new one. Duplicate rules are disabled by default. You can only make one customized copy of any given anomaly rule. Attempts to make a second copy will fail.

- To change the configuration of an anomaly rule, select the anomaly rule in the Active rules tab.
    
- Right-click anywhere on the row of the rule, or left-click the ellipsis (...) at the end of the row, then select Duplicate.
    
- The new copy of the rule will have the suffix " - Customized" in the rule name. To actually customize this rule, select this rule and select Edit.
    
- The rule opens in the Analytics rule wizard. Here you can change the parameters of the rule and its threshold. The parameters that can be changed vary with each anomaly type and algorithm.
    
- You can preview the results of your changes in the Results preview pane. Select an Anomaly ID in the results preview to see why the ML model identifies that anomaly.
    
- Enable the customized rule to generate results. Some of your changes may require the rule to run again, so you must wait for it to finish and come back to check the results on the logs page. The customized anomaly rule runs in Flighting (testing) mode by default. The original rule continues to run in Production mode by default.
    
- To compare the results, go back to the Anomalies table in Logs to assess the new rule as before, only look for rows with the original rule name and the duplicate rule name with " - Customized" appended to it in the AnomalyTemplateName column.
    
    If you're satisfied with the results for the customized rule, you can go back to the Active rules tab, select on the customized rule, select the Edit button and on the General tab switch it from Flighting to Production. The original rule will automatically change to Flighting since you can't have two versions of the same rule in production at the same time.

![[Pasted image 20261008165855.png]]

# Summary and resources

You learned how to use entity behavior analytics in Microsoft Sentinel to identify threats inside your organization.

You should now be able to:

- Explain Entity Behavior Analytics in Microsoft Sentinel
- Explore entities in Microsoft Sentinel
- Use entity behavior in Analytical rules


# Data normalization in Microsoft Sentinel

# Introduction
Data normalization in Microsoft Sentinel allows for the standardization of data across multiple data sources.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You have multiple connectors that write unstructured firewall data to the CommonSecurityLog table. You need to empower security analysts to easily write analytical rule queries against the firewall data. You need to create an ASIM parser to provide one table for the analysts to query.

By the end of this module, you'll be able to use ASIM parsers to identify threats inside your organization.

After completing this module, you'll be able to:

- Use ASIM Parsers
- Create ASIM Parser
- Create parameterized KQL functions

# Understand data normalization
Microsoft Sentinel ingests data from many sources. Working with various data types and tables together requires you to understand each of them, and write and use unique sets of data for analytics rules, workbooks, and hunting queries for each type or schema.

Sometimes, you'll need separate rules, workbooks, and queries, even when data types share common elements, such as firewall devices. Correlating between different types of data during an investigation and hunting can also be challenging.

The Advanced Security Information Model (ASIM) is a layer that is located between these diverse sources and the user. ASIM follows the robustness principle: "Be strict in what you send, be flexible in what you accept". When the robustness principle is used as a design pattern, ASIM transforms Microsoft Sentinel's inconsistent, and hard to use source telemetry to user friendly data.

## Common ASIM usage

ASIM provides a seamless experience for handling various sources in uniform, normalized views, by providing the following functionality:

- **Cross source detection**. Normalized analytics rules work across sources, on-premises and cloud, and detect attacks such as brute force or impossible travel across systems, including Okta, AWS, and Azure.
    
- **Source agnostic content**. The coverage of both built-in and custom content using ASIM automatically expands to any source that supports ASIM, even if the source was added after the content was created. For example, process event analytics support any source that a customer may use to bring in the data, such as Microsoft Defender for Endpoint, Windows Events, and Sysmon.
    
- **Support for your custom sources**, in built-in analytics
    
- **Ease of use**. After an analyst learns ASIM, writing queries is simpler as the field names are always the same.
    

## ASIM and the Open Source Security Events Metadata

ASIM aligns with the Open Source Security Events Metadata (OSSEM) common information model, allowing for predictable entities correlation across normalized tables.

OSSEM is a community-led project that focuses primarily on the documentation and standardization of security event logs from diverse data sources and operating systems. The project also provides a Common Information Model (CIM) that can be used for data engineers during data normalization procedures to allow security analysts to query and analyze data across diverse data sources.

## ASIM components

The following image shows how non-normalized data can be translated into normalized content and used in Microsoft Sentinel. For example, you can start with a custom, product-specific, non-normalized table, and use a parser and a normalization schema to convert that table to normalized data. Use your normalized data in both Microsoft and custom analytics, rules, workbooks, queries, and more.

![Diagram of the A S I M Architecture Components.](https://learn.microsoft.com/en-us/training/wwl-sci/data-normalization-microsoft-sentinel/media/asim-architecture.png)

ASIM includes the following components:

|Component|Description|
|---|---|
|Normalized schemas|Cover standard sets of predictable event types that you can use when building unified capabilities. Each schema defines the fields that represent an event, a normalized column naming convention, and a standard format for the field values.|
|Parsers|Map existing data to the normalized schemas using KQL functions. Many ASIM parsers are available out of the box with Microsoft Sentinel. More parsers, and versions of the built-in parsers that can be modified can be deployed from the Microsoft Sentinel GitHub repository.|
|Content for each normalized schema|Includes analytics rules, workbooks, hunting queries, and more. Content for each normalized schema works on any normalized data without the need to create source-specific content.|
|||

## ASIM terminology

ASIM uses the following terms:

|Term|Description|
|---|---|
|Reporting device|The system that sends the records to Microsoft Sentinel. This system may not be the subject system for the record that's being sent.|
|Record|A unit of data sent from the reporting device. A record is often referred to as log, event, or alert, but can also be other types of data.|
|Content, or Content Item|The different, customizable, or user-created artifacts than can be used with Microsoft Sentinel. Those artifacts include, for example, Analytics rules, Hunting queries and workbooks. A content item is one such artifact.|

## View ASIM Parsers

To view ASIM functions in your Microsoft Sentinel environment.

- Navigate to your Microsoft Sentinel workspace in the Azure portal
- Select Logs from the left navigation
- Expand the schema and filter pane on the left side (if needed use the ellipsis to reveal all the tools)
- Select Functions
- Expand Microsoft Sentinel

You'll see functions starting with **_ASim_** and **_Im_**.


# Use ASIM Parsers
In Microsoft Sentinel, parsing and normalizing happen at query time. Parsers are built as KQL user-defined functions that transform data in existing tables, such as CommonSecurityLog, custom logs tables, or Syslog, into the normalized schema.

Users use Advanced Security Information Model (ASIM) parsers instead of table names in their queries to view data in a normalized format, and to include all data relevant to the schema in your query.

## Built-in ASIM parsers and workspace-deployed parsers

Many ASIM parsers are built in and available out-of-the-box in every Microsoft Sentinel workspace. ASIM also supports deploying parsers to specific workspaces from GitHub, using an ARM template or manually. Both out-of-the-box and workspace-deployed parsers are functionally equivalent, but have slightly different naming conventions, allowing both parser sets to coexist in the same Microsoft Sentinel workspace.

Each method has advantages over the other:

|Compare|Built-in|Workspace-deployed|
|---|---|---|
|Advantages|Exist in every Microsoft Sentinel instance. Usable with other built-in content.|New parsers are often delivered first as workspace-deployed parsers.|
|Disadvantages|Can't be directly modified by users. Fewer parsers available.|Not used by built-in content.|
|When to use|Use in most cases that you need ASIM parsers.|Use when deploying new parsers, or for parsers not yet available out-of-the-box.|

It's recommended to use built-in parsers for schemas for which built-in parsers are available.

## Parser hierarchy

ASIM includes two levels of parsers: unifying parser and source-specific parsers. The user usually uses the unifying parser for the relevant schema, ensuring all data relevant to the schema is queried. The unifying parser in turn calls source-specific parsers to perform the actual parsing and normalization, which is specific for each source.

The unifying parser name is **_Im_Schema** for built-in parsers, and **imSchema** for workspace deployed parsers. Where **Schema** stands for the specific schema it serves. Source-specific parsers can also be used independently. For example, in an Infoblox-specific workbook, use the **vimDnsInfobloxNIOS** source-specific parser.

## Unifying parsers

When using ASIM in your queries, use unifying parsers to combine all sources, normalized to the same schema, and query them using normalized fields.

For example, the following query uses the built-in unifying DNS parser to query DNS events using the ResponseCodeName, SrcIpAddr, and TimeGenerated normalized fields:

KQL

```
_Im_Dns(starttime=ago(1d), responsecodename='NXDOMAIN')
| summarize count() by SrcIpAddr, bin(TimeGenerated,15m)
```

The example uses filtering parameters, which improve ASIM performance. The same example without filtering parameters would look like this:

KQL

```
_Im_Dns
| where TimeGenerated > ago(1d)
| where ResponseCodeName =~ "NXDOMAIN"
| summarize count() by SrcIpAddr, bin(TimeGenerated,15m)
```

The following table lists key unifying parsers. For the complete current list, see [ASIM parsers overview](https://learn.microsoft.com/en-us/azure/sentinel/normalization-parsers-overview).

|Schema|Built-in unifying parser|
|---|---|
|Authentication|`_Im_Authentication`|
|Audit Event|`_Im_AuditEvent`|
|DHCP Event|`_Im_Dhcp`|
|DNS|`_Im_Dns`|
|File Event|`_Im_FileEvent`|
|Network Session|`_Im_NetworkSession`|
|Process Event|`_Im_ProcessEvent`|
|Registry Event|`_Im_RegistryEvent`|
|User Management|`_Im_UserManagement`|
|Web Session|`_Im_WebSession`|

## Optimizing parsing using parameters

Using parsers may impact your query performance, primarily from filtering the results after parsing. For this reason, many parsers have optional filtering parameters, which enable you to filter before parsing and enhance query performance. With query optimization and pre-filtering efforts, ASIM parsers often provide better performance when compared to not using normalization at all.

When invoking the parser, always use available filtering parameters by adding one or more named parameters to ensure optimal performance of the ASIM parsers.

Each schema has a standard set of filtering parameters documented in the relevant schema documentation. Filtering parameters are entirely optional. The following schemas support filtering parameters:

- Authentication
- DNS
- Network Session
- Web Session

Every schema that supports filtering parameters supports at least the starttime and enttime parameters and using them is often critical for optimizing performance.

# Understand parameterized KQL functions
When calling KQL functions, you can provide a set of parameters. This is an important concept for building ASIM parsers as it allows you to filter the function results with dynamic values before returning results.

First, navigate to Logs in the Microsoft Sentinel workspace.

The following sample function returns all events in the Azure Activity log since a particular date and that match a particular category.

Start with the following query using hardcoded values. This verifies that the query works as expected.

KQL

```
AzureActivity
| where CategoryValue == "Administrative"
| where TimeGenerated > todatetime("2021/04/05 5:40:01.032 PM")
```

Next, replace the hardcoded values with parameter names and then save the function by selecting Save and then Save as function.

KQL

```
AzureActivity
| where CategoryValue == CategoryParam
| where TimeGenerated > DateParam
```

Enter Function name as AzureActivityByCategory Then create two parameters:

|Type|Name|Default value|
|---|---|---|
|string|CategoryParam|"Administrative"|
|datetime|DateParam||

Your screen should look like the image below:

[![Screenshot of KQL function properties.](https://learn.microsoft.com/en-us/training/wwl-sci/data-normalization-microsoft-sentinel/media/example-function-properties.png)](https://learn.microsoft.com/en-us/training/wwl-sci/data-normalization-microsoft-sentinel/media/example-function-properties.png#lightbox)

Create a new query. Then enter:

KQL

```
AzureActivityByCategory("Administrative", todatetime("2021/04/05 5:40:01.032 PM")) 
```

[![Screenshot of a KQL query calling a parameterized function.](https://learn.microsoft.com/en-us/training/wwl-sci/data-normalization-microsoft-sentinel/media/example-use-function.png)](https://learn.microsoft.com/en-us/training/wwl-sci/data-normalization-microsoft-sentinel/media/example-use-function.png#lightbox)

# Create an ASIM Parser

Advanced Security Information Model (ASIM) users use unifying parsers instead of table names in their queries, to view data in a normalized format and to include all data relevant to the schema in the query. Unifying parsers, in turn, use source-specific parsers to handle the specific details of each source.

Microsoft Sentinel provides built-in, source-specific parsers for many data sources. You may want to modify, or develop, these source-specific parsers in the following situations:

When your device provides events that fit an ASIM schema, but a source-specific parser for your device and the relevant schema isn't available in Microsoft Sentinel.

When ASIM source-specific parsers are available for your device, but your device sends events in a method or a format different than expected by the ASIM parsers. For example:

Your source device may be configured to send events in a non-standard way.

Your device may have a different version than the one supported by the ASIM parser.

The events might be collected, modified, and forwarded by an intermediary system.

## Custom parser development process

The following workflow describes the high level steps in developing a custom ASIM, source-specific parser:

1. Collect sample logs.
    
2. Identify the schemas or schemas that the events sent from the source represent.
    
3. Map the source event fields to the identified schema or schemas.
    
4. Develop one or more ASIM parsers for your source. You'll need to develop a filtering parser and a parameter-less parser for each schema relevant to the source.
    
5. Test your parser.
    
6. Deploy the parsers into your Microsoft Sentinel workspaces.
    
7. Update the relevant ASIM unifying parser to reference the new custom parser.
    
8. You might also want to contribute your parsers to the primary ASIM distribution. Contributed parsers may also be made available in all workspaces as built-in parsers.
    

### Collect sample logs

To build effective ASIM parsers, you need a representative set of logs, which in most case will require setting up the source system and connecting it to Microsoft Sentinel. If you don't have the source device available, cloud pay-as-you-go services let you deploy many devices for development and testing.

In addition, finding the vendor documentation and samples for the logs can help accelerate development and reduce mistakes by ensuring broad log format coverage.

A representative set of logs should include:

- Events with different event results.
- Events with different response actions.
- Different formats for username, hostname and IDs, and other fields that require value normalization.

### Mapping

Before you develop a parser, map the information available in the source event, or events to the schema you identified:

- Map all mandatory fields and preferably also recommended fields.
- Try to map any information available from the source to normalized fields. If not available as part of the selected schema, consider mapping to fields available in other schemas.
- Map values for fields at the source to the normalized values allowed by ASIM. The original value is stored in a separate field, such as EventOriginalResultDetails.

### Developing parsers

Develop both a filtering and a parameter-less parser for each relevant schema.

A custom parser is a KQL query developed in the Microsoft Sentinel Logs page. The parser query has three parts:

Filter > Parse > Prepare fields

### Filtering the relevant records

In many cases, a table in Microsoft Sentinel includes multiple types of events. For example:

- The Syslog table has data from multiple sources.
- Custom tables may include information from a single source that provides more than one event type and can fit various schemas.

Therefore, a parser should first filter only the records relevant to the target schema.

Filtering in KQL is done using the **where** operator. For example, **Sysmon event 1** reports process creation, and is therefore normalized to the **ProcessEvent** schema. The **Sysmon event 1** event is part of the **Event** table, so you would use the following filter:

KQL

```
Event | where Source == "Microsoft-Windows-Sysmon" and EventID == 1
```

Important

A parser should not filter by time. The query which uses the parser will apply a time range.

### Filtering by source type using a Watchlist

In some cases, the event itself doesn't contain information that would allow filtering for specific source types.

For example, Infoblox DNS events are sent as Syslog messages, and are hard to distinguish from Syslog messages sent from other sources. In such cases, the parser relies on a list of sources that defines the relevant events. This list is maintained in the ASimSourceType watchlist.

To use the ASimSourceType watchlist in your parsers:

- Include the following line at the beginning of your parser:

KQL

```
let Sources_by_SourceType=(sourcetype:string){_GetWatchlist('ASimSourceType') | where SearchKey == tostring(sourcetype) | extend Source=column_ifexists('Source','') | where isnotempty(Source)| distinct Source };
```

- Add a filter that uses the watchlist in the parser filtering section. For example, the Infoblox DNS parser includes the following in the filtering section:

KQL

```
| where Computer in (Sources_by_SourceType('InfobloxNIOS'))
```

To use this sample in your parser:

- Replace Computer with the name of the field that includes the source information for your source. You can keep this as Computer for any parsers based on Syslog.
    
- Replace the InfobloxNIOS token with a value of your choice for your parser. Inform parser users that they must update the ASimSourceType watchlist using your selected value, and the list of sources that send events of this type.
    

### Filtering based on parser parameters

When developing filtering parsers, make sure that your parser accepts the filtering parameters for the relevant schema, as documented in the reference article for that schema. Using an existing parser as a starting point ensures that your parser includes the correct function signature. In most cases, the actual filtering code is also similar for filtering parsers for the same schema.

When filtering, make sure that you:

- **Filter before parsing using physical fields**. If the filtered results aren't accurate enough, repeat the test after parsing to fine-tune your results. For more information, see filtering optimization.
- **Do not filter if the parameter is not defined and still has the default value.**

The following examples show how to implement filtering for a string parameter, where the default value is usually '*', and for a list parameter, where the default value is usually an empty list.

KQL

```
srcipaddr=='*' or ClientIP==srcipaddr
array_length(domain_has_any) == 0 or Name has_any (domain_has_any)
```

### Filtering optimization

To ensure the performance of the parser, note the following filtering recommendations:

- **Always filter on built-in rather than parsed fields**. While it's sometimes easier to filter using parsed fields, it dramatically impacts performance.
- **Use operators that provide optimized performance**. In particular, ==, has, and startswith. Using operators such as contains or matches regex also dramatically impacts performance.

Filtering recommendations for performance may not always be easy to follow. For example, using has, is less accurate than contains. In other cases, matching the built-in field, such as SyslogMessage, is less accurate than comparing an extracted field, such as DvcAction. In such cases, we recommend that you still pre-filter using a performance-optimizing operator over a built-in field and repeat the filter using more accurate conditions after parsing.

For an example, see the following Infoblox DNS parser snippet. The parser first checks that the SyslogMessage field has the word client. However, the term might be used in a different place in the message, so after parsing the Log_Type field, the parser checks again that the word client was indeed the field's value.

KQL

```
Syslog | where ProcessName == "named" and SyslogMessage has "client"
…
      | extend Log_Type = tostring(Parser[1]),
      | where Log_Type == "client"
```

### Parsing

Once the query selects the relevant records, it may need to parse them. Typically, parsing is needed if multiple event fields are conveyed in a single text field.

The KQL operators that perform parsing are listed below, ordered by their performance optimization. The first provides the most optimized performance, while the last provides the least optimized performance.

|Operator|Description|
|---|---|
|split|Parse a string of delimited values.|
|parse_csv|Parse a string of values formatted as a CSV (comma-separated values) line.|
|parse|Parse multiple values from an arbitrary string using a pattern, which can be a simplified pattern with better performance, or a regular expression.|
|extract_all|Parse single values from an arbitrary string using a regular expression. extract_all has a similar performance to parse if the latter uses a regular expression.|
|extract|Extract a single value from an arbitrary string using a regular expression. Using extract provides better performance than parse or extract_all if a single value is needed. However, using multiple activations of extract over the same source string is less efficient than a single parse or extract_all and should be avoided.|
|parse_json|Parse the values in a string formatted as JSON. If only a few values are needed from the JSON, using parse, extract, or extract_all provides better performance.|
|parse_xml|Parse the values in a string formatted as XML. If only a few values are needed from the XML, using parse, extract, or extract_all provides better performance.|

In addition to parsing string, the parsing phase may require more processing of the original values, including:

- **Formatting and type conversion**. The source field, once extracted, may need to be formatted to fit the target schema field. For example, you may need to convert a string representing date and time to a datetime field. Functions such as todatetime and tohex are helpful in these cases.
    
- **Value lookup**. The value of the source field, once extracted, may need to be mapped to the set of values specified for the target schema field. For example, some sources report numeric DNS response codes, while the schema mandates the more common text response codes. The functions iff and case can be helpful to map a few values.
    
    For example, the Microsoft DNS parser assigns the EventResult field based on the Event ID and Response Code using an iff statement, as follows:
    
    KQL
    
    ```
    extend EventResult = iff(EventId==257 and ResponseCode==0 ,'Success','Failure')
    ```
    
    For several values, use datatable and lookup, as demonstrated in the same DNS parser:
    
    KQL
    
    ```
    let RCodeTable = datatable(ResponseCode:int,ResponseCodeName:string) [ 0, 'NOERROR', 1, 'FORMERR'....];
    ...
     | lookup RCodeTable on ResponseCode
     | extend EventResultDetails = case (
     isnotempty(ResponseCodeName), ResponseCodeName,
     ResponseCode between (3841 .. 4095), 'Reserved for Private Use',
     'Unassigned')
    ```
    

### Mapping values

In many cases, the original value extracted needs to be normalized. For example, in ASIM a MAC address uses colons as separator, while the source may send a hyphen delimited MAC address. The primary operator for transforming values is extend, alongside a broad set of KQL string, numerical and date functions, as demonstrated in the Parsing section above.

Use case, iff, and lookup statements when there's a need to map a set of values to the values allowed by the target field.

When each source value maps to a target value, define the mapping using the datatable operator and lookup to map. For example

KQL

```
let NetworkProtocolLookup = datatable(Proto:real, NetworkProtocol:string)[
        6, 'TCP',
        17, 'UDP'
   ];
    let DnsResponseCodeLookup=datatable(DnsResponseCode:int,DnsResponseCodeName:string)[
      0,'NOERROR',
      1,'FORMERR',
      2,'SERVFAIL',
      3,'NXDOMAIN',
      ...
   ];
   ...
   | lookup DnsResponseCodeLookup on DnsResponseCode
   | lookup NetworkProtocolLookup on Proto

```

Notice that lookup is useful and efficient also when the mapping has only two possible values.

When the mapping conditions are more complex use the **iff** or **case** functions. The **iff** function enables mapping two values:

KQL

```
| extend EventResult = 
      iff(EventId==257 and ResponseCode==0,'Success','Failure’)
```

The **case** function supports more than two target values. The example below shows how to combine **lookup** and **case**. The **lookup** example above returns an empty value in the field DnsResponseCodeName if the lookup value isn't found. The **case** example below augments it by using the result of the **lookup** operation if available, and specifying additional conditions otherwise.

KQL

```
| extend DnsResponseCodeName = 
      case (
        DnsResponseCodeName != "", DnsResponseCodeName,
        DnsResponseCode between (3841 .. 4095), 'Reserved for Private Use',
        'Unassigned'
      )
```

### Prepare fields in the result set

The parser must prepare the fields in the results set to ensure that the normalized fields are used.

The following KQL operators are used to prepare fields in your results set:

|Operator|Description|When to use in a parser|
|---|---|---|
|project-rename|Renames fields.|If a field exists in the actual event and only needs to be renamed, use project-rename. The renamed field still behaves like a built-in field, and operations on the field have much better performance.|
|project-away|Removes fields.|Use project-away for specific fields that you want to remove from the result set. We recommend not removing the original fields that aren't normalized from the result set, unless they create confusion or are very large and may have performance implications.|
|project|Selects fields that existed before, or were created as part of the statement, and removes all other fields.|Not recommended for use in a parser, as the parser shouldn't remove any other fields that aren't normalized. If you need to remove specific fields, such as temporary values used during parsing, use project-away to remove them from the results.|
|extend|Add aliases.|Aside from its role in generating calculated fields, the extend operator is also used to create aliases.|

### Handle parsing variants

In many cases, events in an event stream include variants that require different parsing logic. To parse different variants in a single parser either use conditional statements such as iff and case, or use a union structure.

To use union to handle multiple variants, create a separate function for each variant, and use the union statement to combine the results:

KQL

```
let AzureFirewallNetworkRuleLogs = AzureDiagnostics
    | where Category == "AzureFirewallNetworkRule"
    | where isnotempty(msg_s);
let parseLogs = AzureFirewallNetworkRuleLogs
    | where msg_s has_any("TCP", "UDP")
    | parse-where
        msg_s with           networkProtocol:string 
        " request from "     srcIpAddr:string
        ":"                  srcPortNumber:int
    …
    | project-away msg_s;
let parseLogsWithUrls = AzureFirewallNetworkRuleLogs
    | where msg_s has_all ("Url:","ThreatIntel:")
    | parse-where
        msg_s with           networkProtocol:string 
        " request from "     srcIpAddr:string
        " to "               dstIpAddr:string
    …
union parseLogs,  parseLogsWithUrls…

```

To avoid duplicate events and excessive processing, make sure each function starts by filtering, using native fields, only the events that it's intended to parse. Also, if needed, use project-away at each branch, before the union.

### Deploy parsers

Deploy parsers manually by copying them to the Azure Monitor Log page and saving the query as a function. This method is useful for testing. For more information, see Create a function.

To deploy a large number of parsers, we recommend using parser ARM templates, as follows:

1. Create a YAML file based on the relevant template for each schema and include your query in it. Start with the YAML template relevant for your schema and parser type, filtering or parameter-less.
    
2. Use the ASIM Yaml to ARM template converter to convert your YAML file to an ARM template.
    
3. If deploying an update, delete older versions of the functions using the portal or the function delete PowerShell tool.
    
4. Deploy your template using the Azure portal or PowerShell.
    

You can also combine multiple templates to a single deploy process using linked templates.


# Configure Azure Monitor Data Collection Rules

Another way of normalizing log data is transforming the data at ingestion time. This provides the benefit of storing the data in a parsed format for use in Microsoft Sentinel.

## Data collection rules in Azure Monitor

Data Collection Rules (DCRs) provide an ETL-like pipeline in Azure Monitor, allowing you to define the way that data coming into Azure Monitor should be handled. Depending on the type of workflow, DCRs may specify where data should be sent and may filter or transform data before storing it in Azure Monitor Logs. Some data collection rules are created by Azure Monitor, while you may create others to customize data collection for your particular requirements.

## Types of data collection rules

Azure Monitor supports several types of data collection rules. Common types include:

- **Standard DCR**. Used with different workflows that send data to Azure Monitor, including the Azure Monitor agent and custom logs ingestion.
    
- **Workspace transformation DCR**. Used with a Log Analytics workspace to apply ingestion-time transformations to workflows that don't currently support DCRs directly.
    

Note

For the current complete list of DCR types and supported workflows, see [Data collection rules in Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/data-collection-rule-overview).

## Transformations

Transformations in a data collection rule (DCR) allow you to filter or modify incoming data before storing it in a Log Analytics workspace. Data transformations are defined using a Kusto Query Language (KQL) statement that is applied individually to each entry in the data source. It must understand the format of the incoming data and create output in the structure of the target table.

### Transformation structure

The input stream is represented by a virtual table named **source** with columns matching the input data stream definition. Following is a typical example of a transformation. This example includes the following functionality:

- Filters the incoming data with a where statement
- Adds a new column using the extend operator
- Formats the output to match the columns of the target table using the project operator

KQL

```
source  
| where severity == "Critical" 
| extend Properties = parse_json(properties)
| project
    TimeGenerated = todatetime(["time"]),
    Category = category,
    StatusDescription = StatusDescription,
    EventName = name,
    EventId = tostring(Properties.EventId)
```


**![[Pasted image 20261008190722.png]]**

# Summary and resources


You learned how to normalize and use ASIM Parsers in Microsoft Sentinel.

You should now be able to:

- Use ASIM Parsers
- Create ASIM Parser
- Create parameterized KQL functions


# Query, visualize, and monitor data in Microsoft Sentinel

# Introduction

Microsoft Sentinel Workbooks provide interactive reports that help you visualize important signals by combining text, table, charts, and tiles.

Contoso, Ltd. is a midsize financial services company in London with a New York branch office. Contoso uses several Microsoft products and services to implement data security and threat protection for its resources. These products are:

- Microsoft 365
- Microsoft Entra ID
- Microsoft Entra ID Protection
- Defender for Cloud Apps
- Microsoft Defender for Identity
- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- System Center Endpoint Protection
- Microsoft Azure Information Protection

Contoso provides threat protection for its Azure-based and on-premises resources by using the paid version of Microsoft Defender for Cloud. The company also monitors and protects other non-Microsoft assets.

A recent incident with compromised identities led to exposed customer data. The Contoso Security Operations (SecOps) team wants to ensure that proper monitoring and reporting methods are in place. As Contoso's security administrator, you need to demonstrate the Microsoft Sentinel reporting and monitoring capabilities and how they can alert your organization to potential security incidents.

In this module, you learn how to create and use Microsoft Sentinel Workbooks. You can visualize security data, use queries to generate reports, and explore the functionalities of a workbook.

By the end of this module, you can create Microsoft Sentinel Workbooks to take advantage of the reporting and monitoring features in Microsoft Sentinel.

## Learning objectives

- Visualize security data using Microsoft Sentinel Workbooks.
- Understand how queries work.
- Explore workbook capabilities.
- Create a Microsoft Sentinel Workbook.

## Prerequisites

To get the best learning experience from this module, you should have:

- Familiarity with security operations in an organization
- Basic experience with Azure services
- Basic knowledge of operational concepts such as monitoring, logging, and alerting
- Microsoft Sentinel instance in your Azure subscription

Note

If you choose to perform the exercise in this module, be aware that you could incur costs in your Azure Subscription. To estimate the cost refer to [Microsoft Sentinel Pricing](https://azure.microsoft.com/pricing/details/azure-sentinel/).

# Exercise - Query and visualize data with Microsoft Sentinel Workbooks

This _query and visualize data_ exercise is an optional unit. If you want to perform this exercise, you need access to an Azure subscription where you can create Azure resources. If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn_c04111f5-68e0-c69e-982f-746612a61fb9) before you begin.

Note

If you choose to perform the exercise in this module, be aware that you might incur costs in your Azure Subscription. To estimate the cost, refer to [Microsoft Sentinel Pricing](https://azure.microsoft.com/pricing/details/azure-sentinel/).

To deploy the prerequisites for the exercise, perform the following tasks.

## Task 1: Create resources

1. Select the following link:
    
    [![Deploy To Azure.](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftDocs%2Fmslearn-security-ops-sentinel%2Fmain%2Fmslearn-query-data-sentinel%2Fsentinel-template.json?azure-portal=true)
    
    You're prompted to sign in to Azure.
    
2. On the **Custom deployment** page, provide the following information:
    
    |Name|Description|
    |---|---|
    |Subscription|Select your Azure subscription.|
    |Resource group|Select **Create new** and provide a name for the resource group such as _azure-sentinel-rg_.|
    |Region|From the dropdown menu, select the location where you want to deploy Microsoft Sentinel.|
    |Workspace Name|Provide a unique name for the Microsoft Sentinel Workspace such as _<yourName>-sentinel_.|
    |Location|Accept the default value of **[resourceGroup().location]**.|
    |Simplevm Name|Accept the default value of **simple-vm**.|
    |Simplevm Windows OS Version|Accept the default value of **2022-Datacenter**.|
    
3. Select **Review + create**, and then select **Create**.
    
    ![Screenshot of the Custom Deployment page.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/02-custom-deployment.png)
    
    Note
    
    Wait for the deployment to complete. The deployment should take less than 5 minutes.
    

## Task 2: Check the resources created

1. In the Azure portal, search for _Resource groups_.
    
2. Select **azure-sentinel-rg**.
    
3. Sort the list of resources by **Type**.
    
4. The resource group should contain the resources listed in the following table.
    
    |Name|Type|Description|
    |---|---|---|
    |<yourName>-sentinel|Log Analytics workspace|Log Analytics workspace used by Microsoft Sentinel, with the workspace name that you chose in the previous task.|
    |simple-vmNetworkInterface|Network Interface|Network interface for the virtual machine (VM).|
    |SecurityInsights(<yourName>-sentinel)|Solution|Security insights for Microsoft Sentinel.|
    |st1_xxxxx_|Storage account|Storage account used by the VM. The random string _xxxxx_ creates a unique storage account name.|
    |simple-vm|Virtual machine|Virtual machine used in the demonstration.|
    |vnet1|Virtual network|Virtual network for the VM.|
    

Note

The resources and configuration in this exercise are required in the next exercise. If you intend to complete the next exercise, don't delete these resources.

## Task 3: Configure Microsoft Sentinel connectors

In this task, you deploy a Microsoft Sentinel connector to Azure Activity.

1. In the Azure portal, search for and select **Microsoft Sentinel**. Select the Microsoft Sentinel workspace that you created in the previous task.
    
2. On the **Microsoft Sentinel** page, on the menu bar, under **Configuration**, select **Data connectors**.
    
3. In the **Data connectors** pane, search and select **Azure Activity**.
    
4. In the details pane, select **Open connector page**.
    
    ![Screenshot of the Microsoft Sentinel Data connectors page.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/02-azure-sentinel-connector.png)
    
5. In the **Azure Activity** screen, under **Instructions**, verify your **Prerequisites** and then follow the **Configuration** steps.
    
6. When you receive a status of **Connected**, close all open panels to return to the **Microsoft Sentinel | Data connector** panel.
    

Note

The connector for Azure Activity could take 15 minutes to deploy. You can proceed with the rest of the steps in the exercise and with the subsequent units in this module.


# Monitor and visualize data


Microsoft Sentinel Logs provide you access to the various logs collected from the security connectors. Microsoft Sentinel collects these logs from its integrated connectors and stores them in the Azure Log Analytics workspace.

## Log Analytics workspace

The Log Analytics workspace is a repository that stores data and configuration information. You can create queries to filter important information, which you can then use to create analytics rules and detect threats. For example, you can use Microsoft Sentinel Logs to search data from multiple sources, aggregate large data sets, and perform complex operations to locate potential security threats and vulnerabilities.

## Explore the Microsoft Sentinel Logs page

You can search for specific logs on the **Microsoft Sentinel Logs** page. View the page by selecting **Logs** in the navigation pane in Microsoft Sentinel.

The **Logs** page has these main parts:

- The page header contains links to the **Queries**, settings, and help section.
- The **Tables** pane displays collected data from the logs in tables, each comprising multiple columns.
- The query pane is where you write your own query expressions.
- The query result pane displays the results of your queries.

![Screenshot of the default Logs page that shows four elements: the Header bar, the Tables pane, the Queries pane, and the Query results/history pane.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/03-logs.png)

### Queries

When you select the **Queries** link on the page header, a new window opens, where you can select from some of the predefined sample queries. From the **Queries** drop-down menu, you can filter these queries based on:

- Category
- Query Type
- Resource Type
- Solution
- Topic

Select **Run** to start a predefined query. This action redirects you to the query pane. You can observe the query structure and the results. To address Contoso's concern about unauthorized users, run the predefined query **Unauthorized Users**.

![Screenshot that presents unauthorized users.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/03-unauthorized-users.png)

### Query Explorer

Use the Query Explorer to access your previously saved queries. You can also access some **Solution Queries** that basically filter the most common queries that you can use to filter the data. From the **Solution Queries** list, you can either run the query or organize the query in the favorites section by selecting the star symbol.

### Tables pane

The **Tables** pane groups logs from different solutions into tables. You can expand the solution group and observe all the logs that are collected. You can also select one of the logs from the tables pane. You can preview the data or add that log to the **Favorites** section.

The following screenshot displays the logs collected in Microsoft Sentinel solution.

![Screenshot displaying the Tables view.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/03-logs-azure-sentinel.png)

### Queries pane

Use the **Queries** pane to create queries that retrieve data based on the expression that you provide. The **Queries** pane helps you to write an accurate query by providing suggestions and automatically filling the expected elements of the query.

Take advantage of the capabilities of the Kusto Query Language (KQL) to write a query that retrieves data from the logs. The following example illustrates how to use KQL code in your queries to identify deleted virtual machines.

Kusto

```
AzureActivity
| where OperationName == 'Delete Virtual Machine'
| where ActivityStatus == 'Accepted'
| extend AccountCustomEntity = Caller
| extend IPCustomEntity = CallerIpAddress
```

### Header toolbar

The header toolbar provides more interaction with the query, as displayed in the following screenshot.

![Screenshot of the header toolbar, with options described in the text following the image.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/03-header-toolbar.png)

- Save the query from the **Query** pane by selecting **Save**. This action opens a new window, where you're prompted to enter the name of the saved query and category. Saved queries appear in the query explorer.
    
- In the **Time Range** field, you can provide a different time to change the time range for which you want to display the results of the query.
    
- Create a link for the query and share with other team members by selecting **Copy link to query**. You can also copy the query text.
    
- From the header toolbar in the **Query** pane, you can create either a **New Azure Monitor alert** or a **New Microsoft Sentinel alert**. If you opt to create a new Microsoft Sentinel alert, you'll be directed to the next steps for creating an analytics rule.
    
- Export the query into one of the following formats:
    
    - **Export to CSV**. Export all the columns, both visible and hidden, into a CSV file that you can open with Microsoft Excel.
    - **Export to CSV-Displayed Columns**. Export only those columns that are displayed in the results windows of the query.
    - **Export to Power BI (M query)**. Create and download a _PowerBIQuery.txt_ file that you can open with Microsoft Power BI application.
    
    You can pin the results of the query into a private or shared dashboard to quickly examine the results of the query.
    
- You can use **Format query** on the header toolbar to make the query more readable.
    

Note

You can export or pin the query only if the query expression generates data in the query result section.

![[Pasted image 20261008192130.png]]

# Query data using Kusto Query Language

You can use the Kusto Query Language (KQL) in Microsoft Sentinel to search and filter collected data.

## Kusto Query Language

KQL provides you with the ability to create, store, and run interactive analytics on collected data. Microsoft Sentinel uses KQL to visualize and analyze the important data. You can use KQL to create complex analytical queries that include some of the following operators:

- Calculated columns
- Join functions
- Group by aggregates

## Write and run basic queries

A query is a read-only request that processes data and returns the results of this processing without modifying the data or metadata. Similar to SQL queries, KQL queries use schema entities that are organized in a hierarchy such as databases, tables, and columns. A schema is a collection of tables grouped under logical categories. The queries consist of sequences of query statements that are delimited by a semicolon (;).

When you construct a query, you start with either a table name or a search command. For example, the following query retrieves all records from the `Event` table:

Kusto

```
Event
```

You can use the pipe (|) character to separate commands. The output of the first command becomes the input of the next command. You can add any number of commands to a single query. The following query retrieves the records from the `Event` table, and then searches them for the term `error` in any property:

Kusto

```
Event

| search error
```

You can construct the query with tabular and scalar operators that KQL combines into multiple tabular expression statements, which produce the results of the query.

Kusto

```
source1 | operator1 | operator2
```

In the following example, the source is `AzureActivity`. The first operator is `where`, which filters out records based on the logical expression. The second operator is again `where`:

Kusto

```
AzureActivity

| where OperationName == 'Delete Virtual Machine'
| where ActivityStatus == 'Accepted'
```

By default, Log Analytics limits queries to a time range of the past 24 hours. To set a different time range, you can add an explicit `TimeGenerated` filter to the query or use the `Time range` control. For example, the following query returns data from the preceding hour:

Kusto

```

AzureActivity

| where OperationName == 'Delete Virtual Machine'
| where ActivityStatus == 'Accepted'
| where TimeGenerated > ago (1h)
```

You can combine your queries with some of the most commonly used operators:

- `count`. Returns the count of rows in the table.
- `take`. Returns up to the specified number of rows of data.
- `project`. Selects a subset of columns.
- `sort`. Sorts the rows of the input table into order by one or more columns.
- `top`. Returns the first N records sorted by the specified columns.
- `extend`. Computes derived columns.
- `summarize`. Aggregates groups of rows.
- `render`. Renders results as a graphical output.

To combine the records from two sources (tables), you can use the `join` operator. The `union` operator combines two or more tables into one.

For more information, see the Microsoft [Log analytics tutorial](https://learn.microsoft.com/en-us/azure/azure-monitor/log-query/log-analytics-tutorial) that uses features of Log Analytics to build and run a query instead of working with the query itself.

You can also use [Azure Data explorer tutorial](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/tutorial?pivots=azuredataexplorer) to learn about KQL.

Note

Microsoft Sentinel Log Analytics doesn't support all the KQL syntax that is used in Azure Data Explorer.

## Microsoft Sentinel repository on GitHub

You can also use the [Microsoft Sentinel repository](https://github.com/Azure/Azure-Sentinel) on GitHub to search for specialized queries and workbooks to help secure your environment and hunt for threats. For example, the following query from Microsoft Sentinel GitHub repository displays suspicious delegation of permissions to user accounts.

Kusto

```
let timeframe = 7d;
AzureActivity
| where TimeGenerated >= ago(timeframe)
| where OperationName == "Create role assignment"
| where ActivityStatus == "Succeeded"
| project Caller, CallerIpAddress
| evaluate basket()
| extend AccountCustomEntity = Caller, IPCustomEntity = CallerIpAddress
```

The query analyzes the IP address from where the administrator grants access to other users to Azure resources. If an operation isn't from a valid IP address, the query signals suspicious activity, which you can further investigate.

If you want to try some examples, use [the demonstration environment on the Azure portal](https://ms.portal.azure.com/#blade/Microsoft_Azure_Monitoring_Logs/DemoLogsBlade).


![[Pasted image 20261008192538.png]]

# Use default Microsoft Sentinel Workbooks
Microsoft Sentinel provides several templates that are ready for use. You can use these templates to create your own workbook and then modify them as needed for Contoso.

## Microsoft Sentinel Workbooks

Most of the data connectors Microsoft Sentinel uses to ingest data come with their own workbooks. You can get insights into the data that is being ingested by using tables and visualizations, including bar and pie charts. You can also make your own workbooks from scratch instead of using the predefined templates.

## Workbook page

You can access the **Workbooks** page for Microsoft Sentinel from the navigation pane. In the **Workbooks** page, you can add a new workbook and review the saved workbooks and templates that are available.

You can access existing workbook templates on the **Templates** tab. You can save some of the workbooks for quick access. They appear on the **My workbooks** tab.

From the **Templates** tab, you can select an existing workbook to display a details pane for it, which contains additional information for the template. The details pane also contains information about the required data types and data connectors that must be connected to Microsoft Sentinel. You can also review how the report displays.

## Review an existing workbook template

As mentioned earlier, Contoso is concerned about compromised identities. As the security administrator, you can examine the existing **Microsoft Entra sign-in logs** workbook by selecting that template in the **Templates** section. Then select **View template** in the details pane.

The **Microsoft Entra sign-in logs** workbook contains predefined charts, graphs, and tables that can provide important insight about the sign-in activity in Microsoft Entra ID. You can find information about user sign-ins and locations, email addresses, and IP addresses of your users. You can also review information about failed activities and the errors that triggered the failures.

On the **Microsoft Entra sign-in logs** page, you can expand the time range or filter the apps and users that have sign-in privileges in Microsoft Entra ID. For example, Contoso wants to identify users that can sign-in to the Azure portal, so you can filter the data as follows.

![Screenshot that displays Sign-in Analysis with filtering of the users that sign-in to the Azure portal.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/05-filter-users.png)

Contoso is interested in identifying the failed sign-in attempts. You can display these accounts by selecting the information tiles, and then select a tile or a row to display more information such as:

- **Sign-ins by location**. This section indicates the location from which the user signed in to Microsoft Entra ID.
- **Location sign-in details**. This section displays the users, their sign-in status, and the time of the sign-in attempt.
- **Sign-ins by device**. This section lists devices used by the users to sign in to Microsoft Entra ID.
- **Device sign-in details**. This section displays the users that signed in on a particular device and the time they signed in.

This information tile in the background is configured to run the query and filter the data collected from the Microsoft Entra connector. Microsoft Sentinel then visualizes and presents the data collected by using tables, which are more meaningful and provide useful insight on user sign-in attempts.

The workbook contains other tiles that indicate the users who signed in using Conditional Access. From the **Conditional access status** table, you can review users who required multifactor authentication to validate their identity.

![Screenshot of Conditional Access activity.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/05-conditional-access.png)

The rest of the page also contains tables and charts that are interactive. Select some of the rows or tiles to filter the data that is presented. Some tables are created with links to corresponding logs as displayed in the following screenshot.

![Screenshot of the links that can open the query in Azure Data Explorer or pin the query in dashboard.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/05-links.png)

Note

You can also pin the query step in the private or shared dashboard for quick retrieval.

## Edit the query from the workbook

For example, Contoso wants to search the logs for more information that presents the failed user sign-in. They're redirected to the Azure Data Explorer, where Microsoft Sentinel performs the log query to filter the information.

![Screenshot of Data Explorer.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/05-data-explorer.png)

## Explore saved workbooks

From the **Templates** page, you can save a workbook from existing templates by selecting one of the templates, and then selecting **Save.** You must provide a location to indicate where you want to save the workbook. This process creates an Azure resource based on the template with template's JSON file.

Saved workbooks are available on the **My Workbooks** tab, where you can customize them. You can open saved workbooks by selecting **View saved workbook**. This action opens the same page as the template workbook page, but you can customize this one based on Contoso's requirements.

Select **Edit** to open the workbook in the edit mode. You can add or remove items and provide more customization. The editing mode displays all content in the workbook, including steps and parameters that would be hidden in the reading mode.

The header bar in the editing mode contains several options, which the following screenshot depicts.

![Screenshot of the Editing mode that depicts the various editing options such as Save, Save As, Settings, Refresh, Share, Help, and more.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/05-editing-options.png)

When you switch to the editing mode, notice several **Edit** options that correspond to each individual aspect of your workbook. If you select one of these edit options, you can examine the query that Microsoft Sentinel uses to filter the data from the corresponding log.

When you select the settings icon, the **Settings** page opens, where you can provide other resources that you want to use in the workbook. You can also change the style of the workbook, provide tagging, or pin an item in the workbook.

![Screenshot of the Settings page.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/05-settings.png)

You can rearrange the placement of different tables in the workbook by selecting **Show Pin Options**.

For advanced customization, you can select **Advanced Editor** to open the JSON representation of the current workbook, and then further customize it in the text editor. You can save your changes in the existing workbook or save as another workbook. When you're done with all the customization, you can exit the edit mode by selecting **Done Editing**.

## Explore the Microsoft Sentinel repository on GitHub

The Microsoft Sentinel repository contains out-of-the-box detections, exploration queries, hunting queries, workbooks, playbooks, and more to help you secure your environment and detect threats. Microsoft and the Microsoft Sentinel community contribute to this repository.

The repository contains folders with contributed content for several areas of Microsoft Sentinel functionality, including detection queries. You can use the code from these queries to create custom queries in your Microsoft Sentinel workspace.

![[Pasted image 20261008192810.png]]

# Create a new Microsoft Sentinel Workbook

In addition to using built-in templates to create a customized workbook, you can create custom workbooks from scratch to produce highly interactive reports that contains texts, analytic queries, metrics, and parameters.

## Create a custom workbook

You can create a custom workbook from the **Workbooks** page in Microsoft Sentinel. Select **+Add workbook** on the header bar. The **New workbook** page opens, which contains a basic analytics query to get you started.

Tip

The Azure portal saves each workbook that you create as a workbook resource in the Microsoft Sentinel resource group.

You can start building your workbook on the **New Workbook** page by selecting **Edit**. Then select the **Edit** option to change the text that appears in the new workbook template.

Each workbook provides a rich set of capabilities for visualizing the security data collected from the connectors. You can design your workbook with the following visualization types and elements:

- Text
- Query
- Parameters
- Links/tabs
- Metric

You can add a new element to your workbook by selecting **+Add** as the following screenshot depicts.

![Screenshot of adding a new step in the workbook.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/06-add-visualization.png)

## Text visualizations

You can use text blocks to interpret your security data, section headings, telemetry data, and other information. You can edit the text using the Markdown markup language, which provides different formatting options for headings, font styles, hyperlinks, and tables.

Note

Markdown is a markup language that you can use to format text in plain text documents. For more information on how to format text by using Markdown controls, see the markdown guides available online.

After you add the text, select the **Preview** tab to preview how your content appears. When you complete editing the text, select the **Done Editing** option.

## Query item

You can create a different query from the logs and visualize the data as text, charts, or grids. You can write the query using KQL. Then format the data using various visualizations including:

- Grids (or tables)
- Area charts
- Bar charts
- Line charts
- Pie charts
- Scatter charts
- Time charts
- Tiles

When you create a query, Microsoft Sentinel adds a new **Run Query** step to the workbook as the following screenshot depicts:

![Screenshot of the Query visualization step, with the Done editing button called out.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/06-query-visualization.png)

On the header bar, there are several fields that provide you with options to tune the output of the query.

|Name|Description|
|---|---|
|Run Query|Use this option to test the result of the query.|
|Samples|Microsoft provides sample code that contains sample queries that you can add to the workbook.|
|Data Source|Use this option to specify the data source for the query.|
|Resource type|Use this option select the type of resource.|
|Log Analytics workspace|Use this option if you want to query data against more than one resource.|
|Time Range|Use this option to specify a time range parameter to use in the query.|
|Visualization|Use this option to choose a specific visualization or choose **Set by query** to present the data in a different format.|
|Size|Use this option to choose the size of the visualization element.|

On the **Advanced Settings** tab, you can provide more customization for the settings and the styles of your query step. On the **Advanced Settings** tab, you can modify properties. For example, you can enter the **Chart title**, as the following screenshot depicts.

![Screenshot of the Advanced settings tab, with the chart title.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/06-advanced-settings.png)

You can use the **Style** tab to adjust the margin and padding element in the step. After you're done customizing the settings and styles, remember to save the step by selecting **Done Editing**.

## Chart visualizations

When you create a query to present the security data as charts, you can customize:

- Height
- Width
- Color palette
- Legend
- Titles
- Axis types and series

The following example counts all the security alerts and visualizes them in a pie chart.

Kusto

```

SecurityAlert
| where TimeGenerated \&gt;= ago(180d)
| summarize Count=count() by AlertSeverity
| render piechart
```

In the previous example, the query indicates the visualization type for the data. You can also use the query without including the _render_ parameter. Use the **Visualization** dropdown menu to select one of the offered types of visualizations:

![Screenshot of the Visualization dropdown menu options.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/06-visualization-menu.png)

## Grid visualizations

You can use the **Grid** visualization option from the **Visualization** dropdown menu to present data in tables, which provides an enriched UI for the reports. You can select the **Column Settings** option to specify which column is displayed in the table and to provide column labels, if necessary.

On the **Edit Column settings** tab, you can select a different column renderer such as, heatmap, bar, and spark area. If you select **Custom formatting**, you can set units, style, and formatting options for number values.

## Parameters

You can use parameters in your interactive workbook to manipulate the results of the query in different ways. When you select **Add Parameter**, a **New Parameter** page opens where you can provide the name and other inputs required for the parameter.

You can create the following parameter types:

- **Text**. You can enter arbitrary text.
- **Drop down**. You can modify the appearance of a query step to include a dropdown menu in which you can select a value from a set of values. In this parameter type, you can enter a KQL query or a JSON string to provide the choices for the dropdown list.
- **Time range picker**. You can select from prepopulated time ranges or select a custom range.
- **Resource picker**. You can select one or more Azure resources.
- **Subscription picker**. You can select one or more Azure subscription resources.
- **Resource type picker**. You can select one or more Azure resource type values.
- **Location picker**. You can select one or more Azure location values.
- **Options group**. You can group multiple properties into group.
- **Tabs**.
- **Multi-value**.

You can reference parameter values in other parts of the workbooks either by using bindings or by using value expansions.

On the **New Parameter** pane in the **Previews** section, you can review the variables that are displayed and used in the query code.

## Links/tabs

You can add a links/tabs step to customize the navigation in the workbook with tabs, lists, paragraphs, or bullet lists. You can provide the following inputs while adding a new links/tabs step:

- **Text before link**. Use this option to display the text before the link is selected.
- **Link text**. Use this option to specify the actual text that is displayed in the link.
- **Text after link**. Use this option to indicate the text that is displayed after the link is selected.
- **Action**. Use this option to specify the action that is performed when you select the link, such as **Url**, **Set a parameter value**, and **Scroll to a step**.
- **Value**. Use this option to indicate a value for the link.
- **Settings**. Use this option to configure specific settings based on the link type and support parameters syntax.
- **Context pane?**. Use this option to open a new context panel to the side instead of a full view.
- **Style**. Use this option to select between **Link**, **Button (primary)**, and **Button (secondary)** styles.

## Metric steps

You can use metric steps to combine the results of the workbook with metrics from different Azure resources. After you're done making all your custom modifications to your workbook, remember to save the workbook by selecting **Done Editing**.

![[Pasted image 20261008193032.png]]

# Exercise - Visualize data using Microsoft Sentinel Workbooks
As a security engineer working for Contoso, you notice suspicious activities in your Azure subscription and you decide to analyze this activity by using Microsoft Sentinel workbooks.

## Exercise: Query and visualize data with Microsoft Sentinel Workbooks

You want to analyze the logs in Microsoft Sentinel from the Azure Activity connector. You want to further implement visualization of this data and save it in a customized workbook.

In this exercise, explore logs and Microsoft Sentinel Workbooks. You perform the following tasks:

- Interact with logs data in the Microsoft Sentinel **Logs** page.
- Create and edit a custom workbook to visualize important data.

Note

You must have completed the [Query and visualize data with Microsoft Sentinel Workbooks](https://learn.microsoft.com/en-us/training/modules/query-data-sentinel/2-exercise-setup) unit before you can complete this exercise. If you have not done so, complete it now, and then continue with the exercise steps.

### Task 1: Work with Logs in Microsoft Sentinel

1. In the Azure portal, search for and select **Microsoft Sentinel**, and then select the previously created Microsoft Sentinel workspace.
    
2. On the **Microsoft Sentinel** page, in the **General** section, select **Logs**.
    
    Note
    
    When you open the **Logs** page for the first time, you might be redirected to the **Queries** window. Close the **Queries** window and return to the **New Query 1** section.
    
3. On the **Microsoft Sentinel | Logs** page, in the **Tables** pane, from the **Group by: Solution** dropdown menu, select **Category**.
    
4. In the **Tables** pane, from the list of tables, expand the **Azure Resources** category, move the cursor over the **Azure Activity** table or use the **Tab** key to navigate to the table, and then select **Preview data**.
    
5. In the **AzureActivity** window, select **See in query editor**. This option enables you to preview the data and to check if the results are as you expect before you actually run a query with it.
    
    ![Screenshot of the Tables pane.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/07-tables-pane.png)
    
    In the **Query** section, you can observe the query structure. This query searches and presents the last 10 events from the Azure Activity log. The first row in the query, `AzureActivity` specifies the table used in the query. The second line contains a `where` statement that filters the records from the last day. The third line contains another statement to filter only the last 10 events.
    
    The query results section presents the results of the query. You can expand any of the records to review the values in the table. Select the name of any column to sort the results by that column.
    
6. Select the filter icon next to it to provide a filter condition. This approach is similar to adding a filter condition to the query itself except that this filter is cleared if you run the query again. If you select the **Columns** dropdown menu, you can filter the columns from the table that you want to display. By selecting **Group columns**, you can group records by a particular column.
    
    ![Screenshot of the Query results with the previous items called out.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/07-query-result.png)
    
7. Select **Queries** tab in the left pane. This pane includes example queries that you can add to the query window. If you're using your own workspace, you should have various queries in multiple categories. If you're using the demonstration environment, you might only see a single **Log Analytics workspaces** category.
    
    Note
    
    You can try to practice writing queries in the following [demonstration environment](https://ms.portal.azure.com/#blade/Microsoft_Azure_Monitoring_Logs/DemoLogsBlade).
    

### Task 2: Work with Workbooks in Microsoft Sentinel

1. On the **Microsoft Sentinel** page, in the **Threat Management** section, select **Workbooks**.
    
2. On the **Microsoft Sentinel | Workbooks** page, select the **Templates** tab.
    
3. In the **Search** field, enter and select **Azure Activity**.
    
4. In the details pane, review the information provided for the template, and then select **Save**. In the **Save workbook to…** window, select the same location that you selected in the preparation exercise, and then select **OK**.
    
5. On the **Microsoft Sentinel | Workbooks** page, select **My workbooks** tab. From the list of saved templates, select **Azure Activity**. Then in the details pane, select **View saved workbook**.
    
6. On **Azure Activity-** _sentinelname_ page, review all the elements of the workbook. You can interact with the workbook by selecting some of the elements.
    
7. Select the **Time range** field to select a different time range for the records presented in the **Azure Activity** table. Select the **Caller** dropdown menu to filter the records based on the user or service that generates the events. Select the **Resource Group** dropdown menu to filter the events based on a specific resource group.
    
    ![Screenshot of the Azure Activity page, with the previous elements called out.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/07-default-workbook.png)
    
8. Scroll down to the **Caller activities** table, which displays the activities run by your users or security principals. Sort the table data in each column by selecting the arrows in the column header.
    
9. Scroll up to the header bar in the **Azure Activity-** _sentinelname_ page. Select the **Edit** option to switch the workbook to the editing mode. Observe the various **Edit** options that display on the page.
    
10. Select the first **Edit** option. This action displays the editing pane for one of the steps in the workbook. You can customize the presentation of the elements by adjusting the style and reordering them in different order.
    
11. You can add other parameters with different types such as text, dropdown, multivalues, or similar.
    
12. Select **Add parameters**.
    
13. In the **New Parameter** page, enter the following values:
    
    |Name|Description|
    |---|---|
    |**Parameter name**|Level|
    |**Display name**|Level|
    |**Parameter type**|From the dropdown menu, select **Drop down**.|
    |**Required?**|Select this checkbox.|
    |**Allow multiple selections**|Select this checkbox.|
    |**Limit multiple selections**|Don't select this checkbox.|
    |**Delimiter**|Retain the default values.|
    |**Quote with**|Retain the default values.|
    |**Explanation**|This parameter filters the events based on the level.|
    |**Hide parameter in reading mode**|Don't select this checkbox.|
    |**Get data from**|Query|
    
14. In the **Log Analytics workspace Logs Query** section, enter the following query, and then select **Run Query**.
    
    Kusto
    
    ```
    AzureActivity
    |summarize by Level
    ```
    
15. Confirm that the query result returns two types of events based on the level: **Informational** and **Warning**.
    
    ![Screenshot of the New Parameter pane, with steps for adding a new parameter. The Save, Query, Run query options and the AzureActivity section are highlighted in the screenshot.](https://learn.microsoft.com/en-us/training/wwl-sci/query-data-sentinel/media/07-add-parameter.png)
    
16. Select **Save** to commit the changes, and notice the parameter step now includes a parameter called **Level**.
    
    Tip
    
    In the edit mode, you can select the ellipsis icon next to the **Edit** option to display a new dropdown menu. From that menu, you can move this step to different parts of the workbook. You can also clone or remove the step from the workbook.
    
17. On the header bar, select the **Save as** icon to save the customized workbook.
    
18. In the **Title** field, provide a name for the new workbook, and then select **Save**.
    
19. When you're finished making changes, select **Done Editing**.
    
    Tip
    
    Your new workbook is accessible from the **Microsoft Sentinel | Workbooks pane** in the **My workbooks** tab. If your new workbook isn't listed, select the **Refresh** option.
    

### Clean up the resources

1. In the Azure portal, search for **Resource groups**.
2. Select **azure-sentinel-rg**.
3. On the header bar, select **Delete resource group**.
4. In the **TYPE THE RESOURCE GROUP NAME:** field, enter the name of the resource group _azure-sentinel-rg_ and select **Delete**.

# Summary


The Contoso SecOps team recently encountered issues when users with compromised accounts tried to access Contoso's customer data. Microsoft Sentinel provides several monitoring and reporting features that help alert Contoso about potential security threats.

Microsoft Sentinel workbooks provide interactive reports with graphs, charts, and tables, and security administrators can use these features to visualize their security data by using advanced filtering. The SecOps team can use these techniques to gain more insights into their data during their investigations.

## Learn more

You can learn more by reviewing the following documents.

### Getting started

- [Microsoft Sentinel documentation](https://learn.microsoft.com/en-us/azure/sentinel)
- [Quickstart: On-board Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard)
- [Microsoft Sentinel pricing](https://azure.microsoft.com/pricing/details/azure-sentinel)
- [Permissions in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/roles)
- [Tutorial: Visualize and monitor your data](https://learn.microsoft.com/en-us/azure/sentinel/tutorial-monitor-your-data)
- [Quickstart: Get started with Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-get-visibility)
- [What is Azure Lighthouse?](https://learn.microsoft.com/en-us/azure/lighthouse/overview)
- [Extend Microsoft Sentinel across workspaces and tenants](https://learn.microsoft.com/en-us/azure/sentinel/extend-sentinel-across-workspaces-tenants#cross-workspace-monitoring?azure-portal=true)
- [What is Azure Resource Manager?](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/overview)
- [Azure Foundation 4-Week Implementation](https://azuremarketplace.microsoft.com/marketplace/consulting-services/servent.servent-azure-foundation)

### Microsoft Sentinel agent

- [Tutorial: Detect threats out-of-the-box](https://learn.microsoft.com/en-us/azure/sentinel/tutorial-detect-threats-built-in)
- [Connect data sources](https://learn.microsoft.com/en-us/azure/sentinel/connect-data-sources)

## Get started with Azure

Choose the Azure account that's right for you. Pay as you go or try Azure free for up to 30 days.[Sign up.](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn_e3fd937e-18b2-af8c-7169-ebcb26cafd4e


# Manage content in Microsoft Sentinel

# Introduction


Microsoft Sentinel **content** is Security Information and Event Management (SIEM) content that enables customers to ingest data, monitor, alert, hunt, investigate, respond, and connect with different products, platforms, and services in Microsoft Sentinel.

Content in Microsoft Sentinel includes any of the following types:

- **Data connectors** provide log ingestion from different sources into Microsoft Sentinel
- **Parsers** provide log formatting/transformation into ASIM formats, supporting usage across various Microsoft Sentinel content types and scenarios
- **Workbooks** provide monitoring, visualization, and interactivity with data in Microsoft Sentinel, highlighting meaningful insights for users
- **Analytics** rules provide alerts that point to relevant SOC actions via incidents
- **Hunting queries** are used by SOC teams to proactively hunt for threats in Microsoft Sentinel
- **Notebooks** help SOC teams use advanced hunting features in Jupyter and Azure Notebooks
- **Watchlists** support the ingestion of specific data for enhanced threat detection and reduced alert fatigue
- **Playbooks** and Azure Logic Apps custom connectors provide features for automated investigations, remediations, and response scenarios in Microsoft Sentinel

To maintain **content** in for Microsoft Sentinel use:

- **Content hub**: - Microsoft Sentinel **solutions** are packages of Microsoft Sentinel content or Microsoft Sentinel API integrations, which fulfill an end-to-end product, domain, or industry vertical scenario in Microsoft Sentinel.
- **Repositories**: - Repositories help you automate the deployment and management of your Microsoft Sentinel content through central repositories.
- **Community**: Onboard community content on-demand to enable your scenarios. The GitHub repo at [https://github.com/Azure/Azure-Sentinel](https://github.com/Azure/Azure-Sentinel) contains content by Microsoft and the community that is tested and available for you to implement in your Sentinel workspace.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You need to install connectors and analytical rules from a vendor. You also created a library of hunting queries that need to be maintained across multiple environments.

By the end of this module, you are able to manage _content_ in Microsoft Sentinel.

After completing this module, you'll be able to:

- Install a content hub solution in Microsoft Sentinel
- Connect a GitHub repository to Microsoft Sentinel
# Use solutions from the content hub

Use the Microsoft Sentinel Content hub to centrally discover and install out-of-the-box (built-in) content.

The Microsoft Sentinel Content Hub provides in-product discoverability, single-step deployment, and enablement of end-to-end product, domain, and/or vertical out-of-the-box solutions and content in Microsoft Sentinel.

In the Content hub, filter by categories and other parameters, or use the powerful text search, to find the content that works best for your organization's needs. The Content hub also indicates the support model applied to each piece of content, as some content is maintained by Microsoft and others are maintained by partners or the community.

Manage updates for out-of-the-box content via the Microsoft Sentinel Content hub, and for custom content via the Repositories page.

Customize out-of-the-box content for your own needs, or create custom content, including analytics rules, hunting queries, notebooks, workbooks, and more. Manage your custom content directly in your Microsoft Sentinel workspace, via the Microsoft Sentinel API, or in your own source control repository, via the Microsoft Sentinel Repositories page.

## Solutions

Microsoft Sentinel solutions are packaged content or integrations that deliver end-to-end product value for one or more domain or vertical scenarios.

The solutions experience is powered by Azure Marketplace for solutions’ discoverability and deployment.

Microsoft Sentinel solutions provide in-product discoverability, single-step deployment, and enablement of end-to-end product, domain, and/or vertical scenarios in Microsoft Sentinel. This experience is powered by for solutions’ discoverability, deployment, and enablement, and by for solutions’ authoring and publishing.

- **Packaged content** are collections of one or more pieces of Microsoft Sentinel content, such as data connectors, workbooks, analytics rules, playbooks, hunting queries, watchlists, parsers, and more.
    
- **Integrations** include services or tools built using Microsoft Sentinel or Azure Log Analytics APIs that support integrations between Azure and existing customer applications, or migrate data, queries, and more, from those applications into Microsoft Sentinel.
    

You can also use solutions to install packages of out-of-the-box content in a single step, where the content is often ready to use immediately. Providers and partners can use solutions to productize investments by delivering combined product, domain, or vertical value.

Use the Content hub to centrally discover and deploy solutions and out-of-the-box content in a scenario-driven manner.

### Find a solution

- From the Microsoft Sentinel navigation menu, under Content management, select Content hub.
    
- The Content hub page displays a searchable and filterable grid of solutions.
    
- Filter the list displayed, either by selecting specific values from the filters, or entering any part of a solution name or description in the Search field.
    
    Each solution in the grid shows the categories applied to the solution, and types of content included in the solution.
    
    For example, in the Cisco Umbrella solution shows a category of Security - Others, and that this solution includes 10 analytics rules, 11 hunting queries, a parser, three playbooks, and more.
    

## Install or update a solution

- In the content hub, select a solution to view more information on the right. Then select Install, or Update, if you need updates. For example:
    
- On the solution details page, select Create or Update to start the solution wizard. On the wizard's Basics tab, enter the subscription, resource group, and workspace to which you want to deploy the solution.
    
- Select Next to cycle through the remaining tabs (corresponding to the components included in the solution), where you can learn about, and in some cases configure, each of the content components.
    
- Finally, in the Review + create tab, wait for the Validation Passed message, then select Create or Update to deploy the solution. You can also select the Download a template for automation link to deploy the solution as code.
# Use repositories for deployment



When creating custom content, you can store and manage it in your own Microsoft Sentinel workspaces, or an external source control repository, including GitHub and Azure DevOps repositories. Managing your content in an external repository allows you to make updates to that content outside of Microsoft Sentinel, and have it automatically deployed to your workspaces.

## Prerequisites and scope

Before connecting your Microsoft Sentinel workspace to an external source control repository, make sure that you have:

- Access to a GitHub or Azure DevOps repository, with any custom content files you want to deploy to your workspaces, in relevant Azure Resource Manager (ARM) templates.
    
    Microsoft Sentinel currently supports connections only with GitHub and Azure DevOps repositories.
    
- An Owner role in the resource group that contains your Microsoft Sentinel workspace. This role is required to create the connection between Microsoft Sentinel and your source control repository. If you're unable to use the Owner role in your environment, you can instead use the combination of User Access Administrator and Sentinel Contributor roles to create the connection.
    

## Maximum connections and deployments

Each Microsoft Sentinel workspace is currently limited to five connections.

Each Azure resource group is limited to 800 deployments in its deployment history. If you have a high volume of ARM template deployments in your resource group(s), you may see a Deployment QuotaExceeded error.

## Validate your content

Deploying content to Microsoft Sentinel via a repository connection doesn't validate that content other than verifying that the data is in the correct ARM template format.

We recommend that you validate your content templates using your regular validation process. You can use the Microsoft Sentinel GitHub validation process and tools to set up your own validation process.

## Connect a repository

This procedure describes how to connect a GitHub or Azure DevOps repository to your Microsoft Sentinel workspace, where you can save and manage your custom content, instead of in Microsoft Sentinel.

Each connection can support multiple types of custom content, including analytics rules, automation rules, hunting queries, parsers, playbooks, and workbooks. For more information, see About Microsoft Sentinel content and solutions.

To create your connection:

- Make sure that you're signed into your source control app with the credentials you want to use for your connection. If you're currently signed in using different credentials, sign out first.
    
- In Microsoft Sentinel, on the left under Content management, select Repositories.
    
- Select Add new, and then, on the Create a new connection page, enter a meaningful name and description for your connection.
    
- From the Source Control dropdown, select the type of repository you want to connect to, and then select Authorize.
    
- Select one of the following tabs, depending on your connection type:
    

### GitHub

- Enter your GitHub credentials when prompted.
    
    The first time you add a connection, you see a new browser window or tab, prompting you to authorize the connection to Microsoft Sentinel. If you're already logged into your GitHub account on the same browser, your GitHub credentials are auto-populated.
    
- A Repository area now shows on the Create a new connection page, where you can select an existing repository to connect to. Select your repository from the list, and then select Add repository.
    
    The first time you connect to a specific repository, you see a new browser window or tab, prompting you to install the Azure-Sentinel app on your repository. If you have multiple repositories, select the ones where you want to install the Azure-Sentinel app, and install it.
    
    You are directed to GitHub to continue the app installation.
    
- After the Azure-Sentinel app is installed in your repository, the Branch dropdown in the Create a new connection page is populated with your branches. Select the branch you want to connect to your Microsoft Sentinel workspace.
    
- From the Content Types dropdown, select the type of content you are deploying.
    
    - Both parsers and hunting queries use the Saved Searches API to deploy content to Microsoft Sentinel. If you select one of these content types, and also have content of the other type in your branch, both content types are deployed.
        
    - For all other content types, selecting a content type in the Create a new connection pane deploys only that content to Microsoft Sentinel. Content of other types isn't deployed.
        
- Select Create to create your connection.
    

After the connection is created, a new workflow or pipeline is generated in your repository, and the content stored in your repository is deployed to your Microsoft Sentinel workspace.

The deployment time may vary depending on the volume of content that you're deploying.

### Azure DevOps

- You're automatically authorized to Azure DevOps using your current Azure credentials. To ensure valid connectivity, verify that you've authorized to the same Azure DevOps organization that you're connecting to from Microsoft Sentinel, or use an InPrivate browser window to create your connection.
    
- In Microsoft Sentinel, from the dropdown lists that appear, select your Organization, Project, Repository, Branch, and Content Types.
    
    - Both parsers and hunting queries use the Saved Searches API to deploy content to Microsoft Sentinel. If you select one of these content types, and also have content of the other type in your branch, both content types are deployed.
        
    - For all other content types, selecting a content type in the Create a new connection pane deploys only that content to Microsoft Sentinel. Content of other types isn't deployed.
        
- Select Create to create your connection. For example:
    

After the connection is created, a new workflow or pipeline is generated in your repository, and the content stored in your repository is deployed to your Microsoft Sentinel workspace.

The deployment time may vary depending on the volume of content that you're deploying.

![[Pasted image 20261008193938.png]]

# Summary and resources


By the end of this module, you're able to manage _content_ in Microsoft Sentinel.

You should now be able to:

- Install a content hub solution in Microsoft Sentinel
- Connect a GitHub repository to Microsoft Sentinel