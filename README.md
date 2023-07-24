# osTicket-Prereqs-Installation
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket - Prerequisites and Installation
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket. 


## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop 
- Internet Information Services (IIS)
- 
## Operating Systems Used

- Windows 10 (21H2)
</b>

## List of Prerequisites

1. [Create a virtual machine in Azure and access it using Remote Desktop](https://github.com/jontavioust/osTicket-Prereqs-Installation#create-a-virtual-machine-in-azure-and-access-it-using-remote-desktop)

2. [Access the required installation files](https://github.com/jontavioust/osTicket-Prereqs-Installation#access-the-required-installation-files) 
3. [Enable IIS and subsequent features in Windows VM](https://github.com/jontavioust/osTicket-Prereqs-Installation#enable-iis-and-subsequent-features-in-windows-vm)
4. [Download and install the required installation files](https://github.com/jontavioust/osTicket-Prereqs-Installation#download-and-the-install-the-required-installation-files)
5. [Setup osTicket](https://github.com/jontavioust/osTicket-Prereqs-Installation#setup-osticket)
6. [Access your osTicket helpdesk admin login and end-user page](https://github.com/jontavioust/osTicket-Prereqs-Installation#access-your-helpdesk-admin-login-and-end-user-page)
7. [Clean up your setup and permissions](https://github.com/jontavioust/osTicket-Prereqs-Installation#clean-up-your-setup-and-permissions)

## Installation Steps

### Create a Virtual Machine in Azure and Access it Using Remote Desktop
> **Note:**
> Using a virtual machine to host osTicket preserves resources on your personal machine. It also keeps it safe. 

https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/82c34051-02dc-44cd-b6da-41fce79d06cb
<p>
Name your VM "VM-osTicket" for best organizational practices. The region you choose is where your VM's physical reasources are located. Create a VM with a Windows 10 image and 4vCPUs for optimal proccessing speed. Set a usermae and password you will remember, this is how you will log onto the desktop. Creating a new VM in azure will automatically create a vnet (your VM's network) and a resource group (where your VM will be stored in Azure). Ensure RDP port 3389 is enabled, this is how you will access your VM's desktop. Make no changes on the Disk tab. On the Network tab observe your vnet and IP address. Ensure that the IP and NIC will delete when your VM is deleted. This prevents unwanted storage charges in Azure. Make no changes on the Management, Monitoring, and Advanced tabs. Review and create your VM. Wait for Deployment to finish. 
</p>

<br />
<img src="https://i.imgur.com/4JTyhmj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Ije8ot3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Copy VM-osTicket's public IP address and paste it in Remote Desktop Connection (Windows) or Microsoft Remote Desktop (MacOS). Give it a "friendly name" and log in with the username and password you configured. If using a Windows PC, your log in screen may look different. The functions are still the same. The VM's desktop will populate after a successful login. 
</p>
<br />

### Access the Required Installation Files
<img src="https://i.imgur.com/5pLrt83.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Copy and paste [this link](https://drive.google.com/drive/folders/1Jc9E6JWnnyLiUse49tfqYC4zGCkVRwSW?usp=drive_link)  within your Windows VM for easy access to the required instalation files.
<br />


### Enable IIS and Subsequent Features in Windows VM
<img src="https://i.imgur.com/A3a1kaA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Find IIS: Control Panel -> Programs and Features -> Turn Windows features on or off.
</p>
<br />
<img src="https://i.imgur.com/uEE2Soj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 
<p>In the Windows Features settings enable: [▪️]Internet Information Services -> [▪️]Web Management Tools -> [✔] IIS Management Console.
   
Enable CGI and Common HTTP features: [▪️]World Wide Web Services -> [▪️]Application Development Features -> [✔] CGI -> [▪️]Common HTTP Features.
 </p>
 
<br />

https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/5b498b8b-833a-4cdf-9b53-fe6f16a606da

<p>Verify IIS functionality with loopback address: Type 127.0.0.1 in Edge browser, the IIS welcome page will populate. </p>
<br />

    
### Download and the Install the Required Installation Files
>**Note:**
>This is the longest step, so each part is broken down for your convenience.

>**Warning:**
>Some of these installation files are out of date, however they are still functional (and free). Because of this, you may come across a stop message; "This file type might be dangerous". Download the files anyway. The isolated VM hosted in Microsoft Azure keeps your personal machine safe.

#### From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
<img src="https://i.imgur.com/fEPWtxq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

#### From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
<img src="https://i.imgur.com/uivGncD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

#### Create the directory C:\PHP
https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/1831cfc1-1c34-4aa3-a4f2-9761b01b1439
<p> This PC -> Windows (C:) Drive -> New Folder -> type "PHP". </p> 

#### From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP

https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/92286ab1-c6e0-46a3-8b16-c2224a6001ec
<p>Downloads -> Right click PHP 7.3.8 -> Extract all -> Browse to C:\PHP -> Select folder -> Extract.  </p>

#### From the Installation Files, download and install VC_redist.x86.exe.
<img width="706" alt="VC redist" src="https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/0bfe4a17-a228-4963-9f41-004a4f645931">

#### From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
<img width="848" alt="MySQL" src="https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/7443fd10-b770-475a-be0a-3436c9cc9074">


https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/3f15c657-62a2-483f-90ca-ad5e8615d2f3
<p>Typical Setup -> Launch Configuration Wizard (after install) -> Install as Windows Service -> Standard Configuration -> Modify Security Settings ->  Set a password you will remember -> Execute and finish installation. </p>

#### Run IIS as an admin & register PHP from within IIS
https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/fbcbd092-fc5d-427a-b658-1fc50faa7fcb
<p> Search IIS -> Run as administrator -> PHP manager -> Register new PHP version -> Provide a path to the php executable file (...) -> C:\php\php-7.3.8-nts-Win32-VC15-x86\php.cgi -> Open -> OK.</p>

#### Reload IIS (open IIS and restart the server)
<img width="204" alt="reload IIS" src="https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/feb407ff-ecf3-44cb-9f38-958a330aad3a">
<p>You can also click stop and then start.</p>

#### From the installation files, install osTicket v1.15.8
<img width="688" alt="downlaod osT" src="https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/886f8748-6552-4d5b-9133-aa74dc3e7ecf">
<p>The osTicket zip does not have an installation manager like the previous files. Access it from the Downloads section in the File Explorer.</p>

#### Copy, extract, and rename the "Upload" folder within osTicket zip
https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/4d5096ff-4161-45b0-b07a-272742b81c93
<p>Double click osTicket in Downloads -> Right click "upload" folder and copy -> Paste the "upload" folder in c:\inetpub\wwwroot -> After extraction, rename “upload” to “osTicket” within c:\inetpub\wwwroot.</p>

#### Launch osTicket in Microsoft Edge 
<img width="396" alt="Launch osT" src="https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/d6571a0b-781e-4652-85f2-f39e9556bf62">
<p> VM-osTicket -> Sites -> Default Website -> osTicket -> On the right, click “Browse *:80”. The osTicket installation page will populate in the Edge browser.</p>

> **Note:**
> If you receive an error in Edge, check to see if you properly [registered PHP from within IIS's PHP manager](https://github.com/jontavioust/osTicket-Prereqs-Installation#run-iis-as-an-admin--register-php-from-within-iis).  

#### Enable PHP extensions
https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/6c35aa76-de1a-4a45-accd-92600fa9bb3c
<p>After launching osTicket, notice that some extensions are disabled. The required extensions are PHP IMAP, Intl, and Zend OPcache. 
    
Enable extensions in IIS Manager: VM-osTicket -> Sites -> Default Website -> osTicket -> Double click PHP Manager -> Enable and disable an extension -> Enable: php_imap.dll, php_intl.dll, php_opcache.dll -> Refresh the osTicket site, observe the changes. </p>

#### Rename: ost-sampleconfig.php
https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/ba208a15-d350-4699-ac9e-aa3999a941bd
<p>From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php ➡️ To: C:\inetpub\wwwroot\osTicket\include\ost-config.php. (delete "sample"). 
    
>**Note:**
> Arrive at the file by clicking the relevant folders (like in the walk-through) or copy and paste the path name into File Explorer.</p>

#### Assign permissions to ost-config.php
https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/042fb3d9-4a48-4b46-a621-5090a116f54d
<p> Observe the file path to access C:\inetpub\wwwroot\osTicket\include\ost-config.php.ost-config.php. 
    
Assign permissions: Right click ost-config.php -> Properties -> Security -> Advanced -> Disable inheritance -> Remove all -> Add -> Select principal -> type "everyone" -> Check names -> OK -> [✔️]Full control -> OK -> Apply -> OK.
</p>  

#### From the Installation Files, download HeidiSQL. Install and begin a new session
<img width="903" alt="HeidiSQL" src="https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/a9f49948-4b92-4212-8ff6-0ddfb3ff95f6">

> **Note:**
> Heidi SQL may download as a word document. If so, open the document and click the link to download the file 

https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/831961e7-4af3-4806-9c50-bfd985eb8427
<p> Accept the agreement and let the installation manager guide you. 

After installation, the session manager will automatically populate: Click "➕New -> Right click to remane the new session "osTicket" -> observe that the MySQL database username is "root" -> Set a password you will remember. This database information is required to configure osTicket Basic Installation. </p>

<br />

### Setup osTicket 
<img width="535" alt="sysset:admin osTicket" src="https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/eb222462-2bfd-4652-98a0-92bd7857dd5f">
<p>In the browser, complete the System Settings and Admin User sections of osTicket Basic Installation. The Default Email receives email from end-users. The Admin User portion is how you will log into the helpdesk.</p>

<img width="556" alt="osT dadtabase" src="https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/694b9346-10e9-4cf9-a67d-55ea61374590">
<p> Scroll to the Database section. The MySQL database is "osTicket". The MySQL username is "root". Use the password you configured in HeidiSQL. Click: Install Now. </p>
<br />

### Access your Helpdesk Admin Login and End-user Page
<img width="838" alt="access ost admin:user" src="https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/8e183ae3-2d2a-49a6-a0d5-ec81a2011dd7">
<p>Verify that your admin login works.</p>
<br />

### Clean Up Your Setup and Permissions
<img width="537" alt="cleanup ost" src="https://github.com/jontavioust/osTicket-Prereqs-Installation/assets/101889571/0d1c8405-ee72-4b36-9e1d-3c1fface2823">
<p>Delete: C:\inetpub\wwwroot\osTicket\setup. 

Set Permissions to Read Only: C:\inetpub\wwwroot\osTicket\include\ost-config.php</p>
<br />

### osTicket - Prerequisites and Installation Complete!👏🏾
