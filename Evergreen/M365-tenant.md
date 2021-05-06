## Setup details

One paid tenant (croq.work) and a separate Dev tenant (tfivew).
Use croq.work for Email, Teams, SharePoint (content and prod-testing), services not available in dev tenant like SharePoint Syntex as well as Azure.

| Tenant               | Account |
| -------------------- | ------- |
| croqwork (croq.work) | bass    |
| tfivew (tfive.work)  | admin   |

<br/>

## Pre-installed

1. All Company site for Yammer
1. Communication site for SharePoint Home
1. Security Defaults enabled

## Next Actions

1. Domain should already be added from registration for the paid tenant, confirm via [Domains tab](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/Domains) under Admin Center. If not (and for dev tenant), you can add one via guided setup on the admin center homepage. Make sure to add for emails as well (and preferably before adding new users)
1. Configure AAD [Company branding](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/LoginTenantBranding) to change `Sign-in page background color` and `Banner logo`

   ### Optional

   1. Add SharePoint sites from [the look-book](https://lookbook.microsoft.com/) as needed

   1. **[Dev Tenant]** Add `Sample data packs, events and SharePoint sites` from M365 developer profile, good for demos
