# 🛡️ DefectDojo – Finding Management

Centralizing vulnerability data from GVM (OpenVAS) into DefectDojo to perform lifecycle management, triage, and risk-based prioritization.

---

## 🖥️ Environment

| Host | IP | Role |
|------|----|------|
| Ubuntu Server 24.04 LTS | 192.168.102.131 | Orchestrator (DefectDojo) |

DefectDojo provides the interface to track findings from "Detected" to "Remediated".

![DefectDojo Dashboard](screenshots/06-defectdojo-dashboard.png)

---

## 🐳 Deployment

DefectDojo is deployed as a multi-container stack via Docker Compose.

```bash
cd ~/defectdojo-container
docker compose up -d

```

Verify that all services (PostgreSQL, Redis, Celery, and Django) are running:

```bash
docker ps --format "table {{.Names}}\t{{.Status}}"

```

---

## 🔗 Integration Flow

1. **Report Export:** Extract the scan results from GVM (OpenVAS) in XML format.
2. **Engagement Setup:** Create a new "Engagement" in DefectDojo for the target lab.
3. **Ingest:** Import the XML file using the dedicated GVM parser.
4. **Lifecycle:** Track vulnerability remediation progress over time.

---

## 🎯 Objective

Transition from raw scan data to a manageable security posture:

* **Centralization:** Single source of truth for all vulnerabilities.
* **Triage:** Distinguish between false positives and real threats.
* **Tracking:** Automated aging and status reporting for remediation teams.

---

## 🧪 Status

* [ ] Deployment completed
* [ ] GVM parser configuration
* [ ] Initial data ingestion
