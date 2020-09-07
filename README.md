# Tor scripts
A collection of shell and bash scripts to interact with Tor on Linux, written by me (Roy Kienjet).
If you have a question about the scripts or a request for a script, you can send an email to rkienjet@protonmail.com and I will happily help you out.

## Mandatory prerequisites and information for all scripts
- First of all, make sure you've researched how to use Tor safely.
- Next, Tor should be installed on your system.
- For most of the scripts you will probably need to have superuser access. I recommend using `sudo`, because it's much safer then using Tor as root.
- Apart from these prerequisites, every script will have their own prerequisites listed that need to be present in order to use the script.
- Every script will have it's raw download command linked here, so that you easily download the script seperately with a one-liner.
- All scripts must be made executable after downloading them. This can be done with `$ sudo chmod +x`

### New Circuit (newcircuit);

**Purpose:**<br>
This _bash_ script can be used to easily request a clean Tor circuit. Additionally, you can choose to clear the DNS Cache and/or route all your commands through the new circuit. Your new torsocks ip will be shown after the new circuit request is fullfilled.

**Prerequisites:**
- Netcat needs to be availlable for this script to run.
- You alse need to have set a Tor connection password<sup>**!**</sup>.

**Usage:**
- Once you've downloaded the script from this repository one way or another and browsed into the folder, you can run it using<br>```$ sudo ./newcircuit```.
- The script will ask you to enter your Tor authentication password. Enter it and press enter to continue.
- The following things will be sent respectively to port 9051 of 127.0.0.1 (localhost), where Tor is listening: 
  1. The Tor authentication password you entered after running the script.
  2. _(If you chose to clear the DNS Cache: the signal to clear the DNS Cache.)_
  3. The signal to request a new circuit.
  4. The signal to close the netcat connection to the Tor port.
- The new socket ip will be retirieved and shown onto the screen.
- Next, Enter _y_ if you want to torify your shell, so that all your shell commands will be routed through the Tor circuit, or _n_, if you don't want to do that.
- If you chose _y_ and everything went well, you will now see the following text:<br>
```Tor mode activated. Every command will be torified for this shell.```<br>
If you want to keep your shell torified even after closing it and/or rebooting, check out my _torifiedshell_ script in this repository.
- The script will now automatically close.<br>

<br><sup>**!**</sup>**In case you have _not_ set one yet, you can use my *setpasswd* script from this repository to set a password for your Tor connection**

**Raw download:**<br>
```$ wget https://raw.githubusercontent.com/rkienjet/torscripts/master/newcircuit```

### Set Password (setpasswd);

**Purpose:**<br>
This _shell_ script sets the Tor connection authentication password to whatever the user wants it to be.

**Prerequisites:**
- A strong password. I highly recommend using a password manager like [KeePass](https://keepass.info/) or [1Password](https://1password.com/).

**Usage:**
- Once you've downloaded the script from this repository one way or another and browsed into the folder, you can run it using<br>```$ sudo ./setpasswd```.
- You will be asked to enter your new Tor password.
- When you've done so and if everything went as it's supposed to, you will see your the HashedControlPassword and on the other line the ControlPort 9051. These two lines are  supposed to be present in the /etc/tor/torrc configuration file. You can check this by using the following command:
```$ tail -2 /etc/tor/torrc```

**Raw download:**<br>
```wget https://raw.githubusercontent.com/rkienjet/torscripts/master/setpasswd```

### Always Torified (alwaystor)
**Purpose:**<br>
A really simple oneliner, but a usefull one. It adds one line to the .bashrc. This line makes sure your shell is always torified unless you turn it off, even after rebooting and/or closing the shell.

**Prerquisites:**
- None

**Usage:**
- Once you've downloaded the script from this repository one way or another and browsed into the folder, you can simpky run it using<br>```$ sudo ./alwaystor```.

**Raw download:**<br>
```wget https://raw.githubusercontent.com/rkienjet/torscripts/master/alwaystor```
