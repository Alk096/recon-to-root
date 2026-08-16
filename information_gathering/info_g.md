# Information Gathering

## Objective
Learn as much information as possible about the target before any exploitation phase.

## Target Scoping
Scoping answers one simple question:
> **What am I allowed to target?**

## Passive vs Active Reconnaissance

### Passive reconnaissance
Involves collecting information **without directly interacting** with the target systems (OSINT, public DNS, open sources...).

### Active reconnaissance
Involves **direct interaction** with the target systems (port scanning, service enumeration...).

---

## Four-Step Strategy for Every Engagement

### Step 1: Define the target
- Identify the domain
- Confirm what is in scope (in-scope / out-of-scope)

### Step 2: Perform passive reconnaissance
- Gather public information
- Identify potential attack surfaces
- Build initial understanding of the target

### Step 3: Perform active reconnaissance
- Discover live hosts
- Identify open ports
- Detect exposed services

### Step 4: Document & organize your findings
- Record domains, IPs, and ports
- Prepare information for enumeration
- Avoid repeating work later

---

## Passive Reconnaissance

### Website Recon & Footprinting

| Technique | Command / Location |
|---|---|
| DNS query | `host <domain>` |
| Robots file | `<domain>/robots.txt` |
| Sitemap | `<domain>/sitemap.xml` |
| Browser extensions | BuiltWith, Wappalyzer |
| Passive scanner | `whatweb <domain>` |
| Offline site copy | HTTrack |
| Domain registration lookup | `whois <domain>` |

**Notes:**
- `robots.txt` can reveal paths the admin wants hidden from search engines (often a good lead).
- `sitemap.xml` lists indexable pages — useful for mapping the site's structure.
- `BuiltWith` / `Wappalyzer` identify the technologies in use (CMS, framework, server-side language, etc.) without extra active requests.
- `HTTrack` downloads the site locally: useful for analyzing source code offline, without generating repeated traffic to the target.
- `whois` is a query/response protocol used to retrieve registration information about internet resources such as domain names, IP addresses, and autonomous systems.

### Website Footprinting with Netcraft

| URL | Role |
|---|---|
| https://sitereport.netcraft.com/ | Generates a site report (hosting provider, IP, technologies, SSL info). Netcraft specializes in digital risk protection and cybercrime disruption. |

### DNS Recon

| Command / URL | Purpose |
|---|---|
| `dnsrecon --help` | Show available options |
| `dnsrecon -d <domain>` | Gather DNS info about the target (A, MX, NS, TXT records, etc.) |
| https://dnsdumpster.com | DNS recon & research tool — find and look up DNS records |

### Web Application Firewall (WAF) Detection

| Command | Purpose |
|---|---|
| `wafw00f <domain>` | Detect whether the target is behind a WAF |
| `wafw00f <domain> -a` | Test against all known WAF signatures |

**Note:**
- GitHub repo: https://github.com/EnableSecurity/wafw00f

### Subdomain Enumeration with Sublist3r

| Command | Purpose |
|---|---|
| `sublist3r -d <domain>` | Enumerate subdomains using all supported search engines |
| `sublist3r -d <domain> -e yahoo,google` | Enumerate subdomains using specific engines only |

**Note:**
- GitHub repo: https://github.com/aboul3la/Sublist3r
- Has a bruteforce option, which is **not** passive reconnaissance (it sends direct DNS requests).
- Using a free VPN can help avoid rate-limiting when relying on the Google search engine.

### Google Dorking

Google dorking uses advanced search operators to find exposed information indexed by Google (files, login pages, error messages, misconfigurations...).

See the dedicated file **[`dork.md`](./dork.md)** for a comprehensive list of dorks.

**Note**
- Wayback Machine : https://web.archive.org/ for target old versions of the target

## Active Reconnaissance

### Dns zone transfers

| DNS Records | Purpose |
|---|---|
| A | Resolve a hostname or domaine to an ipv4 addresses |
| AAAA | Resolve a hostname or domaine to an ipv6 addresses| 
| NS | Reference to the domaine nameserver |
| MX | Resolve domain to a mail server |
| CNAME | Used for domain aliases |
| TXT | Text record |
| HIFO | Host iformation |
| SOA | Domain authority |
| SRV | Service record |
| PTR | Resolve an IP address to a hostname |

**Note**
- `dnsenum` and `dig` commands can also return some interesting stuff
- check for `fierce` command for more
