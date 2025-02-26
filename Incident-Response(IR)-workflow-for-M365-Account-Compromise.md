# **Microsoft 365 Account Compromise Incident Response Workflow**

## **1. Introduction** 🎯🔐🔥
This playbook provides a structured **Incident Response (IR) workflow** for handling **Microsoft 365 (M365) account compromises**. It integrates **M365, Entra ID (Azure AD), and endpoint security**, ensuring a **comprehensive response to identity-based breaches**.

## **2. Incident Response Lifecycle**

### **2.1 Preparation** 🛠️✅💡
- **Enable Security Logging:** Ensure auditing/logging for M365, Azure AD, and endpoint security tools (Defender, Sentinel, SIEM).
- **MFA Enforcement:** Require **Multi-Factor Authentication (MFA)** for all users.
- **Conditional Access Policies:** Restrict access based on location, risk level, and device compliance.
- **User Awareness Training:** Educate employees on phishing, MFA fatigue, and suspicious activity reporting.
- **Incident Response Team (IRT):** Define roles for SOC analysts, IT admins, and security engineers.

---

### **2.2 Detection & Identification** 🔍🚨🛑
#### **Common Indicators of Compromise (IoCs):**
- **Unauthorized Logins:** Unusual sign-ins from new locations, devices, or Tor networks.
- **Impossible Travel Alerts:** Logins from geographically impossible locations.
- **MFA Fatigue Attacks:** Excessive MFA requests, indicating MFA bombing.
- **Mailbox Forwarding Rules:** Suspicious email auto-forwarding to external addresses.
- **OAuth App Abuse:** Unauthorized third-party applications with high permissions.
- **Privileged Account Modification:** Unauthorized role elevation in Azure AD.
- **Endpoint Compromise:** Lateral movement detected via Defender logs.

#### **Detection Steps:**
1. **Check Microsoft Defender for Identity/Sentinel:** Look for alerts on abnormal logins, token theft, or privilege escalation.
2. **Review Azure AD Sign-in Logs:** Identify risky sign-ins, MFA failures, and unknown devices.
3. **Inspect M365 Audit Logs:** Detect email rule modifications, data access events, and file sharing changes.
4. **Analyze Endpoint Security Alerts:** Look for suspicious processes, persistence mechanisms, and unauthorized access attempts.

---

### **2.3 Containment** 🛡️🚫🔒
#### **Short-Term Actions:**
- **Disable Compromised Accounts:** Immediately disable affected M365/Azure AD accounts.
- **Force Password Reset:** Reset credentials and revoke active sessions.
- **Block Malicious IPs:** Restrict access from flagged IPs in Conditional Access.
- **Revoke OAuth App Consents:** Remove unauthorized app permissions in **Azure Enterprise Apps**.
- **Disconnect Infected Endpoints:** Isolate endpoints showing signs of compromise.

#### **Long-Term Actions:**
- **Enable Risk-Based Conditional Access:** Restrict access for high-risk users automatically.
- **Reconfigure MFA Enforcement:** Require MFA for all privileged accounts.
- **Monitor for Residual Access:** Verify no persistence methods remain (PowerShell logs, token hijacking, etc.).

---

### **2.4 Eradication** 🧹🛠️🔄
- **Investigate Root Cause:** Analyze logs to determine how credentials were compromised (phishing, password spraying, MFA bypass).
- **Check for Lateral Movement:** Review endpoint telemetry and Defender alerts.
- **Remove Malicious Email Rules:** Reverse unauthorized forwarding rules.
- **Rebuild Affected Endpoints:** If persistence is found, reimage compromised devices.

---

### **2.5 Recovery** 🔄✅🔍
- **Restore Affected Systems:** Recover M365 services if downtime occurred.
- **Validate Security Posture:** Test security configurations (MFA, Conditional Access, logging).
- **Educate Affected Users:** Provide guidance on security best practices.
- **Monitor for Re-Infection:** Enable heightened monitoring for at least 72 hours.

---

### **2.6 Lessons Learned** 📖📊📌
- Conduct a **post-incident review** within 48-72 hours.
- Identify and address **gaps in detection, response, and containment**.
- Update **IR playbooks, SIEM detection rules, and security policies**.
- **Train staff** on new security measures to prevent recurrence.

## **3. Attack Scenarios & Response Actions**
### **3.1 Unauthorized Access (Credential Theft)** 🔑🕵️‍♂️
- **Signs:** Risky sign-ins, unusual MFA prompts, impossible travel alerts.
- **Response:** Force logout, reset password, enforce stronger MFA.

### **3.2 Business Email Compromise (BEC)** ✉️🔓
- **Signs:** Email auto-forwarding rules, phishing emails from a user’s account.
- **Response:** Remove malicious rules, reset credentials, notify affected recipients.

### **3.3 MFA Bypass (Phishing Attack)** 🎭🔑
- **Signs:** MFA fatigue attacks, users approving unexpected prompts.
- **Response:** Reset MFA settings, re-enforce phishing-resistant MFA (e.g., FIDO2).

### **3.4 Privileged Account Takeover** 👑🚨
- **Signs:** Unauthorized admin role assignments, security settings changes.
- **Response:** Revoke access, enforce Just-In-Time (JIT) privileged access.

### **3.5 Malicious OAuth App Consent** 📎🔓
- **Signs:** Unknown applications granted high permissions in M365.
- **Response:** Remove app access, investigate OAuth attack path.

## **4. Conclusion** 🎯💡🔚
This playbook ensures **rapid detection, containment, and mitigation** of compromised M365 accounts, integrating **Azure AD, M365 Security, and Endpoint protection**. Regular updates, security awareness, and strong authentication mechanisms are key to minimizing risk.

