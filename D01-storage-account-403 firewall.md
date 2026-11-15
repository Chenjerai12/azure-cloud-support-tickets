# D01 - Storage Account 403 - Firewall Block - SA North

**Service:** Azure Storage Account | **Region:** South Africa North
**Error:** 403 - This request is not authorized to perform this operation
**Severity:** Sev 2 | **Impact:** App Service cannot read blobs - Customer app down

### 1. Triage & RCA (L2 Tools)

**Step 1 - Check Storage Logs:**
Azure Portal > Storage Account (stappkby001) > Monitoring > Logs
- Request failed with `AuthorizationFailure` + `403`
- Source IP: `196.15.102.45` (App Service Outbound IP - JHB)
- Operation: `GetBlob`

**Step 2 - Check Networking:**
Portal > Storage > Networking > Firewalls and virtual networks
- Public network access: `Enabled from selected virtual networks and IP addresses`
- Allowed IPs: `102.132.15.20/32` (Office IP only)
- App Service subnet NOT whitelisted
- App Service IP `196.15.102.45` NOT in allowlist -> 403 expected

**Step 3 - Check Diagnostic Settings:**
Storage > Activity Log > `AddNetworkRule` 2 days ago by `admin@client.co.za`
- Someone locked down storage to office only, forgot app

**Root Cause:** Firewall allowlist too restrictive - App Service outbound IP not allowed after hardening.

### 2. Fix (Do NOT disable firewall)

**Bad L1 Fix:** Set Public access = Enabled from all networks (Insecure)

**Good L2 Fix:** Whitelist App Service via Bicep (IaC)

```bicep
param storageAccountName string = 'stappkby001'
param appServiceOutboundIp string = '196.15.102.45'
param officeIp string = '102.132.15.20'

resource stg 'Microsoft.Storage/storageAccounts@2023-01-01' existing = {
  name: storageAccountName
}

resource firewall 'Microsoft.Storage/storageAccounts@2023-01-01' = {
  name: storageAccountName
  location: 'southafricanorth'
  properties: {
    networkAcls: {
      defaultAction: 'Deny'
      bypass: 'AzureServices'
      ipRules: [
        {
          value: officeIp
          action: 'Allow'
        }
        {
          value: appServiceOutboundIp
          action: 'Allow'
        }
      ]
      virtualNetworkRules: [
        {
          id: '/subscriptions/xxx/resourceGroups/rg-app-jhb/providers/Microsoft.Network/virtualNetworks/vnet-app-prod/subnets/snet-app'
          action: 'Allow'
        }
      ]
    }
  }
}
