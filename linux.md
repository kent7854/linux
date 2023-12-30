# Mounting a remote smb drive

Needed to mount a drive from my NAS to a linux machine. This happened to be a VM in Proxmox (Debian) but it shouldn't matter that it was a VM.

The issue I kept running into was that it would often make root the owner of the mount and then I couldn't write to it from most (if not all) software programs.

In the end assigning the uid and gid values of the user in the command worked.

You use the command id to get the information about the user.

In the below code that worked the uid and gid were both 1000, and the user was kent

I was connecting to the NAS so the IP and the folders were for that.

I was also in the base directory that had the final mount folder in it so I didn't need the full reference to that.

sudo mount -t cifs -o username=kent,uid=1000,gid=1000 //192.168.86.147/Movies/MKV MKV

That mounted the MKV folder in the NAS to the MKV folder under my username account in Linux.

