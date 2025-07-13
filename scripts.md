# Scripts Overview

The `/sbin` directory contains various utilities used by Clonezilla and related tools. Below is a short description of each script.


### clonezilla
Clonezilla is the main entry script for the imaging system. It loads DRBL configuration and sets up the environment for disk cloning and restoration tasks. This script presents the user menu and orchestrates actions like saving or restoring disks. It is typically invoked in Clonezilla Live sessions.

### create-debian-live
This utility builds a Debian-based live ISO that serves as the foundation for Clonezilla images. It assembles the necessary packages and configurations so the resulting ISO can boot on multiple machines. The script is helpful when you want a customized Debian live environment with built-in restoration capability.

### create-drbl-live
`create-drbl-live` generates a DRBL (Diskless Remote Boot Linux) live ISO or USB image. It packages DRBL server components so that multiple machines can boot from a single network source. This script is used when preparing a DRBL live environment for mass deployment.

### create-drbl-live-by-pkg
This helper wraps around `create-drbl-live` and selects the required packages automatically. It simplifies generating a DRBL live media when you have a predefined set of packages. The script ensures the resulting live system contains the desired tools with minimal manual setup.

### create-gparted-live
`create-gparted-live` creates a bootable ISO or USB image containing GParted along with Clonezilla utilities. The resulting media allows disk partitioning and cloning operations from a single environment. It's useful when you want a live system focused on partition management.

### create-ocs-tmp-img
This script constructs a Clonezilla image whose partition and logical volume files are symbolic links. It is intended for temporary images used to restore to other disks. By linking the files, space usage is minimized while preserving the structure needed for restoration.

### create-ubuntu-live
`create-ubuntu-live` produces a Ubuntu-based live ISO for Clonezilla. Similar to the Debian version, it includes restoration functions and necessary packages. This is handy for users who prefer Ubuntu as the base system.

### cv-ocsimg-v1-to-v2
This utility converts older Clonezilla image archives (version 1) to the newer version 2 format. It reads the existing image layout and reorganizes files to match the updated structure. Administrators use it when migrating archives to remain compatible with newer Clonezilla releases.

### drbl-ocs
`drbl-ocs` is a central control script that ties DRBL server functions with Clonezilla imaging tasks. It prepares network boot configurations and triggers cloning jobs for multiple clients. The script is commonly used in Clonezilla Server Edition setups.

### drbl-ocs-live-prep
This helper downloads Clonezilla Live ISO images for use with Clonezilla Server Edition. It ensures the server has the correct live environment ready for network boot. Administrators run it when setting up or updating their Clonezilla SE resources.

### ocs-btsrv
`ocs-btsrv` starts a BitTorrent service for distributing images. Using BitTorrent allows efficient multicast-style transfers when restoring or deploying a system to many machines. The script initializes the service and manages torrent files for Clonezilla images.

### ocs-chkimg
This script checks the integrity of Clonezilla images. It verifies partition tables, boot loaders, and partition contents via partclone’s checking tool. Running it helps detect corrupted or incomplete backups before restoration.

### ocs-chnthn
`ocs-chnthn` changes a Windows machine’s hostname offline using the chntpw registry tool. It is run in the DRBL environment to modify Windows registry entries prior to imaging or deployment. This simplifies renaming hosts without booting into Windows.

### ocs-clean-disk-part-fs
This program cleans filesystem and LVM information on all partitions of a specified disk. It wipes metadata so residual LVM or filesystem data does not interfere when creating new partition tables. It is typically used before partitioning or restoring an image.

### ocs-cnvt-usb-zip-to-dsk
`ocs-cnvt-usb-zip-to-dsk` converts DRBL or Clonezilla live ZIP archives into raw disk or VMDK images. This allows bootable USB images to be used with virtual machines or other environments requiring disk images. It automates the conversion so users can easily test live environments virtually.

### ocs-console-font-size
This script adjusts the console font size in the live environment. It helps improve readability on high-resolution displays or small screens. Users can select a preferred font size prior to running other Clonezilla operations.

### ocs-cvt-dev
`ocs-cvt-dev` converts a Clonezilla image from one device to another. It handles differences in disk geometry so the restored system boots correctly. This is useful when migrating an image from an old disk to a new model.

### ocs-cvtimg-comp
This utility converts Clonezilla images between compression formats. By changing the compression type, you can trade storage space for processing time or compatibility. It reads existing image files and outputs a recompressed version.

### ocs-decrypt-img
`ocs-decrypt-img` decrypts an encrypted Clonezilla image to create a usable plaintext copy. It asks for the passphrase and then processes the encrypted files. This is necessary when you need to restore or inspect an image that was previously encrypted.

