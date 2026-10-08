
Microsoft Purview and Microsoft Defender XDR help organizations detect potential data loss risks and respond quickly to protect sensitive information. Investigation and response activities include reviewing DLP alerts, applying appropriate remediation actions, and documenting findings in a structured and consistent way.

# Introduction

DLP alerts accumulate fast. A single policy across a few hundred users can generate dozens of alerts in a week. Without a consistent process, they get handled differently every time. Some over-investigate low-risk matches. Others dismiss alerts without enough context and move on. The queue becomes unreliable, the audit trail is incomplete, and patterns that span multiple alerts go unnoticed.

Over time, that inconsistency erodes trust in the queue itself. Alerts stop being a signal and start being noise that people scroll past.

In this module, you:

- Identify how DLP alerts are triggered and where they appear
- Investigate alerts in Microsoft Purview and Microsoft Defender XDR
- Apply appropriate response actions based on investigation outcomes
- Complete the investigation process by documenting findings, assigning ownership, and closing alerts or incidents
- Recognize opportunities to improve DLP policies based on investigation outcomes

# Understand data loss prevention (DLP) alerts
Data loss prevention (DLP) alerts fire when someone's action matches a condition in a DLP policy. To investigate one effectively, you need to know what triggered it, where it shows up, and which tool to open first. Staying on top of alerts is how you spot risky activity early, respond before small issues escalate, and figure out which policies need tuning.

## What is a DLP alert?

DLP alerts are notifications that get triggered when someone's actions match a condition in a DLP policy. These actions can involve sharing sensitive information like credit card numbers, Social Security numbers, or financial records in ways that could put data at risk.

Some alerts are triggered by a single event, like someone emailing a document containing sensitive data to a personal account. Other alerts are triggered when multiple small events add up over time. For example, sending several emails with one credit card number each within a day could trigger an alert, even if no single email violated the policy on its own.

Alerts don't automatically mean something malicious happened. They just tell you that something met the criteria to be flagged. Your job is to figure out whether the alert is something that needs action or something that indicates a policy needs to be fine-tuned.

## Where do DLP alerts show up?

DLP alerts appear in two tools. Both show the same alerts, but they serve different purposes:

- **Microsoft Defender XDR** is used for security investigations. It consolidates incidents so you can see everything related to a potential threat in one place. If DLP alerts are part of a bigger security issue, like someone exfiltrating data while also turning off antivirus settings, Defender XDR is where you correlate those signals.
    
- **Microsoft Purview** is used for compliance. It focuses more on the policy itself: what triggered the alert, what rules were involved, and whether those rules are working as expected. If the alert came from a false positive, Purview is where you'd go to adjust the policy so it doesn't happen again.
    

## How alerts help during investigations

Let's say you have a DLP policy that blocks sharing credit card numbers through email. An alert comes in showing that someone in the finance department triggered this policy. You open the alert in Microsoft Purview and see it was caused by a monthly report being emailed to an external contractor. After reviewing the file, you realize it included masked credit card numbers, not real ones. This might be a false positive, so you decide to adjust the policy to ignore numbers formatted like that.

But at the same time, you check Defender XDR. You notice that the same user also downloaded many files from SharePoint earlier that morning, and there's a second alert showing they tried to upload a file to a personal Dropbox account. That gives you a more complete picture. Maybe this wasn't a false positive after all. Now you know to follow up.

# Understand the DLP alert lifecycle
Data loss prevention (DLP) alerts follow a structured path from detection through resolution. Each stage has a specific purpose and a different set of decisions.

## Trigger

A DLP alert starts when a user's action matches a condition in a DLP policy. Policies are typically configured to watch for activity that could lead to data loss, like:

- Sharing sensitive data with people outside the organization
- Downloading confidential files to removable media
- Uploading protected content to unsanctioned cloud apps

When this kind of activity happens, the policy can take actions such as blocking the activity, warning the user, and if configured to do so, generating an alert.

## Notify

If a policy is configured to generate an alert, that alert appears in two places:

- **Microsoft Defender portal**: Where alerts are grouped into incidents along with other security signals
- **Microsoft Purview alerts dashboard**: Where you can track alert history, review alert details, and perform basic actions

Email notifications can also be sent to users, admins, or security teams depending on the policy setup. These notifications let you know something happened that might require a closer look.

In this phase, you can also use Activity explorer to view the details of what happened. If your team uses Microsoft's APIs, you can export activity data for long-term storage or custom reporting.

## Triage

Triage is about reviewing new alerts and deciding what to do next. You decide if the alert is a false positive or something that needs a deeper investigation. If it's valid, you assign it a priority level and designate someone to own the response.

The Microsoft Defender portal groups related alerts into incidents. This gives you a broader view of the user's actions. For example, if a user downloads a file from SharePoint, uploads it to a personal OneDrive, and then shares it externally, those events are grouped into one incident. This makes it easier to focus on what matters.

You can use tags, comments, and filters to manage the incident queue. To focus only on DLP-related alerts, select **Add filter**, choose **Service/detection sources**, and select **Microsoft Data Loss Prevention**.

If your organization shares Insider Risk Management signals with Defender, you can also see the user's insider risk severity level next to their DLP alerts. This helps prioritize which alerts might require immediate action.

