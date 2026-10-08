
# Introduction
Microsoft Security Copilot is accessible directly from some Microsoft security products. This solution is referred to as the embedded experience. Copilot is embedded with Microsoft Defender XDR, Microsoft Purview, Microsoft Entra, Microsoft Intune, Microsoft Defender for Cloud, and other Microsoft security solutions.

The Microsoft solution in which the Copilot capabilities are embedded determines the scenarios that are available through the embedded experiences. For example, in Microsoft Purview Communication Compliance, Copilot can provide a summary of a message and its attachments, in the context of the policy and classifier conditions that flagged the message.

In the standalone experience, Copilot does some processing to determine which of its many capabilities is best suited to respond to your prompt. In the embedded experience, because Copilot is available in the specific product, Copilot is able to invoke the product specific capabilities directly, providing processing efficiency.

The embedded experience is also a great place to start a security investigation. For example, as an analyst using Microsoft Defender XDR, you're likely to spend a good amount time in the incidents page. From the incident page, you can select an alert and immediately get a summary of that incident. Depending on what you learn you might determine that a deeper investigation is needed. In this scenario, you can easily transition to the standalone experience to pursue a more detailed, cross product investigation that brings to bear all the Copilot capabilities enabled for your role.

In this module, you learn about the scenarios supported by the embedded experiences of Microsoft Security Copilot.

 Note

This module is intended to give you a flavor of just a few of the Security Copilot embedded experiences. The list of Microsoft Security solutions in which Copilot is embedded is continually growing. For information about Copilot embedded in a given security solutions, refer to training for that specific solution.

After completing this module, you'll be able to:

- Describe Copilot in Microsoft Defender XDR.
- Describe Copilot in Microsoft Purview.
- Describe Copilot in Microsoft Entra.
- Describe Copilot in Microsoft Intune.
- Describe Copilot in Microsoft Defender for Cloud.
# Describe Copilot in Microsoft Defender XDR

Microsoft Security Copilot is embedded in the Microsoft Defender portal to enable security teams to quickly and efficiently investigate and respond to incidents, hunt for threats, and protect their organization with relevant threat intelligence.

The brief video that follows shows a few of the Copilot capabilities embedded in Microsoft Defender and how they can help security analysts be more productive.

 Note

The list of Copilot capabilities embedded in Microsoft Defender is continually growing. This unit provides just a sampling of some of those Copilot capabilities. For more information, see the documentation on Microsoft Security Copilot in Microsoft Defender.

There are also some options that are common across all these features, including the ability to provide feedback on prompt responses and seamlessly moving to the standalone experience.

