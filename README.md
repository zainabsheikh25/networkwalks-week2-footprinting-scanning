# networkwalks-week2-footprinting-scanning
# Week 2: Footprinting & Network Scanning

Penetration testing report for Week 2 of the **Cybersecurity & Ethical Hacking Internship at Networkwalks**.

| | |
|---|---|
| **Name** | Zainab Haider |
| **Date** | 13 November 2026 |
| **Modules** | W2-PM1 (Multiple Kali Tools), W2-PM5 (Zenmap Scanning) |
| **Targets** | networkwalks.com (written permission taken) and my own home LAN |
| **Phases covered** | Phase 1: Reconnaissance & Footprinting, Phase 2: Scanning & Network Discovery |

## What this repo has

```
├── README.md
├── Pentest_Report_W2_with_Zenmap.pdf   Full report (Zenmap PDF attached on the last page)
├── screenshots/                        Evidence screenshots from the practicals
└── zenmap/topology.pdf                 Network topology saved from Zenmap
```

## What I did

### 1. Footprinting on networkwalks.com (Kali Linux)

| Tool | What I used it for |
|---|---|
| `whois` | Domain registration details, registrar and name servers |
| `whatweb` | Website technologies (server, CMS, plugins, IP) |
| `nslookup` | Domain name to IP address |
| `curl -I` | HTTP response headers |
| `wafw00f` | Checking for a Web Application Firewall |
| `dnsrecon` | DNS record enumeration |

### 2. Network scanning on my own LAN (Zenmap)

- Ran a ping scan on my home subnet: `nmap -sn 192.168.1.0/24`
- Found 7 live hosts in 12.59 seconds and noted their IP and MAC addresses
- Opened the Topology tab, turned on the legend and saved the topology as a PDF

## Key findings

- The site runs on **Apache** with **WordPress 7.1.4** and the **WP Download Manager 3.3.76** plugin
- The domain resolves to **192.232.216.135**
- The WordPress REST API link (`/wp-json/`) is visible in the HTTP headers
- The site is protected by a **ModSecurity (SpiderLabs)** WAF
- The domain owner details are hidden behind a privacy service, and DNSSEC is unsigned
- `dnsrecon` timed out because of a DNS problem on my Kali VM, so no DNS records came from that tool
- 3 of the 7 devices on my LAN had an unknown MAC vendor and should be identified

These are observations only. No exploitation or vulnerability testing was done, so none of these are confirmed vulnerabilities.

## Recommendations

- Hide version numbers and keep WordPress and plugins updated
- Remove unneeded information from HTTP headers
- Review DNS records and consider enabling DNSSEC
- Keep the WAF enabled and tuned
- Scan your own network regularly and check unknown devices

The full list is in the report.

## Disclaimer

I did these activities only on systems where I had written permission or on devices that I own. This material is for education and research only. Do not use anything from here to break the law. Unauthorised access is a crime in most countries, and every action you take is your own responsibility.

- Program: Cybersecurity program at Networkwalks | Week 02| B084