### ocs-encrypt-img
This script encrypts an existing Clonezilla image. It takes the plain image files and generates an encrypted set to protect sensitive data at rest. Use it when storing backups in locations where encryption is required.

### ocs-expand-gpt-pt
`ocs-expand-gpt-pt` expands a GUID Partition Table on a disk to fill available space. After restoring an image to a larger disk, this script grows the GPT layout accordingly. It ensures the additional space can be used by new or existing partitions.

### ocs-expand-lvm
This program expands an LVM volume group and its logical volumes after restoration. When an image is placed on a larger disk, running this script grows the LVM structures so all free space becomes available. It automates LVM resizing tasks for Clonezilla images.

### ocs-expand-mbr-pt
`ocs-expand-mbr-pt` enlarges an MBR partition table to occupy the entire disk. It is similar to the GPT version but operates on legacy MBR layouts. Use it after restoring to a bigger disk so partitions can be resized or new ones added.

### ocs-ezio-leecher
This tool starts the Ezio client for downloading Clonezilla images via BitTorrent. It connects to an Ezio server and receives image data in a peer-to-peer manner. The script is intended for clients participating in large-scale deployments.

### ocs-ezio-seeder
`ocs-ezio-seeder` checks Clonezilla images and prepares them for Ezio distribution. Acting as a BitTorrent seeder, it ensures image integrity and then shares the data with leechers. This aids efficient image propagation across a network.

### ocs-find-live-key
This program scans for Clonezilla Live USB devices and extracts boot parameters. It is used by other scripts to automatically locate the live media when the device path may vary. The utility helps streamline boot processes in diverse hardware setups.

### ocs-gen-bt-metainfo
`ocs-gen-bt-metainfo` generates `.torrent` metadata directly from a filesystem. It allows you to create torrent files for Clonezilla images stored on a partition without first creating an archive. The output can then be used with BitTorrent services for distribution.

### ocs-gen-bt-slices
This script produces the slice files needed for Clonezilla’s BitTorrent mode from an existing image. Slices divide the image into small pieces so many clients can download concurrently. Running it prepares images for efficient peer-to-peer restoration.

### ocs-gen-grub2-efi-bldr
`ocs-gen-grub2-efi-bldr` builds a signed GRUB2 EFI bootloader. It is used when creating secure bootable media, ensuring the bootloader is properly signed for UEFI systems. This helps maintain compatibility with secure boot environments.

### ocs-get-dev-info
This utility collects detailed information about storage devices in the system. It queries udev and other tools to obtain serial numbers and attributes. Such information assists Clonezilla in mapping disks correctly during operations.

### ocs-img-2-vdk
`ocs-img-2-vdk` converts a Clonezilla image into a virtual disk file for use with virtualization platforms. By creating a VDK or VMDK file, the image can be booted as a virtual machine. This is convenient for testing backups without needing physical hardware.

### ocs-install-grub
This script reinstalls the GRUB bootloader on an MBR disk. It first attempts to use the GRUB binaries from the restored system, falling back to those in the live environment if necessary. The tool ensures the system can boot after imaging operations.

### ocs-iso
`ocs-iso` packages a minimal Debian Live system with Clonezilla tools into a bootable ISO. The resulting image can be burned to optical media or written to USB. It provides a portable environment for performing clone and restore tasks.

### ocs-iso-2-onie
This program converts a Clonezilla Live ISO into an ONIE self-extracting boot file. ONIE-enabled hardware can then boot directly into the Clonezilla environment. It streamlines deployment on compatible network devices.

### ocs-label-dev
`ocs-label-dev` assigns a filesystem label to a partition. It supports common filesystems such as ext, xfs, NTFS and FAT. Labeling partitions helps identify them during cloning or after restoration.

### ocs-lang-kbd-conf
This helper configures language and keyboard settings for the running environment. It updates system locale files so menus and prompts appear in the selected language. The script is typically called during boot or initial setup.

### ocs-langkbdconf-bterm
Designed for use in bterm or jfbterm consoles, this script also sets language and keyboard options. It ensures multilingual support when the framebuffer terminal is used in Clonezilla Live. The configuration improves international usability.

### ocs-live
`ocs-live` provides command-line options for running Clonezilla in live mode. It parses parameters such as postaction or repository setup and then launches the appropriate tools. Administrators call this script when scripting automated backups or restores in the live environment.

### ocs-live-bind-mount
This tool browses to a Clonezilla image repository and performs a bind mount. By mounting the repository within the live system, images can be accessed for saving or restoring. It simplifies connecting to external storage locations.

### ocs-live-boot-menu
`ocs-live-boot-menu` places a syslinux or isolinux configuration in a directory for booting Clonezilla Live. It prepares the boot menu entries so users can start the live environment with desired options. This script is often used when customizing boot media.

