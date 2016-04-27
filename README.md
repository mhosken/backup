# Introduction

This backup script uses rsync to copy an image of the user's machine
to a backup drive and then uses btrfs snapshots to keep older versions.

btrfsbackup should always be run as root or using sudo.

There are 3 subcommands as part of btrfsbackup:

* new: Given a new empty drive, creates an encrypted btrfs volume on
  the drive ready to save backups. It also creates a partition that
  can be given to Startup Disk Creator to create a recovery bootable
  partition on the drive.
  
* init: Initialises a new backup volume for example for a user.

* backup: This does the backup. The command is implied on the command line.

btrfsbackup has some sensible defaults in it for volume and subvolume
names. use btrfsbackup -h to see their default values and how to change
them.

The rsync copy that btrfsbackup uses includes .rsync-filter support. A
default system level .rsync-filter is created, if none exists, during
btrfsbackup init. See man rsync for more details on how to control what
is backed up using .rsync-filter files.

If you have a new drive that you are plugging in to initialise, you
can use the disks command in Ubuntu to help find the disk and then
to get the path to the device that needs to be given to btrfsbackup new.
