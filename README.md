## Bash Command Reference

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
```

### ☠️ Nmap
```sh
# Scan a single target
nmap 10.129.86.241/24
# Service Version Detection
nmap -sV 10.129.86.241
# Operating System Detection
nmap -O 10.129.86.241
# Run a detailed scan on open ports
nmap 10.10.11.125 -sV -sC -p22,80,1337 -T4
# Scan a server for open ports, find what version of software is running and what OS it is and saving it to a file named nmap_scan.txt
nmap -sV -O -oN nmap_scan.txt 10.10.226.53
# Scan a server for open ports, find what version of software is running, scan all ports (not just the common ports, so this will take more time)
# Treat all host as online (useful if scan is being blocked by firewall)
nmap -sV -p- -Pn 10.10.226.53
```
### 📁 On a vulnerable FTP server which allows anonymous access
```sh
User:  anonymous
Password:  anonymous@domain.com
```
Anonymous FTP is a common way to get access to a server in order to view or download files that are publicly available.

### 🗄️ Accessing SMB Shares using `smbclient`

```sh
smbclient \\\\{target_IP}\\{SHARE_NAME}
```

### 🕸️ Set a static IP address on your Linux machine
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
# 🌎 Web Reconnaissance
+ Enumerate port 80 with `gobuster`
```sh
gobuster dir -u http://10.10.226.146/ -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -o gobuster_scan.txt

```

# ⚔️ XSS
```js
// Inside of input field the following command will help find XSS by creating a simple alert
<script>alert(1)</script>

```
Add the payload in the URL
```sh
# Exploiting a vulnerable URL parameter and alerting the users cookie
http://10.10.226.56/vulnerabilities/xss_r/?name=<script>alert(document.cookie)</script>
```
