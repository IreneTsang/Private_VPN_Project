[← Back to overview](../README.md)

# 2. Product Backlog

## 2.1 Epic Overview

| Epic ID | Epic Name | Description |
|---|---|---|
| EP-01 | Infrastructure setup | Provision and configure cloud server in UK region |
| EP-02 | VPN installation | Install and configure Outline VPN on the server |
| EP-03 | Client connectivity | Connect devices to the VPN and verify UK IP |
| EP-04 | Cost optimisation | Minimise monthly running cost for low-frequency usage |
| EP-05 | Resilience and maintenance | Ensure system survives restarts, IP changes, and GFW interference |

## 2.2 User Stories and Tasks

### EP-01 — Infrastructure setup

| Story ID | User Story | Acceptance Criteria |
|---|---|---|
| US-01 | As a user, I want a cloud server in London so that my traffic appears to originate from the UK. | VM created in europe-west2 (London) region running Ubuntu 22.04 LTS |
| US-02 | As a user, I want a static IP address so that my VPN configuration does not break when the server restarts. | Static external IP reserved and attached to VM; IP persists across stop/start cycles |
| US-03 | As a user, I want firewall rules configured so that VPN traffic can reach my server. | TCP and UDP all ports open; Outline successfully receives incoming connections |

**Tasks for EP-01**

| Task ID | Task | Status |
|---|---|---|
| T-01 | Create Google Cloud account and enable billing | Done |
| T-02 | Create e2-micro VM in europe-west2 (London) | Done |
| T-03 | Set boot disk to Ubuntu 22.04 LTS | Done |
| T-04 | Create firewall rule — TCP + UDP all ports | Done |
| T-05 | Reserve static external IP in europe-west2 | Done |
| T-06 | Attach static IP to VM network interface | Done |

### EP-02 — VPN installation

| Story ID | User Story | Acceptance Criteria |
|---|---|---|
| US-04 | As a user, I want Outline VPN installed on my server so that I can route traffic through a UK IP. | Outline shadowbox and watchtower Docker containers running; `sudo docker ps` shows both Up |
| US-05 | As a user, I want the apiUrl string so that I can connect Outline Manager to my server. | `sudo cat /opt/outline/access.txt` returns valid certSha256 and apiUrl values |

**Tasks for EP-02**

| Task ID | Task | Status |
|---|---|---|
| T-07 | Connect to VM via SSH browser tool (with secondary VPN active) | Done |
| T-08 | Run Outline install script via `wget` | Done |
| T-09 | Confirm Docker installation (type Y when prompted) | Done |
| T-10 | Resolve Watchtower container conflict (type Y to replace) | Done |
| T-11 | Retrieve apiUrl from `/opt/outline/access.txt` | Done |
| T-12 | Verify static IP matches apiUrl IP — reinstall if mismatch | Done |

### EP-03 — Client connectivity

| Story ID | User Story | Acceptance Criteria |
|---|---|---|
| US-06 | As a user, I want Outline Manager connected to my server so that I can manage access keys. | Outline Manager shows green server dashboard with key list |
| US-07 | As a user, I want Outline Client installed on my devices so that I can connect to the VPN. | Outline Client connects successfully and shows green status |
| US-08 | As a user, I want to verify my UK IP so that I can confirm the VPN is working correctly. | ipleak.net shows UK IPv4 address with no Chinese IP leaks |

**Tasks for EP-03**

| Task ID | Task | Status |
|---|---|---|
| T-13 | Format apiUrl and certSha256 into JSON string | Done |
| T-14 | Paste JSON string into Outline Manager — add server | Done |
| T-15 | Rename default keys (Key 0, Key 1, Key 2) per device | Done |
| T-16 | Share key to phone via QR code — install Outline Client | Done |
| T-17 | Resolve NordVPN driver conflict on Windows laptop | Done |
| T-18 | Verify UK IP on ipleak.net — confirm no leaks | Done |

### EP-04 — Cost optimisation

| Story ID | User Story | Acceptance Criteria |
|---|---|---|
| US-09 | As a user, I want to stop the VM when not in use so that I minimise my monthly cloud spend. | VM stopped after each use session; monthly cost confirmed below $2.50 with static IP |
| US-10 | As a user, I want a cost breakdown so that I can plan my monthly spend. | Cost model documented: ~$0.44 storage + $1.46 static IP = ~$1.90/month when stopped |

### EP-05 — Resilience and maintenance

| Story ID | User Story | Acceptance Criteria |
|---|---|---|
| US-11 | As a user, I want the VPN to survive VM restarts so that I do not need to reconfigure devices after each session. | Static IP ensures Outline Client and Manager require no reconfiguration after restart |
| US-12 | As a user, I want to know how to recover from SSH failures so that I can resolve issues independently. | Recovery procedure documented: retrieve apiUrl via access.txt; reinstall via idempotent script |

---

[← Back to overview](../README.md) · [← Previous: BRA](01-business-requirements-analysis.md) · [Next: Kanban Methodology →](03-kanban-methodology.md)
