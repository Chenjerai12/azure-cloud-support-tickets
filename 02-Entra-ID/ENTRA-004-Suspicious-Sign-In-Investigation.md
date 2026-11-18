# ENTRA-004: Suspicious Sign-in Investigation

## Project Information

- **Ticket ID:** ENTRA-004
- **Module:** Microsoft Entra ID
- **Category:** Identity and Access Management / Security
- **Priority:** High
- **Status:** Resolved
- **Environment:** Simulated Microsoft 365 environment

## 1. Incident Summary

An employee reported receiving an unexpected Microsoft Authenticator approval request and a security notification about a sign-in from an unfamiliar location.

The employee did not recognise the activity and confirmed that they had not travelled.

The investigation was initiated to establish whether the employee's account had been compromised.

## 2. Initial Investigation

Reviewed Microsoft Entra sign-in logs.

Findings:

- Unfamiliar sign-in location: Bucharest, Romania.
- Employee's normal location: Johannesburg, South Africa.
- Unrecognised Windows device.
- Unfamiliar IP address.
- Successful Microsoft 365 sign-in.
- High sign-in risk.
- Conditional Access policy applied.

The employee confirmed that the device and activity were unfamiliar.

## 3. Authentication Investigation

Inspected authentication details.

Findings:

- Password authentication successful.
- MFA requirement satisfied.
- Microsoft Authenticator used.
- Unrecognised Authenticator device.
- Additional authentication method registered earlier that day.

The employee confirmed that the additional device had not been registered by them.

## 4. Security Escalation

Escalated the incident to the security team.

Preserved the sign-in evidence and followed the approved incident-response procedure.

The security team classified the incident as a suspected account compromise and authorised containment.

## 5. Account Containment

Following security-team authorisation:

- Temporarily blocked account sign-in.
- Revoked active sessions.
- Confirmed the account remained blocked during investigation.

These actions helped prevent further access while the incident was investigated.

## 6. Authentication Methods Review

Reviewed the employee's registered authentication methods.

Findings:

- Original Microsoft Authenticator: Recognised.
- Additional Microsoft Authenticator: Unrecognised.
- Registered mobile number: Recognised.
- FIDO2 security key: Not registered.

The security team authorised removal of the unauthorised Authenticator registration.

Only the unauthorised method was removed. Legitimate authentication methods were preserved.

## 7. Account Recovery

After the security team completed its initial investigation and authorised recovery:

1. Verified the employee's identity.
2. Reset the account password.
3. Confirmed legitimate authentication methods.
4. Confirmed removal of the unauthorised method.
5. Removed the sign-in restriction following security approval.
6. Required fresh authentication.

## 8. Final Verification

Confirmed:

- Successful Microsoft Entra sign-in.
- Successful MFA authentication.
- Conditional Access passed.
- Outlook access restored.
- Microsoft Teams access restored.
- Employee confirmed successful access.

The security team continued monitoring the account.

## 9. Final Resolution

The suspected compromised account was successfully contained and recovered.

The unauthorised authentication method was removed, the password was reset, and access was restored after security approval and verification.

**Ticket status: Resolved.**

## 10. Skills Demonstrated

- Microsoft Entra ID user administration.
- Sign-in log investigation.
- Authentication and MFA troubleshooting.
- Risky sign-in investigation.
- Session revocation.
- Account sign-in restrictions.
- Authentication method management.
- Identity incident escalation.
- Secure account recovery.
- Incident documentation.

## Environment Disclaimer

This is a simulated Microsoft 365 administration training exercise. No production tenant, real employee account, or customer information was accessed.
