---
description: Setup access to my clients
---

# SAM Setup

This section describes the best practices and recommended setup for CIPP, including account usage, multi factor authentication, and DAP/GDAP groups. This section also describes the recommended setup for Conditional Access Policies. When this document has not been implemented you could encounter issues with the CSP, Graph, or Exchange sections of CIPP.

{% hint style="danger" %}
Failing to adhere precisely to these instructions may result in a malfunctioning CIPP instance where features don't work as expected. Do not deviate from these instructions and follow them to the letter.&#x20;
{% endhint %}

## Authorization requirements

to setup the Graph API, CSP, and Exchange integration CIPP requires a minimum level of permissions. We recommend to setup the account as follows

1. Create a new account. Recommended to name this "CIPP Integration" and give it the username "CIPP@domain.tld" a. This account must be a Global Administrator while setting up the integration. These permissions may be removed after the integration has been setup.
2. Add the account to the correct groups

* The CIPP user must be added to the **"AdminAgents**" group and the groups you've assigned for GDAP. The minimum GDAP **groups** & permissions CIPP needs to function are:
  * Application Administrator
  * Authentication Policy Administrator
  * Cloud App Security Administrator
  * Cloud Device Administrator
  * Exchange Administrator
  * Intune Administrator
  * Privileged Role Administrator
  * Security Administrator
  * SharePoint Administrator
  * Teams Administrator
  * User Administrator
  * Privileged Authentication Administrator
* These groups are **not roles in your own tenant.** These must be the GDAP assigned **groups.**
* Do not over-assign GDAP groups. Too many permissions will stop GDAP functionality. For more information check out Microsoft's documentation [here](https://learn.microsoft.com/en-us/partner-center/gdap-faq)

3. This account must have **Microsoft** multi-factor authentication enforced for each logon, either via Conditional Access when available or via [Per User MFA](https://account.activedirectory.windowsazure.com/UserManagement/MultifactorVerification.aspx) when Conditional Access is not available.

* You may not use any other authentication provider than Microsoft for this account. Duo or other providers will not work. For more information on this see [this](https://learn.microsoft.com/en-us/partner-center/partner-security-requirements-mandating-mfa#supported-mfa-options)
* The CIPP service account requires MFA for each logon. That means no excluded locations may be applied nor authentication length policies. See the chapter about conditional access to make sure your policies are configured correctly.

The account will be used for all actions performed from the CIPP portal.

## Setup Video for SAM Service Account

{% embed url="https://app.guidde.com/share/playbooks/i9fztXsCUWjY3cr8mySvCX" fullWidth="false" %}

## Executing the wizard

{% hint style="danger" %}
Make sure you are logged into CIPP under your own account (user@domain.com). The CIPP SAM wizard will prompt you to logon, at this moment you use the CIPP Service Account(CIPP@domain.com).

Your browser **MUST** allow cookies and have any ad-blocker disabled for the duration of the wizard. Do not use in-private mode.
{% endhint %}

To setup the connection to your tenants you'll need to run the Sam Wizard. The Sam Wizard can be found under Settings -> SAM Setup Wizard. The Wizard will present you with multiple options. If this is your first setup it is recommended to choose "I'd like CIPP to create a SAM Application for me".

When executing the Sam Wizard with "I'd like CIPP to create a SAM Application for me" you'll be presented with a button to start the Wizard. Do not navigate away from this page and execute all **5 steps** that this page will prompt you for.

After completing the wizard 5 steps, you must [clear the token cache](https://cipp.app/docs/general/troubleshooting/#clear-token-cache).

{% embed url="https://app.guidde.com/share/playbooks/cHS8iUw2JCAGwiJxSnp7sp?origin=IEPB08VSavefFaCa9OSp3Y87aGu1" %}