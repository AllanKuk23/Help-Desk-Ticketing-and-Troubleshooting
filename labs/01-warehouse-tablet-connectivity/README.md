# Lab 01 — Warehouse Tablet Connectivity

## 1. Incident Overview
A warehouse tablet could browse public websites but could not reach the internal Inventory Scan application, interrupting receiving operations.

**SysDesks:** INC5981226 · **Priority:** P3 Moderate · **ServiceNow:** INC0010003

![Original simulated incident](screenshots/original-incident.png)

## 2. Tools & Environment
- **SysDesks:** Simulated tablet troubleshooting, requester messaging, and ticket resolution
- **ServiceNow PDI:** Matching incident, assignment, work notes, and resolution documentation
- **Device:** Orchard SlatePad, `NL-TAB-0221` · **Application:** Inventory Scan

## 3. Troubleshooting & Investigation
1. Assigned the SysDesks ticket and created a matching ServiceNow incident.
2. Opened the simulated tablet's Wi-Fi settings and found it connected to **Northline-Guest**.
3. Switched the tablet to **Northline-Corp** which is used for the company's internal network. I retried Inventory Scan synchronization and made connection.

<img src="screenshots/guest-wifi.png" alt="Tablet connected to guest Wi-Fi" width="650">

**ServiceNow — Incident Investigation and Work Notes**

![ServiceNow incident and work notes](screenshots/ServiceNowTicket.png)

## 4. Root Cause & Resolution
The tablet was on guest Wi-Fi, which did not provide access to the internal Inventory Scan service. Connecting to corporate Wi-Fi restored service without removing device management.

## 5. Verification & Results
- Inventory Scan reported **Service online** and synchronized the warehouse catalog.
- Corporate IP: `10.30.22.41`; private DNS and TCP **443** checks passed.
- Managed profile remained present; requester confirmed the application worked.
- **SysDesks incident resolved** with code *Solved Permanently*.

<img src="screenshots/corporate-wifi-app-online.png" alt="Inventory Scan restored on corporate Wi-Fi" width="650">

<img src="screenshots/network-diagnostics.png" alt="Successful application diagnostics" width="650">

<img src="screenshots/requester-confirmation.png" alt="Requester confirmation" width="750">
![ServiceNow resolution documentation](screenshots/ServiceNowResolvedTicket.png)

## 6. Lessons Learned
Public internet access does not guarantee access to private company services. I verified the connected network, tested the affected application, and confirmed the fix with the requester.


