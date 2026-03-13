# Workstation Security Audit: Lenovo Desktop (CAPACITI-JHB)

## Project Overview
This repository documents a comprehensive **System Security Audit** performed on a Lenovo workstation. The goal was to evaluate the current security posture, identify critical vulnerabilities, and implement immediate hardening measures to protect against unauthorized access and malware.

**System Details:**
* **Hostname:** CAPACITI-JHB
* **User Account:** Local Administrator
* **Audit Date:** March 13, 2026
* **Auditor:** Thandeka Mbokazi

---

## Audit Methodology & Findings

### 1. Identity & Access Management (IAM)
**Status:** ❌ Critical Risk Identified  
**Finding:** During the audit of the `Sign-in Options`, it was discovered that the primary administrative account had **no password protection**.

* **Vulnerability:** Without a password, the system lacks a basic "front door," allowing any physical user to bypass security and access sensitive data.
* **Action Taken:** Initiated the setup of a high-entropy alphanumeric password.

> **Screenshot Evidence:** > Password Security

<img width="951" height="284" alt="Password" src="https://github.com/user-attachments/assets/915fab58-75fc-4e4b-9fb2-bcfff58f52e5" />

---

### 2. Operating System Lifecycle & Patch Management
**Status:** ❌ High Risk Identified  
**Finding:** The Windows Update center indicates the current OS build has reached **End of Support (EoS)**.

* **Vulnerability:** EoS systems no longer receive "Patch Tuesday" updates or critical security fixes from Microsoft. This leaves the system open to known exploits that will never be patched.
* **Remediation Plan:** Scheduled a full system upgrade to a supported Windows 10/11 version.

> **Screenshot Evidence:** > Windows Update
<img width="1033" height="815" alt="windows update" src="https://github.com/user-attachments/assets/1cfded9d-953d-4054-99f4-3460fe899f76" />

---


### 3. Endpoint Protection (Antivirus)
**Status:** ✅ Secure  
**Finding:** Microsoft Defender is fully operational. A manual `Quick Scan` was performed to verify the integrity of the filesystem.

* **Metrics:** 12,579 files scanned in 20 seconds.
* **Result:** 0 Threats detected. Security intelligence is verified as up-to-date (Version: 2026/03/13).

> **Screenshot Evidence:** > Antivirus Status

<img width="928" height="800" alt="Virus and Thread Protection" src="https://github.com/user-attachments/assets/e4f0833e-52be-4ac3-a9e9-ca1dd3c0d3a5" />

---

### 4. Network Firewall Configuration
**Status:** ✅ Secure  
**Finding:** The Windows Defender Firewall is actively filtering traffic across all three network profiles (Domain, Private, and Public).

* **Security Posture:** All incoming connections are blocked by default unless explicitly allowed. This prevents unauthorized network probing.

> **Screenshot Evidence:** > Firewall Settings

<img width="939" height="718" alt="Firewall settings" src="https://github.com/user-attachments/assets/d1ba062f-13bd-4c9b-b03c-0507edc5409c" />

---

### 5. Software Inventory & Attack Surface Review
**Status:** ✅ Managed  
**Finding:** A review of the `Programs and Features` list was conducted to ensure only authorized development tools are installed.

* **Approved Toolchain:** Git, Python 3.14, Node.js, Oracle VirtualBox, and VS Code.
* **Analysis:** No suspicious third-party software or unauthorized "bloatware" was found. The attack surface is minimized to necessary productivity tools.

> **Screenshot Evidence:** > Software Inventory

<img width="991" height="673" alt="Installed Software" src="https://github.com/user-attachments/assets/e43939b7-44ee-40cf-bdff-440d3cb52ab2" />


---

##  Final Security Recommendations

1.  **Immediate OS Re-imaging:** Perform a clean install of a supported Windows version to mitigate the "End of Support" risk.
2.  **Password Policy:** Implement a policy requiring passwords to be changed every 90 days.
3.  **Virtualization Security:** Since `VirtualBox` is installed, ensure that "Core Isolation" is enabled in Device Security to protect memory processes.
4.  **Least Privilege:** Create a standard (non-admin) user account for daily tasks to prevent accidental system-wide changes.

---

## How to Replicate this Audit
To perform this audit on any Windows-based Lenovo machine:
1.  Check Update Status: `Settings > Update & Security`
2.  Check Account Security: `Settings > Accounts > Sign-in options`
3.  Audit Installed Apps: `Control Panel > Programs > Programs and Features`
4.  Verify Defense: `Windows Security > Virus & threat protection`