Microsoft Security Copilot is also available in some tenants and can help analyze alert context and suggest next steps. This feature is embedded in the [DLP Alerts dashboard](https://learn.microsoft.com/en-us/purview/dlp-alerts-dashboard-get-started#investigate-a-dlp-alert) and in [Data Security Posture Management (preview)](https://learn.microsoft.com/en-us/purview/data-security-posture-management-copilot#use-microsoft-security-copilot-with-data-security-posture-management-preview).

## Investigate

Once a triage owner is assigned, the next step is to investigate the alert further. This means gathering evidence, reviewing activity logs, and deciding on a remediation plan.

Where you start depends on what you're trying to answer:

- **Start in Microsoft Defender** when you need to see whether the DLP alert is part of a broader pattern. Defender correlates DLP alerts with signals from endpoints, email, identity, and cloud apps, so it's the right place when the user's behavior looks like more than a one-off policy match.
- **Start in the Microsoft Purview alerts dashboard** when you already know which policy fired and want to review the specific match, check the file content, or decide whether the policy needs tuning.
- **Use Activity explorer** when you need to filter and compare user actions over time without opening individual alerts.
- **Use Content explorer** when you need to inspect the actual file or message content that triggered the match.

If your organization has enabled data sharing in Insider Risk Management settings and the user is in scope of an Insider Risk policy, you can also access a **User activity summary** that shows up to 120 days of user behavior, including risky actions like exfiltrating files or bypassing policy warnings.

## Remediate

After investigation, the alert owner decides what actions to take. Remediation options vary based on how your organization handles risk. Some common actions include:

- Marking the alert as informational and taking no action
- Following up with the user to explain why the action was risky
- Blocking file sharing or revoking access
- Removing the file from cloud storage or applying a sensitivity label
- Resetting passwords, disabling accounts, or isolating devices

In Defender, you can take many of these actions directly from the portal, including:

- Remove or quarantine a file
- Revoke sharing permissions
- Disable user accounts
- Reset passwords
- Download or delete emails
- Use Advanced Hunting to look for related events

## Tune

The final step in the alert lifecycle is tuning your DLP policy. Once you respond to the alert, ask whether the policy worked as intended. You might need to adjust:

- The sensitivity level of conditions that trigger an alert
- The scope of the policy (users, locations, or groups)
- Notification settings
- Whether certain low-risk actions should trigger alerts at all

Tuning reduces false positives and improves detection accuracy over time. You can revisit your policy intent and compare it to actual outcomes to decide what changes are needed.

# Configure DLP policies to generate alerts
Alert settings in a data loss prevention (DLP) policy control how and when you're notified about risky activity. The configuration determines whether alerts fire for every policy match or only when certain thresholds are met. ==Licensing affects ==which options are available, and the wrong threshold can mean either alert fatigue or missed incidents.

## When do you configure alerts in a DLP policy?

When you create or edit a DLP policy in Microsoft Purview, you start by defining which conditions to monitor. You then decide what actions to take and how alerts should be handled. Alert settings are part of the rule configuration stage. After you define your conditions and actions, you decide whether to notify someone and whether an alert should be created.

To configure alerts when creating or editing a DLP policy:

1. Go to the Microsoft Purview portal.
    
2. Select **Solutions** > **Data Loss Prevention** > **Policies**.
    
3. Create a new DLP policy or select an existing policy to modify.
    
4. **Choose where to apply the policy** in locations such as Exchange, SharePoint, or devices.
    
5. Create a new rule or edit an existing rule.
    
6. After defining conditions and actions, configure incident reports and alerting behavior.
    
    This is where you choose between single-event and aggregate alerts. Use single-event for anything where one match warrants immediate review. Use aggregate when the signal only becomes meaningful at volume.
    
    [![Screenshot showing the configuration options for incident reports in a data loss prevention policy.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/configure-incident-reports.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/configure-incident-reports.png#lightbox)
    
7. Choose to deploy your policy right away, in simulation mode, or off.
    
8. Save and submit your policy settings.
    

## Types of DLP alerts

DLP alerts in Microsoft Purview come in two types:

- **Single-event alerts** generate an alert every time a policy rule match occurs. These alerts are best for low-volume, high-sensitivity events, like a user emailing a file that contains multiple credit card numbers.
- **Aggregate-event alerts** generate alerts only when a threshold is met, such as 10 matching events within 24 hours. This reduces alert fatigue in high-volume environments.

You can set thresholds by:

- **Number of matches** (for example, 10 matches in 60 minutes)
- **Volume of data** (for example, more than 1 MB of matching content)

To prevent alert overload, policy matches on the same item in the same location are grouped if they occur within a one-minute window.

## Licensing requirements

What you can configure depends on your Microsoft 365 license:

- **Single-event alerts**: Available with E1, F1, G1, E3, or G3 licenses.
- **Aggregate-event alerts**: Requires an E5 or G5 license, or one of the following add-ons for E1/E3/G1/G3:
    - Office 365 Advanced Threat Protection Plan 2
    - Microsoft Purview Suite (formerly Microsoft 365 E5 Compliance)
    - Microsoft 365 eDiscovery and Audit add-on

Licensing also affects the aggregation time window:

- **One-minute window**: E5 or add-on license
- **15-minute window**: E3/G3 or lower without the add-on

## Roles required to configure alerts

To configure or view DLP alerts, users must be assigned specific roles in Microsoft Purview. These roles include:

- **Compliance Administrator**
- **Information Protection Admin**
- **Security Operator**
- **Security Reader**
- **Information Protection Investigator**

To access the DLP alert management dashboard, users must have the **Manage alerts** role, with membership in either the **DLP Compliance Management** or **View-Only DLP Compliance Management** role group.

For viewing matched content or using Content explorer, the **Content Explorer Content Viewer** role is also required.

## Where alerts appear

Email notifications deliver alerts and also display them in two key locations:

- **Microsoft Defender XDR**: Used for investigating alerts and managing incidents. This is where alerts are grouped, correlated with other events, and acted on.
- **Microsoft Purview alerts dashboard**: Used for configuring policies and reviewing alert history. You can change alert status, export activity data, or share events with others.

## How alerts behave after deployment

- For a given policy match, alert emails, incident reports, and user notifications are sent once per document. If the same document triggers the same rule again within the aggregation window, it's grouped into the existing alert rather than generating a new one.
- It can take up to 3 hours for a new or updated policy to begin generating alerts.
- If your tenant uses Endpoint DLP or Teams DLP, alerts from those services also appear in the DLP alerts dashboard.
- If your tenant has **user-and-rule-based alert aggregation** enabled (currently in preview), single-event alerts are also grouped by user. When the same person triggers the same rule multiple times within a configurable window of 15 to 60 minutes, those matches are combined into a single alert rather than generating separate ones. This means fewer alerts in the queue, but each alert can contain more events. Confirm whether this is enabled under **Data Loss Prevention** > **Settings** in the Microsoft Purview portal.

# Investigate DLP alerts in Microsoft Purview
When a DLP alert doesn't involve other security signals and you need to check what matched, why, and whether the policy needs adjusting, the **Alerts dashboard** in Microsoft Purview is where you start.

## Where DLP alerts appear

Alerts appear in the **Microsoft Purview Alerts dashboard** when a user action matches a DLP policy condition. From there, you can filter, investigate, and triage.

How long alerts remain visible in the dashboard depends on your organization's audit log retention policy. If you need alerts retained longer than the default, adjust your retention settings in the Microsoft Purview Audit solution.

## Workloads supported

The dashboard displays alerts from DLP policies configured across:

- Exchange email
- SharePoint sites
- OneDrive accounts
- Teams chat and channel messages
- Devices
- Instances
- On-premises repositories
- Fabric and Power BI

## Review and investigate alerts

To begin an investigation, go to the [Microsoft Purview portal](https://purview.microsoft.com/) and go to **Data loss prevention** > **Alerts**. The dashboard shows all recent DLP alerts. You can filter and customize the view to focus on what matters most.

### Step 1: Filter and find relevant alerts

Use the **Filters** panel to narrow down alerts by policy name, severity, user, alert status, or detection time. You can also select **Customize columns** to show or hide specific properties in the list view.

Once you locate an alert you want to investigate, select it to open the alert details.

[![Screenshot showing Alerts dashboard in data loss prevention.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-alerts-dashboard.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-alerts-dashboard.png#lightbox)

### Step 2: Review the alert details

When you select an alert, the **Details** tab opens by default. This view shows key metadata, such as:

- Alert ID
- Status
- Severity
- Detection timestamp
- Matched policy and rule

You can also see the workload where the match occurred, such as Exchange, SharePoint, or OneDrive.

[![Screenshot showing the details of a data loss prevention alert.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-alerts-details.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-alerts-details.png#lightbox)

### Step 3: View related user activity

If your organization has integrated **Insider Risk Management**, the **User activity summary** tab becomes available. For this tab to appear, [data sharing must be turned on in Insider Risk Management settings](https://learn.microsoft.com/en-us/purview/insider-risk-management-settings-share-data), and the user must be in scope of an Insider Risk Management policy. Once enabled, the tab shows exfiltration activities the user engaged in over the past 120 days, so you can determine whether the alert is part of a larger pattern.

[![Screenshot showing user activity summary in a data loss prevention alert.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-activity-summary.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-activity-summary.png#lightbox)

### Step 4: Review matched events

You can select **View events** on the **Details** tab, or go to the **Events** tab and select the event directly. This shows a list of actions that matched the DLP policy.

From this view, you can:

- Review detailed metadata such as the file name, location, size, and timestamp
- Confirm whether the user received and overrode a policy tip
- Understand what triggered the alert based on the policy rule that matched

To respond to the event, select **Actions**. From the **Actions** dropdown, you can:

- Download the matched content (requires appropriate role)
    
- Apply or remove a sensitivity label (if permitted)
    
- Unshare or delete the file
    
- Send a notification email
    
- Copy event link to share with someone else in your organization
    
    [![Screenshot showing the Events page of a data loss prevention alert.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-alert-events.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-alert-events.png#lightbox)
    

### Step 5: Complete the investigation

After reviewing the alert and any related user activity or events:

- Use the **Overview** panel to summarize what occurred and who was involved
    
- Add notes or comments
    
- Assign ownership if needed
    
- Set the alert **Status** to **Resolved** when the investigation is complete
    
    [![Screenshot showing the Overview page of a data loss prevention alert.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-alert-overview.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-alert-overview.png#lightbox)
    

## Use Microsoft Security Copilot

Security Copilot is integrated into the DLP Alerts dashboard. Select **Summarize with Copilot** on any alert to generate an AI summary of the alert context, including:

- Triggered policy and rule
    
- File involved and access path
    
- User identity and associated Insider Risk level
    
- Suggested follow-up actions
    
    [![Screenshot showing the Security Copilot pane embedded in the data loss prevention alerts dashboard.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-alert-security-copilot.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-alert-security-copilot.png#lightbox)
    

You can interact with Security Copilot directly in the DLP alert view. Use the options to copy or regenerate the summary, or open it in the standalone experience for more context.

## Share alert events

If someone outside your security or compliance role groups needs to review an alert, you can create a **shareable link** to a specific event:

1. Open the alert and navigate to the **Events** tab.
2. Select the event to share.
3. Choose **Actions** > **Copy event link**.
4. Paste the link into a chat, ticket, or email to share it with others.

Shared users only see what's included in the shared view. Permissions to edit or act on the alert aren't granted through the link.

## View matched content and metadata

DLP alerts include detailed information about:

- **Matched content**: Names, labels, and sizes of files or emails
- **User actions**: The behavior that matched the policy (for example, sending, uploading, copying)
- **Policy match details**: The rule, condition, and sensitive information type (SIT) involved

This data can be viewed directly in the Events tab or in **Content explorer** and **Activity explorer**, depending on your role permissions.

## Limitations when downloading emails

From the dashboard, some alerts allow you to download emails involved in the incident. However, emails might be unavailable if:

- An internal sender deleted the message sent to an external recipient
- An external sender's message was deleted by the internal recipient
- Both internal sender and recipient deleted the message

These limitations apply to Exchange-based DLP events.

# Investigate DLP alerts in Microsoft Defender XDR
Downloading multiple files to an unmanaged device might trigger a policy violation. But what if the same user also shared sensitive documents externally or bypassed a policy warning earlier that day? Viewing alerts one at a time can miss these broader patterns. Microsoft Defender XDR groups related alerts into incidents and surfaces risky behavior across data sources, so you see the full picture instead of isolated events.

## Why use Microsoft Defender XDR to investigate data loss prevention alerts?

Defender XDR gives you the broader context that individual alerts don't provide on their own. It:

- Automatically correlates related data loss prevention (DLP) alerts into incidents
- Extends investigation across endpoints, email, cloud apps, and identities
- Enables response actions like disabling accounts or revoking access

Use Defender when you need to see whether a DLP alert connects to other security activity for the same user or device.

## Licensing and permissions

To investigate DLP alerts in Microsoft Defender XDR or Microsoft Sentinel, your organization must have eligible Microsoft 365 licensing. Most capabilities are available to organizations with Microsoft 365 E5 or equivalent compliance licensing.

Role-based access control also applies. Users must be assigned appropriate Defender or compliance roles to view and act on DLP incidents.

## Investigate alerts in Defender XDR

### Step 1: Open the incidents queue

1. Go to the [Microsoft Defender portal](https://security.microsoft.com/).
2. In the left navigation pane, select **Incidents & alerts** > **Incidents**.
3. Select **Add filter**, choose **Service/detection sources**, and then select **Microsoft Data Loss Prevention**.

[![Screenshot showing the Microsoft Defender XDR filtering for data loss prevention alerts.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/investigate-alert-defender.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/investigate-alert-defender.png#lightbox)

This view shows incidents that include one or more DLP alerts. Each incident can contain multiple related alerts grouped together. Defender retains incident history for six months, so you can search back through that window to find related resolved incidents or recurring alerts from the same user.

### Step 2: Investigate a DLP alert

After an incident is identified in the queue, the next step is to examine the details of an individual alert. This helps you confirm what happened, determine whether the alert is valid, and decide what to do next.

- Review the **Alert story** to understand what triggered the policy match.
- Use the **Related events** section to explore user activity like downloads, shares, or overrides.
- Open the **Sensitive info types** tab to see what types of sensitive content were detected.
- If permissions allow, access the **Source tab** to inspect the file involved in the alert.

You can copy the summary, regenerate it, or open the Security Copilot pane for deeper insights. The summary includes:

- Alert title and severity
- Matched policy and rule
- File details and access path
- User identity and associated activities

[![Screenshot showing the Microsoft Defender XDR alert details page with attack story and Security Copilot pane.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/investigate-alert-defender.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/investigate-alert-defender.png#lightbox)

### Step 3: Take response actions

Based on your investigation, you can take action directly from the alert view:

- **Download email** (for Exchange alerts)
- **Apply sensitivity label**, **Unshare**, **Delete**, or **Download** (for SharePoint or OneDrive files)
- **Apply retention label**
- **Send email notification**
- **Withdraw feedback** if the alert was marked incorrectly

To respond at the user level, select the **User card** to view profile details and take actions like resetting passwords or disabling accounts.

For device-based DLP alerts, select the **Device card** to view device details and isolate or manage the device.

 Note

To inspect file content for Endpoint DLP alerts, your organization must have [evidence collection for file activities on devices](https://learn.microsoft.com/en-us/purview/dlp-copy-matched-items-learn) configured. Without it, you can see alert metadata and policy match details, but you won't be able to view or download the actual file that triggered the alert.

### Step 4: Manage the incident

To complete incident handling, return to the incident summary page and select **Manage incident**. You can:

- Set the incident **Severity**
- Add or create **Incident tags**
- Assign the incident to an analyst or response team
- Update the **Status** to reflect progress (for example: In Progress, Resolved)
- Choose a **Classification**, such as True Positive or False Positive, and specify a reason (like Malicious user activity or Security testing)

[![Screenshot showing the Manage incident flyout page in Microsoft Defender.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/defender-manage-incident.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/defender-manage-incident.png#lightbox)

Use these fields to classify and close the incident.

## Use advanced hunting for deeper investigation

Advanced hunting lets you query user, file, and activity data across workloads using the **CloudAppEvents** table. This table contains audit logs from across Microsoft 365 workloads, including:

- Exchange
- SharePoint
- OneDrive
- Devices

To start hunting:

1. In the Defender portal, select **Advanced hunting**.
2. Use a built-in query, or select **Go Hunt** from an event in the alert details.
3. Defender provides contextual queries based on the event source, such as:
    - File shared with
    - File activities
    - Site activity
    - User DLP violations (last 30 days)

You can run, customize, or save the query to track related activity.

## Extend your investigation with Microsoft Sentinel

While Defender XDR offers deep alert-level investigation, Microsoft Sentinel adds cross-platform correlation and automation. Microsoft Sentinel can bring DLP insights into broader investigations and workflows alongside other Microsoft and non-Microsoft data sources.

If your organization uses Microsoft Sentinel, you can integrate DLP alerts from Microsoft Defender XDR into Microsoft Sentinel for:

- Cross-platform investigation
- Custom correlation rules
- Automated response using SOAR (security orchestration, automation, and response)

To get started:

1. Use the [Microsoft Defender XDR connector](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender) in Microsoft Sentinel to import DLP alerts and incidents.
2. Enable the **CloudAppEvents** connector to ingest audit logs.
3. Use KQL queries in Microsoft Sentinel to correlate alerts and investigate root causes.

Example query:

Kusto

```
let Alert = SecurityAlert
| where TimeGenerated > ago(30d)
| where SystemAlertId == "INSERT_ALERT_ID"; // insert the systemAlertID here
CloudAppEvents
| extend correlationId1 = parse_json(tostring(RawEventData.Data)).cid
| extend correlationId = tostring(correlationId1)
| join kind=inner Alert on $left.correlationId == $right.AlertType
| where RawEventData.CreationTime > StartTime and RawEventData.CreationTime < EndTime
```

This query identifies activity related to a specific alert using the **CloudAppEvents** table.


# Investigate DLP alerts with Security Copilot and AI agents
Investigating data loss prevention (DLP) alerts often involves sorting through large volumes of activity to find what matters most. The Microsoft Purview DLP triage agent, powered by Microsoft Security Copilot, automates that process. It reviews alerts, prioritizes those with the highest potential risk, and surfaces the ones that need attention first.

In a typical week, a DLP policy might generate alerts for external file shares, email attachments, and cloud uploads. Most are low risk. A few contain sensitive financial data that needs immediate review. Rather than opening each one to make that determination manually, the triage agent analyzes content, assesses policy risk, and ranks alerts by severity. Security Copilot then summarizes context and suggests next steps.

## Understand how the DLP triage agent works

The DLP triage agent uses AI to evaluate and prioritize alerts that your DLP policies generate in Microsoft Purview. It examines content, policy actions, and potential exfiltration behavior to identify which alerts pose the greatest risk.

You can fine-tune how the agent interprets alerts by writing custom instructions in plain language. For example:

> Focus on alerts containing tax or finance information with more than five credit card or Social Security numbers.

When configured, the agent can:

- Interpret your instructions and convert them into logical conditions
- Prioritize alerts that meet those conditions
- Apply your criteria automatically each time it runs
- Allow manual reruns or adjustments when needed

The agent handles the sorting, but you still decide what to act on.

## Interpret triaged alerts in Microsoft Purview

After the agent runs, you can interpret the triaged alerts to understand which incidents need attention first and why. You'll see the results in the **Alert triage agent (preview)** view on the **Alerts** page.

The agent automatically groups triaged alerts into categories:

- **Needs attention**: Alerts that present the highest risk and should be reviewed first
- **Less urgent**: Alerts that appear lower in severity or likelihood of data loss
- **Not categorized**: Alerts the agent couldn't evaluate, such as those triggered by unsupported policy types

[![Screenshot showing the Alert Triage Agent view in Microsoft Purview with prioritized DLP alerts.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-triage-agent-alerts-view.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-triage-agent-alerts-view.png#lightbox)

Alerts are prioritized using three main factors:

- **Content risk**: Sensitive information types, trainable classifiers, or sensitivity labels detected in files
- **Exfiltration risk**: Activities that suggest data movement outside approved channels, such as external sharing or downloads
- **Policy risk**: Rule mode and actions, including whether a label was removed or downgraded

Alerts most likely to involve sensitive data exposure rise to the top.

## Run the DLP triage agent

The agent must be deployed and configured before you can use it. Deployment involves provisioning Security Compute Units (SCUs), enabling the Purview plugin in Security Copilot, and assigning an agent identity. For full setup steps, see [Get started with the Microsoft Purview Triage Agent in Data Loss Prevention](https://learn.microsoft.com/en-us/purview/copilot-in-purview-triage-dlp-agent-get-started).

To view and act on triaged alerts, you need the Information Protection Analyst or Investigator role, Purview Agent Analysis, and Security Copilot Contributor. For device-based alerts, the Data Classification Content Viewer and Content Downloader roles are also required.

Once the agent is deployed, it can run in two modes:

- **Automatically**, on a fixed schedule, to continuously review alerts from a selected timeframe
- **Manually**, on one alert at a time, when you want to evaluate a specific case more closely

The timeframe controls how far back the agent looks. You can set it to cover the past 24 hours up to 30 days. When running automatically, it processes existing alerts in that window and triages new ones as they appear.

The agent only triages alerts from **active DLP policies**. Alerts from policies in **simulation mode** aren't included.

## Use Security Copilot to analyze triaged alerts

After the agent runs, switch to the **Alert triage agent (preview)** view to see how alerts are grouped and prioritized. You can open Security Copilot directly from an alert to summarize findings, review context, or get suggestions for next steps.

Security Copilot can help you:

- Summarize why the alert was triggered and prioritized
- Highlight sensitive data and potential exfiltration risks
- Correlate activity across SharePoint, OneDrive, Exchange, and Teams
- Recommend next actions for investigation or remediation

You can ask Copilot for specific help, such as:

- _Explain why this alert was marked as high risk._
- _Summarize the user's recent activity related to this file._
- _Identify whether this alert is part of a broader data exfiltration pattern._

After reviewing summaries and suggested actions, you can return to the triaged alert queue to take direct action on alerts that require further attention.

## Review and act on triaged alerts

Once alerts are triaged, review the prioritized queue to decide what comes next:

1. In the Microsoft Purview portal, go to **Data Loss Prevention** > **Alerts**.
    
2. In the upper-right corner, switch to **Alert triage agent (preview)** view.
    
3. Review **Needs attention** alerts first.
    
4. Select an alert to open the **Agent summary** pane and review the agent's categorization and triage notes.
    
5. Use **Summarize** to generate an AI summary of the alert or user activity if you need more context.
    
6. Select **View details** or update the alert as needed, for example by assigning it or notifying users.
    
    [![Screenshot showing the Agent summary pane in Microsoft Purview with DLP alert categorization and triage notes.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-triage-agent-summary.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-data-loss-prevention-alerts/media/data-loss-prevention-triage-agent-summary.png#lightbox)
    

You can rerun the agent on a single alert if conditions change or you need a new evaluation.

## Limitations and supported scenarios

- The agent triages alerts from **Exchange, SharePoint, OneDrive, Teams, and devices (Endpoint)**. For device alerts, [evidence collection for file activities on devices](https://learn.microsoft.com/en-us/purview/dlp-copy-matched-items-learn) must be enabled.
- Alerts triggered solely by **custom sensitive information types** or **custom trainable classifiers** aren't included.
- Files larger than **2 MB** aren't analyzed.
- When an alert includes more than 10 files, the agent analyzes the 10 most relevant based on policy matches and risk score.
- Simulation-mode policies and administrative unit scoping aren't supported.

For alerts that aren't fully triaged, continue your investigation in the standard DLP Alerts dashboard or Microsoft Defender XDR.

# Respond to DLP alerts
After you've investigated a data loss prevention (DLP) alert, the next step is to respond appropriately. This includes documenting your findings, assigning ownership if needed, taking mitigation actions, and closing out the alert or incident. Microsoft Purview and Microsoft Defender XDR each handle different parts of this process.

## Response actions in Microsoft Purview

In Microsoft Purview, you respond to DLP alerts directly from the **Alerts dashboard**. These alerts are typically scoped to user actions that match a DLP policy.

Key actions include:

- **Set alert status** to track progress, such as Investigating or Resolved
- **Assign the alert** to a reviewer for accountability
- **Add comments** to capture internal notes or observations
- **Share alert details** using a generated read-only link
- **View user activity summary** (if Insider Risk Management is integrated)

Recording this context keeps your audit trail clean and gives the next analyst something to work from.

## Response actions in Microsoft Defender XDR

In Microsoft Defender XDR, alerts are grouped into incidents, giving analysts a broader view of correlated activity across endpoints, email, cloud apps, and identities.

From the incident and alert views, you can:

- **Update the incident status**, assign it to a team member, and add notes
- **Apply classifications** like **True Positive** or **False Positive** and specify a reason
- **Take remediation actions** directly, such as:
    - Disabling a user account
    - Removing file access
    - Applying a sensitivity or retention label

You can also **correlate the DLP alert** with other security signals to determine whether it's part of a larger threat or an isolated incident.

## Handle false positives

Sometimes an alert fires on legitimate activity. A finance team shares masked account numbers with an authorized vendor, or a test environment triggers a production policy. When that happens, close the alert with the right classification so your queue stays useful and your reporting reflects actual risk.

In **Microsoft Defender XDR**, classify the incident as **False Positive** and select a reason, such as _Inaccurate alert_ or _Security testing_. That classification shows up in Defender reporting, so you can track how much noise a policy generates over time.

In **Microsoft Purview**, set the alert status to **Resolved** and add a comment explaining why it was a false positive. Purview doesn't have a separate classification field, so the comment is where you document the rationale for the next person who looks at this alert.

If the same legitimate activity keeps triggering alerts, adjust the policy conditions, add an exception, or narrow the scope. The goal is to prevent the next analyst from spending time on the same determination you already made.

## What happens when you resolve an alert

Setting an alert or incident to **Resolved** closes it, but doesn't suppress future alerts from the same activity. If the same user does the same thing again and it still matches the policy, a new alert appears. Resolve means "I've handled this one," not "stop alerting on this pattern."

==Resolved incidents stay visible in Defender for up to six months==. You can filter for them when reviewing historical patterns or auditing past decisions. In Purview, resolved alerts remain visible based on your organization's audit log retention settings.


# Exercise - Investigate a DLP alert and related incident
In this exercise, you investigate a data loss prevention (DLP) alert using the Triage Agent in Microsoft Purview, then continue your investigation in Microsoft Defender XDR to identify whether the alert is part of a broader incident.

 Note

This exercise uses an interactive guide. Follow the on-screen instructions to complete each step. If you select an incorrect area, the correct target will be highlighted. Use the MENU to track your progress and the NOTES panel for additional context.

**What you'll practice:**

- Prioritizing high-risk DLP alerts using the Triage Agent
- Reviewing the Agent summary to assess sensitivity, policy, and exfiltration risk
- Searching for the same alert in Microsoft Defender XDR
- Identifying correlated incidents and reviewing alert patterns across a single user

![[Pasted image 20260828144343.png]]

![[Pasted image 20260828144354.png]]
# Summary

A data loss prevention (DLP) alert is only as useful as the response behind it. From the moment an alert fires, each stage matters: triaging to separate signal from noise, investigating with the right tool, taking action, and documenting what happened so the next person doesn't start from scratch.

You learned to:

- Investigate DLP alerts in Microsoft Purview and Microsoft Defender XDR
- Review alert details, related user activities, and matched events
- Take appropriate response actions, such as revoking access, disabling accounts, or updating alert statuses
- Assign ownership, document decisions, and support accountability throughout the investigation process

When this process isn't followed consistently, problems compound. Alerts sit unreviewed and lose context as time passes. Patterns across users or policies go unnoticed because no one correlates them. False positives never get tuned out, so the queue fills with noise that trains analysts to ignore it. And when an incident does escalate, there's no documented trail showing what was checked, what was ruled out, or who made the call.


# Investigate insider risk alerts and related activity
# Introduction

Identifying insider risks is only the beginning. Organizations also need a clear and consistent approach to investigating alerts and understanding the full context of user behavior. Without a structured process, high-risk activity might go unnoticed, low-risk alerts might receive too much attention, and investigators can struggle to determine the right response.

This module focuses on helping you analyze and respond to alerts in Microsoft Purview Insider Risk Management. You'll learn how to:

- Review and triage alerts using the Alerts dashboard
- Understand the factors that influence alert generation and risk scoring
- Use tools like Activity explorer, User activity, and All risk factors to investigate user behavior
- Work with insider risk cases to organize related alerts and take follow-up actions
- Extend your investigation into Microsoft Defender XDR and use advanced hunting for deeper insight

By the end of this module, you'll understand how to investigate insider risk alerts in a way that's efficient, accurate, and aligned with your organization's risk policies.

# Understand insider risk alerts and investigations
Alerts in Microsoft Purview Insider Risk Management aren't generated randomly. They follow a defined sequence of actions that begins with policy settings and ends with a triggered alert. Understanding how alerts are generated is critical to reviewing and interpreting them accurately during investigations. This understanding allows investigators to identify relevant activity, determine why it was evaluated, and assess whether it meets the defined risk criteria.

## Why alert generation matters

Knowing how an alert was generated helps investigators:

- Identify what triggered the alert
- Understand which activities were evaluated
- Determine appropriate next steps
- Align alert evaluation with policy criteria

This context supports more consistent triage decisions and helps reduce time spent on irrelevant or low-risk activity.

## Alert generation process

Alerts are generated through a five-step process:

[![Diagram illustrating the process of how alerts are generated in Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-management-alert-generation-chart.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-management-alert-generation-chart.png#lightbox)

1. **Settings configured**: Organizations configure policy settings to align with their insider risk management strategy. This includes defining which risk indicators to monitor, identifying sensitive domains, and setting privacy preferences.
    
2. **Policy created**: Policies define whose activity to evaluate, what activity to detect, and which events should trigger active monitoring. For example, a policy might monitor users in finance for data exfiltration after a resignation is submitted.
    
3. **Triggering event occurs**: A triggering event activates the policy for a specific user. This could include events such as a resignation date being set or a risky website being accessed. It might also include detection of exfiltration behavior.
    
4. **User activity evaluated and scored**: The system begins monitoring the user's actions. Activities are assigned risk scores based on the type of activity, configured thresholds, and the user’s history.
    
5. **Alert generated**: An alert is generated if the user's risk score exceeds the policy-defined threshold.
    

This process ensures that alerts are based on defined conditions and relevant context. Not all activity results in an alert. For example, a user downloading files might not trigger an alert unless other risk factors are present.

Each alert is the result of a defined policy, a triggering event, and risk-based evaluation of user activity. Understanding how alerts are generated helps investigators assess their relevance and determine whether further action is needed. This insight supports more accurate, timely, and consistent handling of insider risk alerts.

# Manage alert volume in insider risk management
Balancing alert volume is an important part of maintaining an efficient insider risk program. If your policies generate too few alerts, you might miss meaningful signals. If they generate too many, investigators might become overwhelmed, making it harder to focus on high-risk activity. Microsoft Purview Insider Risk Management includes several tools and settings to help you fine-tune alert volume and ensure your environment supports consistent, focused investigations.

## When you're receiving too few alerts

Receiving fewer alerts than expected might indicate that your policies are too narrow or that thresholds are set too high. To increase alert volume:

- **Enable more risk indicators** in the **Policy indicators** settings. This expands the types of activities that policies detect.
- **Include more users** in policy scope by editing the **Users and groups** section of the policy.
- **Lower trigger thresholds** to start evaluating users earlier based on specific events, such as resignation or access to sensitive content.
- **Lower indicator thresholds** to generate alerts based on less frequent or less severe activity.
- **Adjust the alert volume slider** under **Settings > Intelligent detections**. Moving the slider toward "More alerts" increases overall alert generation, including medium- and low-severity alerts.

 Tip

Policies based on certain templates, like _Data leaks_ and _Risky browser usage_, allow custom thresholds that can be lowered to help generate more alerts.

## When you're receiving too many alerts

High alert volume can overwhelm analysts and reduce the effectiveness of your investigation process. To reduce alert volume:

- **Enable analytics** in **Settings > Analytics** to identify high-risk areas and adjust your approach accordingly.
- **Use real-time insights** to update thresholds and indicator selections based on recommended values.
- **Refine policy scope and content** by narrowing the list of in-scope users or prioritizing only the most sensitive files and communication channels.
- **Enable inline alert customization** to allow analysts to adjust thresholds during triage.
- **Dismiss multiple low-priority alerts in bulk** to reduce noise in the alert queue.

## Configuration options for alert management

Beyond basic tuning, Microsoft Purview provides several configuration options to help manage alert volume more effectively:

- **Use appropriate policy templates** to target specific risk scenarios.
- **Configure global exclusions** to prevent benign activity from triggering alerts.
- **Define detection groups** to apply different policies to different user populations.
- **Create indicator variants** to refine detection logic.
- **Adjust policy timeframes** to control how far back activity is evaluated.
- **Assign appropriate roles** to ensure only qualified users can make sensitive configuration changes.

Effective alert volume management requires both upfront planning and ongoing tuning. Use built-in analytics and threshold recommendations to maintain a manageable signal-to-noise ratio. When alert volume is tuned effectively, your investigation process becomes more focused, efficient, and aligned with organizational risk priorities.

# Investigate and triage insider risk alerts in Microsoft Purview
The Alert dashboard in Microsoft Purview Insider Risk Management helps investigators and analysts view, prioritize, and take action on potentially risky user activity. Each alert is based on policy-defined conditions and provides a summary of the user's actions, associated risks, and relevant context. Effective alert triage ensures that high-risk behavior is addressed quickly, while low-risk activity can be dismissed to reduce noise.

## Overview of the Alert dashboard

The Alerts dashboard provides a centralized queue of all alerts generated by Insider Risk Management policies. Each row in the dashboard represents an individual alert and includes key fields to support triage and prioritization at a glance:

- **ID**: A unique identifier for each alert.
- **Copilot icon**: Indicates whether Copilot is available to summarize the alert.
- **Users**: The individual associated with the potentially risky activity.
- **Policy**: The Insider Risk Management policy that generated the alert.
- **Status**: Shows if the alert is new, confirmed, dismissed, or resolved.
- **Spotlight**: Highlights high-priority alerts that meet specific risk criteria.
- **Alert severity**: Automatically calculated risk level—Low, Medium, or High.
- **Time detected**: Indicates when the alert was generated.
- **Assigned to**: Shows who, if anyone, is currently assigned to investigate the alert.
- **Case**: Lists any case associated with the alert.

[![Screenshot showing the Alerts dashboard in Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-alerts-dashboard.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-alerts-dashboard.png#lightbox)

You can use filters, saved views, and column customization to focus on the alerts that matter most. Selecting an alert opens the Alert details page, where you can investigate activity, view user history, and take action such as dismissing or escalating the alert.

### Filtering and customizing views

When working with a high volume of alerts, filtering and customizing your view can improve efficiency:

- **Add filters** to narrow results by attributes like risk factor, severity, policy, assigned analyst, or triggering event.
- **Save custom filter views** to quickly return to commonly used alert queues.
- **Customize columns** to show or hide fields like policy name, time detected, or alert status.
- **Search by keyword** such as user principal name (UPN), alert ID, or assigned admin.

[![Screenshot highlighting the filters on the Alerts dashboard.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-filter-alerts.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-filter-alerts.png#lightbox)

### Spotlight high-priority alerts

Insider Risk Management includes a [[**Spotlight**]] feature that ==automatically highlights high-priority alerts in the alert queue==. This helps analysts focus on the most critical cases first. Spotlight uses rule-based logic to evaluate alerts based on activity type, tags, and risk scoring patterns observed across organizations. Spotlighted alerts appear visually distinct in the alert list and support faster triage decisions.

 Tip

Spotlight is especially useful in environments with high alert volume. It brings attention to alerts that might require immediate review.

These tools help reduce investigation time and support consistency across teams.

## Review individual alerts

After identifying an alert of interest in the dashboard, you can select it to open the Alert details page. This view provides a deeper investigation workspace with information about the triggering activity, user context, and risk factors. From here, analysts and investigators can assess whether the alert warrants further action.

- **Alert summary**: Displays the risk severity level, alert score, activity that triggered the alert, and triggering event.
- **User details and history**: Shows general user information and past alerts, including unresolved or repeated risk patterns.
- **Tabs for deeper analysis**: Includes tabs for **All risk factors**, **User activity**, and **Activity explorer** to review specific behavior in detail.

[![Screenshot showing alert details in Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-alert-details.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-alert-details.png#lightbox)

Alerts are automatically categorized by severity (low, medium, high) and can be filtered by status, policy, risk factor, or other criteria. Each new insight related to a user is added to their existing alert instead of generating a new one.

 Note

Only unrestricted administrators or users with proper role assignments can view alerts, depending on how administrative units are scoped.

## Triage and take action on alerts

Once you've identified an alert that needs review, you can triage and take action directly from the Alert details page:

- **Dismiss** the alert if it was triggered by expected or non-risky behavior.
- **Confirm and create a case** to escalate the alert for deeper investigation.
- **Assign** the alert to another analyst or investigator.

Each alert is assigned a risk severity score based on multiple factors, including frequency of activity, user history, and the presence of risk indicators. If an alert remains untriaged and more risky behavior occurs, its severity level might increase.

 Tip

You can select and dismiss multiple low-priority alerts in bulk using the command bar. ==Up to 400 alerts can be dismissed at once.==

## Use Security Copilot to accelerate triage

If enabled, Security Copilot embedded in Microsoft Purview can summarize an alert to help you triage faster. Without opening the alert, you can select **Summarize with Copilot** to generate an overview that includes:

- Policy name and triggering event
- Activity that generated the alert
- Key user attributes
- Top risk factors

Copilot can also suggest questions to help refine your summary, such as:

- What actions did the user perform in the last 10 days?
    
- List all sequential activities involving this user.
    
- Did the user engage in any unusual behavior?
    
    [![Screenshot showing embedded Security Copilot in Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-security-copilot.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-security-copilot.png#lightbox)
    

These insights make it easier to prioritize the most important alerts and dismiss those that don't require follow-up.

## Retention and alert limits

Alerts in a "==Needs review" state are retained for 120 days==. After this period, they're automatically deleted unless linked to an active case. ==Active and unresolved cases are retained indefinitely. ==Organizations can have ==up to 100 active cases at any given time.==

The Alert dashboard is the central hub for reviewing and triaging insider risk alerts in Microsoft Purview. It allows investigators to:

- Quickly assess risk severity and context
- Filter and organize large volumes of alerts
- Use Copilot to streamline triage
- Assign, dismiss, or escalate alerts as needed

By combining automated insights with manual review tools, the Alert dashboard supports efficient, accurate investigation workflows aligned with your organization's risk management goals.

# Investigate insider risk alerts with Security Copilot and AI agents
Investigating insider risk alerts involves understanding patterns of user behavior and identifying actions that might put sensitive information or business integrity at risk. The Microsoft Purview insider risk triage agent, powered by Microsoft Security Copilot, helps automate this process. It reviews alerts, analyzes activity indicators, and prioritizes those with the highest potential risk so analysts can focus on what matters most.

Imagine you're reviewing alerts for employees uploading files to personal cloud storage or accessing sensitive data outside normal working hours. Some activity might be justified, but other cases could point to data exfiltration or policy violations. Instead of reviewing each alert manually, you can enable the insider risk triage agent to evaluate signals, assess policy risk, and highlight alerts that need immediate review. You can then use Security Copilot to summarize context, trace related activities, and guide your next steps.

 Note

Insider Risk Management pseudonymizes usernames by default to protect user privacy. You can adjust pseudonymization settings in the Insider Risk Management settings page if your investigation procedures require identifiable data.

## Understand how the insider risk triage agent works

The insider risk triage agent uses AI to analyze alerts generated by insider risk policies in Microsoft Purview. It examines multiple risk indicators, including data movement, communication patterns, and user context such as employment status or role changes. By analyzing these signals together, the agent determines which alerts pose the highest insider risk.

You can fine-tune how the agent interprets alerts by writing custom instructions in plain language. For example:

> Focus on alerts where users shared confidential design documents externally after a resignation notice.

When configured, the agent can:

- Interpret your instructions and convert them into logical conditions
- Evaluate alerts against those conditions
- Apply your criteria automatically each time it runs
- Allow manual reruns or adjustments if needed

This reduces the time spent manually comparing user actions and keeps analysts in control of prioritization and decision-making.

## Interpret triaged alerts in Microsoft Purview

After the agent runs, you can interpret results in the **Alert triage agent (preview)** view on the **Alerts** page. The agent organizes alerts into categories:

- **Needs attention**: Alerts that represent the highest insider risk and should be reviewed first
    
- **Less urgent**: Alerts that appear lower in severity or likelihood of policy violation
    
- **Not categorized**: Alerts that couldn't be evaluated, such as those triggered by unsupported policy types
    
    [![Screenshot showing the Alert triage agent view in Microsoft Purview Insider Risk Management with filter and category options for triaged alerts.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/triage-agent-alerts-filter-view.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/triage-agent-alerts-filter-view.png#lightbox)
    

Alerts are prioritized based on several factors:

- **Risk indicators**: User activity patterns, such as unusual downloads, external sharing, or access from unmanaged devices
- **Policy type**: The policy category that triggered the alert, such as data theft, security violation, or risky AI usage
- **User context**: Risk level from adaptive protection, recent HR signals, or role changes

This prioritization helps analysts focus on alerts most likely to involve insider-driven data exposure or policy abuse.

 Tip

Alert severity can change over time as new activity signals are detected or additional user behavior is analyzed. If the triage agent runs again with updated data, it might reprioritize alerts automatically.

## Run the insider risk triage agent

Before running the agent, confirm you have the correct roles and licensing:

- **Roles:** Insider Risk Administrator, Insider Risk Analyst, or Security Copilot Contributor
- **Licensing:** Microsoft Purview Insider Risk Management and provisioned **Security Compute Units (SCUs)** for the agent to run
- **Configuration:** Your tenant must be onboarded to Microsoft Security Copilot with the **Purview plugin** enabled

Agents run using the security context of the user who last saved the configuration, ==which must be renewed every 90 days.==

You can set the agent to run automatically or manually:

- **Automatically**, on a schedule, to review new alerts within a selected timeframe
- **Manually**, on individual alerts or policies when deeper analysis is needed

The agent only triages alerts from ==active insider risk policies==. Alerts from policies in simulation mode aren't included.

## Use Security Copilot to analyze triaged alerts

After the agent completes triage, you can open Security Copilot directly from an alert to review findings and receive guidance. Copilot provides AI-generated summaries that highlight activity, intent, and relationships between events.

Security Copilot can help you:

- Explain why the alert was prioritized as high risk
- Identify sensitive data or user actions involved
- Correlate behavior across data, devices, and communication channels
- Suggest next steps, such as escalating or applying adaptive protection controls

You can ask Copilot questions such as:

- _Summarize the user's recent activity that increased risk._
- _Identify related alerts involving the same user or data source._
- _Explain the behavioral indicators contributing to this alert._

After reviewing Copilot's summary, return to the triaged alert queue to take action on alerts that require further investigation.

## Review and act on triaged alerts

Once alerts are triaged, review the prioritized queue to decide what to do next:

1. In the Microsoft Purview portal, go to **Insider Risk Management** > **Alerts**.
    
2. Select **Alert triage agent (preview)** view.
    
3. Review **Needs attention** alerts first.
    
4. Select an alert to open the **Agent summary** pane and review the agent's risk categorization and notes.
    
5. Use **Summarize** to generate an AI summary of the case for more context.
    
6. Select **View details** or take actions such as assigning ownership, escalating to a case, or applying adaptive protection.
    
    [![Screenshot showing the Agent summary view in Microsoft Purview Insider Risk Management with categorized risk factors and user alert history.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/triage-agent-alert-summary.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/triage-agent-alert-summary.png#lightbox)
    

You can also use tools like **Activity explorer** and the **Data risk graph** for a deeper look at user behavior. These tools help you visualize activity trends, identify repeated risk patterns, and explore how specific actions contributed to the alert.

You can rerun the agent on an alert if new activity or context becomes available.

Security Copilot helps analysts investigate insider risk alerts faster, connect behavioral patterns, and make consistent, evidence-based decisions.

# Analyze alert context with the All risk factors tab
The **All risk factors** tab in Microsoft Purview Insider Risk Management provides a summary of potentially risky activity associated with an alert. This view helps investigators understand why an alert might be significant by showing which risk signals are present, even if those signals weren’t the direct cause of the alert.

Use this tab to evaluate the broader context of a user's behavior and decide whether to investigate further, dismiss the alert, or take action.

[![Screenshot showing the All risk factors tab in Microsoft Purview Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/all-risk-factors-tab.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/all-risk-factors-tab.png#lightbox)

## Risk factors shown in this tab

The All risk factors tab surfaces several types of behavior that might increase a user's overall risk level:

- **Top exfiltration activities**: Lists the most frequent exfiltration actions, such as archiving or uploading files.
- **Cumulative exfiltration**: Shows whether repeated actions build over time to indicate rising risk.
- **Sequences of activities**: Highlights related activities that form a recognizable risk sequence.
- **Priority content**: Indicates whether the user interacted with files marked as sensitive or business-critical.
- **Unallowed domains**: Flags any file or data transfers to domains that aren't permitted by policy.
- **Unusual behavior or high-impact user status**: Detects abnormal patterns or identifies users whose role or access level contributes to elevated risk.

Not all alerts are directly caused by these factors, but the tab helps you assess what else might be happening that could influence the user’s risk level.

 Tip

Risk signals shown on this tab might not be the reason the alert was triggered. Always check the activity listed in the alert summary before deciding how to respond.

## Use the Content detected section

The **Content detected** section on this tab shows specific items involved in each risk activity. Selecting a listed item allows you to:

- View metadata such as file name, type, location, and sensitivity label if present
- Open the **Activity explorer** to see how that item fits into a broader timeline of activity

[![Screenshot showing the Content detected section of the All risk factors tab in Microsoft Purview Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/all-risk-factors-content-detected.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/all-risk-factors-content-detected.png#lightbox)

This view helps you validate whether the behavior was risky and supports more informed decisions.

## Important behavior to understand

- **Risk factor summaries don't always match the trigger.** An alert might be triggered by access to priority content, but the tab could instead highlight unrelated risky browsing activity or sequences that increase concern.
- **Sequences can include excluded events.** Even if a file type is excluded from scoring, it can still appear in a sequence if it contributes to broader risky behavior. For example, a .png file might normally be excluded but still appears if used during an obfuscation attempt.
- **Use the Content detected section to investigate further.** This section links to Activity explorer, where you can view detailed events and associated content. It serves as a key entry point for deeper review.
# Investigate activity details with the Activity explorer tab
The **Activity explorer** tab in Microsoft Purview Insider Risk Management helps analysts investigate the full context of potentially risky behavior. This tab shows a ==timeline== of user activity that contributes to the alert, with detailed metadata to support investigation, filtering, and review.

Use this tab to confirm what triggered the alert and identify patterns or supporting evidence that indicate whether further action is needed.

[![Screenshot showing the Activity explorer tab in Microsoft Purview Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/activity-explorer-tab.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/activity-explorer-tab.png#lightbox)

## Review activity details

Each row in the Activity explorer represents an event associated with the alert or broader user activity. Columns show details such as:

- Date and time of the event
- Activity type (for example, file download or risky prompt)
- File name and location
- Associated sensitivity label, if present
- Risk score and related risk factors

You can select an item to open the activity details pane and review:

- Event metadata, such as file path or recipient
- Assigned risk score
- Indicators that contributed to the risk level

This level of detail supports deeper investigation of user behavior.

## Filter activity for investigation

To help focus your review, use filters at the top of the page to narrow the activity list. You can filter by:

- **Activity scope**: Show all scored activity for the user or only activity associated with this specific alert
- **Risk factor**: Focus on specific indicators like sequences, cumulative exfiltration, unallowed domains, or priority content
- **Review status**: Hide previously reviewed items to focus on new activity

Filtering helps streamline triage and identify which events require the most attention.

## Customize the view

Customizing the view helps you focus on relevant attributes during triage. To match your investigation workflow, you can:

- Select or remove columns using **Customize columns**
- Sort the view by date or risk score
- Save custom filter and column views for reuse

These options help personalize the workspace so investigators can focus on what matters most.

## Understand activity count discrepancies

The number of activities shown in Activity explorer might not always match the number of raw event logs. Common reasons include:

- **Cumulative exfiltration detection**: Similar activities are deduplicated and scored as a single risk event
- **Policy changes**: If policy settings change after events occur, prior events might be excluded
- **Excluded items in sequences**: Files excluded from risk scoring might still appear if they're part of a larger sequence

These factors explain why sequences or exfiltration activity counts might differ between views.

## Investigate excluded items in sequences

Even when a file type is excluded from scoring, it might still show up in a sequence if it contributes to broader risk. For example, a .png file normally excluded from policy might appear in a sequence if it was used during an obfuscation attempt.

In these cases:

- A score of 0 appears for the excluded event
- Excluded events are marked as **Excluded** in the activity details
- A link is available to filter and view all excluded events

This helps you understand the full context of a user's behavior, even when individual events aren't scored directly.

## Save views for future use

If you create a useful filter and column setup, you can select **Save this view** to reuse it later. Saved views include both filters and column selections, allowing consistent triage workflows across analysts or alert types.

Select **Views** to load saved views at any time. Views can be personal or shared depending on how your team manages investigations.

# Review patterns over time with th
## Investigate ongoing risk with the User activity tab

The **User activity** tab in Microsoft Purview Insider Risk Management shows a visual timeline of potentially risky behavior over time. This view helps investigators assess whether a user’s activity is ongoing, escalating, or part of a broader pattern.

Use this tab to evaluate risk across multiple alerts and understand how individual actions fit into a larger risk profile.

[![Screenshot showing the User activity tab in Microsoft Purview Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/user-activity-tab.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/user-activity-tab.png#lightbox)

## Identify patterns over time

This view uses colored bubbles to show activity categories and risk scores across a timeline. Bubbles represent distinct risk events. Select any bubble to open a details pane that includes:

- Date of the event
- Risk category (for example, Exfiltration or Obfuscation)
- Risk score
- Number of associated files or emails, with links for review

This visual layout makes it easier to spot repeated behaviors or concerning trends.

## Understand risk sequences

Sequences are shown with connecting lines between bubbles. These indicate related events that are part of a broader risk pattern. When a sequence is selected, the details pane includes:

- Name and date range of the sequence
- Combined risk score
- Total number of events and links to associated content

This view helps connect the dots between activities that might seem low-risk individually but are more significant together.

## Use the scatter plot to visualize risk patterns

The User activity tab includes a **color-coded scatter plot** that shows potentially risky activity over time. Each bubble represents a scored event. The vertical position indicates the risk score, and the horizontal position shows when the event occurred.

Use this visual timeline to:

- See when risk activity happened and how it changed over time
- Spot clusters or gaps in activity
- Identify risk sequences, shown with connecting lines and icons

## Filter and sort user activity

To focus your analysis, use the filters and sorting options at the top of the page:

- **Risk category**: Filter for sequences or high-risk events
- **Activity type**: Narrow to specific behaviors, such as AI usage or deletion
- **Date range**: View activity over 1, 3, or 6 months
- **Sort by**: Organize the timeline by risk score or event date
- **Review status**: Filter out activity that has already been reviewed

These filters make it easier to review large amounts of user activity.

## Interpret the full user timeline

The User activity tab provides a complete view of risk-assigned behavior:

- Shows events that span multiple alerts
- Displays cumulative exfiltration risk as a visual trend line
- Highlights sequences that include excluded file types if relevant to the risk pattern
- Uses a color-coded legend to categorize risk events

This comprehensive view supports better decision-making during investigations and case reviews.

# Investigate insider risk alerts in Microsoft Defender XDR

**Microsoft Defender Extended Detection and Response (XDR)** helps expand investigation capabilities for insider risk by integrating alerts from Microsoft Purview Insider Risk Management with other Microsoft security data. This combined view gives security operations center (SOC) analysts the context they need to assess user behavior, correlate risk signals, and take action across Microsoft 365 workloads.

Use this view to correlate insider risk alerts with data from other services like Microsoft Defender for Endpoint, Microsoft Entra ID, and Microsoft Purview Data Loss Prevention.

## Access insider risk alerts in Defender XDR

To review alerts in the [Microsoft Defender portal](https://security.microsoft.com/):

1. Go to **Investigation & response** > **Incidents & alerts** > **Incidents**.
    
2. Use the **Service source** filter to select **Microsoft Purview Insider Risk Management**
    
    [![Screenshot showing the Incidents page being filtered to show Microsoft Purview Insider Risk Management incidents.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/defender-insider-risk-incidents.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/defender-insider-risk-incidents.png#lightbox)
    

This filter shows alerts from Insider Risk Management and highlights when those alerts are grouped into incidents with alerts from other Microsoft tools.

## Understand the investigation view

When insider risk alerts appear in the Defender portal, they might be:

- Part of a unified **incident** that includes multiple alert types
- Listed individually in the **alert queue** for review
- Linked to other activity such as endpoint behavior or identity signals

Selecting an alert or incident provides details such as severity, classification, and alert mappings. You can also view the user entity page for a risk summary and associated activity.

## Review alert status and classification sync

Alert status and classification automatically sync between Microsoft Purview and Microsoft Defender:

|Microsoft Defender status|Insider Risk Management status|
|---|---|
|New, In progress|Needs review|
|Resolved|Dismissed or Confirmed (based on classification)|

How classification types align:

|Microsoft Defender classification|Insider Risk Management classification|
|---|---|
|True positive|Confirmed|
|Information, expected activity|Dismissed|
|False positive|Dismissed|

Updates to status, classification, and alert details reflect across both portals within about 30 minutes.

## Investigate insider risk activity with advanced hunting

Defender's **Advanced hunting** feature allows deeper investigation of insider risk activity using Kusto Query Language (KQL). Insider risk alerts and behavior logs are available in the following tables:

- `AlertInfo`: Alert metadata from multiple sources
- `AlertEvidence`: Linked entities such as files or users
- `DataSecurityBehaviors`: Policy-triggering behavioral patterns
- `DataSecurityEvents`: Detailed events from policy violations

These tables support cross-tool investigation. For example, you might query:

Kusto

```
DataSecurityEvents
| where FileName endswith ".zip"
| where ActionType == "FileUploaded"
```

You must be assigned the **Insider Risk Management Analyst** or **Investigator** role in Microsoft Purview to access this data.

## Requirements and setup

Before alerts appear in the Microsoft Defender portal:

The setting **Share user risk details with other security solutions** must be enabled in the Microsoft Purview portal. To enable this setting:

1. Go to the [Microsoft Purview portal](https://purview.microsoft.com/).
    
2. Select **Settings** > **Insider Risk Management** > **Data sharing**.
    
3. Enable **Share user risk details with other security solutions**.
    
    [![Screenshot showing where to enable data sharing in Microsoft Purview Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/enable-data-sharing-insider-risk-settings.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/enable-data-sharing-insider-risk-settings.png#lightbox)
    

Users must have roles in both Microsoft Purview and Microsoft Defender:

- **Defender**: _Security Operator_ or _Security Reader_
- **Purview**: _Insider Risk Management_, _Analyst_, or _Investigator_

Licensing for both solutions is also required. See Microsoft documentation for details.

## Limitations

Not all insider risk data is available in Defender:

- Alerts created from custom detections
- Risky AI usage events
- Non-Microsoft app events
- Exfiltration via email
- Events that occurred before an alert was generated
- Excluded events based on policy settings

Viewing insider risk alerts in Microsoft Defender XDR helps bring together security signals across Microsoft 365. This integration supports broader investigations, faster triage, and more comprehensive incident response.

# Manage and take action on insider risk cases


Cases in Microsoft Purview Insider Risk Management allow investigators to track user risk over time, review associated alerts, and take action based on the severity and context of the activity. Each case focuses on a single user and can include one or more alerts. Cases are created manually when an alert requires deeper review or coordination with other teams.

Use the **Cases** dashboard to view all active and closed cases, assign ownership, and manage follow-up actions such as escalation, communication, and resolution.

## Respond to alerts

Not all alerts require a case. You can take action directly from the **Alerts** queue by confirming or dismissing alerts as part of your triage process:

- **Dismiss** an alert if it's a false positive or doesn't require further review.
- **Confirm** an alert to indicate a policy violation and optionally create a case for deeper investigation.

Creating a case is recommended when an alert involves serious risk, multiple incidents, or needs collaboration across teams. Once a case is created, you can take further action such as sending notices, escalating, or resolving with a classification.

## Create and manage cases

Cases are created from alerts when an incident needs further review or response. Once created, cases can be updated with new alerts and managed throughout their lifecycle.

[![Screenshot showing how to create a case in Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-create-case.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-create-case.png#lightbox)

You can:

- Assign or reassign ownership
- Send an email notice to the user
- Escalate to Microsoft Purview eDiscovery (Premium)
- Run Power Automate flows
- Create or view a connected Microsoft Teams team
- Resolve the case with a classification of Benign (доброкачественный)or Confirmed policy violation

You can assign a case to any user with one of these roles: **Insider Risk Management**, **Analyst**, or **Investigator**.

## Use the Cases dashboard

The Cases dashboard lists each case and includes key details:

- Case name and ID
- Assigned user (anonymized if enabled)
- Status: **Active** or **Closed**
- Number of alerts
- Time opened and last updated
- Last updated by

You can search by case ID or keywords, and use filters to narrow by status, date opened, or last updated.

To customize the view, select **Customize columns**. To save filters for future use, apply filters and select **Save this view**.

[![Screenshot showing the Cases dashboard in Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-case-details.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-case-details.png#lightbox)

## Investigate a case

Selecting a case opens a detailed investigation view with multiple tabs:

- **Case overview**: User identity, department, risk score, associated alerts
    
- **Alerts**: Status, severity, and alert ID for each included alert
    
- **User activity**: Timeline of scored risk activity from the alert or broader user history
    
- **Activity explorer (preview)**: Detailed timeline and metadata for each associated event
    
    **User activity** shows the overall timeline of user risk behavior, while **Activity explorer** focuses on event-level details within the case scope.
    
- **Forensic evidence**: Screen captures from activity that triggered the alert
    
- **Content explorer**: Copies of files and email messages associated with risk alerts
    
- **Case notes:** Permanent, timestamped notes added by analysts
    
- **Contributors**: Users added to the case for collaboration
    
    [![Screenshot showing details of a case investigation.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-case-details.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-case-details.png#lightbox)
    

 Note

==Contributors can view the case and add notes, but they can't edit contributor lists or confirm/dismiss alerts.==

## Take action on a case

The case toolbar includes actions for responding to the alert:

### Send email notice

Send a message to the user to reinforce policies or training. Notices are based on templates and are recorded in the **Case notes** tab.

 Tip

Sending a notice doesn't close the case. To resolve it, you must select **Resolve case** separately.

### Escalate for investigation

Use this option to escalate the case to a Microsoft Purview eDiscovery (Premium) case for deeper investigation and legal hold workflows.

### Run Power Automate flows

Trigger flows for common tasks such as:

- Notifying a manager
- Creating a record in ServiceNow
- Requesting details from HR

### Create or view Teams team

If Teams integration is enabled in Insider Risk Management settings, a team is created automatically when a case is opened. Teams are archived when a case is resolved. To enable Teams integration:

1. Go to the [Microsoft Purview portal](https://purview.microsoft.com/).
    
2. Select **Settings** > **Insider Risk Management** > **Microsoft Teams**.
    
3. Select the toggle to enable integration with Microsoft Teams.
    
    [![Screenshot showing where to enable Teams integration in Microsoft Purview Insider Risk Management.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-teams-integration.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-insider-risk-investigate-alerts/media/insider-risk-teams-integration.png#lightbox)
    

## Resolve a case

When investigation is complete, resolve the case as:

- **Benign**: Behavior is low-risk, accidental, or false positive
- **Confirmed policy violation**: Behavior is intentional or a serious violation

Enter a reason for the resolution. Resolution actions are recorded in Case notes, and the case status is updated to Closed.





![[Pasted image 20260828164111.png]]
![[Pasted image 20260828164123.png]]
# Summary
Investigating insider risk requires more than reviewing a single alert. It demands tools and workflows that provide insight into user behavior, risk indicators, and broader patterns of activity.

In this module, you learned how Microsoft Purview Insider Risk Management supports that process by:

- Providing the Alerts dashboard for structured triage and prioritization
- Offering context through the All risk factors tab, Activity explorer, and User activity views
- Enabling deeper review and coordinated response through cases
- Connecting alert data to Microsoft Defender XDR for broader investigation
- Supporting advanced queries with hunting tools for detailed behavioral analysis

Together, these tools help analysts and investigators move from initial detection to informed response. With this approach, organizations can respond more effectively to insider risks and reduce the time it takes to identify and act on meaningful threats.


# Conduct investigations with Microsoft Purview Audit
# Introduction
Microsoft Purview Audit records what users and administrators do across Microsoft 365 so you can answer questions about access, deletions, admin changes, and AI app activity.

Consider a network of healthcare facilities that manages a large amount of sensitive patient data daily. After noticing unusual access patterns to their electronic health record (EHR), they need to confirm all access is authorized and aligns with health data protection regulations. The compliance team uses Microsoft Purview Audit to **trace who accessed which records**, then hands those findings to the analysts who compare them to approved access patterns.

# Understand how Microsoft Purview Audit works

Microsoft Purview Audit records much of what users and administrators do in Microsoft 365. That includes sending mail, sharing a file, changing a setting, and prompting Copilot. You investigate incidents and answer compliance questions by searching those records. Coverage isn't uniform across every service, and some workloads log less than others, so an empty result doesn't always mean the activity didn't happen.

To run useful searches, you first need a working model of how audit records are created, stored, and retrieved.

## Vocabulary that carries through every search

==Two terms show up in every audit search== you'll run. _Record type_ is the category the activity belongs to, like `SharePointFileOperation` or `Copilot`. _Operation_ is the specific action, like `FileAccessed` or `CopilotInteraction`. Those are the filter values you'll reach for again and again.

## One log, many services

==All Microsoft 365 workloads ==write to the same unified audit log. Exchange, SharePoint, OneDrive, Teams, Microsoft Entra ID, and Microsoft Copilot all go to the same place. One search interface answers questions that span mail, files, admin changes, and AI app activity at the same time.

## Two things that shape what your searches can find

- **Enablement timing**. ==Records exist only from the moment auditing was turned on==. That applies at both the tenant level and, for Audit (Premium) events like `MailItemsAccessed`, at the per-user level. Turning auditing on today doesn't ==backfill== yesterday.
- **Retention**. Records age out on a schedule that depends on your tier and any retention policies you create. The== default is 180 days for most activity.==

## Where you work

The same audit log is exposed through the Microsoft Purview portal, the `Search-UnifiedAuditLog` cmdlet in Exchange Online PowerShell, and the Office 365 Management Activity and Audit Search Graph APIs.

## What the tiers change

Audit (Standard) covers thousands of activities across Microsoft 365 with 180-day default retention. Audit (Premium) adds the capabilities most investigations lean on: retention policies, longer default retention for key workloads, high-value events like `MailItemsAccessed` that show which specific messages a user opened, and higher bandwidth for the Management Activity API.

|Capability|Audit (Standard)|Audit (Premium)|
|---|---|---|
|Search user and admin activity across Microsoft 365|✔|✔|
|Default retention|180 days|180 days, or 1 year for Microsoft Entra ID, Exchange, SharePoint, and OneDrive|
|Audit log retention policies up to 10 years||✔|
|High-value events, such as `MailItemsAccessed`||✔|
|Higher Management Activity API bandwidth||✔|

The tier your organization has decides which questions the audit log can answer. The interface you use to ask questions stays the same across both tiers.

For current licensing details, see [Microsoft Purview auditing solutions](https://learn.microsoft.com/en-us/purview/audit-solutions-overview#licensing-requirements).

## What audit isn't

Audit is built for searching records of past activity. It isn't the tool for real-time monitoring, alerting, applying holds, preventing actions, or scoring behavior. Those jobs belong to other Microsoft Purview and Microsoft security tools that pair with audit in real investigations.

| Capability                                                                                                                                                                  | Which parts of this module apply                                                                                  |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| [Audit (Standard)](https://learn.microsoft.com/en-us/purview/audit-solutions-overview), on by default for eligible Microsoft 365 and Office 365 subscriptions               | All units                                                                                                         |
| [Audit (Premium)](https://learn.microsoft.com/en-us/purview/audit-solutions-overview) with the **Microsoft 365 Advanced Auditing** service plan enabled per user            | Audit log retention policies, intelligent insights like `MailItemsAccessed`, higher API bandwidth                 |
| **10-Year Audit Log Retention** add-on license, assigned per user                                                                                                           | Long-term retention beyond one year                                                                               |
| [Microsoft Purview pay-as-you-go billing](https://learn.microsoft.com/en-us/purview/purview-billing-models) enabled, with the tenant linked to an active Azure subscription | Audit records for user interactions with non-Microsoft AI apps, captured under the `AIAppInteraction` record type |
| **Audit Logs** or **View-Only Audit Logs** role, granted through the **Audit Manager** or **Audit Reader** role group in the Microsoft Purview portal                       | Running any search or export in the portal or with `Search-UnifiedAuditLog`                                       |

![[Pasted image 20260907144919.png]]
# Configure and manage Microsoft Purview Audit
Before anyone runs an audit search, the tenant has to be set up. Setup means confirming auditing is on and assigning the roles that let people search the log. For Audit (Premium) tenants, setup also includes enabling Advanced Auditing per user. In large or delegated-admin environments, someone also scopes which users each searcher can see.

Even if you don't run setup yourself, know what setup shapes. Per-user Advanced Auditing decides whether the Premium events an investigation looks for exist at all. Admin-unit scoping decides which users your searches can return. In the healthcare compliance team's investigation, both matter. Without Advanced Auditing on the physician's account, the message-level events aren't there to find. Without the right role scope, the team might not see logs for users in the affected clinic.

## Setup that applies to every tenant

### Confirm auditing is enabled

Audit logging is enabled by default for Microsoft 365 tenants, recording user and admin activities and retaining them for 180 days unless longer retention is configured. For new organizations, verify auditing is active.

 Note

The PowerShell examples throughout this module use the `ExchangeOnlineManagement` module. Install it once with `Install-Module ExchangeOnlineManagement`, then connect with `Connect-ExchangeOnline` before running any command.

To check status in Exchange Online PowerShell:

PowerShell

```
Get-AdminAuditLogConfig | Format-List UnifiedAuditLogIngestionEnabled
```

If the result is `False`, enable auditing before continuing. In the Microsoft Purview portal, select **Audit**. If a banner prompts you to start recording activity, select it. Enablement can take up to 60 minutes to take effect. To enable via PowerShell instead:

PowerShell

```
Connect-ExchangeOnline
Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
```

Turning auditing off is rare and only available in PowerShell:

PowerShell

```
Connect-ExchangeOnline
Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
```

### Assign permissions to search the audit log

Authorized staff need the **Audit Logs** or **View-Only Audit Logs** role in the Microsoft Purview portal. These roles are included in the **Audit Reader** and **Audit Manager** role groups:

- **Audit Manager**: search and export audit logs, and manage audit settings including enabling or disabling logging.
- **Audit Reader**: search and export audit logs, without changing audit settings.

## Additional setup for Audit (Premium)

Two more pieces apply if your tenant has Audit (Premium) and you want to use its high-value events.

### Enable Advanced Auditing for the users who need it

Audit (Premium) events like `MailItemsAccessed`, `Send`, `SearchQueryInitiatedExchange`, and `SearchQueryInitiatedSharePoint` require the **Microsoft 365 Advanced Auditing** service plan turned on for each user. Microsoft 365 E5, Office 365 E5, and E5 Compliance licensing include the service plan, but it isn't turned on automatically. Someone still has to enable it per user for those events to start logging.

1. In the **Microsoft 365 admin center**, go to **Users** > **Active users**, then select a user.
2. On the user properties page, select **Licenses and apps**. Verify the user is licensed for Audit (Premium).
3. In **Apps**, make sure **Microsoft 365 Advanced Auditing** is selected. If not, select it and save changes.

Assignment typically propagates in 15 to 30 minutes, and full logging can take up to 24 hours to begin. Records exist only from the enablement date forward.

### Re-enable customized mailbox audit events

Skip this section for most tenants. It only applies if someone previously customized the mailbox actions audited on user or shared mailboxes. When that happened, new Audit (Premium) events released by Microsoft aren't added automatically, so you have to re-enable them.

To restore the search-query events on a mailbox, run this in Exchange Online PowerShell:

PowerShell

```
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

 Note

In multi-geo tenants, run the command in the region where the user's mailbox is hosted. If the event was enabled in another region before, remove it there and then add it again in the correct region.

## Scope audit access with administrative units

Skip this section if your tenant is small or centrally administered. It applies when you delegate audit search to different teams or regions and need to restrict what each team can see.

Use **administrative units** to restrict which users' audit logs someone can search:

- **Unrestricted admins**, the default assignment with no admin unit, can search all audit logs, including logs from nonuser and system accounts.
- **Restricted admins**, meaning admins assigned one or more admin units, can search only audit logs for users in their assigned admin units.

A few audit activities are visible only to unrestricted admins, including Azure Information Protection `Discover`, Dynamics 365 `CrmDefaultActivity`, Endpoint data loss prevention (DLP) file events, Exchange `Set-Mailbox` and `Set-MailboxPlan`, and Microsoft Forms `ViewRuntimeForm`. To search for these activities, use an unrestricted admin account or the `Search-UnifiedAuditLog` cmdlet.

![[Pasted image 20260907160702.png]]

# Configure audit retention with Audit (Premium)
Retention policies are an Audit (Premium) capability that determine how far back an audit search can reach. If your tenant only has Audit (Standard), records are kept for the default 180 days with no policy to manage.

Because policies apply forward from the time you create them, retention is a planning step. You configure it before you need the data, not when an investigation starts.

For the healthcare compliance team's investigation, retention is what decides whether records from six or eight months ago are still there to search. A tenant on Audit (Standard) retention alone loses most non-Entra, non-Exchange, non-SharePoint, and non-OneDrive records at 180 days. A tenant with Audit (Premium) and a custom retention policy can hold Copilot and other high-value records for the full lookback window a healthcare investigation typically needs.

## Audit log retention policies

In Microsoft Purview Audit (Premium), retention policies define how long audit records are kept, for up to 10 years. Policies can be scoped by:

- All activities across one or more Microsoft 365 services
- Specific activities within a service, for all or selected users
- Priority level to control which policy applies when more than one could apply

## Default retention policy

Audit (Premium) provides a default retention policy that retains audit records from Microsoft Entra ID, Exchange, OneDrive, and SharePoint for one year. This default can't be modified, but you can create custom policies for other workloads or to set different durations for specific record types.

## Considerations for retention policies

Before creating a policy, keep in mind:

- **Required role**: You need the **Organization Configuration** role in the Microsoft Purview portal to create or edit policies.
- **Policy limit**: Each organization can have up to 50 retention policies.
- **Policy priority**: Custom policies override the default for covered records.
- **Data retention timing**: Retention is determined when the record is created. Policy or license changes affect only new records.
- **Non-user activity**: Audit records generated by nonuser entities such as service principals, system events, and application activities are retained for a fixed one year. This retention isn't configurable and custom retention policies don't apply.

## Choose a retention duration

Durations run from 7 days to 10 years. Which one you pick depends on:

- **Regulatory scope**. Healthcare, financial, and government data often carry specific retention requirements. Match the policy duration to what applies to your organization and the workload the policy covers.
- **Investigation lookback needs**. If your incident response process routinely reaches back 6 to 12 months, set the duration to cover that. Retention only helps if records are there when you go looking.
- **Priority planning**. Custom policies override the default for the records they cover. Lower priority numbers win, so use them for narrowly scoped policies on critical users or record types, and higher numbers for broader safety-net policies.

## Create an audit log retention policy

You can create retention policies in the Microsoft Purview portal.

1. Sign in to the [Microsoft Purview](https://purview.microsoft.com/) portal with an account that has the **Organization Configuration** role.
    
2. Go to **Solutions** > **Audit** > **Audit retention policies**.
    
3. Select **Create audit retention policy**, then complete the fields:
    
    - **Policy name**: Unique name for the policy
    - **Description**: Optional short description
    - **Users**: Apply to all users or specific ones
    - **Record type**: Choose the type of audit record. Multiple types can't have activity-specific selections
    - **Duration**: Choose the retention period, from 7 days to 10 years
    - **Priority**: Set the priority, where lower numbers have higher priority ![Screenshot showing the new audit retention policy flyout page.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-audit-search-investigate/media/audit-create-new-audit-retention-policy.png)
4. Select **Save**.
    

## Manage policies in the Microsoft Purview Portal

Once created, policies appear in the **Audit retention policies** dashboard. You can view, edit, or delete them, and adjust priority as needed.

![Screenshot showing the priority column in the Audit retention policies dashboard.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-audit-search-investigate/media/audit-log-retention-dashboard-priority.png)

## Manage retention policies using PowerShell

For scripted management, use [Security & Compliance PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-scc-powershell). Retention policies use the standard verb pattern: `New-`, `Get-`, `Set-`, and `Remove-UnifiedAuditLogRetentionPolicy`.

Here's an example that creates a 10-year retention policy for Microsoft Teams activity:

PowerShell

```
New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "10-year retention policy for Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration TenYears -Priority 100
```

For the full parameter set for each cmdlet, see the [`New-UnifiedAuditLogRetentionPolicy` reference](https://learn.microsoft.com/en-us/powershell/module/exchange/new-unifiedauditlogretentionpolicy).

 Note

Deleting a policy with `Remove-UnifiedAuditLogRetentionPolicy` can take up to 30 minutes to propagate. Records already retained under the deleted policy fall back to the default retention on their next evaluation, so records you thought were held for years can age out earlier than expected.

![[Pasted image 20260907161614.png]]

# Run audit searches with Audit (Standard)

An audit search starts with confirming that auditing is on. Once it is, scope the search with the right filters, manage the jobs that run in the background, and read the results the portal returns.

## Prepare to search the audit log

Confirm three things before you run a search:

1. **Auditing is enabled**. Run the following in Exchange Online PowerShell. If `UnifiedAuditLogIngestionEnabled` returns `True`, you're set.
    
    PowerShell
    
    ```
    Get-AdminAuditLogConfig | Format-List UnifiedAuditLogIngestionEnabled
    ```
    
2. **You have the right role**. You need **Audit Logs** or **View-Only Audit Logs**, included in the **Audit Manager** and **Audit Reader** role groups on the **Permissions** page in the Microsoft Purview portal.
    
3. **The retention window covers your date range**. Users with a Microsoft 365 E5 or equivalent license get one-year retention for Microsoft Entra ID, Exchange, SharePoint, and OneDrive activity. Other users get the default 180 days.
    

 Note

A few things surprise investigators on their first real search:

- **Latency**: Records from core services like Exchange, SharePoint, OneDrive, and Teams are typically available 60 to 90 minutes after the activity. Other services can take longer.
- **Time zones**: Portal search results and `Search-UnifiedAuditLog` timestamps use UTC. Convert your incident window to UTC before you set a date range, or you'll miss activity that fell outside your intended hours.
- **One-year cap on non-user activity**: Records for service principals, application permissions, and system events age out after one year regardless of tier or retention policy. No policy raises that cap, so investigations that reach further back into those categories won't return records.

## Conduct an audit search

Once your environment is ready, you can search the audit log in the Microsoft Purview portal.

1. Sign in to the [Microsoft Purview](https://purview.microsoft.com/) portal.
    
2. Select **Solutions** > **Audit**.
    
3. Configure your search parameters:
    
    |Parameter|What it does|
    |---|---|
    |**Date range**|Defaults to the last seven days. Adjust up to the retention limit for your license.|
    |**Keyword Search**|Enter keywords or phrases. Use `*` for wildcard matches.|
    |**Admin Units**|Select specific admin units, or leave blank for all.|
    |**Activity types**|Choose from friendly names or operation names.|
    |**Record types**|Filter by service-specific record types.|
    |**Search name**|Name the search for future reference.|
    |**Users**|Specify individual accounts, or leave blank for all.|
    |**File, folder, or site**|Enter names or URLs to filter by location. Use `*` for wildcards.|
    |**Workloads**|Narrow to specific Microsoft services.|
    
4. Select **Search** to run the query. You can run up to 10 concurrent search jobs per user, with a limit of one unfiltered search job. If the limit is reached, wait for a job to finish or delete one.
    

## Manage audit search jobs

Search jobs run in the background, so you can close the browser and return later. In large tenants, a broadly scoped search with wide date ranges, many users, or high activity volumes can take up to 48 hours to complete. If a search stays at 0% progress for more than an hour, or doesn't advance in a full day, treat it as stuck. Delete it and rerun with a narrower scope.

The search job dashboard displays:

- **Search name**
- **Job status**: _Queued_, _In Progress_, or _Completed_
- **Progress (%)**
- **Search time**: Time taken to complete
- **Total results**
- **Creation time** (UTC)
- **Search performed by**: Account that initiated the search

[![Screenshot showing the results of an Audit search overview in Microsoft Purview.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-audit-search-investigate/media/audit-new-search-columns.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-audit-search-investigate/media/audit-new-search-columns.png#lightbox)

You can delete a search job to remove its definition and results without affecting the underlying audit data. Use **Copy this search** to duplicate a job with the same parameters.

 Note

Completed audit search jobs are stored in the portal for **30 days**. You can reopen results or re‑export without rerunning the search.

### View detailed search results

Select a specific search job to see item-level details:

- **Date (UTC)**
- **IP Address**
- **User**
- **Record type**
- **Activity**
- **Item**
- **Admin Units**
- **Details**

You can sort, filter, or export this information. A single export supports up to 50,000 rows for Audit (Standard) and up to 1,000,000 rows for Audit (Premium).

[![Screenshot showing the search job item detail dashboard.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-audit-search-investigate/media/audit-new-search-result-details.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-audit-search-investigate/media/audit-new-search-result-details.png#lightbox)

## When a search returns nothing

Empty results are usually a setup issue, not a search issue. Walk down this list before you rerun:

1. **Auditing is enabled tenant-wide**. Confirm with `Get-AdminAuditLogConfig | Format-List UnifiedAuditLogIngestionEnabled`. If it returns `False`, no records exist for the search window.
2. **Your date range falls inside the retention window**. Users with a Microsoft 365 E5 or equivalent license get one-year retention for Microsoft Entra ID, Exchange, SharePoint, and OneDrive. Other users get 180 days.
3. **The activity is recent enough to be indexed**. Core-service records take 60 to 90 minutes to appear. If the activity happened moments ago, wait and rerun.
4. **Advanced Auditing is enabled on the user**, and was enabled during the window you're searching. Required for `MailItemsAccessed`, `Send`, `SearchQueryInitiatedExchange`, and `SearchQueryInitiatedSharePoint`. Records only exist from the per-user enablement date forward.
5. **Your role covers what you're searching for**. You need **Audit Logs** or **View-Only Audit Logs**. If your account is scoped to an administrative unit, it only sees logs for users in that unit.
6. **Your date range is in UTC**. Portal results and `Search-UnifiedAuditLog` interpret dates as UTC, not your local time zone.

## Scenario: Investigating unauthorized access to patient records

The healthcare compliance team begins its investigation with Audit (Standard). Their first question: did anyone delete email messages related to the flagged patient records, and if so, were those deletions authorized?

Steps in the investigation:

1. **Define search criteria**:
    
    - Activities: Under **Exchange mailbox activities**, select **Deleted messages from Deleted Items folder** and **Purged messages from mailbox**.
    - Date range: Match the suspected activity period.
    - Users: Focus on accounts with unusual access patterns.
2. **Run the search**:
    
    - In the Microsoft Purview portal, run a new search with the defined criteria.
    - Review for suspicious patterns such as bulk deletions or activity outside normal duties.
3. **Analyze results**:
    
    - Check the time of deletion, IP address, and user details.
        
    - For soft- or hard-deleted items, open the record's **Details** and view **More information** for context like the subject line and original location.
        
        **Example of a soft-deleted item**:
        
        ![Screenshot showing the audit record for a soft-deleted item.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-audit-search-investigate/media/soft-deleted-item.png)
        
        **Example of a hard-deleted item**:
        
        ![Screenshot showing the audit record for a hard-deleted item.](https://learn.microsoft.com/en-gb/training/wwl-sci/purview-audit-search-investigate/media/hard-deleted-item.png)
        
4. **Take corrective action**:
    
    - If unauthorized deletions are confirmed, follow incident response procedures.
    - If deletions were valid but flagged due to unusual volume or timing, adjust monitoring thresholds to reduce false positives.

### Recovery options

- SoftDeleted items can be restored from the Recoverable Items folder until they reach the mailbox's deleted-item retention limit.
- HardDeleted items might be recoverable if the mailbox is on hold or covered by a retention policy.
- Use Microsoft Purview portal search tools to locate and recover items where possible.
![[Pasted image 20260909171435.png]]

# Investigate activities with Audit (Premium)

To confirm which individual messages a user opened, an investigation needs the `MailItemsAccessed` event from Audit (Premium). That event captures message-level access details that Audit (Standard) doesn't record. Working with it means understanding when Exchange records a bulk sync operation instead of individual bind events, and when throttling can create gaps in the log. It also means seeing how the healthcare compliance team applies those results to investigate unusual electronic health record (EHR) access.

## Investigate compromised accounts with MailItemsAccessed

**MailItemsAccessed** provides detailed records of how and when emails are accessed, making it a critical event type for investigations involving sensitive communications.

### Understand sync and bind access

- **Sync access**: Logs a single event when multiple emails are downloaded during a session, like when using Outlook.
- **Bind access**: Logs each time an individual email is opened or interacted with.

### Manage audit log volume

To maintain performance, Exchange Online throttles MailItemsAccessed logging if a mailbox logs more than 1,000 bind events in 24 hours. Throttling:

- Affects less than 1% of mailboxes
- Only pauses logging for MailItemsAccessed events, not other activities
- Applies to bind operations only. Sync activities aren't affected.
- Might result in gaps where bind events weren't recorded

If your investigation window overlaps a throttled period, the missing bind events don't backfill . Cross-reference the gap with **Exchange message trace** or **Microsoft Entra sign-in logs** ==to reconstruct what happened. If the question is "what was the user searching for" rather than "what did they open," `SearchQueryInitiatedExchange` and `SearchQueryInitiatedSharePoint` aren't throttled and can help fill the gap.==

### Scenario: Investigate using MailItemsAccessed in a healthcare setting

The Standard-tier mailbox search confirmed unauthorized deletions but not which specific patient messages the physician opened. To close that gap, the healthcare compliance team turns to `MailItemsAccessed`. Here's how they proceed:

1. **Set up and pull the data**:
    
    Identify the mailboxes linked to users who have access to sensitive patient data. Define the time period the suspicious activities were detected, converted to UTC. Then use the `Search-UnifiedAuditLog` cmdlet to pull the `MailItemsAccessed` records for that window:
    
    PowerShell
    
    ```
    $log = Search-UnifiedAuditLog -StartDate "2026-01-06" -EndDate "2026-01-20" -UserIds "user1, user2" -Operations MailItemsAccessed -ResultSize 1000
    ```
    
    `-StartDate` and `-EndDate` are interpreted as UTC. `-ResultSize` counts audit events, not mail items, so raise it or narrow the date range if you expect more than 1,000 records. `Search-MailboxAuditLog` is being deprecated in Exchange Online in favor of `Search-UnifiedAuditLog`.
    
2. **Slice the results to answer specific questions**:
    
    Pipe `$log` into a `Where-Object` filter that matches the property you want to check.
    
    Given the sensitivity of the data, start with a throttling check to confirm no gaps in the log:
    
    PowerShell
    
    ```
    $log | Where {$_.AuditData -like '*"IsThrottled","Value":"True"*'} | FL
    ```
    
    Then look at sync access, which is how Exchange logs bulk downloads that pull folders of messages:
    
    PowerShell
    
    ```
    $log | Where {$_.AuditData -like '*"MailAccessType","Value":"Sync"*'} | FL
    ```
    
    And at bind access, which shows the specific messages the user opened:
    
    PowerShell
    
    ```
    $log | Where {$_.AuditData -like '*"MailAccessType","Value":"Bind"*'} | FL
    ```
    
3. **Contextual analysis of access**:
    
    Compare IP addresses and session IDs to separate regular user actions from unusual or unauthorized access. The comparison narrows down how, and sometimes why, the access happened.
    
4. **Forensic recovery and reporting**:
    
    For each bind access event where an email was opened, identify the affected emails using their `InternetMessageId`. Check whether they contain sensitive patient data. Record findings clearly for healthcare compliance rules and use the documentation to guide response and future protections.
    

### Manage duplicate audit records

In high-activity environments, duplicate audit records can clutter and complicate log analysis. Audit (Premium) filters out duplicate `MailItemsAccessed` records within a one-hour window, so investigators see meaningful activity instead of the same access repeated dozens of times. A new record still gets logged when properties that change the context of the access differ, like `ClientIPAddress`, `SessionId`, or `MailAccessType`.

For the full list of properties that break the deduplication window, see [Filter duplicate audit records](https://learn.microsoft.com/en-us/purview/audit-log-investigate-accounts#filter-duplicate-audit-records).

## Other Audit (Premium) events worth knowing

==`MailItemsAccessed`== is the flagship Premium event, but the tier logs other high-value events that let you answer questions Audit (Standard) can't:

- **`Send`**: Records each time a user sends or replies to a mail item. If you're confirming whether a compromised account was used to send messages during a suspected timeframe, this is the event to filter on.
    
    PowerShell
    
    ```
    Search-UnifiedAuditLog -StartDate "2026-01-06" -EndDate "2026-01-20" -UserIds "user1" -Operations Send -ResultSize 1000
    ```
    
- **`SearchQueryInitiatedExchange`** and **`SearchQueryInitiatedSharePoint`**: Record the search terms a user runs against their mailbox or against SharePoint sites. Both help reconstruct what a user was looking for around the time of an incident.
    
    PowerShell
    
    ```
    Search-UnifiedAuditLog -StartDate "2026-01-06" -EndDate "2026-01-20" -UserIds "user1" -Operations SearchQueryInitiatedExchange,SearchQueryInitiatedSharePoint -ResultSize 1000
    ```
    

Like `MailItemsAccessed`, these events only log for users with Microsoft 365 Advanced Auditing enabled, and only from the date of enablement forward.

Message-level events show which patient messages the physician opened, but the investigation still doesn't know whether the same records were reached through any other channel. Copilot and AI app activity is where the healthcare compliance team looks next.

![[Pasted image 20260916134940.png]]




# Search for Copilot and AI app activities
The mailbox investigation confirmed which patient messages the physician opened. It didn't answer whether the same patient records were reached through Copilot or a connected AI app. To close that gap, the healthcare compliance team runs an audit search for AI activity. The flow is the same one that works for any Microsoft 365 workload. What changes is the set of record types, operations, and properties you filter on.

Microsoft Purview Audit captures metadata for Copilot and AI application activity: who was involved, when and where the activity occurred, and which Microsoft 365 resources were referenced. This metadata answers questions like "Which user prompted Copilot?", "Which files did Copilot access to answer?", and "Did the prompt attempt a jailbreak?" Audit doesn't capture the actual prompt or response text. To review that content, pair audit data with Microsoft Purview Data Security Posture Management (DSPM), Communication Compliance, or eDiscovery.

## What to filter on

Copilot and AI interactions map to three record types. Filter by these when you search:

|Record type|Workload|Covers|
|---|---|---|
|`CopilotInteraction`|`Copilot`|First-party Microsoft Copilot experiences, such as Microsoft 365 Copilot, Copilot Chat, Security Copilot, and Copilot in Fabric.|
|`ConnectedAIAppInteraction`|`ConnectedAIApp`|Custom Copilots built with Microsoft Copilot Studio and non-Microsoft AI apps registered in your tenant.|
|`AIAppInteraction`|`AIApp`|Non-Microsoft AI apps used outside your tenant, captured through browser or network data loss prevention (DLP).|

### What each record type depends on

Not every record type appears in audit search on the strength of auditing alone. `CopilotInteraction` records show up as soon as auditing is enabled for the user. The other two rely on tools outside audit itself:

- **`ConnectedAIAppInteraction`** relies on Microsoft Entra registration and onboarding through DSPM. Copilot Studio agents and other Entra-registered AI apps only produce these records once they're onboarded. If a search for a known agent returns nothing, check whether it was onboarded before you dig into the search itself.
- **`AIAppInteraction`** relies on the Microsoft Purview Browser Extension on user devices plus DLP policies that inspect AI app traffic. Prompts a user sends to a non-Microsoft AI website in a browser don't reach audit search unless that pipeline is deployed.

 Note

`AIAppInteraction` records, and the non-Microsoft Entra-registered app scenarios under `ConnectedAIAppInteraction`, are billed through Microsoft Purview [pay-as-you-go billing](https://learn.microsoft.com/en-us/purview/purview-billing-models). The tenant needs to be linked to an active Azure subscription and pay-as-you-go features have to be enabled before those records start ingesting. Copilot Studio agents are excluded.

For the setup steps, see [Use Microsoft Purview to manage data security and compliance for Entra-registered AI apps](https://learn.microsoft.com/en-us/purview/ai-entra-registered) and [Use Microsoft Purview to manage data security and compliance for other AI apps](https://learn.microsoft.com/en-us/purview/ai-other-apps).

### If a Copilot search returns nothing

Start with the standard empty-result checklist that covers auditing state, retention window, latency, role scope, and UTC dates. If those all check-out, two AI-specific dependencies are usually the cause:

1. **For `ConnectedAIAppInteraction`**: the agent or AI app is onboarded through DSPM. Records don't appear until onboarding completes, so a search for a known agent returns nothing if you're searching a window before onboarding, or if onboarding never happened.
2. **The user needs a Copilot license** covering the interaction, and the record type has to match what they actually did. First-party Copilot use produces `CopilotInteraction`. A Copilot Studio agent or Entra-registered AI app produces `ConnectedAIAppInteraction`. A non-Microsoft AI website in a browser produces `AIAppInteraction`, and that one also requires the Microsoft Purview Browser Extension on the device plus a DLP policy inspecting AI app traffic.

### Admin operations to watch for

User interactions map to those three record types. Admin activity around Copilot shows up under separate operations, including `UpdateTenantSettings`, `CreatePlugin`, `DeletePlugin`, and `EnablePromptBook`. Filter on these when the question is who changed a Copilot setting or managed a plugin or agent, not who used Copilot.

### Questions an AI investigation asks

Each investigation question maps to a specific property in the audit record. When you have search results and need to narrow down what happened, use the property listed with the question you're trying to answer.

**Questions you'll ask on most investigations:**

- **Which app was the user interacting with?** `AppIdentity`. Format is `workloadName.appGroup.appName`, for example `Copilot.MicrosoftCopilot.Microsoft365Copilot` or `Copilot.Security.SecurityCopilot`.
- **Which files or sites did Copilot look at to answer?** `AccessedResources`. Each entry includes `SiteUrl`, `Name`, `Type`, and `SensitivityLabelId`, so you can also see whether Copilot touched sensitivity-labeled content.
- **Did a prompt try to jailbreak?** Look for the `JailbreakDetected` flag inside `Messages`. Prompt and response pairs live in `Messages` too.

**Questions for specific scenarios:**

- **Where was the user when they interacted?** `AppHost`:
    
    |`AppHost` value|Where the user was|
    |---|---|
    |`BizChat`|Microsoft 365 Copilot Chat, Teams, or `microsoft365.com/copilot`|
    |`Bing`|Microsoft Edge browser or Office mobile|
    |`Office`|`office.com` or `microsoft365.com`|
    |`Word`, `Excel`, `PowerPoint`, `Stream`|The named app|
    
- **What was the user doing during the interaction?** `Contexts`, such as the document they had open at the time.
    
- **Was a Copilot Studio agent involved?** `AgentName` and `AgentVersion`.
    

## Run a search for AI app activities

The portal flow is the same as any audit search: **Solutions** > **Audit** > configure > **Search**. Two fields carry the Copilot-specific picks:

- **Activities - friendly names**: expand **Copilot activities**, or type _Copilot_ in the search box.
    
    [![Screenshot showing Interacted with Copilot selected under Activities - friendly names.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-audit-search-investigate/media/audit-copilot-new-search-activities.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-audit-search-investigate/media/audit-copilot-new-search-activities.png#lightbox)
    
- **Record types**: select `CopilotInteraction`, `ConnectedAIAppInteraction`, or `AIAppInteraction`. Type _Copilot_ or _AI_ in the search box to filter the list.
    
    [![Screenshot showing CopilotInteraction selected under Record types.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-audit-search-investigate/media/audit-copilot-new-search-record-type.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-audit-search-investigate/media/audit-copilot-new-search-record-type.png#lightbox)
    

 Note

Copilot audit records take the same 60 to 90 minutes to appear as records from core Microsoft 365 services. If you searched right after prompting Copilot, wait and try again.

 Tip

To find all activity for a specific `AppIdentity`, first search and export the Copilot audit records by operation name, then filter the exported results on `AppIdentity` in Excel or Power Query.

## Scenario: Extend the healthcare investigation to Copilot activity

With the mailbox thread wrapped up, the healthcare compliance team turns to Copilot activity. The question now is whether Copilot or a connected AI app referenced any of the same patient records the physician had accessed. To answer, the team:

- Filters on the `CopilotInteraction` and `ConnectedAIAppInteraction` record types, scoped to the same users and date range as the mailbox investigation.
- Reviews the `AccessedResources` property on returned records to identify patient files Copilot read to answer prompts, and checks each file's `SensitivityLabelId`.
- Scans the `Messages` property for `JailbreakDetected` flags, which mark prompts that tried to bypass safeguards.
- Exports the results so they can be joined with the mailbox findings by user, resource, and time window.

![[Pasted image 20260916140525.png]]

# Analyze and report on audit results
An investigation ends with someone acting on findings, not with a search result on screen. That last step means getting the records out of the portal into a format you can sort, correlate with other logs, and hand to whoever asked the question. Both Standard and Premium export search results to CSV. What matters here is how you turn that CSV into report-ready data.

For the healthcare compliance team, this is where the mailbox deletions from Standard-tier searches, the Copilot patient-file access, and the physician's `MailItemsAccessed` records converge. Scattered searches become a single sortable table the compliance officer and clinical leadership can act on.

## Get records out of the portal

After running an audit log search in the Microsoft Purview portal, you can export the results for offline analysis.

1. Run your audit search with the desired filters.
    
2. On the search results page, select **Export** to download the audit records to a CSV file.
    
    ![Screenshot showing where to select Export to export data.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-audit-search-investigate/media/audit-export-audit-search-results.png)
    
3. Once the export finishes, save the file locally.
    
    - A single export supports up to 50,000 rows for Audit (Standard) and up to 1,000,000 rows for Audit (Premium). If your results exceed the limit, narrow the date range or apply more filters.

## Parse the export into a report-ready table

The exported CSV puts most of the useful detail inside a single `AuditData` column formatted as JSON, which is hard to read as-is. In Excel's Power Query Editor, you can parse that column into structured fields such as `SiteUrl`, `AccessedResources`, and `SensitivityLabelId`, then load the expanded table back into Excel for sorting and filtering.

The short version:

1. Open the exported CSV in Excel and select **Transform Data** to open Power Query.
2. Right-click the **AuditData** column, choose **Transform** > **JSON**, then use the expand icon to promote the JSON properties into columns.
3. Deselect properties you don't need, then **Close & Load** to return the flattened data to Excel.

For the full walkthrough with screenshots, see [Export, configure, and view audit log records](https://learn.microsoft.com/en-us/purview/audit-log-export-records).

## Turn the parsed table into a finding

Parsing gets the data into a shape you can analyze. The analysis is what turns records into a finding.

The healthcare investigation's last question was whether Copilot referenced the same patient records the physician had opened directly. With both exports parsed in Excel, the team answers it by joining across the two tables:

1. Filter the Copilot export to rows where `AccessedResources` includes a patient record identifier or a `SensitivityLabelId` that matches the labeled patient data set.
2. Filter the `MailItemsAccessed` export to rows for the same users and time window, expanding `Folders[].FolderItems[]` down to individual messages.
3. Join the two filtered tables on user, resource identifier, and a time window loose enough to catch records that landed within a few minutes of each other.

Rows where both tables match mean the same patient record was reached through mail _and_ through Copilot by an account already flagged for review. That's the finding the compliance officer hands to clinical leadership, and it's a much shorter list than either export on its own.

The same pattern applies beyond healthcare. Once the CSV is parsed, any investigation that spans record types follows the same two steps. Filter each table on the property that identifies the resource, then join on user, resource, and time window.

## Search and export at scale with PowerShell

For more control over your audit searches and exports, use the `Search-UnifiedAuditLog` cmdlet in Exchange Online PowerShell.

### Example: Export SharePoint sharing operations

PowerShell

```
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2025 -EndDate 06/30/2025 -RecordType SharePointSharingOperation
$auditlog | Select-Object CreationDate, UserIds, RecordType, AuditData | Export-Csv -Path C:\AuditLogs\SharePointAudit.csv -NoTypeInformation -Encoding UTF8
```

To append more data:

PowerShell

```
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2025 -EndDate 06/30/2025 -RecordType SharePointFileOperation
$auditlog | Select-Object CreationDate, UserIds, RecordType, AuditData | Export-Csv -Append -Path C:\AuditLogs\SharePointAudit.csv -NoTypeInformation -Encoding UTF8
```

 Tip

`-Encoding UTF8` keeps non-ASCII characters in user names, folder paths, and Copilot content readable. Without it, Windows PowerShell defaults to ASCII and those characters can display as garbage in Excel. Use `UTF8BOM` if Excel still has trouble detecting the encoding.

 Note

`Search-UnifiedAuditLog` returns a maximum of 5,000 rows per call and 100 by default. The one-shot examples above silently truncate at 5,000 rows on larger date ranges. For larger exports, page through results with the `-SessionId` and `-SessionCommand ReturnLargeSet` parameters. See the [`Search-UnifiedAuditLog` reference](https://learn.microsoft.com/en-us/powershell/module/exchange/search-unifiedauditlog) for the pagination pattern.

## Tips for exporting and reviewing audit data

- **Filter by RecordType** to focus on specific workloads.
- **Filter by Operations** to narrow results to key actions, such as file sharing or deletion.
- Use Power Query transformations to make JSON data in the **AuditData** column easier to read.
![[Pasted image 20260916141744.png]]

![[Pasted image 20260916142526.png]]

![[Pasted image 20260916142544.png]]

![[Pasted image 20260916142558.png]]

![[Pasted image 20260916142725.png]]

# Summary

You started this module with a healthcare compliance team facing an electronic health record (EHR) access pattern that needed answers. You now have the audit skills that team relied on: knowing what Microsoft Purview Audit records, how long it retains those records, and how to search them from the portal and PowerShell for regular activity, Copilot and AI app activity, and message-level access.

Here's what you covered:

- How Microsoft Purview Audit records, retains, and exposes activity across Microsoft 365, and where Audit (Standard) and Audit (Premium) differ.
- Configuring a tenant for audit, including per-user Advanced Auditing where Audit (Premium) is in use.
- Planning audit log retention to match compliance requirements.
- Running audit searches from the Microsoft Purview portal and with `Search-UnifiedAuditLog` to surface evidence of user and admin activity.
- Extending the same search to Copilot and AI app activity across first-party, connected, and non-Microsoft record types.
- Investigating message-level access with Audit (Premium) events like `MailItemsAccessed`.
- Analyzing and reporting on audit results by parsing exports and joining across record types.

## Where audit fits in your compliance stack

Audit is one tool in the Microsoft Purview investigation and compliance stack. It's built for searching records of past activity. It isn't the tool for real-time monitoring, alerting, applying holds, preventing actions, or scoring behavior. Those jobs belong to other tools you pair audit with:

- **eDiscovery** preserves content, applies legal holds, and lets you review the actual body of messages, files, or Copilot prompts. Audit only surfaces that an interaction happened.
- **Data Loss Prevention (DLP)** and the **Microsoft Purview Browser Extension** extend visibility into non-Microsoft AI apps and websites. The `AIAppInteraction` records that show up in audit search rely on that visibility being deployed first.
- **Data Security Posture Management (DSPM)** registers connected AI apps in your tenant. Without that registration, the `ConnectedAIAppInteraction` records you filter on in audit search stay sparse or empty.
- **Insider Risk Management (IRM)** turns behavioral signals into risk scores. Some signals come from the same events audit records, but audit doesn't do the scoring.
- **Microsoft Defender** and **Microsoft Sentinel** cover real-time detection, alerting, and response. Audit is where an investigator goes after an alert fires to reconstruct what happened.

## When you get back to your tenant

Use this quick reference to map common investigation questions to the audit filters that answer them:

|To investigate|Filter on|
|---|---|
|Who deleted specific email messages|Record type `ExchangeItem`, operations `HardDelete`, `SoftDelete`, `MoveToDeletedItems`|
|Which files a user shared externally|Record type `SharePointSharingOperation`, operations like `SharingSet`, `AnonymousLinkCreated`|
|Which files a user accessed or downloaded|Record type `SharePointFileOperation`, operations `FileAccessed`, `FileDownloaded`|
|Which specific messages a user opened, when your tenant has Audit (Premium)|Operation `MailItemsAccessed` scoped to the user's mailbox|
|Whether a user used first-party Copilot|Record type `CopilotInteraction`|
|Whether a user used a Copilot Studio agent or Entra-registered AI app|Record type `ConnectedAIAppInteraction`. Requires DSPM onboarding.|
|Whether a user used a non-Microsoft AI website|Record type `AIAppInteraction`. Requires Purview Browser Extension plus DLP.|
|Admin permission or configuration changes|Record type `AzureActiveDirectory` and service-specific admin record types|

Before your first real search, confirm three things:

1. Auditing is on for your tenant. Run `Get-AdminAuditLogConfig | Format-List UnifiedAuditLogIngestionEnabled` in Exchange Online PowerShell.
2. You have the **Audit Reader** or **Audit Manager** role in the Microsoft Purview portal.
3. For any Audit (Premium) event, **Microsoft 365 Advanced Auditing** is enabled on the user whose activity you're investigating, and was enabled during the time window you care about.

## Resources

- [Learn about auditing solutions in Microsoft Purview](https://learn.microsoft.com/en-us/purview/audit-solutions-overview)
- [Get started with auditing solutions](https://learn.microsoft.com/en-us/purview/audit-get-started)
- [Search the audit log](https://learn.microsoft.com/en-us/purview/audit-search)
- [Manage audit log retention policies](https://learn.microsoft.com/en-us/purview/audit-log-retention-policies)
- [Export, configure, and view audit log records](https://learn.microsoft.com/en-us/purview/audit-log-export-records)
- [Turn auditing on or off](https://learn.microsoft.com/en-us/purview/audit-log-enable-disable)

## Use cases and scenarios

Explore how Microsoft Purview Audit can help investigate specific scenarios:

- [Search the audit log to investigate common support issues](https://learn.microsoft.com/en-us/purview/audit-troubleshooting-scenarios)
- [Search the audit log for events in Microsoft Teams](https://learn.microsoft.com/en-us/purview/audit-teams-audit-log-events)
- [Use sharing auditing in the audit log](https://learn.microsoft.com/en-us/purview/audit-log-sharing)
- [Use Microsoft Purview Audit (Premium) to investigate compromised accounts](https://learn.microsoft.com/en-us/purview/audit-log-investigate-accounts)
- [Use a PowerShell script to search the audit log](https://learn.microsoft.com/en-us/purview/audit-log-search-script)


![[Pasted image 20260916143733.png]]

![[Pasted image 20260916143948.png]]

# Search for content with Microsoft Purview eDiscovery


Use Microsoft Purview eDiscovery to search for content across Microsoft 365. This module covers how to configure cases, define search criteria, and locate messages, files, and other organizational data.

## Learning objectives

In this module you learn how to:

- Assign the roles and permissions to access Microsoft Purview eDiscovery
- Create and manage cases used to run eDiscovery searches
- Define search scope and build queries using conditions, keywords, and Copilot-generated prompts
- Run searches and validate results using statistics or random samples

# Introduction
Information security administrators often need to investigate incidents involving sensitive or improperly shared content. Whether responding to a data leak, regulatory inquiry, or internal policy violation, the ability to locate and analyze content quickly is essential.

In this module, you take on the role of an information security administrator using Microsoft Purview eDiscovery to search for content across Microsoft 365 services. You'll work within an eDiscovery case to define data sources, build targeted queries, and validate search results before taking further action.

In this module, you:

- Assign roles and permissions needed to access eDiscovery
- Create a case and configure search criteria
- Search across Microsoft 365 workloads using keywords, conditions, and Copilot-assisted query generation
- Review and validate search results using samples or statistics

By the end of this module, you'll be able to locate content across Microsoft 365, evaluate the results, and prepare for next steps like exporting or adding data to a review set.

# Understand eDiscovery and content search capabilities
Searching for ==[[content]]== is one of the most common tasks information security administrators perform in [[Microsoft Purview.]] Whether you're investigating a data leak, responding to a legal inquiry, or reviewing user activity, having the ability to locate and export relevant data quickly is essential. ==eDiscovery== provides a structured, secure way to== search across Microsoft 365 services== and support security and compliance efforts.

### What is eDiscovery?

eDiscovery is a feature in the Microsoft Purview portal that enables authorized users to create cases, search for content, place holds to preserve data, and export results. It's designed to support internal investigations, legal obligations, regulatory audits, and incident response.

Although the interface is labeled simply as "eDiscovery," the features available depend on the organization’s licensing. When advanced tools like review sets or custodian management aren't enabled, the functionality available is typically part of the default feature set included with enterprise plans.

## Licensing and access

To use eDiscovery, users must be assigned the appropriate role in Microsoft Purview, such as **eDiscovery Manager** or **eDiscovery Administrator**. These roles allow access to the **eDiscovery > Cases** area, where cases are created and managed.

Key licensing notes:

- Core eDiscovery features are included in Microsoft 365 E3 and E5 plans.
- Advanced features might require separate licensing.

Before beginning any investigation or search, it's important to confirm both the necessary permissions and the correct license are in place.

## Common scenarios for using eDiscovery

eDiscovery is typically used when content must be located across Microsoft 365 workloads for review, export, or preservation. Common scenarios include:

- **Internal investigations**: Searching messages, documents, and files related to a human resources or security incident.
- **Regulatory or legal requests**: Locating content required to comply with litigation, investigations, or regulatory reviews.
- **Data subject requests**: Identifying and collecting personal data as part of a subject rights request.
- **Incident response**: Reviewing user activity or communications after a potential breach or misuse of data.

Understanding when and why to use eDiscovery builds the foundation for conducting effective searches and supporting your organization's compliance and security goals.


# Prerequisites for using eDiscovery in Microsoft Purview
Before using eDiscovery to search for content, certain roles and access must be assigned to ensure users can view cases, create searches, and export results. These prerequisites help maintain a secure and auditable investigation process.

## Required roles

**Global** and **Compliance Administrators** can't access eDiscovery cases or search user content unless they're explicitly assigned to the **eDiscovery Manager** or **eDiscovery Administrator** role group. This permission model ensures that access to sensitive data is intentional and auditable.

To access eDiscovery, users need to be assigned one of the following roles:

- **eDiscovery Manager**: Allows users to create and manage eDiscovery cases, run content searches, and export results.
- **eDiscovery Administrator**: Includes all eDiscovery Manager permissions, plus the ability to manage role assignments and settings across all cases.

These roles can be assigned in the Microsoft Purview portal under **Permissions > Roles**.

## Assign users to eDiscovery roles

Administrators can assign users to eDiscovery roles by doing the following:

1. In the [Microsoft Purview portal](https://purview.microsoft.com/), select **Settings** > **Roles and Scopes** > **Role groups**.
2. Search for and select the appropriate eDiscovery role group.
3. Add users or groups to the role group.

Once assigned, users might need to sign out and sign back in to see the eDiscovery interface.

## Confirm access to eDiscovery

To verify that the role assignment was successful:

1. Open the Microsoft Purview portal.
2. In the left-hand navigation, select **eDiscovery**.
3. The **Cases** page should load. If not, confirm the user has been assigned the appropriate role and that the Microsoft 365 license includes eDiscovery access.

With the right roles and access in place, users can begin creating cases and searching for content across Microsoft 365 workloads.


# Create an eDiscovery search
To search for content in Microsoft Purview eDiscovery, you must first create a case. A case provides the workspace where searches, holds, and exports are managed. Creating a search also creates a case, which ensures that access to investigation data is controlled and auditable. This ensures that access to investigation data is controlled and auditable.

To create and run an eDiscovery search, the user account must be assigned the **eDiscovery Manager** or **eDiscovery Administrator** role in Microsoft Purview. These roles determine who can create cases and execute searches.

## Why cases are required

Every search must be associated with a case. The case model provides:

- Controlled access to investigation data
- An auditable trail of search and export actions
- A consistent structure for managing investigation tasks

The person who creates the case is automatically added as a member. Other users must be added manually. Even with the correct eDiscovery roles, users can’t access a case unless they’re listed as a member.

## Create a search

You can either create a case and search in a single step or create a search through a case.

### Create a search directly

1. In the [Microsoft Purview portal](https://purview.microsoft.com/), go to **Solutions** > **eDiscovery** > **Cases**.
    
2. Select the arrow next to **+ Create case**, then select **Create search**.
    
    [![Screenshot showing split button and where to create a search in eDiscovery.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/create-search-split-button.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/create-search-split-button.png#lightbox)
    
3. Enter a **case name** and a **search name**.
    
4. Optionally, provide descriptions for the case and search.
    
5. Select **Create** to create the case and search.
    
    [![Screenshot showing the fields to create an eDiscovery search.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/create-search-fields.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/create-search-fields.png#lightbox)
    

This creates a case and a search at the same time, so you can move directly into configuring your search criteria without setting up the case separately.

### Create a search through a case

If you prefer to create the case first and then add a search from within it:

1. Go to **Solutions** > **eDiscovery** > **Cases**.
    
2. Select **+ Create case**.
    
3. Enter a **name** and optional **description**.
    
4. Select **Create** to create a case.
    
    [![Screenshot showing the fields to create an eDiscovery case.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/create-case-fields.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/create-case-fields.png#lightbox)
    
5. On the **Searches** tab of your case, select **Create search**.
    
6. Enter a **name** and optional **description**.
    
7. Select **Create** to create the search.
    

Once the search is created, you can begin configuring the search criteria to locate the content relevant to your investigation.


# Conduct an eDiscovery search
As an information security administrator, one of your responsibilities might be to investigate activity that could indicate a data leak or misuse of sensitive information. eDiscovery searches in Microsoft Purview help you locate potentially relevant content across Microsoft 365 services, such as email, files, and Teams messages.

For example, you might need to identify messages and documents shared externally by members of the Sales department during a specific time period. To do that, you'll create a search in an eDiscovery case, define the locations to search, and configure your query to find the relevant content.

## Supported Microsoft 365 workloads

When you conduct a search, the results might include content from the following workloads, depending on the locations you choose:

- **Exchange Online**: Email messages and calendar items
- **SharePoint Online and OneDrive for Business**: Files and document metadata
- **Microsoft Teams**:
    - **Chat messages** (1:1 and group chats)
    - **Channel messages**
    - **Files shared in chat and channels**
- **Microsoft 365 Groups and Viva Engage**: Group conversations and shared documents

## Conduct an eDiscovery search

eDiscovery searches in Microsoft Purview are typically conducted in phases. Each phase helps narrow the focus of the investigation and ensures that the results are accurate and relevant.

The phases include:

1. Define the scope of your search
2. Identify data sources
3. Build the query
4. Run and review the results

You might return to earlier phases to adjust sources or refine your query based on the results. Once you're confident in the results, you can move on to the next steps in the investigation, such as exporting data or adding it to a review set.

### Phase 1: Define search criteria

When configuring a search, you'll specify:

- A **search name** and optional description
- One or more **data sources**, such as users, groups, or sites
- A **query** using conditions, keywords, or Keyword Query Language (KQL)

You can use the **Conditions** tab to apply filters like date range or sender, and the Keywords tab to build your query using text or KQL.

### Phase 2: Identify data sources

Before you can run a search, you need to specify the sources where content should be collected. In Microsoft Purview eDiscovery, this includes users, groups, SharePoint sites, OneDrive accounts, and Teams.

To add sources:

1. In the **Data sources** section, select **Add sources** or choose **Add tenant-wide sources** if you want to search across the entire organization.
    
2. In the **Search for sources** pane, you can filter by:
    
    - All people and groups (default)
    - People only
    - Groups only
3. Enter the name, email address, or URL of the source. For SharePoint and OneDrive, enter a full site or account URL.
    
4. Optionally, select **Exclude inactive users** to limit the results.
    
5. Choose your sources, then select **Save and close**.
    
    [![Screenshot showing where to select data sources in eDiscovery.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/select-data-sources.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/select-data-sources.png#lightbox)
    

You can select individual sources or include all active users and groups in the tenant. For most investigations, narrowing the scope of your data sources helps return more relevant results and improves performance.

### Phase 3: Build the query

The **Condition builder** lets you define filters to narrow the results returned by your search. You can use simple matching logic or combine conditions to focus on specific types of content.

To add conditions:

1. In the **Query** tab, under **Condition builder**, select **Add conditions**.
2. Choose from the available options:
    - **KeyQL**: Write advanced queries using Keyword Query Language.
    - **Date**: Filter content based on sent, received, or modified dates.
    - **Subject/Title**: Match specific terms in email subjects or document titles.
    - **Participants**: Filter by sender, recipient, or other participants.
    - **Type**: Filter by message kind, such as Email, Chat, or Teams.

Each condition supports different operators, such as **equals**, **contains**, or **starts with**. Conditions are combined using **AND**, meaning content must meet all specified criteria to be included.

[![Screenshot showing an example query in the condition builder in eDiscovery.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/condition-builder.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/condition-builder.png#lightbox)

You can add multiple conditions and adjust or remove them as needed. When using both the condition builder and a keyword query, the system will apply both sets of criteria to your results.

#### Use Copilot to generate queries (preview)

If available, Microsoft Security Copilot can help build a query from a natural language prompt. For example:

_Find Teams messages sent by Alex Wilber between March 1 and March 15 that contain attachments related to budget planning._

[![Screenshot showing Copilot generating KeyQL code with Copilot.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/generate-keyql-copilot.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/generate-keyql-copilot.png#lightbox)

Copilot generates a suggested KeyQL query that you can review and edit.

#### Search by file (preview)

If you're working with evidence like chat logs, documents, or audit exports, you can use the Search by file option to find related content. This preview feature lets you upload sample data and use it as the basis for your search instead of writing manual queries.

To use Search by file:

1. Select the **Search by file (preview)** tab.
2. Choose **Attach files**, then select one of the following:
    - **Find similar content (.txt file)**: Upload a plain text file containing sample content to match against.
    - **Find reference content (.csv file)**: Upload a CSV file, such as one generated from audit logs, to identify messages or files tied to specific users and actions.
3. After uploading, your file appears in the table with its details.

Each file must be 10 MB or smaller and in `.txt` or `.csv` format. When using this method, KQL and condition builder options are disabled. Instead, Microsoft Purview analyzes the uploaded content to find matches.

This feature is especially useful when you're investigating suspicious behavior and already have sample evidence to work from.

### Phase 4: Run and review the results

After you've configured your search criteria, you're ready to run the query and review the results.

1. Select **Run query**.
    
2. Choose your preferred result type:
    
    - **Statistics**: View summary data about the search, including the number of items found, size of the results, and breakdown by location.
    - **Sample**: View a random sample of the search results to validate your query before proceeding.

Results appear in the **Query** and **Statistics** tabs. If the results don't match what you expected, you can update your conditions or data sources and run the query again.

After confirming that the results are accurate, you can export the content or add it to a review set, depending on what your investigation requires.


# Export eDiscovery search results

After you've confirmed that your search results contain the content you need, you can export those results directly from Microsoft Purview eDiscovery. Exporting creates a downloadable package of items and metadata that can be used for legal review, investigation documentation, or external handoff.

Exporting is often the final step in the eDiscovery search process. If your organization performs deeper analysis before exporting, you might add results to a review set first. But if you're ready to hand off data or archive results, exporting is the most direct approach.

## Choose what to export

When you're ready to export:

1. Go to the **Searches** tab in your case.
2. Select a completed search.
3. Select **Export**.

In the export pane, you'll provide a name for your export and decide what types of items to include. You can export:

- **Only indexed items** that matched your search query
    
- **Indexed items and partially indexed items** (useful if you're concerned about items that couldn't be fully processed)
    
- **Only partially indexed items** (useful in special cases, such as if you're following up on indexing issues)
    
    [![Screenshot showing the index options for an eDiscovery export.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/ediscovery-export.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/ediscovery-export.png#lightbox)
    

These choices control how comprehensive your export will be. For most investigations, the first or second option is appropriate.

## Configure export settings

Depending on the types of content in your search results, you can configure additional export options.

### OneDrive and SharePoint

If your search includes sites or document libraries, you can customize how much document history or folder context to include. You can choose:

- How many document versions to include (latest, recent 10 or 100, or all versions)
    
- Whether to include subfolder items that didn't match the query
    
- Whether to include attachments from SharePoint lists
    
    [![Screenshot showing the OneDrive and SharePoint export options for eDiscovery.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/ediscovery-export-onedrive-sharepoint.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/ediscovery-export-onedrive-sharepoint.png#lightbox)
    

These options are helpful if you're dealing with collaborative content or list-based business processes.

### Mailboxes and Teams

These options help preserve conversational context, especially for Teams chats or messages with cloud attachments. For Exchange and Teams content, you can:

- **Thread conversations** into HTML transcripts (especially useful for chat review)
    
- **Include contextual Teams and Viva Engage messages** (up to 12 hours of related conversation)
    
- **Include cloud attachments** from SharePoint or OneDrive, and choose the version range to include
    
    [![Screenshot showing the message and mailbox export options for eDiscovery.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/ediscovery-export-mailbox-teams.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/ediscovery-export-mailbox-teams.png#lightbox)
    

These settings help ensure that the content you export preserves its original context and includes linked documents when applicable.

## Select format and structure

Next, choose how your exported items are packaged:

- Export mailbox content as **PST** files or **MSG files**  (PST File (Personal Storage Table)MSG File (Outlook Message))
    
- Organize data by **source location**
    
- Include or condense the **original folder path**
    
- Generate **friendly names** for items to make them easier to reference
    
    [![Screenshot showing the type and format export options for eDiscovery.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/ediscovery-export-type-format.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/ediscovery-export-type-format.png#lightbox)
    

These options help shape the output to meet your internal or legal team's requirements.

## Start the export and track progress

Once you've configured your export, select Export to begin. A confirmation message appears, and the process starts in the background.

You can monitor the export from the **Process manager**, where you'll see:

- Export status and completion time
- Number of items and locations
- Export options used

This helps you keep track of multiple exports and ensures you know when everything is ready for download.

## Download the export package

After the export finishes, go to the **Exports** tab in your case to view the results. Completed exports appear in the table with their name, status, search name, and creation details.

To download the export package:

1. Select the export to open its **Overview**.
2. In the **Export packages** section, review the list of downloadable files, including message content, reports, and item metadata.
3. Select the checkboxes next to the files you want to download.
4. Select Download.

[![Screenshot showing the download packages view in eDiscovery.](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/download-export.png)](https://learn.microsoft.com/en-us/training/wwl-sci/purview-ediscovery-search/media/download-export.png#lightbox)

The download includes all exported content along with reports that summarize what was included.

![[Pasted image 20260917101959.png]]

![[Pasted image 20260917102016.png]]