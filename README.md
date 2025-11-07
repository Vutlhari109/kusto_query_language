# 🔍 KQL Labs: Data Explorer Demo & KC7Cyber Investigation

## 🧠 Overview

This README covers two connected cybersecurity learning projects:

* **Microsoft Data Explorer Demo** — focused on mastering **Kusto Query Language (KQL)** for threat hunting and SIEM operations.
* **KC7Cyber Lab** — a practical cyber investigation challenge emphasizing real-world analytic reasoning, log analysis, and attacker tracing.

Together, they simulate real-life SOC workflows: **detecting, investigating, and reporting incidents using KQL** and data analysis skills.

---

## 🧩 Project 1: Data Explorer Demo

### 🎯 Purpose

To demonstrate how **KQL** is used to query, filter, and visualize log data from sources like Microsoft Sentinel or Defender for Endpoint.

### ⚙️ Skills Developed

* Writing and optimizing **KQL queries** for real-world datasets.
* Understanding **data tables**, **joins**, **summarizations**, and **time-based filtering**.
* Building **custom detections** and **analytic rules** in SIEM.
* Investigating alerts and anomalies across network, endpoint, and identity logs.

### 🧮 Example KQL Use Cases

```kql
SecurityEvent
| where EventID == 4625
| summarize FailedLogons = count() by Account, IPAddress, bin(TimeGenerated, 1h)
| sort by FailedLogons desc
```

📘 *Detects failed logon attempts grouped by account and IP address, showing brute-force indicators.*

---

## 🕵️‍♂️ Project 2: KC7Cyber Investigation (Rap Beef Lab)

### 🎯 Purpose

To simulate a **cyber defense and forensic investigation** scenario where logs, domains, and patterns are analyzed to uncover malicious activity.

### 🧰 Skills Developed

* **Threat hunting** using KQL and real-world data.
* **Log correlation and pivoting** between multiple sources.
* **Incident reconstruction** — tracing attacker movement across the environment.
* **Evidence reporting** and analytical reasoning.

### ⚔️ Example KQL Query in KC7Cyber Context

```kql
SigninLogs
| where ResultType == 50053 or ResultDescription contains "invalid"
| project TimeGenerated, UserPrincipalName, IPAddress, Location, ResultDescription
```

📘 *Identifies failed authentication attempts possibly linked to account enumeration or credential stuffing.*

---

## 💡 Real-Life Relevance

KQL is widely used by **SOC analysts, threat hunters, and digital forensics experts** to:

* Query and interpret SIEM data in **Microsoft Sentinel**.
* Build **dashboards and alerts** for suspicious activity.
* Perform **threat hunting** and **incident correlation** across cloud and on-prem environments.
* Support **forensic timelines** and **evidence analysis** during investigations.

---

## 🧰 Tools Used

| Tool                                   | Purpose                                        |
| -------------------------------------- | ---------------------------------------------- |
| **Microsoft Sentinel / Data Explorer** | For querying, visualization, and log analytics |
| **KC7Cyber Platform**                  | For real-world cyber investigation challenges  |
| **Azure Log Analytics Workspace**      | For ingesting and testing KQL queries          |
| **Excel / Notebooks**                  | For data export and enrichment                 |

---

## 🚀 Skills You’ll Master

| Category            | Skills                                                          |
| ------------------- | --------------------------------------------------------------- |
| **KQL Querying**    | Filtering, summarizing, joining, extending, parsing             |
| **Threat Hunting**  | Brute-force, persistence, lateral movement patterns             |
| **Forensics**       | Event correlation, IP tracing, evidence timeline reconstruction |
| **SIEM Operations** | Rule creation, incident triage, and log analytics               |
| **Reporting**       | Analytical documentation and incident summary building          |

---

## 🧾 Recommended Learning Path

1. Learn **KQL basics** via Microsoft Learn (Data Explorer fundamentals).
2. Practice with **Data Explorer Demo datasets**.
3. Complete **KC7Cyber Labs** to simulate SOC investigations.
4. Apply findings in **Microsoft Sentinel** or **ELK Stack** for deeper context.

---

## 📁 Directory Structure

```
kql_projects/
│
├── data_explorer_demo/
│   ├── queries/
│   ├── visuals/
│   └── README.md
│
├── kc7cyber_investigation/
│   ├── logs/
│   ├── findings/
│   └── README.md
│
└── combined_readme.md ← (this file)
```

---

## 🏁 Conclusion

These labs reflect how KQL underpins modern **SOC, threat hunting, and digital forensics workflows**. Together, they prepare you for real-world cybersecurity roles such as:

* SOC Analyst (Tier 1–2)
* Threat Hunter
* Cyber Forensic Investigator
* Incident Responder

📌 *Mastering KQL helps turn raw log data into actionable intelligence — the backbone of every effective cyber defense operation.*

