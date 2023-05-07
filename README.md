# NAS_Server_with_Raspberrypi_3
Step by Step Process of NAS (Network Attached Storage) Server With Raspberry Pi 3.
This NAS Server can be accessed from all computers and mobile devices connected with the same WiFi Network.

## Requirements:
1. Raspberry Pi 3
2. External Hard Drive
3. Micro SD Card (16GB above)
4. Ethernet Cable
5. WiFi Router

## System Architecture
![NAS Server Creation](https://user-images.githubusercontent.com/28311232/236661027-b13baeed-c699-426f-836e-fbfa2fd419f7.png)


## OS Burning on Raspberry Pi 3 Micro-SD card

1.   Download "raspbian-strech-lite.zip" from the following link.   
     https://howchoo.com/raspbian/raspbian-stretch-download#download-zip-file
     
2.   Extract the zip file then you will see  raspbian-stretch-lite.img  file.

3.   Format the Micro SD card using SD Card Formater Application. From here you can download SD card formatter.
     (https://www.sdcard.org/downloads/formatter/sd-memory-card-  formatter-for-windows-download/)
     
4.   Now, Burn the imag file on the SD card. You can use Win32DiskImager. (https://sourceforge.net/projects/win32diskimager/)


## System Setup according to Architecture

1.  Firstly, Make sure your router is connected with internet connection properly as raspberry pi will require internetconnection for it's upgradation. 
    Then, Connect all the necessary ecquipments as shown in system architecture.
    

##  Inside raspbian-stretch-lite 

1. After booting up Login  as  
     User:  pi  
     Passsword: raspberry
2. Execute the following commands serially 

Update all the Repositories:

sudo apt-get update   (make sure internet is connected)

### NTFS Package :

sudo apt-get install ntfs-3g

Samba Package Installation:
sudo apt-get install samba samba-common-bin

Creating a directory in root:

sudo mkdir /External

sudo mount /External
 
 
     
