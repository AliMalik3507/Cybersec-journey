# SOC Team Internals

`SOC Level 1`

## SOC L1 Alert Triage

### What this room covers
- Explore alert fields, statuses, and classification
- Learn how to perform alert triage as an L1 analyst

### Key takeaways
- How alerts come in: Alert Management Platforms (SIEM, EDR, SOAR, ITSM)
- Alert properties: Time, Name, Severity, Status, Verdict, Assignee, Description
- Flow: Events → Alerts → Alert Prioritization

### Why it matters in a real SOC
So you know what to do when an alert comes in — what to ask, where to look, who to alert, and what to note down.

---

## SOC L1 Alert Reporting

### What this room covers
- Understand the need for SOC alert reporting and escalation
- Learn how to write alert comments or case reports properly
- Explore escalation methods and communication best practices

### Key takeaways
- Use the 5 W's when leaving a comment: Who, What, Where, When, Why
- Escalation path: if L2 is unavailable → L3 → manager
- Source process: the process that directly triggered the alert
- Parent process: the program that launched the source process
- Grandparent process: the program that launched the parent

### Why it matters
Understanding the workflow of communicating an alert — what info is required and how to relay it to other team members.

---

## SOC Workbooks and Lookups

### What this room covers
- Familiarize yourself with SOC investigation workbooks
- Learn where to find and how to use asset inventory in a SOC
- Understand the importance of corporate network diagrams

### Key takeaways
- Identity inventory: catalogue of corporate employees and services with details — privileges, contacts, and roles
- Sources of identities: AD, SSO providers, HR systems, custom solutions
- Asset inventory: list of all computing resources within an organization's IT environment
- Sources of assets: AD, SIEM or EDR, MDM solution, custom solution
- Playbooks: structured documents that define the steps required to investigate and remediate
- Three logical groups: Enrichment, Investigation, and Escalation

### Why it matters
- Gives guidance on what steps are required to investigate and remediate specific threats
- Lets a SOC analyst know where their sources of intel are coming from (lookups)

---

## SOC Metrics and Objectives

> Key SOC metrics used to measure alert volume, detection speed, analyst response time, escalation quality, and recovery efficiency.

### Objectives
- Understand the concepts of SLA, MTTD, MTTA, and MTTR
- Understand the importance of the False Positive Rate
- Learn why and how to improve these metrics as an L1 analyst

### Core Metrics
- **Alert Count (AC)** — total count of alerts received
- **False Positive Rate (FPR)** — `False Positives / Alert Count`
  - Measures the level of noise in alerts
- **Alert Escalation Rate (AER)** — `Escalated Alerts / Alert Count`
  - Shows how often L1 analysts escalate alerts
- **Threat Detection Rate (TDR)** — `Detected Threats / Total Threats`
  - Measures the reliability of the SOC's detection capability

### SLA (Service Level Agreement)
An **SLA** is a formal commitment to how fast the SOC will act on alerts. It sets the target times that triage metrics like MTTA and MTTR are measured against — so the "example targets" below aren't arbitrary, they're the SLA.

- Defines the **expected** time to acknowledge, respond, and resolve
- Usually tiered by alert severity (e.g. a critical alert has a tighter SLA than a low-severity one)
- Meeting SLA = the SOC is responding within its agreed limits; breaching SLA = alerts are sitting too long
- As an L1 analyst, the SLA is the clock you're working against — acknowledging an alert quickly is often the first SLA you're directly responsible for

### Triage Metrics
- **SOC Team Availability** — 24/7 coverage
- **MTTD** — Mean Time to **Detect** (example target: 5 minutes)
- **MTTA** — Mean Time to **Acknowledge** (example target: 10 minutes)
- **MTTR** — Mean Time to **Respond / Recover / Resolve** (example target: 60 minutes)

### Why It Matters
SOC metrics provide insight into the **reliability**, **efficiency**, **consistency**, and **recoverability** of a SOC team.

They help show:
- How quickly threats are detected
- How quickly alerts are acknowledged
- How noisy the alert queue is
- How often alerts are escalated
- How reliable the SOC is at detecting real threats
- How quickly the team responds or recovers
