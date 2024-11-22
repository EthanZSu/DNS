# DNS
<p align="center">
<img src="https://github.com/user-attachments/assets/92d8c727-882e-44a5-9293-0eb0bfe6cea6" height="70" width="110"  alt="osTicket logo"/>
</p>


This lab focuses on DNS in Active Directory by experimenting with A-records, DNS cache, CNAME records, and root hints.  <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022 Datacenter

<h2>List of Prerequisites</h2>

- Virtual Machine "Client-1" (joined to Domain Controller)
- Virtual Machine "DC-1" (Domain Controller with Active Directory)

<h2>Lab Experiment Phases</h2>

 1. Creating and observing A-records.
 2. Understanding the importance of ipconfig /flushdns.
 3. Creating and observing CNAME records.
 4. Understanding Root Hints.
     
<p>
<h3>1. Creating and observing A-records.</h3>
<img src="https://github.com/user-attachments/assets/d7455235-a04d-4757-9462-035b85b0b8b8" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Microsoft Azure search: Virtual Machines & select Client-1 VM.
  <br />
Copy Client-1's Public IP address into the Remote Desktop Connection & Connect.
  <br />
Enter the administrator account credentials for the VM: your domain administrator account & password.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/37b1419b-63a7-465c-ad25-1dfc2675cc81" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Click "Yes" to this pop-up.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/64885a08-8346-4bcf-9dbf-6180906e9c32" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Login DC-1 with your domain admin account.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />



<p>
<img src="https://github.com/user-attachments/assets/3570ef62-bd71-457a-84a4-3243ff8b2d7c" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Click "Yes" to this pop-up.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
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
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/1507ef5b-4558-4bd2-a2af-ff1a9e2d972b" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
You can manually quickly check Client-1's local DNS cache. 
 <br />
 <br />
Open command prompt: input the above commands.
 <br />
On your keyboard: hold down CTRL, then F.
 <br />
Then input: mainframe, click "Find Next".
 <br />
The result will be mainframe isn't in the DNS cache.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/c316cee1-c410-4047-ae84-a7ec56013425" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
You can also manually check Client-1's Host File 
</p>
<p>
Search for Notepad in Client 1's taskbar searchbox.
 <br />
Right click: Notepad, then click: Run as admin.
 <br />
Allow Notepad to make changes by clicking: Yes.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/6ee6ddf2-a8d6-4f56-926f-bf9a2b1850b2" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In top left select: File, then: open .
 <br />
Then in bottom right select: All Files .
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/5acd88cd-3e40-4d0d-971e-eb2dc5147356" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
At the top, open: System 32, 
 <br />
Scroll down and open: drivers.
 <br />
Then open: etc, hosts .
 <br />
 <br />
The result will again be mainframe isn't in the local host file either
 <br />
(as IP mappings must first be manually inputted there).
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/bc9735c9-ebf6-4716-9aa1-77c5c6188cf6" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Anyways, an A-record for mainframe must be made in the DNS server (being DC-1) so Client-1 can ping it.
  <br />
  <br />
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
________________________________________________________________________________________________________________________
<br />
<br />
<br />
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
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />



<p>
<img src="https://github.com/user-attachments/assets/30bb1197-d660-4d71-81bb-8ed538b763a1" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In Client-1's command prompt: ping mainframe again.
  <br />
Now you should see 4 replies from mainframe.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />



<p>
<img src="https://github.com/user-attachments/assets/2f264d4f-ea5b-469a-903f-d90ba4dbdfcb" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Observe Client-1's DNS cache: 
  <br />
in the command prompt type: ipconfig /displaydns , click: ENTER.
  <br />
  <br />
You will see the A-record for mainframe in the client's local DNS cache.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />



<p>
<h3> 2. Understanding the importance of ipconfig /flushdns.</h3>
<img src="https://github.com/user-attachments/assets/fccbb0d9-5c29-453d-9c35-e1f4316f637c" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In DC-1's DNS Manager, on the left select: mydomain.com .
  <br />
Then under Name select: mainframe .
  <br />
Change the IP address to: 8.8.8.8
  <br />
Click: Apply, OK.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />



<p>
<img src="https://github.com/user-attachments/assets/56068a0a-761e-44b1-9ab5-8b2da81ebe46" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In Client-1's command prompt: ping mainframe.
  <br />
  <br />
