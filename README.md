# osTicket - Prerequisites and Installation

This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.

## Environments and Technologies Used
- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

## Operating Systems Used
- Windows 10 (21H2)

## List of Prerequisites
- Create a VM using Azure
- Enable IIS
- Install Web Platform Installer
- Install MySQL
- Install C++ Redistributable
- Configure permissions and install osTicket

## Installation Steps

1. **Create Azure VM**
   - Create an Azure VM using Windows 10 with 4 vCPUs.
   - Obtain the VM's IP address and open it in the Remote Desktop Connection program on Windows.
   - Log in using the VM's IP address in the Remote Desktop Connection app.

2. **Download and Extract osTicket**
   - Within the VM, download and extract osTicket.

3. **Enable IIS in Windows**
   - Open Control Panel → Programs → Programs and Features → Turn Windows features on or off.
   - Navigate to Internet Information Services → World Wide Web Services → Application Development Features.
   - Enable [CGI] → Click OK → Done.

4. **Install PHP Manager**
   - From the “osTicket-Installation-Files” folder, install `PHPManagerForIIS_V1.5.0.msi`.

5. **Install Rewrite Module**
   - From the “osTicket-Installation-Files” folder, install `rewrite_amd64_en-US.msi`.

6. **Set Up PHP**
   - Create the directory `C:\`.
   - From the “osTicket-Installation-Files” folder, unzip `php-7.3.8-nts-Win32-VC15-x86.zip` into `C:\PHP`.

7. **Install Visual C++**
   - From the “osTicket-Installation-Files” folder, install `VC_redist.x86.exe`.

8. **Install MySQL**
   - From the “osTicket-Installation-Files” folder, install `mysql-5.5.62-win32.msi`.
     - Choose Typical Setup.
     - Launch Configuration Wizard after installation.
     - Select Standard Configuration.
     - Use Username: `root`, Password: `password`.

9. **Configure IIS**
   - Open IIS as an Administrator.
   - Register PHP using PHP Manager (`C:\PHP\php-cgi.exe`).
   - Restart the IIS server.

10. **Install osTicket**
    - From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip”.
    - Copy the “upload” folder into “c:\inetpub\wwwroot”.
    - Within “c:\inetpub\wwwroot”, rename “upload” to “osTicket”.
    - Restart IIS.
    - In IIS, go to Sites → Default → osTicket.
    - Click “Browse *:80” on the right.
    - Verify the osTicket site loads (note: some extensions may be unavailable).

11. **Enable PHP Extensions**
    - In IIS, go to Sites → Default Web Site → osTicket → Double-click PHP Manager.
    - Click “Enable or disable an extension.”
    - Enable:
      - `php_imap.dll`
      - `php_intl.dll`
      - `php_opcache.dll`
    - Refresh the osTicket site in the browser to observe changes.

12. **Configure ost-config.php**
    - Rename `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php` to `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.
    - Assign Permissions:
      - Disable inheritance → Remove All.
      - Add New Permissions → Everyone → All.
      - Grant access to “Everyone” and enable all permissions.

13. **Reload osTicket Site**
    - Reload the osTicket website and fill in personal information.

14. **Install and Configure HeidiSQL**
    - From the “osTicket-Installation-Files” folder, install HeidiSQL.
    - Open HeidiSQL, click “New” in the bottom left, enter password (`root`), and click Open.
    - Right-click (Unnamed) → Create new → Database.
    - Name the database `osTicket` (exactly as shown) → Click OK.

15. **Finalize osTicket Installation**
    - Return to the osTicket site and input the database settings.
      - Click “Install.”
      - osTicket is now installed!
