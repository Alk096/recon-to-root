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
nmap -Pn --traceroute <target>  # Trace the network path to the target
```

---

## Service Version & OS Detection

Goal: fingerprint the OS and identify exact service versions on open ports.

```bash
nmap -T4 -sS -sV -p- <target>       # Service and version detection

nmap -T4 -sS -sV -O -p- <target>    # No exact OS match, but provides a TCP/IP fingerprint

nmap -T4 -sS -sV --version-intensity <level> -O --osscan-guess -p- <target>  # Version intensity 0-8 (higher = more accurate, slower)
```

### Nmap Scripting Engine (NSE)

```bash
nmap -T4 -sS -sV -sC -p- <target>          # Run default NSE scripts on open ports

ls /usr/share/nmap/scripts                  # List all available scripts
nmap --script-help=<script>                 # Show details about a specific script

nmap -T4 -sS -sV --script=<script> -p- <target>                    # Run a specific script on open ports
nmap -T4 -sS -sV --script=<script>,<another_script> -p- <target>   # Run multiple scripts on open ports
nmap -T4 -sS -sV --script=ftp-* -p- <target>                       # Run all FTP-related scripts
```


## Firewall Detection & IDS Evasion

```bash
nmap -Pn -sA -p<port> <target>
# ACK scan: tells us whether a port is filtered or unfiltered (does not reveal open/closed)

nmap -Pn -sS -F -f <target>
# Fragment packets for firewall & IDS evasion

nmap -Pn -sS -F -f --mtu <8-?> <target>
# Set a custom Maximum Transmission Unit (must be a multiple of 8) for finer control over fragment size

nmap -Pn -sS -sV -p<port> -f --data-length 200 -D <decoy1>,<decoy2> <target>
# Fragment packets, pad them with 200 extra bytes to obscure the nmap signature, and use decoy IPs to hide the real scanning source

nmap -Pn -sS -sV -p<port> -f --data-length 200 -g <port> -D <decoy1>,<decoy2> <target>
# Same as above, plus spoof the source port (-g) to a commonly trusted port (e.g. 53, 80) to slip past simple port-based firewall rules
```

## Optimizing nmap scan

```bash
nmap -Pn -sS -sV -p<port> --host-timeout <5s|5m|5h> <target>
# Give up on a host if it takes longer than the specified time (accepts s/m/h suffixes) — avoids wasting time on unresponsive hosts

nmap -sS -sV -F --scan-delay 5s <target>
# Wait 5 seconds between each probe — slows the scan down deliberately to stay under IDS detection thresholds

nmap -sS -sV -F -f -T1 <target>
# Combine packet fragmentation with a slow timing template (T1) for a stealthier, IDS-evasive scan
```

## Nmap output format

```bash
nmap -Pn -sS -F -T4 <target> -oN nmap_normal.txt
# Normal format — human-readable, same as standard terminal output

nmap -Pn -sS -F -T4 <target> -oX nmap_xml.xml
# XML format — structured, can be imported into Metasploit and other tools

nmap -Pn -sS -F -T4 <target> -oS nmap_script_kiddie.txt
# Script kiddie format — same as normal output but in "l33t speak", novelty/joke format

nmap -Pn -sS -F -T4 <target> -oG nmap_grep.txt
# Grepable format — one line per host, easy to parse with grep/awk/cut

nmap -Pn -sS -F -T4 <target> -oA nmap_all
# Output in all three major formats at once (normal, XML, grepable) using a shared filename prefix
```
