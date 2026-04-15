# Restic installation

## Linux:
1) ```sudo apt update``` (updating the system)
2) ```sudo apt install restic``` (installing restic)

## Windows:
1) Download the official binary (https://github.com/restic/restic/releases)
2) Extract the zip file
3) Move .exe file (in zip file) to somewhere (for example: C:\restic)

Then you need to add it to PATH:
1) Press Win + S
2) Search Environment Variables
3) Open Edit the system environment variables
4) Click Environment Variables
5) Find Path → Edit
6) Add your path (C:\restic)

## MacOS
1) ```brew install restic``` (installing restic)


# Making a backup

1) Create a directory for backup (for example: restic_backup)
2) Initialize a repository in the directory (restic_backup as my case):
```restic -r /home/james/restic_backup init```.
4) Make a backup:
```restic -r /path/to/storage_device backup /what/to/backup```.
(for instance: ```restic -r /home/james/EOS23642 backup /home/james/Documents``` means make a backup `/home/james/Documents` to `/home/james/EOS23642`.
5) Recover data:
```restic -r /path/to/storage_device restore latest --target /what/to/backup```.
6) Check list of backups (also called as snapshots):
```restic -r /path/to/storage_device snapshots```.
7) Delete a snapshot:
* ```restic forget <snapshot_id>```.
(```restic -r /path/to/storage_device snapshots``` to see snapshot's ID).
