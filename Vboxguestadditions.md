# My-Debian-setup


up vote
13
down vote
This works for me (Debian GNU/Linux 8 (jessie) 64-bit):

Login as root with terminal command su press Enter and then type your root password
Update your APT database with apt-get update
Install the latest security updates with apt-get upgrade
Install required packages with apt-get install build-essential
module-assistant
Configure your system for building kernel modules by running m-a
prepare
Click on Install Guest Additions… from the VirtualBox Devices menu
Run mount /dev/sr0 /media/cdrom
Run sh /media/cdrom/VBoxLinuxAdditions.run, and follow the instructions on screen.
shareimprove this answer
edited Nov 29 '16 at 10:13

cambunctious
1427
answered Mar 24 '16 at 11:26

menkow
23123
1	 	
Missing step between 6. and 7.: mount /dev/sr0 /media/cdrom – user11153 Oct 4 '16 at 7:32
  	 	
if you get an error that the mount point doesn't exist, create it: mkdir /media/cdrom – AndrewD Nov 16 '16 at 2:40
  	 	
The one that worked for me was: $su $apt-get update $apt-get upgrade $apt-get install build-essential module-assistant linux-header-$(uname -r) Click mount Guest Additions on virtualbox $sh /media/cdrom/VBoxLinuxAdditions.run – Esteban Nov 17 '16 at 4:27 
  	 	
I don't see any option that says "Install Guest Addition" on the Devices menu there is only "Insert guest addition CD image" – samayo Jan 17 at 19:44
  	 	
@samayo its just changed menu item name in new version of VirtualBox from "Install Guest Additions" to "Insert guest addition CD image" (imgur.com/a/9AVVC) – menkow Jan 18 at 22:01 
  	 	
Thanks. It worked when i did that – samayo Jan 19 at 6:35
add a comment
