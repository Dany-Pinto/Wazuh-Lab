# Playbook: User Added to Group (Event ID 4728)

## 1. Detection
- Alert triggered in Wazuh for a member added to a security-enabled group
- Event ID: 4728 (A member was added to a security-enabled global group)
- Logs collected from Domain Controller (Active Directory) via Wazuh agent

## 2. Analysis
- Identify the user account that was added to the group
- Identify the group that was modified
- Identify who performed the action (Subject User)
- Check the system where the event occurred (Domain Controller)
- Analyze the timestamp of the activity

## 3. Validation
- Verify if the group membership change is expected
- Verify if there is a request or approval for the action
- Analyze if the activity occurred during normal working hours
- Identify any unusual group membership changes

## 4. Response
- Remove the user from the group (if unauthorized)
- Review the account that performed the action
- Verify if the affected group has privileged access
- Notify administrator
- Monitor for further suspicious activity

## 5. Lessons Learned
- Restrict permissions to modify security groups
- Improve Wazuh detection rules
- Monitor privileged group membership changes

## 6. Notes
- Event ID 4728 is generated on the Domain Controller (Active Directory)
- Logs are collected and analyzed via Wazuh SIEM
- Adding a user to a privileged group may indicate privilege escalation

## 7. MITRE ATT&CK
- T1098 – Account Manipulation (Privilege Escalation)
