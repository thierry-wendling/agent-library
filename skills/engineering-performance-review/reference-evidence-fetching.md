# Evidence fetching (reference)

Use this file when automatically gathering artifacts. Confirm the **review period** and load **organisation settings** from [reference-org-configuration.md](reference-org-configuration.md) before querying. Substitute placeholders such as `[CLOUD_ID]`, `[PRIMARY_FEATURE_SPACE_KEY]`, and `[GITHUB_OWNER]/[GITHUB_REPO]` with values the manager provided — do not assume a specific company, domain, or wiki layout.

## Automated evidence fetching

When an engineer's name is provided, automatically fetch evidence from connected data sources
**before** asking the manager for any manual inputs. Do this silently and present a summary of
what was found. Only ask the manager for additional inputs after fetching is complete.

### Wiki and issue tracker (e.g. Atlassian Confluence + Jira) — when tools exist

**Step 0 — Confirm workspace:**

Before fetching, resolve the correct site / `cloudId` (e.g. via `getAccessibleAtlassianResources` or your environment’s equivalent). If multiple workspaces are returned, ask the manager which one to use.

Use the org’s search tools (e.g. `searchAtlassian`, `getConfluencePage`, `searchJiraIssuesUsingJql`, `lookupJiraAccountId`) when available. Tool names vary by integration — adapt to what is actually connected.

**Wiki — search strategy:**

Doc naming conventions differ by org — do **not** rely on title prefixes alone. Use a two-pass approach.

**Pass 0 — Know your spaces:**

From configuration, record:

- `[PRIMARY_FEATURE_SPACE_KEY]` — where product/feature engineers document work (designs, analyses, RFCs).
- `[PLATFORM_SPACE_KEYS]` — where platform/internal engineers document runbooks, infra, tooling (may overlap or be separate).

If the manager only has one primary space, use it for both passes and widen if results are thin.

**Pass 1 — broad author search, scoped by role:**

Use the confirmed review period start date (default: 6 months ago) in all queries.

For **product / feature engineers** — search primary feature space(s) first:

```
contributor = "[engineer display name]"
AND type = page
AND space.key = "[PRIMARY_FEATURE_SPACE_KEY]"
AND lastmodified >= "[review period start date]"
ORDER BY lastmodified DESC
```

For **platform / internal engineers** — search platform space(s):

```
contributor = "[engineer display name]"
AND type = page
AND space.key IN ([PLATFORM_SPACE_KEYS])
AND lastmodified >= "[review period start date]"
ORDER BY lastmodified DESC
```

Retrieve up to 25 results. If fewer than 5 found in primary spaces, re-run without the space
filter to catch cross-space contributions.

**Pass 2 — targeted content searches (fills gaps from Pass 1):**

Run supplemental searches to catch docs the engineer did not author alone. Use the **manager’s engineering domain**, **org vocabulary**, and **rubric** to pick keywords — the table below is illustrative only:

| Search query (pattern) | What you're looking for | Typical competency signal |
|---|---|---|
| `[engineer name] [domain keyword] design` | Solution / technical design | Architecture, Craftsmanship |
| `[engineer name] architecture review` | Architecture review | Architecture, Leadership |
| `[engineer name] post-mortem` / `postmortem` | Failure analyses | Craftsmanship, Autonomy |
| `[engineer name] decision` / `tradeoff` / `ADR` | Decision logs | Architecture, Autonomy |
| `[engineer name] [rubric-specific term]` | Anything the rubric names explicitly | Per rubric |

**Classifying docs without clear type prefixes:**

When a doc title doesn't indicate its type, use the content to classify it:
- Contains hypothesis, measurements, comparative results → **analysis / evaluation**
- Contains system diagram, options considered, tradeoffs → **solution design**
- Contains review of architectural choices, recommendations → **architecture review**
- Contains what went wrong, root cause, learnings → **error analysis / post-mortem**
- Contains rationale for a choice between alternatives → **decision log**
- Otherwise → classify as **general technical doc** (still useful evidence)

