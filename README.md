# 🛡️ Risk-Driven Vulnerability Management Lab

![Status](https://img.shields.io/badge/status-in%20progress-yellow)
![Stack](https://img.shields.io/badge/stack-Greenbone%20%7C%20DefectDojo%20%7C%20EPSS-blue)
![Platform](https://img.shields.io/badge/platform-VMware%20%7C%20Docker-lightgrey)

> Enterprise-grade vulnerability management environment combining automated scanning,
> centralized finding management, and risk-based prioritization using EPSS and CISA KEV.

---

## 🔁 Workflow

[Greenbone CE] ──scan──► [DefectDojo] ──enrich──► [EPSS + CISA KEV] ──► Risk Report

1. **Scan** – Greenbone CE (OpenVAS) identifies vulnerabilities across targets
2. **Triage** – Findings imported into DefectDojo for centralized tracking
3. **Prioritize** – Risk scoring enhanced with EPSS scores and CISA KEV data
4. **Report** – Actionable output with business-context risk prioritization

---

## 🖥️ Architecture

| Host | OS | IP | Role |
|------|----|----|------|
| Windows Workstation | Windows 11 | 192.168.102.1 | Operator |
| Ubuntu Server | Ubuntu 24.04 LTS | 192.168.79.131 | Scanner / DefectDojo |
| Metasploitable 2 | Linux | 192.168.79.132 | Target |

> All VMs run on VMware Workstation in an isolated host-only network segment.

---

## 🧰 Stack

| Component | Purpose |
|-----------|---------|
| [Greenbone CE](https://www.greenbone.net/en/community-edition/) | Vulnerability scanning (OpenVAS engine) |
| [DefectDojo](https://www.defectdojo.org/) | Finding management & deduplication |
| [EPSS](https://www.first.org/epss/) | Exploit probability scoring |
| [CISA KEV](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) | Known exploited vulnerabilities feed |
| Docker / Docker Compose | Container orchestration |
| SSH tunneling | Secure admin access, no exposed management ports |

---

## 📂 Labs

| Lab | Status |
|-----|--------|
| [Greenbone CE – Deployment & Scanning](labs/greenbone/README.md) | ✅ In progress |
| DefectDojo – Finding Management | 🔜 Coming soon |
| EPSS + CISA KEV – Risk Prioritization | 🔜 Coming soon |
