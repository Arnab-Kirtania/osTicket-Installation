![alt text][osticketlogo]

[osticketlogo]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/osticket.png "osTicket Logo"

# osTicket Installation Guide
Tutorial on how to install osTicket on a cloud virtual machine.

<h1>Environments and Technologies Used</h1>

* Microsoft Azure (Virtual Machines/Compute) <br>
* Microsoft Remote Desktop (RDP) <br>
* Internet Information Services (IIS) <br>

<h1>Operating Systems Used</h1>

* Windows 10 <br>

<h1>Necessary Files</h1>

* [Microsoft Azure](portal.azure.com)
* [osTicket Installation Files](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) (download these files directly onto your VM's desktop for an easier time)

<h1>Installation Steps</h1>

Using Microsoft Azure create a resource group called osTicket. After that create a virtual machine (VM) with 2-4 CPUs, we'll be using a VM in case there are any problems so we won't damage our local machine. <br>

![alt text][1]

[1]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/1.png "Microsoft Azure VM Page"

Connect to the VM via remote desktop protocol (RDP) with the login information you set up. If you are a Mac user you'll need to install RDP. <br>

![alt text][2]

[2]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/2.png "Remote Desktop Protocol"

Once connected to your VM we need to install some things such as Internet Information Services (IIS) and Common Gateway Interface (CGI). Search control panel -> Uninstall a program -> Turn Windows features on or off -> Select IIS, CGI, HTTP Redirection, and WebDAV Publishing.

![alt text][3]

[3]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/3.png "Windows Features"

After that, go to installation files and download PHPManagerForIIS_V1.5.0. After that quickly run through the installation of the program. <br>

![alt text][4]

[4]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/4.png "PHP Manager for IIS"

After that download and install rewrite_amd64_en-US from the installation files. <br>

![alt text][5]

[5]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/5.png "IIS URL Rewrite Module 2"

Next, go to Windows (C:) and create a new folder called PHP. After that download and unzip the contents of php-7.3.8-nts-Win32-VC15-x86 from installation files into your newly created PHP folder. <br>

![alt text][6]

[6]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/6.png "Creating a new PHP folder"

Next download and install VC_redsitx86 from installation files. <br>

![alt text][7]

[7]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/7.png "Microsoft Visual C++"

Next download and install mysql-5.5.62-win32. Go through the typical setup. <br>

![alt text][8]

[8]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/8.png "MySQL Server Setup"

Next, go through the Instance configuration wizard with the standard configuration. After that set the password. For this example, we'll set it to Password1, then hit execute. You can also open up a txt file with Notepad to write down your usernames and password throughout this process so you remember. <br>

![alt text][9]

[9]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/9.png "MySQL Server Instance Setup"

Next open up IIS as admin. <br>

![alt text][10]

[10]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/10.png "Opening IIS Manager as admin"

Double click PHP manager -> Register new PHP version -> go to PHP folder -> select php-cgi.exe. After that hit ok and restart the server.

![alt text][11]

[11]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/11.png "Registering a new PHP version"

Next download osTicket-v1.15.8 from installation files. Next, navigate to Windows (C:) > inetpub > wwwroot. Now double click the file you downloaded and move upload into wwwroot and rename it osTicket. <br>

![alt text][12]

[12]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/12.png "Moving upload into wwwroot and renaming it osTicket"

Next go back to the IIS Manager -> click osTicket -> click Browse *:80 (http) to see what we still need to install. <br>

![alt text][13]

[13]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/13.png "clicking Browse *:80(http)"

Go back to PHP manager and then click "Enable or disable an extension." Enable php_imap.dll, php_intll.dll, php_opcache.dll. Then refresh osTicket in your browser to see changes. <br>

![alt text][14]

[14]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/14.png "Enabling PHP extensions."

Next, go back to osTicket -> include -> then rename ost-sampleconfig to ost-config <br>

![alt text][15]

[15]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/15.png "Renaming ost-sampleconfig to ost-config"

Next, go into ost-config.php properties then disable inheritance and remove all, then set new permissions for everyone and then all. <br>

![alt text][16]

[16]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/16.png "Changing permissions"

Now hit continue and set up the basics of osTicket. Remember your default email address can't be the same as the admin email address. <br>

![alt text][17]

[17]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/17.png "Putting in basic information"

Now go back to installation files and install HeidiSQL. Then create a new session and make the password Password1. Then click open. <br>

![alt text][18]

[18]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/18.png "Creating a new HeidiSQL session"

Then create a new database called osTicket. <br>

![alt text][19]

[19]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/19.png "Creating a new SQL database"

Then type the info you need here in the installer, and then install. <br>

![alt text][20]

[20]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/20.png "Putting in SQL information"

Next, follow the instructions here. You can achieve most of this by deleting the setup folder from osTicket. Then go to os-ticket.php and change the permissions to remove write access. <br>

![alt text][21]

[21]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/21.png "Cleaning up files"

Finally, go to http://localhost/osTicket/scp/login.php and log in. Congratulations you have now successfully installed osTicket! <br>

![alt text][22]

[22]: https://github.com/Arnab-Kirtania/osTicket-Installation/blob/main/22.png "Logging into osTicket"

