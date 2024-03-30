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

The first thing you want to do is make a resource group in Azure. 
On your Azure Portal go to Create resource group.
I like to keep things organised so I will call this resource group "osTicket-lab".
Choose Your Region. 
Then click create resource group. 

<img width="1440" alt="Screenshot 2024-03-29 at 20 58 20" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/98077935-7253-4994-932c-7413bef26d37">

Next Go to your Azure Portal and Click Create Virtual Machine. 
I will name mine 'osTicketVM' and put it in the "osTicket-lab" resource group. 
For the image section we will be using a windows 10 virtual machine. 
<img width="1440" alt="Screenshot 2024-03-29 at 21 13 53" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/8d6e5682-32f6-4042-b25f-c0f1201542bf">

There are a few key steps to keep in mind here. 

1.Firstly Make Sure that your virtual machine is in the same region as your resource group. 

2. Second Ensure that the size of your virtual machine is adequate. 
It must have at 2vcpus! 
This is an important step. I experienced a lot of problems during this stage because I picked a machine that only have 1vcpu at first. 
My Virtual Machine was so slow to the point of it being unusable.

3. Finally when creating the VM, allow it to make a new Virtual Network or "Vnet".

STEP 2: Log On To Your Virtual Machine 

First off copy your Virtual Machine's public address. 
<img width="1440" alt="Screenshot 2024-03-29 at 21 25 10" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/09ca4af8-c967-4346-81ff-69cbe3e0ebe0">

We will paste this into a remote desktop software.

If you are on a mac you can use the app "microsoft remote desktop"
Windows Users can you the program remote desktop connection. 
<img width="473" alt="Screenshot 2024-03-29 at 21 27 58" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/302debc6-ac41-4025-8ae8-deda8c23492e">

Using the user name and password you made on Azure log onto your virtual machine.
<img width="439" alt="Screenshot 2024-03-29 at 21 29 16" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/4daa1bb6-733c-455e-acf4-5aeec8314b63">

If you found this part difficult it's probably because you made a difficult username and password. 
Remember guys KISS. Keep it simple stupid. 

STEP 3: Set Up & Configure IIS

Bring up your control panel and go to programs. 
From there click turn windows features on/off. 
<img width="1123" alt="Screenshot 2024-03-29 at 21 45 53" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/7b913287-9b4e-4a04-bf4e-aa337ce2c608">

Look for IIS which stands for internet information services. 
Check the ISS box.
Expand World Wide Web Services. Then Expand Application Development features then check CGI.
Expand ISS and check everything under comman HTTP features.
After all of that click 'ok' to install the web server.
<img width="416" alt="Screenshot 2024-03-29 at 21 44 45" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/cf9c8921-b28f-4c91-bbe6-fbd30a4cc5e3">

STEP 4: Test The Server 
Type in 127.0.0.1 in a web browser.
You should see a page like the screenshot down below. 
If It didnt work restart the ISS section you might have checked the wrong boxes for that section. 
<img width="1440" alt="Screenshot 2024-03-29 at 21 50 19" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/54b3c012-0ca0-4ea5-b349-3e06cce70472">

STEP 5: Lots of Installation files. 
From the installation folder I made start install things in this order. 

Download and install PHP manager for IIS. File name: PHPMangerForIIS_V1.5.0.msi
Download and install Rewrite Module. File name: rewrite_amd64_en-US.msi 

Go to your C drive and create a folder called PHP
<img width="499" alt="Screenshot 2024-03-29 at 22 07 03" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/5a19a644-798a-41cf-9db2-9d5271f0127d">

Download and Install PHP 7.3.8 and extract it's content into the PHP folder in the C drive. 
<img width="609" alt="Screenshot 2024-03-29 at 22 10 14" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/6978f6ef-87fe-472f-89f4-a4e43e58d8a2">

Another installation.... 

Download and install the VC_redist.x86.exe file. 

ONE MORE INSTALLATION... atleast for this step. 

Download and install the MySQL5.5.62 file. 
Some important things to note when installing this file. 
Choose typical setup.
<img width="497" alt="Screenshot 2024-03-29 at 22 13 14" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/98cf3776-4351-4e8b-b9c3-21035c9d1af3">

Click finish and Launch the configuration wizard.
<img width="495" alt="Screenshot 2024-03-29 at 22 13 50" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/c5b72ed6-9830-43eb-bd9a-81aa0f3f80d2">

