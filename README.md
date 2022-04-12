# Homelab: Creating a DC with AD on VM

## Requirements for Oracle VirtualBox
    https://www.virtualbox.org/wiki/End-user_documentation
    
    Visit Oracles website for documentation on minimum to maximum specifications needed to run Oracle VirtualBox.
    
## Downloads Needed:
    https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise
    https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019
    https://download.virtualbox.org/virtualbox/6.1.32/VirtualBox-6.1.32-149290-Win.exe

## Downloading ISO's and Installing Oracle Virtual Box
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
    
##  Installing Windows Server 2019 Operating System
    
