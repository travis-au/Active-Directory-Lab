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

<h3>Step: Promote the Server to a Domain Controller</h3>
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