As described in the introduction unit, in the embedded experience Copilot is able to invoke the product specific capabilities directly, providing processing efficiency. To ensure access to these Microsoft Security Copilot features, the Microsoft Defender XDR plugin needs to be enabled and this is done through the standalone experience. To learn more, refer to [Describe the features available in the standalone experience of Microsoft Security Copilot](https://learn.microsoft.com/en-us/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience).

[![Screen capture of the Manage plugins window that highlights the Microsoft Defender XDR plugin.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/manage-plugins-microsoft-defender-xdr.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/manage-plugins-microsoft-defender-xdr.png#lightbox)

### Summarize incidents

Copilot automatically creates a summary when you navigate to an incident's page, providing an overview of the attack containing essential information including what transpired, what assets are involved, the timeline of the attack, indicators of compromise (IOCs), and the names of threat actors involved. ==Incidents== containing up ==to 100 alerts== can be summarized into ==one incident summary==.

[![Screen capture of Security Copilot embedded experience in Microsoft Defender XDR, showing an incident summary.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-incident-summary-v5.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-incident-summary-v5.png#lightbox)

Copilot also suggests follow-up prompts about related identities, devices, and IP addresses to help you understand the assets involved and how to act.

### Guided responses

Copilot uses AI and machine learning to contextualize an incident and learn from previous investigations to generate appropriate response actions. Guided responses recommend actions in the following categories:

- **Triage** - includes a recommendation to classify incidents as informational, true positive, or false positive.
- **Containment** - includes recommended actions to contain an incident.
- **Investigation** - includes recommended actions for further investigation.
- **Remediation** - includes recommended response actions to apply to specific entities involved in an incident.

[![Screen capture showing the information included in a guided response.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-guided-responses-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-guided-responses-v2.png#lightbox)

Each card contains information about the recommended action, including why the action is recommended. Administrators can also upload organization-specific response guidelines to tailor the recommendations to their environment. Guided responses are available for incident types such as phishing, business email compromise, and ransomware.

### Script and command-line analysis

Sophisticated attacks commonly evade detection by using obfuscated scripts and command lines. The script analysis capability enables security teams to inspect scripts and code without using external tools, quickly assessing whether a script is malicious or benign.

[![Screen capture showing the option to analyze a PowerShell script.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-analyze-script-v4b.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-analyze-script-v4b.png#lightbox)

Copilot analyzes the script and displays the results in a script analysis card, including a plain-language explanation of what the script does, whether it's malicious, and which MITRE ATT&CK techniques it employs. Users can select Show code to see specific lines of code related to the analysis. You can access script analysis in the alert timeline within an incident, for a timeline entry consisting of script or code.

[![Screen capture showing the lines of code related to the script analysis.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-script-analysis-show-code-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-script-analysis-show-code-v2.png#lightbox)

 Note

Script analysis functions are continuously in development. Analysis of scripts in languages other than PowerShell, batch, and bash are being evaluated.

### Generate KQL queries

Copilot in Microsoft Defender includes a query assistant capability in advanced hunting that converts natural-language questions into ready-to-run KQL queries. This feature reduces the time it takes to write a hunting query from scratch, enabling threat hunters and security analysts to focus on hunting and investigating threats.

[![Screen capture showing the KQL query generated from a natural language request.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-advanced-hunting-query-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-advanced-hunting-query-v2.png#lightbox)

Using the prompt bar, analysts can ask for a threat hunting query using natural language, such as "Give me all the devices that signed in within the last 10 minutes." The generated query can then be run automatically, added to the query editor for further tweaks, or copied for use elsewhere.

### Create incident reports

Copilot enables security teams to instantly create an extensive incident report within the portal. While an incident summary provides an overview of what happened, an incident report consolidates incident information from various data sources available in Microsoft Sentinel and Microsoft Defender XDR.

The incident report includes timestamps for key management actions, the analysts involved, incident classification with analyst comments, investigation and remediation actions (both manual and automated including Microsoft Sentinel playbooks), and follow-up actions noted by analysts.

[![Screen capture showing the generated incident report and the drop-down menu of options available by selecting the ellipses.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-incident-report-output.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/xdr-incident-report-output.png#lightbox)

### Analyze files

Copilot enables security teams to quickly identify malicious and suspicious files through AI-powered file analysis capabilities. When an analyst opens a file page, Copilot can generate a summary that includes detection information, related file certificates, a list of API calls, and strings found in the file. Files can be accessed from an incident's evidence and response tab, the incident graph, or the search feature.

- [Select file to analyze](https://learn.microsoft.com/en-gb/training/modules/security-copilot-embedded-experiences/2-copilot-for-defender?tabs=select-file-to-analyze%2Cdevice-summary#tabpanel_1_select-file-to-analyze)
- [File analysis](https://learn.microsoft.com/en-gb/training/modules/security-copilot-embedded-experiences/2-copilot-for-defender?tabs=select-file-to-analyze%2Cdevice-summary#tabpanel_1_file-analysis)

[![Screen capture showing the incident graph of an incident, with files highlighted.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-xdr-files-v3.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-xdr-files-v3.png#lightbox)

### Summarize devices and identities

Copilot in Defender can generate summaries for devices and identities to help security teams quickly assess their security posture during an investigation.

**Device summaries** include the device's security posture with information about the status of protection capabilities such as attack surface reduction and tamper protection, any unusual user activity, a list of vulnerable software, firewall settings, and relevant Microsoft Intune information.

**Identity summaries** provide a contextual overview of a user identity, including account creation date, criticality level, role and role changes, sign-in behaviors and patterns, authentication methods, risks from Microsoft Entra ID, and contact information.

- [Device summary](https://learn.microsoft.com/en-gb/training/modules/security-copilot-embedded-experiences/2-copilot-for-defender?tabs=select-file-to-analyze%2Cdevice-summary#tabpanel_2_device-summary)
- [Identity summary](https://learn.microsoft.com/en-gb/training/modules/security-copilot-embedded-experiences/2-copilot-for-defender?tabs=select-file-to-analyze%2Cdevice-summary#tabpanel_2_identity-summary)

[![Screen capture showing the device summary from Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/device-summary.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/device-summary.png#lightbox)

### Threat intelligence

Copilot is embedded in the threat intelligence section of the Microsoft Defender portal, helping security teams make informed decisions by consolidating and summarizing threat intelligence data. You can ask Copilot to summarize the relevant threats impacting your environment, prioritize threats based on your organization's exposure levels, or find threat actors that might be targeting your industry. Copilot uses the Microsoft Defender Threat Intelligence plugin to surface summaries of threat analytics reports, intel profiles, and vulnerability disclosures—all in natural language.

### Common functionality across key features

There are some options that are common across the features of Copilot for Microsoft Defender.

#### Providing feedback

As with the standalone experience, the embedded experience provides users a mechanism to provide feedback on the accuracy of the AI-generated response. For any AI-generated content, you can select the feedback prompt on the bottom right of the content window and select from the available options.

[![Screen capture of the feedback icon for AI generated content and the three options. The options are confirmed, it looks great, off target, inaccurate, and potentially harmful, inappropriate.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/verify-for-accuracy-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/verify-for-accuracy-v2.png#lightbox)

#### Move to the standalone experience

Investigators who start in the Defender portal can easily transition to the standalone experience for a more detailed, cross-product investigation that brings to bear all the Copilot capabilities enabled for their role. To move to the standalone experience, select the ellipses within the generated content window then choose Open in Security Copilot.

[![Screen capture showing the option to open in Security Copilot, which is available by selecting the ellipses in the AI generated content window.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/switch-to-standalone-experience.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/switch-to-standalone-experience.png#lightbox)

# Copilot in Microsoft Purview
Microsoft Security Copilot is accessible from within Microsoft Purview solutions as part of the embedded experience. With Copilot in Microsoft Purview, data security and compliance admins can use the power of AI to assess risk exposure, summarize alerts, investigate user activities, and gain insights into policies—directly from within Microsoft Purview solutions.

You can open Security Copilot in Microsoft Purview by selecting the **Copilot** icon in the top navigation bar. It's available across all Microsoft Purview solutions.

 Note

The list of Copilot capabilities embedded in Microsoft Purview is continually growing. This unit provides just a sampling of those capabilities. For more information, see the documentation on Security Copilot in Microsoft Purview.

### Getting started

For all use cases supported through the embedded experience, your organization must be onboarded to Security Copilot, the Microsoft Purview plugin must be enabled, and your organization must be licensed and onboarded to the applicable Microsoft Purview solutions. To enable the Microsoft Purview plugin, the option to allow Security Copilot to access data from your Microsoft 365 services must be enabled as part of the owner plugin settings.

[![Screen capture of the setting to allow Security Copilot to access data from your Microsoft 365 services, which is required to enable the Microsoft Purview plugin.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/purview-plugin-requirement-new.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/purview-plugin-requirement-new.png#lightbox)

Users must have the appropriate role permissions for both Copilot and the Purview solutions. For ==Copilot==, users need, ==at a minimum, the Copilot workspace contributor role or the Microsoft Entra Security operator role==. For Microsoft Purview, Copilot assumes the permissions of the user when it tries to access data, so you ==need the required permissions== for the specific Purview solution you're working with.

The embedded experience in Microsoft Purview supports scenarios across the following solutions:

- Data Security Posture Management (DSPM)
- Data Loss Prevention (DLP)
- Insider Risk Management
- Communication Compliance
- eDiscovery

### Data Security Posture Management

Data Security Posture Management (DSPM) integrates with Security Copilot to help you quickly explore details and get answers about unprotected sensitive data assets and potentially risky user activities. Data security insights come from scanned data across DLP, Information Protection, and Insider Risk Management solutions.

DSPM provides built-in promptbooks—sequences of prompts that automatically run in order—to help you investigate risky users and protect sensitive data. The **Risky user investigation** promptbook helps you investigate a specific user's sensitive data activities, anomalies, exfiltration patterns, and related alerts. The **Sensitive data protection** promptbook helps you identify where specific types of sensitive data are stored, how that data has been transferred, and how to prevent unauthorized transfers.

DSPM also offers a prompt gallery with built-in prompts organized into categories such as alerts and policies, data at risk, potentially risky users, potentially suspicious activity, and sensitive data. You can customize these prompts or run them directly in Copilot.

### Data Loss Prevention

Security Copilot helps data security teams manage the volume of DLP alerts they receive daily. From the DLP alerts queue, you can select an alert and have Copilot generate a comprehensive summary that accelerates your investigation.

[![Screen capture of the Microsoft Purview DLP alerts page showing the details for a specific alert and the option to get a summary from Security Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/purview-data-loss-prevention-alert-summary.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/purview-data-loss-prevention-alert-summary.png#lightbox)

From the alert summary, you can copy the response to clipboard, regenerate, or transition to the standalone experience by selecting Open in Security Copilot.

[![Screen capture of the Microsoft Purview DLP alert summary and the options available. Options include copy to clipboard, regenerate, and open in Security Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/purview-data-loss-prevention-alert-summary-ellipses-v4.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/purview-data-loss-prevention-alert-summary-ellipses-v4.png#lightbox)

Beyond alert summaries, Copilot can also help you understand what your DLP policies are doing in your organization and where they're active, providing insights into policy configurations and effectiveness.

### Insider Risk Management

Copilot in Insider Risk Management enables you to quickly gain the highlights of a potential incident by summarizing alerts. The summary identifies critical user details like exfiltration activities, patterns, user roles, and unusual activities that might lead to potential security incidents.

[![Screen capture of an Insider Risk Management alerts page that shows the option to summarize an alert.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/copilot-insider-risk-management-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/copilot-insider-risk-management-v2.png#lightbox)

From the alerts queue, select the alert you want to review and select Summarize to have Copilot generate the alert summary. From the summary, you can copy the response to clipboard, regenerate, or open it in the standalone Copilot experience.

[![Screen capture of an Insider Risk Management alert summary generated by Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/copilot-insider-risk-management-summary.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/copilot-insider-risk-management-summary.png#lightbox)

Copilot can also summarize user activities in Insider Risk Management, helping you understand a user's risk profile and activity patterns across a specified time period.

### Activity explorer

Security Copilot is embedded in the activity explorer to help you efficiently drill down into activity data and identify activities, files with sensitive information, users, and other details that are relevant to an investigation. You can use natural language prompts to explore top activities, filter and investigate specific activities, or find files used in specific activities.

Activity explorer also supports natural language to filter set generation. You can enter complex natural language queries—for example, "Filter and investigate files copied to cloud with sensitive info type credit card number for past 30 days"—and Copilot generates a filter set that you can review and apply to the data.

### Communication Compliance

Reviewing communications is an integral part of protecting your organization's communication landscape, but it can be time-consuming to review lengthy content and attachments. Copilot in Communication Compliance provides contextual summaries of messages and their attachments in the context of the classifier conditions that flagged the message. You can also ask follow-up contextual questions to dig deeper into the summary.

[![Screen capture of a Communication Compliance policy alerts page and the Copilot summary for the policy alerts.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/copilot-communication-compliance-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/copilot-communication-compliance-v2.png#lightbox)

Contextual summarization currently supports trainable classifiers as context and is only available for ==messages and attachments with a combined length of 100 words or more==. To get contextual summaries, you must have the ==Communication Compliance or Communication Compliance Investigator role.==

[![Screen capture showing more default prompts and the prompt bar to enable the user to learn more about the message that triggered the policy.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/copilot-communication-compliance-follow-up.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/copilot-communication-compliance-follow-up.png#lightbox)

### eDiscovery

Copilot embedded with Microsoft Purview eDiscovery helps admins and managers optimize the time spent reviewing evidence collected in review sets. Copilot can generate a contextual summary of a single item in a review set and you can ask follow-up contextual questions about the summary. ==Contextual summary is supported only for file types with text extraction support.==

[![Screen capture of the context generated by Copilot for an item in a review set of Microsoft Purview eDiscovery.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/purview-ediscovery-context-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/purview-ediscovery-context-v2.png#lightbox)

eDiscovery also supports natural language search to help you find relevant content across your cases, and Copilot can generate case summaries to help you quickly understand the scope and key details of eDiscovery cases.

### Feedback

For any AI-generated content, you can provide feedback on the accuracy of the response. Select the feedback prompt on the bottom right of the content window and select from the available options: confirmed, it looks great; off target, inaccurate; or potentially harmful, inappropriate.

[![Screen capture of the feedback options. The options are: confirmed, it looks great, off target, inaccurate, or potentially harmful, inappropriate.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/ai-accuracy-feedback-data-loss-prevention-summary.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/ai-accuracy-feedback-data-loss-prevention-summary.png#lightbox)

# Copilot in Microsoft Entra
[[Microsoft Entra]] is one of the Microsoft plugins that enable the Security Copilot platform to generate accurate and relevant information. Through this plugin, Security Copilot can help you investigate and resolve== identity risks==, assess identities and access with AI-driven intelligence, and complete complex tasks quickly. Security Copilot gets insights from your Microsoft Entra users, groups, sign-in logs, audit logs, and more, while also providing contextualized insights and recommendations in security best practices.

 Note

The list of Copilot capabilities embedded in Microsoft Entra is continually growing. This unit provides just a sampling of those capabilities. For more information, see the documentation on Security Copilot in Microsoft Entra.

### Getting started

Before you use Copilot in Microsoft Entra, your organization must be onboarded to Security Copilot, the Microsoft Entra plugin must be enabled, and users must have the appropriate role permissions. Copilot assumes the permissions of the current user when it tries to access data, so you need the required roles to access the relevant Microsoft Entra data.

Security Copilot is accessible in the Microsoft Entra admin center through a ==globally available button in the menu bar==. You can choose from a set of starter prompts that appear at the top of the Security Copilot window or enter your own natural language queries in the prompt bar. Suggested prompts, which can appear after a response, are predefined prompts that Security Copilot selects based on the prior response.

Security Copilot scenarios in Microsoft Entra span multiple product areas, each covering specific use cases for identity security and administration:

- **Microsoft Entra ID** – Enterprise user management, ==sign-in and audit log analysis, Conditional Access evaluation, and more.==
- **Microsoft Entra ID Protection** –== Risky user investigation and application risk assessment==.
- **Microsoft Entra ID ==Governance==** – Access reviews, entitlement ==management==, Privileged Identity Management (PIM), and lifecycle workflows.
- **Microsoft Entra Internet Access and Private Access** – Global Secure Access== network traffic analysis==.

### Microsoft Entra ID scenarios

Microsoft Entra ID is the foundational product of Microsoft Entra, and provides the ==essential identity, authentication, policy, and protection to secure users, devices, apps, and resources==. Security Copilot enhances these capabilities across multiple areas:

- **Enterprise user management**: Quickly retrieve and investigate user, group, domain, and license information using natural language. For example, you can ask Copilot to list all users in a specific department, identify ownerless groups, or check the licenses assigned to your tenant.
- **Sign-in and audit log analysis**: Investigate sign-in failures and suspicious activity by querying sign-in logs, audit logs, and provisioning logs. For example, you can ask Copilot for sign-in logs for a specific user over the past 48 hours or audit logs in table format.
- **Conditional Access**: Understand and evaluate Conditional Access policies using natural language prompts. Copilot helps you find gaps in access policies and troubleshoot policy configurations faster.
- **Authentication**: Discover enabled authentication methods, registration status, and overall authentication strategy for your tenant or specific users.
- **Roles and administrators**: Investigate role assignments within your directory to ensure proper role-based access control.
- **Recommendations and health monitoring**: Get insights from Microsoft Entra recommendations and health monitoring alerts to proactively improve your security posture.
- **Devices**: Explore device details and compliance status registered in Microsoft Entra.

### Microsoft Entra ID Protection scenarios

Microsoft Entra ID Protection focuses on identity risk detection and remediation. Security Copilot provides AI-powered insights for:

- **Risky user investigation**: Security Copilot summarizes a user's risk level, provides insights relevant to the incident at hand, and provides recommendations for rapid mitigation. This helps reduce the time to resolution by giving IT admins and SOC analysts the right context to investigate and remediate identity risk incidents.
    
    [![Screen capture showing the Copilot generated summary of a risky user.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/entra-risky-users-summarize-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/entra-risky-users-summarize-v2.png#lightbox)
    
    You can use natural language prompts to list or identify users based on risk, get user-specific risk information, and review user risk history.
    
- **Application risk assessment**: Identity admins and security analysts can assess risk from workload identities by using natural language prompts. By using prompts like "List risky app details for my tenant," you can discover permissions granted (especially high privileged permissions), unused apps, apps from outside your tenant, and the risk level of applications. App risk starter prompts appear in application-related admin center blades such as **Enterprise apps**, **App Registrations**, and **Identity Protection Risky workload identities**.
    

### Microsoft Entra ID Governance scenarios

Microsoft Entra ID Governance helps you manage identity lifecycle and access governance at scale. Security Copilot enhances these capabilities in the following areas:

- **Access reviews**: Extract and analyze access review data using natural language. You can understand who approved access, identify reviewers who took no decisions, and investigate overrides of AI recommendations.
- **Entitlement management
Interact with entitlement management (**who gets access to what, for how long, and under which conditions**) data to query access packages, policies, connected organizations, and catalog resources without custom scripting.
- **Privileged Identity Management (PIM)**: Monitor and manage privileged access using natural language queries. You can get insights into just-in-time role assignments, track changes, and rapidly respond to potential risks. PIM write actions also allow you to activate the least-privileged role needed for a task directly within a Copilot conversation, without manually navigating away.
- **Lifecycle workflows**: Configure custom workflows to manage the lifecycle of users across joiner, mover, and leaver (JML) scenarios. Copilot helps you create step-by-step guidance for new workflows, explore available configurations, analyze the active workflow list, troubleshoot workflow runs, and compare workflow versions.

### Microsoft Entra Internet Access and Private Access scenarios

Security Copilot integrates with Global Secure Access to enable network traffic analysis using natural language queries. Network administrators and security teams can analyze user, device, and branch network usage, identify network issues, and detect threats or policy violations in real time. Use cases include monitoring data consumption and bandwidth usage, investigating blocked traffic and security threats, analyzing user application access patterns, and monitoring cross-tenant access and external connections.

### Data exploration

Security Copilot supports a data exploration feature for Microsoft Entra scenarios. When prompts return datasets with more than 10 items, you can select **Open list** from the Copilot chat response to access a comprehensive data grid. This allows you to explore large datasets with complete and accurate results for more efficient decision-making. Each data grid displays the underlying Microsoft Graph URL, helping you verify query accuracy.

### Feedback

Copilot in Microsoft Entra uses AI and machine learning to process data and generate responses. However, ==AI-generated content might be incorrect. ==Your feedback on generated responses helps improve the accuracy of Copilot over time. All key features include an option for providing feedback through thumbs up and thumbs down icons.

[![Screen capture showing the feedback menu.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/entra-feedback.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/entra-feedback.png#lightbox)

# Copilot in Microsoft Intune
Microsoft Intune has capabilities that are powered by Microsoft Security Copilot. These capabilities access your Intune data and can help you manage your policies and settings, understand your security posture, and troubleshoot device issues, including Windows 365 Cloud PCs.

Access to your Intune data is supported through the standalone Security Copilot experience or embedded within the Intune admin center, referred to as Copilot in Intune. This unit focuses on the embedded experience.

 Note

The list of Copilot capabilities embedded in Microsoft Intune is continually growing. This unit provides just a sampling of those capabilities. For more information, see the documentation on Microsoft Copilot in Intune.

### Before you begin

To use Copilot in Intune, Security Copilot must be configured, the Microsoft Intune plugin must be enabled in Security Copilot, and you need the appropriate role permissions. ==Copilot in Intune is included with Security Copilot—there are no other licensing requirements or Intune-specific licenses needed.==

==Access to Copilot in Intune is managed through Security Copilot or Microsoft Entra ID==. ==The **Intune Administrator** role in Microsoft Entra ID has access to Copilot in Intune by default==. Other roles can be assigned access through Security Copilot. There ==isn't a built-in Intune role== that includes access to Copilot.

[![Screen capture showing the Microsoft Intune plugin enabled.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/intune-plugin.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/intune-plugin.png#lightbox)

Copilot uses your Intune data. When an admin submits a prompt, Copilot can only access the data that the admin has permissions to, which includes the RBAC roles and scope tags assigned to them. You can also check the status of Copilot in Intune from the Intune admin center under **Tenant administration** > **Copilot**.

[![Screen capture of Intune admin portal showing that Copilot in Intune is enabled.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/copilot-in-intune-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/copilot-in-intune-v2.png#lightbox)

To use Copilot in Intune for Windows 365 Cloud PCs, you must also enable the **Windows 365** plugin in Security Copilot.

### Copilot in Intune

To access Copilot in Intune, sign into the Intune admin center and select the **Copilot** button in the banner at the top. Copilot Chat opens, where you can use natural language to ask questions. An intelligent search matches your request to available prompts built into Intune, which are offered as dynamic suggestions that update as you type.

The prompt suggestions are organized into three sections:

- **Suggestions** – Prompts specific to Intune scenarios, such as device troubleshooting, policy and setting management, Surface device troubleshooting, and Windows 365 Cloud PC insights.
- **Explore your data** – Prompts for querying and exploring your Intune data. Results might include an **Explore further** option that redirects you to the data explorer with your prompt already filled out.
- **Check documentation** – Allows you to ask a question directly to the Microsoft documentation.

Copilot in Intune supports the following scenarios:

- Data exploration using natural language
- Policy and setting management
- Device details and troubleshooting
- Device query
- Analyzing Endpoint Privilege Management (EPM) requests
- Troubleshooting Microsoft Surface devices
- Gaining insights about Windows 365 Cloud PCs

#### Policy and setting management

Copilot is embedded in policy settings and with your existing policies, on the following policy types in Intune:

- Compliance policies
- Device configuration policies, including the settings catalog
- Most endpoint security policies

When you create a new policy, you can use Copilot to learn more about individual settings, their impact, and recommended values through the Copilot tooltips that appear next to each setting. Selecting the Copilot icon displays detailed information about that setting, including whether it's been configured in other policies, Microsoft's recommended value, and how the setting could affect users or security.

[![Screen capture of Copilot in Intune tool tip icon for a setting and the information Copilot generates for that setting.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/intune-copilot-settings-tooltip-preview-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/intune-copilot-settings-tooltip-preview-v2.png#lightbox)

From an existing policy, you can use Copilot to summarize the policy. The summary describes what the policy does, the users and groups assigned to the policy, and the settings in the policy. This feature can help you understand the impact of a policy and its settings on your users and devices. For compliance policies, Copilot can also help identify policies that have conflicting settings.

[![Screen capture of Copilot in Intune showing a summary for a device policy and the available prompts.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/intune-policy-summarize.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/intune-policy-summarize.png#lightbox)

Whether you're learning about settings for a new policy or summarizing an existing policy, the Copilot window provides more prompts that you can use. You can also select the prompt guide icon on the bottom right and select from an existing list of prompts.

[![Screen capture of Copilot in Intune prompt guide icon and the available prompts.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/intune-prompt-guide.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/intune-prompt-guide.png#lightbox)

#### Device details and troubleshooting

You can use Copilot to get device-specific information, like the installed apps, group membership, and other information that can help troubleshoot a device.

[![Screen capture of Copilot in Intune device summary, showing prompts that provide device specific information and can help in troubleshooting.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/intune-copilot-device-summary-troubleshooting.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/intune-copilot-device-summary-troubleshooting.png#lightbox)

Prompts include summarizing a device, analyzing an error code, comparing a device with another device, showing apps or policies on a device, showing group memberships, and showing the primary user. You can also use the error analyzer prompt to enter an error code, get more information about the error, and get a possible resolution.

#### Data exploration

Using natural language, you can query and explore your Intune data, including data about your devices, users, apps, policies, updates, and compliance. Copilot summarizes the results and recommends actions you can take based on the query results. You can also use the query output to add users or devices to groups, and create custom reports.

#### Device query

You can use Copilot to help you create Kusto Query Language (KQL) queries to run when using device query in Intune. You can use this feature for an individual device or across many devices. In Copilot Chat, enter your question about the device and, if device query supports the properties needed, Copilot generates a KQL query that you can use, along with an explanation of how it created the query. Device query requires a license that includes Microsoft Intune Advanced Analytics.

#### Endpoint Privilege Management

Copilot can help you analyze Endpoint Privilege Management (EPM) elevation requests. When reviewing EPM requests, Copilot provides insights and context to help you make informed decisions about whether to approve or deny elevation requests.

#### Surface device troubleshooting

The Surface Management Portal in the Intune admin center integrates with Security Copilot, bringing AI-powered insights to IT teams managing Surface devices. This enables automated troubleshooting, proactive device management, and security-driven intelligence, helping administrators resolve issues faster and strengthen security postures.

#### Windows 365 Cloud PC insights

Copilot in Intune includes Windows 365 integrations that help IT administrators manage Cloud PCs. Key use cases include Cloud PC performance optimization through recommendations for resizing, user experience improvements by summarizing connectivity issues such as high latency or dropped connections, license optimization by identifying unused or underutilized Cloud PCs, and Cloud PC management assistance for diagnosing provisioning issues and Cloud PCs in grace period.

# Copilot in Microsoft Defender for Cloud

Microsoft Defender for Cloud integrates both Microsoft Security Copilot and Microsoft Copilot for Azure into its experience. These integrations allow you to ask security-related questions, receive responses, and automatically trigger the necessary skills to analyze, summarize, remediate, and delegate recommendations using natural language prompts.

 Note

The list of Copilot capabilities embedded in Microsoft Defender for Cloud is continually growing. This unit provides just a sampling of those capabilities. For more information, see the documentation on Microsoft Security Copilot in Defender for Cloud.

### How the integration works

Copilot in Defender for Cloud uses a ==dual-platform architecture==. When you enter a prompt in the Copilot interface, Copilot for Azure receives the prompt and evaluates it along with the active page to determine the skills needed. If the prompt is security related and a matching Security Copilot skill is available, Security Copilot executes the skill and sends the response back through Copilot for Azure for presentation. If the skill is unavailable, Copilot for Azure searches its own available skills to find the most relevant match and responds accordingly.

This distinction matters for SCU consumption. ==Only prompts that invoke Security Copilot skills consume Security Compute Units.== Prompts handled entirely by Copilot for Azure don't consume SCUs.

### Prerequisites

Copilot in Defender for Cloud is available for all users when you:

- Enable Defender for Cloud on your environment.
- Have access to Azure Copilot, which is available by default to all Azure portal users ==unless restricted by a Global Administrator==.
- Have Security Compute Units (SCUs) assigned for Security Copilot.

Copilot in Defender for Cloud doesn't rely on any of the available Defender for Cloud plans. However, to enjoy the full range of Copilot capabilities, enabling the Defender Cloud Security Posture Management (DCSPM) plan is recommended. The DCSPM plan includes extra security features such as attack path analysis and risk prioritization, all of which can be navigated and managed using Security Copilot. Without the DCSPM plan, you can still use Copilot in Defender for Cloud, but with limited capacity.

### Analyze recommendations

Copilot's integration with Defender for Cloud enables you to analyze all recommendations presented on the recommendations page using natural language prompts. From the recommendations page, selecting **Analyze with Copilot** opens the Copilot interface where you can use natural language prompts to narrow the scope of the recommendations and focus on specific areas of concern.

[![Screen capture of the recommendations page of Microsoft Defender for Cloud.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-recommendations.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-recommendations.png#lightbox)

Some sample prompts include:

- Show risks for publicly exposed resources
- Show risks for resources with sensitive data
- Show risks for critical resources

Copilot generates an initial analysis and you can filter the list of recommendations based on the results. You can further refine the results by selecting suggested follow-up prompts or entering prompts manually. The recommendations page updates with the appropriate filters applied based on the prompts you provided.

[![Screen capture of the recommendations analysis provided by Microsoft Defender for Cloud and the option to filter the list of recommendations.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defend-for-cloud-apply-filter.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defend-for-cloud-apply-filter.png#lightbox)

### Summarize recommendations

Once you select a specific recommendation, Copilot can summarize it to provide a quick, natural-language overview of the risks and vulnerabilities associated with that recommendation. The summary helps you understand the context and effect of the recommendation, enabling you to prioritize remediation efforts effectively.

By summarizing a recommendation, you gain insight into what the recommendation addresses, why it matters, and the potential impact of implementing it—all without having to interpret the technical details manually.

[![Screen capture of the recommendation summary generated by Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-summarize-recommendation.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-summarize-recommendation.png#lightbox)

Once you have a better understanding of the recommendation, you can decide how best to handle it. For example, you can ask Copilot to help remediate the recommendation, delegate the remediation to the resource owner, or enter other prompts as needed.

### Remediate recommendations

After summarizing a recommendation, Copilot can assist with remediation by providing step-by-step guidance to address the identified risk. Remediating recommendations with Copilot allows you to improve your security posture by directly addressing vulnerabilities in your environment.

When you ask Copilot to help with remediation, it provides suggested remediation information along with instructions. In some cases, a recommendation might include a script that can be run to apply the remediation directly.

[![Screen capture of a recommendation summary showing the option to run a script to remediate a recommendation.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-run-script.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-run-script.png#lightbox)

### Delegate recommendations

Copilot can also help you delegate recommendations to the appropriate person or team. Delegating recommendations ensures that the right people address the risks and vulnerabilities in your environment, improving overall security posture.

When you choose to delegate, Copilot drafts an email summarizing the recommendation and the suggested remediation actions. You can review the email, add recipients, and send it directly from the interface. Once delegated, you can monitor the progress of the remediation on Defender for Cloud's recommendations page.

[![Screen capture of the response Copilot generates when you select to delegate a recommendation to the resource owner.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-delegate-v2b.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-delegate-v2b.png#lightbox)

[![Screen capture of the email Copilot generates when you select to delegate a recommendation to the resource owner.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-delegate-email.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-delegate-email.png#lightbox)

### Remediate code

Copilot in Defender for Cloud can also help remediate Infrastructure as Code (IaC) misconfigurations discovered in your code repositories. This capability allows you to address security misconfigurations and vulnerabilities early in the development cycle by automatically generating pull requests (PRs) that correct the identified weaknesses.

This capability requires additional prerequisites beyond the standard Copilot requirements, including connecting your Azure DevOps environment to Defender for Cloud, configuring the Microsoft Security DevOps Azure DevOps extension, and meeting the DevOps security support and prerequisites requirements.

When a recommendation related to IaC scanning findings is identified, you can select **Reduce risk with Copilot** to have Copilot generate a code fix. Copilot identifies the relevant security check, generates a remediation, and creates a pull request in your code repository. A developer should then review and approve the PR before merging it into the code base.

[![Screen capture of a recommendation titled, Azure DevOps repositories should have infrastructure as code scanning findings resolved, and the option to reduce risk with Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-devops.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-devops.png#lightbox)

[![Screen capture showing Copilot's response to selecting Reduce risk with Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-security-check-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-embedded-experiences/media/defender-for-cloud-security-check-v2.png#lightbox)

### Providing feedback

As with other embedded experiences, Copilot in Defender for Cloud provides a mechanism to give feedback on the accuracy of AI-generated responses. After each completed prompt, you can select from available options including **Looks right** if the results are accurate, **Needs improvement** if the results are incomplete or incorrect, or **Inappropriate** if the results contain questionable information. Whenever possible, provide additional details to help improve future responses.
![[Pasted image 20260826113244.png]

![[Pasted image 20260826113355.png]]
![[Pasted image 20260826113407.png]]


# Experience Security Copilot through guided simulations
# Introduction
Microsoft Security Copilot is an AI-powered security analysis tool that helps analysts process security signals, investigate threats, and respond to incidents at machine speed. It integrates with Microsoft Security solutions you already use, including Microsoft Purview and Microsoft Defender XDR.

Imagine you're a security operations analyst at an organization that uses several Microsoft Security solutions. Your team handles everything from ==reviewing data protection alerts in Microsoft Purview== to investigating complex security incidents in Microsoft Defender XDR. With Security Copilot, you can accelerate these workflows using natural language prompts to summarize incidents, analyze activity patterns, and guide your investigations.

In this module, you explore Security Copilot capabilities through a series of interactive guides. You start by configuring owner settings and working with prompts and promptbooks in the standalone experience. You then move into embedded experiences in Microsoft Purview and Microsoft Defender XDR. In these experiences, Security Copilot assists with data protection investigations, insider risk analysis, compliance review, and security incident response.

# Explore owner settings in Security Copilot

As a [[Security Copilot owner]], you're responsible for configuring the settings that control how your team accesses and uses the environment. The owner settings define how access controls, integrations, and collaboration work across your Security Copilot workspace. Before your team begins using Security Copilot, you need to review and understand these configuration areas.

In this interactive guide, which takes approximately 10 minutes to complete, you navigate the Owner menu in Security Copilot and explore the key configuration areas. You review settings related to workspace management, access controls, and integrations that shape how Security Copilot operates across your environment. Every action you take as an owner applies to a specific workspace, so you also learn the importance of confirming you're in the correct workspace before making changes.


# Use prompts and promptbooks in Security Copilot

Prompts, plugins, and promptbooks are the core tools you use to interact with Security Copilot. A prompt is a natural language input—a question or instruction—that you enter in Security Copilot to perform a task. A promptbook is a curated collection of reusable prompts designed for common security scenarios, where each prompt builds on the previous one to automate investigation workflows. Plugins extend Security Copilot's capabilities by integrating with both Microsoft and non-Microsoft security solutions.

==Your interactions with Security Copilot support three key areas: threat investigation, troubleshooting and remediation, and security posture management.== As a Copilot contributor, you create sessions and use prompts and promptbooks to investigate and analyze security incidents. While the Copilot contributor role and enabled plugins allow integration with security solutions, they don't grant you additional permissions to view security data. Your ==Microsoft Entra and Azure role-based access control (RBAC) roles== determine what security data you can access in Security Copilot.

In this interactive guide, which takes approximately 10 minutes to complete, you complete three tasks:

- **Explore the prompt bar and manage sources**: Navigate the prompt bar options and configure the sources Security Copilot uses.
- **Run prompts and review Copilot responses**: Enter prompts and review the insights Security Copilot provides.
- **Run promptbooks and review or share results**: Execute a promptbook and learn how to review and share the investigation results.

# Create a custom promptbook in Security Copilot

When you repeatedly run the same prompts to investigate similar scenarios, you can save time by creating a custom promptbook. A custom promptbook lets you reuse prompts from a previous session, turning a one-time investigation into a repeatable workflow.

In this interactive guide, you create a custom promptbook in Security Copilot by reusing prompts from an earlier identity investigation session. The scenario involves a security analyst who regularly reviews failed sign-in attempts and authentication activity in Microsoft Entra. Rather than manually entering the same prompts each time, you save those prompts as a custom promptbook allowing you to reuse the workflow in future investigations.

# Investigate data protection activity in Microsoft Purview

Security Copilot integrates with Microsoft Purview to help you investigate data protection activity. In this unit, you work through two interactive guides that demonstrate how Security Copilot assists with monitoring sensitive data activity and investigating data loss prevention (DLP) alerts.

## Investigate sensitive activity in Activity explorer

Activity explorer in Microsoft Purview provides visibility into activity involving sensitive information across services such as SharePoint, OneDrive, and Exchange. When a data loss prevention policy detects activity that may involve sensitive content, you need to review the activity signals to identify potential policy matches or high-risk activity.

## Investigate a DLP alert

When a DLP alert is triggered—for example, after a file containing sensitive financial data is accessed and modified—you need to quickly understand the context and determine the appropriate response. Security Copilot surfaces alert context and insights to help you focus on what matters during a DLP investigation.

# Investigate insider risks and compliance in Microsoft Purview
Security Copilot also assists with investigating insider risks and compliance-related scenarios within Microsoft Purview. In this unit, you work through two interactive guides that cover insider risk alert investigation and the analysis of unlabeled sensitive content using eDiscovery.

## Investigate an insider risk alert

Insider Risk Management in Microsoft Purview helps detect and investigate potentially risky user activity within your organization. When an alert is triggered—for example, suspicious activity involving the copying of sensitive data to a USB device—you need to investigate the user's activity and determine whether sensitive data was shared outside the organization.

## Investigate unlabeled sensitive content using eDiscovery

Organizations preparing for cloud migrations or regulatory audits often need to identify documents that lack sensitivity labels. An eDiscovery content search can surface thousands of unlabeled documents, making it challenging to assess the scope of compliance risk.

# Investigate security incidents in Microsoft Defender XDR
Security Copilot integrates with Microsoft Defender XDR to help you investigate and respond to security incidents. In this unit, you work through two interactive guides that take you through a complete incident investigation workflow—from understanding incident context to analyzing specific artifacts and performing advanced investigation.

## Investigate incident context and activity

When a complex incident is identified in Microsoft Defender XDR—involving a compromised asset and dozens of alerts—it can be difficult to determine where the attack started and how it progressed. Security Copilot summarizes incident activity, connects related events, and provides guided responses to help you focus on what matters.
## Analyze artifacts and pivot to advanced investigation

After you understand the overall incident context, the next step is to analyze individual alerts and investigate specific artifacts. Security Copilot helps you examine alert details, review device and user context, and identify risks with recommended actions.

# Explore and create an agent in Security Copilot
Agents in Microsoft Security Copilot automate security tasks by integrating with Microsoft Security solutions and partner services. They can run automatically based on configured triggers or be run on demand with selected parameters. Agents exist for both the standalone and embedded experiences.

In this interactive guide, which takes approximately 10 minutes to complete, you complete two tasks:

- **Explore the Threat Intelligence Briefing Agent**: Review the agent's details, activity, and reports, and run it on demand to generate a threat intelligence briefing.
- **Create an agent in the standalone experience**: Build a new agent in Security Copilot's standalone experience to automate a security operations task.
# Explore the Conditional Access Optimization Agent

The Conditional Access Optimization Agent in Microsoft Security Copilot helps identity security teams analyze Conditional Access policies and recommend improvements. When new applications or user accounts are added to your environment, existing policies may not cover them effectively. The agent identifies these gaps and suggests optimizations.

In this interactive guide, which takes approximately 10 minutes to complete, you complete two tasks:

- **Navigate to the Conditional Access Optimization Agent and review its details**: Access the agent in the Microsoft Entra admin center and explore its configuration.
- **Review agent activity and suggestions**: Examine the agent's activity feed, review its suggestions, and analyze how Conditional Access policies apply to newly added users and applications.
![[Pasted image 20260826141125.png]]
![[Pasted image 20260826141318.png]]
# Summary
In this module, you explored how Microsoft Security Copilot enhances security operations workflows across both the standalone and embedded experiences. Through a series of interactive guides, you configured owner settings, used prompts and promptbooks to investigate security scenarios, and created a custom promptbook to streamline a repeatable investigation workflow. You then used Security Copilot within Microsoft Purview to investigate data protection activity, insider risk alerts, data loss prevention (DLP) alerts, and unlabeled sensitive content in eDiscovery. Finally, you used Security Copilot in Microsoft Defender XDR to investigate security incidents, analyze artifacts, and perform advanced investigation.