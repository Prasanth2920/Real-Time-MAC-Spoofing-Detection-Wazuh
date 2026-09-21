# Real-Time MAC Address Spoofing Detection Using Wazuh SIEM

## 📌 Project Overview

This project presents a **Real-Time MAC Address Spoofing Detection and Response System** using **Wazuh SIEM**.

A custom Python monitoring script continuously monitors the MAC address of a Linux network interface. When an unauthorized MAC address change is detected, the system generates a structured JSON event and forwards it to the Wazuh Manager through the Wazuh Agent.

Wazuh analyzes the event using custom detection rules, generates a security alert, maps the event to the **MITRE ATT&CK Framework**, updates the Wazuh Dashboard, sends an email notification, and supports automated Active Response.

---

## 🎯 Objectives

* Monitor MAC address changes in real time
* Detect unauthorized MAC address spoofing attempts
* Integrate MAC monitoring with Wazuh SIEM
* Generate custom security alerts
* Map detected events to MITRE ATT&CK
* Implement automated Active Response
* Send real-time email notifications
* Visualize security events using the Wazuh Dashboard

---

## 🛠️ Technologies Used

| Technology           | Purpose                                  |
| -------------------- | ---------------------------------------- |
| Wazuh SIEM 4.14.7    | Security monitoring and alert generation |
| Ubuntu 24.04         | Wazuh Server                             |
| Kali Linux           | Monitored endpoint                       |
| Python 3             | MAC address monitoring                   |
| Bash                 | Active Response                          |
| macchanger           | MAC address modification/testing         |
| Postfix              | Email notifications                      |
| OpenSearch Dashboard | Security event visualization             |
| MITRE ATT&CK         | Attack technique mapping                 |

---

## 🏗️ System Architecture

```text
                Kali Linux
                    │
                    ▼
        Python MAC Monitoring Script
                    │
                    ▼
           MAC Address Change
                    │
                    ▼
              Wazuh Agent
                    │
                    ▼
             Wazuh Manager
                    │
          ┌─────────┼─────────┐
          │         │         │
          ▼         ▼         ▼
       Custom     MITRE    Security
        Rule      ATT&CK     Alert
          │
          ├──────────────► Wazuh Dashboard
          │
          ├──────────────► Email Notification
          │
          └──────────────► Active Response
```

---

## ⚙️ Project Workflow

1. The Python script reads the current MAC address.
2. The current MAC address is compared with the previously stored MAC address.
3. A MAC address change is detected.
4. System and network information are collected.
5. A structured JSON event is generated.
6. The Wazuh Agent forwards the event to the Wazuh Manager.
7. Custom Wazuh detection rules analyze the event.
8. A security alert is generated.
9. The event is mapped to MITRE ATT&CK.
10. The alert is displayed on the Wazuh Dashboard.
11. An email notification is sent.
12. Active Response can be executed.

---

## 🔍 Information Collected

The monitoring script collects the following information when a MAC address change is detected:

* Old MAC Address
* New MAC Address
* Permanent MAC Address
* IP Address
* Default Gateway
* DNS Server
* Hostname
* Timestamp
* Vendor Information
* Randomized Status
* Change Count

---

## 🚨 Wazuh Detection Rule

A custom Wazuh rule was created to detect MAC address modification events.

```text
Rule ID: 100510
Alert Type: MAC_INVESTIGATION
Severity: High
```

The rule detects MAC address modification events and provides MITRE ATT&CK mapping for additional security context.

---

## 📧 Email Notification

Postfix is configured to send an email notification whenever a MAC address change is detected.

The notification contains:

* Timestamp
* Hostname
* Network Interface
* Old MAC Address
* New MAC Address
* Alert Level

---

## 🛡️ Active Response

The project includes Wazuh Active Response functionality.

When a MAC spoofing event is detected, the Active Response script records the incident and can optionally perform additional response actions, including restoring the original MAC address.

---

## 🧪 Testing & Validation

The system was tested by intentionally changing the MAC address using the `macchanger` utility.

### Test Procedure

```text
Start Monitoring
       ↓
Change MAC Address
       ↓
Generate JSON Event
       ↓
Wazuh Agent
       ↓
Wazuh Manager
       ↓
Custom Detection Rule
       ↓
Security Alert
       ↓
Dashboard + Email Alert
       ↓
Active Response
```

### Expected Result

The system successfully detects the MAC address change, generates an investigation event, creates a Wazuh security alert, displays the event on the dashboard, sends an email notification, and supports Active Response.

---

## 📂 Repository Structure

```text
Real-Time-MAC-Spoofing-Detection-Wazuh/
│
├── README.md
│
├── Documentation/
│   └── Final_Report.pdf
│
├── Python/
│   └── mac_monitor.py
│
├── Wazuh/
│   ├── custom_rules.xml
│   ├── active-response.sh
│   └── ossec.conf
│
└── Screenshots/
    │
    ├── 01_MAC_Change_Detection/
    │   ├── 01_MAC_Address_Before_Change.png
    │   ├── 02_MAC_Address_Changed.png
    │   └── 03_MAC_Address_After_Change.png
    │
    ├── 02_Python_Monitoring/
    │   ├── 04_MAC_Monitoring_Script.png
    │   └── 05_MAC_Investigation_JSON.png
    │
    ├── 03_Wazuh/
    │   ├── 06_Wazuh_Agent_Status.png
    │   ├── 07_Wazuh_Manager_Status.png
    │   ├── 08_Wazuh_Custom_Rule.png
    │   └── 09_Wazuh_Security_Alert.png
    │
    ├── 04_Dashboard/
    │   ├── 10_Wazuh_Dashboard_Alert.png
    │   └── 11_MAC_Spoofing_Dashboard.png
    │
    ├── 05_Email_Alert/
    │   └── 12_Email_Alert_Received.png
    │
    └── 06_Active_Response/
        ├── 13_Active_Response_Executed.png
        └── 14_Investigation_Report.png
```

---

## 📸 Project Evidence

The `Screenshots` folder contains evidence of:

* MAC address modification
* Python monitoring
* JSON event generation
* Wazuh Agent and Manager
* Custom detection rule
* Wazuh security alerts
* Dashboard visualization
* Email notifications
* Active Response
* Testing and validation

---

## 🎓 Key Learning Outcomes

Through this project, the following practical cybersecurity concepts were demonstrated:

* SIEM implementation
* Linux security monitoring
* Network security
* MAC address spoofing detection
* Python security automation
* Log collection and analysis
* Custom Wazuh detection rules
* MITRE ATT&CK mapping
* Security alerting
* Automated incident response
* Email-based security notifications
* Security dashboard monitoring

---

## 🔮 Future Enhancements

Future versions of the project can include:

* Monitoring multiple network interfaces
* Historical MAC address storage
* Threat intelligence integration
* Web-based investigation dashboard
* Windows and macOS endpoint support
* Slack or Microsoft Teams notifications
* Machine learning-based anomaly detection
* Automated forensic investigation reports

---

## 👨‍💻 Author

**Prasanth**

**Cybersecurity Fresher | Cybersecurity | SOC | Penetration Testing | Network Security**

---

## 📚 References

* Wazuh Documentation
* MITRE ATT&CK Framework
* Kali Linux Documentation
* Ubuntu Documentation
* Python Documentation
* macchanger Manual
* Postfix Documentation
* OpenSearch Dashboards Documentation
* NIST Cybersecurity Framework

