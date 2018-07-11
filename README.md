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
* Choose a server size: $5/mo will be fine 
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
* Type "root" as the login/username.
![Example-Root](https://imgur.com/S0fcGzm.png)
***

***Step 4***
* Copy the root password from the VULTR server page.

![Example-RootPass](https://i.imgur.com/JnXQXav.png)
***

***Step 5*** 
* Paste the password into the Putty terminal by right clicking (it will not show the password so just press enter).
![Example-RootPassEnter](https://imgur.com/65jWobg.png)
***

***Step 6***

* Once you have hit enter it will open a security alert (click yes).
![Example-RootPassEnter](https://imgur.com/x7ILFUy.png)

***Step 7***
* Paste the 2 codes below into the Putty terminal then press enter after each one (it will just go to a new line)
![Example-RootPassEnter](https://imgur.com/dDbHPnt.png)

`wget https://raw.githubusercontent.com/NLXionaire/nullex-nav-installer/master/nullex-nav-installer.sh`

`sudo chmod +x nullex-nav-installer.sh`

***

***Step 8***
* Paste the code below into the Putty terminal then press enter

![Example-Bash](https://imgur.com/iOSuHgl.png)

`sudo sh nullex-nav-installer.sh`

***

***Step 9***
* Sit back and wait for the install (this will take a few mins)
***

***Step 10***
* After the install is complete, scroll up a little bit in the terminal, you will need this info for your cold wallet. 
![Example-installing](https://imgur.com/WQC4FO5.png)

***Step 11***
* Make sure you save your genkey as well, it will be right above the info in Step 10.
![Example-installing](https://imgur.com/NZCHCfp.png)

***Step 12***
* Keep this terminal open as we will need the info for the wallet setup.
***

## Section D: Preparing the Local Wallet

***Step 1 (if neccessary)***
* Download and install the NulleX wallet [here](https://github.com/white92d15b7/NLX/releases/tag/1.3.3-NEW)
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
* Send EXACLY 50,000 NulleX to the receive address within your wallet that was generated in Step 3.  Do not send any extra for fees, the wallet will automatically add that to the total.
***

***step 5***
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
***

# Section E: Connecting & Starting the NAV

***Step 1***
* Go to the tools tab within the wallet and click open "masternode configuration file" 

![Example-create](https://i.imgur.com/COsfvfA.png)
***

***Step 2***
* Start a new line at the bottom, and make it look like the example on the above line, but with your info.
* 'Alias' 'VPS IP Address:Port' 'Genkey' 'TxHash' 'Output Index' 
* For `Alias` type something like "MN01" **don't use spaces**
* The `Address` is the IP and port (43879) of your server (this will be in the Putty terminal that you still have open).
* The `GenKey` is your masternode GEN key (This is also in the Putty terminal that you have open).
* The `TxHash` is the transaction ID/long key that you copied to the text file.
* The `Output Index` is the 0 or 1 that you copied to your text file.
![Example-create](https://i.imgur.com/9b1I3bk.png)

* Click "File Save"
***

***Step 3***

* Go to the tools tab within the wallet and click open "wallet configuration file" and enter the info from Section C, Step 10.
![Example-create](https://imgur.com/WQC4FO5.png)
***

***Step 4***
* Close out of the wallet and reopen wallet
* Go to the debug console within the wallet, type the command below and press enter

'startmasternode alias false 'your NAV alias'`

![Example-console](https://i.imgur.com/6NM7G9a.png)

![Example-console](https://imgur.com/86XpkOc.png)
***
***

***Step 5***
* Check the status of your NAV within the VPS by using the command below:

`/usr/local/bin/NulleX/nullex-cli masternode status`

*You should see ***status 4 or 9***

If you do, congratulations! You have now setup a NAV. If you do not, please contact support on Discord or Telegram and they will be happy to assist you.


This guiide was created by a community member.  NulleXReb.  If it has helped you in anyway, made your day, or was the clutch in getting your Array running drop the guy some rewards @ 

NLX- AdoZ9zYgequjf7KttfLyj7ucyrBigh937T

BTC- 1Eiu35Eb8AUCp8BzVNjUKd7tPXWrP96hQM


