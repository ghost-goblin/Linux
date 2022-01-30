## Bash Command Reference

```sh
# Returns useful information about the specific flavour of the OS and its kernel
uname -a

# Install and enable rdp services
sudo apt install xrdp
sudo systemctl enable xrdp
```

### ☠️ Nmap
```sh
# Scan a single target
nmap 10.129.86.241
# Service Version Detection
nmap -sV 10.129.86.241
```
