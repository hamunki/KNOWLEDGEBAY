Virtualbox
==========

#### Install Virtualbox Guest Additions / Extension Pack
https://techpiezo.com/linux/download-and-install-virtualbox-guest-additions-in-ubuntu/

#### Install the virtual CD image
`sudo apt update`  
`sudo apt install virtualbox-guest-additions-is`o

#### Mount
`Menu->Device->Insert Guest Additions CD Image`   

Install from mounted CD (not a real CD the virtual one that shows on the desktop)  
`cd /media/<user-name>/VBox_GAs_X.X.X/`  

`sudo sh VBoxLinuxAdditions.run`  

### Extension Pack

#### Install the same version of Extension pack as the version of VirtualBox
Current version from here:  
https://www.virtualbox.org/wiki/Downloads%20  
Old versions from here:  
https://www.virtualbox.org/wiki/Download_Old_Builds  
Install in VirtualBox Preferences:  
`File->Preferences (Ctrl+G)`  
![ExtensionPack](../../media/VBX01)


#### Add user to vbox group:
`sudo usermod -a -G vboxusers <USER>`

