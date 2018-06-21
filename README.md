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

RaspberryPi NAS]
comment = Pi Server
public = yes
writeable = yes
browsable = yes
path = /External
create mask = 0777
directory mask = 0777
public = yes

7. Restating the Samba :
sudo /etc/init.d/samba restart
