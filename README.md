# NAS-Raspberrypi-
using rasbian NAS

1. Samba Server Installation:
sudo apt-get install samba samba-common-bin

2. NTFS Package :
sudo apt-get install ntfs-3g

3. List connected disk:
lsblk

4. Creating a directory in root:
sudo mount /dev/sda1 /External

5. Configuring samba:
sudo gedit /etc/samba/smb.conf

6. put following code in file
   NOTE - a)If you want just to access only External drive
          b)In case If you want to access Raspberrypi's internal storage and other storage
          
 a. If you want just to access only External drive
 
RaspberryPi NAS]
comment = Pi Server
public = yes
writeable = yes
browsable = yes
path = /External
create mask = 0777
directory mask = 0777
public = yes


b. In case If you want to access Raspberrypi's internal storage and other storage :

[global]
netbios name = RP2
server string = The Pi File Center
workgroup = WORKGROUP
hosts allow =
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
remote announce =
remote browse sync =

[HOMEPI]
path = /home/pi
comment = No comment
browsable = yes
read only = no
valid users =
writable = yes
guest ok = yes
public = yes
create mask = 0777
directory mask = 0777
force user = root
force create mode = 0777
force directory mode = 0777
hosts allow =

[EXTERNAL DRIVE]
path = /External
comment = No comment
browsable = yes
read only = no
valid users =
writable = yes
guest ok = yes
public = yes
create mask = 0777
directory mask = 0777
force user = root
force create mode = 0777
force directory mode = 0777
hosts allow =



7. Restating the Samba :
sudo /etc/init.d/samba restart


8. If you want it to run on each boot :
      		  i) create a executable file as follows:

  		     sudo gedit /usr/bin/zz.sh

                     and paste the code
                     
                   #!/bin/bash
		    sudo /etc/init.d/samba restart

		  ii)Change permission to executable as:

   		   sudo chmod +x /usr/bin/zz.sh

                  iii) Reboot the device

			sudo reboot

NOTE- since external drive is mounted after the boot,you will not be able 
      to acess hdd/external storage.
      After each boot you have to mount external storage. 
      so run this command in terminal after boot up

	sudo mount /dev/sda1 /External

9. Open This PC / My_Computer and click on Network in LHS below. You'll see RP2


    					**ENJOY**
