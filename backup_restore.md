##Backup restore

#Install and configure infrastructure with Ansible:

    ansible-playbook infra.yaml

#Restore MySQL data from the backup:

    Command to download the backup, run on the managed host as user backup:
    1. Login as backup: 
        sudo su backup
    2. Run command: 
        duplicity --no-encryption restore rsync://leonidpeskov1337@backup.dungeonmaster.io//home/leonidpeskov1337/ /home/backup/restore/
    Command to restore the backup, run on the managed host as root:
    1. Login as root: 
        sudo su -
    2. Restore the backup: 
        mysql agama < /home/backup/restore/agama.sql

    Verify:
    1. Login as root: sudo su -
    2. Go to mysql: mysql
    3. Use agama database: use agama;
    4. Verify that all items that are needed are there: select * from item;
    Or check the web server on address: http://193.40.156.86:<port of the kristina-1> +58


#Restore InfluxDB data from the backup:
    Login as root:
        sudo su -
    Stop the telegraf:
        service telegraf stop
    Delete existing database:
        influx -execute 'DROP DATABASE telegraf'
    Restore telegraf:
        influxd restore -portable -database telegraf /home/backup/influxdb
    Run:
        ansible-playbook infra.yaml
    
    Verify:
    1. Login as root:
        sudo su -
    2. Go into the influxdb:
        influx
    3. Use telegraf database:
        use telegraf;
    4. Verify that measurements are there:
        show measurements;


<add a few words here how the result of backup restore can be checked>

## More info

	1. For more info write me : toprikivpike765@gmail.com
	2. You can also call +372 *** ***

