Centralized Backup and Recovery Server

📌 Project Overview

The **Centralized Backup and Recovery Server** is a Linux-based project developed to automate data backup and recovery operations using Bash shell scripting, Cron scheduling, and a Python Tkinter graphical user interface.

The system supports full and incremental backups, backup integrity verification, scheduled backup execution, restoration of files, recovery testing, and log management. It provides a simple dashboard through which users can execute and monitor backup operations.

🎯 Objectives

- Automate full and incremental backups.
- Schedule backup operations using Cron.
- Verify backup integrity using SHA-256 checksums.
- Restore backed-up data to a selected destination.
- Test the recovery process to verify data availability.
- Maintain logs for backup and scheduled operations.
- Provide a user-friendly graphical dashboard.

🛠️ Technologies Used

- **Operating System:** Ubuntu Linux
- **Scripting Language:** Bash Shell Scripting
- **Dashboard:** Python with Tkinter
- **Scheduling:** Cron
- **Backup Utility:** `tar`
- **Integrity Verification:** `sha256sum`
- **System Management:** Linux system utilities

🏗️ System Architecture

The system consists of five major components:

1. **Dashboard:** Provides a graphical interface for selecting and executing backup and recovery operations.
2. **Backend Scripts:** Handle backup creation, restoration, checksum verification, recovery testing, and other menu functions.
3. **Cron Scheduler:** Automatically executes configured backup jobs.
4. **System Utilities:** Tools such as `tar` and `sha256sum` manage archives and verify integrity.
5. **Storage Directories:** Store source data, backup archives, logs, and restored files.

📂 Project Directory Structure

```text
backup_system/
├── scripts/
│   ├── config.sh
│   ├── backup.sh
│   ├── restore.sh
│   ├── recovery_test.sh
│   ├── menu.sh
│   ├── gui.sh
│   └── dashboard.py
├── full/
├── incr/
├── logs/
│   ├── backup.log
│   └── cron.log
└── snapshot.snar/

project_data/
└── Source files to be backed up

restored/
└── project_data/
```

*Note: The exact files in the `scripts/` directory may vary depending on the final implementation.*

⚙️ Key Features

1. Full Backup
Creates a compressed archive containing the source data. It serves as the baseline for subsequent incremental backups.

2. Incremental Backup
Creates a backup of changes since the previous backup using the configured snapshot mechanism, helping reduce backup size and execution time.

3. Scheduled Backups
Uses Cron to execute backup jobs automatically according to the configured schedule.

4. Backup Integrity Verification
Uses SHA-256 checksums to check whether backup archives have changed or become corrupted.

5. Data Restoration
Restores backed-up files into a selected destination directory using the restoration script.

6. Recovery Testing
Tests the recovery process to demonstrate that backed-up data can be restored when required.

7. Log Management
Maintains application and scheduled-job logs to help review backup activity and troubleshoot failures.

8. Graphical Dashboard
Provides a Tkinter-based interface with ten menu options for accessing backup, scheduling, logging, validation, and recovery functions.

🖥️ Dashboard Menu Options

| Option | Function |
|---|---|
| 1 | Full Backup |
| 2 | Incremental Backup |
| 3 | List Backups |
| 4 | Cron Job Menu |
| 5 | Backup Checksum Test |
| 6 | Scheduled Logs |
| 7 | View Application Log |
| 8 | Restore Data |
| 9 | Recovery Test |
| 10 | Input Validation |

📅 Cron Schedule

The intended backup schedule is:

- **Sunday at 2:00 AM:** Full backup
- **Monday to Saturday at 2:00 AM:** Incremental backup

Example Cron configuration:

```cron
0 2 * * 0 /home/pujitha/backup_system/scripts/backup.sh full
0 2 * * 1-6 /home/pujitha/backup_system/scripts/backup.sh incr
```

Update the paths if the project is installed under a different username or directory.

🚀 Installation and Execution

Step 1: Install the required packages

Open the Ubuntu terminal and run:

```bash
sudo apt update
sudo apt install -y python3 python3-tk cron tar
```

Step 2: Create the project directories

```bash
mkdir -p ~/backup_system/{scripts,full,incr,logs}
mkdir -p ~/project_data
mkdir -p ~/restored
```

Step 3: Add source files

Place the files you want to protect inside:

```text
~/project_data/
```

Step 4: Make shell scripts executable

```bash
chmod +x ~/backup_system/scripts/*.sh
```

Step 5: Start the dashboard

```bash
python3 ~/backup_system/scripts/dashboard.py
```

The graphical dashboard should open, allowing you to select an operation and execute it.

🧪 Testing and Validation

The system can be tested by performing the following steps:

1. Create sample files inside the source directory.
2. Run a full backup.
3. Modify or add source files and run an incremental backup.
4. Verify the archive checksums.
5. Restore the backup into a separate destination directory.
6. Compare the restored files with the original files.
7. Review the application and scheduled-job logs.
8. Verify the Cron configuration and service status.

Example comparison command:

```bash
diff -r ~/project_data ~/restored/project_data
```

If the directories match, the command produces no differences. Run this comparison when the restored data is expected to match the current source data.

🔐 Security and Reliability

- Uses checksum verification to help detect archive corruption or modification.
- Stores backup archives separately from the source directory.
- Maintains logs for troubleshooting and review.
- Supports recovery testing to check restoration functionality.

For stronger protection, future versions can add encrypted backups, remote storage, and automatic cleanup policies.

✅ Expected Outcome

The project provides a centralized approach to backup and recovery management on Ubuntu Linux. It reduces manual effort through scheduled backups, supports integrity checks and restoration, and provides a graphical interface for managing backup operations.

🔮 Future Enhancements

- Remote or cloud backup storage.
- Email notifications for failed backup jobs.
- Automatic deletion of outdated backups.
- Backup encryption and access control.
- Improved reporting and recovery status monitoring.

👥 Team Members

- **Nandana N** — Team Leader / Linux System Administrator
- **K B Sanjana** — Storage & Backup Administrator
- **Abinayathri A** — Automation & Security Engineer
- **Pujitha S** — Testing, Documentation & Presentation Lead

📚 Academic Project

**Course:** Linux System Administration (E1ITA307)  
**Project Title:** Centralized Backup and Recovery Server



*This project demonstrates the practical use of Linux administration, shell scripting, scheduled automation, data integrity verification, and disaster recovery.*
