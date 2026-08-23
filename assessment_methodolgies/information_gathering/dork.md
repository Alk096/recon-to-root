# Google Dorking Cheat Sheet

Reference list of Google search operators ("dorks") for passive reconnaissance / OSINT. Combine operators to narrow results, e.g. `site:example.com filetype:pdf`.

## Core Operators

| Operator | Purpose |
|---|---|
| `site:` | Restrict results to a specific domain |
| `inurl:` | Search for a keyword in the URL |
| `intitle:` | Search for a keyword in the page title |
| `intext:` / `allintext:` | Search for a keyword in the page body |
| `filetype:` / `ext:` | Search for a specific file extension |
| `cache:` | Show Google's cached version of a page |
| `link:` | Find pages linking to a URL (largely deprecated) |
| `related:` | Find sites related to a given domain |
| `-` (minus) | Exclude a term from results |
| `"..."` | Exact phrase match |
| `*` | Wildcard placeholder |
| `OR` / `\|` | Logical OR between terms |
| `..` | Numeric range, e.g. `2015..2020` |

---

## Site & Subdomain Discovery

- `site:example.com`
- `site:*.example.com`
- `site:example.com -www`
- `site:example.com -inurl:www`

## Login Pages & Admin Panels

- `site:example.com inurl:login`
- `site:example.com inurl:admin`
- `site:example.com intitle:"admin login"`
- `site:example.com inurl:signin`
- `site:example.com inurl:wp-admin`
- `site:example.com inurl:cpanel`
- `site:example.com intitle:"index of" inurl:admin`

## Directory Listings

- `site:example.com intitle:"index of"`
- `site:example.com intitle:"index of" "parent directory"`
- `site:example.com intitle:"index of" backup`
- `site:example.com intitle:"index of" .git`
- `site:example.com intitle:"index of" .env`
- `site:example.com intitle:"index of" config`

## Sensitive Files

- `site:example.com filetype:pdf`
- `site:example.com filetype:doc OR filetype:docx`
- `site:example.com filetype:xls OR filetype:xlsx`
- `site:example.com filetype:ppt OR filetype:pptx`
- `site:example.com filetype:txt`
- `site:example.com filetype:log`
- `site:example.com filetype:sql`
- `site:example.com filetype:bak`
- `site:example.com filetype:env`
- `site:example.com filetype:xml`
- `site:example.com filetype:json`
- `site:example.com filetype:conf OR filetype:cfg OR filetype:ini`
- `site:example.com filetype:yml OR filetype:yaml`
- `site:example.com ext:php intitle:"index of"`

## Configuration & Credential Exposure

- `site:example.com inurl:wp-config.php`
- `site:example.com inurl:.env`
- `site:example.com filetype:env "DB_PASSWORD"`
- `site:example.com inurl:config.php`
- `site:example.com "password" filetype:log`
- `site:example.com "username" "password" filetype:xls`
- `site:example.com inurl:.git`
- `site:example.com inurl:.svn`
- `site:example.com inurl:.htpasswd`
- `site:example.com intext:"BEGIN RSA PRIVATE KEY"`
- `site:example.com intext:"DB_PASSWORD" OR intext:"DB_USERNAME"`

## Error Messages / Stack Traces (info leakage)

- `site:example.com intext:"Warning: mysql_connect()"`
- `site:example.com intext:"Fatal error" "on line"`
- `site:example.com intext:"ORA-01756"`
- `site:example.com intext:"SQL syntax" "MySQL"`
- `site:example.com "Microsoft OLE DB Provider for SQL Server" error`
- `site:example.com intext:"stack trace"`

## Exposed Databases / Backups

- `site:example.com filetype:sql "INSERT INTO"`
- `site:example.com filetype:sql "CREATE TABLE"`
- `site:example.com filetype:bak inurl:backup`
- `site:example.com inurl:backup filetype:zip OR filetype:tar OR filetype:gz`
- `site:example.com filetype:mdb`

## Cloud Storage Buckets

- `site:s3.amazonaws.com "example.com"`
- `site:blob.core.windows.net "example.com"`
- `site:storage.googleapis.com "example.com"`
- `intitle:"index of" site:s3.amazonaws.com`
- `inurl:amazonaws.com filetype:env`

## Network & Infrastructure Info

- `site:example.com intitle:"webcamXP"`
- `site:example.com intitle:"router" intext:"login"`
- `site:example.com inurl:phpinfo`
- `site:example.com filetype:php intitle:"phpinfo()"`
- `site:example.com inurl:server-status` (Apache mod_status)
- `site:example.com inurl:server-info`

## VPN / Remote Access

- `site:example.com inurl:vpn`
- `site:example.com intitle:"remote desktop web connection"`
- `site:example.com inurl:owa` (Outlook Web Access)
- `site:example.com inurl:webmail`

## API Keys & Tokens

- `site:example.com intext:"api_key"`
- `site:example.com intext:"apikey" filetype:json`
- `site:example.com intext:"aws_access_key_id"`
- `site:example.com intext:"client_secret"`
- `site:pastebin.com "example.com" api_key`

## Documents Mentioning Employees / Emails

- `site:example.com filetype:pdf "confidential"`
- `site:example.com intext:"@example.com" filetype:xls`
- `site:linkedin.com "example.com" intitle:"employee"`
- `site:example.com filetype:doc "internal use only"`

## CMS-Specific Dorks

**WordPress**
- `site:example.com inurl:wp-content`
- `site:example.com inurl:wp-includes`
- `site:example.com inurl:wp-login.php`
- `site:example.com inurl:xmlrpc.php`

**Joomla**
- `site:example.com inurl:/administrator/`
- `site:example.com inurl:com_ AND inurl:controller`

**Drupal**
- `site:example.com inurl:CHANGELOG.txt "Drupal"`
- `site:example.com inurl:user/login`

## Third-Party / Paste Sites (breach & leak hunting)

- `site:pastebin.com "example.com"`
- `site:trello.com "example.com"`
- `site:github.com "example.com" password`
- `site:github.com "example.com" api_key`
- `site:gitlab.com "example.com" secret`
- `site:stackoverflow.com "example.com" error`

## Combined / Useful Chains

- `site:example.com (inurl:login OR inurl:admin OR inurl:signin)`
- `site:example.com filetype:pdf OR filetype:doc OR filetype:xls "confidential"`
- `site:example.com intitle:"index of" (password OR credentials OR secret)`
- `site:example.com -inurl:www -inurl:https intitle:"index of"`

---

## Notes

- Google dorking is passive: it never touches the target's infrastructure directly, only Google's index.
- Results depend on what Google has crawled and cached — always cross-check for stale/removed content.
- Combine with **Google Hacking Database (GHDB)**: https://www.exploit-db.com/google-hacking-database for maintained, categorized dorks.
- Similar operators exist for Bing (`ip:`, `contains:`) and Shodan (`hostname:`, `port:`, `org:`) — useful complements once Google dorking is exhausted.