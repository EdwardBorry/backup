## Required stuff for a backup in storage device:
* Restic (utility for making a backup)

# Restic installation

## Linux:
1) `sudo apt update`
2) `sudo apt install restic`

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
1) `brew install restic`


# Doing backup using Restic

1) You need to create a directory for backup (for instance: restic_backup)
2) After, you should to initialize a repository in that directory:
`restic -r /home/jeylogan/restic_backup init`.
3) Now you can make your first backup:
`restic -r /path/to/storage_device backup /what/to/backup`.
(for instance: `restic -r /home/james/EOS23642 backup /home/james/Documents` means make I'll make a backup (`/home/james/Documents`) to `/home/james/EOS23642`).
4) Your backup is ready, but in order to edit - you should to recover it:
`restic -r /path/to/storage_device restore latest --target /what/to/backup`.
5) If you want to check all your backupS (snapshots), do next:
`restic -r /path/to/storage_device snapshots`.
6) If you want to delete backup snapshot, do:
* `restic forget <snapshot_id>`.
(In order to know a snapshot_id - type `restic -r /path/to/storage_device snapshots` to see all snapshots).

# Extra
* The -r parameter in restic is used to specify the location of the repository.
* restore latest in `restic -r sftp:your_username@your_ip_address:/your/path/restic_backup restore latest --target /your/place/for/backup` means restoring the most recent backup available in the repository.
*  --target in `restic -r sftp:your_username@your_ip_address:/your/path/restic_backup restore latest --target /your/place/for/backup` means distanation of data backup
* backup in `restic -r sftp:your_username@your_ip_address:/your/path/restic_backup backup /what/you/want/to_backup` creates a backup.
