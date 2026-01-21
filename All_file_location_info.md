### System Parameter File:------

##### 

SQL> show parameter spfile



NAME				     TYPE	 VALUE

---

spfile				     string	 /u01/app/oracle/product/19.0.0

 						 /dbhome\_1/dbs/spfileprod.ora





\[oracle@localhost ~]$ cd /u01/app/oracle/product/19.0.0/dbhome\_1/dbs/

\[oracle@localhost dbs]$ ll

total 18328

-rw-rw----. 1 oracle oinstall     1544 Jan 18 03:00 hc\_prod.dat

-rw-r--r--. 1 oracle oinstall     3079 May 14  2015 init.ora

-rw-r-----. 1 oracle oinstall       24 Aug 17 13:47 lkPROD

-rw-r-----. 1 oracle oinstall     2048 Aug 17 13:50 orapwprod

-rw-r-----. 1 oracle oinstall     3584 Jan 18 03:00 spfileprod.ora



SQL> create pfile from spfile;



File created.



\[oracle@localhost ~]$ cd /u01/app/oracle/product/19.0.0/dbhome\_1/dbs/

\[oracle@localhost dbs]$ ll

total 18328

-rw-rw----. 1 oracle oinstall     1544 Jan 18 03:00 hc\_prod.dat

-rw-r--r--. 1 oracle oinstall     3079 May 14  2015 init.ora

-rw-r--r--. 1 oracle oinstall     1113 Jan 18 03:17 initprod.ora

-rw-r-----. 1 oracle oinstall       24 Aug 17 13:47 lkPROD

-rw-r-----. 1 oracle oinstall     2048 Aug 17 13:50 orapwprod

-rw-r-----. 1 oracle oinstall     3584 Jan 18 03:00 spfileprod.ora



\[oracle@localhost dbs]$ cat initprod.ora

prod.\_\_data\_transfer\_cache\_size=0

prod.\_\_db\_cache\_size=889192448

prod.\_\_inmemory\_ext\_roarea=0

prod.\_\_inmemory\_ext\_rwarea=0

prod.\_\_java\_pool\_size=0

prod.\_\_large\_pool\_size=16777216

prod.\_\_oracle\_base='/u01/app/oracle'#ORACLE\_BASE set from environment

prod.\_\_pga\_aggregate\_target=436207616

prod.\_\_sga\_target=1308622848

prod.\_\_shared\_io\_pool\_size=67108864

prod.\_\_shared\_pool\_size=318767104

prod.\_\_streams\_pool\_size=0

prod.\_\_unified\_pga\_pool\_size=0

\*.audit\_file\_dest='/u01/app/oracle/admin/prod/adump'

\*.audit\_trail='db'

\*.compatible='19.0.0'

\*.control\_files='/u01/app/oracle/oradata/PROD/control01.ctl','/u01/app/oracle/fast\_recovery\_area/PROD/control02.ctl'

\*.db\_block\_size=8192

\*.db\_name='prod'

\*.db\_recovery\_file\_dest='/u01/app/oracle/fast\_recovery\_area'

\*.db\_recovery\_file\_dest\_size=8256m

\*.diagnostic\_dest='/u01/app/oracle'

\*.dispatchers='(PROTOCOL=TCP) (SERVICE=prodXDB)'

\*.log\_archive\_format='%t\_%s\_%r.dbf'

\*.nls\_language='AMERICAN'

\*.nls\_territory='AMERICA'

\*.open\_cursors=300

\*.pga\_aggregate\_target=415m

\*.processes=300

\*.remote\_login\_passwordfile='EXCLUSIVE'

\*.sga\_target=1242m

\*.undo\_tablespace='UNDOTBS1'









### **DATFILE :-----------**





**SQL> select name from v$datafile;**



**NAME**

**--------------------------------------------------------------------------------**

**/u01/app/oracle/oradata/PROD/system01.dbf**

**/u01/app/oracle/oradata/PROD/sysaux01.dbf**

**/u01/app/oracle/oradata/PROD/undotbs01.dbf**

**/u01/app/oracle/oradata/PROD/users01.dbf**



