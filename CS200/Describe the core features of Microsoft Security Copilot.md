Microsoft Security Copilot has a rich set of features. Learn about available plugins, promptbooks, the ways you can export and share information from Copilot, and much more.
Microsoft Security Copilot is a platform that provides guidance specific to your organization's security.
Imagine you work for a large financial institution. One day, your organization experiences a significant security breach. The breach exposed sensitive customer data and caused a disruption in your services. As a security professional, you need to quickly assess the situation, identify the root cause of the breach, contain the threat, and take appropriate remediation actions. However, with the vast amount of security data and the complexity of your organization's infrastructure, it can be challenging to navigate through the information and make informed decisions. This is where Copilot comes in. It's a powerful tool that integrates with various sources to provide you with the guidance and insights you need to effectively respond to security incidents and protect your organization's assets.

In this module, you learn how to use Microsoft Security Copilot to enhance your organization's security.

# Describe the features available in the standalone experience of Microsoft Security Copilot
Microsoft Security Copilot can be accessed through the dedicated site, referred to as the standalone experience. It is through the standalone experience that users access the landing page or portal to the platform. To ensure that the users can access the features of Copilot, they need to have the appropriate role permissions. For more information on role-based access control for Copilot, see the Assign roles section of [Understand authentication in Microsoft Security Copilot](https://learn.microsoft.com/en-us/security-copilot/authentication?assign-roles).

There are some key landmarks on the Copilot landing page (portal) to which the user can navigate.

- Navigation panel
- Workspaces
- Prompts to try
- Prompt bar

[![Screen capture of the landing page for the standalone experience of Microsoft Security Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/copilot-landing-page-new-anchors-highlighted-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/copilot-landing-page-new-anchors-highlighted-v2.png#lightbox)

### Navigation panel

From the navigation panel, the user can navigate as follows:

- Agents, which are AI-powered assistants built into Microsoft Security Copilot available for you to choose from. Depending on your role, you can either set them up or access the agent to run it. This page lists Microsoft and non-Microsoft agents that offer significant benefits for security teams and IT operations by automating routine tasks and freeing up valuable time for teams to concentrate on strategic initiatives and complex problem-solving.
    
    [![Screen capture showing the active agents window.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/agent-list-v3.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/agent-list-v3.png#lightbox)
    
- Promptbooks, which includes builtin and custom promptbooks. Information about each promptbook is provided, including the description, the number of prompts, the owner, and more. Selecting the Get started button opens the promptbook so you can start using it. You can also select the ellipses for more options.
    
    [![Screen capture listing the promptbook library.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/promptbooks-new-home-screen.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/promptbooks-new-home-screen.png#lightbox)
    
- Build (preview) takes users to the page where You can extend Security Copilot by building custom agents tailored to your organization's specific security and operational needs. Security Copilot empowers developers to build, test, and publish agents to Security Copilot. Additional information on Microsoft Security Copilot agents is covered in the training module [Describe Microsoft Security Copilot agents](https://learn.microsoft.com/en-us/training/modules/security-copilot-describe-agents/).
    
    [![Screen capture of the build your own agents window that includes the options to build an agent from scratch or upload a YAML manifest.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/build-agents-home-screen.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/build-agents-home-screen.png#lightbox)
    
- History enables users to access their past sessions. Users can view individual, past sessions or a list of all their past sessions, as shown in the image below. Currently sessions are kept until they're manually deleted. When a session is deleted, all data associated with that session is marked as deleted and the time to live (TTL) is set to 30 days. After that TTL expires, queries can't access that data. Logs, which contain session data aren't affected when a session is deleted via the in-product UX. These logs have a retention period of up to 90 days.
    
    [![Screen capture listing a user's past sessions.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/history-all-history.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/history-all-history.png#lightbox)
    
- Owner specific options, for users configured as owners:
    
    - Owner settings. These settings include the option to switch Security Compute Units (SCUs) capacity, select the workspace for Copilot agents, configure data sharing options to help improve Copilot, allow logging audit data in Microsoft Purview, and configure who can upload files.
        
        - [Switch capacity](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_1_switch-capacity)
        - [Agent workspaces](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_1_agent-worksapces)
        - [Improve Copilot](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_1_improve-copilot)
        - [Audit logging](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_1_audit-logging)
        - [File upload](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_1_file-upload)
        
        [![Screen capture showing the owner settings, specifically focused on capacity information.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/owner-settings-capacity.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/owner-settings-capacity.png#lightbox)
        

---

- Plugin settings. Owners configure the following:
    
    - Select who can add and manage their own custom plugins. The available options are Contributors and owners or owners only.
    - Select who can add and manage custom plugins for everyone in the organization. The available options are Contributors and owners or owners only.
    - Decide which new and existing plugins are available to everyone in your organization, and which are restricted to owners only.
    - Allow Security Copilot to access data from your Microsoft 365 services. If you choose not to allow Copilot access, users won't be able to use specific plugins, like Microsoft Purview, or connect any future sources of org knowledge that are housed in Microsoft 365 services.
    
    - [Plugin settings](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_2_plugin-settings)
    - [Restrict plugin access](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_2_restrict-plugin-access)
    
    [![Screen capture showing the plugin settings page.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/plugin-settings-no-restrictions.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/plugin-settings-no-restrictions.png#lightbox)
    
- Role assignments, where admins can view and manage existing role assignments for the Copilot Owner and Copilot Contributor roles. This includes the option to add the recommended roles group.
    
    - [Role assignment](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_3_role-assignment)
    - [Recommended roles](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_3_recommended-roles)
    
    [![Screen capture showing the role assignment page.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/role-assignments-new-edited.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/role-assignments-new-edited.png#lightbox)
    
- Manage workspaces, where owners can create new workspaces, configure them by assigning access and permissions, and fine-tune settings such as owner roles and plugin configurations. Workspaces are described in more detail in the subsequent unit.
    
    [![A screenshot of the manage workspaces page that lists the available workspaces.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-manage-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-manage-v2.png#lightbox)
    
- Usage monitoring, which provides a dashboard showing how SCUs are consumed over a period of time by your Microsoft Security Copilot workloads. The usage monitoring dashboard provides visibility, for a selected workspace, into the number of units used, the specific plugins employed during sessions, and the initiators of those sessions. The dashboard also allows you to apply filters and export usage data seamlessly. The dashboard includes up to 90 days of data. Security Copilot supports both provisioned SCUs for predictable workloads and overage SCUs that provide flexible, on-demand capacity billed only when used. Overage SCUs ensure additional capacity is available when initially provisioned units are depleted during unexpected workload spikes. When an analyst is in the middle of an investigation and the usage is nearing the provisioned capacity limit (90%), a notification is displayed to the analyst while entering the prompt. The notification informs the analyst to contact the owner to increase the capacity or limit the number of prompts to avoid disruptions. These notifications are also shown in the Security Copilot embedded experiences.
    
    When the provisioned capacity is crossed, the analyst sees an error message stating that due to high usage in the organization, they can't submit additional prompts. The analyst is asked to contact the owner to increase the provisioned SCUs.
    
    - [Usage monitoring](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_4_usage-monitoring)
    - [Usage monitoring filters](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_4_usage-monitoring-filters)
    
    [![Screen capture showing the usage monitoring dashboard.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/usage-monitoring-dashboard-new.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/usage-monitoring-dashboard-new.png#lightbox)
    
- Security Store, which is integrated into the standalone experience of Microsoft Security Copilot, is Microsoft Security’s new security-optimized storefront enabling organizations to find, try, buy, and deploy Microsoft and partner-built security solutions and agents. These solutions and agents integrate directly with Microsoft Security products such as Microsoft Defender, Microsoft Sentinel, Microsoft Entra, Purview, Intune and Security Copilot, offering a unified experience that simplifies procurement and accelerates time to value.
    
    [![Screen capture showing the Security store landing page.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/security-store.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/security-store.png#lightbox)
    

Selecting the ellipses on the bottom left corner of the navigation panel, allows users to view settings, access help options, and select a tenant for use with Copilot Studio.

[![Screen capture showing the options available when a user selects the ellipses on the Copilot navigation panel.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/ellipses-navigation-panel.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/ellipses-navigation-panel.png#lightbox)

- Settings, which include configurable preferences, data and privacy statements, and information about the App version.
    
    - The preferences settings allow users to configure the theme, language, and time zone. Copilot supports many languages. For detailed information, see [Supported languages](https://learn.microsoft.com/en-us/security-copilot/supported-languages#supported-languages).
        
    - The data and privacy page provides links to the privacy statement, terms and conditions, and location information for where data is stored.
        
    - The About page provides information of the app version for Copilot.
        
        - [Preferences](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_5_preferences)
        - [Data and privacy](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_5_data-privacy)
        
        [![Screen capture showing the preferences that can be configured by any user.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/preferences-with-workspaces.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/preferences-with-workspaces.png#lightbox)
        
    
    ---
    
- Help enables users to link to documentation and training. If you encounter issues or need to seek assistance, Security Copilot provides an advanced support experience. Depending on your role, the widget allows you to:
    
    - **Find solutions to common problems**. Anyone with access to Security Copilot can access the self help widget by selecting the help icon then selecting the Help tab. Type your question in the prompt bar and articles related to your search will be surfaced.
        
    - **Submit a support case to the Microsoft support team**. To open support cases, you must have, at a minimum, a Service Support Administrator OR Helpdesk Administrator role. You can also view your support history.
        
    
    - [Find solutions](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_6_find-solutions)
    - [Get support](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_6_get-support)
    
    [![Screen capture showing the self-help prompt bar and articles related to the entered prompt.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/help-icon-self-help.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/help-icon-self-help.png#lightbox)
    
- Tenant switcher. The tenant, which is provisioned for Copilot doesn't need to be the tenant your security analyst logs in from. Also a user may have access to Security Copilot across multiple tenants. In the screenshot that follows, the user is provisioned only in the "Zava - Private" tenant. If the user had been provisioned in other tenants, they would be listed and the user would be able to select any of the available tenants.
    
    [![Screen capture showing the tenant switching window, with multiple tenants listed.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/tenant-switcher-v4.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/tenant-switcher-v4.png#lightbox)
    

### Workspaces

Copilot workspaces are separate work environments within the tenant in which your Copilot instance is operating. One way to think about Copilot workspaces is as separate rooms in a house. Each room is configured to be optimized for its function and the people that use that room. The same is true of Copilot workspaces. Admins set up, configure, and manage individual workspaces for specific team needs.

Selecting workspaces opens the drop-down menu where users can select available workspaces to which they have access and set their preferred workspace in cases where they have access to multiple workspaces. Owners will also have the option to manage workspaces, manage capacity usage, and create a new workspace.

More detailed information is provided in a subsequent unit, dedicated to Copilot workspaces.

[![A screenshot showing workspace drop-down menu that can be selected from the main landing page.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-anchor-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-anchor-v2.png#lightbox)

### Prompts to try

Prompts are the primary input Security Copilot needs to generate answers that can help you in your security-related tasks. Promptbooks are a series of prompts that have been put together to accomplish specific security-related tasks.

To help introduce the concept of prompting in Security Copilot, a set of prompts and promptbooks are immediately available on the home screen.

You can apply filters to find prompts or promptbooks that are most relevant to you. Narrow down search results by applying multiple filters to better suit your role or scenario.

Customize your search by selecting filters based on:

- Roles - Examples include: CISO, SOC analyst, threat intel analyst, and IT administrator.
- Plugins - Examples include: Microsoft Defender XDR, Microsoft Threat Intelligence, and Natural language to KQL for advanced hunting.

You can also use the search function to look up prompts or promptbooks by title.

- [Prompts](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_7_prompts)
- [Promptbooks](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_7_promptbooks)
- [Filter by role](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_7_filter-by-role)
- [Filter by plugin](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2-describe-standalone-experience?tabs=switch-capacity%2Cplugin-settings%2Crole-assignment%2Cusage-monitoring%2Cpreferences%2Cfind-solutions%2Cprompts#tabpanel_7_filter-by-plugin)

[![Screen capture showing the Copilot landing page with prompts to try.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/copilot-landing-page-prompts-to-try.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/copilot-landing-page-prompts-to-try.png#lightbox)

### Prompt bar

You use the prompt bar to tell Copilot what insights you want from your security data, in natural language, then select the run icon.

[![Screen capture showing the prompt bar.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/prompt-bar-new.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/prompt-bar-new.png#lightbox)

In addition to the run icon, the prompt bar include two other icons:

- Prompt icon
- Sources icon

#### Prompt icon

Select the prompt icon located inside the prompt bar, to open a window where you search for and access promptbooks and system capabilities.

[![Screen capture showing the prompt icon and the window it opens that shows promptbooks and system capabilities, when selected.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/prompt-icon-mapping.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/prompt-icon-mapping.png#lightbox)

System capabilities, often referred to as prompt suggestions, are specific, single prompts that you can use in Copilot. The list displayed when you select the prompt icon is a small subset of all the available system capabilities available to you. To view all the system capabilities available to you, select See all system capabilities. The list displayed may vary, depending on the plugins you enabled. There are some capabilities that aren't tied to a specific plugin and as such are available, independent of the enabled plugins, to users with access to Copilot.

Selecting a system capability (prompt suggestion) typically requires more input to get a useful response, but Copilot provides that guidance. As an example, the image that follows shows the information that the user must include to analyze a script or command.

[![Screen capture showing the required input for the Analyze a script or command prompt suggestion.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/system-capability-example.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/system-capability-example.png#lightbox)

#### Sources icon

Copilot integrates with security-specific sources using plugins and files.

- Plugins - Copilot currently supports plugins for Microsoft's own security products, non-Microsoft products, open-source intelligence feeds, industry information from the public web, and custom plugins.
    
- Files - Connections to an organization's knowledge bases gives Copilot more context, resulting in responses that are more relevant, specific, and customized to the user. Uploading a file is one approach that Copilot uses to connect to an organization's knowledge base.
    

You access and manage sources through the sources icon that is included in the prompt bar. The Manage sources window lists the plugins tab (the default view) and the files tab.

[![Screen capture showing the sources icon that when selected allows the user to select plugins or files. The default view opens to the plugins page.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/manage-sources-icon-mapping-v3.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/manage-sources-icon-mapping-v3.png#lightbox)

Refer to subsequent units in this module for detailed information on plugins and connection to knowledge bases.

# Describe the features available in a session of the standalone experience
A session is a particular conversation within Copilot and consists of one or more prompts. A session may be initiated through prompts you enter directly in the prompt bar, by running a promptbook, or a prompt suggestion.

Copilot has features that are common across all sessions and the individual prompts that make up a session, including:

- The process log
- Actions you can take a prompt and its response
- Prompt feedback
- The pin board

### Process log

For every prompt Copilot runs, Copilot generates a process log that's visible to the user. The user can see what capability is used to generate the response. This is important because it enables the user to determine whether the response was generated from a trusted source. In the screenshot that follows, the process log shows that Copilot chose the Incident Analysis capability. The process log also shows that the final output went through safety checks, which is part of Microsoft’s commitment to responsible AI.

[![Screen capture showing process log, which shows the selected skill and that a safety check was run on the composed message.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/process-log-new.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/process-log-new.png#lightbox)

### Action you can take on prompt and its response

There's a consistent set of actions available for every prompt/response pair in the Copilot standalone experience. Actions include:

- Pin an individual prompt and its corresponding response to the pin board by selecting the pin icon.
- Edit a prompt.
- Rerun a prompt.
- Delete a prompt.
- Export a prompt.
- Copy a response.
- Provide feedback on a response

[![Screen capture showing highlighting the actions available on a prompt/response pair.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/prompt-response-actions.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/prompt-response-actions.png#lightbox)

### Feedback

Whether you use promptbooks, prompt suggestions, or your own prompt, providing feedback about your satisfaction with the generated response can help Microsoft in improving Copilot. You can find the feedback buttons on the left-hand side at the bottom of every response.

You can select:

- Looks right
- Needs improvement
- Inappropriate

[![Screen capture showing the options to provide feedback for each prompt.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/feedback-new.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/feedback-needs-improvement.png#lightbox)

For each option, the user is prompted for additional information. The image that follows shows the options for a response that needs improvement.

[![Screen capture showing the information a user can provide for a response that needs improvement.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/feedback-needs-improvement-new.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/feedback-needs-improvement-new.png#lightbox)

The option to provide feedback is also available for Copilot features that are available in the embedded experience. Refer to [Describe the embedded experiences of Microsoft Security Copilot](https://learn.microsoft.com/en-us/training/modules/security-copilot-embedded-experiences/).

### Pin board

The pin board enables you to keep track of important responses in a session. You can pin individual or multiple prompt-response pairs. To select one or more individual items, select the check box next to the item then select the pin icon. To select all the prompt-response pairs in the session, select the checkbox at the top of the session window then select the pin icon. Upon selecting the pin icon, the pin board window opens in a split view with the session. The pin board includes a summary tab that summarizes the session and a pinned items tab that lists the prompt and a collapsed view of the response that users can expand. You can also edit the title of the session on the pin board.

[![Screen capture showing the pin icon. When a prompt response is selected along with the pin icon opens the pin board.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/pin-mapping-to-pin-board.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/pin-mapping-to-pin-board.png#lightbox)

The contents of the pin board can be shared so that people in your organization with Copilot access can view this session. Additionally, the contents of the pin board can be exported to Microsoft Word, sent via email, or copied.

[![Screen capture showing the window that is displayed when a user selects the option to share the pinned item.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/share-pinned-item-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/share-pinned-item.png#lightbox)

[![Screen capture showing the options for exporting a pinned item.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/export-pinned-item-v3.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/export-pinned-item-v2.png#lightbox)

# Describe workspaces

[[Copilot workspaces]] are separate work environments within the tenant in which your Copilot instance is operating. Workspaces were designed to give customers the ability to create segmentation for agentic traffic and help teams manage resources, optimize workflows, and maintain compliance with organizational policies.

To help you better understand the concept of workspaces, we use the analogy of house with multiple rooms. Each room is configured to be optimized for its function and the people that use that room. When someone enters the house, they might have access to some rooms but not others.

You can think of Copilot Workspaces fitting into this analogy. A Copilot workspace is analogous to a room in a house. You can also think of the house as analogous to a tenant. In the same way that a house has multiple rooms, the tenant in which Copilot is operating can have multiple workspaces.

Through the tenant-switching capability in Security Copilot, a user can select in which tenant they'll be working. In our analogy, this is a Copilot user getting access to the house. Once the tenant is selected, a Copilot user can access and work in any workspace (room in the house) to which they have access, within the context of their role permissions in that workspace.

[![Illustration of a house, which is like a tenant and a room in the house is like a workspace in Security Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-overview.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-overview.png#lightbox)

There are many benefits to Copilot workspaces.

- Set up individual workspaces to address specific team needs.
- Manage and map costs based on team needs and budgets.
- Ensure critical workflows aren't disrupted by throttling.
- Store session data according to geo-specific regulations.
- Set up and manage specific plugins, promptbooks, and files for specific team needs.
- Experiment with custom plugins and promptbooks before organization-wide deployment.

### Create a workspace

You need to be at least a ==Security Administrator ==to create new workspaces for your organization. A workspace is powered by a capacity resource (SCUs). To attach capacity to a workspace, you also need to be an ==Azure subscription owner or contributor==.

There are several entry points for you to create a new workspace:

- From the landing page of the Security Copilot portal
- From the Manage workspaces section of the Owner settings page

- [From the breadcrumb](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2b-describe-workspaces?tabs=breadcrumb%2Ccreate-workspace%2Cmanage-workspaces%2Cworkspace#tabpanel_1_breadcrumb)
- [Owner settings page](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2b-describe-workspaces?tabs=breadcrumb%2Ccreate-workspace%2Cmanage-workspaces%2Cworkspace#tabpanel_1_owner-settings-page)

[![A screenshot showing the new workspace option from the landing page of the Copilot Studio portal.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-create.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-create.png#lightbox)

1. From any of entry points, select **New Workspace**.
2. To Set up the workspace, specify a name for the workspace, create or select an existing capacity, select the data storage location, and define your data sharing preferences. These choices are all specific to this workspace and can be different from the selections made at the time Security Copilot was initially set up (the first run experience).
3. Confirm that you acknowledge and agree to the terms and conditions, then select Create.

- [Create a workspace](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2b-describe-workspaces?tabs=breadcrumb%2Ccreate-workspace%2Cmanage-workspaces%2Cworkspace#tabpanel_2_create-workspace)
- [Create capacity](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2b-describe-workspaces?tabs=breadcrumb%2Ccreate-workspace%2Cmanage-workspaces%2Cworkspace#tabpanel_2_create-capacity)

[![A screenshot of the page to Create a new workspace.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-create-page.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-create-page.png#lightbox)

### Configure workspaces

Once the workspace is created and selected, it can be configured with unique settings and permissions, allowing you to tailor the environment to meet the specific needs of your team. This includes assigning roles, managing access, and setting up plugins and promptbooks that are relevant to the workspace.

Decisions and configuration made in plugin settings and role permissions apply specifically to the workspace in which they're being configured.

==Decisions and configurations within "owner settings" apply specifically to the workspace that's being configured==, with one exception: ==Audit Logging enablement can only be changed by Security Admins and applies to all workspaces.==

[![Screenshot of owner settings page with logging audit data highlighted.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-audit-logging.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-audit-logging.png#lightbox)

### Manage workspaces

Owners can view, navigate between, manage capacity allocations, and delete workspaces that they own from the Manage Workspaces page.

- [Manage workspaces](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2b-describe-workspaces?tabs=breadcrumb%2Ccreate-workspace%2Cmanage-workspaces%2Cworkspace#tabpanel_3_manage-workspaces)
- [Assign and switch capacity](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2b-describe-workspaces?tabs=breadcrumb%2Ccreate-workspace%2Cmanage-workspaces%2Cworkspace#tabpanel_3_capacity)

[![A screenshot of the manage workspaces page that lists the available workspaces.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-manage-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/workspace-manage-v2.png#lightbox)

### Use workspaces

From the main landing page, users can select the current workspace, which opens the drop-down menu where users can select available workspaces to which they have access. They can also set their preferred workspace in cases where they have access to multiple workspaces. Owners are also given the option to manage workspaces, manage capacity usage, and create a new workspace.

Once in a workspace, users can start using promptbooks, enter prompts directly in the prompt bar, and all the features of Copilot for which they have permissions.

 Note

If users have been doing work with Copilot in one of the Security product portals (for example Defender, Intune, Microsoft Entra, or Purview) and they switch their preferred workspace, they need to reload or sign out & sign in to the portals to continue working with Copilot in those portals. If they don’t, they'll encounter an error.

- [Workspace](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2b-describe-workspaces?tabs=breadcrumb%2Ccreate-workspace%2Cmanage-workspaces%2Cworkspace#tabpanel_4_workspace)
- [Workspace menu option](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/2b-describe-workspaces?tabs=breadcrumb%2Ccreate-workspace%2Cmanage-workspaces%2Cworkspace#tabpanel_4_workspace-menu)

[![A screenshot highlighting the current workspace, on the Copilot landing page.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/landing-page-workspace-small.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/landing-page-workspace-small.png#lightbox)

# Describe Security Copilot plugins
Microsoft Security Copilot integrates with various sources, including Microsoft's own security products, non-Microsoft vendors, open-source intelligence feeds, websites, and knowledge bases to generate guidance that's specific to your organization.

One of the mechanisms by which Copilot integrates with these various sources is through plugins. Plugins extend Copilot's capabilities. In this unit, you explore the different categories of plugins available in Security Copilot.

### Plugin categories

Plugins in Security Copilot are organized into the following categories:

- **Microsoft** – Plugins from Microsoft security products and services.
- **Other** – Plugins from non-Microsoft security services.
- **Websites** – Plugins providing access to public web information.
- **Custom** – Plugins you or your organization develop.

### Microsoft plugins

Microsoft plugins give Copilot access to information and capabilities from within your organization's Microsoft products. Security Copilot includes many preinstalled Microsoft plugins. The image that follows shows only a subset of the available Microsoft plugins and the order in which the plugins are listed may vary from what is displayed in the product.

If a Copilot owner has restricted plugin access, then those plugins that have been set to restricted show greyed out and restricted.

- [Plugins](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/3-describe-microsoft-plugins?tabs=plugins#tabpanel_1_plugins)
- [Restricted plugins](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/3-describe-microsoft-plugins?tabs=plugins#tabpanel_1_restricted-plugins)

[![Screen capture of plugins page, showing Microsoft plugins.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/microsoft-plugins.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/microsoft-plugins.png#lightbox)

For a complete list of all available Microsoft plugins, refer to the [Plugins overview in Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/plugin-overview) documentation.

 Note

Products that integrate with Security Copilot as plugins need to be purchased separately.

### Key concepts for plugins

There are several key concepts related to plugins that are important for understanding how they work within Security Copilot.

#### Authentication

Microsoft plugins in Copilot generally use the [[on-behalf-of (OBO) authentication]] model. This means Copilot knows that a customer has licenses to specific products and is automatically signed into those products. Copilot can then access those products when the plugin is enabled. Some plugins that require setup, as noted by a settings icon or setup button, may include configurable parameters that are used for authentication in lieu of the OBO model.

Non-Microsoft plugins each define their own authentication requirements, which may include API keys, OAuth credentials, or other service-specific credentials.

#### Plugin management

Owners control plugin availability across the organization. By default, all Owners and Contributors have access to preinstalled Microsoft and non-Microsoft plugins. When an owner restricts plugin access, they can set availability to:

- All users
- Owners only

Once access is restricted, new preinstalled plugins are made available to Owners only until configured otherwise. Restricting access is an immediate change that impacts all users of Security Copilot, including embedded experiences.

Some plugins, like Microsoft Sentinel and Azure AI Search, require additional setup. Any plugin with a gear icon or **Set up** button is configured per user.

#### System capabilities

Each enabled plugin exposes system capabilities—specific, single prompts that you can use in Copilot. To view the system capabilities supported by the enabled plugins, select the prompt icon in the prompt bar, and select "See all system capabilities." Selecting a system capability typically requires more input to get a useful response, but Copilot provides guidance.

[![Screen capture of the prompt icon that when selected opens the window to select system capabilities.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/prompts-to-system-capabilities.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/prompts-to-system-capabilities.png#lightbox)

### Examples of Microsoft plugins

The sections that follow provide descriptions of two Microsoft plugins to illustrate the types of capabilities that plugins provide. Microsoft Security Copilot is continually adding support for Microsoft products, and for each plugin the list of capabilities is also growing.

#### Microsoft Defender XDR

[[Microsoft Defender XDR]] is a ==unified pre- and post-breach enterprise defense suite== that natively coordinates detection, prevention, investigation, and response across endpoints, identities, email, and applications to provide integrated protection against sophisticated attacks.

There are two separate plugins in Copilot that relate to Microsoft Defender XDR:

- [[**Microsoft Defender XDR**]] – Provides capabilities to summarize incidents, take action on incidents through guided responses, create incident reports, get device summaries, analyze files and scripts, and more.
- [[**Natural language to KQL for Microsoft Defender XDR**]] – Converts any natural-language question in the context of threat hunting into a ready-to-run KQL query. This saves security teams time by generating a KQL query that can then be automatically run or further tweaked according to the analyst's needs.

The role permission that grants the user access to Copilot determines the level of access to Microsoft Defender XDR data. There ==are no additional role permissions ==required to use the Microsoft Defender XDR plugin or the Natural language to Defender XDR KQL plugin.

Microsoft Defender XDR capabilities in Copilot are built-in prompts that you can use, but you can also enter your own prompts based on the capabilities supported.

[![Screen capture of the Defender XDR capabilities that can be run in the standalone experience.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/defender-xdr-skills.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/defender-xdr-skills.png#lightbox)

Some sample prompts include:

- Summarize incident {incident number}.
- Give me the guided responses for incident {incident number}.
- What devices are involved in incident {incident number}?

Copilot also includes a built-in promptbook for Microsoft Defender XDR incident investigation that you can use to get a report about a specific incident, with related alerts, reputation scores, users, and devices.

With the plugin enabled, Copilot integration with Defender XDR can also be experienced through the embedded experience. The scenarios supported through the embedded experience are described in more detail in the module titled, "Describe the embedded experiences of Microsoft Security Copilot."

#### Microsoft Sentinel

[[Microsoft Sentinel ]]delivers ==intelligent security analytics and threat intelligence== across the enterprise. With Microsoft Sentinel, you get a single solution for attack detection, threat visibility, proactive hunting, and threat response.

There are two separate plugins in Copilot that relate to Microsoft Sentinel:

- [[**Microsoft Sentinel** ]]– Provides capabilities focused on== incidents and workspaces==. It enables analysts to get information about incidents, associated alerts, and workspace data.
- **Natural language to Microsoft Sentinel KQL** – Converts any natural-language question in the context of threat hunting into a ready-to-run KQL query, saving security teams time by generating queries that can then be automatically run or further tweaked.

[![Screen capture of the Microsoft Sentinel and NL2KQL in Microsoft Sentinel plugin.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/sentinel-skills-v3.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/sentinel-skills-v3.png#lightbox)

To use the Microsoft Sentinel plugin, the user needs a ==role permission that grants access to Copilot and a Microsoft Sentinel-specific role like Microsoft Sentinel Reader to access incidents in the workspace==. The Microsoft Sentinel plugin also requires the user to configure the Microsoft Sentinel workspace, the subscription name, and the resource group name.

[![Screen capture of the Microsoft Sentinel plugin settings page.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/sentinel-plugin-settings-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/sentinel-plugin-settings-v2.png#lightbox)

Some sample prompts include:

- Get me the top 5 high severity Microsoft Sentinel incidents.
- Show the most recent incident from Microsoft Sentinel.
- Get Microsoft Sentinel incidents that were assigned to me.

Copilot also includes a promptbook for Microsoft Sentinel incident investigation. This promptbook includes prompts for getting a report about a specific incident, along with related alerts, reputation scores, users, and devices.

### Non-Microsoft plugins

Beyond Microsoft products, Security Copilot also supports non-Microsoft plugins.

#### Other plugins

Other plugins give Copilot access to information and capabilities from non-Microsoft security services your organization uses. The list of supported plugins is continually growing and includes integrations with services like ServiceNow, Splunk, CrowdSec, and GreyNoise.

[![Screen capture of the non-Microsoft plugins.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/plugins-other.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/plugins-other.png#lightbox)

Access to these plugins requires an account and license to the specific service. Each plugin requires its own authentication setup, which may include API keys or other credentials.

#### Website plugins

Website plugins give Copilot access to industry information from the public web. These plugins use anonymous authentication and don't require additional configuration.

[![Screen capture of the website plugins.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/plugins-websites.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/plugins-websites.png#lightbox)

#### Custom plugins

The Security Copilot platform enables developers and users to create their own plugins to perform specialized tasks. There are two types of custom plugins:

- Custom Copilot plugins you develop.
- Custom plugins developed with OpenAI's API.

Every custom plugin requires a YAML or JSON formatted manifest file that describes metadata about the skill set and how to invoke the skills. Owner settings determine who can add and manage custom plugins for themselves and for others in the organization.

[![Screen capture showing the two types of custom plugins.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/custom-plugin-options-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/custom-plugin-options-v2.png#lightbox)

To learn more about custom plugins, see [Create your own custom plugins](https://learn.microsoft.com/en-us/copilot/security/custom-plugins).

Watch this short video for a summary on setting up non-Microsoft plugins and adding custom plugins.

# Describe custom promptbooks
[[Promptbooks]] in Security Copilot are ==collections of prompts put together to accomplish specific security-related tasks. They run one prompt after another, building on previous responses.==

You can create your own promptbook with the promptbook builder to automate investigation flows and optimize repetitive steps in Copilot that are customized to your needs and requirements. You can also share the promptbooks you created with other users so they can also benefit from your work.

### Create a promptbook from an existing session

To create your own promptbook, you can start with an existing session that contains the prompts you want to work with. For this example, the session titled, "Show the last three failed login attempts," is used.

[![Screen capture showing the session to use as the basis for your custom promptbook.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/select-session.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/select-session.png#lightbox)

After selecting the desired session, select the boxes beside the prompts to include them or select the top box to include all prompts in the session. Selecting any or all of the prompts light up the Create promptbook button.

[![Screen capture of the create promptbook icon.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/select-create-promptbook-v4.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/select-create-promptbook-v4.png#lightbox)

Once you select the create promptbook icon, the Create a promptbook page opens. Here you name the promptbook, add a tag and a description, add more prompts, and remove or edit existing prompts. If any of the prompts require an input parameter, you would need to specify an easily understood parameter name within ==angle brackets== and no spaces. For example, if one of the prompts requires an incident ID number, you can specify <IncidentID>. Similarly, if a prompt requires that you enter a threat actor name, you could specify the input parameter as <threatactorname> or <ThreatActor>. You can include more than one input parameter. You can also select to share the promptbook with others in your organization or have it for your own personal use.

In the screenshot that follows, the promptbook is named Failed-Login-Attempts and it includes two prompts. The first prompt was originally to show the last three failed logins. To configure the number as an input parameter, select the ellipses next to the prompt to edit it by replacing the number 3 and entering <number>.

![[Pasted image 20260825142511.png]]

A pop-up window appears once your promptbook is created. From this window, you can select to view the promptbook you just created and then run it or edit it, share your promptbook via link, or go to the promptbook library.

From then on, you can run your promptbook like you would any other promptbook. You can select the prompts icon from the prompt bar and start typing in the name of the promptbook in the search bar then selecting it from the list that appears.

![[Pasted image 20260825142624.png]]

Selecting the promptbook opens it. From here, you enter the required input parameter and then select run.

[![Screen capture promptbook, including the input parameter.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/create-promptbook-run-v3.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/create-promptbook-run-v3.png#lightbox)

Watch this short video for a summary on creating a promptbook.

### Edit a promptbook

To edit your existing promptbook, select the home menu (hamburger icon) and select Promptbook library.

[![Screen capture of the home menu options including the promptbook library option.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/select-promptbook-library-v3.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/select-promptbook-library-v3.png#lightbox)

Select the ellipses for the promptbook you want to edit then select Edit from the options. You can only edit existing promptbooks if you're the owner of the promptbook.

[![Screen capture of the edit option for your custom promptbook.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/my-promptbooks-library-edit-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/my-promptbooks-library-edit-v2.png#lightbox)

In addition to editing, you can also choose to view the details of the promptbook, duplicate it, or delete it. You can also choose to run the promptbook by selecting the Get started button.

### Continue on failure

The **Continue on failure** feature allows users to set a promptbook to continue running the next prompt even after a prompt fails, instead of halting the entire promptbook. This is useful for investigation flows where some prompts might not return results but you still want the rest of the promptbook to complete.


# Describe knowledge base connections

==Knowledge base connections, a== feature of Microsoft Security Copilot currently in preview, allow you to== integrate your organization's knowledge base as an additional source of information.== By including knowledge bases, you give Copilot ==more== ==context==, which results in responses that are more relevant, specific, and customized to your organization.

An organization's knowledge base might include proprietary information such as wikis, policy and compliance documents, investigation and response procedures, templates, historical data, KQL (Kusto Query Language) libraries, or even information from public repositories like prescriptive guidelines and frameworks.

There are two ways to integrate a knowledge base into Copilot:

- File upload
- Azure AI Search plugin

### File upload

You can upload files in Microsoft Security Copilot to allow Copilot to refer to the contents of the files when you prompt Copilot and mention your "uploaded files." Examples of files you can upload include your organization's policy and compliance documents, investigation and response procedures, and templates.

 Note

==The file upload feature in Copilot doesn't support use cases such as evaluation or detonation of malicious files.==

To upload a file:

1. Check that the file is a common text file type like DOCX, MD, PDF, or TXT format, and that each file doesn't exceed 3 MB. You can upload files up to 20 MB in total.
    
2. In the Copilot home page, select the sources icon ![Screenshot of sources icon](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/sources-icon-from-docs.png) in the prompt bar to open the **Manage sources** page.
    
3. Select **Files** to open the file upload section.
    
    [![Screen capture of the files upload page.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/manage-sources-files-new-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/manage-sources-files-new-v2.png#lightbox)
    
4. Select **Upload file** to browse for your file.
    
5. Wait for the file to appear in **Uploads**. If an error message appears, correct the problem and try again.
    
6. To include the file as a source in your current session, toggle the button beside the file to the on position (lit up). If you aren't going to use the file yet, or want to exclude it as a source in your current session, keep the toggle off (greyed out).
    

To prompt using the uploaded file, you need to mention "uploaded files" if you want Copilot to reason over your available files. You can also include the file name to guide Copilot to reason over a specific file. For example:

_Based on the Contoso Data Handling Policy file, list any actions taken by user Preston-123 that might be a violation of the data handling policies. Include a verdict to the action and level of confidence of the verdict. Cite the policy name and section applicable to the verdict_.

#### Storage and availability

Uploaded files are always stored in the home Geo of the tenant. Uploaded files are stored in the Security Copilot service, not inside your Microsoft tenant boundary. Uploaded files are only available to the user account that uploaded them and aren't available to other users within or outside the tenant.

#### Delete a file

To delete a file, select the trash icon next to the file name in **Manage sources > Files > Uploads**.

#### Restrict file upload (for owners)

Users assigned the Owner role can choose who are allowed to upload files in owner settings. The options are:

- No one can upload files
- Contributors and Owners can upload files

By default, file upload is available for all users (Contributors and Owners).

### Azure AI Search plugin

Azure AI Search is a service that allows you to search, retrieve information, and extract insights from your content at scale and securely. It's commonly used for document search, data exploration, and chat-style Copilot apps over proprietary data. There are two primary workloads in Azure AI Search:

- **Indexing** loads your content into the search service and makes it searchable.
- **Querying** allows you to search the content from your index once it's populated with searchable content.

The Microsoft Security Copilot integration for Azure AI Search is enabled via a plugin that must be configured to connect to one of your Azure AI Search indexes. The integration enables you to reference your content to generate contextualized, relevant, and specific responses.

- [Azure AI Search plugin](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/5a-describe-knowledge-base-connections?tabs=azure-ai-search-plugin#tabpanel_1_azure-ai-search-plugin)
- [Plugin set up](https://learn.microsoft.com/en-gb/training/modules/security-copilot-describe-core-features/5a-describe-knowledge-base-connections?tabs=azure-ai-search-plugin#tabpanel_1_plugin-set-up)

[![Screen capture of the Azure AI Search plugin.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/azure-ai-search-plugin-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-describe-core-features/media/azure-ai-search-plugin-v2.png#lightbox)

You can find the required information for the plugin setup in your Azure AI Search page in the Azure portal.

 Important

Currently, Copilot doesn't validate your credentials when you save your settings. If they aren't correct, you see an error later when Copilot attempts to run the Azure AI Search plugin.

#### Requirements

To use the Azure AI Search plugin in Copilot, make sure that the Azure AI Search index is configured as follows:

- The text field must be searchable.
- The title field must be filterable.
- The vector field must use **text-embedding-ada-002**.

One way to get started with setting up an index with these requirements is to use integrated vectorization. Refer to [Quickstart: Integrated vectorization (preview)](https://learn.microsoft.com/en-us/azure/search/search-get-started-portal-import-vectors).

#### Prompting with Azure AI Search

Once connected, prompt Copilot to look for information in the Azure AI Search index. Make sure to mention "Azure AI Search" in the prompt. For example:

- New staff can ask Copilot about the organization's processes within their Copilot workflows. This can speed up the onboarding process.
    
    _Sample prompt: Summarize my organization's multifactor authentication policies in Azure AI Search._
    
- While performing an incident investigation, SOC analysts can ask Copilot for investigation steps from their organization's processes and procedures.
    
    _Sample prompt: Search my Azure AI Search index for investigation steps that I should follow for this incident involving multiple failed sign-in attempts by a user._
    

The Azure AI Search plugin performs a semantic and keyword search across the index's contents to find the relevant information, so it's advisable to be as specific as you can in your prompts.

### Known limitations

For both the Azure AI Search plugin and file upload methods of connecting knowledge bases:

- Copilot reasons over text content only, not other data or media types.
- Searches over structured content like tables aren't well-supported yet.

For the Azure AI Search plugin specifically:

- Only one index at a time can be connected using the plugin. To query a different index, you need to update the plugin settings.
- To invoke the plugin, you need to explicitly mention "Azure AI Search" in the prompt.
- Copilot displays the titles of the referenced documents from the index, but they aren't hyperlinked.
![[Pasted image 20260825144713.png]]

![[Pasted image 20260825144717.png]]
![[Pasted image 20260825144801.png]]
![[Pasted image 20260825144904.png]]

# Summary and resources


In this module, learned about the core features of Microsoft Security Copilot. These features include promptbooks and creating custom promptbooks that provide security analysts a standardized set of prompts that serve as a framework for conducting investigations. You learned about the types of plugins that are available and enable integration with various sources, providing domain specific capabilities to aid your investigations.


