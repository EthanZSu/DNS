# DNS
<p align="center">
<img src="" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- 

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Item 1
- Item 2
- Item 3
- Item 4
- Item 5

<h2>Installation Steps</h2>

<p>
<img src="https://github.com/user-attachments/assets/d7455235-a04d-4757-9462-035b85b0b8b8" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Microsoft Azure search: Virtual Machines & select Client-1 VM.
  <br />
Copy Client-1's Public IP address into the Remote Desktop Connection & Connect.
  <br />
Enter the administrator account credentials for the VM: your domain administrator account & password.
</p>
<br />


<p>
<img src="https://github.com/user-attachments/assets/37b1419b-63a7-465c-ad25-1dfc2675cc81" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Click "Yes" to this pop-up.
</p>
<br />



<p>
<img src="https://github.com/user-attachments/assets/64885a08-8346-4bcf-9dbf-6180906e9c32" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Login DC-1 with your domain admin account.
</p>
<br />



<p>
<img src="https://github.com/user-attachments/assets/3570ef62-bd71-457a-84a4-3243ff8b2d7c" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Click "Yes" to this pop-up.
</p>
<br />



<p>
<img src="https://github.com/user-attachments/assets/283c2e47-196d-4add-9529-3c4c9e0c36da" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In Client-1, open command prompt via the taskbar search box.
  <br />
Then in the command prompt, ping mainframe.
  <br />
  <br />
The ping will fail because Client-1 can't find host mainframe's IP address:
  <br />
1. in it's local DNS cache.
  <br />
2. in it's local host file.
  <br />
3. in it's DNS server (being DC-1).
</p>
<br />



<p>
<img src="https://github.com/user-attachments/assets/bc9735c9-ebf6-4716-9aa1-77c5c6188cf6" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
(In DC-1: Except for the Server Manager, close any remaining windows from the previous active directory project.)
  <br />
  <br />
Open Server Manager via the taskbar search box.
  <br />
On the top right select Tools.
  <br />
Then in DNS manager, select DNS on the left.
  <br />
Under DNS: expand DC-1, and expand Forward Lookup Zones.
  <br />
Select mydomain.com
</p>
<br />



<p>
<img src="https://github.com/user-attachments/assets/52744067-1bfb-4430-84ac-77ae5ab66f8e" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In the bottom right half of the DNS Manager, anywhere in white: right-click.
  <br />
Select: New host (A or AAAA).
  <br />
Input the name: mainframe.
  <br />
Assign (any) IP address: DC-1's private IP address.
  <br />
Click: Add Host, OK, Done.
</p>
<br />



<p>
<img src="https://github.com/user-attachments/assets/30bb1197-d660-4d71-81bb-8ed538b763a1" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In Client-1's command prompt: ping mainframe again.
  <br />
Now you should see 4 replies from mainframe.
</p>
<br />



<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />



<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
