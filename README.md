# L2 Azure Cloud Support Lab - 20+ Tickets | South Africa 

**Location:** Kimberley / Johannesburg | **Focus:** L2 Support Tools: IP Flow Verify, Network Watcher, Entra ID Sign-in Logs, Conditional Access, Boot Diagnostics, Azure Monitor
**Goal:**  L2 Cloud Support Engineer Role

This repo simulates real Azure L2 support tickets with RCA, Bicep fix, and prevention (no delete).

## Ticket Index

### Network / NSG (A)
- **A01 - RDP Blocked by NSG:** IP Flow Verify shows Deny. Fix: Remove restrictive NSG rule, add specific Allow, Resource Lock on NSG.
- **A02 - App Connectivity:** NSG + Effective Security Rules triage.
- **A03 - Effective Routes:** UDR misroute fix.

### Compute / Boot Diagnostics (B)
- **B01 - VM Boot Failed:** Boot Diagnostics screenshot analysis, fix with AZ CLI redeploy.
- **B02 - VM Extension Failed:** Log analysis + Bicep redeploy.

### Identity / Entra ID (C)
- **C01 - Sign-in Logs Blocked:** Entra ID Sign-in Logs show Conditional Access block. Fix: Conditional Access exclusion.
- **C02 - Conditional Access Lockout:** Break-glass account, policy report.
- **C03 - Entra ID Sync Issue:** Entra Connect Health logs.

### Monitoring / Cost (D)
- **D01 - Azure Monitor Alert:** KQL query, Action Group, alert suppression.
- **D02 - Cost Alert:** Cost Management anomaly.

## Tools Used
Azure Network Watcher > IP Flow Verify, NSG Flow Logs, Effective Security Rules, Boot Diagnostics, Microsoft Entra ID > Sign-in Logs, Conditional Access, Azure Monitor, Azure CLI, Bicep, Resource Locks

## Prevention Pattern (Every Ticket)
1.  RCA with native tool (not delete)
2.  Fix with Bicep / CLI
3.  Prevention: Resource Lock + Azure Monitor Alert + Documentation

## Profile
LinkedIn: Chenjerai | Systems Technician @ STG Africa | Johannesburg
Target: L2 Azure Support Engineer - Johannesburg / Remote SA

---
*Lab built following Microsoft L2 Support Engineer documentation pattern*
