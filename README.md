# Tor scripts
A collection of shell and bash scripts to interact with Tor, written by me.

## New Tor circuit;

**Purpose:**<br>
This simple _bash_ script can be used to easily request a clean circuit. Additionally, you can choose to clear the DNS Cache and/or route all your commands through the new circuit. Your new torsocks ip will be shown after the new circuit request is fullfilled.

**Usage:**
- Once you've extracted the script from this repository, you can run it using ```sudo ./tornc```.
- The script will ask you to enter your Tor authentication password. Enter it and press enter to continue.
- The following things will be sent respectively to port 9051 of 127.0.0.1 (localhost), where Tor is listening: 
  1. The Tor authentication password you entered after running the script
  2. _(If you chose to clear the DNS Cache: the signal to clear the DNS Cache)_
  3. The signal to request a new circuit
  4. The signal to close the connection to the Tor port
- The new socket ip will be retirieved and shown onto the screen. 
- Next, Enter _y_ if you want to torify your shell, so that all your shell commands will be routed through the Tor circuit, or _n_, if you don't want to do that.
- If you chose _y_ and everything went well, you will now see the following text:<br>
```Tor mode activated. Every command will be torified for this shell.```<br>
If you want to keep your shell torified even after closing it and/or rebooting, check out my _torifiedshell_ script in this repository.
- The script will now automatically close.<br>

  
<br>**! In case you have _NOT_ set one yet, you can use my *torpasswd* script from this repository to set a password for your Tor connection !**
