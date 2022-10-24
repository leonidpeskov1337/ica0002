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

Incremental backups are done automatically every day at 01:00.
Full backups are done on every Saturday at 01:00.
First incremental backup stores difference from the last created full backup.
Backups are retained for 28 days.
The backups that are older than 28 days are deleted at 03:00 every Saturday.

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


## CONTACTS

Telefon:
Email:
