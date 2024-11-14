# Active Directory Management

![Active Directory Logo](https://flashstart.com/wp-content/uploads/2022/04/fs_sito_img_activedirectory-page.png)

This project demonstrates the management of Active Directory (AD) for user account creation, permission management, and the structuring of Organizational Units (OUs).

## Skills Covered:
- Creating and managing user accounts in AD
- Structuring Organizational Units for better management
- Modifying user permissions and group memberships
- Implementing group policies to enforce security policies

## Key Tasks:
1. **Create a new user account** in Active Directory.
2. **Set up Organizational Units (OUs)** to organize users.
3. **Assign user permissions** and group memberships for resource access.
4. **Modify group policies** to implement company-wide policies.


---
**Resources:**
- [Microsoft AD Documentation](https://learn.microsoft.com/en-us/entra/identity/domain-services/compare-identity-solutions)
- [Active Directory Best Practices](https://learn.microsoft.com/en-us/training/paths/active-directory-domain-services/)



# Microsoft Active Directory (AD) Overview

**Microsoft Active Directory (AD)** is a **directory service** designed to simplify network management for organizations. Operating on **Windows Server**, AD efficiently stores and organizes information about network components, including users, devices, and services. It provides convenient access to this information for both administrators and users. Furthermore, AD allows administrators to regulate permissions, manage access to network resources, and create security policies, optimizing overall network management.

---

## Technologies Used
- **Microsoft Azure**
- **Remote Desktop**
- **Active Directory Domain**
- **PowerShell**

## Operating Systems Used
- **Windows 10**
- **Windows Server**

---

## Steps for Setting up in Azure

![Required Components](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/media/how-to-connect-install-custom/requiredcomponents2.png)

<details>
  <summary style="font-weight: bold; color: #2C3E50;">Step 1: Virtual Machines Setup</summary>
  <p>In this step, the virtual machines must sit in the same **resource group** and the same **virtual network** to be connected. The virtual network can be created separately. The **Domain Controller** will have **Windows Server 2022** as the client computer will be **Windows 10**. Windows Server 2022 has access to the **Server Manager**, which will be used later in the steps.</p>
</details>

<details>
  <summary style="font-weight: bold; color: #2C3E50;">Step 2: Network Configuration</summary>
  <p>In this demonstration, the NIC in the domain controller needs to be set to static. The **DNS** of the client VM should be configured to match the Domain Controller’s DNS. To check connectivity, turn off the firewall in the domain controller. In the client’s computer, open PowerShell and type <code>ipconfig /all</code>. Here, the DNS should show the Domain Controller IP address.</p>
</details>

---

## Configuration Steps

![Active Directory Configuration](https://i.ytimg.com/vi/1jHW_sat2xE/maxresdefault.jpg)

<details>
  <summary style="font-weight: bold; color: #2C3E50;">Step 1: Install Active Directory Domain Services</summary>
  <p>In the **Domain Controller**, download the **Active Directory Domain Services** role, set up a new forest with the domain name (it can be the company or department name). Restart the system and log back in with the domain name.</p>
</details>

<details>
  <summary style="font-weight: bold; color: #2C3E50;">Step 2: Create Organizational Units (OUs)</summary>
  <p>Create **Domain Admin users** by creating new **Organizational Units (OUs)**. For this tutorial, use the names <code>_EMPLOYEES</code> and <code>_ADMIN</code>. New employees will have their names and permissions listed under these OUs. Log out and log back in as the new employee to verify access.</p>
</details>

<details>
  <summary style="font-weight: bold; color: #2C3E50;">Step 3: Add Client VM to Domain</summary>
  <p>Add the **Client-1 Virtual Machine** into the domain. After restarting, the client-1 should appear in the **Active Directory Users and Computers (ADUC)**. Drag the account to <code>_CLIENTS</code>. Under **_CLIENTS**, users will have non-admin permissions. Log into **Client-1** as an admin (e.g., <code>mydomain.com/alice_admin</code>).</p>
</details>

---

## Learn More About Active Directory
For more in-depth information on **Active Directory** and its management, visit the official Microsoft documentation or explore additional resources on related topics:

- [Active Directory Documentation](https://learn.microsoft.com/en-us/windows-server/identity/active-directory-domain-services)
- [PowerShell AD Cmdlets](https://learn.microsoft.com/en-us/powershell/module/activedirectory/)

---

*Note:* The steps mentioned above are essential for setting up and managing **Active Directory** within an organization. With these steps, you'll be able to control network resources, manage users and permissions, and secure access to your company's data.