For each result, fetch the full page when the tool supports it and assess:
- **Quality of problem framing** — problem and success criteria clear?
- **Rigour of approach** — alternatives, tradeoffs, edge cases?
- **Quality of conclusions** — outcomes and learnings documented?
- **Communication clarity** — understandable to someone unfamiliar?

**Wiki — document quality rubric:**

| Signal | Weak | Strong |
|---|---|---|
| Problem framing | Vague or assumed | Clearly stated with success criteria |
| Options considered | One approach only | Multiple alternatives with tradeoffs |
| Decisions documented | Implicit or missing | Explicit rationale recorded |
| Outcomes/learnings | Not captured | Quantified results + lessons learned |
| Audience awareness | Written for self | Accessible to unfamiliar reader |

**Wiki — speed and iteration signals (Craftsmanship differentiator):**

If the API exposes page version (`version.number` or similar), use it cautiously as a proxy for iteration count:

| Version count at reviewed/done state | Interpretation |
|---|---|
| 1–3 versions | Strong first-pass quality — clear thinking before writing |
| 4–7 versions | Normal iteration for complex work |
| 8+ versions | High iteration — may indicate unclear framing or rework |

**Important caveats:**
- Version count alone is not reliable — interpret with doc complexity and whether edits are substantive vs. trivial.
- Many review cycles with PM, peers, and other stakeholders is different from many silent edits.
- Use comparatively within the same engineer or across peers at the same level.

**Time to “done” or approved status** is often more meaningful than raw version count when visible.

**Issue tracker — relevant signals:**

Resolve assignee to account ID if your JQL requires it (e.g. `lookupJiraAccountId`).

```
assignee = "[engineer accountId]" AND updated >= "[review period start date]" ORDER BY updated DESC
```

Look for:
- **Ticket breakdown quality** — well-scoped subtasks? (Autonomy)
- **Blocker escalation** — clear and proactive? (Autonomy)
- **Ticket descriptions** — acceptance criteria and context? (Craftsmanship, Leadership)
- **Delivery speed** — created → Done timing (Craftsmanship, Autonomy)
- **Delivery patterns** — steady vs. stalled? (Autonomy, Impact)
- **Scope** — cross-cutting or high-complexity work? (Impact)

**Issue tracker — speed as a Craftsmanship signal:**

Interpret cycle time carefully: fast on well-scoped tickets vs. fast on trivial tickets; stalls without blockers vs. documented dependency. Do **not** use raw ticket count as quality.

### GitHub (pull requests) — Craftsmanship and Leadership

Use `[GITHUB_OWNER]/[GITHUB_REPO]` from configuration. If multiple repos matter, query each or ask the manager which are primary.

**Step 1 — Determine what GitHub access is available:**

Try in order:

1. **GitHub MCP** (if present) — query PRs for the engineer.
2. **GitHub CLI** — if `gh` is installed and authenticated:

```bash
gh pr list --repo [GITHUB_OWNER]/[GITHUB_REPO] \
  --author [github-username] \
  --state merged \
  --json number,title,createdAt,mergedAt,additions,deletions,comments \
  --limit 50
```

(Review-request queries depend on API shape — adapt to your environment.)

3. **Neither available** — ask the manager to paste `gh` output, a summary from the UI, or rough cadence.

**Step 2 — What to extract and assess:**

| Signal | How to measure | Competency | What it tells you |
|---|---|---|---|
| PR cycle time | Opened → merged | Craftsmanship | Delivery speed and first-pass quality |
| Review rounds | Rework after review | Craftsmanship | How much reviewers had to push |
| PR description quality | Clarity, context | Craftsmanship, Leadership | Makes work legible? |
| Reviews on others’ PRs | Substance of comments | Leadership | Develops peers? |
| PR size | Scope vs. complexity | Craftsmanship, Autonomy | Reviewable units? |

