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

