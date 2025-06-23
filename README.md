 
osTicket - Prerequisites and Installation
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.
Environments and Technologies Used
•	Microsoft Azure (Virtual Machines/Compute)
•	Remote Desktop
•	Internet Information Services (IIS)
Operating Systems Used
•	Windows 10 (21H2)
List of Prerequisites
•	Create a VM using Azure
•	Enable IIS
•	Install web platform installer
•	Install MySQL
•	Install C++ Redistributal
•	Configure permissions and install OsTicket
Installation Steps
•	To begin installation for osTicket, create an Azure VM using Windows 10 and 4 vCPUs.


 
•	Next, get the IP address and open it in the Remote Desktop Connection program on Windows.


 
•	In the Remote Desktop Connection app use our VMs IP address to log in. 

 
•	Within the VM download and extract OsTicket


   
- Next enable IIS in Windows
•	To do this we open Control Panel -> Programs -> Programs and Features -> Turn Windows features on or off -> Internet Information Systems -> Worldwide Web Services -> Application Development Features -> Enable file [CGI] -> Click OK -> DONE


   
•	From the “osTicket-Installation-Files” folder, install PHP Manager for IIS PHPManagerForIIS_V1.5.0.msi


 
•	From the “osTicket-Installation-Files” folder install the Rewrite Module rewrite_amd64_en-US.msi


 
•	Create the directory C:\PHP


 
•	From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 php-7.3.8-nts-Win32-VC15-x86.zip into the “C:\PHP” folder


 
•	From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.


 
•	From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)


 
•	Typical Setup ->
•	Launch Configuration Wizard (after install) ->
•	Standard Configuration ->
•	Username: ROOT
•	Password: ROOT


 
•	Open IIS as an Admin


 
•	Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)


 
•	Reload IIS (Open IIS, Stop and Start the server)


 
 
•	Install osTicket v1.15.8
•	From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot” Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”


 
•	Reload IIS (Open IIS, Stop and Start the server)
•	Go to sites -> Default -> osTicket
•	On the right, click “Browse *:80”


 
•	Note that the osTicket site shows up, you will also notice on the bottom that some extensions are not available. We will begin to start enabling some permissions.


 
•	Now, go back to ISS and open Sites -> Default Web site -> osTicket -> and then double-click PHP Manager


 
•	Now click "Enable or disable an extensions" on the bottom


 
•	Enable: php_imap.dll
•	Enable: php_intl.dll
•	Enable: php_opcache.dll
•	Refresh the osTicket site in your browser, observe the changes


 
Now, we must
•	Rename: ost-config.php
•	From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
•	To: C:\inetpub\wwwroot\osTicket\include\ost-config.php


 
Assign Permissions: ost-config.php Disable inheritance -> Remove All New Permissions -> Everyone -> All


 
•	Now we give access to "Everyone" and then enable the permissions!


 
•	Now we reload the OsTicket website and fill in all of our personal information


 
•	Next, from the “osTicket-Installation-Files” folder, install HeidiSQL.


 
•	Open HeidiSQL, click new on the bottom left, enter the password, the password is "root", and then hit open


 
•	Right click (Unnamed) -> (Create new) -> click (Database)


 
•	In the name section type "osTicket" exactly this way and hit OK


 
•	Now we head back to the osTicket site and input our new login information for the database settings


 
•	Now hit install!!


 
•	OsTicket has been installed!


 

