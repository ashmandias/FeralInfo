# FeralInfo

## Password questions

The manager is offline. This means if you did not save an ssh or ftp password, you cannot get access.

Staff is not able to reset passwords at this time.

Check your ssh client and ftp clients for saved passwords.

### Recovevering password from Filezilla
From filezilla, export... site manager, open file in notepad, find <Pass encoding="base64">XXXXXXX</Pass>, put XXXXXXX into http://base64decode.net/

### Recover SSH password from chrome web cache

1. Download http://www.nirsoft.net/utils/chrome_cache_view.html
2. change double click behavior to "open cached file" in the menu
3. open any entry for feralhosting.com/manager/slot and hopefully find your passwords

### Changing SSH passwords

To CHANGE your SSH/ SFTP password to something new
login with terminal, putty, bash, etc, then:
passwd [user]
 
pick a strong password! see https://strongpasswordgenerator.com/

### Apps passwords
With the SSH password you should be able to get/change your other app passwords
 
If you saved any passwords in chrome, try passwords.google.com to find them!
 
This is the restart script for rutorrent, deluge, transmission, mysql:
wget -qO ~/restart.sh http://git.io/5Uw8Gw && bash ~/restart.sh
 
For other apps, check the FAQ on github:
https://github.com/feralhosting/feralfilehosting/tree/master/Feral%20Wiki
 
-------------RUTORRENT-------------------
To reset from SSH:
cd ~/www/[user].[server].feralhosting.com/public_html/rutorrent; htpasswd .htpasswd [user]
 
Then restart rtorrent with
wget -qO ~/restart.sh http://git.io/5Uw8Gw && bash ~/restart.sh
 
HOW TO RESET DELUGE WEBUI PASSWORD ON FERAL <from mundus2018>
-------------------------------------------
1. Log in via SSH
2. Delete the web config file
    rm ~/.config/web.conf
3. Restart Deluge web
    killall -9 -u $(whoami) deluge-web && screen -dmS deluge-web deluge-web
4. You can now login to deluge webui, the password is reset to deluge, use the deluge setting to change this

## FAQ access

Backup of the Feral FAQ with lots of tips for different software:
https://github.com/feralhosting/feralfilehosting/tree/master/Feral%20Wiki
