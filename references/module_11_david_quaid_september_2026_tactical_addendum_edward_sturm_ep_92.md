# Module 11: David Quaid September 2026 Tactical Addendum (Edward Sturm Ep. 92)

*Source: The Edward Show, Episode 92 (Edward Sturm & David Quaid)*

### **11.1 The "Ad Rank" Formula for Organic Relevance vs. Authority**
Google's organic ranking mirrors the Google Ads Ad Rank equation (`Ad Rank = Quality Score × Dollar Bid`). 
In organic search: **`Rank = Topical Relevance × Domain Authority`**.
*   **Zero-Authority Sites:** When Domain Authority is near zero, the URL can only compete by setting Relevance to 100% (the URL slug and document name must precisely match the exact-match search query).
*   **High-Authority Sites:** Established sites have high domain scores ("high bids"), allowing them to rank with partial matches, broad guides, or nested headings.

### **11.2 The "57 Indexed Document Formats" Law (Against Schema Dependency)**
Schema markup is not an algorithmic ranking prerequisite. Google indexes **57 different file types** (e.g., plain text, PDF, binary, BAS, images). The vast majority of these formats lack `<title>` tags, meta descriptions, or JSON-LD schema support. 
*   Google’s core indexing primitive across all formats is the **document name (URL slug)** and raw body text. 
*   Schema only assists text scrapers in isolating questions from answers; it imparts zero authority or trust score.

### **11.3 Accordions vs. Standalone URLs: The Operational Split**
*   **Accordions:** Built for UI cleanliness and for **high-authority domains** aiming to capture extra SERP click-through rate (CTR) on pages that *already* rank. Low-authority domains nesting questions in an accordion will fail to rank because the URL lacks the authority to carry multiple sub-intents.
*   **Standalone URLs:** The mandatory, distinct mechanism for low-authority domains to rank for long-tail questions (ensuring 100% relevance per Section 11.1).

### **11.4 Multimodal PAA Extraction & Prompt Filtering**
Instead of paid tools, leverage LLM vision capabilities:
1.  **Visual Scraping:** Take a raw desktop screenshot of the Google SERP "People Also Ask" box and paste the image directly into Perplexity (or a multimodal LLM).
2.  **Code Snippet Output Prompt:** Prompt the LLM with: *"Using my topic as a base, write a 120-word answer for each question. Give the answer as plain text in a code snippet. Remove citations."* This bypasses markdown formatting and inline links, yielding raw text ready for instant CMS pasting.
3.  **Subfolder Taxonomy:** When scaling FAQs across multiple disparate product lines (e.g., whiskey vs. tequila), isolate each category into dedicated parent hubs (e.g., `/whiskey-faqs/`, `/tequila-faqs/`) rather than an unsegmented sitewide `/faq/`.

### **11.5 Personal Knowledge Panel Claiming & Verification Playbook**
Schema markup alone does not trigger a Knowledge Panel. Triggering requires a sustained influx of distinct IPs querying the branded name (`[Name] + [Keyword]`). Once triggered, execute the verification workflow:
1.  **Multi-Schema Hub Page:** Deploy a single personal hub page containing a combined schema bundle (`ProfilePage`, `Person`, `LocalBusiness`, and `WebPage`). Use this hub page as the authoritative cross-link target out to LinkedIn and X (Twitter).
2.  **Auto-Scraped Verification Email:** Ensure a primary email address is on the hub page; Google’s verification form will automatically scrape and pre-populate it.
3.  **Identity Proof:** Submit a selfie holding government photo ID.
4.  **Profile Auth:** Submit full screenshots of logged-in X (Twitter) and LinkedIn account management pages showing your face.
