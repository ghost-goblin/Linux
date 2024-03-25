## [System Management](domian01.md)
### Filesystem Hierarchy Standard (FHS)
  - /boot
    + Static Boot Files
  - /proc
    + Kernel and processes information
  - /sys
    + Hotplug hardware devices
  - /var
    + Variable files (logs, caches, mail spools, etc.)
    + `cd /var/log/`
    + `/var/log/httpd`: Contains HTTP Request  / Response and error logs
    + `/var/log/cron`: Events related to cron jobs are stored in this location
    + `/var/log/auth.log` and `/var/log/secure` : Stores authentication related logs
    + `/var/log/kern`: This file stores kernel related events
  - /usr
  - /lib
  - /dev
  - /etc
  - /opt
  - /bin
  - /sbin
  - /home
  - /media
  - /mnt
  - /root
  - /tmp

### Basic boot process
- Basic input/output system (BIOS)
- Unified Extensible Firmware
+ Interface (UEFI)
- Commands
  + mkinitrd
  + grub2-install
  + grub2-mkconfig
  + grub2-update
  + dracut
- initrd.img
- vmlinuz
- Grand Unified Bootloader version 2 (GRUB2)
- Boot sources
+ Preboot eXecution
Environment (PXE)
+ Booting from Universal
Serial Bus (USB)
+ Booting from ISO
### Kernel panic
### Device types in `/dev`
- Block devices
- Character devices
- Special character devices
+ /dev/null
+ /dev/zero
+ /dev/urandom
### Basic package compilation from source
- `./configure`
- make
- make install
### Storage concepts
- File storage
- Block storage
- Object storage
- Partition typo
+ Master boot record (MBR)
+ GUID [globally unique identifier]
+ Partition Table (GPT)
- Filesystem in Userspace (FUSE)
- Redundant Array of Independent (or Inexpensive) Disks (RAID) levels
  + Striping
  + Mirroring
  + Parity
### Listing hardware information
- lspci
- lsusb
- dmidecode
