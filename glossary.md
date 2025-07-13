# Glossary

| Term | Meaning | Example usage in repo |
|------|---------|---------------------|
| GPL | GNU General Public License | Declared as license for scripts, e.g. `bin/ocs-scan-disk` line 2【F:bin/ocs-scan-disk†L1-L4】 |
| DRBL | Diskless Remote Boot in Linux | Mentioned in README line 4 as a component Clonezilla is based on【F:README†L3-L4】 |
| Partclone | Imaging tool used by Clonezilla | Listed in README line 4 among base tools【F:README†L3-L4】 |
| udpcast | Network cloning tool | Also listed in README line 4 among dependencies【F:README†L3-L4】 |
| SE | Server Edition | Defined in README when describing Clonezilla SE【F:README†L3-L4】 |
| MBR | Master Boot Record | Explained in `sbin/ocs-restore-mbr` lines 3‑8 as the 512‑byte boot sector【F:sbin/ocs-restore-mbr†L3-L9】 |
| EBR | Extended Boot Record | Explained in `sbin/ocs-restore-ebr` lines 5‑9【F:sbin/ocs-restore-ebr†L5-L9】 |
| GPT | GUID Partition Table | Discussed in changelog regarding disk formats【F:debian/changelog†L1366-L1375】 |
| EFI | Extensible Firmware Interface | `update-efi-nvram-boot-entry` script updates EFI boot entries【F:sbin/update-efi-nvram-boot-entry†L32-L44】 |
| UEFI | Unified Extensible Firmware Interface | Mentioned in changelog for booting support【F:debian/changelog†L1373-L1375】 |
| NVRAM | Non-Volatile Random Access Memory | Option in `ocs-sr` for updating boot entries【F:sbin/ocs-sr†L55-L1771】 |
| PXE | Preboot eXecution Environment | Boot menu labels in `ocs-live-boot-menu` for network boot【F:sbin/ocs-live-boot-menu†L456-L485】 |
| iPXE | Enhanced PXE implementation | Boot option in `ocs-live-boot-menu`【F:sbin/ocs-live-boot-menu†L476-L485】 |
| DHCP | Dynamic Host Configuration Protocol | Used in lite server mode for assigning addresses【F:sbin/ocs-live-feed-img†L823-L849】 |
| SSHFS | SSH Filesystem for network mounting | Configured in `ocs-prep-repo` lines 317‑327【F:sbin/ocs-prep-repo†L317-L327】 |
| CIFS | Common Internet File System | SMB protocol versions documented in `ocs-prep-repo` lines 569‑579【F:sbin/ocs-prep-repo†L569-L579】 |
| SMB | Server Message Block protocol | Same lines as CIFS configuration【F:sbin/ocs-prep-repo†L569-L579】 |
| NFS | Network File System | Example mount options in `ocs-live-bind-mount` lines 20‑29【F:sbin/ocs-live-bind-mount†L20-L29】 |
| LVM | Logical Volume Manager | Scripts manage LVM volumes such as `ocs-expand-lvm`【F:sbin/ocs-expand-lvm†L4-L220】 |
| VG | Volume Group (part of LVM) | Mentioned in expansion steps in `ocs-expand-lvm` lines 195‑220【F:sbin/ocs-expand-lvm†L195-L220】 |
| LV | Logical Volume (LVM component) | Example operations in `ocs-expand-lvm` lines 35‑150【F:sbin/ocs-expand-lvm†L35-L150】 |
| PV | Physical Volume (LVM component) | Handled in `ocs-expand-lvm` and related checks【F:sbin/ocs-expand-lvm†L4-L210】 |
| UUID | Universally Unique Identifier | Changelog references using UUID to identify devices【F:debian/changelog†L165-L2359】 |
| USB | Universal Serial Bus | Changelog covers Clonezilla live USB handling【F:debian/changelog†L138-L163】 |
| NVMe | Non-Volatile Memory express | Direct I/O option in `ocs-onthefly` for NVMe SSDs【F:sbin/ocs-onthefly†L486-L494】 |
| SSD | Solid State Drive | `ocs-park-disks` checks SSD vs HDD via rota value【F:sbin/ocs-park-disks†L72-L80】 |
| HDD | Hard Disk Drive | Same script parks HDDs only【F:sbin/ocs-park-disks†L72-L80】 |
| BT | BitTorrent | Bittorrent restore options in `ocs-functions`【F:scripts/sbin/ocs-functions†L7580-L8038】 |
| FQDN | Fully Qualified Domain Name | Parameter description in `ocs-socket` lines 9‑13【F:bin/ocs-socket†L9-L14】 |
| iSCSI | Internet Small Computer Systems Interface | Repo preparation script prompts for iSCSI server info【F:sbin/ocs-prep-repo†L203-L237】 |
| ISO | Optical disc image format | Changelog notes recovery ISO generation【F:debian/changelog†L3-L18】 |
| BIOS | Basic Input/Output System | Boot menu for BIOS machines generated in `create-gparted-live`【F:sbin/create-gparted-live†L315-L539】 |
| VGA | Video Graphics Array | Boot menu uses VGA mode option in `create-gparted-live`【F:sbin/create-gparted-live†L315-L317】 |
| MAC | Media Access Control address | Example data in `samples/gen-netcfg` for network setup【F:samples/gen-netcfg†L5-L14】 |
| RAM | Random Access Memory | Changelog adjusts ramfs size for live builds【F:debian/changelog†L2070-L2071】 |
| SATA | Serial ATA interface | Device examples in `ocs-cvt-dev` usage notes【F:sbin/ocs-cvt-dev†L30-L165】 |
| SCSI | Small Computer System Interface | Mentioned in `ocs-cvt-dev` conversion information【F:sbin/ocs-cvt-dev†L30-L165】 |
| GUID | Globally Unique Identifier | Detailed in `ocs-get-dev-info` output example【F:sbin/ocs-get-dev-info†L340-L355】 |
| TUI | Text-based User Interface | Default interface for clone operations in `ocs-sr`【F:sbin/ocs-sr†L60-L64】 |
| GUI | Graphical User Interface | Option `--nogui` disables GUI/TUI output in `ocs-decrypt-img`【F:sbin/ocs-decrypt-img†L30-L31】 |
| LUKS | Linux Unified Key Setup | Changelog describes LUKS-related improvements【F:debian/changelog†L573-L577】 |
