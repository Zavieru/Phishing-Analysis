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

<img width="1897" height="933" alt="image" src="https://github.com/user-attachments/assets/977f7160-10ff-405e-aefc-b50d33e46ec6" />

### 3. Infrastructure Tracing & IP Resolution
To uncover where the adversary is hosting this phishing campaign and verify more about the validity of the website, I ran the domain through MXToolbox's DNS lookup and WHOIS query tools. This analysis provided clear insight into the underlying SSL/TLS certificate chain structure. 

The issuer of this certificate was identified as **YE2 / Let's Encrypt**. Although Let's Encrypt is an excellent free resource for legitimate developers, it is heavily abused by threat actors with malicious intent; it provides an automated method to provision a cryptographic certificate for zero cost, giving the phishing page an active HTTPS lock icon in desktop browsers to falsely reassure target victims. Furthermore, checking the validity period revealed an exceptionally brief 3-month operational timeline. This aligns perfectly with adversarial infrastructure patterns, as phishers anticipate rapid detection and subsequent domain takedowns.

<img width="1564" height="375" alt="image" src="https://github.com/user-attachments/assets/25c08a68-7b09-44cf-972c-9bb5d1359e5c" />

The HTTP Web Server check section below shows that the webpage is actively live on the internet. Receiving an HTTP `200 OK` status indicates that our connection request successfully established data transfers with the remote server. The delay check recorded an efficient response time of 203 ms, showing that the adversaries are leveraging stable, enterprise-grade high-performing server arrays to deliver the deceptive site.

<img width="1564" height="197" alt="image" src="https://github.com/user-attachments/assets/7c96ec79-360f-42fc-807f-71fef20c94f3" />

In order to resolve the hosting provider's true destination IP address, I appended an A-record flag (`a:`) before the URL. This resolved to the public destination IP address **`46.202.182[.]41`**, which represents the actual physical hosting server holding the malicious code assets. The network authority governing this space belongs to **Hostinger International Limited (ASN: AS47583)**. While Hostinger is a completely legitimate global web hosting platform, threat actors routinely favor budget registry options due to their frictionless configuration processes.

Additionally, the analysis reveals that the domain has configured active anti-spoofing protocols. This is a common evasion technique utilized by threat groups; by mapping out valid official cryptographic records for their rogue infrastructure, their outbound phishing communication layouts look safer and stand a significantly higher chance of successfully bypassing automated corporate email gateway filters.

<img width="1588" height="614" alt="image" src="https://github.com/user-attachments/assets/70bdba3f-d9bd-4c70-8243-55eba42f093c" />

### 4. Operational Security (OpSec) Defanging
To ensure absolute safety during documentation and prevent accidental execution of the malicious asset, I extracted the suspicious strings and processed them into a defanged format. This converts the link into plain text, rendering it completely unclickable in standard markdown viewers.

* **Raw Malicious URL:** `https://capital-trustblank.online/`
* **Defanged Operational URL:** `hxxps://capital-trustblank[.]online/`

<img width="1851" height="991" alt="image" src="https://github.com/user-attachments/assets/27d44796-a1ce-4fb0-8862-c0ec6d24adc9" />

---

## 📄 Final Deliverable

### Security Incident Triage Report
Utilizing the telemetry extracted during infrastructure tracking, I authored a corporate security triage brief. This report outlines the technical findings, active Indicators of Compromise (IOCs), and provides recommended firewall and proxy blocking configurations to defend an enterprise network.

## 🧰 Technical Scope & Tools
* **Threat Sourcing:** Sourced from live malicious data streams under PhishTank Submission #9458368 targeting financial/trust institutions via root domain `capital-trustblank.online`.
* **Tool Stack utilized for Triage:** VirusTotal (Threat Intel & Global Blacklists) and MXToolbox (DNS A-Record and Domain Security Verification).

---

## 📑 Core Deliverable

The comprehensive lifecycle breakdown of this incident—including infrastructure tracing, resolved host IP telemetry (`46.202.182[.]41`), SSL certificate trust chain metrics, and actionable defensive firewall/proxy blocking configurations—is documented inside the official security triage report.

### 📄 [DOWNLOAD THE COMPLETED INCIDENT REPORT (PDF)](Phishing_Incident_Mock_Report.pdf)

---

## 🔍 Executive Brief Summary

* **Incident Identification:** Active brand impersonation landing space discovered hosted on budget shared-hosting infrastructure (**Hostinger International - AS47583**).
* **Defensive Evasion Patterns:** Threat actor deployed an ephemeral 90-day automated SSL certificate via Let's Encrypt to simulate cryptographic validity while mapping out public anti-spoofing **DMARC records** specifically to trick inbound automated email security gateways.
* **Remediation Strategy:** The final brief outlines operational block requests for network boundary firewalls, secure web gateway proxy routing rules, and inbound message transport parameters to ensure total organizational isolation from the threat vector.
