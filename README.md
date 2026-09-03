# DIY Private UK VPN — Business Analyst Project Portfolio

![Methodology](https://img.shields.io/badge/methodology-Kanban-2E9E6C) ![Cloud](https://img.shields.io/badge/cloud-Google%20Cloud-4285F4) ![VPN](https://img.shields.io/badge/vpn-Outline%20%2F%20Shadowsocks-informational) ![Container](https://img.shields.io/badge/container-Docker-2496ED) ![Status](https://img.shields.io/badge/status-Complete-brightgreen)

A self-directed infrastructure project, documented end-to-end using standard Business Analyst artifacts: a Business Requirements Analysis, a traceable product backlog, an applied Kanban workflow, process/decision flow modelling, and a retrospective.

The project itself — a private UK VPN, built on Google Cloud, to reach UK payment portals and government services from mainland China — is deliberately small. The point of this repo is the **discipline behind it**: how the problem was scoped, how requirements were captured and traced to evidence, how work was sequenced and tracked, and how failures were converted into lessons rather than lost.

> 📄 A print-formatted version of the full document is available at [`assets/DIY-Private-UK-VPN-Portfolio.pdf`](assets/DIY-Private-UK-VPN-Portfolio.pdf). Everything in it is also reproduced below as native, browsable Markdown.

---

## At a glance

| | |
|---|---|
| **Project owner** | Irene Tsang (sole user, sole delivery) |
| **Duration** | May 2026 |
| **Methodology** | Kanban (solo, flow-based delivery) |
| **Stack** | Google Cloud (Compute Engine, europe-west2), Outline/Jigsaw (Shadowsocks), Docker, Ubuntu 22.04 LTS |
| **Requirements traced** | 6 functional, 5 non-functional — 100% traced to user stories and verification evidence |
| **Backlog delivered** | 5 epics · 12 user stories · 18 tasks — 100% complete, zero items left in Backlog/In Progress/Blocked |
| **Result** | Static London IPv4 address, GFW-resilient connection, running cost ≈ **$1.90/month** stopped between uses (target was <$5/month) |

## Contents

1. [Business Requirements Analysis](docs/01-business-requirements-analysis.md) — problem statement, objectives, stakeholders, functional & non-functional requirements, constraints, risks, and requirements traceability
2. [Product Backlog](docs/02-product-backlog.md) — epics, user stories, acceptance criteria, and tasks
3. [Agile Methodology — Kanban](docs/03-kanban-methodology.md) — why Kanban, principles applied, final board state, blockers and resolutions
4. [Process Flows](docs/04-process-flows.md) — the VPN connection routine and the troubleshooting decision flow, modelled as diagrams
5. [Retrospective and Lessons Learned](docs/05-retrospective.md) — what would change in scoping a similar project again

## Why this structure

Each document maps to an artifact a Business Analyst actually produces on a real engagement:

- The **BRA** shows requirements elicitation from a genuine constraint set (cost, privacy, censorship circumvention) through to measurable, testable acceptance criteria — including a full requirements traceability matrix linking every functional requirement to the user story that implemented it and the evidence that verified it.
- The **backlog** shows requirements decomposed into epics and INVEST-style user stories, each with explicit acceptance criteria, broken into executable tasks.
- The **Kanban section** justifies a methodology choice against the shape of the work (solo execution, unpredictable blockers) rather than defaulting to it, and shows WIP limits and flow-management principles actually applied.
- The **process flows** model both the happy path and the failure/decision path — the two views a BA needs to hand off a process to someone else.
- The **retrospective** is the most BA-relevant page in the repo: it re-examines three real blockers and identifies which ones a pre-mortem against the stated constraints would have caught during planning, rather than during troubleshooting.

---

*Irene Tsang · DIY Private UK VPN · Analyst Portfolio 2026*
