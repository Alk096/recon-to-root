# Enumeration Objective
- After the host discovery and port scanning phase of a penetration test, the next logical phase involves service enumeration.
- The goal of service enumeration is to gather more specific/detailed information about the hosts/systems on a network and the services running on those hosts.

## Port Scanning & Enumeration with Nmap

```bash
nmap -Pn -sV -O <target> -oX file.xml
# Save nmap output into an XML file (structured format, importable into other tools)
```

## Importing Nmap Scan Results into Metasploit (MSF)

```bash
db_status
# Confirm the PostgreSQL service is running before running any MSF database commands

workspace -h
# Show help/usage for the workspace command (list, add, delete, rename workspaces)

workspace <workspace>
# Switch to a specific workspace, to keep engagement data organized/separated

db_import <path>
# Import a previously saved Nmap XML output into the current MSF workspace

hosts
# List all hosts currently stored in the workspace database

services
# List all services discovered and stored in the workspace database

db_nmap -Pn -sV -O <target>
# Run an Nmap scan directly from within msfconsole, automatically importing the results into the current workspace

vulns
# List vulnerabilities discovered and recorded in the current workspace
```

## Port Scanning with Auxiliary Modules

**Note**
- Auxiliary Modules are used to perform functionality like scanning, discovery, and fuzzing.

```bash
search portscan
# Search MSF's module database for available port scanning modules

use auxiliary/scanner/portscan/<syn|ack|tcp>
# Load a specific port scanning module (SYN, ACK, or TCP connect scan)

show options
# Display the required/optional settings for the currently loaded module

run autoroute -s <target>
# Run the autoroute Meterpreter script to pivot: adds a route through the compromised host so MSF can scan/reach the internal network behind it (run from within a Meterpreter session)

use auxiliary/scanner/portscan/tcp
# Load the TCP port scan module — typically used after backgrounding the Meterpreter session (Ctrl+Z), so the newly added route via autoroute can be leveraged to scan the pivoted network

use auxiliary/scanner/discovery/udp_sweep
# Load the UDP sweep module to discover live hosts/services over UDP

set RHOST <target>
# Set the target IP/range for the currently loaded module

set RHOSTS <target_range>
# Set multiple targets (subnet/range) — most scanner modules use RHOSTS rather than RHOST

run
# Execute the currently loaded and configured module
```
