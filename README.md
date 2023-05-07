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

After booting up Login  as  
     
     User:  pi  
     Passsword: raspberry
     
Execute the following commands serially 

### Update all the Repositories:
     sudo apt-get update   (make sure internet is connected)

### NTFS Package :
     sudo apt-get install ntfs-3g

### Samba Package Installation:
     sudo apt-get install samba samba-common-bin


### Creating a directory in root :
     sudo mkdir /External

### Check all the connected drives and mount the specific one:
     lsblk
     sudo mount /dev/sda1 /External    
(Here /dev/sda1 is the External HDD part)

### Configuring samba 
     sudo nano /etc/samba/smb.conf
 
Go inside the file and at the bottom the file type 


          [RaspberryPi NAS]
          comment = Pi Server
          public = yes
          writeable = yes
          browsable = yes
          path = /External
          create mask = 0777
          directory mask = 0777
     
### Restating the Samba :
    sudo /etc/init.d/samba restart


## Access from Windows Computer

1. First Connect the desired computer with same WiFi network.
2. Go to Network Discovary and Enable Device Discovery.
3. Go to  "Turn Windows features on or off" and check the following box
![SMB](https://user-images.githubusercontent.com/28311232/236664246-fe01249e-74be-45d1-bc55-7a79c4b73647.png)
4. Then Restart Your Computer. Again bring the computer within the same WiFi Network. Hopefully, this will work.
![Network Discovery](https://user-images.githubusercontent.com/28311232/236664739-449a7571-4626-4765-bb86-65fd90ea502e.png)


## Access from  Android Mobile

1. First Connect the Android Mobile with same WiFi network.
2. Go to File Manager.

3. Find Remote option.

![file_manager_1](https://user-images.githubusercontent.com/28311232/236665364-96072093-8bb4-481c-a309-7da740e37016.jpeg)

4. Add Remote Device, Select SMB LAN

![fm2](https://user-images.githubusercontent.com/28311232/236665374-d00262ec-d125-43e4-84a2-65cdc884eec7.jpeg)

5. Login through following credentials.

               User:  pi  
               Passsword: raspberry
 
 Here it Goes!
 
 ![WhatsApp Image 2023-05-07 at 2 08 11 PM](https://user-images.githubusercontent.com/28311232/236665683-1455e941-4b24-44a3-9dbc-97f468d98c36.jpeg)
