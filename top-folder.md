# Top Folder Overview

This document provides a short summary of each top-level directory in this repository and notes which other
folders they rely on.

## bin
Helper utilities for tasks like scanning disks or checking Clonezilla Live versions. These scripts source
`drbl-conf-functions`, `drbl-ocs.conf` and `ocs-functions`, meaning they depend on the configuration and
function libraries provided in `conf` and `scripts/sbin`.
Example from `bin/ocs-scan-disk`:
```
DRBL_SCRIPT_PATH="${DRBL_SCRIPT_PATH:-/usr/share/drbl}"
. $DRBL_SCRIPT_PATH/sbin/drbl-conf-functions
. /etc/drbl/drbl-ocs.conf
. $DRBL_SCRIPT_PATH/sbin/ocs-functions
```
【F:bin/ocs-scan-disk†L8-L11】

## conf
Contains the main configuration file `drbl-ocs.conf` which is loaded by many scripts in `sbin`.

## debian
Packaging metadata used when building Debian packages. Scripts in `toolbox` reference this directory when
creating release tarballs.

## doc
Documentation including the GPL license and changelog. Packaging scripts bundle this folder as part of the
distribution.

## postrun
Scripts placed here run after `ocs-sr` starts if the `-o1` option is enabled. The
README in this directory explains the requirement:
```
# The scripts in this direcoty will be run by run-parts comamnd AFTER ocs-sr starts.
# //NOTE//:
# (1) You need to enable the option "-o1" otherwise it won't work.
# (2) The scripts here is nothing to do with the option "-p" or "--postaction" of ocs-sr, and they will be run before that assigned in -p or --postaction."
```
【F:postrun/ocs/00-readme.txt†L1-L4】

## prerun
Scripts executed before `ocs-sr` when `-o1` is enabled. The README states:
```
# The scripts in this direcoty will be run by run-parts comamnd BEFORE ocs-sr starts.
# //NOTE//:
# You need to enable the option "-o1" otherwise it won't work.
```
【F:prerun/ocs/00-readme.txt†L1-L3】

## samples
Examples demonstrating custom Clonezilla workflows. They often call programs from
`sbin`. For instance, `samples/gen-rec-iso` builds an `ocs-iso` command:
```
ocs_iso_cmd="ocs-iso $extra_boot_param_opt -g en_US.UTF-8 -t -k NONE -e \"-g auto -e1 auto -e2 $ocs_imgrest_batch_opt -r -j2 -scr -k1 -p $postaction restoredisk $dest_fname $preset_dest_dev\" $dest_fname"
```
【F:samples/gen-rec-iso†L179-L180】

## sbin
The primary Clonezilla commands such as `clonezilla`, `ocs-sr`, and `ocs-iso`. These scripts load settings from
`conf/drbl-ocs.conf` and function libraries from `scripts/sbin`. Example lines from
`sbin/clonezilla` illustrate the sourcing order:
```
# Load DRBL setting and functions
DRBL_SCRIPT_PATH="${DRBL_SCRIPT_PATH:-/usr/share/drbl}"
. $DRBL_SCRIPT_PATH/sbin/drbl-conf-functions
. /etc/drbl/drbl-ocs.conf
. $DRBL_SCRIPT_PATH/sbin/ocs-functions
```
【F:sbin/clonezilla†L5-L10】

## scripts
Library functions stored under `scripts/sbin`. They are sourced by commands in the `sbin` folder to provide
common utilities.

## setup
Files used to build Clonezilla or DRBL live systems, including init scripts under `setup/files/ocs`. They also
load `drbl-conf-functions` and `ocs-functions` from `scripts/sbin`.

## toolbox
Helper scripts for packaging Clonezilla into tarballs, debs or RPMs. `toolbox/packit.sh` lists several
directories—including `doc`, `sbin`, `samples`, `prerun`, and `postrun`—that are bundled when creating a release:
```
PKG="clonezilla"
FILES_DIRS="Makefile clonezilla.spec conf doc samples sbin bin scripts setup prerun postrun"
```
【F:toolbox/packit.sh†L4-L6】

