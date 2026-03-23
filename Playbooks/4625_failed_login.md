# Playbook: Failed Login (Event ID 4625)

## 1. Detection
- Alert triggered in Wazuh for a failed login attempt
- Event ID: 4625 (Failed Logon)
- Logs collected from Windows Workstation via Wazuh agent

## 2. Analysis
- Identify source IP address
- Identify target username
- Check Logon Type:
  - 2 → Interactive  
  - 3 → Network  
  - 10 → RDP  
- Correlate with other failed login events (if any)
- Analyze the timeframe of the activity
- Check for successful logins (Event ID 4624)

## 3. Validation
- Determine if the source is internal or external
- Verify if behavior matches normal user activity
- Check if the account is valid or suspicious
- Analyze login attempts outside normal working hours
- Identify possible brute force patterns

## 4. Response
- Block source IP address (if external and confirmed malicious)
- Lock or disable affected account (if necessary)
- Force password reset (preventive measure)
- Notify administrator
- Monitor for further suspicious activity

## 5. Lessons Learned
- Enforce Multi-Factor Authentication (MFA)
- Implement account lockout policies
- Improve Wazuh detection rules
- Monitor login activity more closely

## 6. Notes
- Logs are collected from the workstation using Wazuh
- Authentication is performed against Active Directory (Domain Controller)

## 7. MITRE ATT&CK
- T1110 – Brute Force
