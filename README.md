# raspberrypi-NAS
Build your own NAS server using a Raspberry Pi Zero 2W using samba. Step-by-step tutorial for biginers.<br>
I will use `samba` for creating our NAS storage server.

---
# Setting up the Storage device
- Connect your raspberry pi zero 2w using the `ssh` command, `ssh username@<rpi IP>`.
- Connect an external storage device to the rpi and unmount it using `sudo umount <path to the device>` if it's auto mounted.
- Create a new directory and name it `storage` in the `/mnt` directory, `sudo mkdir /mnt/storage`
- Now mount the device to the directory we created above, `sudo mount /dev/sdb1 /mnt/storage`. (The device path can be different for you)

---
[Warning: In progress. Check out later...\]
