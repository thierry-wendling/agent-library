# Organisation configuration (reference)

All **concrete** wiki spaces, repos, naming patterns, and domain wording must come from the manager (or a pasted org brief) — not assumed by the skill.

Collect this **once per review cycle** (or when the manager switches companies). Store the answers and substitute the bracketed placeholders used in [reference-evidence-fetching.md](reference-evidence-fetching.md).

| Topic | Placeholder | What to ask |
|--------|-------------|-------------|
| **Review period** | `[review period start date]` | Start and end dates (default: last 6 months if acceptable). |
| **Engineering domain** | — | Short description (e.g. backend product, mobile, data platform, infrastructure). Used to choose **supplemental search terms** and interpret artifacts — not to hard-code any industry. |
| **Competency rubric** | — | The formal framework (behaviours per level). Names of competencies may vary by org. |
| **Atlassian site** | `[ATLASSIAN_SITE]` | e.g. `company.atlassian.net` — confirm via API/tooling. |
| **Atlassian `cloudId`** | `[CLOUD_ID]` | From `getAccessibleAtlassianResources` (or equivalent). Never invent a UUID. |
| **Wiki — product / feature work** | `[PRIMARY_FEATURE_SPACE_KEY]` | Space key(s) where ICs document customer-facing or product engineering work (RFCs, designs, analyses). |
| **Wiki — platform / internal** | `[PLATFORM_SPACE_KEYS]` | Space key(s) for platform, infra, tooling, shared services (comma-separated or `IN (...)` list). |
| **Wiki — team reviews** | `[REVIEW_SPACE_KEY]` | Space where periodic team/delivery/business review pages live (may match feature space or differ). |
| **Team review title pattern** | `[REVIEW_TITLE_PATTERN]` | How pages are titled, e.g. `"Quarterly review: [Team] - [Period]"` or `"Sprint review [Team]"`. |
| **Engineer’s team label** | `[TEAM_NAME_IN_REVIEW_TITLE]` | The string used in that title for this engineer’s group (so you can find the right pages). |
| **GitHub** | `[GITHUB_OWNER]/[GITHUB_REPO]` | Primary repo(s) to query for PRs; may be a list if the team uses several. |
| **Doc / ticket naming** | — | Optional: common title prefixes or labels the org uses (helps classification, not required). |

If any value is unknown, **ask before running broad automated queries**. Where tools are missing, fall back to the manager pasting exports or summaries.
