# Homelab: Creating a DC with AD on VM (in progress)

## Network Diagram

![This is an image](https://svgshare.com/i/gJb.svg)



## Requirements for Oracle VirtualBox
    https://www.virtualbox.org/wiki/End-user_documentation
    
    Visit Oracles website for documentation on the minimum and recommended specifications needed to run Oracle VirtualBox.
    
## Downloads Needed:
    https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise
    https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019
    https://download.virtualbox.org/virtualbox/6.1.32/VirtualBox-6.1.32-149290-Win.exe

## Download ISO's and Installing Oracle Virtual Box
    01. Navigate to the links provided in downloads needed.
    02. Copy and paste each link into the address of your preferred browser, I'm using Google Chrome.
    03. After completing all downloads open the installer for VirtualBox.
    04. Press next for every button in the installer and open VirtualBox when it finishes the installation.

## Create Windows Server 2019 Virtual Machine
    01. Click "New" in the VirtualBox window.
    02. Name: DC - Machine Folder: Default Type: Microsoft Windows - Version: Other Windows
    03. Memory Size: 4 GB
    04. Hard Disk: Create a virtual hard disk now
    05. Hard Disk File Type: VDI
    06. Storage on Physical Hard Disk: Dynamically Allocated
    07. File Location and Size: File: Default, Size: 20.00 GB
    08. The Virtual Machine with Windows Server 2019 has been created.
    09. Navigate to "Settings" in the Oracle VM VirtualBox Manager
    10. Select "Advanced" Shared Clipboard: Bidirectional, Drag'n'Drop: Bidirectional
    11. Select "System" Select "Processor" Processor(s): 4
    12. Select "Network" Select "Adapter 1" Enable Network Adapter, Attached to: NAT
    13. Select "Adapter 2" Enable Network Adapter, Attached to: Internal Network, Name: intnet
    14. Press OK and return to the VM Manager.
    
##  Install Windows Server 2019 Operating System
    01. Double-click the DC VM, click the folder and browse for the ISO for Windows Server 2019, select it.
    02. VirtualBox will start and Windows Server 2019 will begin installing. This may take some time.
    03. Windows Setup will appear and ask: Language: English, Time and Currency Format: English, Keyboard: US
    04. Press install now, select Windows Server 2019 Standard Evaluation (Desktop Experience)
    05. Accept the license agreements, select Custom: Install Windows only (advanced)
    06. Drive 0 Unallocated Space - This should be the drive selected for OS install. 
    07. This process will take some time and the PC will restart several times.
    08. Customize settings will appear. Username: Admin - Password: Password1
    09. Windows Server 2019 is now installed.
    
 ##  Install VirtualBox Guest Additions   
    01. In VM menu navigate to "Input" and select crtl+alt+del and enter your password.
    02. The server will begin starting up for the first time.
    03. In VM menu select "Devices" and choose: "Insert Guest Additions CD Image"
    04. Go to File Explorer, This PC, you will see the Guest Additions CD and run "VBoxWindowsAdditions-amd64"
    05. Continue through the prompt and select the option to reboot now.

 ## Configure Virtual Machine Server Network Adapters 
    01. In VM menu navigate to "Input" and select crtl+alt+del and enter your password.
    02. Select the Network icon in the bottom right corner of your screen, select network again.
    03. Select "Change Adapter Options", rename Ethernet to _INTERNET_ and rename Ethernet 2 to X_INTERNAL_X
    04. Right-click the start menu and select "System" choose "Rename this PC"
    05. Rename the PC to: DC
    06. Restart the PC and login to the PC.
    07. Open "Change Adapter Options" and right-click X_INTERNAL_X and choose properties.
    08. Double-click Internet Protocol Version 4 (TCP/IPv4)
    09. Input the following:
    10. IP Address: 176.16.0.1
    11. Subnet Mask: 255.255.255.0
    12. Preferred DNS Server: 127.0.0.1
    13. Press OK to apply the configuration.
    
 ## Install Active Directory Domain Services
    01. Open Sever Manager
    02. On the Server Manager "Dashboard" select "Add Roles and Features"
    03. Continue pressing next until you encounter "Select Destination Server" select "DC"
    04. In "Select Server Roles" checkmark: "Active Directory Domain Services" and select "Add Features"
    05. Choose the install button and wait until the installation has finished. This may take some time.
    
## Promote the Domain Controller
    01. In the "Dashboard" you will notice a yellow flag - click on the flag and select "Promote This Server To A Domain Controller".
    02. Under "Deployment Configuration" select the "Add A New Forest" radio button and for "Root Domain Name" input "mydomain.com"
    03. At the "Domain Controller Options" screen, for the "DSRM" password use: "Password1 - continue through and select "Install"
    04. Agree to restart, you will now notice a different username - it should be: "MYDOMAIN\Administrator", login to the VM.

## Creating the Dedicated Domain Administrator Account
    01. Click the Windows icon and select Windows Administrative Tools > Active Directory Users and Computers
    02. You should notice the domain you created on the left-panel: mydomain.com - right-click > Organizational Unit
    03. Name: _ADMINS_
    04. Since we're in a lab environment, we can uncheck the accidental deletion option.
    05. Right-click _ADMINS_ and create a new user. Fill out the New-Object User form, Logon Name should be first initial and last name. 
    06. For the password input: Password1 and uncheck changing password at the next logon and checkmark password never expires.
    07. You will now notice the account you just made will now show up in _ADMINS_
    08. Right-click the domain admin account and select properties, choose the MemberOf tab, select add, in the box below input: Domain Admins, apply it.
  
## Relogin with Domain Admin Account  
    
