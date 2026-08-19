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

## FTP Enumeration

```bash
use auxiliary/scanner/portscan/tcp
set RHOSTS <target>
run
# Confirm which ports are open on the target before diving into FTP-specific enumeration

search type:auxiliary name:ftp
# Search MSF's module database for all auxiliary modules related to FTP

use auxiliary/scanner/ftp/ftp_version
# FTP version detection — banner-grabs the FTP daemon version, useful to match against known vulnerabilities

search ProFTPD
# Search for exploits/info related to ProFTPD, a commonly vulnerable FTP server software (many known CVEs across versions)

use auxiliary/scanner/ftp/ftp_login
# Authentication scanner — attempts to brute-force valid FTP credentials

set USER_FILE /usr/share/metasploit-framework/data/wordlists/common_users.txt
# Path to the username wordlist used by the login scanner

set PASS_FILE <path>
# Path to the password wordlist used by the login scanner (e.g. /usr/share/metasploit-framework/data/wordlists/common_passwords.txt)

set RHOSTS <target>
run
# Set the target and launch the brute-force attempt
```

**Note:**
- Anonymous FTP login (`anonymous:anonymous` or blank password) is a very common misconfiguration — always test this manually first before brute-forcing:
```bash
ftp <target>
# Username: anonymous
# Password: anonymous (or blank)
```

## SMB Enumeration
```bash
setg RHOSTS <target>
# Set a global variable for the target IP address to avoid retyping RHOSTS across different Metasploit modules

search type:auxiliary name:smb
# Search MSF's module database for all SMB-related scanner and enumeration auxiliary modules

use auxiliary/scanner/smb/smb_version
# SMB version detection — identifies the exact version of the running SMB/Samba service

use auxiliary/scanner/smb/smb_enumusers
# User enumeration — attempts to enumerate valid domain or local user accounts on the host

use auxiliary/scanner/smb/smb_enumshares
# Share enumeration — lists available network shares and their read/write access permissions

use auxiliary/scanner/smb/smb_login
# Authentication scanner — tests credential combinations or performs brute-force attacks against SMB

info
# Displays detailed documentation, required options, and settings for the active module

nmap -Pn -sV --script smb-os-discovery <target>
# Nmap discovery — skips ping host discovery (-Pn), identifies service versions (-sV), and extracts OS details via SMB

smbclient -L \\\\<target>\\ -U <user>
# Lists all available network shares on the target using specific user credentials

smbclient \\\\<target>\\<share> -U <user>
# Connects directly to a specific share using the provided user credentials

smbclient -L \\\\<target>\\ -N
# Anonymous smbclient test — attempts to list network shares without providing credentials (Null Session)

rpcclient -U "" -N <target>
# Null Session test via rpcclient — verifies whether the SMB server permits unauthenticated RPC access

srvinfo
# Interactive rpcclient command — displays server details including hostname, OS, and domain information

enumdomusers
# Interactive rpcclient command — enumerates all domain or local users registered on the server
```

## Web Server Enumeration
```bash
search type:auxiliary name:http
# Search MSF's module database for all HTTP-related auxiliary modules

setg RHOSTS <target>
# Set a global variable for the target IP address to avoid retyping RHOSTS across different Metasploit modules

use auxiliary/scanner/http/http_version
# HTTP version detection — identifies the web server software and version via banner/response fingerprinting

use auxiliary/scanner/http/http_header
# Header scanner — retrieves and displays the full set of HTTP response headers (can reveal server, framework, cookies, security headers)

use auxiliary/scanner/http/robots_txt
# Robots.txt scanner — fetches and parses robots.txt, revealing paths the admin wants excluded from search engines (often a good recon lead)

use auxiliary/scanner/http/dir_scanner
# Directory scanner — brute-forces common directory names to discover hidden/unlinked paths on the web server

use auxiliary/scanner/http/files_dir
# File scanner — brute-forces common filenames within directories to discover exposed files

use auxiliary/scanner/http/apache_userdir_enum
# Apache user directory enumeration — checks for the presence of ~username personal directories (mod_userdir), useful for username enumeration

use auxiliary/scanner/http/http_login
# HTTP authentication scanner — brute-forces credentials against HTTP Basic/Digest authentication login forms
```

## MySQL Enumeration
```bash
search type:auxiliary name:mysql
# Search MSF's module database for all MySQL-related auxiliary modules

use auxiliary/scanner/mysql/mysql_version
# MySQL version detection — banner-grabs the MySQL server version without requiring credentials

use auxiliary/scanner/mysql/mysql_login
# Authentication scanner — brute-forces MySQL credentials (requires username/username_file and pass/pass_file options)

use auxiliary/admin/mysql/mysql_enum
# Enumerates MySQL server info (users, privileges, password hashes, config variables) — requires valid MySQL credentials

use auxiliary/admin/mysql/mysql_sql
# Executes arbitrary SQL commands against the server — requires valid MySQL credentials

use auxiliary/scanner/mysql/mysql_schemadump
# Dumps the full database schema (databases, tables, columns) — requires valid MySQL credentials

services
# MSF command — lists all services discovered and stored in the current workspace database

loot
# MSF command — lists collected loot (dumped files, hashes, schemas, etc. saved during the engagement)

creds
# MSF command — lists all credentials discovered/stored in the current workspace database
```

## SSH Enumeration
```bash
setg RHOSTS <target>
# Set a global variable for the target IP address to avoid retyping RHOSTS across different Metasploit modules

search type:auxiliary name:ssh
# Search MSF's module database for all SSH-related auxiliary modules

use auxiliary/scanner/ssh/ssh_version
# SSH version detection — banner-grabs the SSH server/daemon version without requiring credentials

use auxiliary/scanner/ssh/ssh_enumusers
# User enumeration — exploits timing differences in SSH auth responses to guess valid usernames (works on some vulnerable OpenSSH versions)

use auxiliary/scanner/ssh/ssh_login
# Authentication scanner — brute-forces SSH credentials with username/password (automatically opens a session on success)

use auxiliary/scanner/ssh/ssh_login_pubkey
# Public key authentication scanner — tests a private key file against the target to see if it grants SSH access

/bin/bash -i
# Spawn an interactive bash shell — commonly used to upgrade a raw/limited shell into a fully interactive one after gaining access
```
