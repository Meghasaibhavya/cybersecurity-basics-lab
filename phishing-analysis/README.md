# Phishing Analysis & Triage Lab

## Overview
This laboratory demonstrates the process of triaging a suspicious email. The goal is to identify technical Indicators of Compromise (IoCs), analyze social engineering tactics, and verify the legitimacy of a sender using email authentication protocols.

> **Note:** The email analyzed in this lab is a **simulated sample** created for educational purposes in a controlled environment. It was not sent to or received by any actual user.

---

## Lab Activities

### 1. Technical Header Forensics
The raw `.eml` source code was analyzed to verify the digital “envelope” of the message.

* **Observation**:
  * From: `support@paypal.com` (spoofed)
  * Return-Path: `bounce-handler@attacker-infra.net`
  * Source IP: `192.0.2.1`
    
* **Authentication Results**:
    * SPF: FAIL — Sending IP (192.0.2.1) is not authorized for paypal.com
    * DKIM: FAIL — Signature validation unsuccessful or absent
    * DMARC: FAIL — Policy alignment failure; message would be rejected under enforcement

* **Interpretation:** The mismatch between the visible sender and underlying infrastructure indicates likely email spoofing due to sender infrastructure mismatch.
### 2. Social Engineering Analysis
The email body was analyzed to identify manipulation techniques commonly used in phishing campaigns.

**Findings:**
   * Urgency pressure: Claims account suspension within 24 hours to force immediate action.
   * Credential harvesting lure: Call-to-action link is designed to imitate a legitimate login process while directing to a non-trusted domain.
   * Generic salutation: “Dear Valued Customer” indicates bulk phishing distribution.
   * Link deception: Displayed branding does not match actual destination URL.
     
### 3. Indicator Review (IoCs)
The following indicators were extracted and safely defanged for documentation:

* URL: `hxxp://login-paypal-secure[.]net/verify/account_id=99283`
* IP address: `192[.]0[.]2[.]1`
* Domain: `attacker-infra[.]net`

Assessment:
The domain structure, impersonation pattern, and URL formatting are consistent with credential-harvesting phishing infrastructure observed in simulated attack scenarios.

---

## Technical Takeaways
* Identified email spoofing through SPF, DKIM, and DMARC failures.
* Correlated header inconsistencies with sender impersonation techniques.
* Recognized common phishing patterns including urgency-based manipulation and brand impersonation.
* Applied structured triage methodology for extracting and documenting IoCs.
---

### Final Verdict: **MALICIOUS**
The combination of failed authentication, sender spoofing, and credential-harvesting indicators confirms this email is a phishing attempt designed to deceive users into disclosing sensitive information.
