## Bash Command Reference

```sh
# Returns useful information about the specific flavour of the OS and its kernel
uname -a

# Install and enable rdp services
sudo apt install xrdp
sudo systemctl enable xrdp
```

### β οΈ Nmap
```sh
# Scan a single target
nmap 10.129.86.241
# Service Version Detection
nmap -sV 10.129.86.241
# Operating System Detection
nmap -O 10.129.86.241
# Run a detailed scan on open ports
nmap 10.10.11.125 -sV -sC -p22,80,1337 -T4
```
### π On a vulnerable FTP server which allows anonymous access
```sh
User:  anonymous
Password:  anonymous@domain.com
```
Anonymous FTP is a common way to get access to a server in order to view or download files that are publicly available.

### ποΈ Accessing SMB Shares using `smbclient`

```sh
smbclient \\\\{target_IP}\\{SHARE_NAME}
```

### πΈοΈ Set a static IP address on your Linux machine
```sh
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
# π Web Reconnaissance
+ Enumerate port 80 with `gobuster`