Click standard configuration
<img width="495" alt="Screenshot 2024-03-29 at 22 19 00" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/bb8c41b6-9473-4305-9326-6a3252ffdd8f">

For this next section the my sequel username will automatically be root. 
You can choose whatever password you want. 
My password will be Password1 because like I said before keep it simple stupid. 
Especially doing this long setup process the last thing you want to do is forget your password and have to start it all over again. 
What my sequal is doing is installing a database on your virtual machine for osTicket to use. Osticket will need a database for all of the users, tickets and user permissons data. 

Step 6: Back To IIS
Go to your start menu and run ISS as an adminstrator. 
<img width="321" alt="Screenshot 2024-03-29 at 23 22 38" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/71b61a63-ed0b-43b1-9a76-7a06095f7968">

Click on PHP manager
<img width="1024" alt="Screenshot 2024-03-29 at 23 23 36" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/d01199ea-745f-4ec9-94e0-52fe882e9145">

Then Register new PHP manager
<img width="1024" alt="Screenshot 2024-03-29 at 23 24 01" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/9af829b8-982b-4337-9d7a-dd810b1da0a1">


Then We will need to find the PHP folder we made on the C drive earlier and select the \php-cgi.exe file. 
<img width="707" alt="Screenshot 2024-03-29 at 23 25 33" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/6b458abf-c273-4b78-978a-987e485a8486">

Finish installation.
<img width="507" alt="Screenshot 2024-03-29 at 23 29 55" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/748c9e77-8524-426d-b8ad-d4abd7a20159">

STEP 7: Install osTicket 

Download the osticket file in the listed resources folder.
Click on it and you'll see a folder called "upload". 

<img width="841" alt="Screenshot 2024-03-29 at 23 42 50" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/dad95ce7-02c9-478e-ba33-ef545275abef">

We are going to drag that folder to the directory c:\inetpub\wwwroot
Then we will rename the "upload" file to "osTicket".
Please ensure you write it exactly like this with no spaces. 
If it is written different to this there will be an error message later on in the installation which may result in you having to start the process all over again. 

<img width="658" alt="Screenshot 2024-03-29 at 23 43 39" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/89df9876-e9ff-4620-897d-757b11117e84">

Reload the IIS and restart it. 

<img width="1434" alt="Screenshot 2024-03-30 at 13 03 26" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/c3dfe0e0-ebbc-4b83-b0e3-416333f54123">

STEP 8: Check osTicket 
Go to ISS > sites > default > osTicket > browse *80
You should see a screen like the image below 

<img width="1434" alt="Screenshot 2024-03-30 at 13 03 49" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/87e7a3fe-342b-4c9e-9dd8-c032d90c0a68">

Step 9: Enable IIS Extensions 
Go To PHP manager 
Click on enable or disable an extension

Enable: php_imap.dll 
Enable: php_intl.dll
Enable: php_opcache.dll

<img width="1434" alt="Screenshot 2024-03-30 at 13 11 55" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/27d2cedd-aa53-47d7-a184-f1d1d4114344">

Make sure all of these are checked to avoid issues later. 

Refresh osTicket in the browser and you should see that these extentions are now ticked

<img width="1434" alt="Screenshot 2024-03-30 at 13 12 22" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/5cebe41a-4101-427a-8936-6bd7632c6720">

Step 10: Setup ost-config.php file
Go to C-drive > inetpub > wwwroot > include
Then find the ost-sampleconfig.php file 

<img width="791" alt="Screenshot 2024-03-30 at 13 15 45" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/70fbf2a4-adb8-40ba-80fa-b32c626a6b1e">

Rename this file by removing the word sample.

<img width="791" alt="Screenshot 2024-03-30 at 13 19 02" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/8cefec6a-08dd-412c-aec6-e77064af5e6a">

This file is important because the osTicket installer needs to interact with this file to allow users to have permissions to interact with osTickets functions

Right click the file go to properities > security > advanced > disable inheritance.
<img width="364" alt="Screenshot 2024-03-30 at 13 24 01" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/06209fd7-c2f8-4f62-be42-7d55cca34f4b">
<img width="364" alt="Screenshot 2024-03-30 at 13 24 21" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/024678fb-9a9a-4f90-a83f-6f3225881f27">
<img width="770" alt="Screenshot 2024-03-30 at 13 24 51" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/2b2b2b28-d09b-4806-8e73-cac0132394f3">

