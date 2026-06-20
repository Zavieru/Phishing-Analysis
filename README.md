# Phishing-Analysis
Analyzing live phishing samples to extract Indicators of Compromise (IOCs), trace spoofed fake websites, and draft an enterprise-level incident triage report.


## Tools Utilized
* [cite_start]**PhishTank:** For sourcing live, safe phishing domain templates[cite: 41, 113].
* [cite_start]**MXToolbox:** For header extraction and IP tracing[cite: 41, 114].
* [cite_start]**VirusTotal:** For scanning extracted IPs and domains against global threat intelligence databases[cite: 41, 116].

---

## Workflow & Analysis Steps

### 1. Sourcing the Malicious Payload
[cite_start]I began the investigation by downloading a safe, real phishing website file from PhishTank to investigate a live, real-world sample[cite: 113, 344].

> **[ 🖼️ INSERT SCREENSHOT 1 HERE ]**
> *(Note for you: Take a screenshot of the PhishTank page showing the specific phishing email submission you chose to analyze.)*

### 2. Header Extraction & IP Tracing
[cite_start]To uncover the sender's true identity, I extracted the email headers and pasted them into MXToolbox[cite: 114, 345]. [cite_start]This allowed me to bypass the spoofed "From" address and pinpoint the actual server IP address that dispatched the malicious email[cite: 114].

> **[ 🖼️ INSERT SCREENSHOT 2 HERE ]**
> [cite_start]*(Note for you: Snag a screenshot of the MXToolbox results page clearly highlighting the true Sender IP address you uncovered[cite: 30].)*

### 3. Defanging the Malicious Links
[cite_start]As a critical safety precaution, I extracted the malicious URLs embedded in the email and defanged them (e.g., converting `http` to `hxxp`)[cite: 115, 345]. [cite_start]This ensures that the links cannot be accidentally clicked or executed while reviewing the incident notes[cite: 115].

> **[ 🖼️ INSERT SCREENSHOT 3 HERE ]**
> *(Note for you: Take a screenshot of a text editor (like Notepad) showing the original malicious URL next to your safely defanged version.)*

### 4. Infrastructure Threat Scanning
[cite_start]With the true IP address and defanged links in hand, I queried VirusTotal to check the infrastructure against global security vendor databases[cite: 116, 345]. [cite_start]This confirmed whether the IP and domains were actively flagged as dangerous by other threat intelligence feeds[cite: 116].

> **[ 🖼️ INSERT SCREENSHOT 4 HERE ]**
> [cite_start]*(Note for you: Grab a screenshot of the VirusTotal results showing the red flags, detection score, and malicious vendor alerts[cite: 30].)*

---

## Final Deliverable

### Mock Incident Response Report
[cite_start]Based on the extracted Indicators of Compromise (IOCs), I drafted a final incident report detailing the malicious IPs, domains, and the recommended defensive steps needed to block the threat actor from the network[cite: 117, 346]. 

> **[ 📄 INSERT LINK TO PDF HERE ]**
> [cite_start]*(Note for you: Upload your final written incident report as a PDF into the GitHub folder, and link it here so hiring managers can read your actual analysis[cite: 31, 42].)*
