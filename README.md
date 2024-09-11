<h1>Backup Ubuntu Server Data</h1>


<h2>Description</h2>
The project consists of an Bash script that performs a data backup of a specific data directories on a Ubuntu Linux Server to a backup drive.
There are several variables that must be changed in the script to suit your needs. The variables that need to be changed are the following:<br/><br/>

EMAIL_ADDRESS: This is the email address used for backup notifications.<br/>
SRC_DIR: This is the root directory for the subdirectories that will be backed up.<br/>
BACKUP_FOLDER_NAMES: This is an array of directories that will be backed up.<br/>
DEST_BASE_DIR: This is the destination directory for the backup.<br/>

<h2>Language</h2>

- <b>Bash</b>
- <b>Rsync</b>
- <b>Cron</b>
- <b>SSMTP</b>

<h2>Environments Used </h2>

- <b>Ubuntu 22.04.4 LTS</b>

<h2>Setup</h2>


  1. Create /opt/backup directory:</br>
    $ sudo mkdir /opt/backup

  2. Create /opt/backup/backup_server_data.sh and copy contents of backup_server_data.sh.txt</br>
    into /opt/backup/backup_server_data.sh:</br>
    $ sudo nano /opt/backup/backup_server_data.sh

  3. Grant the execute permissions to /opt/backup/backup_server_data.sh:</br>
    $ sudo chmod +x /opt/backup/backup_server_data.sh

  4. Setup Cron Jobs to run the backup scripts at selected times:</br>
    $ sudo crontab -e

  5. Add the following lines to crontab:</br>
   <span>#</span> Run backup_server_data.sh every day at 3:00am.</br>
   0 3 * * * /opt/backup/backup_server_data.sh > /dev/null 2>&1</br>
</br>
</br>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
