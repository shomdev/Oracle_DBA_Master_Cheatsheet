### **My Day-to-Day Activities as an Oracle DBA**



**1. OS Level Checks**



**Check 1: Server Load \& Uptime**



\[oracle@localhost \~]$ uptime

&#x20;11:50:08 up 56 min,  2 users,  load average: 0.46, 0.48, 0.41

&#x20;



(High Load Average, load average)



Check 2: Mount Points



\[oracle@localhost \~]$ df -h

Filesystem           Size  Used Avail Use% Mounted on

devtmpfs             2.1G     0  2.1G   0% /dev

tmpfs                2.1G     0  2.1G   0% /dev/shm

tmpfs                2.1G  9.5M  2.1G   1% /run

tmpfs                2.1G     0  2.1G   0% /sys/fs/cgroup

/dev/mapper/ol-root   37G   27G   11G  72% /

/dev/mapper/ol-home   18G   69M   18G   1% /home

/dev/sda1           1014M  235M  780M  24% /boot

vm\_share              94G   51G   44G  54% /media/sf\_vm\_share

tmpfs                415M   24K  415M   1% /run/user/54321

/dev/sr0              59M   59M     0 100% /run/media/oracle/VBox\_GAs\_7.1.10



(mount point 90-95%)



Check 3: Listener Status



\[oracle@localhost \~]$ lsnrctl status



LSNRCTL for Linux: Version 19.0.0.0.0 - Production on 03-FEB-2026 11:56:17



Copyright (c) 1991, 2019, Oracle.  All rights reserved.



Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=192.168.1.99)(PORT=5500)))

STATUS of the LISTENER

\------------------------

Alias                     LISTENER

Version                   TNSLSNR for Linux: Version 19.0.0.0.0 - Production

Start Date                03-FEB-2026 11:49:06

Uptime                    0 days 0 hr. 7 min. 11 sec

Trace Level               off

Security                  ON: Local OS Authentication

SNMP                      OFF

Listener Parameter File   /u01/app/oracle/product/19.0.0/dbhome\_1/network/admin/listener.ora

Listener Log File         /u01/app/oracle/diag/tnslsnr/localhost/listener/alert/log.xml

Listening Endpoints Summary...

&#x20; (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=192.168.1.99)(PORT=5500)))

Services Summary...

Service "prod" has 1 instance(s).

&#x20; Instance "prod", status UNKNOWN, has 1 handler(s) for this service...

The command completed successfully



2\. Database Level Checks



Check 4: Database \& Instance Status



SQL> SELECT INSTANCE\_NAME, STATUS, DATABASE\_STATUS FROM V$INSTANCE;



INSTANCE\_NAME	 STATUS       DATABASE\_STATUS

\---------------- ------------ -----------------

sha		 OPEN	      ACTIVE



SQL> SELECT NAME, OPEN\_MODE, LOG\_MODE FROM V$DATABASE;



NAME	  OPEN\_MODE	       LOG\_MODE

\--------- -------------------- ------------

SHA	  READ WRITE	       ARCHIVELOG



Check 5: Alert Log Monitoring



Step 1 (Location dhoondo):



SQL> SHOW PARAMETER background\_dump\_dest;



NAME				     TYPE	 VALUE

\------------------------------------ ----------- ------------------------------

background\_dump\_dest		     string	 /u01/app/oracle/product/19.0.0

&#x09;					 /dbhome\_1/rdbms/log



SQL> select name, value from v$diag\_info where name='Diag Trace';



NAME

\----------------------------------------------------------------

VALUE

\--------------------------------------------------------------------------------

Diag Trace

/u01/app/oracle/diag/rdbms/sha/sha/trace



Step 2 (OS pe check karo):



\[oracle@localhost \~]$ cd /u01/app/oracle/product/19.0.0/dbhome\_1/rdbms/log

\[oracle@localhost log]$ ls -ltr alert\_sha.log

\-rw-r-----. 1 oracle oinstall 139 Jan 18 03:30 alert\_sha.log



\[oracle@localhost \~]$ cd /u01/app/oracle/product/19.0.0/dbhome\_1/rdbms/log

\[oracle@localhost log]$ ls -ltr alert\_sha.log

\-rw-r-----. 1 oracle oinstall 139 Jan 18 03:30 alert\_sha.log

\[oracle@localhost log]$

\[oracle@localhost log]$ cd /u01/app/oracle/diag/rdbms/sha/sha/trace

\[oracle@localhost trace]$

\[oracle@localhost trace]$ ls -ltr alert\_sha.log

\-rw-r-----. 1 oracle oinstall 144097 Feb  3 11:57 alert\_sha.log





\[oracle@localhost trace]$ tail -100f alert\_sha.log

28912691,28915561,28917080,28918429,28919145,28922227,28922532,28922608,

ERROR: Shared memory area is accessible to instance startup process

&#x20;prior to instance startup operation.

2026-02-03T11:57:31.087259-05:00

Warning: VKTM detected a forward time drift.

Please see the VKTM trace file for more details:

/u01/app/oracle/diag/rdbms/sha/sha/trace/sha\_vktm\_5021.trc



\[oracle@localhost trace]$ grep -i "ORA-" alert\_sha.log

ORA-1109 signalled during: ALTER DATABASE CLOSE NORMAL...

