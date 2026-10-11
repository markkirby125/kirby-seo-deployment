# Module 19: Location Rollout Swap-Test Pre-Deployment Gate

*Source: Sept 24, 2026 Spam Update doctrine (Nico | AI Ranking). Rule definitions live in `../../kirby-local-seo/SKILL.md` Module 7 — this module defines the deployment-time enforcement mechanism only.*

### **19.1 Why a Deployment Gate**
The spam update demotes programmatic location sets at the folder level. The only structural defense is preventing undifferentiated pages from reaching production in the first place. This module specifies an automated lint pass that **blocks bulk programmatic location rollouts unless every page passes the Swap Test**. Manual review after publish is too late — demotion and Crawled-not-indexed classification happen on first crawl.

### **19.2 Gate Scope**
The gate triggers when a deployment diff adds or modifies more than one page under a location/city folder (`/locations/`, `/city-pages/`, or any folder whose pages follow a `{template}+{locality}` naming pattern). Single-page edits to genuinely unique pages (contact, about, service hub) are out of scope.

### **19.3 Automated Lint Checks**
The linter implements mechanical proxies for the Module 7 rules. **Mechanical checks gate the deploy; they never clear it alone** — a page passing all mechanical checks still requires the human metadata pass (`../../kirby-aiseo-skill/SKILL.md` Module 15 §15.2).

| Check | Mechanism | Block Condition |
|---|---|---|
| Swap Test (Rule 1) | Cross-page n-gram similarity within the folder + locality-token masking: replace every locality token with a placeholder, then measure substance overlap between sibling pages | >50% shared substance between any two pages after locality masking |
| Schema uniqueness (Rule 2) | Parse each page's JSON-LD; assert distinct `url`, `areaServed` matching the page's locality, `serviceType` present, single shared provider `@id` | Missing block, duplicated `url`/`areaServed`, or multiple provider `@id`s across the set |
| Alt-text honesty flags (Rule 3) | Flag alt text containing "our team", "our job", "our crew" on images whose file hash matches a stock/AI asset or is reused across localities | First-hand claims on non-unique assets |
| Landmark spam (Rule 6) | Detect bottom-of-page landmark/zip lists (locality names in list context, no sentence context) | Landmark list blocks |
| Cross-locality asset reuse (Rules 3, 9) | Hash photos/videos; identical asset on >1 locality page | Any reuse |

### **19.4 Wiring**
*   **Pre-commit / pre-push:** run the linter on staged files under location folders; fail with the per-page report (which rule, which sibling collision).
*   **CI (authoritative):** run on the full deployment diff so partial local commits cannot bypass the folder-level similarity check — similarity is computed across the *deployed set*, not just the commit.
*   **Report format:** per URL — rule, evidence (similarity %, colliding sibling, failed assertion), and the remediation pointer into Module 7 §7.4.
*   **Escape hatch:** none for Rules 1–2. A page that cannot achieve 50% variance does not ship; Gate 0 says the page should not exist.

### **19.5 Post-Gate Loop**
Pages that pass and ship still land under telemetry surveillance: `../../kirby-seo-telemetry/SKILL.md` Module 11 tracks the folder through the next core-update window, so a gate miss (mechanically passing but humanly thin) surfaces as a differentiation-deficit alert rather than a silent demotion.
