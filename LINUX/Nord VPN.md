NordVPN
=======

#### Installing Nord VPN Linux

`sh <(curl -sSf https://downloads.nordcdn.com/apps/linux/install.sh)`

> Note: If you do not have a curl package, evidenced by the  
> fact that the above does not work, you can alternatively use this command:  
> `sh <(wget -qO - https://downloads.nordcdn.com/apps/linux/install.sh)`  

Additionally, if you receive the following issue:  
`Whoops! Permission denied accessing /run/nordvpn/nordvpnd.sock`

all you need to do is write the following command: 

`sudo usermod -aG nordvpn $USER`

and then reboot your device.

#### Logging into NordVPN in Terminal

Run the nordvpn login command on your Linux device.
Open the provided link in any browser.
Complete the login procedure.
Right-click on the "Continue" button and select "Copy link address".
Run `nordvpn login --callback "URL"` with the previously copied URL. Please note that the URL must be surrounded by quotation marks "".
Verify that login was successful with nordvpn account.
Sharing files with Nord VPN Meshnet

Send:

`nordvpn set meshnet on`

`nordvpn meshnet peer list`

`nordvpn fileshare send <peer ip> </path/to/your/file>`

Receive:

`nordvpn fileshare list --incoming`

`nordvpn fileshare accept <id>`