**SQL> select name from v$tempfile;**



**NAME**

**--------------------------------------------------------------------------------**

**/u01/app/oracle/oradata/PROD/temp01.dbf**





**SQL> select \* from v$logfile;**



    \*\*GROUP# STATUS  TYPE\*\*



**---------- ------- -------**

**MEMBER**

**--------------------------------------------------------------------------------**

**IS\_	CON\_ID**

**--- ----------**

 \*\*3	   ONLINE\*\*



**/u01/app/oracle/oradata/PROD/redo03.log**

**NO	     0**



 \*\*2	   ONLINE\*\*



**/u01/app/oracle/oradata/PROD/redo02.log**

**NO	     0**



    \*\*GROUP# STATUS  TYPE\*\*



**---------- ------- -------**

**MEMBER**

**--------------------------------------------------------------------------------**

**IS\_	CON\_ID**

**--- ----------**



 \*\*1	   ONLINE\*\*



**/u01/app/oracle/oradata/PROD/redo01.log**

**NO	     0**



**SQL> col MEMBER for a50**

**SQL> set lin 200 pages 200**

**SQL> /**



    \*\*GROUP# STATUS  TYPE    MEMBER					      IS\\\_     CON\\\_ID\*\*



**---------- ------- ------- -------------------------------------------------- --- ----------**

 \*\*3	   ONLINE  /u01/app/oracle/oradata/PROD/redo03.log	      NO	   0\*\*

&nbsp;\\\*\\\*2	   ONLINE  /u01/app/oracle/oradata/PROD/redo02.log	      NO	   0\\\*\\\*

	 \\\*\\\*1	   ONLINE  /u01/app/oracle/oradata/PROD/redo01.log	      NO	   0\\\*\\\*





















**\[oracle@localhost ~]$ cd /u01/app/oracle/oradata/PROD/**

**\[oracle@localhost PROD]$ ll**

**total 2453700**

**-rw-r-----. 1 oracle oinstall  10600448 Jan 18 03:39 control01.ctl**

**-rw-r-----. 1 oracle oinstall 209715712 Jan 18 03:39 redo01.log**

**-rw-r-----. 1 oracle oinstall 209715712 Jan 18 03:32 redo02.log**

**-rw-r-----. 1 oracle oinstall 209715712 Jan 18 03:32 redo03.log**

**-rw-r-----. 1 oracle oinstall 576724992 Jan 18 03:37 sysaux01.dbf**

**-rw-r-----. 1 oracle oinstall 943726592 Jan 18 03:37 system01.dbf**

**-rw-r-----. 1 oracle oinstall  33562624 Aug 25 01:45 temp01.dbf**

**-rw-r-----. 1 oracle oinstall 346038272 Jan 18 03:37 undotbs01.dbf**

**-rw-r-----. 1 oracle oinstall   5251072 Jan 18 03:32 users01.dbf**



**SQL> select \* from v$controlfile;**



**STATUS	NAME						      IS\_ BLOCK\_SIZE FILE\_SIZE\_BLKS	CON\_ID**

**------- ----------------------------------------------------- --- ---------- -------------- ----------**

\*\*/u01/app/oracle/oradata/PROD/control01.ctl	      NO       16384		646	     0\*\*

\\\*\\\*/u01/app/oracle/fast\\\\\\\_recovery\\\\\\\_area/PROD/control02.ctl NO       16384		646	     0\\\*\\\*













\[oracle@localhost ~]$ cd /u01/app/oracle/oradata/PROD/

\[oracle@localhost PROD]$ ll

total 2453700

-rw-r-----. 1 oracle oinstall  10600448 Jan 18 03:39 control01.ctl

-rw-r-----. 1 oracle oinstall 209715712 Jan 18 03:39 redo01.log

-rw-r-----. 1 oracle oinstall 209715712 Jan 18 03:32 redo02.log

-rw-r-----. 1 oracle oinstall 209715712 Jan 18 03:32 redo03.log

-rw-r-----. 1 oracle oinstall 576724992 Jan 18 03:37 sysaux01.dbf