Then we will click remove all permissions.
<img width="524" alt="Screenshot 2024-03-30 at 13 25 14" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/3e1c8ae7-155f-4688-98cb-f4f3b259ea82">

Then click add 

Set principle

<img width="901" alt="Screenshot 2024-03-30 at 13 27 37" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/24e01fc6-d9a9-4b90-9435-e67feb4557b9">

You see a box at the bottom with the description "enter the objects name to select". 
In this box write "everyone".

Then click check names and press ok to finish this process.

For now we will be giving everyone permissions to use this file.
Check the "full control box" to do this. 

<img width="901" alt="Screenshot 2024-03-30 at 13 34 35" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/8445eb9f-1339-4cc5-9fd1-218451bc2a9c">


Then click ok > apply > ok > ok to finish this process 

STEP 11: Continue setting up osticket 

We are almost done now. 

Go to your browser with osticket loaded and click continue.
Enter in all of the personal detials till you get to the mydatabase section. 
Be sure to note down all of this information to avoid trouble with logging in later.
<img width="821" alt="Screenshot 2024-03-30 at 13 42 54" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/26505883-3f7c-478e-9d2d-1f0b91343b25">

Step 12: Set up a database on our Virtual machine

To do this we have to install Heidi SQL
<img width="598" alt="Screenshot 2024-03-30 at 13 48 19" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/2e205ae9-0e60-433d-910d-c364f02ef676">

Once you have finished the intial installation you'll see a screen like the one below.
<img width="598" alt="Screenshot 2024-03-30 at 13 48 40" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/3d588f78-3015-4180-8fa7-6e1792bec740">

Click new then type in your password from before. 
<img width="685" alt="Screenshot 2024-03-30 at 13 50 42" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/f070a6fe-75f5-4150-962d-e33c24490915">

Click open and you would have finished the connection to the my sequal server.

Step 11: Finish setting up osTicket on your browser

Type in your user name "root" and the password you picked into the database settings on your browser. 

We will next need to make an osticket database on Heidi SQL
<img width="916" alt="Screenshot 2024-03-30 at 13 54 43" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/4bd9858d-3177-4511-bbc2-65fee87a86f5">

Right click unnamed them create new. 
<img width="916" alt="Screenshot 2024-03-30 at 13 58 01" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/080ea93c-791e-4bbc-9ddb-2164e2044a14">
<img width="916" alt="Screenshot 2024-03-30 at 13 58 22" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/8ff03445-5aef-41c5-a944-04cd1cd9ad99">

Name the database osticket then click ok.
<img width="318" alt="Screenshot 2024-03-30 at 14 00 23" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/3a08c976-a0fa-4f4c-9d63-2b4a7a3f7601">

Go back to your browser and click install 
<img width="817" alt="Screenshot 2024-03-30 at 14 02 06" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/84326257-ce69-4105-b612-bc4b3021d22b">

and boom!!! You've set up osTicket

<img width="814" alt="Screenshot 2024-03-30 at 14 03 01" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/56328caa-6e5f-400e-9a93-02c3354c7c05">

STEP 12: Clean up

Delete the setup folder located in C:\inetpub\wwwroot\osTicket\setup 
<img width="800" alt="Screenshot 2024-03-30 at 14 06 44" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/05499ef6-aa78-4971-b0a3-5ca7aefffaf2">

Next we are going to change back the permission settings on the ost-config.php to read only
<img width="795" alt="Screenshot 2024-03-30 at 14 12 14" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/47ae638a-1f95-4283-bc8d-f7ae97376be8">

Right click the file > go to properties > security > advanced > go to everyone > edit > then uncheck everything besides read & execute and read. 
<img width="915" alt="Screenshot 2024-03-30 at 14 13 49" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/b3125c33-6b10-41f0-bbe7-3ec0c7bfd5a2">

With that done all we need to do now is test logging on.

STEP 13: TEST 

Using this link login using the password and username you made earlier: 
http://localhost/osTicket/scp/login.php 

Enter in your detials 
<img width="915" alt="Screenshot 2024-03-30 at 14 18 16" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/7e5285b8-4c25-4914-afdf-1fe4494a4473">


BOOM! COMPLETE! 
<img width="967" alt="Screenshot 2024-03-30 at 14 18 49" src="https://github.com/JospehAdetifa/osticket-prereqs/assets/165278529/f3e2ce32-b5b1-47e5-ab44-7e5a9551fffd">


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
