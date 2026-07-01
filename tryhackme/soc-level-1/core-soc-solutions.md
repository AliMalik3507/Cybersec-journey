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
## 