ORA-00313: open failed for members of log group 1 of thread 1

ORA-00312: online log 1 thread 1: '/u01/app/oracle/oradata/SHA/redo01.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 1 of thread 1

ORA-00312: online log 1 thread 1: '/u01/app/oracle/oradata/SHA/redo01.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 2 of thread 1

ORA-00312: online log 2 thread 1: '/u01/app/oracle/oradata/SHA/redo02.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 2 of thread 1

ORA-00312: online log 2 thread 1: '/u01/app/oracle/oradata/SHA/redo02.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 3 of thread 1

ORA-00312: online log 3 thread 1: '/u01/app/oracle/oradata/SHA/redo03.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 3 of thread 1

ORA-00312: online log 3 thread 1: '/u01/app/oracle/oradata/SHA/redo03.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 1 of thread 1

ORA-00312: online log 1 thread 1: '/u01/app/oracle/oradata/SHA/redo01.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 1 of thread 1

ORA-00312: online log 1 thread 1: '/u01/app/oracle/oradata/SHA/redo01.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 2 of thread 1

ORA-00312: online log 2 thread 1: '/u01/app/oracle/oradata/SHA/redo02.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 2 of thread 1

ORA-00312: online log 2 thread 1: '/u01/app/oracle/oradata/SHA/redo02.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 3 of thread 1

ORA-00312: online log 3 thread 1: '/u01/app/oracle/oradata/SHA/redo03.log'

ORA-27037: unable to obtain file status

ORA-00313: open failed for members of log group 3 of thread 1

ORA-00312: online log 3 thread 1: '/u01/app/oracle/oradata/SHA/redo03.log'

ORA-27037: unable to obtain file status



\[oracle@localhost trace]$ grep -B 2 "2026-02-03" alert\_sha.log

2026-02-02T15:05:50.750522-05:00

Resize operation completed for file# 3, old size 552960K, new size 563200K

2026-02-03T11:48:46.512818-05:00

ERROR: Shared memory area is accessible to instance startup process

&#x20;prior to instance startup operation.

2026-02-03T11:57:31.087259-05:00



(Identify critical errors (ORA-) and database events.)



Check 6: Tablespace Usage



SQL> SELECT df.tablespace\_name,

&#x20;      ROUND(df.total\_space\_mb, 2) Total\_MB,

&#x20;      ROUND(df.total\_space\_mb - fs.free\_space\_mb, 2) Used\_MB,

&#x20;      ROUND((df.total\_space\_mb - fs.free\_space\_mb) / df.total\_space\_mb \* 100, 2) Pct\_Used

FROM   (SELECT tablespace\_name, SUM(bytes) / 1024 / 1024 total\_space\_mb

&#x20;       FROM dba\_data\_files

&#x20;       GROUP BY tablespace\_name) df,

&#x20;      (SELECT tablespace\_name, SUM(bytes) / 1024 / 1024 free\_space\_mb

&#x20;       FROM dba\_free\_space

&#x20;       GROUP BY tablespace\_name) fs

WHERE  df.tablespace\_name = fs.tablespace\_name

ORDER BY Pct\_Used DESC;  2    3    4    5    6    7    8    9   10   11   12



TABLESPACE\_NAME 		 TOTAL\_MB    USED\_MB   PCT\_USED

\------------------------------ ---------- ---------- ----------

SYSTEM				      890      889.5	  99.94

SYSAUX				      550     515.94	  93.81

USERS					5	2.69	  53.75

UNDOTBS1			      295      13.25	   4.49



(Monitor space usage to prevent outages. Example finding: Detected SYSTEM tablespace at 99% usage.)



Check 7: RMAN Backup Status



SQL> SELECT OPERATION, STATUS, START\_TIME, END\_TIME,

&#x20;      ROUND(input\_bytes/1024/1024/1024,2) "INPUT\_GB",

&#x20;      ROUND(output\_bytes/1024/1024/1024,2) "OUTPUT\_GB"

FROM V$RMAN\_STATUS

WHERE START\_TIME > SYSDATE - 1

ORDER BY START\_TIME DESC;  2    3    4    5    6



no rows selected



(Ensure backups are running and no sessions are stuck. NO backup has run in the last 24 hours.)



Check 8: Blocking Sessions



SQL> SELECT s1.username || '@' || s1.machine || ' (SID=' || s1.sid || ') is blocking ' ||

&#x20;      s2.username || '@' || s2.machine || ' (SID=' || s2.sid || ')' AS blocking\_status

FROM v$lock l1, v$session s1, v$lock l2, v$session s2

WHERE s1.sid = l1.sid

&#x20; AND s2.sid = l2.sid

&#x20; AND l1.BLOCK = 1

&#x20; AND l2.request > 0

&#x20; AND l1.id1 = l2.id1

&#x20; AND l1.id2 = l2.id2;  2    3    4    5    6    7    8    9



no rows selected







***Note on Incident Management:*** 

***The queries above are strictly for Monitoring and Detection.***

***If all checks pass: The status is marked as "Green" in the daily report.***

***If an anomaly is found (e.g., Backup 'FAILED' or Tablespace > 90%): A P1/P2 Incident Ticket is immediately raised, and the issue is resolved following the specific remediation SOP (e.g., Adding a Datafile or Re-triggering the Backup).***

