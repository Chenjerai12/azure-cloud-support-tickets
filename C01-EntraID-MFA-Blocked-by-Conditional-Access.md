# C01 - Entra ID MFA Blocked by Conditional Access | Sign-in Logs + What-If

**Severity:** P1 | **Service:** Microsoft Entra ID (Azure AD) | **Region:** South Africa North
**User Impact:** User cannot login to Azure Portal / M365 - Conditional Access blocking + MFA required
**Lab Simulation | Docs Reference:** Microsoft Learn - Entra ID Sign-in logs, Conditional Access What-If, Authentication methods

## 1. Issue Summary
User chenjerai@stgafrica.onmicrosoft.com from trusted location (Kimberley office IP 102.132.15.20) blocked when accessing Azure Portal. Error: `AADSTS50005 - User tried to log in to a device from a platform that is currently not supported` OR `Access blocked by Conditional Access policy`.

MFA prompt loops, even though user completed MFA.

Common in SA enterprises with strict CA policies.

## 2. Symptoms
- Sign-in fails in My Sign-Ins
- Error Code: 53003 - Blocked by Conditional Access
- Location: South Africa (outside Named Location)
- Client App: Browser
- User risk: Medium (new location)

## 3. RCA - L2 Triage (Native Tools, No Delete)

**Step 1: Entra ID Sign-in Logs**
Portal: Entra ID > Monitoring > Sign-in logs > Filter user = chenjerai@stgafrica.onmicrosoft.com > Status = Failure
Check: Conditional Access tab > Which policy applied = `CA01-Require-MFA-For-Portal-Outsite-SA-North`

Failure reason: `Failure reason - Other - Conditional Access failure`

**Step 2: What-If Tool**
Entra ID > Conditional Access > What If
- User: chenjerai@stgafrica.onmicrosoft.com
- IP: 102.132.15.20 (Kimberley)
- Cloud App: Microsoft Azure Management
- Result: Policy `CA01` = Block - Conditions not met: Named Location `SA-North-Trusted` missing this IP.

**Step 3: Check Named Locations**
Entra ID > Conditional Access > Named Locations
- `SA-North-Trusted` only has 196.15.220.0/24 (JHB DC) - Missing Kimberley branch.

**Step 4: Authentication Methods**
Entra ID > Users > Authentication methods > User MFA state = Enabled but not registered for Authenticator.

**Root Cause:** Conditional Access policy requires Compliant Device + MFA + Trusted Location, but Named Location not updated for Kimberley branch IP. User also not registered for Authenticator, causing MFA loop.

## 4. Fix - IaC (Do Not Manually Disable CA Policy)

**Fix 1: Add Kimberley IP to Named Location via Microsoft Graph / Bicep (Entra ID as IaC)**

Bicep for Named Location update (via `Microsoft.Graph` extension):

```bicep
// C01 Fix - Add Kimberley Office to Trusted Locations
// Learn doc: Named locations with Microsoft Graph

resource trustedLocation 'Microsoft.Graph/identity/conditionalAccess/namedLocations@1.0' = {
  // Using Bicep for Graph - adds IP range
  name: 'SA-North-Trusted-Kimberley-Addition'
  properties: {
    displayName: 'SA-North-Trusted'
    ipRanges: [
      '196.15.220.0/24'
      '102.132.15.20/32' // Kimberley Office - Fix for C01
    ]
    isTrusted: true
  }
}