-rw-r-----. 1 oracle oinstall 943726592 Jan 18 03:37 system01.dbf

-rw-r-----. 1 oracle oinstall  33562624 Aug 25 01:45 temp01.dbf

-rw-r-----. 1 oracle oinstall 346038272 Jan 18 03:37 undotbs01.dbf

-rw-r-----. 1 oracle oinstall   5251072 Jan 18 03:32 users01.dbf

\[oracle@localhost PROD]$ cd /u01/app/oracle/fast\_recovery\_area/PROD/

\[oracle@localhost PROD]$ ll

total 10352

drwxr-x---. 6 oracle oinstall       78 Jan 18 03:00 archivelog

-rw-r-----. 1 oracle oinstall 10600448 Jan 18 03:52 control02.ctl

drwxr-x---. 2 oracle oinstall        6 Aug 17 13:50 onlinelog





#### **PASSWORD FILE:-------**





**SQL> select \* from v$pwfile\_users;**





**SQL> col USERNAME for a10**

**SQL> col PASSWORD\_PROFILE for a20**

**SQL> col LAST\_LOGIN for a14**

**SQL> col EXTERNAL\_NAME for a20**

**SQL> /**



**USERNAME   SYSDB SYSOP SYSAS SYSBA SYSDG SYSKM ACCOUNT\_STATUS PASSWORD\_PROFILE LAST\_LOGIN LOCK\_DATE EXPIRY\_DA EXTERNAL\_NAME AUTHENTI COM CON\_ID**

**---------- ----- ----- ----- ----- ----- ----- -------------- ---------------- ---------- --------- --------- ------------- -------- --- -------**

**SYS	   TRUE  TRUE  FALSE FALSE FALSE FALSE OPEN	                                                                    PASSWORD NO	    0**



**{CHECK PWSSWORD FILE MISING OR NOT}**



**\[oracle@localhost dbs]$ pwd**

**/u01/app/oracle/product/19.0.0/dbhome\_1/dbs**

**\[oracle@localhost dbs]$ ll**

**total 18348**

**-rw-rw----. 1 oracle oinstall     1544 Jan 18 02:55 hc\_orcl.dat**

**-rw-rw----. 1 oracle oinstall     1544 Jan 18 04:08 hc\_prod.dat**

**-rw-rw----. 1 oracle oinstall     1544 Jan 18 03:30 hc\_sha.dat**

**-rw-r--r--. 1 oracle oinstall     3079 May 14  2015 init.ora**

**-rw-r--r--. 1 oracle oinstall     1129 Jan 19  2026 initorcl.ora**

**-rw-r--r--. 1 oracle oinstall     1113 Jan 18 03:17 initprod.ora**

**-rw-r-----. 1 oracle oinstall       24 Aug  3 14:14 lkORCL**

**-rw-r-----. 1 oracle oinstall       24 Aug 17 13:47 lkPROD**

**-rw-r-----. 1 oracle oinstall       24 Jan 18 03:31 lkSHA**

**-rw-r-----. 1 oracle oinstall     2048 Aug  3 14:18 orapworcl**

**-rw-r-----. 1 oracle oinstall     2048 Aug 17 13:50 orapwprod**

**-rw-r-----. 1 oracle oinstall     2048 Jan 18 03:36 orapwsha**

**-rw-r-----. 1 oracle oinstall 18726912 Aug  3 15:11 snapcf\_orcl.f**

**-rw-r-----. 1 oracle oinstall     3584 Jan 18 02:55 spfileorcl.ora**

**-rw-r-----. 1 oracle oinstall     3584 Jan 18 04:07 spfileprod.ora**

**-rw-r-----. 1 oracle oinstall     3584 Jan 18 03:18 spfilesha.ora**

**\[oracle@localhost dbs]$ . oraenv**

**ORACLE\_SID = \[oracle] ? sha**

**The Oracle base has been set to /u01/app/oracle**

**\[oracle@localhost dbs]$ orapwd file=orapwsha password=sha entries=5 force=y {CREATE PASSWORD FILE}**



**OPW-00029: Password complexity failed for SYS user : Password must contain at least 8 characters.**









