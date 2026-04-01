# Setting up Active Directory

## Lab Objective
Deploy a fully functional Active Directory domain within a segmented home lab environment. In this lab, I configured my Windows Server, installed Active Directory DS, linked my Windows 11 desktop to the server, and created two organizational units, each with its own users.  


## Skills Demonstrated
### Infrastructure & Virtualization
- *Windows Server Administration* — Navigated Server Manager to install roles and features, promoted a server to a Domain Controller, and configured a new AD forest from the ground up.
- *Active Directory Design & Management* — Structured the domain using Organizational Units (HR and IT), provisioned user accounts, and applied domain controller promotion settings, including forest/domain functional levels.
- *DNS Troubleshooting* — Diagnosed a domain join failure caused by incorrect DNS resolution, manually redirected the client's DNS to the Domain Controller, and verified the fix using ipconfig /all.
- *Domain Client Enrollment* — Successfully joined a Windows machine to the AD domain and authenticated with a domain user account, confirming end-to-end directory functionality.
- *Security Awareness* — Identified and documented sensitive AD file locations (NTDS.dit and related paths) that store domain data including credential hashes, demonstrating an understanding of high-value targets in an AD environment.
- *Home Lab & Virtualized Environment Management* — Built and configured a multi-machine lab environment with a segmented network, laying the groundwork for further security tooling integration (Splunk, Kali Linux, Atomic Red Team).
- *Technical Documentation* — Captured each configuration step with screenshots and written context, producing reproducible documentation suitable for a security portfolio or team knowledge base.

## Result
Successfully deployed a fully functional Active Directory domain within a segmented home lab environment. A Windows Server instance was configured as a Domain Controller, a new forest was established, and the domain was populated with two Organizational Units (HR and IT) each containing a test user account.

- A Windows client machine was enrolled in the domain and used to authenticate as a domain user (John Doe, IT), confirming that directory services, DNS resolution, and domain authentication were all operating correctly end-to-end.
- The completed setup serves as the foundational identity layer for the JuiceBox lab — providing a realistic enterprise-like AD environment ready for the next phases of the project, including attack simulation with Atomic Red Team and log ingestion and detection engineering in Splunk.



## Network Architecture
Hyper-V Internal Switch (Layer 2 only)
### Lab Topology
Subnet: 192.168.100.0/24
| System | Role | IP | 
|-------|----------|------------|
| Windows Server | 2022	Domain Controller + DNS	| 192.168.100.5 |
| Ubuntu 24.04 |	Splunk Server |	192.168.100.30 |
| Windows 11 |	Domain Client |	192.168.100.10 |
| Kali Linux |	Attack Simulation |	192.168.100.20 |

<br />
<br />

<img width="766" height="951" alt="homelab topography" src="https://github.com/user-attachments/assets/adc37c6f-866f-4bf9-a8c1-389602293d2e" />


<br />
<br />

## Step 1 — Enabling ADDS on Windows Server 
Path: <br />
Server Manager → Dashboard →
Manage → Add roles and Features → Enable AD DS
<br />
<br />

<img width="975" height="697" alt="image" src="https://github.com/user-attachments/assets/8b0e901c-979d-4c71-881a-ba498eea8cb3" />

<br />

<img width="975" height="689" alt="image" src="https://github.com/user-attachments/assets/f472608a-942c-43a2-ac4f-fcbb62532f34" />


<br />
<br />

## Step 2 — Promote The Server To a Domain Controller 
<br />
<br />
<img width="975" height="695" alt="image" src="https://github.com/user-attachments/assets/1c2f5212-22eb-4a0f-9098-8eebea24f54f" />
<br />
<br />

### Add a new forest because we are creating a brand new environment 
<br />
<br />
<img width="975" height="646" alt="image" src="https://github.com/user-attachments/assets/db767871-11ae-409b-b08f-b4b6d8b546e0" />
<br />
<br />

### Reboot and Check Status

<img width="773" height="492" alt="image" src="https://github.com/user-attachments/assets/9f1fc608-d260-48d4-900e-ed6e8369e551" />


<br />
<br />

### ✅ Successfully installed ADDS


## Step 3 - Create Units/Users
### Created 2 organizational units: HR and IT, created one user in each 
-	IT:
    -	John Doe 
-	HR:
    -	Amy Doe  

<br />
<br />

<img width="770" height="538" alt="image" src="https://github.com/user-attachments/assets/46c759b0-e911-41f9-925d-0d50351e0312" />

<br />
<br />

## Step 4 - Connect Windows 11 Machine to AD Server


## Technical Concepts Reinforced


