# Core SOC Solutions
`SOC Level 1`

## Introduction to EDR

### What this room covers

**Learning Objectives**
- Understand the basics of EDR and how it works
- Differentiate EDR from traditional Antivirus solutions
- Examine the architecture of an EDR solution
- Analyze the types of telemetry it collects from endpoints
- Understand the detection and response capabilities of an EDR

### Key takeaways
- **What EDR is:** Endpoint Detection and Response — a security solution designed to proactively detect and respond to advanced threats at the endpoint level (e.g. CrowdStrike Falcon, SentinelOne, Microsoft Defender for Endpoint). Its core features are visibility (collects endpoint data and presents it in a process tree), detection (signature + behaviour based, catches fileless malware and custom IoCs), and response (terminate, quarantine, or remote action from the console).
- **EDR vs AV:** AV can only detect and block *known signatures*, whereas EDR can detect known, unknown, and behaviour-based threats.
- **Architecture:** Two main components — **Agents** (the "eyes and ears" sitting at the endpoint, monitoring all activity and sending it up) and the **EDR Console** (analyzes the data through complex logic and ML to form alerts).
- **Telemetry:** The endpoint's activity record — process executions/terminations, network connections, command-line activity, file/folder modifications, and registry modifications.

### Why it matters
Telemetry is what makes EDR powerful: it helps analysts understand the kill chain of events, identify root cause, and reconstruct the attack timeline — acting as the endpoint's "black box." Because AV only catches known signatures, EDR's behaviour-based detection and rich telemetry are what let a SOC analyst spot and investigate the modern threats that traditional antivirus misses.

---

## Introduction to SIEM

### What this room covers

**Learning Objectives**
- Understand what a SIEM is and its role in a SOC
- Differentiate between host-centric and network-centric log sources
- Examine the core features of a SIEM
- Identify common log sources and how logs are ingested into a SIEM

### Key takeaways
- **What SIEM is:** Security Information and Event Management — a central security platform that collects logs from many systems, analyzes them for suspicious activity, and helps analysts investigate incidents across the whole environment.
- **Logs:** Serve as a trail of all activities and are extremely helpful for identifying malicious activity. Two main types of source:
  - **Host-Centric:** Capture events that occur within or relate to the host (e.g. a user accessing a file, adding/deleting a registry key).
  - **Network-Centric:** Generated when hosts communicate with each other or access the internet/a website (e.g. SSH connection, web traffic, file transfer via FTP).
- **Features:** Centralized log collection, normalization of logs (parsing and normalization), correlation of logs → real-time alerting, and dashboards/reporting.
- **Log Sources:** Windows machines (via Event Viewer), Linux machines (in `/var/log/`), and web servers.
- **Log Ingestion:** Each SIEM has its own way — Agent/Forwarder (a lightweight tool called an agent), Syslog, Manual Upload, and Port Forwarding (endpoints send data to a listening port).

### Why it matters
A SIEM is the central nervous system of a SOC. By pulling logs from across the environment, normalizing them into a common format, and correlating them, it turns scattered raw events into real-time alerts an analyst can act on. Understanding where logs come from (host vs network) and how they're ingested is essential for a SOC analyst to investigate incidents and know what visibility they do — and don't — have.

---
## Splunk: The basics 
## Introduction to Splunk

### What this room covers

**Learning Objectives**
- Understand what Splunk is and its role as a SIEM
- Examine the core components of Splunk and how they work together
- Understand how data flows from endpoint to search
- Introduce SPL (Search Processing Language)

### Key takeaways
- **What Splunk is:** A leading SIEM solution that collects, analyzes, and correlates network and machine logs in real time.
- **Components (work together to search and analyze data):**
  - **Forwarder:** A lightweight agent installed on the endpoint being monitored; collects and sends data to the Splunk instance.
  - **Indexer:** Parses and normalizes the data received from forwarders into field-value pairs, categorizes it, and stores it as events.
  - **Search Head:** Lives within the Search & Reporting app, where users search the indexed logs using **SPL (Search Processing Language)**.
