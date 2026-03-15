[![Windows](https://img.icons8.com/ios/50/000000/windows-10.png)](https://www.microsoft.com/windows)
[![macOS](https://img.icons8.com/ios/50/000000/mac-os.png)](https://www.apple.com/macos/)
[![Linux](https://img.icons8.com/ios/50/000000/linux.png)](https://www.linux.org/)

Используются иконки с icons8.com — плоские, без блестящих эффектов.

# Encrypted backup using restic

## Simple guide for different data backup using a wonderful tool called restic. I'll show you how to make an ecrypted backup from scratch in external storage (HDD, SSD...) and also in a real computer (using SSH).

## Necessary things for storage device:
* Any external device (storage), whether HDD (including SATA), SSD, flashdrive etc...
* USB cabel for connecting to your PC.

## Necessary things for a computer-storage:
* Your PC (I'd totally recommend you use an unnecessary, old and low PC/laptop/netbook... for this ocassion of backup. There is no need to turn an usable computer into a backup service, even whether it has a lot of GB).
* Local network (it needs for SSH-transfer)
* preferably using a lightweight Linux distribution (or another low System) for a low perfomance.

## My devices for this guide:
Flashfrive (256GB) as an external device.
Netbook with AntiX Linux (2GB of RAM, Intel Atom N570, 512GB of HDD) as a computer.
