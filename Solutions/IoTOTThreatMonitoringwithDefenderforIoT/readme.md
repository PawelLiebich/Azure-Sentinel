# Overview
There has been a long-standing split between SCADA (OT) and Corporate (IT) cybersecurity. This split was often driven by significant differences in technology/tooling. Microsoft Defender for IoT's integration with Azure Sentinel drives convergency by providing a single pane for coverage of both D4IOT (OT) and Azure Sentinel (IT) alerting. This solution includes (1) Workbook, (14) Analytics rules, and (4) Playbooks providing a guide OT/IoT Detection, Analysis, and Response. This solution augments staffing through automation, artificial intelligence, machine learning, query/alerting generation and visualizations.<br>

# Getting Started
1)  [Onboard Azure Defender for IoT](https://docs.microsoft.com/azure/defender-for-iot/device-builders/quickstart-onboard-iot-hub)<br>
2)  [Onboard Azure Sentinel](https://docs.microsoft.com/azure/sentinel/quickstart-onboard)<br> 
3)  [Enable Azure Defender for IoT Connector to Azure Sentinel](https://docs.microsoft.com/azure/defender-for-iot/organizations/how-to-configure-with-sentinel)<br>
4)  View the Workbook: Navigate to Azure Sentinel > Workbooks > My Workbooks > IoT/OT Threat Monitoring with Defender for IoT > View<br>
5)  View the Analytics Rules: Navigate to Azure Sentinel > Analytics > Search "IOT"<br>
6)  View the Playbooks: Navigate to Azure Sentinel> Automation > Playbooks > Search "IOT"<br>

# Workbook
The IoT/OT Threat Monitoring with Defender for IoT Workbook features IoT/OT filtering for Security Alerts, Incidents, and Asset Inventory. The workbook features a dynamic assessment of the MITRE ATT&CK for ICS matrix across your environment to analyze and respond to IoT/OT-based threats. This workbook is designed to enable SecOps Analysts, Security Engineers, and MSSPs to gain situational awareness for IT/OT security posture. This workbook augments staffing through automation, artificial intelligence, machine learning, query/alerting generation and visualizations.<br>

# Analytics Rules
## 1) Denial of Service (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect attacks that would prevent the use or proper operation of a DCS system including Denial of Service events.<br>
## 2) Excessive Login Attempts (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect excessive login attempts that may indicate improper service configuration, human error, or malicious activity on the network such as a cyber threat attempting to manipulate the SCADA network.<br>
## 3) Firmware Updates (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect unauthorized firmware updates that may indicate malicious activity on the network such as a cyber threat that attempts to manipulate PLC firmware to compromise PLC function.<br>
## 4) High Bandwidth (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect an unusually high bandwidth which may be an indication of a new service/process or malicious activity on the network. An example scenario is a cyber threat attempting to manipulate the SCADA network.<br>
## 5) Illegal Function Codes (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect Illegal function codes in SCADA equipment indicating improper application configuration or malicious activity such using illegal values within a protocol to exploit a PLC vulnerability.<br>
## 6) Insecure PLC (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect PLC operating mode changes indicating the PLC is potentially insecure. If the PLC is compromised, devices that interact with it may be impacted. This may affect overall system security and safety.<br>
## 7) Internet Access (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect an OT device communicating with Internet which is possibly an indication of improper configuration of an application or malicious activity on the network.<br>
## 8) Malware (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect IoT/OT malware found on the network indicating possible attempts to compromise production systems.<br>
## 9) Network Scanning (Microsoft Defender for IoT)
his alert leverages Microsoft Defender for IoT to detect multiple scans on the network indicating new devices, functionality, application misconfiguration, or malicious reconnaissance activity on the network.<br>
## 10) PLC Stop Command (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect PLC stop commands which could indicate improper configuration or malicious activity on the network such as a threat manipulating PLC programming to affect the function of the network.<br>
## 11) Unauthorized Network Device (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect a new device indicating a legitimate device recently installed on the network or an indication of malicious activity such as a cyber threat attempting to manipulate the SCADA network.<br>
## 12) Unauthorized Network Configuration (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect an unauthorized DHCP configuration indicating a possible unauthorized device configuration.<br>
## 13) Unauthorized PLC Modifications (Microsoft Defender for IoT)
 This alert leverages Microsoft Defender for IoT to detect unauthorized changes to PLC ladder logic code indicating new functionality in the PLC, improper configuration of an application, or malicious activity on the network.<br>
## 14) Unauthorized Remote Access (Microsoft Defender for IoT)
This alert leverages Microsoft Defender for IoT to detect unauthorized remote access to network devices, if another device on the network is compromised, target devices can be accessed remotely, increasing the attack surface.<br>

# Playbooks
## 1) AutoCloseIncidents
In some cases, maintenance activities generate alerts in Sentinel which distracts the SOC team from handling the real problems, the playbook allows to input the time period in which the maintenance is expected and the assets IP (Excel file can be found). The playbook requires a watchlist which includes all the IP addresses of the assets on which alerts will handled automatically. This playbook parses explicitly the IOT device entity fields. For more information, see [AD4IoT-AutoCloseIncidents](https://github.com/Azure/Azure-Sentinel/tree/master/Playbooks/AD4IoT-AutoCloseIncidents)<br>
## 2) MailbyProductionLine
The following playbook will send mail to notify specific stake holders. One example can be in the case of specific security team per product line or per physical location. The playbook requires a watchlist which maps between the sensors name and the mail addresses of the alerts stockholders. For more information, see [AD4IoT-MailbyProductionLine](https://github.com/Azure/Azure-Sentinel/tree/master/Playbooks/AD4IoT-MailbyProductionLine)<br>
## 3) NewAssetServiceNowTicket
Normally, the authorized entity to program a PLC is the Engineering Workstation, to program a PLC attackers might create a new Engineering Workstation to create malicious programing. The following playbook will open a ticket in ServiceNow each time a new Engineering Workstation is detected. This playbook parses explicitly the IOT device entity fields. For more information, see [AD4IoT-NewAssetServiceNowTicket](https://github.com/Azure/Azure-Sentinel/blob/master/Playbooks/AD4IoT-NewAssetServiceNowTicket/readme.md)<br>