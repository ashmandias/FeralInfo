# FeralInfo

The manager is offline, the slots are online. Please see status.feral.io for the latest up to date information

This is an unofficial document. Anything on [status.feral.io](status.feral.io) trumps this infomation. This document was created to help answer frequent questions on IRC.

## Password questions

The manager is offline. This means if you did not save an ssh or ftp password, you cannot get access.

Staff is not able to reset passwords at this time.

Check your ssh client and ftp clients for saved passwords.

### Recovering password from Filezilla
From filezilla, export... site manager, open file in notepad, find <Pass encoding="base64">XXXXXXX</Pass>, put XXXXXXX into http://base64decode.net/

### Recovering password from BitKinex
There are no know free ways to recover your slot's password if you saved it in BitKinex.
However you can open an SSH session from BitKinex via the black ssh button on the left menu bar of your slot.  Once you have ssh access to your slot, follow the .htpasswd process under the Alternative for rutorrent
To regain full ssh access without having to open BitKinex, use the SSH Keys instructions below.  Once you can ssh in via the balck ssh button in BitKinex, you can set up keys and login via PuTTY any time (took the N00b author of this section less than 10 minutes to set up)

### Recovering password from winscp
[Please follow this guide.](https://winscp.net/eng/docs/faq_password)

### Recover SSH password from chrome web cache

* Download http://www.nirsoft.net/utils/chrome_cache_view.html
* change double click behavior to "open cached file" in the menu
* open any entry for feralhosting.com/manager/slot and hopefully find your passwords

### SSH Keys
If you have SFTP/FTP access, you can set up [SSH keys to get SSH access without knowing the password](https://github.com/feralhosting/feralfilehosting/tree/master/Feral Wiki/SSH/Public Key Authentication for password-less login)

### Using a tool to reveal hidden passwords
[Program to recover passwords from asterisks](http://www.majorgeeks.com/files/details/asterisk_password_spy.html)

### Detailed password changing directions
[Existing FAQ docs](https://github.com/feralhosting/feralfilehosting/blob/8ae0e7806f65705ef64da01059d63c8effbd674e/Feral%20Wiki/General/Changing%20passwords/readme.md)
These docs may or may not currently work. 

### Changing SSH passwords

To CHANGE your SSH/ SFTP password to something new
login with terminal, putty, bash, etc, then:
```bash
passwd 
```
 
pick a strong password! see https://strongpasswordgenerator.com/

### Apps passwords
With the [SSH](https://github.com/feralhosting/feralfilehosting/tree/master/Feral%20Wiki/SSH/SSH%20Guide%20-%20The%20Basics) password you should be able to get/change your other app passwords
 
If you saved any passwords in chrome, try passwords.google.com to find them!
 
This is the restart script for rutorrent, deluge, transmission, mysql:

```bash
wget -qO ~/restart.sh http://git.io/5Uw8Gw && bash ~/restart.sh
``` 

For other apps, check the FAQ on github:
https://github.com/feralhosting/feralfilehosting/tree/master/Feral%20Wiki
 

#### Alternative for rutorrent
To reset from [SSH](https://github.com/feralhosting/feralfilehosting/tree/master/Feral%20Wiki/SSH/SSH%20Guide%20-%20The%20Basics):
(copy and paste as is -- do not modify)
```bash
cd ~/www/$(whoami).$(hostname).feralhosting.com/public_html/rutorrent; htpasswd .htpasswd $(whoami)
``` 

Then restart rtorrent with
```bash
wget -qO ~/restart.sh http://git.io/5Uw8Gw && bash ~/restart.sh
```
 
#### Alternaitve for rutorrent
1. Go to http://www.htaccesstools.com/htpasswd-generator/
1. Enter your slot username and a new password
1. Click "create .htpasswd file" 
1. Copy the generated text
1. Open your FTP/[SSH](https://github.com/feralhosting/feralfilehosting/tree/master/Feral%20Wiki/SSH/SSH%20Guide%20-%20The%20Basics) client, connect to your site and ensure "Show Hidden Files" is turned on
1. Navigate to .../home/username/www/username.slotname/public_html/rutorrent
1. Right-click and edit the .htpasswd file
1. Paste the text copied from step 4 and save
1. You now have access to the rutorrent web-GUI using your new password!(https://slotname.feralhosting.com/username/rutorrent/)

#### HOW TO RESET DELUGE WEBUI PASSWORD ON FERAL <from mundus2018>
-------------------------------------------
* Log in via [SSH](https://github.com/feralhosting/feralfilehosting/tree/master/Feral%20Wiki/SSH/SSH%20Guide%20-%20The%20Basics)

```bash
    cp ~/.config/deluge/web.conf ~/.config/deluge/web.conf-$(date -I)
```

Now you open web.conf with a text editor and replace the sha1 with "bc28bfa49a73fd2384cbecd6572ea72d0166aa28" and clear the salt with "".

* Restart Deluge web

(copy and paste as is -- do not modify)
```bash
    killall -9 -u $(whoami) deluge-web && screen -dmS deluge-web deluge-web
```
NOTE: It takes up to 5 minutes for deluge to restart

* You can now login to deluge webui, the password is reset to deluge, use the deluge setting to change this


You can check if deluge is running with:
```bash
ps -x | grep deluge  | wc -l
```

if the number is higher than 1, deluge is running

#### Alternative way to restart deluge
[Please check here for another way to restart deluge](https://github.com/feralhosting/feralfilehosting/tree/master/Feral%20Wiki/Installable%20software/Restarting%20-%20rtorrent%20-%20Deluge%20-%20Transmission%20-%20MySQL)

## FAQ access

Backup of the Feral FAQ with lots of tips for different software:
https://github.com/feralhosting/feralfilehosting/tree/master/Feral%20Wiki

## Application access

### Torrent clients
Note: update server with your server, and user with your username
The urls to access things are 
#### Rutorrent
https://server.feralhosting.com/user/rutorrent 
#### Deluge
https://server.feralhosting.com/user/deluge
#### Transmission
https://server.feralhosting.com/user/transmission

### SSH access
[Follow this guide to get started with SSH](https://github.com/feralhosting/feralfilehosting/tree/master/Feral%20Wiki/SSH/SSH%20Guide%20-%20The%20Basics)

## Payments

Payments are currently halted, and no slots are being suspended. There is currently no way to make a payment even if you want to.
