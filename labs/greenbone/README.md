# 🔍 Greenbone CE – Deployment & Scanning

Automated vulnerability assessment using Greenbone Community Edition (OpenVAS)
against a Metasploitable 2 target in an isolated lab network.

---

## 🖥️ Environment

| Host | IP | Role |
|------|----|------|
| Ubuntu Server 24.04 LTS | 192.168.79.131 | Scanner (Greenbone CE) |
| Metasploitable 2 | 192.168.79.132 | Target |

Access from Windows operator workstation via SSH tunnel.

![Scanner VM – network and SSH access](screenshots/01-ssh-login.png)

---

## 🐳 Deployment

Greenbone Community Edition runs fully containerized via Docker Compose.

    cd /home/labuser/greenbone-community-container
    docker compose up -d
    docker ps --format "table {{.Names}}\t{{.Image}}\t{{.Ports}}"

![Docker installed and containers running](screenshots/02-docker-installed.png)

---

## 🔐 Accessing the GSA Web Console

GSA binds to `127.0.0.1:443` by design. Access is handled via SSH local
port forwarding — the management interface is never exposed on the network.

    ssh -L 8443:127.0.0.1:443 labuser@192.168.102.131

Navigate to `https://127.0.0.1:8443` and accept the self-signed certificate.

![GSA login screen](screenshots/03-openvas-login.png)

---

## 🎯 Target Configuration

To ensure accurate vulnerability assessment, the Metasploitable 2 target is configured within an isolated NAT network segment shared with the Scanner.

1. **Verify Connectivity:** Confirm the Scanner can reach the target.

    ping -c 4 192.168.79.132

2. **Define the Target:**
   * Navigate to **Configuration > Targets**.
   * Click the **New Target** (blue star) icon.
   * Set **Hosts** to `192.168.79.132`.
   * Set **Alive Test** to `ICMP Ping`.

![Target setup](screenshots/04-target-config.png)

3. **Task Setup:**
   * Navigate to **Scans > Tasks**.
   * Create a new task using the `Full and Fast` configuration for optimal performance.

---

## 📊 Scan Results

Once the task is initiated, the GVM engine processes 170k+ NVTs against the Metasploitable host.

* **Scan Status:** `Running` / `Done`
* **Coverage:** Full enumeration of ports and vulnerability checks.

![Task status and progress](screenshots/05-scan-progress.png)

---

## 🚀 Next Steps

* **Report Export:** Generate a filtered report in XML format to be imported into DefectDojo.
* **Risk Analysis:** Aggregate findings in DefectDojo to prioritize remediation based on business impact.
