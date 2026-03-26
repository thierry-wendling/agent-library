# Role-specific evidence (reference)

Guidance for which artifacts tend to matter for which competencies. **Role labels and evidence types must align with the manager’s rubric and engineering domain** — adjust rows using inputs from [reference-org-configuration.md](reference-org-configuration.md).

### Recommended evidence inputs by role archetype

Not all inputs are equally available or useful across roles. Use this as a collection guide.

**For product / feature-team engineers** (customer-facing or roadmap-owned delivery):

| Input | Signal quality | Typical competency signal |
|---|---|---|
| Pull requests (code + reviews left on others) | ⚠️ Limited without context | Craftsmanship, Architecture, Leadership — use GitHub MCP or `gh` when available |
| Design docs / RFCs / written analyses in the wiki | ✅ High | Architecture, Leadership (communication), Craftsmanship |
| Quantitative outcomes (product metrics, SLOs, adoption, quality) | ✅ High | Impact |
| Work trackers (Jira, Linear, etc.) — breakdown, escalation, cycle time | ⚠️ Medium | Autonomy, Impact — quantity ≠ quality |
| Product / partner / EM input | ✅ High | Impact, Leadership, Autonomy |
| Retrospectives | ⚠️ Medium | Leadership, Impact |
| Incidents / postmortems | ✅ High | Autonomy, Craftsmanship |
| Manager 1:1 notes | ✅ High | Trajectory, Autonomy |
| Chat / email (if available) | ⚠️ Low–Medium | Leadership — prefer patterns over volume |

**For platform / internal-tooling engineers** (infra, dev productivity, shared services):

| Input | Signal quality | Typical competency signal |
|---|---|---|
| Pull requests (infra, tooling, pipelines) | ⚠️ Limited without context | Craftsmanship, Architecture |
| Reliability / performance / cost metrics | ✅ High | Impact, Craftsmanship |
| Feedback from internal customers (feature teams, SRE, etc.) | ✅ High | Impact, Leadership |
| Incidents / postmortems | ✅ High | Autonomy, Craftsmanship, Architecture |
| Runbooks / diagrams / docs in the wiki | ✅ High | Architecture, Leadership |
| Throughput / toil / onboarding-time trends | ✅ High | Impact — often invisible without metrics |
| Reduction in support burden | ⚠️ Medium | Impact — needs baseline |

### Competency coverage by artifact type

Be aware of what artifacts alone cannot tell you (exact competency names may match the org rubric):

| Competency (example) | Artifact coverage | What’s still missing |
|---|---|---|
| Craftsmanship | ✅ Good — PRs, tests, detailed write-ups | Depth of judgment may need technical discussion |
| Architecture | ✅ Good — designs, RFCs, ADRs | Only if they document; “silent” work leaves less trail |
| Autonomy | ⚠️ Partial — tickets, chat | Quality of judgment and proactive escalation need observation |
| Leadership | ⚠️ Partial — reviews, docs | Mentoring and feedback quality often need peers + manager |
| Impact | ⚠️ Weak in repos alone | Business or user outcomes need metrics and stakeholders |

**Practical implication:** artifacts are necessary but not sufficient. For Leadership and Impact especially, supplement with direct observation, stakeholder input, and peer feedback.
