# Nmap Cheatsheet – CTF & Pentest

## Objective
Nmap is an essential network scanner for discovering hosts, services, and vulnerabilities.
This cheatsheet is designed to be **useful in both CTFs and real pentests**, no fluff.

---

## Host Discovery
```bash
nmap -sn <target>        # Ping scan (discover active hosts)
nmap -Pn <target>        # Skip host discovery (useful if ICMP is blocked)
nmap -PS80,443 <target>  # SYN scan on common ports
```

---

## Basic Scan
```bash
nmap <IP>                # Default scan (top 1000 TCP ports)
nmap -p- <IP>             # Scan all TCP ports
nmap -sU <IP>             # UDP scan
```

---

## Host Discovery Filtering
```bash
nmap --exclude <IP>          # Exclude a single IP
nmap --exclude-file <file>   # Exclude a list of IPs
```

---

## Service Detection
```bash
nmap -sV <IP>             # Version detection
nmap -A <IP>              # Aggressive scan (OS, services, scripts)
nmap -O <IP>              # OS detection
```

---

## Scripting (NSE)
```bash
nmap --script=vuln <IP>       # Vulnerability scripts
nmap --script=http-enum <IP>  # Web directory enumeration
nmap --script=ftp-anon <IP>   # Check for anonymous FTP access
```

---

## Speed & Timing
```bash
nmap -T4 <IP>              # Fast but noisy
nmap -T0 <IP>              # Very slow and stealthy
nmap --min-rate 1000 <IP>  # Force a minimum packet rate per second
```

---

## Output
```bash
nmap -oN result.txt <IP>   # Output in plain text
nmap -oX result.xml <IP>   # Output in XML
nmap -oG result.grep <IP>  # Output in greppable format
```

---

## Scanning Against a Firewall
```bash
nmap -Pn <target>          # Skip host discovery (ICMP blocked)
nmap -sA <target>          # ACK scan (detects firewall filtering)
nmap -sF <target>          # Stealthy FIN scan
nmap -sN <target>          # Stealthy NULL scan
nmap -sX <target>          # Stealthy Xmas scan
nmap -f <target>           # Fragment packets
nmap -D RND:10 <target>    # Generate decoy IPs
```

---

## Misc
```bash
nmap -v <IP>               # Verbose mode
nmap --reason <IP>         # Explain why a port is open/closed
nmap --top-ports 100 <IP>  # Scan the 100 most common ports
```

---

## Practical Tips
- Always start with a **full port scan** (`-p-`) so nothing gets missed.
- Follow up with a **targeted scan** (`-sV -A -p <ports>`).
- Use **NSE scripts** to automate vulnerability discovery.
- Adjust speed (`-T`) depending on context (fast for CTFs vs. stealthy for pentests).
- Save results for later analysis and comparison.
