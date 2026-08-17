# Network Mapping Objective
- Discovery of live hosts: active devices and hosts on the network
- Identifying open ports and services
- Network topology mapping: creating a map of the network (topology, including routers, switches, firewalls...)
- Operating system fingerprinting: determining the OS running on the hosts discovered
- Service version detection: identifying the specific version of a service running on open ports
- Identifying filtering and security measures: discovering firewalls, IPS, and others

---

## Host Discovery

Goal: determine which hosts are alive on the network, before doing any port/service scanning.

```bash
ping <target>

fping -I eth1 -g <target/NETWORK> -a
fping -I eth1 -g <target/NETWORK> -a 2>/dev/null

nmap -sL <target>                # List targets to scan (no actual scan)
nmap -sn <target>                # Nmap ping scan (ARP if on same subnet)
nmap -sn <target> --send-ip      # Force ICMP even on same subnet
nmap -sn -iL target.txt          # Ping scan against a list of targets from a file
nmap -sn -PS<port> <target>      # SYN ping scan (default port 80)
nmap -sn -PA <target>            # ACK ping
nmap -sn -PE <target> --send-ip  # ICMP ping
nmap -sn -PS21,22,25,80,445,3389,8080 -T4 <target>  # Faster scan on common ports

netdiscover -i eth1 -r <target/NETWORK>  # ARP scan
```

---

## Host / Port Scanning

Goal: once live hosts are known, identify open ports and running services on them.

```bash
nmap <scan_options> <target>   # General syntax

nmap -Pn -F <target>    # Fast scan on the 100 most common ports instead of the default 1000
nmap -Pn -sT <target>   # TCP connect scan
nmap -Pn -sS <target>   # SYN scan (stealthier than -sT)
nmap -Pn -sC <target>   # Run default NSE scripts (same as --script=default)
```

## Services version & OS detection

Goal:

```bash
nmap -T4 -sS -sV -p- <target>  # Service and version detection
nmap -T4 -sS -sV -O -p- <target>  # No exact OS match but give us a TCP/IP fringerprint
nmap -T4 -sS -sV -O -p- <target>  # No exact OS match but give us a TCP/IP fringerprint
nmap -T4 -sS -sV --version-intensity <level> -O --osscan-guess -p- <target>  # version intensity 0-8

```