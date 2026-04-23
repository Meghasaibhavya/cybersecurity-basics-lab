# Phishing Analysis & Triage Lab

## Overview
This laboratory demonstrates the process of triaging a suspicious email. The goal is to identify technical Indicators of Compromise (IoCs), analyze social engineering tactics, and verify the legitimacy of a sender using email authentication protocols.

> **Note:** The email analyzed in this lab is a **simulated sample** created for educational purposes in a controlled environment. It was not sent to or received by any actual user.

---

## Lab Activities

### 1. Technical Header Forensics
I analyzed the raw `.eml` source code to verify the digital "envelope" of the message. [cite_start]This mirrors the process of inspecting file metadata and system configurations found in my other security walkthroughs[cite: 1].

* **Observation**: The `From` address is spoofed as `support@paypal.com`, but the `Return-Path` is directed to `bounce-handler@attacker-infra.net`.
* **Authentication Results**:
    * **SPF (Sender Policy Framework)**: **FAIL** — The sending IP (`192.0.2.1`) is not authorized to send mail for `paypal.com`.
    * **DKIM (DomainKeys Identified Mail)**: **FAIL** — The cryptographic signature is invalid or missing.
    * **DMARC**: **FAIL** — The email failed alignment and should have been rejected by a strict policy.

### 2. Social Engineering Analysis
I performed a visual inspection of the email body to identify psychological triggers commonly used in cyberattacks.

* [cite_start]**Sense of Urgency**: The subject line and body threaten "Permanent Suspension" within 24 hours to induce panic, a common tactic described in security reconnaissance[cite: 1].
* **The "Hover Test"**: By hovering over the "Secure Your Account Now" button, I observed that the visible text points to a trusted domain while the actual destination is a suspicious IP-based URL.
* **Generic Greeting**: The use of "Dear Valued Customer" instead of a personalized name indicates a mass-distributed phishing campaign rather than a legitimate service communication.

### 3. Artifact Triage & Safety
[cite_start]I extracted and "defanged" the malicious indicators to prevent accidental execution, following standard industry safety procedures[cite: 1].

* **Malicious URL**: `hxxp[://]login-paypal-secure[.]net/verify/account_id=99283`
* **Source IP**: `192[.]0[.]2[.]1`
* **Tool Proof**: I submitted the URL to **VirusTotal** for automated analysis, where it was flagged by multiple vendors as a credential harvester.

---

## Technical Takeaways
* **Protocol Proficiency**: Gained hands-on experience identifying failures in **SPF**, **DKIM**, and **DMARC**.
* **Safe Handling**: Established a professional workflow for analyzing threats in a **Sandbox** environment and documenting them safely using **Defanging**.
* [cite_start]**Analyst Mindset**: Developed the ability to connect technical discrepancies in headers to behavioral lures in the email body, similar to the multi-step analysis required for complex security challenges[cite: 1].

---

### Final Verdict: **MALICIOUS**
The combination of failed authentication, spoofed headers, and urgency-based social engineering confirms this is a targeted phishing attempt aimed at credential theft.
