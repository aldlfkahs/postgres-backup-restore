# Postgres  Migration

This shell script is for migrating(backup and restore) postgres data in kubernetes environment. 'tar' binary should be included in containers.

## Step 0. Set up backup.config
- Purpose : `Set up configuration file for shell script`
- Order : 
	- Set up configuration for your environment
		- backup_file_directory
			- The path of backup file
			- Only write the path except file-name omitting the last '/' character
			- ex) /home/swlee/postgres-backup
		- origin_ns
			- Namespace of postgres to backup
			- ex) my-backup
		- origin_label
			- Label array of postgres to backup
			- ex) ("app=postgres", "cluster=cluster1")
		- restore_ns
			- Namespace of postgres to restore
			- ex) my-restore
		- restore_label
			- Label array of postgres to restore
			- ex) ("app=postgres", "cluster=cluster2")

## Step 1. Execute postgres-backup.sh
- Purpose : `Execute shell script`
- Pre-work
	``` bash
	sudo chmod +x postgres-backup.sh
	```
- Backup :
    ``` bash
    ./postgres-backup.sh backup
    ```
- Restore : 
    ``` bash
    ./postgres-backup.sh restore
    ```
