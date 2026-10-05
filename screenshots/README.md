# Identity & Access Governance Lab Screenshots
 
This folder contains all screenshots from the Entra ID Identity & Access Governance Lab.
 
---
 
## Screenshot Index
 
| # | File Name | Description |
|---|-----------|-------------|
| 01 | `existing-compliant-devices-policy.png` | Existing Conditional Access policy requiring compliant devices |
| 02 | `licenses-entra-id-p2-intune.png` | Entra ID P2 and Intune Plan 1 licenses |
| 03 | `tenant-overview.png` | Tenant overview (tenant ID and domain redacted) |
| 04 | `intune-tenant-status.png` | Intune tenant status with 1 enrolled device |
| 05 | `ca-overview-page.png` | Conditional Access overview page |
| 06 | `mfa-policy-exclude-admin.png` | MFA Registration policy - excluding admin user |
| 07 | `user-risk-policy-config.png` | User Risk policy - High risk configured |
| 08 | `user-risk-policy-grant-password-change.png` | User Risk policy - Grant controls (MFA + Password change) |
| 09 | `three-ca-policies.png` | Three CA policies (MFA, User Risk, Compliant) |
| 10 | `signin-risk-policy-exclude-admin.png` | Sign-in Risk policy - excluding admin user |
| 11 | `signin-risk-policy-target-resources.png` | Sign-in Risk policy - All resources |
| 12 | `signin-risk-policy-config.png` | Sign-in Risk policy - Medium + High risk configured |
| 13 | `signin-risk-policy-grant-mfa.png` | Sign-in Risk policy - Grant MFA control |
| 14 | `signin-risk-policy-grant-mfa2.png` | Sign-in Risk policy - Grant MFA (continued) |
| 15 | `four-ca-policies.png` | All 4 Conditional Access policies |
| 16 | `breakglass1-create.png` | Creating Break Glass Account 1 |
| 17 | `breakglass1-role-global-admin.png` | Break Glass Account 1 - Global Admin role |
| 18 | `breakglass1-assignments.png` | Break Glass Account 1 - Role assignments |
| 19 | `two-breakglass-accounts.png` | Both break-glass accounts created |
| 20 | `emergency-group-add-owner.png` | Emergency-Access-Admins group - adding owner |
| 21 | `emergency-group-add-members.png` | Emergency-Access-Admins group - adding members |
| 22 | `emergency-group-created.png` | Emergency-Access-Admins group created |
| 23 | `policy1-exclude-group.png` | Policy-01 excluding Emergency-Access-Admins group |
| 24 | `policy2-exclude-group.png` | Policy-02 excluding Emergency-Access-Admins group |
| 25 | `policy3-exclude-group.png` | Policy-03 excluding Emergency-Access-Admins group |
| 26 | `pim-settings-activation.png` | PIM - Global Admin activation settings (MFA + Justification) |
| 27 | `pim-select-member.png` | PIM - Selecting member for role assignment |
| 28 | `pim-add-assignment.png` | PIM - Add assignment to Global Admin |
| 29 | `pim-eligible-assignment.png` | PIM - Eligible assignment (not active) |
| 30 | `pim-assignments-list.png` | PIM - Assignments list showing eligible role |
| 31 | `pim-activation-form.png` | PIM - Activation form with justification |
| 32 | `pim-active-role.png` | PIM - Role activated successfully |
| 33 | `catalog-create.png` | Entitlement Management - Creating catalog |
| 34 | `catalog-created.png` | Entitlement Management - Catalog created |
| 35 | `sc300-lab-group-create.png` | Creating SC300-Lab-Users security group |
| 36 | `two-groups-created.png` | Both groups created (Emergency + SC300) |
| 37 | `access-package-basics.png` | Access Package - Basics configuration |
| 38 | `access-package-select-group.png` | Access Package - Selecting SC300-Lab-Users group |
| 39 | `access-package-resource-roles.png` | Access Package - Resource roles (Member) |
| 40 | `access-package-requests.png` | Access Package - Request settings |
| 41 | `access-package-request-scope.png` | Access Package - Request scope (All members) |
| 42 | `access-package-approval.png` | Access Package - Approval required |
| 43 | `access-package-select-approver.png` | Access Package - Selecting approver |
| 44 | `access-package-approver-set.png` | Access Package - Approver configured |
| 45 | `access-package-lifecycle-expiration.png` | Access Package - Expiration settings |
| 46 | `access-package-lifecycle-reviews.png` | Access Package - Access reviews enabled |
| 47 | `access-package-lifecycle-advanced.png` | Access Package - Advanced lifecycle settings |
| 48 | `access-package-review-summary.png` | Access Package - Review + create summary |
| 49 | `access-review-create.png` | Access Review - Create new review |
| 50 | `access-review-settings.png` | Access Review - Settings (Auto-apply, Remove access) |
| 51 | `access-review-name-desc.png` | Access Review - Name and description |
| 52 | `access-review-summary.png` | Access Review - Confirm + create |
| 53 | `access-review-created.png` | Access Review - Created successfully |
| 54 | `final-all-policies-on.png` | FINAL - All 4 Conditional Access policies ON |
 
---
 
## Lab Components Summary
 
| Component | Status |
|-----------|--------|
| Entra ID P2 License | ✅ Active |
| Intune Plan 1 License | ✅ Active |
| Windows 11 VM | ✅ Compliant |
| MFA Registration Policy | ✅ ON |
| User Risk Policy | ✅ ON |
| Sign-in Risk Policy | ✅ ON |
| Device Compliance Policy | ✅ ON |
| Break-Glass Accounts | ✅ Created |
| PIM Configuration | ✅ Active |
| Access Package | ✅ Created |
| Access Review | ✅ Created |
 
---
 
## Skills Demonstrated
 
- ✅ MFA Configuration & Registration Policy
- ✅ Conditional Access (4 policies)
- ✅ Identity Protection (User & Sign-in Risk)
- ✅ Privileged Identity Management (PIM)
- ✅ Entitlement Management (Access Packages)
- ✅ Access Reviews
- ✅ Emergency Access (Break-Glass) Strategy
- ✅ Intune Device Compliance Integration
---
 
## Repository
 
**GitHub:** `entra-id-identity-governance-lab`
 
**Environment:** Entra ID P2 and Intune Plan 1 trial tenant (details redacted)
 
> Some object names in these screenshots contain "SC300" because I originally planned this lab around that syllabus. I have not taken that exam, and this repository makes no certification claim.
 
