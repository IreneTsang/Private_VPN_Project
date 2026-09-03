[← Back to overview](../README.md)

# 3. Agile Methodology — Kanban

## 3.1 Why Kanban

Kanban was selected over Scrum for this project based on the following factors:

| Factor | Rationale |
|---|---|
| Solo execution | Scrum ceremonies (standups, retrospectives, sprint planning) are designed for teams — Kanban suits individual contributors |
| Unpredictable blockers | GFW interference, SSH failures, and IP mismatches made sprint-based estimation impractical — work progressed as blockers were resolved |
| Continuous flow | Tasks were completed as soon as they were unblocked rather than batched into fixed sprints |
| Low overhead | Kanban's minimal process allowed focus on delivery rather than ceremony |

## 3.2 Kanban Principles Applied

| Principle | How it was applied |
|---|---|
| Visualise the workflow | Tasks tracked across Backlog → In Progress → Blocked → Done columns |
| Limit work in progress (WIP) | One epic addressed at a time — infrastructure before VPN before client |
| Manage flow | Blockers (GFW, SSH auth, IP mismatch) identified and resolved before progressing |
| Make policies explicit | Clear acceptance criteria defined per user story before work began |
| Improve continuously | Each failure (NordVPN conflict, suspended account, IP mismatch) fed directly into updated documentation |

## 3.3 Kanban Board State — Final

| Column | Items |
|---|---|
| Backlog | None — all items completed |
| In Progress | None — all items completed |
| Blocked | None — all blockers resolved |
| Done | T-01 through T-18 — all tasks complete |

## 3.4 Key Blockers and Resolutions

| Blocker | Root Cause | Resolution |
|---|---|---|
| SSH connection failing | GFW blocking Google Cloud SSH from China | Used secondary VPN (Psiphon) to establish SSH session |
| Outline Manager cannot connect | GFW blocking management port | Outline Manager requires secondary VPN; Outline Client does not |
| NordVPN driver conflict | Residual NordVPN TAP adapter blocking Outline's outline-tap0 | Full uninstall of NordVPN + clean reinstall of Outline Client |
| Google Cloud account suspended | Free trial expired mid-project | Upgraded to paid account; VM and data preserved |
| SSH authentication failed | Account suspension invalidated SSH keys | Deleted old VM; created fresh VM with same static IP |
| Outline IP mismatch | Static IP not attached before Outline installation | Attached static IP first; reinstalled Outline to pick up correct IP |

---

[← Back to overview](../README.md) · [← Previous: Product Backlog](02-product-backlog.md) · [Next: Process Flows →](04-process-flows.md)
