# Phishing-Analysis

Analyzing live phishing samples to extract Indicators of Compromise (IOCs), trace spoofed fake websites, and draft an enterprise-level incident triage report.





## Tools Utilized

* **PhishTank:** For sourcing live, safe phishing domain templates.

* **MXToolbox:** For header extraction and IP tracing.

* **VirusTotal:** For scanning extracted IPs and domains against global threat intelligence databases.



---



## Workflow & Analysis Steps



### 1. Sourcing the Malicious Payload

I began the by investigating a safe, real phishing website (hxxps://capital-trustblank[.]online/) from PhishTank to investigate a live, real-world sample.



<img width="2850" height="1557" alt="image" src="https://github.com/user-attachments/assets/ff4ddae2-e31e-458f-9131-42a4d2482926" />





### 2. Header Extraction & IP Tracing

To uncover the sender's true identity, I extracted the email headers and pasted them into MXToolbox. This allowed me to bypass the spoofed "From" address and pinpoint the actual server IP address that dispatched the malicious email.



> **[ 🖼️ INSERT SCREENSHOT 2 HERE ]**

> [_]*(Note for you: Snag a screenshot of the MXToolbox results page clearly highlighting the true Sender IP address you uncovered)*



### 3. Defanging the Malicious Links

As a critical safety precaution, I extracted the malicious URLs embedded in the email and defanged them (e.g., converting `http` to `hxxp`). This ensures that the links cannot be accidentally clicked or executed while reviewing the incident notes.



> **[ 🖼️ INSERT SCREENSHOT 3 HERE ]**

> *(Note for you: Take a screenshot of a text editor (like Notepad) showing the original malicious URL next to your safely defanged version.)*



### 4. Infrastructure Threat Scanning

With the true IP address and defanged links in hand, I queried VirusTotal to check the infrastructure against global security vendor databases.This confirmed whether the IP and domains were actively flagged as dangerous by other threat intelligence feeds.



> **[ 🖼️ INSERT SCREENSHOT 4 HERE ]**

> *(Note for you: Grab a screenshot of the VirusTotal results showing the red flags, detection score, and malicious vendor alerts.)*



---



## Final Deliverable



### Mock Incident Response Report

Based on the extracted Indicators of Compromise (IOCs), I drafted a final incident report detailing the malicious IPs, domains, and the recommended defensive steps needed to block the threat actor from the network.



> **[ 📄 INSERT LINK TO PDF HERE ]**

> *(Note for you: Upload your final written incident report as a PDF into the GitHub folder, and link it here so hiring managers can read your actual analysis)*
