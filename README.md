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
</p>



