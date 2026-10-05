# Entra ID Identity & Access Governance Lab
 
[![Entra ID](https://img.shields.io/badge/Entra%20ID-P2-green)](https://www.microsoft.com/en-us/security/business/identity-access/azure-active-directory-pricing)
[![Intune](https://img.shields.io/badge/Intune-Plan%201-orange)](https://www.microsoft.com/en-us/microsoft-365/enterprise-mobility-security/microsoft-intune)
 
## Overview
 
This repository documents a hands-on identity and access governance lab built in an Entra ID P2 trial tenant with an Intune-enrolled Windows 11 VM. It covers risk-based Conditional Access, Privileged Identity Management (PIM), entitlement management, access reviews and emergency access, and shows how identity controls tie in with device compliance.
 
> **Lab Completed:** July 2026
> **Environment:** Entra ID P2 and Intune Plan 1 trial tenant (tenant details redacted)
 
## What This Lab Demonstrates
 
| Category | Implemented Features |
|----------|---------------------|
| **Conditional Access** | MFA registration, User risk remediation (High risk → password reset), Sign-in risk (Medium/High → MFA), Device compliance enforcement |
| **Identity Protection** | Risk-based policies using Entra ID Protection signals |
| **Privileged Identity Management (PIM)** | Just-in-time Global Administrator access with MFA and justification |
| **Entitlement Management** | Self-service access packages with approval workflows and expiration |
| **Access Reviews** | Automated group membership reviews with auto-apply and removal |
| **Emergency Access** | Break-glass accounts excluded from all Conditional Access policies |
| **Device Management** | Windows 11 VM enrolled in Intune, marked compliant |
 
## Lab Architecture
 
```
┌─────────────────────────────────────────────────────────────────┐
│                    Entra ID P2 Trial Tenant                     │
├─────────────────────────────────────────────────────────────────┤
│  ┌───────────────────────────────────────────────────────────┐ │
│  │              Conditional Access Policies                  │ │
│  │  ┌─────────────────────┐  ┌──────────────────────────┐  │ │
│  │  │ MFA Registration    │  │ Risk-Based Policies       │  │ │
│  │  │ Policy              │  │ (User & Sign-in Risk)    │  │ │
│  │  └─────────────────────┘  └──────────────────────────┘  │ │
│  └───────────────────────────────────────────────────────────┘ │
│  ┌───────────────────────────────────────────────────────────┐ │
│  │              Identity Governance                          │ │
│  │  ┌─────────────────────┐  ┌──────────────────────────┐  │ │
│  │  │ Access Reviews      │  │ Entitlement Management   │  │ │
│  │  │ (Group Membership)  │  │ (Access Packages)        │  │ │
│  │  └─────────────────────┘  └──────────────────────────┘  │ │
│  └───────────────────────────────────────────────────────────┘ │
│  ┌───────────────────────────────────────────────────────────┐ │
│  │              Identity Protection                         │ │
│  │  ┌─────────────────────┐  ┌──────────────────────────┐  │ │
│  │  │ User Risk Policy    │  │ Sign-in Risk Policy      │  │ │
│  │  │ (High Risk =        │  │ (Med/High Risk =         │  │ │
│  │  │  Remediation)       │  │  MFA Required)          │  │ │
│  │  └─────────────────────┘  └──────────────────────────┘  │ │
│  └───────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────┘
```
 
## Lab Environment
 
| Component | Detail |
|-----------|--------|
| **Tenant** | Entra ID P2 trial tenant (name and ID redacted) |
| **Admin Account** | Lab Global Administrator account (redacted) |
| **Licenses** | Entra ID P2 (Trial), Intune Plan 1 (Trial) |
| **Enrolled Device** | Windows 11 VM (Compliant) |
| **Conditional Access Policies** | 4 policies (all active) |
 
## Conditional Access Policies
 
| Policy Name | State | Grant Controls | Conditions |
|-------------|-------|----------------|------------|
| **Require-Compliant-Devices** | ✅ **ON** | Require compliant device, Require hybrid joined device | All users, All resources |
| **Policy-01-Require-MFA-Registration** | ✅ **ON** | Require MFA registration | All users, All resources |
| **Policy-02-User-Risk-Remediation** | ✅ **ON** | Require MFA, Require password change | All users, All resources, User risk: High |
| **Policy-03-Signin-Risk-MFA** | ✅ **ON** | Require MFA | All users, All resources, Sign-in risk: Medium + High |
 
## Emergency Access Configuration
 
| Component | Details |
|-----------|---------|
| **Break-glass Accounts** | Two cloud-only emergency accounts (usernames redacted) |
| **Emergency Group** | Emergency-Access-Admins (both break-glass accounts as members) |
| **Exclusion** | Excluded from ALL Conditional Access policies ✅ |
| **Role** | Global Administrator (both accounts) |
 
## Privileged Identity Management (PIM)
 
| Setting | Value |
|---------|-------|
| **Role** | Global Administrator |
| **Assignment Type** | Eligible (not permanently active) |
| **Activation Duration** | 2 hours |
| **MFA Required** | Yes |
| **Justification Required** | Yes |
| **Approval Required** | No (lab simplified) |
 
## Entitlement Management
 
| Component | Details |
|-----------|---------|
| **Catalog** | Project-SC300-Lab-Catalog |
| **Access Package** | Access-Package-SC300-Lab |
| **Resource** | SC300-Lab-Users (Security Group) |
| **Approval** | Required (lab admin account as approver) |
| **Expiration** | 09/09/2026 |
 
## Access Reviews
 
| Setting | Value |
|---------|-------|
| **Review Name** | Access-Review-SC300-Lab-Users |
| **Resource** | SC300-Lab-Users group |
| **Reviewers** | Group owner(s) |
| **Fallback Reviewers** | Lab admin account |
| **Frequency** | One-time (7 days) |
| **Auto-apply Results** | Enabled |
| **If Reviewers Don't Respond** | Remove access |
 
## Design Decisions
 
- **Break-glass accounts are excluded from every Conditional Access policy** through the Emergency-Access-Admins group, so a misconfigured policy cannot lock all administrators out of the tenant.
- **Global Administrator is eligible, not permanently active.** Activation through PIM requires MFA and a written justification, and expires after 2 hours.
- **PIM approval was left off to keep the lab simple.** In production I would require approval for Global Administrator activation.
- **The access review removes access if reviewers do not respond**, so unreviewed access does not persist by default.
## Repository Structure
 
```
entra-id-identity-governance-lab/
├── README.md                         # This file
├── screenshots/
│   ├── README.md                     # Screenshot index
│   ├── 01-existing-compliant-devices-policy.png
│   ├── 02-licenses-entra-id-p2-intune.png
│   ├── 03-tenant-overview.png
│   ├── ... (54 screenshots total)
│   └── 54-final-all-policies-on.png
├── scripts/
│   ├── Get-ConditionalAccessPolicySummary.ps1
│   └── Invoke-IdentityLabCheck.ps1
└── templates/
    ├── ConditionalAccessPolicies.json
    └── PIMSettings.json
```
 
## Skills Demonstrated
 
- Conditional Access: compliant-device, MFA registration, user-risk and sign-in-risk policies
- Entra ID Identity Protection: risk-based access decisions
- Privileged Identity Management: just-in-time, MFA-protected administrator access
- Entitlement management: catalogs, access packages, approval workflows and expiry
- Access reviews: automated group membership reviews with auto-apply
- Emergency access: break-glass account design and policy exclusions
- Intune device compliance integrated with Conditional Access
- PowerShell and Microsoft Graph: validation script and exported policy templates
## PowerShell Validation Script
 
A validation script is included in `/scripts/Invoke-IdentityLabCheck.ps1` to verify your lab configuration:
 
```powershell
# Connect to Microsoft Graph
Connect-MgGraph -Scopes "Policy.Read.All", "RoleManagement.Read.All"
 
# Run lab validation
.\Invoke-IdentityLabCheck.ps1
```
 
Expected output:
```
=== Identity Lab Validation ===
 
Conditional Access Policies:
  - Require-Compliant-Devices: On
  - Policy-01-Require-MFA-Registration: On
  - Policy-02-User-Risk-Remediation: On
  - Policy-03-Signin-Risk-MFA: On
 
PIM Eligible Assignments:
  - Lab admin account: Global Administrator (Eligible)
 
=== Validation Complete ===
```
 
## Screenshots
 
All lab configuration screenshots are available in the `/screenshots` folder with detailed descriptions in `/screenshots/README.md`.
 
| Key Screenshot | Description |
|----------------|-------------|
| `01-existing-compliant-devices-policy.png` | Existing Conditional Access policy |
| `15-four-ca-policies.png` | All 4 Conditional Access policies |
| `32-pim-active-role.png` | PIM role activated |
| `54-final-all-policies-on.png` | Final state - all policies ON |
 
## How to Replicate This Lab
 
### Prerequisites
 
- Entra ID P2 license (trial available)
- Intune Plan 1 license (trial available)
- Global Administrator access
- Windows 11 VM (optional but recommended)
### Quick Start Steps
 
1. **Review existing configuration** - Document your tenant baseline
2. **Create MFA Registration Policy** - All users must register for MFA
3. **Create User Risk Policy** - High user risk → MFA + password reset
4. **Create Sign-in Risk Policy** - Medium/High sign-in risk → MFA
5. **Create Break-glass Accounts** - Emergency access accounts excluded from all policies
6. **Configure PIM** - Make Global Admin role eligible (not active)
7. **Create Access Package** - Self-service access with approval workflow
8. **Create Access Review** - Scheduled group membership reviews
## Security Considerations
 
| Consideration | Implementation |
|---------------|----------------|
| **Tenant Lockout Prevention** | Break-glass accounts excluded from all policies ✅ |
| **Just-in-Time Admin** | PIM with MFA and justification ✅ |
| **Risk-based Access** | User and sign-in risk policies ✅ |
| **Device Trust** | Intune compliance enforced ✅ |
| **Access Governance** | Access reviews and entitlements ✅ |
 
## Resources
 
- [Microsoft Entra ID Documentation](https://learn.microsoft.com/en-us/entra/identity/)
- [Conditional Access Documentation](https://learn.microsoft.com/en-us/entra/identity/conditional-access/)
- [Privileged Identity Management Documentation](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/)
- [Microsoft Intune Documentation](https://learn.microsoft.com/en-us/mem/intune/)
## Important Notes
 
> **License Warning:** This lab was built using trial licenses. After the trial period expires, some features may be disabled.
 
> **Guest User Billing:** Beginning January 15, 2026, a linked Azure subscription is required to use Entra ID Governance features for guest users. This lab does not include guest users, so billing is not impacted.
 
> **Break-glass Accounts:** Store break-glass account passwords securely offline. They are critical for tenant recovery.
 
> **Object Names:** Some object names in the tenant and screenshots contain "SC300" because I originally planned this lab around that syllabus. I have not taken that exam, and this repository makes no certification claim.
 
## License
 
This project is for educational purposes, built on trial licenses. All Microsoft screenshots are property of Microsoft Corporation.
 
## Author
 
**Hlulani Chavalala** — [GitHub](https://github.com/Hlulaniheis)
 
