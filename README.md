<p align="center">
<img src="https://i.imgur.com/KzJbWRS.png" height="50%" width="50%" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This demonstration outlines the prerequisites and installation of the open-source help desk ticketing system "osTicket" within a Microsoft Azure virtual machine.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machine)
- Microsoft Remote Desktop
- Internet Information Services (IIS)
- MySQL / Heidi SQL
- osTicket: Support Ticketing System

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- MacOS

<h2>List of Prerequisites</h2>

- Microsoft Azure basic fundamentals (<a href="https://github.com/terikaj/azure-begin">Demo</a>)
- Azure Virtual Machine running Windows OS
- Installation Files within VM (<a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Download All</a>):
  - <a href="https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view">PHP Manager for IIS v1.5.0</a>
  - <a href="https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view">Rewrite Module</a>
  - <a href="https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view">PHP v7.3.8 NTS</a>
  - <a href="https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view">Microsoft Visual C++ Redistributable</a>
  - <a href="https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view">MySQL v5.5.62</a>
  - <a href="https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe">HeidiSQL v12.3.0.6589</a>

<h2>Installation Steps</h2>

<h3>&#9312; Creating and Connecting to a Microsoft Azure Virtual Machine</h3>

- Create a "Resource Group".
- Create a "Virtual Machine" running Windows 10 OS with adequate hardware to sustain computational operations.
  - _This example uses a Virtual Machine named `osTicket-VM`, with the username `ostuser`, Size `4 vCPUs`_
- Connect to the Virtual Machine using Microsoft's Remote Desktop Connection (RDP).

_If you're unsure of how to do this, please click the prerequisite link, refer to <a href="https://github.com/terikaj/azure-begin?tab=readme-ov-file#-connect-to-the-virtual-machine-via-remote-desktop">THIS PAGE</a>_
<hr>

<h3>&#9313; Enabling Windows Features inside of the Virtual Machine</h3>

- Before installing any file on the virtual machine:
  - Click the Windows Key/Button, then search for "Turn Windows Features on or off /Control Panel".
<p align="center">
<img width="500" alt="Screen Shot 2024-04-05 at 1 14 13 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/3c409211-0510-4b78-9bab-208adeeb47e8">
<img width="350" alt="Screen Shot 2024-04-05 at 1 16 21 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/4e2033e1-2e09-4bfa-bdb2-7c946378d61d">
</p>

- Find "Internet Information Services", then click the checkbox ☐ to enable it (should now have a small black box in the middle, NOT a checkmark).
  - Then, expand the folder by clicking the [+] button next to it.
- Expand "Application Development Features", then checkmark "CGI".
- Expand "Common HTTP Features", then checkmark ALL boxes.
- Click "OK" to apply changes.
<p align="center">
<img width="350" alt="Screen Shot 2024-04-05 at 1 19 02 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/6ab04000-f5c7-4e1a-a4d4-64ea07136ceb">
<img src="https://i.imgur.com/FYHztm2.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

_With those changes applied, we'll need to confirm if they are working._
- Open Microsoft Edge browser (or any other browser).
- On the address bar, type in "127.0.0.1", then ENTER.

_This should take you to the "Internet Information Services" page, which confirms the features are working._
<p align="center">
<img width="450" alt="Screen Shot 2024-04-05 at 1 22 20 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/985d0c40-a261-4a40-a41a-6ec52f383702">
</p>
<hr>

<h3>&#9314; Installing osTicket: Support Ticketing System</h3>

_Now we must install the prerequisite files onto the virtual machine to allow osTicket to run correctly._ </br>
_You can download all necessary files <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">HERE</a>_, or download them individually while following this demo.</br>
_(Download within the Virtual Machine by copying the link to Microsoft Edge or Google Chrome!)</br>_
_You can right-click the .zip file, click "Extract All...", then "Extract"._
<p align="center">
<img width="1268" alt="Screen Shot 2024-04-05 at 1 29 52 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/d57cdd17-1316-4155-afcc-7fa7193af6ff">
</p>

- On the virtual machine, first install <a href="https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view">PHPManagerForIIS_V1.5.0.msi</a> (PHP Manager for IIS).
- When the installation prompt appears, click "Next" > Select "I Agree" and "Next" > After installation, "Close".
<p align="center">
<img width="509" alt="Screen Shot 2024-04-05 at 1 31 40 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/7a1f81c3-6dee-43e5-a5fd-f313eb54ead2">
<img width="512" alt="Screen Shot 2024-04-05 at 1 32 43 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/40723fd0-8a75-44ae-8ec3-c0e0f4b2dc12">
</p>

