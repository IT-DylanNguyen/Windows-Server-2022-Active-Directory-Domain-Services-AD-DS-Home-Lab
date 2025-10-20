# 🧱 Windows Server 2022 Active Directory Domain Services (AD DS) Home Lab

**Author:** [Dylan Nguyen](https://www.linkedin.com/in/dylan-nguyen-it/)
**GitHub:** [IT-DylanNguyen](https://github.com/IT-DylanNguyen)
**Date:** October 2025

---

### 🔍 Overview

This project simulates a **real-world enterprise Active Directory environment** using **Windows Server 2022** and a **Windows 11 client VM**.
The lab demonstrates skills in domain management, security policy enforcement, access control, and network resource sharing — all essential to modern IT administration and cybersecurity operations.
I have plans to implement SCCM and AI features.

---

### 🖥️ Environment Setup

* Platform: **VMware Workstation Pro**
* Server OS: **Windows Server 2022**
* Client OS: **Windows 11 Pro**

**Configuration Steps:**

1. Installed **Active Directory Domain Services (AD DS)**, **DNS Server**, **Remote Access**, and **Group Policy Management** roles.
2. Promoted the server to a **Domain Controller** and created a **new forest** with the root domain:

   ```
   test4dylan.local
   ```
3. Assigned a **static IP address** to ensure consistent DNS resolution and domain connectivity.

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/b6a48532-0587-48a6-abb1-5dec3fe8a467" />
<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/f5793688-44fe-418e-8b30-2af2cb108aa2" />

---

### 🧩 Active Directory Structure

* Created **Organizational Units (OUs)** for departments (HR, IT, Marketing).
* Created **Security Groups** and **Users** for each OU.
* Configured **Group Policy Objects (GPOs)** to enforce:

  * Password and Account Lockout Policies
  * Drive Mapping
  * Desktop Wallpaper
  * Control Panel Restriction
  * USB Storage Disablement

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/7ae24b99-d880-4f7b-9433-89807a03306c" />
<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/26773082-0f64-4ed9-9f1d-008fcba81366" />
<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/bb5ab0ce-b477-401c-84c1-f9efc1e3c76b" />




---

### 🌐 DNS and Domain Join

1. Configured **DNS Server** on Windows Server 2022.
2. Set the Windows 11 client VM to use the server’s IP as its DNS resolver.
3. Joined the client machine to the domain using:

   ```
   System > Advanced System Settings > Computer Name > Change > Domain = test4dylan.local
   ```
4. Applied all policies with:

   ```
   gpupdate /force
   ```

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/895991e1-3661-4c16-bde1-4f23f4aee533" />
<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/e7eba098-6e13-4c92-94a9-d2bf8095c8dd" />



---

### 🗂️ Network Sharing and Access Control

* Created **shared folders** and set NTFS/share permissions:

  * **HR Folder:** Accessible only by `HR_Staff`.
  * **IT Folder:** Accessible by `IT_Staff`, with a restricted `Licenses` subfolder only for `IT_Admins`.
* Enabled **Access-Based Enumeration (ABE)** to hide folders users lack permissions for.
* Configured **GPO-based drive mapping** to automatically mount network drives at user login.

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/74af1603-b3ac-489d-9d4d-10621bdc4621" />
<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/1ff4a88c-9e2d-4d70-abc9-2cf38fd7e025" />

---

### 💾 File Server Resource Manager (FSRM)

Installed and configured **FSRM** to manage storage and enforce file hygiene policies:

* **Quota Management:** Applied storage limits using quota templates.
* **File Screening Management:** Blocked certain file types (e.g., .mp3, .exe) from being stored.

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/0cae363d-d6c0-45f2-b4c0-60dd5e9e0721" />
<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/eb5b1b8c-0744-450e-8a14-e6c39bcb4816" />

---

### 🔐 Security Policy Implementation

* Applied **Fine-Grained Password Policies** through Active Directory Administrative Center.
* Configured **User Rights Assignments** via GPO:

  * Denied local logon for non-admin accounts.
  * Restricted Remote Desktop access to authorized groups only.
* Verified enforcement using test user accounts on domain-joined Windows 11 clients.

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/9d27bfcf-3280-4345-b3f6-072f60dfc22a" />
<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/1c96e826-acf8-4de3-95e4-834a262deab3" />


---

### 🧠 Key Takeaways

* Gained practical experience deploying **enterprise-level Active Directory environments**.
* Learned centralized **security management**, **policy enforcement**, and **role-based access control**.
* Implemented **automated resource mapping** and **secure file access**.
* Strengthened understanding of **DNS integration**, **GPO management**, and **file system security**.

---

### ⚙️ Commands Used

| Purpose                           | Command           |
| --------------------------------- | ----------------- |
| View IP configuration             | `ipconfig /all`   |
| Force Group Policy update         | `gpupdate /force` |
| Verify domain controller hostname | `hostname`        |


