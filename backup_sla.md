##Introduction

#Definition of SLA

This Service Level Agreement (this “SLA”) governs the backup Services. Operations and security teams may update, amend, modify or supplement this SLA from time to time.

#Terms

SLA - Service Level Agreement
RPO - Recovery Point Objective (How frequently backups are taken)
RTO - Recovery Time Objective (Amount of downtime infrtastrusture can tolerate)
Full backup - stores the whole backed up data
Incremental backup - stores only the difference in the data relative to the last incremental backup produced

#Backup coverage

This SLA describes the backup approach for the next services in the infrastructure:
Database services - MySQL, InfluxDB
Other service - Ansible repository
NB! All the other services, that are not included under the backup service can be restored using Ansible service.

#RPO

RPO - 28 days

#Versioning and retention

MySql Agama:

mysqldump is done automatically every day at 23:45 UTC. 
Incremental backups are done automatically every day at 00:15 UTC.
Full backups are done on every Saturday at 00:00 UTC.
First incremental backup stores difference from the last created full backup.
Backups are retained for 28 days, 28 versions can be stored at the same time.
The backups that are older than 28 days are deleted at 01:00 UTC every Saturday.

InfluxDB Telegraf:

Backup of telegraf database is done automatically every day at 00:30 UTC.
The previous dump is deleted before new one is created.

#Usability checks

All backup and recovery policies and procedures shall be tested at least 7 days before new modifications to Ansble repository by the persons responsible for those processes. 
The test must be monitored by an independent third party, whether internal audit, external auditors or consultants qualified to audit these processes.
New modifications/backups must be tested in the development environment.

#Restoration criteria

Backup restoration should be done only if it was detected and confirmed that the stored data was corrupted, modified, stolen or deleted.

#RTO
RTO - 2 hours

#SLA validity
The procedure is valid until the new procedure is approved.
The system administrator of the storage devices is responsible for updating the procedure.
The exception should be discussed and documented with the system administrator.
