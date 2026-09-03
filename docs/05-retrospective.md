[← Back to overview](../README.md)

# 5. Retrospective and Lessons Learned

Looking back across the blockers logged in [3.4](03-kanban-methodology.md#34-key-blockers-and-resolutions), a few things would change how I'd scope a similar project next time:

- **NordVPN driver conflict** — I would like to add "audit existing VPN clients on target devices" as an explicit task under EP-01, before installation, rather than discovering the conflict mid-connection. A five-minute check would have prevented a same-day support loop.
- **Google Cloud account suspension** — the free trial's billing-cycle risk was never captured as a requirement at all. In hindsight, "billing account must not lapse mid-build" belongs alongside NFR-03, since an unplanned outage is functionally the same failure whether it's technical or administrative.
- **Outline IP mismatch** — this only surfaced because installation ran before the static IP was attached. A dependency note on the EP-01/EP-02 tasks — "static IP must be attached before VPN installation" — would have caught it during planning instead of during troubleshooting.

More generally, treating each blocker as a documentation update worked well for capturing resolutions after the fact (see [3.2, "Improve continuously"](03-kanban-methodology.md#32-kanban-principles-applied)). Still, a short pre-mortem against the constraints in [1.7](01-business-requirements-analysis.md#17-constraints-and-assumptions) would have caught at least two of these three issues before they happened rather than after.

That's the gap between a backlog that tracks what got built and one that captures why it went the way it did — and it's the habit I'd bring into a BA role.

---

[← Back to overview](../README.md) · [← Previous: Process Flows](04-process-flows.md)
