# Malicious URL & Phishing Infrastructure Analysis

Analyzing live phishing deployments to extract Indicators of Compromise (IOCs), map adversarial hosting infrastructure, and draft an enterprise-level incident triage report.

## 🧰 Tools Utilized

* **PhishTank:** For threat identification and capturing live, active phishing URLs.
* **VirusTotal:** For cross-referencing malicious domains against global threat intelligence feeds and reputation databases.
* **MXToolbox (DNS/WHOIS Lookup):** For domain name system resolution, identifying hosting providers, and checking registrar records.

---

## 🔍 Workflow & Analysis Steps

### 1. Threat Identification & Sourcing
I isolated an active, online credential-harvesting campaign from the PhishTank global threat stream targeting financial or trust institutions under **Submission #9458368**. The target threat vector is the live malicious root domain: `capital-trustblank.online`.

<img width="2850" height="1557" alt="image" src="https://github.com/user-attachments/assets/ff4ddae2-e31e-458f-9131-42a4d2482926" />

### 2. Threat Intelligence Reputation Audit
With the target domain identified, I immediately queried VirusTotal to cross-reference the component against upstream security vendor databases. This scan provides initial data on whether global firewall networks, web proxies, and security providers have already actively blacklisted this asset.

> **[ 🖼️ INSERT SCREENSHOT 2 HERE ]**
> *(Note for Zavier: Grab a screenshot of your VirusTotal results page highlighting the red flags, detection ratio, and specific malicious categorizations).*

### 3. Infrastructure Tracing & IP Resolution
To uncover where the adversary is hosting this phishing campaign, I ran the domain through MXToolbox's DNS and WHOIS query tools. This allowed me to resolve the domain to its true destination IP address, identify the hosting provider/Autonomous System Number (ASN), and analyze the domain registration date.

> **[ 🖼️ INSERT SCREENSHOT 3 HERE ]**
> *(Note for Zavier: Snag a screenshot of the MXToolbox DNS or WHOIS results page clearly showing the resolved IP address and hosting network provider of the website).*

### 4. Operational Security (OpSec) Defanging
To ensure absolute safety during documentation and prevent accidental execution of the malicious asset, I extracted the suspicious strings and processed them into a defanged format. This converts the link into plain text, rendering it completely unclickable in standard markdown viewers.

* **Raw Malicious URL:** `https://capital-trustblank.online/`
* **Defanged Operational URL:** `hxxps://capital-trustblank[.]online/`

> **[ 🖼️ INSERT SCREENSHOT 4 HERE ]**
> *(Note for Zavier: Take a snippet of a text editor showing your raw URL processed into this safely defanged version).*

---

## 📄 Final Deliverable

### Security Incident Triage Report
Utilizing the telemetry extracted during infrastructure tracking, I authored a corporate security triage brief. This report outlines the technical findings, active Indicators of Compromise (IOCs), and provides recommended firewall and proxy blocking configurations to defend an enterprise network.

> **[ 📁 LINK TO YOUR COMPLETED REPORT PDF HERE ]**
> *(Note for Zavier: Save your written report as a PDF, commit it to this GitHub directory, and link the file location right here).*
