<h1>Backup Ubuntu Server Data</h1>


<h2>Description</h2>
The project consists of an Bash script that performs a data backup of specific data directories on a Ubuntu Linux Server to a backup drive using Rsync.<br/><br/>

<h2>Language</h2>

- <b>Bash</b>
- <b>Rsync</b>
- <b>Cron</b>
- <b>SSMTP</b><br/><br/>

<h2>Environments Used </h2>

- <b>Ubuntu 22.04.4 LTS</b><br/><br/>

<h2>Variables and Settings</h2>

There are several variables that must be changed in the script to suit your needs. The variables that need to be changed are the following:<br/>

- <b>EMAIL_ADDRESS:</b> This is the email address used for backup notifications.<br/>
- <b>SRC_DIR:</b> This is the root directory for the subdirectories that will be backed up.<br/>
- <b>BACKUP_FOLDER_NAMES:</b> This is an array of directories that will be backed up.<br/>
- <b>DEST_BASE_DIR:</b> This is the destination directory for the backup.<br/>

The examples in the ssmtp.conf file are for Gmail. The settings that need to be changed in the ssmtp.conf file are the following:<br/>

- <b>root:</b> This is the email address that gets all mail for userids < 1000. Leave this empty to disable rewriting.<br/>
- <b>mailhub:</b> Fully qualified domain name of the mail server you use, both port 465 or 587 should be acceptable.<br/>
- <b>rewriteDomain:</b> Domain where email is coming form. Set this to the domain of your mail server.<br/>
- <b>hostname:</b> The full hostname.  Must be correctly formed, fully qualified domain name or GMail will reject connection.<br/>
- <b>UseTLS:</b> If your email supports TLS set this to YES. This implies that you are using port 465 or 587.<br/>
- <b>UseSTARTTLS:</b> If you are using port 587 set this to YES. If using port 465 set this to NO.<br/>
- <b>AuthUser:</b> Email account username.<br/>
- <b>AuthPass:</b> Email account password.<br/>
- <b>FromLineOverride:</b> Set this to YES is email users are able to send from their own address. If not, set it to NO.<br/><br/>

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
