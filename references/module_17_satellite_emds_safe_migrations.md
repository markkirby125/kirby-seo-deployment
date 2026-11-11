# Module 17: Satellite EMDs & Safe Migrations

*Source: Mike King (iPullRank) & Edward Sturm / The Edward Show, Episode 1127*

For Generative Engine Optimization, this module documents an older approach of launching third-party Exact Match Domain (EMD) satellite sites. The approach is legacy-risk (see the §17.1 notice). It is claimed to widen your AI citation footprint and to firewall experiments from your main domain; both claims are unverified.

### **17.1 The EMD Firewall**
* **Legacy-Risk Notice:** This section and the satellite launch rules in §17.2 document an older satellite and "firewall" approach. Treat it as legacy-risk. Satellites that exist to carry experiments or support a main domain can form a network, and forensic classifiers reportedly target topology, hosting, burst velocity and repeated DOM (directional, single source, unverified; see Module 7 §7.3). Evasion is not a defence, and the isolation described below is not guaranteed to protect the main domain. Prefer staged, human-reviewed launches (Module 7 §7.1 and §7.4) and satellites that are genuine, disclosed brands or properties you are prepared to stand behind.
* **The Strategy (historical, legacy-risk):** Deploy test campaigns and new semantic architecture on isolated EMDs. 
* **The Benefit (claimed, unverified):** This is claimed to confine algorithmic penalties or "Scaled Content Abuse" filters to the satellite, protecting the primary money domain from traffic loss during aggressive testing. No guarantee: see the Legacy-Risk Notice above.
* **EMD Trust Signals (Semantic Bridges):** Throwaway penalty-test nodes are legacy-risk and should not be launched. For satellite EMDs intended to survive and merge, operate the satellite as a genuine, disclosed brand or property that is truthfully presented as yours, rather than dressing it up to look like an independent company. Consistent brand trust signals (logo placement, footers, privacy statements) are claimed to support the EMD (unverified), and distinct hosting, styling and markup should reflect genuinely distinct properties (Module 7 §7.3). **Note the tradeoff:** linking out to the same primary social media accounts (or specific branded X/YouTube accounts) is claimed (unverified) to establish a semantic bridge that validates the EMD, but it creates a discoverable footprint that pierces the claimed isolation. Do not use a shared-social mirror to link satellites you would not disclose as yours, and do not launch high-risk experimental nodes in the first place (see the Legacy-Risk Notice above).
* **Entity Expansion (claimed, unverified):** If successful, these third-party domains are claimed to act as independent nodes that can cite the main entity, increasing generative visibility. Cross-property citation between sites you operate is also the interlinking pattern that Module 7 §7.3 warns against, so use it with care.

### **17.2 The 10-Page Indexation Rule**
* **Launch Cap (legacy-risk, see the §17.1 notice):** Launch the satellite with a maximum of 10 dense, bottom-of-funnel pages.
* **The Indexation Gate:** Never outpace indexation. Wait until the initial batch reaches ~90% indexation (verified via Google Search Console) before adding new URLs. 
* *Note: For rules regarding "Launch in Finished Form", "No Velocity Spikes", and "Entity Set Isolation" (now the §7.3 bullets on standalone assets and genuinely distinct entity profiles), refer directly to `kirby-seo-deployment` Module 7.*

### **17.3 Safe Migrations & 1:1 Redirects**
* When migrating a successful satellite to merge with a main domain, never mass-redirect to the homepage. 
* Maintain a strict 1:1 redirect map, preserving the exact URL path structure to ensure semantic relevance transfers seamlessly.
* **Persistent source-domain holding:** After the 1:1 map is live, keep the source EMD registered, hosted, and serving those 301s. Do not drop the registration, expire DNS, or collapse the source to a parked page.
* *Note: Refer to `kirby-seo-deployment` Module 7 for detailed URL Preservation and 301 execution rules.*

### **17.4 PARKED — Satellite Hub Directory Architecture (Do Not Implement)**

* **Status:** Parked at its provenance gate (October 2026). The proposed doctrine — topic-focused satellite *directory* sites with continuously refreshed publish dates to secure high-frequency ChatGPT/Bing citations — has **no verifiable primary source** (adjacent concepts exist: the third-party EMD firewall above (§17.1), generic freshness tactics; the specific claim does not).
* **Previously documented alternative (legacy-risk):** the third-party EMD satellite architecture above (§17.1 EMD Firewall, §17.2 10-page rule) was the earlier satellite doctrine (see also the Module 7 §7.3 warning against building a network) and carries the legacy-risk notice in §17.1; it is not a recommendation.
* **If ever revived:** the originator must first produce a primary source; any implementation must then ship with disclosure/nofollow requirements and hard footprint limits — the pattern is PBN-adjacent and carries Google link-spam detection risk either way.

---

### **17.5 Satellite Review Domain Prohibition & FTC Disclosure Mandate (Ep. 1206)**

*Source: The Edward Show, Episode 1,206 (David Quaid, Gagan Ghotra & Edward Sturm)*

* **The Satellite Review Domain Trap:** Spinning up disposable, unlinked review satellite domains (e.g., `[brand]reviews.com`) to host scraped or transcribed YouTube influencer reviews is strictly prohibited.
* **The Hazards:**
  1. **FTC Endorsement Rule Violations:** Hosting paid influencer review transcripts on external satellite domains without conspicuous, on-page sponsorship disclosures violates FTC regulations (16 CFR Part 465) on deceptive endorsements.
  2. **Google Scaled Content & Reputation Abuse:** Programmatic deployment of transcript review sites falls under Google's Scaled Content Abuse and Site Reputation Abuse penalties.
  3. **Zero Retrieval Weight:** LLMs and answer engines heavily prioritize high-authority domains; newly spun-up satellite review domains carry negligible retrieval probability in real-world LLM comparison queries.
* **The Sanctioned Architecture:**
  * Collect authorized creator and influencer video reviews and publish verified transcripts directly on the **primary domain** under `/reviews/` (e.g., `brand.com/reviews/[creator]-review`).
  * Ensure explicit, visible sponsorship disclosures: *"This review features a paid product partnership with [Creator]."*
  * Mark up transcripts with `VideoObject` and `Review` schema on the primary domain to concentrate entity corroboration where it compounds authority.

