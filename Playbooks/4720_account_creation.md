# Playbook: Account Creation (Event ID 4720)

## 1. Detection
- Alert triggered in Wazuh for a new user account creation  
- Event ID: 4720 (A user account was created)  
- Logs collected from Domain Controller (Active Directory) via Wazuh agent  

## 2. Analysis
- Identify the account that was created (Target User)  
- Identify who created the account (Subject User)  
- Check the system where the event occurred (Domain Controller)  
- Analyze the timestamp of the activity  

## 3. Validation
- Verify if the account creation is expected  
- Verify if there is a request or approval for the account creation  
- Analyze if the activity occurred during normal working hours  
- Identify any unusual account creation patterns  

## 4. Response
- Disable or remove the created account (if unauthorized)  
- Review the account that created the user  
- Reset credentials if necessary  
- Notify administrator  
- Monitor for further suspicious activity  

## 5. Lessons Learned
- Restrict account creation permissions  
- Improve Wazuh detection rules  
- Monitor account creation activity  

## 6. Notes
- Event ID 4720 is generated on the Domain Controller (Active Directory)  
- Logs are collected and analyzed via Wazuh SIEM  

## 7. MITRE ATT&CK
- T1136 – Create Account (Persistence)
