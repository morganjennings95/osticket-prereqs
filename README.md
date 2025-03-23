<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create Azure Account (free or paid)
- Create Resource Group 
- Create Virtual Machine (be sure to match region you selected within your resource group)
  - System Size of 2 Virtual CPUs Recommended
  - Confirm Windows 10 Licensing
  - Confirm and Create VM
- Locate VM Public IP Address and Log in Via Remote Desktop (Using credentials you assigned during vm setup)

<h2>Installation Steps</h2>

![image](https://github.com/user-attachments/assets/150f66b9-e350-4260-a579-83e00e770d13)

<p>
Upon logging in, select No for all privacy settings as they are not necessary for the ticketing system setup
</p>
<br />

![image](https://github.com/user-attachments/assets/89c27cf0-a0ed-45cc-a342-93da81033fd7)

<p>
https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD
  Using this hyperlink, open browser window and download file to begin OS Ticket setup, Unzip files onto desktop
<br />

![image](https://github.com/user-attachments/assets/edfa6adf-7fe2-4214-b327-3c4d82d2570a)

<p>
In Control Panel, open "Turn Windows features on or off" and select the check boxes as seen in the image under "Internet Information Services" click Okay once finished
</p>
<br />

![image](https://github.com/user-attachments/assets/5b3dcec2-c6dd-48e8-9996-188efbc0542c)

<p>
Open the OsTicket-Installation file folder and install both "PHPManagerForIIS-V1.5.0" & "rewrite_amd64_en-US"
</p>
<br />

![image](https://github.com/user-attachments/assets/de08e0a9-5dd2-46a3-abea-54493d96e009)

<p>
Create a file folder on your C-drive & name it "PHP" then extract "php-7.3.8-nts-Win32-VC15-x86" onto your newly created PHP file folder
</p>
<br />

![image](https://github.com/user-attachments/assets/d40607fc-eb4f-41a2-862c-9ac037031daa)

<p>
Install "VC_redist.x86"
</p>
<br />

![image](https://github.com/user-attachments/assets/69949d84-320c-4dba-8d91-f7a1d9bfe8f3) ![image](https://github.com/user-attachments/assets/a171ad2f-d311-4258-85a3-c166cfc98e8a) ![image](https://github.com/user-attachments/assets/bfa7d7b2-1c1d-40b1-b57e-89379e3d421b)

<p>
Install "MySQL 5.5.62-win32" select "typical" setup, launch the configuration wizard after install, and select "standard" configuration
</p>
<br />

![image](https://github.com/user-attachments/assets/562112f7-cb04-4b2c-93fb-0d764530db0e)

<p>
Be sure to note down your desired password, enter it and finish out the installation
</p>
<br />

![image](https://github.com/user-attachments/assets/0d82f6ce-410f-4fca-a16b-78c7a0a33368)

<p>
Open IIS as admin, windows search bar -> IIS (right click, run as administrator) -> Register new PHP version -> select the file above from the PHP file folder in the C-drive -> Okay
</p>
<br />

![image](https://github.com/user-attachments/assets/dff1ec2e-0f3c-4940-aa2f-453e6fd75be5)


<p>
Reload IIS by right clicking the highlighted section in the left column, stop (wait 3 seconds), start
</p>
<br />

![image](https://github.com/user-attachments/assets/32285b76-84a0-4877-9965-255eb20285d5)

<p>
Extract "osTicket-v1.15.8" from the Osticket-installation folder to the default location then, a new file window will open once complete, do not close it, Reload IIS stop then start service once more
</p>
<br />

![image](https://github.com/user-attachments/assets/dd67925c-552b-416e-9fe4-013b12d306eb)

<p>
Move the "upload" folder from the newly opened file window to windows(C) -> inetpub -> wwwroot and rename the folder to "osTicket" Reload IIS stop and start service once again
</p>
<br />

![image](https://github.com/user-attachments/assets/67530785-4992-44bd-bce2-d1d076036c9b)

<p>
While in IIS Manager, in the left column, expand sites -> default web site, select osTicket and in the right column click "Browse 80(http)" This will open your osTicket Installer
</p>
<br />

![image](https://github.com/user-attachments/assets/64138e06-7b1d-4c9a-80c0-90a5fc4ebb7d)

<p>
Return to IIS Manager as we will need to enable some additional extensions. Select the osTicket tab -> open PHP Manager -> scroll down to Extensions -> select "enable or disable an extension" and in the "Disabled content right click and enable (php_imap.dll) (php_intl.dll) & (php_opcache.dll)
</p>
<br />

![image](https://github.com/user-attachments/assets/28a3b18a-0e25-40aa-8409-3c8fb756b382) ![image](https://github.com/user-attachments/assets/4674328b-1594-4128-8d17-bf5ef351f8e1)


<p>
Re-open the osTicket Installer page and you will notice that some additional extensions have been enabled
</p>
<br />

![image](https://github.com/user-attachments/assets/f59535ff-a62a-4d7e-af8b-b563510b304d)

<p>
Open file explorer -> Windows(C) -> inetpub -> wwwroot -> osTicket -> include, rename "ost-sampleconfig.php" to "ost-config.php"
</p>
<br />

![image](https://github.com/user-attachments/assets/82292b95-8e89-494d-a539-7a8276a870ee)

<p>
Disable inheritance within the file. Right click ost-config.php -> properties -> security -> advanced -> disable inheritance -> Remove all inherited permissions from this object
</p>
<br />

![image](https://github.com/user-attachments/assets/88af77e8-bfea-452a-9538-5a6b34d17076)

<p>
Enable permissions for everyone. Add -> select a principal -> type "everyone" -> check names -> OK -> select "Full control" check box -> OK (As a general rule, you should never practice giving full permission to all users, however as this excercise is simply setting up a mock ticketing system to play around in, we will give ourselves full access in this sandbox environment)
</p>
<br />

![image](https://github.com/user-attachments/assets/f12e9461-bff5-48f6-b935-99ca61cae5af)

<p>
Back to osTicket, continue to setup and fill out information as desired, but do not click "Install now"
</p>
<br />

![image](https://github.com/user-attachments/assets/03d1e3e3-148b-4505-b8f9-8bc6922ca9b2)

<p>
From your osTicket-install file folder, select "HeidiSQL" file, accept and install, proceed with default settings and file locations. Finish -> skip
</p>
<br />

![image](https://github.com/user-attachments/assets/ffa2ecc6-cc56-4598-b8a3-12a59a9865d9)

<p>
Select "New" and fill in the password you selected when setting your "root" password in SQL from approximately step 8, select "open"
</p>
<br />

![image](https://github.com/user-attachments/assets/9ac6d3ed-fba3-4893-a777-6451ff73376d) ![image](https://github.com/user-attachments/assets/ea5f3d51-742c-4790-b7d8-28e00512526e)


<p>
Now we need to set up a new database called osTicket right click "Unnamed" -> Create new -> Database. Name the database exactly "osTicket" mind your capitalization
</p>
<br />

![image](https://github.com/user-attachments/assets/cd6056d7-2e45-46a4-960b-8544e8b970f6)

<p>
Return to your browser and finish filling out the Database Settings section and click install now
</p>
<br />

![image](https://github.com/user-attachments/assets/29234f7e-6330-4700-bbc6-6ac192b36924)

<p>
Congrats on installing your Open Source Ticketing system, you will locate your login URLs at the bottom of the page, I would recommend opening each of them in a new window and saving them as a bookmark to make navigating to them easier (The notable links are http://localhost/osTicket/scp/login.php and http://localhost/osTicket/) one is for end users and the other for admin login
