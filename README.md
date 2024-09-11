<h1>Backup Ubuntu Server Data</h1>


<h2>Description</h2>
The project consists of an Bash script that performs a data backup of a specific data directories on a Ubuntu Linux Server to a backup drive.<br/><br/>

There are several variables that must be changed in the script to suit your needs. The variables that need to be changed are the following:<br/>

EMAIL_ADDRESS: This is the email address used for backup notifications.<br/>
SRC_DIR: This is the root directory for the subdirectories that will be backed up.<br/>
BACKUP_FOLDER_NAMES: This is an array of directories that will be backed up.<br/>
DEST_BASE_DIR: This is the destination directory for the backup.<br/>

The settings that need to be changed in the ssmtp.conf file are the following:<br/>

root:<br/>
mailhub:<br/>
rewriteDomain:<br/>
hostname:<br/>
UseTLS:<br/>
UseSTARTTLS:<br/>
AuthUser:<br/>
AuthPass:<br/>
FromLineOverride:<br/>

<h2>Language</h2>

- <b>Bash</b>
- <b>Rsync</b>
- <b>Cron</b>
- <b>SSMTP</b>

<h2>Environments Used </h2>

- <b>Ubuntu 22.04.4 LTS</b>

<h2>Setup</h2>

<b>Create backup script</b></br>

  1. Create /opt/backup directory:</br>
     $ sudo mkdir /opt/backup

  2. Create /opt/backup/backup_server_data.sh and copy contents of backup_server_data.sh.txt</br>
    into /opt/backup/backup_server_data.sh:</br>
     $ sudo nano /opt/backup/backup_server_data.sh

  3. Grant the execute permissions to /opt/backup/backup_server_data.sh:</br>
     $ sudo chmod +x /opt/backup/backup_server_data.sh</br>

<b>Setup Cron to run script at proper time</b></br>     

  1. Setup Cron Jobs to run the backup scripts at selected times:</br>
     $ sudo crontab -e

  2. Add the following lines to crontab:</br>
   <span>#</span> Run backup_server_data.sh every day at 3:00am.</br>
   0 3 * * * /opt/backup/backup_server_data.sh > /dev/null 2>&1</br>

  <b>Install and setup sSMTP</b></br>

  1. Install sSMTP via apt:</br>
     $ sudo apt install ssmtp

  3. Make a backup of /etc/ssmtp/ssmtp.conf before making changes:</br>
     $ sudo cp /etc/ssmtp/ssmtp.conf /etc/ssmtp/ssmtp.conf_old

  4. Edit /etc/ssmtp/ssmtp.conf and copy contents of ssmtp.conf.txt into it:</br>
     $ sudo nano /etc/ssmtp/ssmtp.conf
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
