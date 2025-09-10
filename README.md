# raspberrypi-NAS Personal Storage Server
Build your own NAS server using a Raspberry Pi Zero 2W using samba. Step-by-step tutorial for biginers.<br>
I will use `samba` for creating our NAS storage server.

---
# Setting up the Storage device
- Connect your raspberry pi zero 2w using the `ssh` command, `ssh username@<rpi IP>`.
- Connect an external storage device to the rpi and unmount it using `sudo umount <path to the device>` if it's auto mounted.
- Create a new directory and name it `storage` in the `/mnt` directory, `sudo mkdir /mnt/storage`
- Now mount the device to the directory we created above, `sudo mount /dev/sdb1 /mnt/storage`. (The device path can be different for you)

---

# Edit fstab file
- Get the `UUID` of the storage device by using the command: `sudo blkid /dev/sda1`. (change the path for your device).
- Add this line, `UUID=your_uuid  /mnt/storage  ext4  defaults,nofail  0  2`, to the `sudo nano /etc/fstab` file.
- This will ensure the storage is auto mounted and set-up after device reboots.

---
# Install samba
- Install `samba` from the bash shell, `sudo apt update && sudo apt install samba samba-common-bin -y`
## Edit smb.conf
- Before editing the `smb.conf` file create a backup for the original file: `sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak`.
- Copy and paste the `smb.conf` file in this repository. *(replace the <username> in the valid users line in the file)*
- Create a new user for SMB or use any existing user to set the password for the smb service and add it in valid users in the smb.conf file.
- Set the passowrd for the smb service using: `sudo smbpasswd -a <username>`.
- Change the ownership: `sudo chown -R 777 username:username /mnt/storage`
- Restart the services: `sudo systemctl restart smbd nmbd`

---
# Access Storage
- Press `Win+R` and type `\\<IPofRPI>\storage`. Press enter. (Example: `\\192.168.172.180\storage`).
- It will ask for the username and password for the SMB service.
- You can also access the storage from a browser, type the `\\<IPofRPI>\storage` in the address field.

---
# My YouTube tutorial
- Click [Storage Server](https://youtu.be/_ntcCw6miC4?si=GVUh6ID_Wf7r9Ptb) to view a step-by-step tutorial for this project.

---
# Issues
- For any issues check out the `Troubleshoot.txt` file in this repository.
- For other issues you can open up new Issue in this repository.
