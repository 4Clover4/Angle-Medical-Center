# Network Documentation

## 1. Network Overview

This network documentation outlines the IT infrastructure setup for Angle Hospital. The focus is on creating a reliable, secure, and efficient network environment to support critical hospital operations, patient data security, and seamless communication between departments.

### Objectives:
- Provide reliable connectivity for critical hospital systems.
- Ensure network redundancy and high availability.
- Implement secure protocols and data protection mechanisms.

---

## 2. Topologies

### Network Logical Relationships:
- The network connects to the internet via a cloud at the top of the topology.
- Multiple routers manage inter-VLAN routing and subnet connectivity.
- Switches aggregate wired connections from LAN devices and provide VLAN segmentation.
- Wireless routers/APs support guest and internal device connectivity.

##Logical Topology:

![image](https://github.com/user-attachments/assets/e81e0f05-41ba-4183-a518-8740bb343b54)

##Physical Topology:

![image](https://github.com/user-attachments/assets/644b662c-bfcd-4445-8ef8-b7e7f8030a6e)


# Network Documentation

## 3. IP Addressing Schema Information

### Etherchannel and Trunk Implementation

| **Network Devices** | **Trunk Port**       | **Etherchannel**        |
|----------------------|----------------------|-------------------------|
| MLS-1               | Port-channel 2       | Fa0/1, Fa0/2            |
|                      | F0/5                |                         |
|                      | F0/7                |                         |
| MLS-2               | Port-channel 3       | Fa0/3, Fa0/4            |
|                      | F0/6                |                         |
|                      | F0/8                |                         |
| S-1                 | Port-channel 2       | Fa0/1, Fa0/2            |
|                      | Port-channel 3       | Fa0/3, Fa0/4            |
| S-2                 | F0/5                 |                         |
|                      | F0/6                |                         |
| S-3                 | F0/7                 |                         |
|                      | F0/8                |                         |

### IP Address Table

| **Network Device** | **Model**              | **Interfaces**  | **IP Address**       | **Subnet Mask**    | **MAC Address**       |
|--------------------|------------------------|-----------------|----------------------|-------------------|-----------------------|
| R1                 | Cisco 2900             | Gig0/1          | 10.128.250.230       | 255.255.255.0     | 00D0.58D9.0102        |
|                     |                        | Gig0/0          | 192.168.1.3          | 255.255.255.0     | 00D0.58D9.0101        |
| R2                 | Cisco 2900             | Gig0/1          | 10.128.250.232       | 255.255.255.0     | 0006.2A9D.3E02        |
|                     |                        | Gig0/0          | 192.168.1.1          | 255.255.255.0     | 0101.9687.7418        |
| MLS-1              | Cisco Catalyst 3560 v2 | Fa0/23          | 192.168.3.1          | 255.255.255.0     | 0001.C7D0.5117        |
|                     |                        | Fa0/24          | 192.168.1.1          | 255.255.255.0     | 0001.C7D0.5118        |
|                     |                        | VLAN 10         | 192.168.10.1         | 255.255.255.0     | 00D0.9776.4401        |
|                     |                        | VLAN 20         | 192.168.20.1         | 255.255.255.0     | 0012.4AD6.3B01        |
|                     |                        | VLAN 30         | 192.168.30.1         | 255.255.255.0     | 00D0.9776.4403        |
|                     |                        | VLAN 40         | 192.168.40.1         | 255.255.255.0     | 00D0.9776.4404        |
|                     |                        | VLAN 50         | 192.168.50.1         | 255.255.255.0     | 00D0.9776.4405        |
|                     |                        | VLAN 60         | 192.168.60.1         | 255.255.255.0     | 00D0.9776.4406        |
|                     |                        | VLAN 70         | 192.168.70.1         | 255.255.255.0     | 00D0.9776.4407        |
|                     |                        | VLAN 80         | 192.168.80.1         | 255.255.255.0     | 00D0.9776.4408        |
|                     |                        | VLAN 90         | 192.168.90.1         | 255.255.255.0     | 00D0.9776.4409        |
|                     |                        | VLAN 100        | 192.168.100.1        | 255.255.255.0     | 00D0.9776.440A        |
| MLS-2              | Cisco Catalyst 3560 v2 | Fa0/23          | 192.168.3.3          | 255.255.255.0     | 0001.9687.7417        |
|                     |                        | Fa0/24          | 192.168.2.1          | 255.255.255.0     | 0001.9687.7418        |
|                     |                        | VLAN 10         | 192.168.10.2         | 255.255.255.0     | 0012.4AD6.3B01        |
|                     |                        | VLAN 20         | 192.168.20.2         | 255.255.255.0     | 0012.4AD6.3B02        |
|                     |                        | VLAN 30         | 192.168.30.2         | 255.255.255.0     | 0012.4AD6.3B03        |
|                     |                        | VLAN 40         | 192.168.40.2         | 255.255.255.0     | 0012.4AD6.3B04        |
|                     |                        | VLAN 50         | 192.168.50.2         | 255.255.255.0     | 0012.4AD6.3B05        |
|                     |                        | VLAN 60         | 192.168.60.2         | 255.255.255.0     | 0012.4AD6.3B06        |
|                     |                        | VLAN 70         | 192.168.70.2         | 255.255.255.0     | 0012.4AD6.3B07        |
|                     |                        | VLAN 80         | 192.168.80.2         | 255.255.255.0     | 0012.4AD6.3B08        |
|                     |                        | VLAN 90         | 192.168.90.2         | 255.255.255.0     | 0012.4AD6.3B09        |
|                     |                        | VLAN 100        | 192.168.100.2        | 255.255.255.0     | 00D0.9776.4409        |

### Virtual Router VLANs

| **VLAN**  | **IP Address**       | **Subnet Mask**    |
|-----------|----------------------|--------------------|
| VLAN 10   | 192.168.10.3         | 255.255.255.0      |
| VLAN 20   | 192.168.20.3         | 255.255.255.0      |
| VLAN 30   | 192.168.30.3         | 255.255.255.0      |
| VLAN 40   | 192.168.40.3         | 255.255.255.0      |
| VLAN 50   | 192.168.50.3         | 255.255.255.0      |
| VLAN 60   | 192.168.60.3         | 255.255.255.0      |
| VLAN 70   | 192.168.70.3         | 255.255.255.0      |
| VLAN 80   | 192.168.80.3         | 255.255.255.0      |
| VLAN 90   | 192.168.90.3         | 255.255.255.0      |
| VLAN 100  | 192.168.100.3        | 255.255.255.0      |

---

## 4. Network Devices Running Configuration Details

*Additional documents and instructions are attached.*

![image](https://github.com/user-attachments/assets/cc1fa756-d055-4eff-9f89-e0ace9b354fa)

## DHCP
*Below are the DHCP scope created on the server:*

![image](https://github.com/user-attachments/assets/0283d6ef-d00b-4bfe-80c6-c79ca3fdbdd5)

# Backup

Server backups are critical for ensuring data security, operational continuity, and compliance. Backup ensures the following:

- Protection against data loss due to hardware failure and human error
- Acts as a backbone during disaster recovery caused by natural disasters or cyberattacks
- Ensures business continuity by minimizing downtime and quickly restoring the system in case of failure

Regular backups ensure data security, business resilience, and regulatory compliance, making them an essential part of any IT strategy.

Angel Medical has a dedicated physical server for backup operations, and a scheduled backup is configured with Windows Backup to run daily at 9 PM.

Below is a configuration of the backup operations and success rate:


![image](https://github.com/user-attachments/assets/29264479-02e8-4072-a18e-5539360a1013)

![image](https://github.com/user-attachments/assets/49bd658d-c79f-4e9b-ac19-d1b4f4558d6e)

# Webserver

The webserver is accessible via the link below:

- **Login credentials to Ubuntu server:**
  - Username: `webadmin`
  - Password: `xxxxxxxxxxxx`

[http://192.168.100.252/index1.html](http://192.168.100.252/index1.html)

The webserver was created with Ubuntu server 24.10, and SQL was set up with the following details:

| S/N | Users created  | Databases  | Privilege |
| --- | -------------- | ---------- | --------- |
| 1   | Sql_admin      | Angelmedical | ALL       |
| 2   | account        | Finance    | ALL       |
| 3   | doctor         | Management | ALL       |
| 4   | Medical        |            |           |
| 5   | Pharmacy       |            |           |

---

# File Server

Angel Medical has an SMB file sharing system for departmental folders. The following departmental folders have been created:

- Administration folder
- Front-desk folder
- IT folder
- Management folder
- Medical folder
- Finance folder
- General Services folder
- Laboratory folder
- Marketing folder
- Pharmacy folder

It can be accessed via: `\\syslog-2022\` or `\\192.168.100.194\`.

---

# Angel Medical Center SharePoint Site

## 1) Introduction

The Angel Medical Center SharePoint site serves as a centralized hub for managing information, collaboration, and communication across departments. This site is designed to streamline workflows and manage healthcare-related documents securely. It ensures compliance with healthcare IT standards and provides role-based access to critical resources.

This documentation provides comprehensive guidance on the site’s structure, functionality, and management to ensure optimal utilization.

## 2) Purpose

The SharePoint site is designed to:

- **Enhance collaboration among team members:**
  - Establish open and transparent communication channels to ensure all team members are informed and aligned on goals, tasks, and progress.
  - Provide opportunities for brainstorming and collective problem-solving.

- **Secure document storage and management:**
  - Protect sensitive information, control access, ensure compliance, facilitate secure document sharing, and monitor access for accountability.

- **Streamline communication and announcements:**
  - Ensure timely, clear, and organized dissemination of important updates, news, and alerts, ensuring that all team members are well-informed, aligned on goals, and aware of key events or changes.

- **Provide access to departmental tools and resources:**
  - Provide a centralized hub where team members can easily access the tools, documents, and resources they need for their daily tasks. It helps ensure that everyone has the necessary resources at their fingertips and makes sure that materials like reports are readily available.

## 3) Site Structure

### 3.1 Home Page Overview

- Displays key announcements, quick links, Department/Units, events, and news.

- **Welcome Banner:** Displays a greeting and the team's mission or focus to set a positive tone for the homepage.

- **Quick Links:** Links to frequently used documents and tools.

- **Other site Pages:** Provides easy navigation to the Pharmacy, Emergency, and Covid Response departments/units.

- **Announcements:** For hospital-wide updates.


![image](https://github.com/user-attachments/assets/50593290-f0ff-4352-b018-7b20589fe1a7)

*Quick Links*: Links to frequently used documents and tools.

![image](https://github.com/user-attachments/assets/b2b9aac2-a7bc-4126-976a-5f7f5b103f7d)

*Other site Pages*: Provides easy navigation to the Pharmacy, Emergency and Covid Response 
departments/units

![image](https://github.com/user-attachments/assets/0c4d8cf5-bc2c-4868-a662-72328ed5ec8e)

*Announcements*: For Hospital-wide updates.

![image](https://github.com/user-attachments/assets/77e72508-370a-4bde-a314-754b8da195c8)

*Event and News*: Tracks events, meetings, and deadlines.

![image](https://github.com/user-attachments/assets/8c368162-7397-4a96-acc1-dbe870bc5a1c)

# Document Libraries

A centralized document management system that provides a secure, collaborative platform for various departments to store, access, and manage documents, with features such as permission-based access.

- **Doctors Patient Record**
- **Nurse’s Patient Record**
- **Laboratory Records**
- **Emergency Records**
- **Inpatient Records**
- **Outpatient Records**
- **Dental Records**

---

# Hospital Departments

- **Medical Department**
- **Pharmacy Department**
- **Emergency Department/Unit**

---

# 4) Key Features

### Version Control
Tracks changes to documents and allows rollback to previous versions.

### Alerts and Notifications
Notifies users about updates, new uploads, or changes to content.

### Integration
- **Microsoft Office:** Seamless integration with Word, Teams, and Outlook.

### Future Enhancements
- Implement AI-powered insights for document usage.
- Expand integration with third-party healthcare applications.
- Develop additional training modules for new users.

---

# Conclusion

The Angel Medical Center SharePoint site is a powerful tool for improving collaboration and efficiency. Following this documentation will help users and administrators make the most of its features.
