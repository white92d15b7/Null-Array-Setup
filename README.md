![NulleX-Logo](https://pbs.twimg.com/media/DhAvsGDX0AAZJ92.jpg)
# Nullex Null Array Verifier (NAV) Guide (Ubuntu 16.04)
This guide will assist you in setting up a NulleX NAV on a Linux Server running Ubuntu 16.04. (Use at your own risk)

If you require further assistance contact the support team on [Discord](https://discord.gg/6q7VWpN) or [Telegram](https://t.me/joinchat/ICJpaEhYCYtqic9X1KM7Ew)

***
## Requirements
1) **50,000 NulleX coins per NAV**
2) **VPS running Linux Ubuntu 16.04**
(Vultr is what's used in my guide, but you are free to use whatever you want)
3) **Windows local wallet**
4) **An SSH client such as [Putty](https://www.putty.org/)**
***
## Contents
* **Section A**: Creating the VPS within [Vultr](https://www.vultr.com/?ref=7473052).
* **Section B**: Downloading and installing [Putty](https://www.putty.org/).
* **Section C**: Connecting to the VPS and installing the NAV script via Putty.
* **Section D**: Preparing the local wallet.
* **Section E**: Connecting & starting the NAV.
***

## Section A: Creating the VPS within [Vultr](https://www.vultr.com/?ref=7473052) 
***Step 1***
* Register at [Vultr](https://www.vultr.com/?ref=7473052)
***

***Step 2***
* After you have added funds to your account go [here](https://my.vultr.com/deploy/) to create your server
***

***Step 3*** 
* Choose a server location (preferably somewhere close to you)
![Example-Location](https://i.imgur.com/ozi7Bkr.png)
***

***Step 4***
* Choose a server type: Ubuntu 16.04
![Example-OS](https://i.imgur.com/aSMqHUK.png)
***

***Step 5***
* Choose a server size: $5/mo will be fine 
![Example-OS](https://i.imgur.com/UoGoHcM.png)
***

***Step 6***
* Enable IPv6 and Private Networking  ***(there is a different cmd listed below for those using IPv4)***
![Example-OS](https://imgur.com/EYhmnUx.png)
***

***Step 7*** 
* Set a Server Hostname & Label (name it whatever you want)
![Example-hostname](https://i.imgur.com/uu0rvOr.png)
***

***Step 8***
* Click "Deploy Now"

![Example-Deploy](https://i.imgur.com/4qpYuH0.png)
***


## Section B: Downloading and Installing Putty

***Step 1***
* Download Putty [here](https://www.putty.org/)
***

***Step 2***
* Select the correct installer depending upon your operating system. Then follow the install instructions. 

![Example-Putty Installer](https://imgur.com/wqfWyvg.png)
***


## Section C: Connecting to the VPS & Installing the NAV Script via Putty

***Step 1***
* Copy your VPS IP (you can find this by going to the server tab within Vultr and clicking on your server. 
![Example-Vultr](https://i.imgur.com/z41MiwY.png)
***

***Step 2***
* Open the Putty application and fill in the "Host Name" box with the IP address of your VPS.
![Example-PuttyInstaller](https://imgur.com/WffwFYW.png)
***

***Step 3***
* Once you have hit enter it will open a security alert (click yes).
![Example-RootPassEnter](https://imgur.com/x7ILFUy.png)
***

***Step 4***
* Type "root" as the login/username.
![Example-Root](https://imgur.com/S0fcGzm.png)
***

***Step 5***
* Copy the root password from the VULTR server page.

![Example-RootPass](https://i.imgur.com/JnXQXav.png)
***

***Step 6*** 
* Paste the password into the Putty terminal by right clicking (it will not show the password so just press enter).
![Example-RootPassEnter](https://imgur.com/65jWobg.png)
***

***Step 7***

***WARNING- IF YOU HAVE ALREADY RUN THE INSTALL SCRIPT, AND YOU ARE JUST UPDATING IT, MAKE SURE TO STOP YOUR WALLET BEFORE RUNNING THE FOLLOWING COMMANDS.***

* Before we start the NAV install we are going to make sure Ubuntu is up to date with the 3 commands below.  Run each command separately, when promted choose 'Y' and hit Enter.

`apt-get update`

`apt-get upgrade`

`apt-get dist-upgrade`

***

***Step 8***
* Adduser to secure your VPS, by adding a new username so you aren't running everything as root.  
* Run the command below and use a username that you want associated with this server ***('nullexnav1' is an example, you need to use your own username).***  

`adduser nullexnav1`

* You will then need to make a new password associated with your new username.  Hit 'Enter' for the next 5 lines after your new password has been set, then 'Y' to save your information.

![Example-Bash](https://imgur.com/mrhihrj.png)

* The final step is granting sudo permissions for your adduser.  Run the command below to activate this setting ***('nullexnav1' is an example, you need to use your username).***

`usermod -aG sudo nullexnav1`

* Now you will close your Putty terminal and log back with your new username and password that we made above.  

![Example-Bash](https://imgur.com/FUFkEFu.png)

* ***KEEP YOUR NEW USERNAME AND PASSWORD IN A SAFE PLACE.  THIS WILL BE HOW YOU LOG IN FROM NOW ON.***
***

***Step 9***

***YOU ONLY NEED TO RUN THESE 2 COMMANDS IF IT'S A NEW INSTALL.  IF YOU ARE JUST UPDATING A PREVIOUS INSTALL, YOU ONLY NEED TO RUN THE COMMAND IN STEP 10.***

* Paste the 2 codes below separately into the Putty terminal then press enter after each one (it will just go to a new line)

`wget https://raw.githubusercontent.com/NLXionaire/nullex-nav-installer/master/nullex-nav-installer.sh`

`sudo chmod +x nullex-nav-installer.sh`

![Example-RootPassEnter](https://imgur.com/dDbHPnt.png)

***

***Step 10***
* Paste the code below into the Putty terminal then press enter.  ***(THE BELOW COMMAND WILL ALSO BE USED FOR ANY UPDATES THAT ARE MADE TO THE SCRIPT.  YOU WILL JUST RUN THIS SINGLE COMMAND, AND NOT THE 2 ABOVE.  THEY ARE ONLY FOR THE INITIAL INSTALL.)***

`sudo sh nullex-nav-installer.sh`

![Example-Bash](https://imgur.com/iOSuHgl.png)

***NOTE*** ***(DO NOT RUN THIS COMMAND IF YOU'VE ALREADY RUN THE ONE ABOVE)

The above cmd will install using IPv6 by default. If you are only going to be setting up a single NAV, and you prefer to use IPv4 instead you can force the install to use your IPv4 IP address by using  

`sudo sh nullex-nav-installer.sh -N 4`

***

***Step 11***
* Sit back and wait for the install (this will take a few mins).  You will need a txt file to save info from Step 10.
***

***Step 12***
* After the install is complete, scroll up a little bit in the terminal.  
![Example-installing](https://imgur.com/WQC4FO5.png)
***

***Step 13***
* Save this info in the txt file that we made earlier, you will need this info for your cold wallet.  Genkey is the same as 'masternodeprivkey'.
![Example-installing](https://imgur.com/bJACITk.png)
***

***Step 14***
* Keep this terminal open as we will need the info for the wallet setup, but you also have this info saved in the txt file that we just made.
***

## Section D: Preparing the Local Wallet

***Step 1 (if neccessary)***
* Download and install the NulleX wallet [here](https://github.com/white92d15b7/NLX/releases/tag/v1.3.4)
***

***Step 2***
* Create a text document to temporarily store information that you will need. 
***

***Step 3***
* Go to the debug console within the wallet, type the command below and press enter.
* NAV1 is used as an example, name your NAV whatever you want.

`getaccountaddress <NAV1>`

![Example-console](https://i.imgur.com/6NM7G9a.png)
***

***Step 4***
* Send EXACLY 50,000 NulleX to the receive address within your wallet that was generated in Step 3.  Do not send any extra for fees, click ***Choose*** (right next to ***Transaction Fee***) and check the box for ***Send as zero-fee transaction***.

![Example-console](https://imgur.com/FBVOnyA.png)
***

***Step 5***
* Go to the debug console within the wallet 

![Example-console](https://i.imgur.com/6NM7G9a.png)
***

***Step 6***
* Type the command below and press enter 

`masternode outputs` 

![Example-outputs](https://i.imgur.com/GD7Ro1m.png)
***

***Step 7***
* Copy the long key (this is your transaction ID) and the 0 or 1 at the end (this is your output index)
* Paste these into the text document you created earlier as you will need them in the next step.

![Example-outputs](https://imgur.com/Z9lsQyd.png)
***

# Section E: Connecting & Starting the NAV

***Step 1***
* Go to the tools tab within the wallet and click open "masternode configuration file" 

![Example-create](https://i.imgur.com/COsfvfA.png)
***

***Step 2***
* Start a new line for each NAV at the bottom, and make it look like the example on the last line of existing info, but with your info.

 `'Alias' 'VPS IP Address:Port' 'Genkey' 'TxHash' 'Output Index'` ***(Do not use a # at the beginning)***

* For `Alias` use the one you made for ***Section E: Step 4***
* The `VPS IP Address:Port` is the IP from ***Section C: Step 1*** and the dedicated Port is ***43879***.
* The `GenKey` is your masternode genkey from ***Section C: Step 11***.
* The `TxHash` is the transaction ID/long key that you copied to the text file from ***Section D: Step 6 and 7***.
* The `Output Index` is the 0 or 1 that you copied to your text file from ***Section D: Step 6 and 7***.

![Example-create](https://imgur.com/tMkdY7h.png)
* Click "File Save"
***

***Step 3***
* Go to the tools tab within the wallet and click open 'wallet configuration file' and enter the info from ***Section C, Step 10***.
![Example-create](https://imgur.com/7XENqin.png)
***

***Step 4***
* Check the status of your VPS wallet to make sure it's on the same block as your controller wallet.

`/usr/local/bin/NulleX/nullex-cli getmininginfo`

![Example-console](https://imgur.com/B4Wk0in.png)
***

***Step 5***
* Close out of the controller wallet and reopen it
* Unlock your wallet to start your NAV
* Go to the debug console within the wallet, type the command below and press enter

`startmasternode alias false YOUR-NAV-ALIAS`

![Example-console](https://i.imgur.com/6NM7G9a.png)

![Example-console](https://imgur.com/86XpkOc.png)
***

***Step 6***
* Check the status of your NAV within the VPS by using the command below in Putty terminal:

`/usr/local/bin/NulleX/nullex-cli masternode status`

* You should see ***status 4 or 9***

![Example-console](https://imgur.com/W1ZAMTk.png)

If you do, congratulations! You have now setup a NAV. If you do not, please contact support on [Discord](https://discord.gg/6q7VWpN) or [Telegram](https://t.me/joinchat/ICJpaEhYCYtqic9X1KM7Ew) and they will be happy to assist you.
***

This guide was created by a community member.  ***NulleXReb***.  If it has helped you in anyway, made your day, or was the clutch in getting your Array running drop the guy some rewards @ 

NLX- AdoZ9zYgequjf7KttfLyj7ucyrBigh937T

BTC- 1Eiu35Eb8AUCp8BzVNjUKd7tPXWrP96hQM


