# Samples Directory Overview

This document summarizes the scripts under the `samples/` directory. Each entry briefly explains when you might use the script and what actions it performs.

## create-1P-pt-sf
This script automatically creates a single partition on a target disk using `sfdisk`. It wipes the disk entirely and makes one bootable NTFS partition that spans the whole device. The sample is intended to be invoked as a Clonezilla pre-run hook with advanced parameters, cautioning the user that all existing data will be destroyed. Use it when you need an automated way to create a single-partition layout before imaging or deploying a system.

## create-2P-pt-sf
`create-2P-pt-sf` partitions a disk into two parts: a large primary partition and a 3 GB swap partition. The script calculates partition sizes based on the disk geometry and uses `sfdisk` to apply the layout. Like the single‑partition example, this is dangerous and meant for automated setups where the disk should be freshly prepared. It is useful when you want a simple root-plus-swap layout generated without manual interaction.

## create-usb-2P-pt-sf
This sample prepares removable media with two partitions. The first partition is formatted with a user-defined filesystem (defaulting to ext4 or vfat), while the second becomes an NTFS partition. It confirms the target is a USB drive, writes the partition table, and formats both partitions. Administrators can use it to automate USB drive preparation for Clonezilla Live or other portable environments.

## custom-ocs
`custom-ocs` demonstrates how to build a simple menu-driven Clonezilla workflow. After loading Clonezilla functions, it lets the user back up `/dev/sda1` (or `/dev/hda1`) to a designated image location or restore that image back to the same partition. The script mounts the destination, invokes `ocs-sr` for saving or restoring, and unmounts when finished. It is intended as a starting point for customizing Clonezilla Live menus.

## custom-ocs-1
This variation shows how to integrate network storage. It configures networking via DHCP, mounts a Samba share as the Clonezilla image repository, and then runs a disk restore from a user-selected image. The script is tailored for unattended restoration where images reside on a remote server. Use it to automate deployments from a centralized share.

## custom-ocs-2
`custom-ocs-2` provides a multilingual menu (in Traditional Chinese) for backing up and restoring Windows and EZGO partitions. Images are stored on `/dev/sda7`, and the script offers options to back up or restore each partition as well as restore predefined default images. It demonstrates more complex menu logic and can serve in classroom or lab settings where multiple Windows and Linux images are managed. The script mounts the repository, runs `ocs-sr` with appropriate options, and handles cleanup.

## custom-ocs-3
This example targets Clonezilla Live running from a USB device that has two partitions. It can save the machine’s first disk to the second partition of the USB drive or restore an image from that partition. The script checks that Clonezilla is booted from USB, mounts the image repository, and calls `ocs-sr` in save or restore mode. It's useful for creating a self-contained recovery USB stick.

## gen-netcfg
`gen-netcfg` generates network configuration files on RedHat-like systems based on entries in `mac-ip-list.txt`. It scans network interfaces, matches their MAC addresses with the data file, and writes the appropriate ifcfg scripts, gateway, DNS, and hostname settings. After generating the files, the network service is restarted. This is handy for provisioning multiple machines with predefined network settings.

## gen-rec-iso
This script creates a recovery ISO directly from a running machine. It captures a disk image using Clonezilla, then invokes `ocs-iso` to build a bootable ISO that can later restore that image. Options allow batch mode, specifying a working directory, and adding extra boot parameters. Use it when you need a turnkey recovery CD or DVD for a specific machine configuration.

## gen-rec-usb
`gen-rec-usb` builds a recovery USB flash drive. It saves the specified source disk as an image to the target USB partition and then runs `ocs-live-dev` to install a bootable Clonezilla environment that automatically restores the image. The script can operate in batch or semi-batch modes and adjusts the boot menu to display a custom prompt. It's useful for producing portable recovery sticks for field deployment.

## mdisks-checksum
This large script manages disk imaging with checksum verification. It can save a disk image, restore an image to multiple disks, or check that restored files match recorded checksums. During restore, it can label partitions sequentially and log verification results both in the image repository and on the destination disks. Administrators can employ it when data integrity must be verified across many machines.

## singularity-debian-ocs.def
This file is a Singularity definition for creating a container image that runs Clonezilla in batch mode. It starts from a Debian base, adds the DRBL and Clonezilla packages, sets up locales, and performs a few configuration tweaks required for Clonezilla to operate inside the container. Build it with `singularity build` to obtain a self-contained environment for network-based Clonezilla operations.

