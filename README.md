<h1>Backup Ubuntu Server Data</h1>


<h2>Description</h2>
The project consists of an Bash script that performs a data backup of a volume on Ubuntu Linux to a backup drive.<br/>

<h2>Language</h2>

- <b>Bash</b>

<h2>Environments Used </h2>

- <b>Ubuntu 22.04.4 LTS</b>

<h2>Setup</h2>

- Setup backup script to run at desired time</br>

  - Create /opt/backup directory:</br>
    $ sudo mkdir /opt/backup

  - Create /opt/backup/backup_server_data.sh and copy contents of backup_server_data.sh.txt</br>
    into /opt/backup/backup_server_data.sh:</br>
    $ sudo nano /opt/backup/backup_server_data.sh

  - Grant the execute permissions to /opt/backup/backup_server_data.sh:</br>
    $ sudo chmod +x /opt/backup/backup_server_data.sh

  - Setup Cron Jobs to run the backup scripts at selected times:</br>
    $ sudo crontab -e

  - Add the following lines to crontab:</br>
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
