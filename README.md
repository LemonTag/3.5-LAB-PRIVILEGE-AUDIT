# 3.5-LAB-PRIVILEGE-AUDIT
3.5 LAB: PRIVILEGE AUDIT
## Scenario
The management team requested an audit of the Mad Hat Labs Azure tenant following concerns about access permissions after a previous security incident. The investigation focused on reviewing users, groups, and role assignments to identify who had access to sensitive resources, what permissions they held, and whether any access posed a security risk.

## Environment
One list: platform, services, tools, access level. Honest framing: "live multi-user Azure training tenant, Reader access."
Platform: Microsoft Azure (Mad Hat Labs training tenant).
Services: Microsoft Entra ID, Azure RBAC, Resource Groups, Privileged Identity Management (PIM).
Tools: Azure Portal, Azure CLI, PowerShell.
Access Level: Reader access in a live, multi-user Azure training tenant. No administrative permissions or ability to modify tenant configurations.

## Investigation
1. Reviewed Privileged Identity Management (PIM)

I started by navigating to Privileged Identity Management in Azure to review the available eligible roles. I found the rg-madhatlabs-hidden-pim resource group assignment and activated the eligible role so I could investigate the resource group. <img width="1664" height="562" alt="Screenshot 2026-11-11 122815" src="https://github.com/user-attachments/assets/f4db4b5a-5749-49ed-976f-f55c880dde70" />

2. Located the hidden PIM resource group

After activating the role, I returned to Resource Groups and located rg-madhatlabs-hidden-pim. This confirmed that the resource group was available for further investigation.<img width="1726" height="758" alt="Screenshot 2026-11-11 123441" src="https://github.com/user-attachments/assets/d2de0f7e-d502-4ee2-a32a-d663986b8966" />

3. Investigated the role assignments

I opened the hidden PIM resource group and downloaded its role assignment information. While reviewing the assignments, I found the lab flag inside the Role Assignment Description field.

<img width="1147" height="519" alt="image" src="https://github.com/user-attachments/assets/3953a509-7130-4554-b317-dbd2f4ede98b" />

4. Recorded the finding

I documented the recovered flag and identified the role assignment description as the location where the security team had hidden the information. This demonstrated the importance of reviewing role assignment details rather than only looking at role names and permissions.


## What broke / what surprised me
Challenges and Roadblocks

One of the biggest challenges I faced was navigating Privileged Identity Management (PIM). After activating my eligible role, I struggled to understand where I needed to go next and what actions I was supposed to take. This made parts of the assignment, especially Part 5, more difficult because I wasn't always sure if I was following the correct process.

What surprised me was that I was actually doing everything correctly in Part 5 until the final step. My mistake was downloading the JSON file instead of the CSV file. At the time, I didn't fully understand the difference between the two formats or what kind of information each one provided.

This experience taught me that completing a technical task isn't just about following instructions. It's also important to understand the tools you're using and the data you're collecting. I still need to improve my understanding of JSON and CSV formats, but I now recognize why choosing the correct file format matters when working with exported data.


## Findings and recommendations
What I determined:

During this investigation, I learned how Azure Privileged Identity Management (PIM) and role assignments are used to manage access to resources. I was able to locate and activate the eligible role needed to continue the investigation. I also learned how important it is to follow the correct process when exporting information, as downloading a JSON file instead of a CSV file initially caused confusion during Part 5.

This investigation helped me better understand how user permissions and group access can affect the security of Azure resources. It also showed me the importance of reviewing access assignments and verifying that users and groups only have the permissions they need.

Recommendations:

Review role assignments regularly: Resource owners should periodically audit users and security groups to make sure they only have the permissions necessary for their responsibilities. Remove access that is no longer needed.

Use Privileged Identity Management: Require eligible users to activate elevated permissions only when necessary instead of providing permanent administrative access. This helps reduce the risk of unauthorized or unnecessary access.


## What I learned
Technical: I learned how Azure Privileged Identity Management (PIM) works and how eligible roles must be activated before accessing certain resources.

Technical: I learned the difference between JSON and CSV exports. CSV is easier to review in spreadsheets, while JSON is useful for examining structured and nested data.

Troubleshooting: I learned that even when I'm following the correct steps, small mistakes, such as choosing the wrong export format, can affect the outcome.

What I'd do differently: I would spend more time understanding the Azure portal and where each option leads before activating roles. This would help me avoid getting lost or wasting time figuring out the next step.


