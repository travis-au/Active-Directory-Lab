# Active-Directory-Lab
<h1>Working with Active Directory in Windows Server 2025</h1>
  
<h2>Description</h2>

<b>In Azure, I create a virtual machine and install a Windows Server 2025 instance. I promote the server to a Domain Controller and build a basic Active Directory structure, creating OUs, users and groups.
</b>

<br />
<br />

<h3>Step 1: Create a VM in Azure</h3>
<p>
  To begin my Active Directory lab, I deployed a Windows Server virtual machine in Azure that will serve as my Domain Controller. I selected a nearby region for better performance, chose a VM size capable of running AD services, and created secure administrator credentials. I placed the VM in the correct virtual network and assigned it a static private IP address, ensuring the Domain Controller always uses the same IP—critical for DNS, authentication, and domain reliability. After enabling RDP access, I reviewed the configuration, created the VM, and connected to it to begin installing and configuring Active Directory.
</p>

<br />

<p align="center">
  <img src="images/vm-creation1.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation2.png" height="85%" width="85%" alt="virtual machine DC01"/>
</p>

<br />

<h3>Step 2: Installing Active Directory Domain Services (AD DS)</h3>
<p>
  In this step, I connected to my server via RDP and opened Server Manager to begin installing the Active Directory Domain Services role. I used the Add Roles and Features wizard to select Active Directory Domain Services, added the required features, and completed the installation. At this stage, I’m only installing the AD DS binaries and management tools—I’m not creating a domain or promoting the server yet . No domain, forest, DNS, or authentication settings are configured during this step; the server simply becomes AD‑DS‑ready. Once the installation finished, Server Manager displayed the notification to Promote this server to a domain controller, confirming that the role was successfully installed and the server is ready for domain creation in the next step .
</p>

<br />

<p align="center">
  <img src="images/vm-creation3.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation5.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation4.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation6.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation7.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation8.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation9.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation10.png" height="85%" width="85%" alt="virtual machine DC01"/>
</p>

<br />

<h3>Step 3: Promote the Server to a Domain Controller</h3>
<p>
  With AD DS installed, I used Server Manager to start the promotion process by selecting the notification flag and choosing Promote this server to a domain controller . Since this is a brand‑new environment, I created a new forest and specified my private internal root domain name (e.g., lab.local) . I kept the default Domain Controller options, enabled DNS and Global Catalog, and set a Directory Services Restore Mode (DSRM) password, which is required for recovery scenarios even though it’s rarely used day‑to‑day . After reviewing the configuration, I proceeded through the DNS and NetBIOS steps, accepted the defaults for database, log, and SYSVOL paths, and ran the prerequisites check Current page. Once everything passed, I completed the installation, and the server automatically rebooted. After the restart, I logged in using my new domain administrator account, confirming that the server was successfully promoted and that Active Directory and DNS tools were now available.
</p>

<br />

<p align="center">
  <img src="images/vm-creation11.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation12.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation13.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation14.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation15.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation16.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation17.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation18.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation19.png" height="85%" width="85%" alt="virtual machine DC01"/>
</p>

<br />

<h3>Step 4: Create Organizational Units</h3>

<p>
  With my Domain Controller fully promoted, I began organizing the domain by creating a set of Organizational Units (OUs) to structure users, computers, and administrative groups. I opened Active Directory Users and Computers and created a top‑level OU to hold all domain resources, then added sub‑OUs for Users, Computers, and Admins. This structure keeps the environment clean and makes it easier to apply Group Policies later. By separating standard users, admin accounts, and computer objects into their own OUs, I ensure better security, clearer management boundaries, and more precise control over policies as the domain grows.
</p>

<br />

<p align="center">
  <img src="images/vm-creation20.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation21.png" height="85%" width="85%" alt="virtual machine DC01"/>
</p>

<br />

<h3>Step 5: Create Users</h3>

<p>
  In this step, I began adding user accounts to my domain by creating them inside the correct Organizational Unit structure. I opened Active Directory Users and Computers, navigated to my branch‑specific Users OU, and created my first user by entering their name and logon details . I set an initial password and kept the standard password options unchanged for the lab environment Current page. After that, I created the remaining users and placed them in the same OU so they inherit the proper policies and remain organized according to the domain structure . Once finished, I verified that all accounts appeared in the correct OU and that each user’s properties reflected the right path in Active Directory Current page.
</p>

<br />

<p align="center">
  <img src="images/vm-creation22.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation23.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation24.png" height="85%" width="85%" alt="virtual machine DC01"/>
</p>

<br />

<h3>Step 6: Create Security Groups</h3>

<p>
  In this step, I set up the security groups that will control access throughout my Active Directory environment. Since groups are usually centralized rather than stored inside branch OUs, I first created a dedicated _Groups OU at the domain root to keep everything organized . Inside this OU, I created three Global Security Groups—Helpdesk, Accounting, and ITSupport—which represent the different roles or departments in my lab environment . Global Security Groups are the standard choice for grouping users by role because they can be cleanly nested into resource‑specific groups later on Current page.

After creating the groups, I assigned users to them based on their job function—for example, adding Alice Johnson to Helpdesk, bmartinez to Accounting, and cwalker to ITSupport . Finally, I verified each group to ensure the correct members were listed, since group membership is how access is granted in real‑world AD environments and changes take effect immediately 
</p>

<br />

<p>
  <img src="images/vm-creation25.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation26.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation27.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation28.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation29.png" height="85%" width="85%" alt="virtual machine DC01"/>
  <img src="images/vm-creation30.png" height="85%" width="85%" alt="virtual machine DC01"/>
</p>

<br />

<h3>Step 7: Create a Windows Client VM and Join the Domain</h3>