### ocs-live-bug-report
This program gathers disk and system information for troubleshooting Clonezilla Live. It collects logs and hardware details to assist in bug reports. Running it is useful when diagnosing issues or submitting feedback to developers.

### ocs-live-dev
`ocs-live-dev` writes a minimal Debian Live system with Clonezilla to a bootable device like a USB stick. The script installs necessary bootloaders and copies files to create portable Clonezilla media. It is helpful for generating custom live USB drives.

### ocs-live-feed-img
This script feeds multicast or BitTorrent data for clients restoring an image. It creates a tarball of the image metadata and provides instructions for clients. The tool serves as the sending side of network-based deployment.

### ocs-live-final-action
`ocs-live-final-action` performs shutdown or reboot actions after Clonezilla operations finish. It runs outside of the framebuffer terminal so messages remain visible. By separating power control from other tasks, it avoids issues with hidden prompts.

### ocs-live-general
This program initiates saving or restoring operations within Clonezilla Live. It sets up environment variables and then calls `ocs-sr` with the appropriate parameters. Users rely on it when starting standard clone or restore tasks from the live system.

### ocs-live-get-img
`ocs-live-get-img` restores an image by receiving multicast packets from a server. It downloads a tarball describing the image and a script with the full restoration command. Clients use it to participate in multicast-based deployment.

### ocs-live-netcfg
This lightweight network configuration tool configures network interfaces in Clonezilla Live. Derived from Knoppix netcardconfig, it allows interactive setup of IP addresses and other settings. It ensures connectivity before accessing remote image repositories.

### ocs-live-nicbonding
`ocs-live-nicbonding` enables channel bonding of multiple network interfaces. Bonding improves throughput and provides redundancy during network cloning sessions. The script configures bonding modules and settings on the fly.

### ocs-live-preload
This utility preloads a tarball or set of files into the live environment, based on the `ocs_preload` boot parameter. It can fetch data over HTTP, FTP, TFTP, CIFS, or NFS before Clonezilla starts. Administrators use it to inject scripts or drivers needed during cloning.

### ocs-live-repository
`ocs-live-repository` prepares the Clonezilla image home directory using a given URI. It supports various protocols so repositories can reside on local drives, SSH, WebDAV, or cloud storage. The script automates mounting and setup of the repository path.

### ocs-live-restore
This script starts the restoration workflow in Clonezilla Live. It ensures embedded images on recovery media are accessible and then launches `ocs-sr` with restore parameters. Users invoke it when booting a live system specifically to restore an image.

### ocs-live-run-menu
`ocs-live-run-menu` displays the interactive menu for Clonezilla Live. It loads necessary configurations and then presents choices such as save, restore, or other utilities. The menu guides users through operations in a user-friendly way.

### ocs-live-save
This program initiates the saving of a disk or partition image in Clonezilla Live. It sets variables from configuration files and calls `ocs-sr` to perform the backup. The script is widely used for creating new images of systems.

### ocs-live-swap-kernel
`ocs-live-swap-kernel` replaces the running Linux kernel and modules with another version. This is useful when a specific kernel is required for hardware compatibility. It synchronizes necessary hooks so the new kernel functions correctly.

### ocs-lvm2-start
Borrowed from Gentoo scripts, `ocs-lvm2-start` activates LVM volume groups before filesystem checks occur. It ensures logical volumes are available early in the boot process. Clonezilla Live includes it so images on LVM volumes can be accessed.

### ocs-lvm2-stop
The counterpart to `ocs-lvm2-start`, this script safely deactivates LVM volume groups. It disables udev rules and tears down mappings before shutdown or when unmounting images. Proper LVM shutdown prevents corruption.

### ocs-makeboot
`ocs-makeboot` creates bootable USB devices using GRUB for non-FAT filesystems or syslinux for FAT. It writes boot loaders and copies necessary files so the device can start Clonezilla. This helps users prepare flash drives for booting.

### ocs-match-checksum
This tool compares checksums stored in a Clonezilla image with those computed on a device. It verifies that files were written correctly during restoration. Running it adds an extra level of assurance that data integrity is preserved.

### ocs-memtester
`ocs-memtester` stresses the system’s memory to identify faults. It runs a series of tests and reports any errors found. This is often used before cloning to ensure hardware reliability.

### ocs-onthefly
This script performs disk-to-disk or partition-to-partition cloning on the fly. It streams data directly from source to destination without creating an intermediate image. The approach is efficient for immediate migrations or backups.

### ocs-park-disks
`ocs-park-disks` issues sync commands and then spins down local disks. Parking disks can prevent damage when a machine is powered off after cloning. The script ensures all writes are flushed before spin-down.

### ocs-prep-cache
This utility prepares cache files such as disk and partition lists. Having cached information speeds up subsequent Clonezilla operations. It is usually executed during initial setup of the live environment.

