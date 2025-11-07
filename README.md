k# 🔍 KQL Labs: Data Explorer Demo

## 🧠 Overview

This README documents the **Microsoft Data Explorer Demo**, a hands-on cybersecurity learning project focused on mastering **Kusto Query Language (KQL)** for threat hunting, SIEM operations, and incident response.

This project simulates real-life SOC workflows: **detecting, investigating, and reporting incidents using KQL** and advanced data analytics techniques.

---

## 🧩 Project: Data Explorer Demo

### 🎯 Purpose

To demonstrate how **KQL** is used to query, filter, and visualize log data from sources like **Microsoft Sentinel**, **Defender for Endpoint**, and **Log Analytics Workspace**.

### ⚙️ Skills Developed

* Writing and optimizing **KQL queries** for real-world datasets.
* Understanding **data tables**, **joins**, **summarizations**, and **time-based filtering**.
* Building **custom detections** and **analytic rules** in SIEM.
* Investigating alerts and anomalies across network, endpoint, and identity logs.
* Performing **incident triage** and building chronological investigation timelines.

### 🧮 Example KQL Use Case

```kql
SecurityEvent
| where EventID == 4625
| summarize FailedLogons = count() by Account, IPAddress, bin(TimeGenerated, 1h)
| sort by FailedLogons desc
```

📘 *Detects failed logon attempts grouped by account and IP address, showing brute-force indicators.*

---

## 💡 Real-Life Relevance

KQL is a foundational skill used daily by **SOC Analysts, Threat Hunters, and Incident Responders** to:

* Query and interpret security logs in **Microsoft Sentinel**.
* Build **dashboards, alerts, and analytics rules** for suspicious activities.
* Perform **threat hunting** and **incident correlation** across multiple log sources.
* Support **digital forensics** and **post-incident reporting**.

---

## 🧰 Tools Used

| Tool                                   | Purpose                                    |
| -------------------------------------- | ------------------------------------------ |
| **Microsoft Sentinel / Data Explorer** | Querying, visualization, and log analytics |
| **Azure Log Analytics Workspace**      | Ingesting and testing KQL queries          |
| **Excel / Jupyter Notebooks**          | Data export, enrichment, and visualization |

---

## 🚀 Skills You’ll Master

| Category              | Skills                                                            |
| --------------------- | ----------------------------------------------------------------- |
| **KQL Querying**      | Filtering, summarizing, joining, extending, parsing               |
| **Threat Hunting**    | Detecting brute-force, persistence, and lateral movement patterns |
| **Incident Response** | Log analysis, evidence correlation, and timeline creation         |
| **SIEM Operations**   | Building detections, dashboards, and performing triage            |
| **Reporting**         | Writing structured incident reports and documenting findings      |

---

## 🧾 Recommended Learning Path

1. Learn **KQL fundamentals** via Microsoft Learn or Data Explorer Docs.
2. Practice queries in **Data Explorer Demo** or **Log Analytics Workspaces**.
3. Build **custom detection rules** in Microsoft Sentinel.
4. Recreate investigations using real-world log samples.

---

## 📁 Directory Structure

```
kql_projects/
│
├── data_explorer_demo/
│   ├── queries/
│   ├── visuals/
│   └── README.md ← (this file)
```

---

## 🏁 Conclusion

The **Data Explorer Demo** showcases how **KQL powers modern SOC, threat hunting, and digital forensics operations**.

Mastering KQL equips you with the ability to:

* Turn raw log data into actionable insights.
* Perform investigations efficiently within Microsoft Sentinel.
* Build a strong foundation for careers in **SOC analysis, threat hunting, and cyber defense**.

📌 *KQL is not just a query language — it’s the analytical engine behind effective cybersecurity operations.*

