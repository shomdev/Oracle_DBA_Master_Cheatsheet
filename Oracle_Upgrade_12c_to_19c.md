# Oracle Database Upgrade: 12c to 19c

## 1. Pre-Upgrade Checks
### Step 1: Check Invalid Objects
Before starting the upgrade, verify if there are any invalid objects in the database.

**Command:**
```sql
SELECT count(*) FROM dba_objects WHERE status='INVALID'?
Note: The count should be 0. If not, recompile invalid objects.

Step 2: Create Required Directories
Create the folders needed for the pre-upgrade tool.

Command:
!mkdir -p /home/oracle/PRIM/preupgrade```
2. Run Pre-Upgrade Tool
Execute the jar file to analyze the database.

Command:
