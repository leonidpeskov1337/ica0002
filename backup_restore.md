##Backup restore

#Install and configure infrastructure with Ansible:

    ansible-playbook infra.yaml

#Restore MySQL data from the backup:

    Command to download the backup, run on the managed host (leonidpeskov1337-2) as user backup:
    1. Login as backup: 
        sudo su backup
    2. Run command: 
        duplicity --no-encryption restore rsync://leonidpeskov1337@backup.captop.io//home/leonidpeskov1337/mysql /home/backup/restore/
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
    Or check the web server on address: http://193.40.156.86:<port of the leonidpeskov1337-1> +58


#Restore InfluxDB data from the backup:

    Command to download the backup, run on the managed host (leonidpeskov1337-1) as user backup:
    1. Login as backup: 
        sudo su backup
    2. Run command: 
        duplicity --no-encryption restore rsync://leonidpeskov1337@backup.captop.io//home/leonidpeskov1337/influxdb /home/backup/restore/

    Command to restore the backup, run on the managed host as root:
    1. Login as root:
        sudo su -
    2. Stop the telegraf:
        service telegraf stop
    3. Delete existing database:
        influx -execute 'DROP DATABASE telegraf'
    4. Restore telegraf:
        influxd restore -portable -database telegraf /home/backup/influxdb
    5. Run:
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
        
        
# Contacts

## Email: toprikivpike765@gmail.com
## Telefon: 56243811