### ocs-prep-repo
`ocs-prep-repo` interactively prepares a Clonezilla image repository. It guides the user through mounting or creating the directory that will hold images. This script is helpful when setting up storage for backups for the first time.

### ocs-put-log-usb
This program copies Clonezilla log files to a live USB drive. Saving logs is useful for troubleshooting or auditing after operations finish. The script automates locating the USB drive and transferring the logs.

### ocs-put-signed-grub2-efi-bldr
`ocs-put-signed-grub2-efi-bldr` places a signed GRUB2 EFI bootloader onto removable media. It assists in preparing secure-boot compliant Clonezilla drives. The script ensures the correct bootloader file is used.

### ocs-related-srv
This helper script starts related services needed by Clonezilla Server Edition. It may launch DHCP, TFTP, or other daemons that support PXE booting and image distribution. Running it ensures the server environment is fully operational.

### ocs-resize-part
`ocs-resize-part` solves the issue of restoring a small partition image to a larger partition. It expands the partition and adjusts filesystem structures to occupy the new size. Use it when your restored partition does not fill the target disk.

### ocs-restore-ebr
This script writes the extended boot record (EBR) back to a disk after imaging. It restores the boot code and partition metadata stored in the EBR. This step can be necessary for disks with extended partitions.

### ocs-restore-mbr
`ocs-restore-mbr` reinstalls the executable portion of the Master Boot Record. By writing the first 446 bytes of the MBR, it recreates boot code that may have been lost or corrupted. The script references MBR specifications to perform the task.

### ocs-restore-mdisks
This program restores a single Clonezilla image to multiple disks simultaneously. It is often used to duplicate USB flash drives or deploy to multiple drives in one machine. The script coordinates the writes to each destination drive.

### ocs-restore-veracrypt-vh
`ocs-restore-veracrypt-vh` restores the volume header of a VeraCrypt-encrypted disk. This can recover access when the header becomes damaged. The script reads a backup header and writes it back to the drive.

### ocs-rm-win-swap-hib
This script removes Windows swap and hibernation files such as `pagefile.sys`, `swapfile.sys`, and `hiberfil.sys`. Deleting these files before imaging saves space and avoids restoration problems. It is typically executed when capturing Windows systems.

### ocs-run-boot-param
`ocs-run-boot-param` executes commands specified by boot parameters like `ocs_prerun` or `ocs_postrun`. It reads values passed from the bootloader and runs the associated scripts. This feature lets administrators automate tasks before or after imaging.

### ocs-save-veracrypt-vh
This tool dumps the volume header of a VeraCrypt-encrypted disk to a file. Keeping a backup header allows later restoration if the original is corrupted. The script prompts for the disk and destination location.

### ocs-sr
`ocs-sr` is the primary script that performs saving and restoring of partitions or disks. It handles multicast mode, various compression options, and advanced parameters. Most Clonezilla operations eventually call this script with appropriate arguments.

### ocs-srv-live
`ocs-srv-live` launches Clonezilla Server Edition within a DRBL live environment. It starts necessary network services and prepares the server for client machines. This script streamlines deploying Clonezilla SE from live media.

### ocs-tune-conf-for-s3-swift
This program adjusts configuration files for uploading Clonezilla images to AWS S3 or OpenStack Swift. It sets volume limits and other options suited for cloud storage. Use it when integrating Clonezilla with these services.

### ocs-tune-conf-for-webdav
`ocs-tune-conf-for-webdav` modifies davfs2 and Clonezilla settings to facilitate uploading images over WebDAV. It tweaks buffer sizes and lock usage for reliability. The script is useful when storing backups on WebDAV servers.

### ocs-tux-postprocess
This helper cleans certain hardware records, such as MAC addresses, from an imaged system. Removing these identifiers prevents conflicts when cloning to multiple machines. It is generally run after restoration is complete.

### ocs-update-initrd
`ocs-update-initrd` updates the initramfs of a deployed operating system. After imaging, it ensures drivers and modules are properly included for the target hardware. The script can be crucial when hardware differs from the source machine.

### ocs-update-syslinux
This script updates the syslinux bootloader files on a partition. It copies the latest ldlinux.sys and related modules so the device boots correctly. It is commonly used when preparing or refreshing Clonezilla boot media.

### ocsmgrd
`ocsmgrd` is a small Perl daemon that listens for Clonezilla management commands over the network. It can log operations, assign ports, and control PXE configuration when jobs are completed. The daemon coordinates tasks in server environments.

### update-efi-nvram-boot-entry
This program updates UEFI NVRAM entries for a restored disk. It removes unused boot entries and adds ones pointing to the correct EFI boot file. Running it helps ensure systems boot properly after cloning.

