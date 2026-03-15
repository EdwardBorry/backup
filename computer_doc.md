## Required stuff for backup in computer:
* OpenSSH (SSH-service)
* Restic (utility for making a backup)

# IMPORTANT
Installation must be performed for both the client and the server PCs.

# OpenSSH installation

## Linux (I'll use apt packet manager for instance):
By default, you may already have OpenSSH in your distribution, but if you don't - do:
1) `sudo apt update`
2) `sudo apt install openssh-server`

## Windows:
* `Add-WindowsFeature -Name OpenSSH.Server`

OR

Open Settings.
Go to Apps > Optional Features.
Scroll down and click Add a feature.
Search for OpenSSH Server.
Select OpenSSH Server and click Install.

## MacOS:
* MacOS has already pre-installed OpenSSH in the system.


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


# Connecting to your machine by OpenSSH

Before you start connect to your client PC by OpenSSH you need to enable its service in a server PC:

## Linux:
If you use a distribution that have systemd as a system initialization, then do:
* `sudo systemctl start ssh`
If you use a distribution that have any other system initialization (runit, OpenRC...), do:
* `sudo service ssh start`

## Windows:
* `Start-Service sshd`

## MacOS:
* `sudo systemsetup -setremotelogin on`


Now OpenSSH service is successfully enable in your server PC. Now you need to connect it by your client PC:

* `ssh your_username@your_ip_address` (Linux, Windows and MacOS use the same command).

From now on you can manage your server remotely.


# Doing backup using Restic

1) Since you've been connected to your server by ssh you need to create a directory for backup there (for instance: restic_backup).

2) After, you should to initialize a repository in that directory:
`restic -r /home/jeylogan/restic_backup init`.

3) Now you should to exit from your server connection (just type `exit` or use Ctrl+D) and make your first backup:
`restic -r sftp:your_username@your_ip_address:/your/path/restic_backup backup /what/you/want/to_backup`
for instance: `restic -r sftp:james@192.168.1.109:/home/james/restic_backup backup /home/kevin/Downloads`. That means, I'll make a backup (`/home/kevin/Downloads`) to `/home/james/restic_backup`.

4) Your backup is ready, but in order to edit - you should to recover it:
`restic -r sftp:your_username@your_ip_address:/your/path/restic_backup restore latest --target /your/place/for/backup`.

5) If you want to check all your backupS (snapshots), do next:
* `restic -r sftp:your_username@your_ip_address:/your/path/restic_backup snapshots`.

6) If you want to delete backup snapshot, do:
* `restic forget <snapshot_id>`
(In order to know a snapshot_id - type `restic -r sftp:your_username@your_ip_address:/your/path/restic_backup snapshots` to see all snapshots).


# Extra
* The -r parameter in restic is used to specify the location of the repository.
* restore latest in `restic -r sftp:your_username@your_ip_address:/your/path/restic_backup restore latest --target /your/place/for/backup` means restoring the most recent backup available in the repository.
*  --target in `restic -r sftp:your_username@your_ip_address:/your/path/restic_backup restore latest --target /your/place/for/backup` means distanation of data backup
* backup in `restic -r sftp:your_username@your_ip_address:/your/path/restic_backup backup /what/you/want/to_backup` creates a backup.
