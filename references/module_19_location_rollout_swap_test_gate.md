# Module 19: Location Rollout Swap-Test Pre-Deployment Gate

*Source: Sept 24, 2026 Spam Update doctrine (Nico | AI Ranking). Rule definitions live in `../../kirby-local-seo/SKILL.md` Module 7, except the advisory `AggregateRating`/`AggregateOffer` review flag in §19.3, which is defined here pending a matching rule there. This module defines the deployment-time enforcement mechanism only.*

### **19.1 Why a Deployment Gate**
The spam update demotes programmatic location sets at the folder level. The only structural defense is preventing undifferentiated pages from reaching production in the first place. This module specifies an automated lint pass that **blocks bulk programmatic location rollouts unless every page passes the Swap Test**. Manual review after publish is too late — demotion and Crawled-not-indexed classification happen on first crawl.

### **19.2 Gate Scope**
The gate triggers when a deployment diff adds or modifies more than one page under a location/city folder (`/locations/`, `/city-pages/`, or any folder whose pages follow a `{template}+{locality}` naming pattern). Single-page edits to genuinely unique pages (contact, about, service hub) are out of scope.

### **19.2a Freeze Interlock**
The gate additionally **blocks production deploys of new/modified location sets between Nov 10 and ~Dec 1, 2026** (core update rollout + 7 days; `Module 7 §7.6` / `../../kirby-seo-telemetry/SKILL.md` Module 16) unless the diff is a logged defect fix. Staging branches may still be linted.

### **19.3 Automated Lint Checks**
The linter implements mechanical proxies for the Module 7 rules, plus one advisory review flag (rating/offer markup) that has no matching Module 7 rule yet. **Mechanical checks gate the deploy; they never clear it alone**: a page passing all mechanical checks still requires the human metadata pass (`../../kirby-aiseo-skill/SKILL.md` Module 15 §15.2).

| Check | Mechanism | Block Condition |
|---|---|---|
| Swap Test (Rule 1) | Cross-page n-gram similarity within the folder + locality-token masking: replace every locality token with a placeholder, then measure substance overlap between sibling pages | >50% shared substance between any two pages after locality masking |
| Schema uniqueness (Rule 2) | Parse each page's JSON-LD; assert distinct `url`, `areaServed` matching the page's locality, `serviceType` present, single shared provider `@id` | Missing block, duplicated `url`/`areaServed`, or multiple provider `@id`s across the set |
| Rating/offer markup (advisory, no matching Rule in `kirby-local-seo` Module 7 yet) | Report any `AggregateRating` or `AggregateOffer` on a non-ecommerce page; the human reviewer confirms whether the ratings are backed by genuine reviews visible on the page. One reported study (source not recorded in the dossier) found that stripping this markup was followed by the removal of a suppression within 24 to 48 hours (the study author's claim; single source, directional, unverified, and the timing is implausibly fast for a folder-level classifier action, so do not plan around it); that is removing a risk, not gaining a lift. Separately, `LocalBusiness` JSON-LD showed no measured ranking lift in one reported study (source not recorded in the dossier; single source, unverified), so treat schema as an identifier aid rather than a ranking lever | None (human-review item, not a build failure, until the finding is verified). Ecommerce pages and the `AggregateOffer` use in `kirby-seo-deployment` Module 7 §7.20 and `kirby-aiseo-skill` §2.49 are the ecommerce carve-out: apply this flag only to non-ecommerce pages |
| Alt-text honesty flags (Rule 3) | Flag alt text containing "our team", "our job", "our crew" on images whose file hash matches a stock/AI asset or is reused across localities | First-hand claims on non-unique assets |
| Landmark spam (Rule 6) | Detect bottom-of-page landmark/zip lists (locality names in list context, no sentence context) | Landmark list blocks |
| Cross-locality asset reuse (Rules 3, 9) | Hash photos/videos; identical asset on >1 locality page | Any reuse |

### **19.4 Wiring**
*   **Pre-commit / pre-push:** run the linter on staged files under location folders; fail with the per-page report (which rule, which sibling collision).
*   **CI (authoritative):** run on the full deployment diff so partial local commits cannot bypass the folder-level similarity check — similarity is computed across the *deployed set*, not just the commit.
*   **Report format:** per URL — rule, evidence (similarity %, colliding sibling, failed assertion), and the remediation pointer into Module 7 §7.4.
*   **Escape hatch:** none for the Rule 1 and Rule 2 structural assertions (the `AggregateRating`/`AggregateOffer` flag is a human-review item, not a build failure). A page that cannot achieve 50% variance does not ship; Gate 0 says the page should not exist.

### **19.5 Post-Gate Loop**
Pages that pass and ship still land under telemetry surveillance: `../../kirby-seo-telemetry/SKILL.md` Module 11 tracks the folder through the next core-update window, so a gate miss (mechanically passing but humanly thin) surfaces as a differentiation-deficit alert rather than a silent demotion.
