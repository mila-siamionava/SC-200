CopilotOrganizations face unprecedented challenges, in the rapidly evolving digital landscape, such as increasingly sophisticated cyber threats and a significant talent shortage in cybersecurity. [[Microsoft Security Copilot ]]is a ==cloud-based, AI-powered security analysis tool== that is designed to address these challenges. It enables analysts to process security signals and respond to threats at a machine speed that far surpasses human capabilities, thus revolutionizing the way organizations approach cybersecurity.
# Get acquainted with Microsoft Security Copilot
The top security challenges organizations face include:
- An increase in the number and sophistication of attacks.
- A talent shortage that's driving the need for automation, integration, and consolidation of security tools.
- Visibility into security, privacy, compliance, and governance.
- 
Organizations need to act quickly to address the security challenges they face, but working at human speed, even if there weren't a talent shortage, isn't enough. Organizations need to work at machine speed.Microsoft Security Copilot is an AI-powered, cloud-based security analysis tool that enables analysts to respond to threats quickly, process signals at machine speed, and assess risk exposure more quickly than may otherwise be possible.
### Use cases
[[Security Copilot]] focuses on making the following highlighted use cases easy to use.
- Investigate and remediate security threats - gain context for incidents to quickly triage complex security alerts into actionable summaries and remediate quicker with step-by-step response guidance
- Build Kusto Query Language (KQL) queries or analyze suspicious scripts - eliminate the need to manually write query-language scripts or reverse engineer malware scripts with natural language translation to enable every team member to execute technical tasks
- Understand risks and manage security posture of the organization - get a broad picture of your environment with prioritized risks to uncover opportunities to improve posture more easily
- Troubleshoot IT issues faster - synthesize relevant information rapidly and receive actionable insights to identify and resolve IT issues quickly
- Define and manage security policies - define a new policy, cross-reference it with others for conflicts, and summarize existing policies to manage complex organizational context quickly and easily
- Configure secure lifecycle workflows - build groups and set access parameters with step-by-step guidance to ensure a seamless configuration to prevent security vulnerabilities
- Develop reports for stakeholders - get a clear and concise report that summarizes the context and environment, open issues, and protective measures prepared for the tone and language of the report’s audience
These use cases represent just a few of the capabilities that Copilot delivers and that helps make analysts more productive and also helps up-level them.
### Standalone and embedded experience
You can experience Copilot through the dedicated site, also referred to as the standalone experience. Users interact with Copilot through the prompt bar. In the prompt bar, users make requests in natural language and receive response outputs as text, images, or documents.[![Screenshot that shows the landing page for the Security Copilot standalone experience. The prompt bar is at the bottom center of the page.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/copilot-new-landing-page.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/copilot-new-landing-page.png#lightbox)Additionally, some Microsoft security products embed Copilot capabilities directly within the products’ user interface. This experience is referred to as the embedded experience. [[Microsoft Defender XDR]], for example, ==enables Copilot capabilities== including summarizing incidents, analyzing scripts, generating KQL queries, and more.[![Diagram that shows the advanced hunting page of Microsoft Defender XDR, The page includes a button for Copilot that When selected opens a side panel for natural language to KQL query assistant.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/security-copilot-embedded-m365-xdr-v3.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/security-copilot-embedded-m365-xdr-v3.png#lightbox)More information on both the standalone and embedded experience are covered in subsequent modules. Images shown throughout the rest of this module are based on the standalone experience.Watch this short video for a summary of the users' experiences that Security Copilot offers.
### Natural language processing (NLP)
[[Copilot]] is built using ==Azure OpenAI Services== and is designed to integrate with existing security tools and processes, making it easier for organizations to improve their overall security posture. 
Azure OpenAI Services provides REST API access to OpenAI's powerful large language models (LLMs) for natural language processing (NLP), while providing security capabilities of Microsoft Azure.
With access to the powerful LLMs for NLP, Copilot is able to read, decipher, and make sense of human languages, enabling users to securely interact with it using natural language. Although the LLMs are trained on a vast amount of information that endows Copilot with broad general knowledge and problem solving abilities, it’s not enough. Security analysts expect their copilot to be trained on security and that's where the integration with existing security tools and processes comes into play.
### Integration with Security-specific sources
Copilot combines powerful LLMs with security-specific sources from Microsoft. These security-specific sources are informed by Microsoft’s unique global threat intelligence, more than 65 trillion daily signals, and incorporates information from a growing set of security solutions using plug-ins and connections to knowledge bases. Through plug-ins, Copilot integrates with Microsoft's own security products, non-Microsoft products, and open-source intelligence feeds. Connections to an organization's knowledge bases gives Copilot more context, resulting in responses that are more relevant, specific, and customized to the user. Through the powerful combination of advanced general models and security specific sources, Copilot is able to learn at machine speed to help analysts identify and respond to emerging threats.
The information you give Copilot is only accessible to your organization. Your data is your data, and it's protected by comprehensive enterprise compliance and security controls. Your data isn't used to train the foundation AI models.[![Diagram showing key attributes of Security Copilot, including hyperscale AI infrastructure, security specific orchestrator,evergreen threat intelligence, and cyber skills and promptbooks.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/security-copilot-stack.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/security-copilot-stack.png#lightbox)Microsoft Security Copilot is the first security product to enable defenders to move at the speed and scale of AI.

# Describe Microsoft Security Copilot terminology
In this unit, we introduce you to some basic terminology.

### Terminology

The following terms are important for understanding the way Microsoft Security Copilot works:

- Session – A particular conversation within Copilot. Copilot maintains context within a session.
- Prompt – A specific statement or question within a session. A user enters a prompt in the prompt bar.
- Capability – A function Copilot uses to solve part of a problem. A capability may sometimes be referred to as a skill.
- Plugin – A collection of capabilities by a particular resource.
- Workspace - Copilot workspaces are separate Copilot work environments within the tenant in which your Copilot instance is operating.
- Agents - Microsoft Security Copilot agents are AI-powered tools that autonomously manage security and IT tasks, enhancing threat response, reducing manual workloads, and improving efficiency across cybersecurity operations at scale.
- Orchestrator – Copilot’s system for composing capabilities together to answer a user’s prompt.

_**Prompt bar and sessions**_

At the center of Security Copilot is the prompt bar. You use the prompt bar to tell Copilot what insights you want from your security data, this is referred to as the prompt. In other words, the prompt is the text-based, natural language input you provide in the prompt bar that instructs Copilot to generate a response. Although you interact with Copilot in natural language, it’s helpful to be specific in the prompts (specific questions or statements) that you provide. For those that are relatively new to the security analyst role and engaging with AI, effective prompting may take some practice. For this reason, Copilot provides promptbooks that provide a series of preselected prompts and prompt suggestions (more details on this in a subsequent module).

[![A screen capture of the Microsoft Security Copilot prompt bar.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/prompt-bar-new.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/prompt-bar-new.png#lightbox)

As you make requests and as Copilot responds, you might have some follow-up requests. The entirety of the dialog is referred to as a session. Copilot maintains context within a session.

_**Plugins and capabilities**_

In the previous unit, we mentioned that Copilot integrates with various sources through plugins, including Microsoft's own security products such as Microsoft Sentinel, Microsoft Defender XDR, and Microsoft Intune, non-Microsoft solutions, and open-source intelligence feeds. The integration enabled by the plugin, for any specific data source, provides Copilot with a collection of capabilities. Each capability is like a function in software, it’s designed to do a specialized task within the scope of the data source. For example, the plugin to Microsoft Defender XDR includes a collection of individual capabilities that are used only by Microsoft Defender XDR. These include:

- The ability to summarize an incident.
- Support incident response teams in resolving incidents through guided responses (a set of recommended actions based on the specific incident).
- The ability to analyze scripts and code.
- The ability to generate KQL queries from natural language input.
- The ability to generate incident reports.

A plugin for Microsoft Sentinel might have similar capabilities but runs only within the scope of Microsoft Sentinel.

Copilot currently supports plug-ins for Microsoft services and non-Microsoft services, including websites and custom plug-ins that can be enabled.

[![A screen capture of the plugins window, showing the Microsoft plugins, including Microsoft Entra, Intune, Microsoft Defender XDR, and more.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/microsoft-plugins-updated.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/microsoft-plugins-updated.png#lightbox)

[![A screen capture of the plugins window, showing the non-Microsoft plugins, including ServiceNow, Splunk, the public web, and custom plugins.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/non-microsoft-plugins-updated.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/non-microsoft-plugins-updated.png#lightbox)

Some plugins require setup and configuration, as depicted by the Setup button or the gear icon. For Microsoft plugins, set up might be required where resource specific information needs to be specified. For non-Microsoft sources, set up might be required for account authentication.

_**Workspaces**_

Copilot workspaces are separate Copilot work environments within the tenant in which your Copilot instance is operating.

To help you better understand the concept of workspaces, we use the analogy of house with multiple rooms. Each room is configured to be optimized for its function and the people that use that room. When someone enters the house, they might have access to some rooms but not others.

[![Illustration of a house, which is like a tenant and a room in the house is like a workspace in Security Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/workspace-overview.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/workspace-overview.png#lightbox)

You can think of Copilot Workspaces fitting into this analogy. A Copilot workspace is analogous to a room in a house. You can also think of the house as analogous to a tenant. In the same way that a house has multiple rooms, the tenant in which Copilot is operating can have multiple workspaces.

[![A screenshot of the manage workspaces page that lists the available workspaces.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/workspace-manage-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/workspace-manage-v2.png#lightbox)

Through the tenant-switching capability in Security Copilot, a user can select in which tenant they'll be working. In our analogy, this is a Copilot user getting access to the house. Once the tenant is selected, a Copilot user can access and work in any workspace (room in the house) to which they have access, within the context of their role permissions in that workspace.

Workspaces are powered by capacities and each workspace must have its own capacity.

Using workspaces, you can efficiently map and monitor costs based on team needs and budgets, ensuring that teams have the capacity they need and resources are allocated effectively. Having workspaces also allows you to store session data according to geo-specific regulations and adhere to local data protection laws. These are just a few of the benefits of using workspaces.

For more information, see "Describe workspaces", which is linked in the Summary and resource section of this module.

_**Agents**_

A Microsoft Security Copilot agent is an advanced, AI-powered assistant built into Microsoft Security Copilot. These agents go beyond just answering questions—they can autonomously manage high-volume security and IT tasks. They’re deeply integrated with Microsoft’s security tools and can also work with partner solutions. Each agent is tailored for specific security scenarios, such as threat protection, identity management, or data security.

These agents are designed to learn from feedback, adapt to your organization’s workflows, and operate securely within Microsoft’s Zero Trust framework. See the summary and resources unit for links to more information on Microsoft Security Copilot agents.

[![A screen capture of the agents page in Microsoft Security Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/active-agents.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/active-agents.png#lightbox)

_**Orchestrator**_

The orchestrator is Copilot’s system for composing capabilities together to answer a user’s prompt. This function is illustrated in more detail in the subsequent unit that describes how Copilot processes prompt requests.

# Describe how Microsoft Security Copilot processes prompt requests
So now that there's a basic understanding of plugins, capabilities, and how the user interacts with Microsoft Security Copilot through prompts, it’s worth taking a look under the hood to see how these components come together to process a prompt request and help security analysts.

### Process flow

When a user submits a prompt, Copilot processes that prompt to generate the best possible response. The diagram that follows illustrates, at a high level, steps that Copilot takes to process the prompt and generate a response.

[![Diagram illustrating how Microsoft Security Copilot processes a prompt request.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/copilot-how-it-works-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/copilot-how-it-works-v2.png#lightbox)

1. Submit a prompt: The process starts when a user submits a prompt in the prompt bar.
    
2. Orchestrator: Security Copilot sends the information to the Copilot backend referred to as the orchestrator. The orchestrator is Copilot’s system for composing capabilities together to answer a user’s prompt. It determines the initial context and builds a plan using all the available capabilities (skills).
    
3. Build context: Once a plan is defined and built, Copilot executes that plan to get the required data context to answer the prompt.
    
4. Plugins: In the course of executing the plan, Copilot analyzes all data and patterns to provide intelligent insights. This includes reasoning over all the plugins and sources of data, enabled and available to Copilot.
    
5. Responding: Copilot combines all the data and context and uses the power of its advanced LLM to compose a response using language that makes sense to a human being.
    
6. Response: Before the response can be sent back to the user, Copilot formats and reviews the response as part of Microsoft's commitment to responsible AI.
    
7. Receives response: The process culminates with the user receiving the response from the Copilot.
    

#### Process log

During this process, Copilot generates a process log that's visible to the user. The user can see what capability is used to generate the response. This is important because it enables the user to determine whether the response was generated from a trusted source. In the screenshot that follows, the process log shows that Copilot chose the Incident Analysis capability. The process log also shows that the final output went through safety checks, which is part of Microsoft’s commitment to responsible AI.

[![Screen capture of the process log that highlights the capability selected and the text indicating that Copilot ran safety checks as part of the process to compose the response message.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/process-log-new.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/process-log-new.png#lightbox)

# Describe the elements of an effective prompt
In a previous unit, we defined a prompt as the text-based, natural language input you provide in the prompt bar that instructs Microsoft Security Copilot to generate a response. Copilot provides promptbooks and prompt suggestions, which are helpful, particularly if you're just starting an incident investigation. At some point, however, you'll want and need to enter your own prompts. In those cases, the quality of the response that Copilot returns depends in large part on the quality of the prompt used. In general, a well-crafted prompt with clear and specific inputs leads to more useful responses by Copilot.

### Elements of an effective prompt

Effective prompts give Copilot adequate and useful parameters to generate a valuable response. Security analysts or researchers should include the following elements when writing a prompt.

- Goal - specific, security-related information that you need
- Context - why you need this information or how you use it
- Expectations - format or target audience you want the response tailored to
- Source - known information, data sources, or plugins Copilot should use

[![Diagram that four elements of an effective prompt: the goal, context, expectations, and source.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/effective-prompts.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/effective-prompts.png#lightbox)

Every good prompt should have a goal. Whether it comes in the form of instructions or questions, it should indicate what you want out of your current session.

For Copilot, context can refer to the time frame, or that you use the response for a report. Expectations can include whether you want the response to be in a table format, a list of action steps, a summary, or even a diagram. Source might be useful in specifying which Microsoft plugins you're referring to, if needed. Some plugins require more context to work effectively or supporting plugins to ensure a response when initial responses fail.

Watch this short video for a summary on how to create effective prompts.

### Other prompting tips

Some things to remember when coming up with your own prompts:

- Be specific, clear, and concise as much as you can about what you want to achieve. You can always start simply with your first prompt, but as you get more familiar with Copilot, include more details following the elements of an effective prompt.
    
    - Basic prompt: Pearl Sleet actor
    - Better prompt: Can you give me information about Pearl Sleet activity, including a list of known indicators of compromise and tools, tactics, and procedures (TTPs)?
- Iterate. Subsequent prompts are typically needed to further clarify what you need or to try other versions of a prompt to get closer to what you're looking for. Like all LLM-based systems, Copilot can respond to the same prompt in slightly different ways.
    
- Provide necessary context to narrow down where Copilot looks for data.
    
    - Basic prompt: Summarize incident 15134.
    - Better prompt: Summarize incident 15134 in Microsoft Defender XDR into a paragraph that I can submit to my manager and create a list of entities involved.
- Give positive instructions instead of "what not to do." Copilot is geared toward action, so telling it what you want it to do for exceptions is more productive.
    
    - Basic prompt: Give me a list of unmanaged devices in my network.
    - Better prompt: Give me a list of high-risk unmanaged devices in my network. If they're named "test" remove them from the list.
- Directly address Copilot as "You" as in, "You should ..." or "You must ...," as this is more effective than referring to it as a model or assistant.
    

While these guidelines can help you get started in creating prompts, it’s important to note that you’re not limited to forming prompts following the structure of the previous examples. What’s great about Copilot is that it's designed to respond to questions or instructions made in your own words (that is, using natural language).

You have the flexibility to adapt these guidelines to your specific needs.

# Describe how to enable Microsoft Security Copilot
To start using Microsoft Security Copilot, organizations need to take steps to onboard the service and users. These include:

1. Identify your customer category
2. Provision Copilot capacity (if required)
3. Set up the default environment
4. Assign role permissions

### Identify your customer category

Your onboarding experience depends on your license status:

- **Microsoft 365 E5 and E7 customers** - Security Copilot is included with your Microsoft 365 E5 and E7 license. Microsoft automatically provisions and onboards Security Copilot for eligible tenants through zero-click activation, so no Azure setup or manual capacity provisioning is required. Customers receive a 7-day advance notification before activation. Once provisioning is complete, Security Copilot is ready for use.
- **Non-Microsoft 365 E5 and E7 customers** - If Security Copilot isn't included in your license, you must follow the manual onboarding steps to provision Security Compute Units (SCUs) to use Security Copilot.

### Provision capacity

For non-Microsoft 365 E5 and E7 customers, Security Copilot operates on a provisioned capacity and an overage model. Provisioned capacity is billed by the hour while the overage capacity is billed on usage.

You can flexibly provision Security Compute Units (SCUs) to accommodate regular workloads and adjust them anytime without long-term commitments. An SCU is the unit of measure of computing power used to run Copilot in both the standalone and embedded experiences.

To manage unexpected demand spikes, you can allocate an overage amount to ensure that additional SCUs are available when initially provisioned units are depleted during unexpected workload spikes. Overage units are billed on-demand and can be set as unlimited or a maximum amount. This approach enables predictable billing while providing the flexibility to handle both regular and unexpected usage. See the summary and resources section of this module for links to information on Managing security compute unit usage and Security Copilot pricing.

Before users can start using Copilot, admins need to provision and allocate capacity. To provision capacity:

- You must have an Azure subscription.
    
- You need to be an Azure owner or Azure contributor, at a resource group level, as a minimum.
    
- You need to be a Security Administrator or higher in the tenant you're onboarding Security Copilot.
    
    _Keep in mind that a global Microsoft Entra administrator role doesn't necessarily have the Azure owner or Azure contributor role by default. Microsoft Entra role assignments don't grant access to Azure resources. As a global Microsoft Entra administrator, you can enable access management for Azure resources through the Azure portal. For details, see [Elevate access to manage all Azure subscriptions and management groups](https://learn.microsoft.com/en-us/azure/role-based-access-control/elevate-access-global-admin). Once you've enabled access management to Azure resources, you can configure the appropriate Azure role._
    

There are two options for provisioning capacity:

- Provision capacity within Security Copilot (recommended) - When you first open Security Copilot as an admin, a wizard guides you through the steps in setting up capacity, including workspace creation. The wizard prompts you for information including workspace name, Azure subscription, resource group, region, capacity name, and the quantity of SCUs.
- Provision capacity through Azure - The Azure portal now includes Security Copilot as a service. Selecting the service, opens the page where you input information including your Azure subscription, resource group, region, capacity name, and the quantity of SCUs.

 Note

Regardless of the method you choose, you need to purchase a minimum of one and a maximum of 100 SCUs. The recommended number of units to conduct an introductory exploration of Security Copilot is three units with overage set to unlimited overage.

- [Provision through Copilot](https://learn.microsoft.com/en-gb/training/modules/security-copilot-getting-started/6-describe-how-to-enable-security-copilot?tabs=provision-through-copilot#tabpanel_1_provision-through-copilot)
- [Provision through Azure portal](https://learn.microsoft.com/en-gb/training/modules/security-copilot-getting-started/6-describe-how-to-enable-security-copilot?tabs=provision-through-copilot#tabpanel_1_provision-through-azure)

[![Screen capture showing the page for capacity provisioning through Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/create-security-capacity-page-no-pricing-info.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/create-security-capacity-page-no-pricing-info.png#lightbox)

Regardless of the approach you choose to provision capacity, the process takes the information and establishes a resource group for the Microsoft Security Copilot service, within your Azure subscription. The SCUs are an Azure resource within that resource group. Deployment of the Azure resource can take a few minutes.

Once admins complete the steps to onboard to Copilot, they can manage capacity by increasing or decreasing provisioned SCUs within the Azure portal or the Microsoft Security Copilot product itself.

Security Copilot provides a usage monitoring dashboard for capacity owners allowing them to track usage over time and make informed decisions about capacity provisioning. The usage monitoring dashboard provides visibility, for a selected workspace, into the number of units used, the specific plugins employed during sessions, and the initiators of those sessions. The dashboard also allows you to apply filters and export usage data seamlessly. The dashboard includes up to 90 days of data.

[![Screen capture showing the usage monitoring dashboard.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/usage-monitoring-v2.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/usage-monitoring-v2.png#lightbox)

### Set up the default environment

To set up the default environment, you need to have, at least, a Security Administrator role.

During the setup of Security Copilot, you're prompted to configure settings. These include:

- SCU capacity - Select the capacity of SCUs previously provisioned. Each workspace must have its own capacity.
    
- Data storage - When an organization onboards to Copilot, one of the available settings determines where your customer data will be stored. Configuration of the data storage location applies at a workspace level. Microsoft Security Copilot operates in the Microsoft Azure data centers in the European Union (EUDB), the United Kingdom, the United States, Australia and New Zealand, Japan, Canada, and South America.
    
- Decide where your prompts are evaluated - You can restrict the evaluation within your geo or allow evaluation anywhere in the world.
    
- Logging audit data in Microsoft Purview - As part of the initial setup and listed under Owner settings in the standalone experience, you can choose to allow Microsoft Purview to process and store admin actions, user actions, and Copilot responses. This includes data from any Microsoft and non-Microsoft Integrations. If you opt in and you already use Microsoft Purview, no further action is needed. If you opt in but aren't already using Purview, you need to follow the Microsoft Purview guides to set up a limited experience. This configuration applies to all workspaces in a tenant.
    
    [![Screen capture showing the settings for how you can configure audit logging.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/owner-settings-logging-audit-data.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/owner-settings-logging-audit-data.png#lightbox)
    
- Your organization's data - The admin must also opt in or opt out of data sharing options. These options are part of the initial setup and also listed under Owner settings in the standalone experience and can be configured per workspace. Turn the toggles on or off for any of the following options:
    
    - Allow Microsoft to capture data from Security Copilot to validate product performance using human review: When turned on, customer data is shared with Microsoft for product improvement. Prompts and responses are evaluated to understand whether the right plugins were selected, if the output is what was expected, how responses, latency, and output format can be improved.
        
    - Allow Microsoft to capture and human review data from Security Copilot to build and validate Microsoft's security AI model: When turned on, customer data is shared with Microsoft for Copilot AI improvement. Opting in does NOT allow Microsoft to use customer data to train foundational models. Prompts and responses are evaluated to enhance responses and to ensure they're what's expected and useful to you.
        
        For more information about how Microsoft handles your data, see [Data security and privacy](https://learn.microsoft.com/en-us/security-copilot/privacy-data-security).
        
        [![Screen capture showing the settings for how you can configure data sharing to help improve Copilot.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/help-improve-copilot.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/help-improve-copilot.png#lightbox)
        
- Plugin settings - The admin manages plugins and configures whether to allow Security Copilot to access data from your Microsoft 365 services. These settings are configured per workspace.
    
    - Configure who can add and manage their own custom plugins and who can add and manage custom plugins for everyone in the organization.
        
    - Manage plugin availability and restrict access. When enabled, admins decide which new and existing plugins are available to everyone in your organization, and which will be restricted to owners only.
        
    - Allow Security Copilot to access data from your Microsoft 365 services. If this option is turned off, your organization won't be able to use plugins that access Microsoft 365 services. Currently, this option is required for use of the Microsoft Purview plugin. Setting and/or changing this setting requires a user with a Copilot owner role or a global Microsoft Entra administrator role.
        
        [![Screen capture showing the plugin settings and the setting to allow Security Copilot to access data from your Microsoft 365 services.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/plugin-settings-no-restrictions.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/plugin-settings-no-restrictions.png#lightbox)
        

### Role permissions

To ensure that the users can access the features of Copilot, they need to have the appropriate role permissions. Role permissions are configured per workspace.

Permissions can be assigned using Microsoft Entra or Microsoft Purview roles, or Security Copilot roles. As a best practice, provide the least privileged role applicable for each user.

[[Security Copilot]] introduces two roles that function like access groups but aren't Microsoft Entra ID roles. Instead, they only control access to the capabilities of the Security Copilot platform and provide no access by themselves to security data.

The [[Microsoft Security Copilot roles]] are:

- Copilot owner
- Copilot contributor

The following ==Microsoft Entra and Microsoft Purview roles ==automatically inherit **Copilot owner** access, ensuring ==Security Copilot always has at least two owners:==

Microsoft Entra roles:

- Billing Administrator
- Microsoft Entra Compliance Administrator
- Global Administrator
- Intune Administrator
- Security Administrator

Microsoft Purview roles:

- Purview Compliance Administrator
- Purview Data Governance Administrator
- Purview Organization Management

[![Screen capture showing the role assignment settings.](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/role-assignments-new-edited.png)](https://learn.microsoft.com/en-gb/training/wwl-sci/security-copilot-getting-started/media/role-assignments-new-edited.png#lightbox)

Only users that have the global administrator, security administrator, or Copilot owner roles can make role assignments in Copilot by adding/removing members from the Owner and Contributor roles.

A group that admins/owners can include as a member of the Contributor role is the **Recommended Microsoft Security roles** group. This group exists only in Security Copilot and is a bundle of existing Microsoft Entra roles. When you add this group as a member of the Contributor role, all users that are members of the Microsoft Entra ID roles that are included in the recommended Microsoft Security roles group get access to the Copilot platform. This option provides a quick, secure way to give users in your organization, who already have access to security data used by Copilot through a Microsoft plugin, access to the Copilot platform.

For a detailed listing of the permissions granted for each of these roles, refer to the Assign roles section in [Understand authentication in Microsoft Security Copilot](https://learn.microsoft.com/en-us/security-copilot/authentication).

#### Copilot plugins and role requirements

Your role controls what activities you have access to, such as configuring settings, assigning permissions, or performing tasks. Copilot doesn't go beyond the access you have. Additionally, individual Microsoft plugins might have their own role requirements for accessing the service and data it represents. As an example, an analyst that has been assigned a security operator role or a Copilot workspace contributor role is able to access the Copilot portal and create sessions, but to utilize the Microsoft Sentinel plugin would need an appropriate role like Microsoft Sentinel Reader to access incidents in the workspace. To access the devices, privileges, and policies available through the Microsoft Intune plugin, that same analyst would need another service-specific role like the Intune Endpoint Security Manager role.

Generally speaking, Microsoft plugins in Copilot use the OBO (on behalf of) model – meaning that Copilot knows that a customer has licenses to specific products and is automatically signed into those products. Copilot can then access the specific products when the plugin is enabled and, where applicable, parameters are configured. Some Microsoft plugins that require setup might include configurable parameters that are used for authentication in-lieu of the OBO model.

Enabling of individual plugins and configuration of plugins is done per workspace.

![[Pasted image 20260824132803.png]]
![[Pasted image 20260824132835.png]]

![[Pasted image 20260824132856.png]]
![[Pasted image 20260824132909.png]]
![[Pasted image 20260824133321.png]]![[Pasted image 20260824133343.png]]![[Pasted image 20260824133610.png]]![[Pasted image 20260824133621.png]]![[Pasted image 20260824133633.png]]![[Pasted image 20260824133644.png]]![[Pasted image 20260824133655.png]]# Summary and resources

Microsoft Security Copilot is an AI-powered, cloud-based security analysis tool designed to help organizations meet the growing challenges of cybersecurity, such as increasing attack sophistication and a shortage of skilled personnel. It enables security analysts to respond to threats at machine speed, process signals rapidly, and assess risk exposure more efficiently than traditional methods. Copilot is a comprehensive solution for managing security posture, responding to incidents, and generating actionable security reports.

Copilot offers a user-friendly interface, allowing interactions through natural language prompts. It integrates seamlessly with Microsoft security products like Microsoft Defender XDR and Microsoft Sentinel and also with non-Microsoft solutions, through plugins, providing a unified view for security analysis. The use of OpenAI's natural language processing models enhances its capability to understand and process user requests, making it an effective tool for both seasoned and novice security analysts.

Copilot maintains high standards of data privacy and security. The process log feature further adds transparency, allowing users to track the source and validity of the information provided by the tool.


