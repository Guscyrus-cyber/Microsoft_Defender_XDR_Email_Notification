**Incident, Action, and Threat Analytics Email Notifications**

**Introduction**

This lab configures Microsoft Defender XDR to send operational email notifications when important security events occur. The objective is to ensure that SOC analysts receive timely notice of new incidents, completed or failed response actions, and newly published threat-analytics reports without continuously watching the portal.

The lab will create and verify three notification rules:

1.  **Incident notifications** — notify the SOC when qualifying incidents are generated or updated.

2.  **Action notifications** — notify the SOC about manual or automated response-action results.

3.  **Threat analytics notifications** — notify the SOC when Microsoft publishes relevant threat intelligence.

The rules will use meaningful names, appropriate severity filters, and a controlled recipient address to avoid unnecessary alert noise.

**Lab objectives**

- Configure incident email notifications.

- Select appropriate incident severities and notification conditions.

- Configure action-center email notifications.

- Configure threat-analytics email notifications.

- Apply practical SOC notification scopes.

- Verify that all three notification rules were saved.

- Capture only report-quality screenshots for GitHub.

**Step 1 — Open Email Notifications directly**

1.  I open [<u>https://security.microsoft.com</u>](https://security.microsoft.com).

2.  I go to: **System → Settings → Microsoft Defender XDR → Email notifications**

The **Email notifications** page showing its notification categories or tabs.This establishes the starting point and confirms that the tenant provides the necessary notification features.

The page confirms that **no incident notification rules currently exist**. Email notifications

Incidents category\
**0 items**\
Add incident notification rule

No sensitive identifiers are visible. (Image 1)

**Step 2 — Create the incident notification rule**

I click **Add incident notification rule**.

The wizard has four stages: Basics, Notification settings, Recipients, and Review rule.

**Name:** SOC High and Medium Incident Notifications\
**Description:** Sends email notifications to the SOC when new high- or medium-severity incidents are generated from Microsoft Defender XDR custom detections, Defender XDR detections, or manual incidents.

This scope prioritizes incidents that normally require timely analyst attention while avoiding unnecessary low-severity notification volume. (Images 2)


I click **Next**. The notification settings allow control over email frequency, context, source, and severity.

I select these three options:

**Send only one notification per incident** — prevents duplicate emails when the same incident is repeatedly updated.\
**Include organization name in the email** — helps identify the affected tenant.\
**Include tenant-specific portal link** — allows the analyst to open the incident directly from the email.

Then I click the **Sources** dropdown. The source list separates incidents by security service and detection origin. (Images 3 and 4)\

Then I select the top-level checkbox:\
**Microsoft Defender XDR**

This includes:

Custom detection\
Defender XDR\
Manual

Including **Manual** is useful because a controlled manual test incident may trigger the rule. (Image 5)

I close the Sources dropdown, then I open **Alert severity**.\

I select:

**Medium**
**High**

I leave **Informational** and **Low** unchecked to reduce notification noise.

The sources already show Custom detection, Defender XDR, and Manual, so no additional service row is needed.

I click **Next**. (Image 6)


I enter my personal email address whose inbox can be checked immediately because the Defender administrator account may not have an Exchange mailbox license.

1.  I enter the monitored email address.

2.  I click **Add**.

3.  I select the added recipient.

4.  I click **Send test email**.

5.  I check my email address, all the inbox and spam/junk folders for the Microsoft Defender test message.

The recipient was added and the test email was sent. (Image 7)


The test succeeded. The email confirms:

Microsoft Defender can deliver email to the configured recipient.\
The recipient list is valid.\
The rule is configured for **Medium** and **High** severities.\
The message came from Microsoft Defender’s notification service.

1.  The test verifies email delivery, but it does not yet prove that a real incident triggers the rule. That will be tested after the rule is saved. (Image 8, 9)\

**Step 3- Create notification rule:**
\
I Return to the Defender tab.\
I click **Next** on the Recipients page.

Rule name and description match the available Defender XDR sources.\
Duplicate notifications are limited.\
Organization name and portal link are included.\
Custom detection, Defender XDR, and Manual sources are covered.\
Medium and High severities are selected.\
Test delivery succeeded.\
I Click **Submit**.(Images 10 and 11)

> 

The incident notification rule was created successfully.

### Incident notification configuration completed

Medium and High incidents covered
Custom detection, Defender XDR, and Manual sources included
Duplicate incident emails limited
Organization name and direct portal link included
Recipient delivery verified through a test email (Image 12)

**Step 4 — Locate Action and Threat Analytics notifications**

I click **Done** to return to the Email notifications page. This is necessary to determine whether **Actions** and **Threat analytics** appear as additional tabs, sections, or tenant-dependent options. No menu exploration is required.\
The incident rule is saved and visible as **1 item**. The tenant currently displays only the **Incidents** notification category. **Actions** and **Threat analytics** are not available on this page. Their notification options may depend on additional Defender workloads, licensing, and endpoint activation. Since MDE has not been onboarded, those portions cannot be configured at this stage and should be documented as deferred. (Image 13)

**Step 5 — Attempt a controlled manual incident test**

1.  I Click **Incidents** in the narrow left shortcut bar.

2.  I Look only for a button such as:

    - **Create incident**

    - **New incident**

    - **Add incident**

If manual incident creation is supported, a harmless Medium-severity test incident will be created to validate the real notification flow. (Images 14, 15, 16, and 17)


There is **plus (+) button** in the incident toolbar. This is likely the manual incident-creation function required for the validation test. I click the blue **+** above the incident table.(Image 18)\
The portal supports creating a manual alert and optionally correlating it into an incident. This is exactly the controlled validation needed.

**Alert title:** LAB TEST - Defender XDR Incident Email Notification

**Severity:** Medium

**Description:** Controlled lab alert created to validate Microsoft Defender XDR incident email notification delivery. No malicious activity occurred and no production asset was affected.

**Recommended actions:** Confirm that the incident is created, verify receipt of the notification email, document the result, and then classify and resolve the test incident. (Image 18)


Then I open the **Category** dropdown.\
I select **Others**.

That is the most accurate category because this is a notification-validation test, not evidence of ransomware, malware, execution, or another real attack tactic. Selecting a threat category would create misleading incident data. (Image 19 and 20)\


After selecting **Others**, I click **Next**.\
**Impacted assets** is required, so the wizard cannot proceed without one. A production identity or the administrator account should not be used. Then I click Add assets. (Image 21)


I click the **Entity name or ID** field and search for: SOC Test User\
This is the dedicated lab identity created earlier, so it is the safest available impacted asset for the simulated alert.\
The **SOC Test User** is selected as the impacted asset. I leave **Related evidence** empty because this is a controlled notification test. (Image 22)


I click next.\
**Incident correlation\**
SOC Test User appears in the field.\
I click the dropdown arrow inside **Entity name or ID**.

I search for SOC Test User.\
I click the matching user result, so Defender registers it as an asset.\
I confirm the field displays the selected user as a recognized entry. (Image 23)\

I click **Next**. The correct asset-selection form is open.

I select **User** as the entity type.\
I search for **SOC Test User**.\
I select the matching result from the list\
I leave **Related evidence** empty.(Image 24)\

I select **AccountUpn**.

In **Identifier value**, I enter the SOC Test User’s complete sign-in address:

testuser01@liberty566yahoo.onmicrosoft.com

I use my exact address assigned to that test user, then I click **Next**.\
The asset was accepted, and I **create a new incident**.

I eave **Exclude this incident from incident correlation** unchecked. Although this is a controlled test, keeping normal correlation enabled lets the lab validate the standard Defender XDR incident workflow. (Image 25)


I click **Next**.\
The review confirms the controlled alert is configured correctly:

Title clearly identifies it as a lab test\
Severity: **Medium**, matching the notification rule\
Category: **Others**\
Impacted asset: SOC Test User\
A new incident will be created\
Normal incident correlation remains enabled (Images 26 and 27)


I click **Submit**.\
The incident appears in the incident queue.

A real incident-notification email arrives.\
The test incident is classified and resolved safely. the controlled alert was created and linked to **Incident 1**. (Image 28)\

I click **Incident 1** under **View incident**.\
The live incident is confirmed:

Incident ID: **1**\
Severity: **Medium**\
Status: **Active**\
Classification: **Unclassified**\
Active alerts: **1/1**\
Impacted asset: **SOC Test User**\
Alert title clearly identifies the controlled lab test (Image 29 and 30)\

I check my Gmail inbox used in the notification rule. I look for a new Defender incident notification—not the earlier **test notification**.

The real email notification was delivered for **Incident 1**, confirming the rule works end to end: **Manual alert → Medium-severity incident → notification rule match → email delivered** (Image 31)


Now I return to the Defender incident tab. I close the **Tasks** panel, and I click the current **Active** status near the incident title.\
I need to return to **Incident 1** and classify it as **Informational** which it was a controlled notification test.\
On the **Incident 1** page, I click **Unclassified** near the top.\
I set **Classification** to **Informational, expected activity**.

1.  I choose **Other**.

2.  I set **Status** to **Resolved**.

3.  I Add this commend: Controlled lab incident created to validate Defender XDR email notifications. No malicious activity occurred.

4.  I save the changes.

<!-- -->

1.  Then I select the **three dots (…)** beside the incident title and choose **Manage incident**.\
    I click **Unclassified**. That opens the incident classification controls. (Image 32)\
    
    Then I click mange inciden.\
    I leave **Severity** as Medium.

> I optionally add the tag Lab Test.\
> I change **Status** from Active to Resolved.\
> I change **Classification** from Unclassified to Informational, expected activity.\
> I select the lab/test equivalent.\
> I click **Save**. (Images 33 and 34)\
> \
