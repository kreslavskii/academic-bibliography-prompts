# Quality Criteria and Validation Checklist

## 1. TRAINING DATA — Inclusion and Exclusion

### Inclusion Criteria (ALL conditions must be met)

**✓ Include from training data ONLY if:**

1. **Canonical/seminal work:**
   - Citation threshold: **>500 citations** in scholarly literature (Google Scholar, Web of Science, Scopus)
   - **OR** broadly recognized canonical status (works by foundational theorists: Heidegger, Foucault, Derrida, McLuhan, Latour, Stiegler, Лотман, Гаспаров, etc.)
   - Rationale: Ensures only widely-recognized, influential works included without full-text verification

2. **Model has substantial content knowledge:**
   - **MUST provide 3-6 sentence summary with SPECIFIC concepts, arguments, theoretical frameworks**
   - NOT vague descriptions: "important work", "influential book"
   - MUST include concrete concepts: "Develops Gestell as mode of revealing", "Introduces épiphylogenèse as tertiary retention"
   - **This is the KEY measurable criterion**

3. **Pre-2020 publication:**
   - Published before 2020 (more reliable in LLM training corpus)
   - Prefer pre-2015 for highest confidence

4. **No sufficient OA alternative:**
   - If full-text OA version exists → use Tier 1 instead
   - If only partial OA (excerpts, chapters) → may use Tier 2 with links to OA alternatives

### Exclusion Criteria (ANY condition excludes)

**✗ Exclude if:**
- Only superficial or second-hand knowledge
- Cannot provide specific concepts/frameworks from work
- Published after 2021 (unreliable; likely not in corpus or incomplete)
- Recent empirical study (data may be outdated in training corpus; use Tier 1 OA for current data)
- Obscure work without clear scholarly impact

### Labeling Requirements

For each Training Data source:
```
- LINKS: unavailable

- Source: Training data corpus
- For OA analysis see: [SPECIFIC alternatives: Author (Year) "Title" DOI/URL]
```

**Quality Standards:**
- Provide 3-6 sentences with specific concepts/frameworks (not vague descriptions)
- Explain relevance to user's text (not just "famous work")
- Acknowledge verification limitation
- Suggest specific OA alternatives (never generic phrases like "extensive literature available")

**Never:**
- ✗ Invent direct quotes or claim page access without certainty
- ✗ Include works with only vague knowledge
- ✗ Use training data for recent empirical studies
- ✗ Mix training-data with OA-verified content without clear tier marking

---

## 2. CITATION COUNT CRITERIA BY TIER

**CRITICAL CLARIFICATION:**

| Tier | Citation Count Requirement | Rationale |
|---|---|---|
| **Tier 1 (OA)** | ❌ NOT required | Direct full-text verification; relevance + quality primary factors |
| **Tier 2 (Training)** | ✅ **>500 cites OR canonical status REQUIRED** | Proxy for canonical status and training corpus reliability |
| **Tier 3 (Paywalled)** | ❌ NOT required | Relevance (metadata) + quality (peer-review) primary factors |

**Why >500 for Training Data only:**
- Training Data: Model relies on memorized knowledge without direct access → restrict to canonical works (>500 cites) where model likely has substantial, accurate knowledge
- OA: Model accesses full text directly → can verify relevance and content → no need for citation threshold
- Paywalled: Metadata-only; relevance to user's specific text more important than citation count

---

## 3. MANDATORY ATTRIBUTES BY SOURCE TYPE

### Books:
- Author(s) (≤3, or first 3 + et al.)
- Full title
- Publisher
- Year
- **ISBN (MANDATORY)** — search and provide; "Not available" acceptable only for pre-1970 editions

### Articles:
- Author(s)
- Full article title
- Journal name
- Volume(Issue)
- Year
- **Pages (pp. XX-YY) — MANDATORY**
- **DOI (MANDATORY)** — search and provide

### Book chapters:
- Chapter author(s)
- Chapter title
- In: Book title (editor if applicable)
- Publisher
- Year
- Pages (pp. XX-YY)
- **ISBN (MANDATORY)**

### News/Web sources:
- Outlet name
- Article title
- Date (Day Month, Year)
- **URL (MANDATORY)**
- [Accessed: Month Day, Year] — recommended

### Translations:
- In square brackets after original
- Include: translator (if known), city, publisher, year, ISBN
- Example: `[Рус. пер.: Автор. Название. М.: Издательство, Год. ISBN: XXX.]`

---

## 4. CITATION LOCATIONS ("Места размещения")

