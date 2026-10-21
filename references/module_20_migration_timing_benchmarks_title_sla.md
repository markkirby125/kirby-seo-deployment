# Module 20: Migration Timing Benchmarks & Title-Update SLA Rules

*Source: Google's official processing-pipeline benchmarks disclosed by Gary Illyes (Search Central Live Deep Dive Europe, Barcelona, Oct 2, 2026; analyzed by Edward Sturm, Ep. E1192). The benchmark table, confidence tiers, forecasting math, and diagnosis doctrine live in `../../kirby-seo-timing-benchmarks/SKILL.md` — this module wires those numbers into deployment staging. Do not duplicate the Matrix here.*

## 20.1 Scope

This module governs **deployment-side timing rules** only:
- Migration staging and cutover schedules anchored to Google's published consolidation windows.
- Post-deploy title/snippet SLA expectations for publishing pipelines and change-verification gates.
- Stall escalation triggers that hand off to telemetry instrumentation (`../../kirby-seo-telemetry/SKILL.md` Module 12).

Client-facing SLA language, contract annexes, and expectation scripts are **not** here — they are `../../kirby-seo-timing-benchmarks/SKILL.md` Reference 04.

## 20.2 Migration Staging Under Empirical Windows

Benchmark anchors (Tier 1, press-corroborated): **site migration signal consolidation runs 1–3 months typical, 6 months to 1+ year slowest case**; canonical convergence adds 1–3 weeks post-cutover under clean signals and extends to months under conflicting ones.

**Staging rules:**
1. **Pre-cutover signal purge (mandatory).** Before any flip, eliminate the three canonical-lag accelerants: internal links pointing at deprecated URLs, sitemaps listing non-canonicals, and chained/conflicting 301s. Mixed signals convert the 1–3 week canonical window into months.
2. **Single-event cutover.** Stage the complete URL map + redirect layer + regenerated sitemaps behind a release gate; flip once. Rolling partial cutovers reset the consolidation clock on each tranche.
3. **Sitemap discipline at cutover.** Regenerate and submit XML sitemaps in the same deploy: canonical-only URLs, true `lastmod`, ≤50k/50MB per file. Expected processing: ~24h typical, up to 14 days slow tail — do not "resubmit spam" inside that window.
4. **Freeze window.** No new architecture changes layered on top during the 1–3 month consolidation window (checkpoints at 30/60/90 days). Mid-window restructuring makes it impossible to attribute recovery or regression.
5. **Escalation gate at 6 months.** Traffic materially below the pre-migration baseline at month 6 exhausts the slow-case window: trigger full technical re-audit + per-template quality review (framework: `../../kirby-seo-timing-benchmarks/SKILL.md` Reference 03 §3.4). Past 6 months, the deficit is not Google's queue.
6. **Interaction with Module 17.** Satellite EMD and expired-domain migrations inherit the same windows — an acquired domain's signal transfer is also a 1–3 month consolidation, and 410-vs-404 retirement of dead URLs follows §7.7 (410 drops dead URLs ~2x faster than passive 404s).

## 20.3 Title & Snippet Update SLA Rules for Publishing Pipelines

Benchmark anchors: title/snippet SERP changes land in **1–2 days typical** — but that row assumes the page is already on a hot recrawl cadence. The governing gate for an average established page is the **~30-day recrawl** cycle.

**Pipeline rules:**
1. **Deploy-time expectations for content edits:** plan verification of title/meta changes at **4–6 weeks** post-deploy (30d recrawl gate + 1–2d refresh), not next-day. Automated next-day "did the title change in SERPs?" checks will false-alarm.
2. **Change-verification gates** in CI/CD for meta changes should assert *on-page* correctness at deploy, and defer *SERP-reflection* assertions to a 30+ day telemetry window (instrumentation: `../../kirby-seo-telemetry/SKILL.md` Module 12).
3. **Hot-path exemption:** pages linked from frequently crawled surfaces (homepage, hub donors) refresh faster than the ~30d default. If a business-critical snippet must land quickly, apply the sanctioned compression levers (internal-link re-pointing, GSC URL Inspection within quota) defined in `../../kirby-seo-timing-benchmarks/SKILL.md` Reference 05 — never bulk resubmission.
4. **Slow-tail classification:** a title change not reflected after ~60 days past deploy, with healthy crawl capacity, is a crawl-deprioritization or quality signal — route to the triage protocol (`../../kirby-seo-timing-benchmarks/SKILL.md` Reference 03 §3.4), not to more deploys.

## 20.4 GBP Domain Cutover & 14-Day Staggered Rebrand Cadence

*Source: Whitespark ("What Google Won't Tell You About Rebranding Your Business Profile" — Darren Shaw) & Caleb Ulku ("Google Business Address Change DENIED?"). Full GBP rebranding & verification rules live in `../../kirby-local-seo/SKILL.md` Module 9 & Module 12 — this section governs the deployment cutover timing gate.*

When a domain migration or rebrand involves an attached **Google Business Profile (GBP)**, flipping the GBP website URL or business name on launch day triggers Google's automated anti-hijacking suspension filter because Googlebot has not yet indexed the new web footprint.

**Deployment cutover sequence:**
1. **T-0 (Website & Tier-1 Cutover):** Deploy the new domain/301 map with updated visible NAP and `LocalBusiness` JSON-LD schema (`name`, `url`, `telephone`, `address`), and synchronize Tier-1 external anchors (Facebook Business Page, Yelp, BBB/Yell, Data Axle, Localeze). **Do NOT touch the GBP dashboard at T-0.**
2. **T+0 to T+14 Days (The Mandatory 14-Day Indexing Buffer):** Enforce a strict 14-day waiting gate after T-0 so Googlebot crawls and indexes the updated website schema and third-party directory citations before GBP verification bots run their cross-check.
3. **T+14 Days (Staggered GBP Field Cutover — 1 Field Per Week):** Logged in strictly as the GBP **Primary Owner** (never Manager), apply changes at 7-day intervals:
   - *Day 14*: Update GBP **Website URL** to the new canonical domain.
   - *Day 21*: Update GBP **Business Name** (if rebranding).
   - *Day 28*: Update **Primary Category** or **Phone Number** (if applicable).
4. **Address Cutover Pre-Check:** Never combine an address change with a domain/name flip. Before any address cutover, audit the target coordinate on Google Maps for prior-tenant ghost listings (`../../kirby-local-seo/SKILL.md` Module 12 §12.2).

## 20.5 Deployment Checklist Addendum (staple to any migration release)

```text
[ ] Pre-cutover: internal links audited (zero references to deprecated URLs)
[ ] Pre-cutover: sitemap inventory canonical-only; lastmod truthful
[ ] Pre-cutover: 301 map 1:1, no chains; 410 chosen for dead URLs where applicable (§7.7)
[ ] Cutover (T-0): single-event flip; sitemaps regenerated + submitted; JSON-LD schema updated
[ ] GBP Gate (T+14d): 14-day indexing buffer elapsed before touching GBP dashboard
[ ] GBP Stagger (T+14d/21d/28d): 1 sensitive field per week via Primary Owner account
[ ] Post: consolidation window declared (90-day freeze; checkpoints 30/60/90)
[ ] Post: canonical convergence monitored (expect 1–3 weeks; alarm at 8)
[ ] Post: title/snippet verification deferred to 30+ day telemetry window
[ ] Escalation: month-6 re-audit armed if baseline not recovered
```
