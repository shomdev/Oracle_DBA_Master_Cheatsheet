# Oracle DBA Master Knowledge Base 🚀

Welcome to my personal documentation for Oracle Database Administration. This repository follows a structured path from Core Architecture to High Availability setups.

> **Status:** 🚧 Active Development (Updating Daily with Lab Scenarios)

## 📚 Table of Contents

### 🟢 Phase 1: Core DBA & Architecture (The Foundation)
*Focus: Internal Architecture, User Management, and Daily Operations.*

1. **[Oracle Architecture Deep Dive](01_Architecture)**
   - Instance (SGA/PGA) & Processes (PMON, SMON, DBWR, LGWR)
   - Physical Structure: Datafiles, Controlfiles, Redo Logs, SPFILE/PFILE
2. **[Storage & Space Management](02_Storage)**
   - Tablespace Management (Creation, Resize, Undo, Temp)
   - Logical Structure: Segments, Extents, Blocks
3. **[User & Security Management](03_Security)**
   - Users, Roles, Privileges & Profiles
   - Audit Trail & Standard Auditing
4. **[Connectivity & Networking](04_Networking)**
   - Listener Configuration, TNS entries, & DB Links
   - Dedicated vs. Shared Server Architecture
5. **[Operational Commands](05_Operations)**
   - Startup/Shutdown Modes & Checkpoints
   - Managing Locks & Latches (Conflict Resolution)

---

### 🟡 Phase 2: Maintenance, Backup & Recovery (The Safety Net)
*Focus: Data Protection, Patching, and Automation.*

6. **[Backup & Recovery (RMAN)](06_RMAN)**
   - RMAN Architecture, Retention Policies & Catalog
   - Scenarios: Loss of Controlfile, Datafile, Redo Log & SPFILE
   - Cloning & Duplication of Database
7. **[Utilities & Data Movement](07_Utilities)**
   - Data Pump (EXPDP/IMPDP) Strategies
   - SQL*Loader & External Tables
8. **[Patching & Upgrades](08_Patching)**
   - OPatch Utilities & Conflict Checking
   - Database Upgrade (12c to 19c) & Migration Steps
   - AutoUpgrade Utility Modes (Analyze, Fixup, Deploy)

---

### 🔴 Phase 3: High Availability & Advanced Config (The Expert Level)
*Focus: Linux Setup, ASM, Data Guard, and RAC.*

9. **[Installation & Configuration](09_Installation)**
   - Oracle Linux Setup (Pre-requisites, RPMs, Kernel Parameters)
   - Grid Infrastructure (ASM) Installation & Configuration
   - Creating CDB & PDB (Multitenant Architecture)
10. **[Disaster Recovery (Data Guard)](10_DataGuard)**
    - Physical Standby Setup & Configuration
    - Switchover, Failover & Gap Resolution
11. **[Real Application Clusters (RAC)](11_RAC)**
    - 2-Node RAC Setup Overview & SRVCTL Commands
12. **[Performance Tuning](12_Tuning)**
    - AWR, ADDM, & ASH Analysis
    - Wait Events, Blocking Sessions & Index Tuning

---
*Author: Shomdev Singh*