### Requirements:
- **SHORT:** 5-15 words maximum
- **CLEAR:** completely obvious WHERE to insert [N]
- **NOT full sentence,** only sufficient fragment for localization
- **For multiple relevance:** list as N.1, N.2, N.3
- **For large texts:** add context (section/chapter number) if phrase may repeat

### Examples:
- ✅ Correct: "Хайдеггер рассматривает технику как способ раскрытия [2]"
- ✅ Correct: "исследований Онга о том, как письменность перестраивает [3]"
- ✅ Correct: "(Раздел 3) классификации структурируют знание [6]"
- ❌ Incorrect: long paragraph without clear indication of where to insert citation

---

## 5. SUM (Short Description)

### Requirements:
- **Length:** 2-3 sentences (maximum 4 for complex works)
- **Content:**
  - (a) WHAT the source covers
  - (b) HOW it supports user's argument
- **Language:** source's original language (Russian sources in Russian, English in English)
- **DO NOT** use untranslated English terms in Russian text if standard translation exists
- **Avoid** overly general phrases: prefer specific concepts/arguments

### Examples:
- ✅ Correct: "Develops concept of antifragility — systems that gain from volatility and stressors. Shows how removing redundancy for efficiency creates fragility: optimized systems win under normal conditions but catastrophically fail under stress."
- ❌ Incorrect: "Taleb opposes fragile, robust, and antifragile." (English terms in potential Russian context without translation)
- ❌ Incorrect: "Important work about risks and uncertainty." (too general, no specifics)

---

## 6. LINKS & Link Hygiene

### Requirements:
- **OA:** direct link to full text (PDF/HTML), not to abstract
- **Paywalled:** write "unavailable"
- **News/Web:** URL MANDATORY
- **Do NOT link** to paywalled publishers or book retailers

### Link Hygiene (normalization):
- **DOI:** format https://doi.org/XXXX (no parameters)
- **Remove** tracking parameters (utm_*, ref=, source=) from URLs
- **Prefer** stable OA repositories (institutional/journal)
- **Test** link functionality before including
- **Backup:** Add Wayback Machine/Perma.cc link if original URL unstable (mark [Archived])

### Examples:
- ✅ Correct: "https://monoskop.org/images/d/db/Ong_Walter_J_Orality_and_Literacy_2nd_ed.pdf"
- ✅ Correct: "https://doi.org/10.1287/isre.7.1.111"
- ✅ Correct: "unavailable"
- ❌ Incorrect: "https://example.com/article?utm_source=twitter" (tracking parameters present)

---

## 7. PROHIBITIONS

### 7.1. NEVER use generic phrases:

❌ "Multiple OA sources available on topic X"
❌ "Literature on subject Y"
❌ "Various sources discuss this concept"
❌ "Extensive secondary literature available"

**Always:** specific author, title, year, ISBN/DOI, link

### 7.2. NEVER skip:

❌ ISBN for books (search mandatory; "Not available" only for old books <1970)
❌ DOI for articles (search mandatory)
❌ URL for news/web (mandatory)
❌ Page range for articles (pp. XX-YY)

### 7.3. NEVER make citation locations too long:

❌ Full paragraphs or multiple sentences
❌ More than 15 words
✅ Short phrase clearly indicating placement

### 7.4. NEVER include redundant fields:

❌ Access: field (duplicates LINKS)
❌ METADATA: block (Type, Peer-reviewed, Language — not needed in final output)
❌ EVIDENCE FOR MAPPING: (internal verification)
❌ Detailed NOTES with duplication

### 7.5. NEVER use untranslated terms unnecessarily:

❌ "robustness", "fragile" in Russian text (if translation exists)
✅ "устойчивость", "хрупкие"

**Exceptions:** terms without direct translation or when original important (Gestell, pharmakon)

---

## 8. METADATA VALIDATION

**Before including any source:**

### DOI validation:
- Query Crossref API to verify DOI existence
- Retrieve/confirm metadata (title, authors, year, journal)
- If metadata conflicts: use API-validated version

### ISBN validation:
- Query OpenLibrary/WorldCat API to verify ISBN
- Retrieve/confirm metadata (title, authors, publisher, year)
- If validation fails: mark "Not available" only after exhaustive search

### Deduplication:
- **Primary key:** DOI (if available) > PMID (if available) > Title+Year+FirstAuthor (normalized, case-insensitive)
- **Action:** Merge duplicates by retaining entry with most complete metadata; combine all citation locations ("Also maps to:")

---

## 9. VERIFICATION BY TIER

### Tier 1 (OA-verified):
- [ ] Full text accessed via live link and inspected directly
- [ ] Relevance confirmed from actual content (not just abstract or title)
- [ ] Working OA link tested
- [ ] Link hygiene applied (no tracking parameters, DOI normalized)