**PR reviews on others’ code (Leadership):**

- Lower maturity: helpful when asked.
- Higher maturity: seeks reviews proactively; teaches in comments.
- Quality beats volume.

**If no GitHub data:** proceed without it; note the gap. Wiki + tracker data still partially cover delivery and collaboration.

### Periodic team / delivery reviews — team-level Impact context

Many orgs publish **monthly or quarterly team reviews** (delivery, capacity, roadmap) in the wiki. Names and locations vary.

From configuration you should have:

- `[REVIEW_SPACE_KEY]` — wiki space containing these pages.
- `[REVIEW_TITLE_PATTERN]` — how titles are formed (e.g. includes team name + period).
- `[TEAM_NAME_IN_REVIEW_TITLE]` — which team this engineer belongs to.

**How to fetch:**

Use the manager’s pattern. Example JQL/CQL-style pattern (adjust placeholders):

```
title ~ "[TEAM_NAME_IN_REVIEW_TITLE]" AND space.key = "[REVIEW_SPACE_KEY]" AND type = page
ORDER BY created DESC
```

Fetch the 2–3 most recent relevant pages and extract:

| Signal | What to look for |
|---|---|
| **Capacity / allocation** | Feature vs. ops vs. debt — context for individual output |
| **Delivery items** | Is this engineer named? What shipped? |
| **Metrics** | Product, reliability, or adoption metrics the org tracks |
| **Learnings** | Are outcomes and retrospectives captured? |
| **Roadmap** | On track, delayed, descoped? |

**How to use in assessment:**

1. **Individual impact** — explicit mentions of the engineer’s work in delivery or learnings.
2. **Team context** — heavy ops load or instability affects interpretation; do **not** blame individuals for team-level context unless evidence ties to them.

### Post-fetch sequence — follow this order exactly

After automated fetching, **before** calibration or full narratives:

**Step A — Present evidence summary**

```
EVIDENCE FETCHED — [Engineer Name]
Review period: [start date] to [end date]

Wiki docs found: [N]
  - [Title] — [doc type: analysis / solution design / architecture review / other]
  - ...

Tracker activity: [N items, date range]
  Notable patterns: [...]

GitHub PR data: [Available / Not available — manager input requested]
  ...

Chat observations: [Not yet collected — will ask below]

Team/delivery reviews: [N fetched for team X, periods ...]
  Allocation / delivery trend: [...]
  Engineer named in items: [Yes / No / Partially]
  Key metrics visible: [...]

Evidence gaps:
  - [Competency]: No [artifact type] — will flag low confidence unless supplemented
```

**Step B — Collect remaining inputs in one ask**

After presenting the evidence summary, ask for everything still needed in **one** message:

- Self-assessment (upload/paste).
- Peer feedback (any form).
- Chat / cross-functional observations if relevant.
- GitHub paste if fetch failed.

Accept partial responses — never block the whole review.

**Peer feedback signal weighting (once received):**

For each piece, note source role (peer IC, PM, partner team, etc.), competencies, and whether it corroborates or contradicts artifacts.

Typical weighting (adjust to org):

- **Peer ICs in same discipline** — strong on Craftsmanship, Architecture, technical Leadership.
- **PM / product / partner** — strong on Impact, cross-functional Autonomy, communication.
- **Other engineering teams** — collaborative Leadership, day-to-day Autonomy.

**Handling thin, contradictory, or absent peer feedback:**

- **Thin (one reviewer):** Treat as one data point; Medium confidence at best for covered areas.
- **Contradictory:** Surface explicitly in calibration; ask the manager to resolve.
- **Absent:** Note for Leadership especially; consider visibility vs. logistics.
- **Uniformly positive for everyone:** May be social filtering — flag; manager observation weighs more.

Then proceed to the workflow in [reference-workflow-narratives.md](reference-workflow-narratives.md).
