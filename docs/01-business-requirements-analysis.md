[← Back to overview](../README.md)

# 1. Business Requirements Analysis (BRA)

## 1.1 Project Overview

| | |
|---|---|
| **Project title** | DIY Private UK VPN on Google Cloud |
| **Project type** | Personal infrastructure project |
| **Project owner** | Irene |
| **Duration** | May 2026 |
| **Methodology** | Kanban (solo, flow-based delivery) |

## 1.2 Problem Statement

As a British national and UK property owner residing in Guangzhou, China, I required a reliable UK IP address to access UK payment portals and government services. Commercial VPN providers were rejected due to:

- Unreliable UK IP assignment — not guaranteed to route through London
- High monthly cost ($5–$13/month) relative to usage (under 2 hours/month)
- Privacy concerns — shared infrastructure used by thousands of users
- Frequent blocking by the Great Firewall of China (GFW)
- Inability to customise obfuscation settings for GFW bypass

## 1.3 Business Objectives

| Objective | Success Criteria |
|---|---|
| Establish a dedicated UK IP address | ipleak.net confirms IPv4 and IPv6 routing through London |
| Bypass the Great Firewall reliably | Connection succeeds from Guangzhou without interruption |
| Minimise monthly operating cost | Total cost under $5/month for under 2 hours usage |
| Ensure full IPv4 and IPv6 coverage | No IP leaks detected on ipleak.net |
| Maintain privacy and sole ownership | No shared infrastructure — private server only |

## 1.4 Stakeholders

| Stakeholder | Role | Interest |
|---|---|---|
| Irene | Project owner and sole user | Reliable, low-cost UK IP for bill payment |
| UK entities | External system | Accepts payments from verified UK IP addresses |
| Google Cloud | Infrastructure provider | Compute and networking services |
| Outline / Jigsaw (Google) | Software provider | Open-source VPN software used for deployment |

**Engagement approach:** as a solo project, Irene held Responsible and Accountable for every stakeholder decision. The remaining RACI roles — Consulted and Informed — were not applicable, since there was no team to delegate to.

## 1.5 Functional Requirements

| ID | Requirement |
|---|---|
| FR-01 | System must assign a static UK (London) IP address to all outbound traffic |
| FR-02 | System must route both IPv4 and IPv6 traffic through the UK server |
| FR-03 | System must obfuscate VPN traffic to bypass GFW deep packet inspection |
| FR-04 | System must support multiple device connections via access keys |
| FR-05 | System must allow VM to be stopped and restarted without IP address change |
| FR-06 | System must provide a management interface (Outline Manager) for key administration |

## 1.6 Non-Functional Requirements

| ID | Requirement |
|---|---|
| NFR-01 | Monthly cost must not exceed $5 under normal usage patterns |
| NFR-02 | Connection must be established within 60 seconds of VM start |
| NFR-03 | System must remain operational without manual intervention once configured |
| NFR-04 | Server must be located in the London (europe-west2) Google Cloud region |
| NFR-05 | Solution must be maintainable by a non-technical user following documented steps |

## 1.7 Constraints and Assumptions

**Constraints**

- The Great Firewall of China actively blocks standard VPN protocols — obfuscation is mandatory
- Google Cloud SSH browser tool is subject to GFW interference — a secondary VPN is required for server management
- Google Cloud free trial is limited to one account per payment method
- Static IP must be reserved separately to survive VM stop/start cycles

**Assumptions**

- User has access to a UK-issued payment card for Google Cloud billing
- User has a secondary VPN available (e.g. Psiphon) for initial server setup
- Ubuntu 22.04 LTS and Docker are sufficient for Outline VPN deployment
- e2-micro compute tier provides adequate performance for personal VPN use

## 1.8 Risks and Mitigations

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| GFW blocks Google Cloud IPs | Medium | High | Switch to Vultr or Hetzner London servers |
| VM IP changes on restart | High | Medium | Reserve static IP before installation |
| SSH connection drops during installation | High | Low | Re-run installer — idempotent script |
| Google Cloud account suspension | Low | High | Upgrade to paid account immediately |
| Outline Client conflicts with other VPN software | Medium | Medium | Uninstall conflicting VPN drivers before installation |

## 1.9 Requirements Traceability

Each functional requirement is traced to the user stories that implement it and the evidence that verifies it:

| Requirement | Traced To (User Stories) | Verification |
|---|---|---|
| FR-01 | US-01, US-02, US-08 | VM provisioned in europe-west2; static IP attached; ipleak.net confirms UK IPv4 address |
| FR-02 | US-08 | ipleak.net confirms UK IPv4 routing; IPv6 routing not independently verified by any acceptance criteria — flagged as a follow-up check |
| FR-03 | US-04, US-07, US-08 | Outline shadowbox container running; Client connects from Guangzhou; UK IP confirmed despite GFW deep packet inspection |
| FR-04 | US-06, US-07 | Outline Manager key list populated; per-device keys renamed and distributed via QR code |
| FR-05 | US-02, US-09, US-11 | Static IP persists across stop/start cycles; no reconfiguration required after restart |
| FR-06 | US-05, US-06 | apiUrl and certSha256 retrieved; Outline Manager dashboard shows green status |

> **Note on FR-02:** the traceability matrix records that IPv6 routing has no independent acceptance-criteria check — an example of the kind of gap a traceability exercise is meant to surface, rather than something to quietly patch after the fact.

---

[← Back to overview](../README.md) · [Next: Product Backlog →](02-product-backlog.md)
