# Microsoft 365 & Azure IT Support – Practical Labs

![AZ-104](https://img.shields.io/badge/AZ--104-Certified-blue) ![M365](https://img.shields.io/badge/Microsoft%20365-Support-orange) ![Azure](https://img.shields.io/badge/Azure-Support-blue) ![Intune](https://img.shields.io/badge/Intune-Endpoint-lightgrey) ![Status](https://img.shields.io/badge/Labs-14%20Tickets-green)

### Project Overview
This repository documents my practical learning journey in IT Support, focusing on Microsoft 365 and Azure cloud services, Windows troubleshooting and IT service management.

The objective is to develop practical technical support skills through simulated real-world IT support tickets, systematic troubleshooting, problem diagnosis, resolution and incident documentation.

Rather than focusing only on theoretical knowledge, this repository demonstrates how IT support issues are investigated and resolved in a business environment.

### Learning Objectives
- Develop practical Microsoft 365 administration and troubleshooting skills
- Troubleshoot Outlook and Exchange Online issues
- Understand Microsoft Entra ID and identity management
- Develop Azure administration and cloud support capabilities
- Troubleshoot Windows operating system and endpoint issues
- Understand user access, authentication and permissions
- Practice IT service management (ITSM) documentation

### Technologies and Tools

| Technology | Learning Focus |
| :--- | :--- |
| **Microsoft 365** | Administration and troubleshooting |
| **Microsoft Outlook** | Email and calendar support |
| **Exchange Online** | Mailboxes and permissions |
| **Microsoft Entra ID** | Identity and access management |
| **Microsoft 365 Admin Centre** | User and service administration |
| **Exchange Admin Centre** | Mailbox administration |
| **Microsoft Azure** | Cloud infrastructure support |
| **Azure Portal** | Resource management |
| **Windows 11** | Endpoint troubleshooting |
| **PowerShell** | Administrative tasks |
| **Microsoft Teams** | Collaboration support |

### Practical Support Labs

#### 1. Microsoft 365 Support
| Ticket | Scenario | Status |
| :--- | :--- | :--- |
| **INC001** | Outlook unable to send or receive emails | Completed |
| **INC002** | User unable to access a shared mailbox | Completed |
| **INC003** | Outlook repeatedly requesting credentials | Planned |
| **INC004** | User unable to access Microsoft 365 applications | Planned |
| **INC005** | Outlook calendar synchronization issue | Planned |

#### 2. Azure Support
| Lab | Scenario | Status |
| :--- | :--- | :--- |
| **AZ001** | Locate and review Azure virtual machines | Planned |
| **AZ002** | Troubleshoot virtual machine connectivity (NSG, RDP) | Planned |
| **AZ003** | Investigate Azure resource access permissions (RBAC/IAM) | Planned |
| **AZ004** | Investigate virtual machine availability | Planned |
| **AZ005** | Review Azure monitoring and alerts (Azure Monitor / KQL) | Planned |

#### 3. Windows Endpoint Support
| Lab | Scenario | Status |
| :--- | :--- | :--- |
| **WIN001** | Troubleshoot Windows login issues (Entra ID Join, Hello) | Planned |
| **WIN002** | Investigate network connectivity problems | Planned |
| **WIN003** | Troubleshoot application installation (Intune / Company Portal) | Planned |
| **WIN004** | Investigate device performance issues | Planned |

### Troubleshooting Methodology
Each practical ticket follows a structured troubleshooting approach:

1.  **Incident Identification** – Understand the reported problem and its impact
2.  **Scope Establishment** – Is it one user, multiple users, or service-wide?
3.  **Initial Troubleshooting** – Check Service Health, compare with working user, basic checks
4.  **Investigation & Log Analysis** – Entra ID Sign-in logs, Exchange logs, Event Viewer, KQL, `dsregcmd /status`
5.  **Root Cause Analysis** – Identify missing permission, policy block, or config issue
6.  **Resolution** – Fix via Admin Centre GUI or PowerShell
7.  **Verification and Testing** – User confirms fix, test functionality
8.  **User Communication** – Clear update on fix and replication time
9.  **Documentation and Closure** – ITSM closure with skills demonstrated

### Each Completed Ticket Contains
- Ticket reference number
- Incident title
- User and department
- Reported symptoms
- Business impact and priority
- Initial troubleshooting
- Investigation findings
- Root cause
- Resolution steps (Portal + PowerShell)
- Verification and testing
- User communication
- Final ticket status
- Lessons learned

### Current Progress

**Microsoft 365**
- [x] Ticket 001 – Outlook connectivity troubleshooting
- [ ] Ticket 002 – Shared mailbox access troubleshooting
- [ ] Additional Exchange Online support scenarios

**Azure**
- [ ] Virtual machine administration (AZ001, AZ004)
- [ ] Azure networking troubleshooting (AZ002)
- [ ] Identity and access management (AZ003 - RBAC)
- [ ] Azure monitoring and diagnostics (AZ005 - KQL / Alerts)

**Windows Endpoint Support**
- [ ] Windows login troubleshooting (WIN001)
- [ ] Network connectivity (WIN002)
- [ ] Application troubleshooting (WIN003 - Intune)

### Professional Development
This project complements my Microsoft Azure Administrator certification (AZ-104) and supports my development towards Cloud Support and DevOps roles.

The focus is on building practical troubleshooting experience, understanding enterprise IT environments and developing the ability to investigate and resolve technical incidents.

### Disclaimer
The support tickets documented in this repository are simulated training scenarios created for educational and professional development purposes.

No confidential company information, real user credentials or private organisational data is included.

**Project:** Microsoft 365 & Azure IT Support – Practical Labs  
**Focus:** IT Support | Microsoft 365 | Azure | Cloud Support | Troubleshooting

## Profile
LinkedIn: Chenjerai | Systems Technician @ STG Africa | Johannesburg
Target: L2 Azure Support Engineer - Johannesburg / Remote SA

---
*Lab built following Microsoft L2 Support Engineer documentation pattern*
---
**Note:** All labs in this repo are simulations based on Microsoft Learn docs, built to practice L2 triage for SA North region. No customer data.
