# Database Backup Script

This script is designed to run in Synology DSM using the Control Panel's Task Scheduler with a user-defined script. It performs backups of a MySQL database and retains them for a specified number of days.

## Prerequisites

- Synology DSM (DiskStation Manager)
- MariaDB package installed (for mysqldump)
- Access to the MySQL database you want to back up

## Usage

1. Open the Synology Control Panel.
2. Navigate to Task Scheduler.
3. Create a new user-defined script task.
4. Paste the contents of this script into the task.
5. Update the values in the script according to your setup (see below).
6. Save and schedule the task as needed.

## Script Configuration

Update the following values in the script:

- `DB_BACKUP_PATH`: The directory where backups will be stored.
- `MYSQL_HOST`: The MySQL server hostname or IP address.
- `MYSQL_PORT`: The MySQL server port (usually 3306).
- `MYSQL_USER`: The MySQL username.
- `MYSQL_PASSWORD`: The MySQL password.
- `DATABASE_NAME`: The name of the database to back up.
- `BACKUP_RETAIN_DAYS`: Number of days to keep local backup copies.
- `MYSQLDUMP`: Path to the `mysqldump` binary (usually provided by the MariaDB package).

## Script Execution

1. The script creates a directory for the current date in the specified backup path.
2. It initiates a backup of the specified database using `mysqldump`.
3. The backup is compressed into a zip file with a timestamp.
4. If the backup is successful, a message is displayed.
5. Older backups (older than the specified retention days) are removed.
