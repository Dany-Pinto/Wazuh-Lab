# Wazuh Detection Lab – Active Directory Environment

Practical SIEM lab built using **Wazuh** to simulate real-world **SOC monitoring in an Active Directory environment**.

---

# Why I Built This Lab

After studying security monitoring and detection engineering, I wanted to apply these concepts in a **realistic environment instead of only theoretical learning**.

This lab demonstrates my ability to:

- Deploy and configure a **SIEM (Wazuh)**
- Collect and analyze **Windows Security logs**
- Simulate **attacker behavior**
- Create **custom detection rules**
- Investigate alerts using a **SOC investigation workflow**

---

# Lab Environment

The lab environment includes:

- **Windows Server** (Domain Controller)
- **Windows 10** (Domain-joined endpoint)
- **Wazuh OVA** (Manager + OpenSearch + Dashboard)

Agents communicate internally using **TLS on port 1514**.

**PowerShell Script Block Logging** was enabled to provide deeper visibility into PowerShell activity.

---

# Lab Architecture

The diagram below shows how security events are collected and processed by Wazuh.

![Lab Architecture](/Screenshots/Agents/01_lab_architecture.png)

---

# Simulated Security Events

The following Windows Security events were generated and analyzed during the lab:

- **4720** – User account creation *(possible persistence)*
- **4728** – User added to Domain Admins *(privilege escalation)*
- **4625** – Failed authentication attempts *(brute force - MITRE T1110)*
- **4104** – PowerShell execution *(Process Discovery – MITRE T1057)*

These events simulate different stages of a potential attack in an Active Directory environment.

---

## MITRE ATT&CK Mapping

| Event ID | Detection | MITRE Technique |
|---------|----------|----------------|
4625 | Failed logon attempts | T1110 – Brute Force |
4720 | User account creation | T1136 – Create Account |
4728 | Added to Domain Admins | T1098 – Account Manipulation |
4104 | PowerShell execution | T1057 – Process Discovery |

---

# Custom Detection – Brute Force (Rule ID 110200)

A custom **Wazuh correlation rule** was created to detect brute force attempts.

**Detection logic**

- 5 failed logons (**Event ID 4625**)
- Occurring within **60 seconds**
- Severity **level 10**

Mapped to **MITRE ATT&CK – T1110 (Brute Force)**.

This detection allows early identification of suspicious authentication activity **before an attacker successfully logs in**.

---

# Investigation Approach

For each alert generated in Wazuh, the following SOC investigation workflow was used:

1. Identify the **actor (subject)**
2. Identify the **affected account or group**
3. Assess potential **risk and impact**
4. Correlate related events
5. Validate legitimacy of the activity
6. Recommend **containment or mitigation**

---

# Evidence

Screenshots from the lab environment are available in the **`screenshots`** directory and include:

- Wazuh agents connected to the manager
- Windows Event Viewer logs
- Wazuh alerts generated from simulated activity
- Evidence of the brute force detection rule

---

# Custom Rules

Custom Wazuh detection rules used in this lab are available in the **`rules`** directory.

---

# SOC Playbooks

This lab includes SOC playbooks created based on the investigation of security events:

- [Failed Login (4625)](Playbooks/4625_failed_login.md)
- [Account Creation (4720)](Playbooks/4720_account_creation.md)
- [Group Addition (4728)](Playbooks/4728_group_addition.md)

---

# Next Steps

Future improvements planned for this lab:

- Expand detection coverage for additional security events
- Improve alert tuning to reduce false positives
- Test **Wazuh Active Response capabilities**
