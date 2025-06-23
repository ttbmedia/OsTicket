![image](https://github.com/user-attachments/assets/6d31c566-d3dd-4032-aa4a-995e7332f0ab)
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
   - ![image](https://github.com/user-attachments/assets/e4a37cce-276e-4ac4-be16-0b50549d8942)

   - Obtain the VM's IP address and open it in the Remote Desktop Connection program on Windows.
   - ![image](https://github.com/user-attachments/assets/c6fe1f2e-cf2c-4389-9157-2e52cc129404)

   - Log in using the VM's IP address in the Remote Desktop Connection app.

2. **Download and Extract osTicket**
   - Within the VM, download and extract osTicket.
   - ![image](https://github.com/user-attachments/assets/048ab0cf-15d2-41a2-bf01-770de7ace8eb)
![image](https://github.com/user-attachments/assets/9feba663-243b-486f-8d40-e4653278bd9e)
![image](https://github.com/user-attachments/assets/2d88d866-3736-47aa-b6d4-4b2c50375ef2)


3. **Enable IIS in Windows**
   - Open Control Panel → Programs → Programs and Features → Turn Windows features on or off.
   - Navigate to Internet Information Services → World Wide Web Services → Application Development Features.
   - Enable [CGI] → Click OK → Done.
   - ![image](https://github.com/user-attachments/assets/23d756f6-faaf-4944-9f63-a55938ea93d6)
![image](https://github.com/user-attachments/assets/118dc855-255d-46ba-b9eb-f1e56ad31a85)


4. **Install PHP Manager**
   - From the “osTicket-Installation-Files” folder, install `PHPManagerForIIS_V1.5.0.msi`.
   - ![image](https://github.com/user-attachments/assets/4683bae1-9495-440f-b146-9ca1d5443a37)

 ![image](https://github.com/user-attachments/assets/870b79b7-a97c-45ed-ac88-c2e96c8e53c9)

5. **Install Rewrite Module**
   - From the “osTicket-Installation-Files” folder, install `rewrite_amd64_en-US.msi`.
   -![image](https://github.com/user-attachments/assets/0b318810-f3d6-46c3-98db-f2e29b99791f)

![image](https://github.com/user-attachments/assets/8f8f3818-464b-42da-969b-c8a9db1d01e5)
![image](https://github.com/user-attachments/assets/4f755a04-911e-47fa-9492-d6f790f038c4)
![image](https://github.com/user-attachments/assets/f20c5614-5936-4a4b-b55d-45a19130f17b)


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
   - ![image](https://github.com/user-attachments/assets/5e595795-56d1-4912-9bae-e45c1ed62114)

   - Restart the IIS server.

10. **Install osTicket**
    - From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip”.
    - Copy the “upload” folder into “c:\inetpub\wwwroot”.
    - Within “c:\inetpub\wwwroot”, rename “upload” to “osTicket”.
    - Restart IIS.
    - In IIS, go to Sites → Default → osTicket.
    - Click “Browse *:80” on the right.
    - ![image](https://github.com/user-attachments/assets/3a8e5a4d-7352-4561-b674-1db9e12b5f66)

    - Verify the osTicket site loads (note: some extensions may be unavailable).

11. **Enable PHP Extensions**
    - In IIS, go to Sites → Default Web Site → osTicket → Double-click PHP Manager.
    - Click “Enable or disable an extension.”
    - Enable:
      - `php_imap.dll`
      - `php_intl.dll`
      - `php_opcache.dll`
    - Refresh the osTicket site in the browser to observe changes.
    - ![image](https://github.com/user-attachments/assets/5610b069-6106-40d5-807b-484196525161)


12. **Configure ost-config.php**
13. ![image](https://github.com/user-attachments/assets/c3490c09-887b-4fe4-89ec-f63a69881480)

    - Rename `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php` to `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.
    - Assign Permissions:
      - Disable inheritance → Remove All.
      - Add New Permissions → Everyone → All.
      - Grant access to “Everyone” and enable all permissions.
      - ![image](https://github.com/user-attachments/assets/6544cc84-f941-4b0b-aebd-3d85c87a5bef)

![image](https://github.com/user-attachments/assets/e0a7430b-6f26-45a2-98c9-58d402e890c4)

13. **Reload osTicket Site**
    - Reload the osTicket website and fill in personal information.
    - ![image](https://github.com/user-attachments/assets/8fbc0aa9-6829-4aab-835e-e2824785d342)


14. **Install and Configure HeidiSQL**
    - From the “osTicket-Installation-Files” folder, install HeidiSQL.
    - ![image](https://github.com/user-attachments/assets/d0699110-aef6-494c-bd4d-56b9ee225bde)

    - ![image](https://github.com/user-attachments/assets/452ae220-8d1c-41a0-bab2-df4d5c27ed40)

    - Open HeidiSQL, click “New” in the bottom left, enter password (`root`), and click Open.
    - ![image](https://github.com/user-attachments/assets/d20385cd-b603-4e7c-a1ed-c8873896b5a1)

    - Right-click (Unnamed) → Create new → Database.
    - ![image](https://github.com/user-attachments/assets/7e98b3c5-1d6a-4975-97e0-30c244ddc40d)

    - Name the database `osTicket` (exactly as shown) → Click OK.

15. **Finalize osTicket Installation**
16. ![image](https://github.com/user-attachments/assets/ba520f80-2b24-4bc3-80e4-b5f5ff1abf7d)

    - Return to the osTicket site and input the database settings.
      - Click “Install.”
      - ![image](https://github.com/user-attachments/assets/14d1c227-ed27-4a25-a92a-f92095c03937)

      - osTicket is now installed!
      - ![image](https://github.com/user-attachments/assets/630a3ad9-874d-4d2e-b9a8-2d2062989d7f)

![image](https://github.com/user-attachments/assets/b2f6e86d-b544-4893-9dd5-905a0b498f6a)
