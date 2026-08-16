# Nmap Cheatsheet – CTF & Pentest

## Objectif
Nmap est un scanner réseau indispensable pour découvrir les hôtes, services et vulnérabilités.  
Cette cheatsheet est conçue pour être **utile en CTF et en pentest réel**, sans bla-bla.

---

## 🔎 Host Discovery
```bash
nmap -sn <target>        # Ping scan (découverte des hôtes actifs)
nmap -Pn <target>        # Ignore le ping (utile si ICMP bloqué)
nmap -PS80,443 <target>  # SYN scan sur ports courants
```

---

## ⚡ Basic Scan
```bash
nmap <IP>                # Scan par défaut (1000 ports TCP)
nmap -p- <IP>            # Scan de tous les ports TCP
nmap -sU <IP>            # Scan UDP
```

---

## 🧩 Host Discovery Filtering
```bash
nmap --exclude <IP>          # Exclure une IP
nmap --exclude-file <file>   # Exclure une liste d’IP
```

---

## 🔧 Service Detection
```bash
nmap -sV <IP>            # Détection des versions
nmap -A <IP>             # Scan agressif (OS, services, scripts)
nmap -O <IP>             # Détection d’OS
```

---

## 📜 Scripting (NSE)
```bash
nmap --script=vuln <IP>       # Scripts de vulnérabilité
nmap --script=http-enum <IP>  # Enumération des répertoires web
nmap --script=ftp-anon <IP>   # Vérifie l’accès FTP anonyme
```

---

## ⏱️ Speed & Timing
```bash
nmap -T4 <IP>             # Rapide mais bruyant
nmap -T0 <IP>             # Très lent et furtif
nmap --min-rate 1000 <IP> # Force un minimum de paquets/seconde
```

---

## 📤 Output
```bash
nmap -oN result.txt <IP>  # Résultats en texte
nmap -oX result.xml <IP>  # Résultats en XML
nmap -oG result.grep <IP> # Résultats greppables
```

---

## 🛡️ Scan en présence d’un Firewall
```bash
nmap -Pn <target>         # Ignore le ping (ICMP bloqué)
nmap -sA <target>         # ACK scan (détecte filtrage firewall)
nmap -sF <target>         # FIN scan furtif
nmap -sN <target>         # NULL scan furtif
nmap -sX <target>         # Xmas scan furtif
nmap -f <target>          # Fragmentation des paquets
nmap -D RND:10 <target>   # Génère de fausses IP (decoys)
```

---

## 🧰 Misc
```bash
nmap -v <IP>              # Mode verbeux
nmap --reason <IP>        # Explique pourquoi un port est ouvert/fermé
nmap --top-ports 100 <IP> # Scan des 100 ports les plus utilisés
```

---

## 🎯 Conseils pratiques
- Toujours commencer par un **scan complet des ports** (`-p-`) pour ne rien rater.  
- Enchaîner avec un **scan ciblé** (`-sV -A -p <ports>`).  
- Utiliser les **scripts NSE** pour automatiser la recherche de failles.  
- Adapter la vitesse (`-T`) selon le contexte (CTF rapide vs pentest discret).  
- Sauvegarder les résultats pour analyse et comparaison.  

---