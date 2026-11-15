# A01 - Lab Simulation | RDP Blocked by NSG - South Africa North

**Lab Type:** L2 Support Simulation
**Region:** South Africa North (SA North)
**Primary Tool:** Azure Network Watcher - IP Flow Verify
**Docs Reference:** Microsoft Learn - IP Flow Verify, Effective Security Rules
**Severity:** Simulated P2

## Simulated Scenario
Lab VM `lab-jhb-vm-01` in SA North VNet. RDP from Kimberley office IP 102.132.15.20 to 10.0.1.4:3389 times out. This simulates a common support ticket where customer cannot RDP.

## L2 Triage Steps (Following MS L2 Runbook)

**Step 1 - Check VM health (not NSG delete):**
- Action: Checked Boot Diagnostics > Screenshot shows VM running, OS booted. Rules out host issue.
- Tool: Boot Diagnostics

**Step 2 - Validate network path:**
- Action: Ran Network Watcher > IP Flow Verify
    - Source: 102.132.15.20/32
    - Destination: 10.0.1.4, port 3389, TCP
    - Result: **Denied** by NSG Rule `DenyAllInbound-Custom` Priority 100
- Tool: IP Flow Verify

**Step 3 - Confirm effective rules:**
- Action: Checked Effective Security Rules on NIC
    - Found: Deny rule at priority 100 blocking all inbound. Allow rule missing for office IP.
- Tool: Effective Security Rules

## RCA (Root Cause Analysis)
Lab created with overly broad Deny rule (Priority 100) during testing. No specific Allow for legitimate office IP. This matches real ticket pattern where test rules left in prod NSG.

## Fix - Bicep (Not Manual Portal Delete)

```bicep
// Fix: Add specific Allow with higher priority, keep audit trail
resource allowRdpRule 'Microsoft.Network/networkSecurityGroups/securityRules@2023-09-01' = {
  name: 'lab-nsg-01/Allow-RDP-Kimberley-Office'
  properties: {
    priority: 110
    access: 'Allow'
    direction: 'Inbound'
    protocol: 'Tcp'
    sourceAddressPrefix: '102.132.15.20/32'
    destinationAddressPrefix: '10.0.1.4/32'
    destinationPortRange: '3389'
    description: 'L2 Fix A01 - Allow RDP from Kimberley office'
  }
}
