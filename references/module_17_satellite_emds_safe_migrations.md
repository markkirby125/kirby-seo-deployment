# Module 17: Satellite EMDs & Safe Migrations

*Source: Mike King (iPullRank) & Edward Sturm / The Edward Show, Episode 1127*

For Generative Engine Optimization, launch third-party Exact Match Domain (EMD) satellite sites. This widens your AI citation footprint and firewalls experiments from your main domain.

### **17.1 The EMD Firewall**
* **The Strategy:** Deploy test campaigns and new semantic architecture on isolated EMDs. 
* **The Benefit:** This confines algorithmic penalties or "Scaled Content Abuse" filters to the satellite, completely protecting the primary money domain from catastrophic traffic loss during aggressive testing.
* **EMD Trust Signals (Semantic Bridges):** For satellite EMDs intended to survive and merge (not throwaway penalty-test nodes), make the satellite look like a real company. Replicate the main brand's trust signals across the EMD: use the same logo placement, identical footers, and privacy statements. **Note the tradeoff:** linking out to the same primary social media accounts (or specific branded X/YouTube accounts) establishes a semantic bridge that validates the EMD, but it creates a discoverable footprint that pierces the network isolation firewall. Only apply this shared-social mirror to trusted bridge sites; do not apply it to high-risk experimental nodes where total administrative isolation is required.
* **Entity Expansion:** If successful, these third-party domains act as independent nodes that can cite the main entity, increasing generative visibility.

### **17.2 The 10-Page Indexation Rule**
* **Launch Cap:** Launch the satellite with a maximum of 10 dense, bottom-of-funnel pages.
* **The Indexation Gate:** Never outpace indexation. Wait until the initial batch reaches ~90% indexation (verified via Google Search Console) before adding new URLs. 
* *Note: For rules regarding "Launch in Finished Form", "No Velocity Spikes", and "Entity Set Isolation", refer directly to `kirby-seo-deployment` Module 7.*

### **17.3 Safe Migrations & 1:1 Redirects**
* When migrating a successful satellite to merge with a main domain, never mass-redirect to the homepage. 
* Maintain a strict 1:1 redirect map, preserving the exact URL path structure to ensure semantic relevance transfers seamlessly.
* **Persistent source-domain holding:** After the 1:1 map is live, keep the source EMD registered, hosted, and serving those 301s. Do not drop the registration, expire DNS, or collapse the source to a parked page.
* *Note: Refer to `kirby-seo-deployment` Module 7 for detailed URL Preservation and 301 execution rules.*

### **17.4 PARKED — Satellite Hub Directory Architecture (Do Not Implement)**

* **Status:** Parked at its provenance gate (October 2026). The proposed doctrine — topic-focused satellite *directory* sites with continuously refreshed publish dates to secure high-frequency ChatGPT/Bing citations — has **no verifiable primary source** (adjacent concepts exist: the third-party EMD firewall above (§17.1), generic freshness tactics; the specific claim does not).
* **Sanctioned alternative:** the third-party EMD satellite architecture above (§17.1 EMD Firewall, §17.2 10-page rule, Module 7 network isolation) is the vetted satellite doctrine.
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

