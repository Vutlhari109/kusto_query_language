# KC7 Cyber Lab — "Rap Beef" (Certificate of Completion)

**Analyst:** Vutlhari Mathebula
**Badge earned:** Rap Beef
**Lab:** KC7 Foundation — Cybersecurity Investigation

---

## Overview

This lab simulates a themed cybersecurity investigation revolving around a public feud between two hip‑hop artists (Dwake and Present). As a security analyst for OWL Records, you used log sources and Kusto Query Language (KQL) to identify suspicious communications and adversary activity. The exercise focuses on log analysis, threat detection, phishing investigation, and account compromise analysis.

---

## Objectives

* Use KQL to query multiple telemetry sources (network, email, authentication, passive DNS).
* Identify and track adversary infrastructure (IP ↔ domain mappings).
* Investigate phishing campaigns and identify targeted users and clicked links.
* Correlate events across data sources to confirm account takeover and data exfiltration.
* Practice documentation and reporting of findings.

---

## Scenario Summary

Two artists — **Dwake** (OWL Records) and **Present** (Dollar Currency Records) — are in a feud. Following a taunting verse by Dwake, Present's label allegedly hired a hacker who used the IP `18.66.52.227` to probe OWL Records' website in early April. The adversary then used a domain (`betterlyrics4u.com`) to host a phishing page that successfully phished Dwake, leading to credential theft and subsequent access to Dwake's account.

Key artifacts discovered during the exercise:

* Adversary IP: `18.66.52.227`
* Associated domain: `betterlyrics4u.com`
* Phishing sender addresses: `ghostwritersanonymous@protonmail.com`, `wemakebeatz@gmail.com`
* Victim email: `dwake_audrey@owl-records.com`
* Victim internal IP: `10.10.0.5`
* Stolen archive: `DwakesDirtySecrets.zip`
* Phishing click timestamp: `2024-04-15T12:03:12Z`
* Adversary authentication attempt: `2024-04-15T13:03:12Z` (successful)

---

## Telemetry & KQL Queries Used

Below are representative KQL queries used in the investigation. (These were provided by the lab and can be reused in your environment.)

1. Find the CEO in the Employees table

```kql
Employees
| where role == "CEO"
```

2. Search inbound network events from the adversary IP over a date range

```kql
InboundNetworkEvents
| where timestamp between (datetime("2024-04-10T00:00:00") .. datetime("2024-04-11T00:00:00"))
| where src_ip has "18.66.52.227"
```

3. Passive DNS lookup for IP to domain mapping

```kql
PassiveDns
| where ip == "18.66.52.227"
```

4. Search email logs for the phishing domain

```kql
Email
| where link has "betterlyrics4u.com"
```

5. Check outbound clicks from Dwake's IP to the phishing URL

```kql
OutboundNetworkEvents
| where url == "http://betterlyrics4u.com/share/online/published/enter"
| where src_ip == "10.10.0.5"
```

6. Verify authentication events for Dwake with the adversary IP

```kql
AuthenticationEvents
| where username == "dwaudrey"
| where src_ip == "18.66.52.227"
```

7. Search inbound events for activity against Dwake's account

```kql
InboundNetworkEvents
| where timestamp between (datetime("2024-04-12T00:00:00") .. datetime("2024-05-01T00:00:00"))
| where url has "dwaudrey"
| where src_ip has "18.66.52.227"
```

---

## Findings (Answers & Evidence)

* **CEO name:** Sean Crater
* **Adversary IP → Domain:** `18.66.52.227` resolved to `betterlyrics4u.com`
* **Number of phishing emails containing the domain:** 13
* **Primary phishing sender:** `ghostwritersanonymous@protonmail.com`
* **Secondary sender:** `wemakebeatz@gmail.com`
* **Most targeted role:** Rapper (and Lead Rapper)
* **Lead Rapper name:** Dwake Audrey
* **Dwake's email:** `dwake_audrey@owl-records.com`
* **Dwake clicked the phishing link at:** `2024-04-15T12:03:12Z`
* **Adversary authenticated successfully at:** `2024-04-15T13:03:12Z`
* **Exfiltrated archive:** `DwakesDirtySecrets.zip`

---

## Skills Practiced

* Log analysis and event correlation
* Kusto Query Language (KQL) usage
* Phishing investigation methodology
* Passive DNS and domain-to-IP correlation
* Timeline construction and evidence collection
* Incident reporting for stakeholder communication

---

## Recommendations (Practice / Real‑world)

1. **Improve user awareness:** Train artists and staff to recognize spear‑phishing indicators and report suspicious email promptly.
2. **Harden account recovery:** Avoid challenge questions based on publicly available information; use multi-factor authentication (MFA) for all accounts.
3. **Email protection tuning:** Review mail filters and phishing verdicts — investigate why the email marked `CLEAN` reached the inbox.
4. **Network monitoring:** Add alerts for login attempts from anomalous IPs and for known malicious domains.
5. **Incident readiness:** Ensure playbooks include immediate actions for suspected credential compromise (password reset, MFA enrollment, search for lateral movement and data access).

---

## How to Reproduce This Lab

1. Use the provided KQL queries in the lab's query pane to explore the simulated telemetry.
2. Follow the clues in the logs (IPs, URLs, email senders) and correlate across telemetry sources.
3. Document timestamps, artifacts, and impacted users.

---

## Acknowledgements & Metadata

* Lab author: KC7 Foundation
* Lab theme: Rap Beef — staged scenario for training analytical skills
* Completed by: Vutlhari Mathebula

---

## License

This README is released under the [Creative Commons Attribution‑ShareAlike 4.0 International (CC BY‑SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/) recommended for training artifacts.

---