### Tier 2 (Training data):
- [ ] Work is canonical/seminal (>500 citations OR foundational theorist)
- [ ] Model has substantial content knowledge (3-6 sentences with specific concepts/frameworks, not vague)
- [ ] Relevance confirmed via specific concepts/frameworks (not just "famous work")
- [ ] Marked clearly: "Source: Training data corpus"
- [ ] No direct quotes claimed without certainty; conceptual paraphrases only
- [ ] Specific OA alternatives suggested (with Author, Year, Title, DOI/URL)
- [ ] Pre-2020 publication (post-2021 excluded)
- [ ] NOT a recent empirical study (data unreliable in training)

### Tier 3 (Paywalled):
- [ ] Marked: "unavailable" in LINKS
- [ ] Based on abstract/preview/secondary sources only
- [ ] OA alternatives suggested if available
- [ ] Relevance assessed from metadata (abstract, title, keywords)
- [ ] Quality verified (peer-reviewed journal/publisher)

---

## 10. COVERAGE AND BALANCE

### Quantity:
- **Minimum:** 2 sources per theme (if OA available; otherwise note gap: "Не найдено достаточных OA-источников для [тема]")
- **Standard:** 2-4 sources per theme
- **Maximum:** 6 sources (unless user explicitly requests more)
- **Priority:** Quality > quantity (2-4 highly relevant sources better than 6 tangential ones)

### Overall coverage:
- **Density target:** 2-5 sources per 1,000 characters of input text (flexible guideline, not rigid rule)
- **Balance requirement:** Ensure ALL major themes, named authors, core claims have representation
- **Deduplication:** Each work listed once at most relevant location; use "Also maps to:" for multi-location relevance

---

## 11. ANTI-HALLUCINATION & TRANSPARENCY

### Core principles:
- **Never invent** DOI/pages/quotes/URLs/ISBNs
- **If data missing:** state explicitly "Not available" / "No suitable sources found for [topic]"
- **Strictly avoid** generic phrases ("literature available", etc.)
- **Metadata conflicts:** defer to API-validated version (Crossref for DOI, OpenLibrary for ISBN)

### For Training Data specifically:
- **No direct quotes** unless absolutely certain of accuracy
- **Provide specific OA alternatives:** never "extensive literature", always cite ACTUAL works with full citations
- **Acknowledge limitation:** "Source: Training data corpus" = model's memorized knowledge, not direct access

---

## 12. QUALITY CHECKLIST (FINAL CHECK BEFORE OUTPUT)

### OA sources:
- [ ] Full text accessible via live link and inspected
- [ ] Relevance confirmed from content (not just abstract)
- [ ] Working OA link tested
- [ ] Link hygiene applied

### Training data sources:
- [ ] Canonical work (>500 cites OR foundational theorist)
- [ ] 3-6 sentences with SPECIFIC concepts/frameworks (not vague)
- [ ] Marked "Source: Training data corpus"
- [ ] SPECIFIC OA alternatives (not generic "literature available")
- [ ] NOT recent empirical study

### Paywalled sources:
- [ ] Marked "unavailable" in LINKS
- [ ] Based on abstract/preview/secondary sources
- [ ] OA alternatives suggested (if available)

### All sources:
- [ ] Complete metadata: authors, title, publisher, year
- [ ] ISBN for books / DOI for articles present (or "Not available" with justification)
- [ ] Citation locations SHORT (5-15 words) and CLEAR
- [ ] SUM 2-3 sentences, concrete (not vague phrases)
- [ ] URLs cleaned (no utm_* parameters)
- [ ] Page range for articles (pp. XX-YY)
- [ ] For web sources: access date recommended
- [ ] SUM language matches source language
- [ ] ALL major themes/authors/claims from text covered
- [ ] No duplicates (merged by DOI/PMID/Title+Year+FirstAuthor)

---

## 13. WORKING PRINCIPLES

### DO NOT BE LAZY:
- Search for **SPECIFIC** sources, not placeholders
- Find ISBN/DOI for **EVERY** source
- Check OA availability
- For Training Data: actively search for OA alternatives
- Test link functionality

### IF CANNOT FIND:
- Explicitly state: "No suitable sources found for [topic]"
- **DO NOT** output generic phrases like "Literature on topic exists"

### QUALITY > SPEED:
- Better to spend time finding a specific source
- Than to output a placeholder useless to the user
- 2-4 high-quality relevant sources better than 8 mediocre ones

---

**These criteria ensure high-quality bibliographies with reproducible results and zero tolerance for generic placeholders.**