- **Data flow:** Forwarder → Indexer → Search Head. A search queries the index and results are returned.

### Why it matters
Splunk is one of the most widely deployed SIEMs in the industry, so knowing its component pipeline (forwarder → indexer → search head) and being able to query with SPL is directly job-relevant. Understanding where data is normalized (the indexer) and where analysts actually work (the search head) maps the tool onto the generic SIEM concepts from the previous room.

---

## Introduction to Elastic Stack (ELK)

### What this room covers

**Learning Objectives**
- Understand what the Elastic Stack (ELK) is and what it's used for
- Examine each component and how data flows through the stack
- Understand index patterns and the Kibana Discover interface
- Introduce KQL (Kibana Query Language) for searching ingested data

### Key takeaways
- **What ELK is:** A stack used for log analysis and investigations. It can collect data from any source, store it, and search it — and is strong at data searching and visualization.
- **Components:**
  - **Elasticsearch:** Full-text search and analytics engine for JSON-formatted documents.
  - **Logstash:** Data-processing engine that takes data from different sources, filters/normalizes it, and sends it to a destination (e.g. Kibana or a listening port). Three parts — **Input** (defines the source), **Filter** (options to normalize the log), **Output** (where the data is sent).
  - **Beats:** Host-based agents (data shippers) that ship/transfer data from the endpoint to Elastic.
  - **Kibana:** Web-based data-visualization tool that works with Elasticsearch to analyze, investigate, and visualize data in real time → better visibility.
- **Kibana Discover tab has:** Logs, Fields pane, Index Pattern, Search Bar, Time Filter, Time Interval. The top bar has the Discover tab and Add Filter.
- **Index Pattern:** Kibana requires an index pattern to access the data stored/ingested in Elasticsearch.
- **KQL (Kibana Query Language):** Used to search the ingested logs/docs.
  - **Free-text search:** Searches on text only; use `*` for partial-word matching.
  - **Logical operators (AND / OR / NOT — case matters):**
    - `"United States" AND "New York"`
    - `"Canada" OR "England"`
    - `"United States" AND NOT ("Florida")`
  - **Field-based search:** Provide a field name and value — e.g. `source.ip: 238.163.231.204 AND user.name: Suleman`.

### Why it matters
ELK is a widely used open-source SIEM stack, so understanding its data flow (Beats → Logstash → Elasticsearch → Kibana) and being able to query with KQL is common in real SOC environments. Index patterns and the Discover tab are where an analyst actually pivots through data during an investigation.

> **Note on "KQL":** Kibana Query Language (this room) is **not** the same as Microsoft's **Kusto** Query Language used in Sentinel/Defender (SC-200). Both are abbreviated "KQL" but have completely different syntax — Kusto is pipe-based (`| where`, `| project`, `| summarize`). Keep them separate.

---

## Introduction to SOAR

### What this room covers

**Learning Objectives**
- Understand what SOAR is and the problems it solves
- Examine the three main capabilities of a SOAR platform
- Understand the role of playbooks in automation

### Key takeaways
- **What SOAR is:** Security Orchestration, Automation, and Response — a tool that unifies all the security tools so analysts don't need to switch between SIEM, EDR, firewall, and other tools.
- **Problems it addresses:** Alert fatigue, disconnected tools, manual processes, and talent shortage.
- **Three main capabilities:**
  1. **Orchestration:** Solves tool-switching by coordinating all the tools together inside the SOAR; defines workflows for investigating various types of alerts (**playbooks**).
  2. **Automation:** The SOAR itself follows the playbooks.
  3. **Response:** Ability to take actions automatically.

### Why it matters
SOAR reduces analyst workload and alert fatigue by automating repetitive triage and response work through playbooks. Understanding orchestration and automation is increasingly expected in modern SOCs, because it's how teams scale detection and response without scaling headcount at the same rate.