You will see 4 replies from mainframe's previous IP address
  <br />
because the old IP address still exists on Client-1's local DNS cache.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />



<p>
<img src="https://github.com/user-attachments/assets/52881d64-e9db-418f-aeb4-ea7ae8532464" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Close the command prompt in Client-1.
  <br />
In the taskbar searchbox type: cmd ,
  <br />
Right click cmd and then select Run as administrator.
  <br />
Confirm: Yes .
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />



<p>
<img src="https://github.com/user-attachments/assets/cce47ff2-7575-4af9-b725-b080ac737177" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
For Client-1 to receive replies from mainframe's new IP address:
  <br />
(you must flush the DNS Resolver Cache 
  <br />  
so Client-1 will be forced to query the DNS server for the new IP address).
  <br />
  <br />
The importance of occasionally flushing a computer's local DNS cache is 
  <br /> if local network resources changed IP addresses, the computer will need the new IP mapping to find those resources.
  <br />
  <br />
In Client-1's command prompt, type: ipconfig /flushdns.
  <br />
Hit: ENTER
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />



<p>
<img src="https://github.com/user-attachments/assets/ee65e408-ea19-4308-8768-f44b40c1648d" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In Client-1's command prompt, ping mainframe again.
  <br />
Now you will get 4 replies from mainframe's new IP address. 
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />



<p>
<img src="https://github.com/user-attachments/assets/c210d5a9-a053-41d3-a2a7-df58339f11cb" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In the command prompt, input: ipconfig /displaydns.
  <br />
You will see Client-1 has the latest A-record for mainframe: 8.8.8.8 .
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />



<p>
<h3> 3. Creating and observing CNAME records.</h3>
<img src="https://github.com/user-attachments/assets/ef9f9ee1-10f7-4bb9-913b-b8055e2e799b" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In Client 1, open command prompt and ping: search .
  <br />
The command prompt will read: ping request could not find host search.

</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/c98a3373-ed2c-4d45-8a2c-819bff66d75e" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In DC-1, open the Server Manager.
  <br />
Select Tools on the right, and open DNS.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/e27ceac6-acf6-487b-8a6e-f156950404fb" height="60%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Select: DC-1, Forward Lookup Zones, mydomain.com .
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/1d14d195-bbcc-4105-8ceb-dcf7b20c0ab4" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Right click beneath the right column & click New Alias (CNAME).
  <br />
For the Alias name, input: search.
  <br />
For the fully qualified domain name for target host, input: www.google.com
  <br />
Click OK .
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/20de4dda-973d-4292-b6bf-58882520da9b" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
You must run command prompt as administrator and flush the dns.
  <br />
Now in Client 1 if you ping the CNAME search, you will see 4 replies from Google.com
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/2068e334-188d-4ae1-a69f-dafc8f4dc639" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Use the command: ipconfig /displaydns,
  <br />
  <br />
and you will see the CNAME search resolve to Google.com, 
  <br />
which resolves to Google's public IP address.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<h3>4. Understanding Root Hints.</h3>
<img src="https://github.com/user-attachments/assets/86769242-e8d4-4130-9c12-71b7c72a4ccb" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
On Client-1, you could open Microsoft Edge and browse to Disney.com.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/dfbfd774-84d3-447d-866e-ed550db0ea05" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Then open command prompt and input: ipconfig /all.
  <br />
You will see client-1's DNS server is DC-1.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/0d9a4566-ec27-41f3-abca-192e474edbf1" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In DC-1, you can open the DNS manager and observe there aren't many records.
  <br />
There certainly aren't public domain sites listed there.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="https://github.com/user-attachments/assets/7e4a2c43-e59c-4c82-8388-72185681f384" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
The reason DC-1 was able to provide Disney's IP mapping to Client-1 is because DC-1 has root hints,
  <br />
which are found under DC-1 Properties in DNS manager.
  <br />
  <br />
Root hints resolve queries for zones that don't exist on the local DNS server, such as Domains found on the Internet.
</p>
________________________________________________________________________________________________________________________
<br />
<br />
<br />
<br />


<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>

</p>
<br />


<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>

</p>
<br />


<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>

</p>
<br />


<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>

</p>
<br />


<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>

</p>
<br />




</p>
<br />



