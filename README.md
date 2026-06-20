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
To uncover where the adversary is hosting this phishing campaign nad more about the validity of the website, I ran the domain through MXToolbox's DNS lookup and WHOIS query tools. This allowed me to learn about what a SSS/TLS certificate Chain is. The issuer of this certificate was YE2 / Lets Encrypt. Though this is good for legitimate developers it abused by people with malicous intent because it is a free way to give phishing websites the https and lock icon in browsers making their website seem legit to bankers. This also allowed me to observe the validity period of the website and it was only 3 months. This makes sense as phishers know that their website will get taken down soon anyway.

<img width="1564" height="375" alt="image" src="https://github.com/user-attachments/assets/25c08a68-7b09-44cf-972c-9bb5d1359e5c" />

The HTTP Web server test section shown below shows that the website is still currently live and active as the 200 OK sign means that we managed to reach the remote web server. IT also had a delay check response time of 203ms showing that the phishers are using an enterprise level high performing server to serve the phishing page.

<img width="1564" height="197" alt="image" src="https://github.com/user-attachments/assets/7c96ec79-360f-42fc-807f-71fef20c94f3" />

In order to find the hosting providers true destination IP address i put a: before the url. This IP adress (46.202.182[.]41) is the actual physical server's IP thats hosting the websites files. THe network provider hosting this is "Hostinger International Limited - AS47583" though they are a legitimate global web hosting platform because they are a budget provider threat actors use providers like these.

Additionally, at the bottom it says "The domain capital-trustblank.online has protection from email spoofing." this is a tactic so that when people attempt to email them offical email security records seem valid and are more likely to reach the victim as it looks safer.

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

> **[ 📁 LINK TO YOUR COMPLETED REPORT PDF HERE ]**
> *(Note for Zavier: Save your written report as a PDF, commit it to this GitHub directory, and link the file location right here).*