- Next, install <a href="https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view">rewrite_amd64_en-US.msi</a> (Rewrite Module)
- When the installation prompt appears, click the checkbox to Agree the terms > click "Install" > After installation, "Finish".
<p align="center">
<img width="506" alt="Screen Shot 2024-04-05 at 1 33 45 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/176355b7-a4da-4750-8d17-e692d38e5b29">
</p>

_Next we'll have to create a directory for the following installation:_
- Open the `C:\` drive in "Windows Explorer".
- Right-click on an empty space and select to "New" > "Folder" to create a blank folder.
- Rename the folder to "PHP".
  - _Right-click the new folder and select "Rename", or softly double-click it to allow renaming_
<p align="center">
<img width="874" alt="Screen Shot 2024-04-05 at 1 35 46 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/9cd37bec-a7e1-41bb-b5a8-25bb5f25a351">
</p>

- Download <a href="https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view">php-7.3.8-nts-Win32-VC15-x86.zip</a> (PHP)
  - _You'll notice the file is contained in a .zip file. We'll have to extract the contents from it before using._
- Right-click on the .zip file > click "Extract All..." > "Browse" > Find and select the PHP folder in C:\ > "Extract".
  - _Or you can simply type it in the box if you already know the path name._
<p align="center">
<img width="804" alt="Screen Shot 2024-04-05 at 1 42 47 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/dc09cae4-9fbc-4283-8c47-88197f2c799a">
<img width="961" alt="Screen Shot 2024-04-05 at 1 44 52 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/370325f4-68e8-4aa0-8c77-3de69bb66bbd">
<img width="326" alt="Screen Shot 2024-04-05 at 1 50 06 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/d802237a-eeee-487e-ae8c-60553148e2be">
</p>

- Install <a href="https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view">VC_redist.x86.exe</a> (Microsoft Visual C++ Redistributable).
- Agree to the License Terms and Conditions, then click "Install".
- Once completed, click "Close".
<p align="center">
<img width="493" alt="Screen Shot 2024-04-05 at 1 51 15 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/35753212-5493-47d4-adc6-0dbf47314bea">
</p>

- Next, install <a href="https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view">mysql-5.5.62-win32.msi</a> (MySQL v5.5.62).
- Agree to the License Agreement, then click "Next".
- Click "Typical".
- Next click "Finish".
<p align="center">
<img width="507" alt="Screen Shot 2024-04-05 at 1 53 10 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/ec35376f-fbe5-4dbf-9b94-59a68da4ecfe">
<img width="509" alt="Screen Shot 2024-04-05 at 1 54 18 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/4c8d9d1f-f346-4167-a02c-a33c6658766a">
<img width="502" alt="Screen Shot 2024-04-05 at 1 55 32 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/4b8c7aaa-65b7-4538-9568-9ce1a66d7087">
<img width="507" alt="Screen Shot 2024-04-05 at 1 56 40 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/bd08cb62-6512-4a05-8176-323f7783ee3c">
</p>

- Another window prompt will appear, click "Next".
- Click "Standard Configuration", then "Next" twice (leaving everything as default).
- Create a password of your choice for the root login, click "Next".
- Click "Execute" to start the configuration process.
- Once completed, click "Finish".
<p align="center">
<img width="511" alt="Screen Shot 2024-04-05 at 1 58 07 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/9d360d76-84b8-4afb-83c6-be3973423f33">
<img width="512" alt="Screen Shot 2024-04-05 at 1 59 26 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/1223e30b-e075-41d7-b732-0c86407e8bd6">
<img width="513" alt="Screen Shot 2024-04-05 at 2 01 34 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/d1a1c5bb-97ee-4242-bb0e-2d9b5a973065">
<img width="515" alt="Screen Shot 2024-04-05 at 2 02 51 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/ffe87161-682c-48a2-9353-0da191dea78b">
<img width="517" alt="Screen Shot 2024-04-05 at 2 03 37 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/8e4cabfe-7e20-4062-86e1-1fbe3448d782">
</p>
<hr>

<h3>&#9315; Register PHP within IIS</h3>

- Press the Windows Key/Button to search for "Internet Information Services (IIS) Manager", then "Run as Administrator".
- Double-click "PHP Manager".
- Under PHP Setup, click on "Register new PHP version".
- Click the 3-dots to the right of the window"..." to browse for `php-cgi.exe`, located inside the PHP folder on the C:\ drive.
- Once you find it, click "Open" (or double-click the file), then "OK".
<p align="center">
<img width="566" alt="Screen Shot 2024-04-05 at 2 07 54 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/a4bdb66e-9e41-4111-9278-19b552fe4ed1">
<img width="1174" alt="Screen Shot 2024-04-05 at 2 11 13 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/e8c27128-7ae5-48b9-8a7b-0e44ce7c1555">
<img width="1173" alt="Screen Shot 2024-04-05 at 2 12 54 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/25f2833a-1782-4390-8cb9-89f4810c79e1">
<img width="777" alt="Screen Shot 2024-04-05 at 2 15 53 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/955c4e80-27d7-4b2c-9269-636badf67220">
<img width="520" alt="Screen Shot 2024-04-05 at 2 20 39 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/192eac87-944a-4335-9dd6-44a5bc6439ed">
</p>
<hr>

<h3>&#9316; Installing osTicket: Support Ticketing System</h3>

_Now we're ready to install osTicket!_
- Download <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">osTicket-v1.15.8.zip</a> (osTicket).
  - Open the .zip file (no need to extract all).
- Open another File Explorer window and navigate to **C:\inetpub\wwwroot**.
- Click and Drag the `upload` folder in the .zip file into wwwroot folder (this will automatically extract that specific folder).
- Rename `upload` to `osTicket`.
<p align="center">
<img width="1530" alt="Screen Shot 2024-04-05 at 2 28 17 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/8ce5eb6a-fb03-4c74-8669-d8e6001a13d7">
</p>

- Return to IIS.
  - On the left sidebar, click "osTicket-VM".
  - Then, on the right sidebar, click "Restart".
<p align="center">
<img width="1171" alt="Screen Shot 2024-04-05 at 2 31 00 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/96c6a591-7b35-4fad-a128-73a5e63832f2">
</p>

- On the left sidebar, click the dropdown arrow beside "Sites", same thing with "Default Web Site", then click "osTicket.
  - _The icons in the center window should change._
- On the right sidebar, click "Browse *:80 (http)".
  - This will open a new tab on Microsoft Edge to the osTicket Installer page.
<p align="center">
<img width="1171" alt="Screen Shot 2024-04-05 at 2 34 29 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/5dbffd07-db37-4bc5-81df-2180f71dc93b">
<img width="1103" alt="Screen Shot 2024-04-05 at 2 36 49 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/3da86a12-4526-4920-8dfc-a2f3089f537c">
</p>

_Note that some of the recommended extensions are not enabled, so we will address this:_
- Return to IIS, located under osTicket folder on the left sidebar, double-click "PHP Manager".
- Under PHP Extensions, click "Enable or disable an extension".
<p align="center">
<img width="1158" alt="Screen Shot 2024-04-05 at 2 39 48 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/39ab1177-2386-4ade-bfb2-7ecf9b63ebf3">
<img width="938" alt="Screen Shot 2024-04-05 at 2 41 38 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/e73d7009-e3a3-4015-86f7-18d9fbf36607">
</p>

- Find the following listed below, then click "Enable" on the right sidebar:
  - php_imap.dll
  - php_intl.dll
  - php_opcache.dll
- Refresh the osTicket webpage to observe the changes.
  - _APCu Extension & Zend OPcache Extension should be the only two with a Red X._
<p align="center">
<img width="950" alt="Screen Shot 2024-04-05 at 2 43 58 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/7a3f29f8-6480-4235-a5bc-f167024d1efc">
</p>

- Return to the wwwroot folder in File Explorer.
  - Navagate to **...wwwroot\osTicket\include**.
  - Find `ost-sampleconfig.php`, and Rename it to `ost-config.php` (essentially removing the word sample).
<p align="center">
<img width="934" alt="Screen Shot 2024-04-05 at 2 47 53 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/ffa7a2a5-ae3f-4691-aa65-d4cc898d868d">
</p>

_For demonstration purposes, we are going to temporarily give every user the permissions to access the `ost-config.php` file._
- Right-click the file and select "Properties".
- Click the "Security" tab at the top, then click "Advanced" at the bottom for special permissions.
<p align="center">
<img width="418" alt="Screen Shot 2024-04-05 at 2 49 37 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/ce391c6b-00c4-4f09-b3e9-296d0b3c57d6">
<img width="523" alt="Screen Shot 2024-04-05 at 2 50 58 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/02ce8e2f-d935-4ed3-af3c-7977f20d4093">
</p>

- Next, click "Disable inheritance".
- When the prompt appears, click "Remove all inherited permissions from this object".
  - _The middle box should no longer have any principals, so we'll need to add one that includes everyone._
- Click "Add".
<p align="center">
<img width="868" alt="Screen Shot 2024-04-05 at 2 54 20 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/3b1e9d33-eb58-4df1-9123-899b16e6f65a">
</p>

- At the top, click "Select a principal".
- In the object name box, type in "everyone", then click "Check Names" (it should automatically assign it to **Everyone**).
- Press "OK", then click the checkmark to enable "Full Control".
- Press "OK" until all properties windows are closed.
<p align="center">
<img width="943" alt="Screen Shot 2024-04-05 at 2 57 20 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/5a95ab66-f660-431f-a31c-fdbf94936f32">
</p>

_Now we can continue setting up the osTicket installation._
- Install <a href="https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe">HeidiSQL v12.3.0.6589</a> (Heidi SQL).
  - Accept the agreement, then keep clicking "Next", then "Install".
  - Once done, click Finish to launch the program.
<p align="center">
<img width="612" alt="Screen Shot 2024-04-05 at 3 01 26 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/f2680b1d-45ef-4e3d-9d62-1bae03726806">
<img width="616" alt="Screen Shot 2024-04-05 at 3 02 41 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/f5bb212b-4459-42bc-95f2-7f7f6efb0602">
<img width="613" alt="Screen Shot 2024-04-05 at 3 03 39 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/3c7c5247-c177-4ee1-aea5-e87c1754305d">
</p>

- In HeidiSQL, click "New" at the bottom left.
- Enter the username **"root"**, and the password you created when installing MySQL.
- Click "Open".
<p align="center">
<img width="705" alt="Screen Shot 2024-04-05 at 3 05 02 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/1b2132af-a375-447b-a2b1-9a432c797f9b">
</p>

- Right-click "Unnamed" on the left sidebar.
  - Select "Created new" > "Database".
- Type in the name "osTicket", then click "OK".
<p align="center">
<img width="965" alt="Screen Shot 2024-04-05 at 3 10 07 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/fecb6cca-8595-4758-bea8-dda3a0e7412f">
</p>

- Return the osTicket Installation webpage, click "Continue".
- Under System Settings section:
  - Create a Helpdesk Name of your choice (this example uses **OST Help Desk**).
  - Create a Default Email of your choice (this example uses **ost@helper.com**).
- Under Admin User section, create the appropriate credentials of your choice (example below):
  - **First Name:** ost
  - **Last Name:** user
  - **Email Address:** ostuser@email.com
  - **Username:** ostuser
  - **Password:** Password1
- Under Database Settings section:
  - Enter MySQL Database name that was created in HeidiSLQ (**osTicket**).
  - Enter MySQL Username (default is **root**).
  - Enter MySQL Password (Password you created when installing MySQL).
- Once completed, click "Install Now".
  - _You should then be sent to a Congratulations! page, if no errors._
<p align="center">
<img src="https://i.imgur.com/1GQbv9n.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img width="1075" alt="Screen Shot 2024-04-05 at 3 15 19 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/be6415cd-93b0-47a3-a6cf-c879123321fa">
</p>
<hr>

<h3>&#9317; Clean Up</h3>

- Return to File Explorer and navigate to "C:\inetpub\wwwroot\osTicket\".
- Find and Delete the `setup` folder.
<p align="center">
<img width="854" alt="Screen Shot 2024-04-05 at 3 18 14 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/0cb5eef2-14d5-43f4-b025-2989cce9edd3">
</p>

_Now we need to reset the permissions of the `ost-config.php` file to read-only to prevent any accidental edits._
- Navigate to "C:\inetpub\wwwroot\osTicket\include".
  - Right-click on `ost-config.php` file, then select "Properties".
  - Select "Security" tab, click "Advanced".
  - Select "Everyone" principal in the center box, then click "Edit".
  - Uncheck "Full Control", "Modify", and "Write".
  - Press "OK", "Apply", then "OK" to close the window.
<p align="center">
<img width="912" alt="Screen Shot 2024-04-05 at 3 24 47 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/613eead5-c5e5-4d41-9ac2-2ad14796aa1b">
<img width="758" alt="Screen Shot 2024-04-05 at 3 26 26 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/1962b812-f705-4842-89b3-cf57b7038050">
</p>
<hr>

<h3>&#9318; Testing The Login Services</h3>
Help Desk Login Page: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></br>
End User Ticket Page: <a href="http://localhost/osTicket/">http://localhost/osTicket/</a>

- Copy the URLs and open them in Microsoft Edge.
<p align="center">
<img width="1695" alt="Screen Shot 2024-04-05 at 3 32 56 PM" src="https://github.com/TerikaJ/osticket-prereqs/assets/136477450/45c5f541-6fff-4a86-99e6-e0a3cfc5f96d">
</p>
<hr>

<h1><p align=center> DONE! Good Job! </p></h1>

<h2><p align=center>The Next Demonstration:<br><a href="https://github.com/terikaj/post-install-config">Post-Installation Configuration</a></p></h2>

<p align=right>Please delete & clean up your Azure resources when finished!<br>
If you're unsure of how to do this, please click <a href="https://github.com/terikaj/azure-begin">HERE</a>

