# osticket-prereqs
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
In this tutorial I will outline the prerequisites and installation of the open-source help desk ticketing system osTicket. I will give both written instructions and a video demonstration. From my experience reading a tutorial then going to watch a video tutorial after really helps deepen my understanding of new concepts. Feel free to follow this tutorial in which ever way suits you best. The process of setting up a ticketing system can be a bit overwhelming and confusing the first time. Don't let this discourage you. After going through this process a couple of times over I'm sure you'll find it very rewarding just like I did.

Something Important to note! You will need to have an Azure subcription to follow this tutorial. You can use the link below and get your first month for free with $200 of credit. https://azure.microsoft.com/en-gb/free.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Item 1
- Item 2
- Item 3
- Item 4
- Item 5

<h2>Installation Steps</h2>
STEP 1: Create Resource Group & Virtual Machine In Azure 
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The first thing you want to do is make a resource group in Azure. 
On your Azure Portal go to Create resource group.
I like to keep things organised so I will call this resource group "osTicket-lab".
Choose Your Region. 
Then click create resource group. 

Next Go to your Azure Portal and Click Create Virtual Machine. 
I will name mine 'osTicketVM' and put it in the "osTicket-lab" resource group. 
For the image section we will be using a windows 10 virtual machine. 

There are a few key steps to keep in mind here. 

Firstly Make Sure that your virtual machine is in the same region as your resource group. 

Second Ensure that the size of your virtual machine is adequate. 
It must have at 2vcpus! 
This is an important step. I experienced a lot of problems during this stage because I picked a machine that only have 1vcpu at first. 
My Virtual Machine was so slow to the point of it being unusable.

Finally when creating the VM, allow it to make a new Virtual Network or "Vnet".

STEP 2: Log On To Your Virtual Machine 

First off copy your Virtual Machine's public address. 
We will paste this into a remote desktop software.

If you are on a mac you can use the app "microsoft remote desktop"
Windows Users can you the program remote desktop connection. 

Using the user name and password you made on Azure log onto your virtual machine.

If you found this part difficult it's probably because you made a difficult username and password. 
Remember guys KISS. Keep it simple stupid. 

STEP 3: Set Up & Configure IIS

Bring up your control panel and go to programs. 
From there click turn windows features on/off. 

Look for IIS which stands for internet information services. 
Check the ISS box.
Expand World Wide Web Services. Then Expand Application Development features then check CGI.
Expand ISS and check everything under comman HTTP features.
After all of that click 'ok' to install the web server.

STEP 4: Test The Server 
Type in 127.0.0.1 in a web browser.
You should see a page like the screenshot down below. 
If It didnt work restart the ISS section you might have checked the wrong boxes for that section. 

STEP 5: Lots of Installation files. 
From the installation folder I made start install things in this order. 

Download and install PHP manager for IIS. File name: PHPMangerForIIS_V1.5.0.msi
Download and install Rewrite Module. File name: rewrite_amd64_en-US.msi 

Go to your C drive and create a folder called PHP

Download and Install PHP 7.3.8 and extract it's content into the PHP folder in the C drive. 

Another installation.... 

Download and install the VC_redist.x86.exe file. 

ONE MORE INSTALLATION... atleast for this step. 

Download and install the MySQL5.5.62 file. 
Some important things to note when installing this file. 
Choose typical setup. 
Click finish and Launch the configuration wizard.

Click standard configuration

For this next section the my sequel username will automatically be root. 
You can choose whatever password you want. 
My password will be Password1 because like I said before keep it simple stupid. 
Especially doing this long setup process the last thing you want to do is forget your password and have to start it all over again. 
What my sequal is doing is installing a database on your virtual machine for osTicket to use. Osticket will need a database for all of the users, tickets and user permissons data. 

Step 6: Back To IIS

Go to your start menu and run ISS as an adminstrator. 

Click on PHP manager

Then Register new PHP manager

Then We will need to find the PHP folder we made on the C drive earlier and select the \php-cgi.exe file. 

Finish installation.

STEP 7: Install osTicket 

Download the osticket file in the listed resources folder.
Click on it and you'll see a folder called "upload". 

We are going to drag that folder to the directory c:\inetpub\wwwroot


Then we will rename the "upload" file to "osTicket".
Please ensure you write it exactly like this with no spaces. 
If it is written different to this there will be an error message later on in the installation which may result in you having to start the process all over again. 

Reload the IIS and restart it. 

STEP 8: Check osTicket 
Go to ISS > sites > default > osTicket > browse *80
You should see a screen like the image below 

Step 9: Enable IIS Extensions 
Go To PHP manager 
Click on enable or disable an extension

Enable: php_imap.dll 
Enable: php_intl.dll
Enable: php_opcache.dll

Make sure all of these are checked to avoid issues later. 

Refresh osTicket in the browser and you should see that these extentions are now ticked

Step 10: Setup ost-config.php file
Go to C-drive > inetpub > wwwroot > include
Then find the ost-sampleconfig.php file 
Rename this file by removing the word sample.

This file is important because the osTicket installer needs to interact with this file to allow users to have permissions to interact with osTickets functions

Right click the file go to properities > security > advanced > disable inheritance.

Then we will click remove all permissions.

Then click add 

Set principle

You see a box at the bottom with the description "enter the objects name to select". 
In this box write "everyone".

Then click check names and press ok to finish this process.

For now we will be giving everyone permissions to use this file.
Check the "full control box" to do this. 

Then click ok > apply > ok > ok to finish this process 

STEP 11: Continue setting up osticket 

We are almost done now. 

Go to your browser with osticket loaded and click continue.
Enter in all of the personal detials till you get to the mydatabase section. 
Be sure to note down all of this information to avoid trouble with logging in later.

Step 12: Set up a database on our Virtual machine

To do this we have to install Heidi SQL

Once you have finished the intial installation you'll see a creen like the one below.
Click new then type in your password from before. 
Click open and you would have finished the connection to the my sequal server.

Step 11: Finish setting up osTicket on your browser

Type in your user name "root" and the password you picked into the database settings on your browser. 

We will next need to make an osticket database on Heidi SQL

Right click unnamed them create new. 

Name the database osticket then click ok.

Go back to your browser and click install and boom!!! You've set up osTicket

STEP 12: Clean up

Delete the setup folder located in C:\inetpub\wwwroot\osTicket\setup 

Next we are going to change back the permission settings on the ost-config.php to read only
Right click the file > go to properties > security > advanced > go to everyone > edit > then uncheck everything besides read & execute and read. 


With that done all we need to do now is test logging on.

STEP 13: TEST 

Using this link login using the password and username you made earlier: 
http://localhost/osTicket/scp/login.php  

Enter in your detials 


BOOM! COMPLETE! 





</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
