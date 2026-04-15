# IMPORTANT

Restic installation must be performed for both PCs.

# Installation

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


# Doing backup using Restic

1) Since you've been connecting to your server by SSH create a directory for backups there (for example: restic_backup).

2) Initialize a repository in the directory (restic_backup as my case):
```restic -r /home/james/restic_backup init```.

3) Quit the server connection and make a backup:
```restic -r sftp:your_username@your_ip_address:/your/path/restic_backup backup /what/you/want/to_backup```
for instance: ```restic -r sftp:james@192.168.1.109:/home/james/restic_backup backup /home/kevin/Downloads```. means make a backup ```/home/kevin/Downloads``` to ```/home/james/restic_backup```.

4) Recover data:
```restic -r sftp:your_username@your_ip_address:/your/path/restic_backup restore latest --target /your/place/for/backup```.

5) Check list of backups (also called as snapshots):
* ```restic -r sftp:your_username@your_ip_address:/your/path/restic_backup snapshots```.

6) Delete a snapshot:
* ```restic forget <snapshot_id>```
(```restic -r /path/to/storage_device``` snapshots to see snapshot's ID).
