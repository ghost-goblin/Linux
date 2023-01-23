<div align='center'>

# 🐧 [Linux](README.md)

</div>

> Check out the [Linux Guide](https://dr0.ch/docs/linux-guide-10ed.pdf)

## System Management
### Filesystem Hierarchy Standard (FHS)
  - /boot
    + Static Boot Files
  - /proc
    + Kernel and processes information
  - /sys
    + Hotplug hardware devices
  - /var
    + Variable files (logs, caches, mail spools, etc.)
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
### Interface (UEFI)
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
• Preboot eXecution
Environment (PXE)
+ Booting from Universal
Serial Bus (USB)
+ Booting from ISO
+ Kernel panic
+ Device types in /dev
- Block devices
- Character devices
- Special character devices
• /dev/null
• /dev/zero
• /dev/urandom
• Basic package compilation from source
- `./configure`
- make
- make install
• Storage concepts
- File storage
- Block storage
- Object storage
- Partition typo
+ Master boot record (MBR)
+ GUID [globally unique identifier]
### Partition Table (GPT)
- Filesystem in Userspace (FUSE)
- Redundant Array of
### Independent (or Inexpensive)
### Disks (RAID) levels
• Striping
• Mirroring
• Parity
• Listing hardware information
- lspci
- lsusb
- dmidecode

- - -

### 🖥️ Lab Setup

```sh
# Returns useful information about the specific flavour of the OS and its kernel
uname -a

# Prints out a routing table
netstat -rn
ip route

# Add route to routing table
ip route add 192.168.222.52 via 10.175.30.1

# Install and enable rdp services
sudo apt install xrdp
sudo systemctl enable xrdp

# Set a static IP address on your Linux machine
sudo nano /etc/network/interfaces
## Add the following config: 
auto eth0
iface eth0 inet static
        address 192.168.1.215/24
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        dns-nameservers 192.168.1.254
```

# 🕸️ Enumeration
### ☠️ **Nmap**
```sh
# Scan a single target
nmap 10.129.86.241/24
# Service Version Detection
nmap -sV 10.129.86.241
# Operating System Detection
nmap -O 10.129.86.241
# Run a detailed scan on open ports
nmap 10.10.11.125 -sV -sC -p22,80,1337 -T4
# Scan a server for open ports + running software version + OS + save to file named nmap_scan.txt
nmap -sV -O -oN nmap_scan.txt 10.10.226.53
# Scan server for ALL open ports + find what version of software is running (will take more time)
# Treat all host as online (useful if scan is being blocked by firewall)
nmap -sV -p- -Pn 10.10.226.53
```

### Metasploit Framework

```sh
# Initialise the database
sudo msfdb init
msfconsole -q
```

### 🚩 **Banner Grabbing**
```sh
echo " " | nc -v 10.10.226.5 80
```
### 📁 **Directory Scanning**
+ Enumerate web server on port 80 with `gobuster`
```sh
gobuster dir -u http://10.10.226.146/ -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -o gobuster_scan.txt
```

- - -

# 🌎 Web Hacking
### 📡 **OWASP ZAP**
[OWASP ZAP](https://www.zaproxy.org/) is an open-source web application security scanner
### ⚔️ **XSS**
```js
// Inside of input field the following command will help find XSS by creating a simple alert
<script>alert(1)</script>
```
Add the payload in the URL
```sh
# Exploiting a vulnerable URL parameter and alerting the users cookie
http://10.10.226.56/vulnerabilities/xss_r/?name=<script>alert(document.cookie)</script>
```


- - -


# 🗄️ SMB Hacking
### Accessing SMB Shares using `smbclient`
```sh
smbclient \\\\{target_IP}\\{SHARE_NAME}
```

- - -

# 📁 FTP Hacking
### On a vulnerable FTP server which allows anonymous access
```sh
User:  anonymous
Password:  anonymous@domain.com
```
Anonymous FTP is a common way to get access to a server in order to view or download files that are publicly available


