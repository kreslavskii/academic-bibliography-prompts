# Bibliography Output Requirements

## 0. GENERAL PRINCIPLES

Output format adapted for interdisciplinary academic publications, combining elements of:
- **Chicago Manual of Style** (humanities)
- **APA Style** (social sciences)
- **Russian VAK requirements**

Priority: **metadata accuracy + source reproducibility + user convenience**.

---

## 1. GENERAL ENTRY STRUCTURE

Each entry in the bibliography follows this uniform format:

```
[N] Author(s). Title. Publisher, Year. ISBN (for books) / DOI (for articles).
[Translation if applicable: Автор. Название. Город: Издательство, Год. ISBN.]

- Места размещения в тексте:
N.1. [Short phrase from user's text indicating where to insert [N]]
N.2. [Another location if source relevant to multiple places]

- SUM: Brief description (2-3 sentences) explaining how the source supports the text's argument and what the work focuses on.

- LINKS: [Direct link to full text] OR "unavailable" (if paywalled/no online access)

[ONLY if source is from training data AND no OA link:]
- Source: Training data corpus
- For OA analysis see: [Specific alternative sources with full bibliographic data and DOI/URL]

---
```

---

## 2. MANDATORY ELEMENTS

### 2.1. Bibliographic Description

**For books:**
- Author(s) (≤3, or first 3 + et al.)
- Full title
- Publisher
- Year
- **ISBN (MANDATORY)**

**For articles:**
- Author(s)
- Full article title
- Journal name
- Volume(Issue)
- Year
- Pages (range: pp. 123-145)
- **DOI (MANDATORY)**

**For book chapters:**
- Chapter author(s)
- Chapter title
- Book title (with editor if applicable)
- Publisher
- Year
- Chapter pages (pp. XX-YY)
- **ISBN (MANDATORY)**

**For news/web sources:**
- Outlet name
- Article title
- Publication date (format: Day Month, Year)
- **URL (MANDATORY)**
- Access date (format: Accessed: Month Day, Year) — recommended

**For translations:**
- Indicated in square brackets after original
- Include full details: translator (if known), city, publisher, year, ISBN

### 2.2. Citation Locations ("Места размещения в тексте")

**REQUIREMENTS:**
- Short phrase (5-15 words maximum)
- Must be completely CLEAR where to insert citation [N]
- NOT full sentence, just enough fragment for unambiguous localization
- If source relevant to multiple places — list as N.1, N.2, N.3, etc.
- For large texts: add context (section/chapter number) when phrase might repeat

**EXAMPLES:**
- ✅ Correct: "Хайдеггер рассматривает технику как способ раскрытия [2]"
- ✅ Correct: "исследований Онга о том, как письменность перестраивает [3]"
- ✅ Correct: "(Раздел 3) классификации структурируют знание [6]"
- ❌ Incorrect: long sentence spanning multiple lines without clear indication of where to insert footnote

### 2.3. SUM (Short Description)

**REQUIREMENTS:**
- 2-3 sentences (maximum 4 for complex works)
- Explain: (a) WHAT the source is about, (b) HOW it supports user's argument
- Summary language: source's original language (Russian sources in Russian, English in English)
- DO NOT use untranslated English terms in Russian text if standard translation exists
- Avoid overly general phrases: prefer concrete concepts/arguments

**EXAMPLES:**
- ✅ Correct: "Развивает концепцию антихрупкости — систем, извлекающих выгоду из волатильности и стрессоров. Показывает, как удаление избыточности ради эффективности создаёт хрупкость: оптимизированные системы выигрывают в нормальных условиях, но катастрофически проигрывают при стрессе."
- ❌ Incorrect: "Талеб противопоставляет fragile, robust и antifragile." (English terms in Russian text without necessity)
- ❌ Incorrect: "Важная работа о рисках и неопределённости в современном мире." (too general, no specifics)

### 2.4. LINKS

**REQUIREMENTS:**
- If source available in open access: provide direct link to full text
- If source paywalled/unavailable online: write "unavailable"
- For news and web sources: link MANDATORY
- Do not provide links to paywalled publishers or book retailers

**Link Normalization (Link Hygiene):**
- DOI format: https://doi.org/XXXX (no spaces or parameters)
- Remove tracking parameters from URLs (e.g., ?utm_*, ?ref=, ?source=)
- Prefer stable OA repositories (institutional/journal) over random mirrors
- Test link functionality before including

**EXAMPLES:**
- ✅ Correct: "https://monoskop.org/images/d/db/Ong_Walter_J_Orality_and_Literacy_2nd_ed.pdf"
- ✅ Correct: "https://doi.org/10.1287/isre.7.1.111"
- ✅ Correct: "https://archive.org/details/domesticationofs0000good"
- ✅ Correct: "unavailable"
- ❌ Incorrect: "https://example.com/article?utm_source=twitter&utm_campaign=share" (contains tracking parameters)

### 2.5. Source: Training data corpus (ONLY for sources from training data)

**WHEN TO USE:**
- Source taken from model's training data (canonical works >500 citations, pre-2020)
- AND no available OA link to full text
- Model has detailed knowledge of work's content (can provide 3-6 sentences with specific concepts/frameworks)

**MUST include:**
- Line "Source: Training data corpus"
- Line "For OA analysis see:" with SPECIFIC alternative sources

**REQUIREMENTS for OA alternatives:**
- Specify SPECIFIC sources: Author, Year, Title, DOI or URL
- DO NOT use generic phrases like "extensive literature available", "secondary sources discuss", "multiple OA articles"
- Minimum 1-2 specific sources with complete data
- Alternatives should allow verification of key concepts from original work

**EXAMPLES:**
- ✅ Correct:
  ```
  - Source: Training data corpus
  - For OA analysis see: Mitcham, C. (1994) Thinking Through Technology: The Path Between Engineering and Philosophy. University of Chicago Press, chapter on Heidegger (excerpts at https://philpapers.org/rec/MITATT); Feenberg, A. (2005) "Heidegger and Marcuse: The Catastrophe and Redemption of History" DOI:10.1177/0270467604271196
  ```

- ❌ Incorrect:
  ```
  - Source: Training data corpus
  - For OA analysis see: Extensive secondary literature available; multiple OA philosophy journals discuss this.
  ```

### 2.6. Special Cases (Edge Cases)

**Preprints without final DOI:**
- Specify identifier: arXiv ID (arXiv:2101.12345) / bioRxiv DOI / SSRN ID
- Mark: [Preprint] after article title
- Example: `Smith, J. "Title of Paper" [Preprint]. arXiv:2101.12345, 2021.`

**Multi-volume works:**
- Format: Author. Title. Volume N: Volume subtitle. Publisher, Year.
- ISBN for specific volume (not series ISBN)
- Example: `Stiegler, B. La technique et le temps. Tome 1: La faute d'Épiméthée. Galilée, 1994. ISBN: 978-2-7186-0425-5.`

**E-books with unstable pagination:**
- Specify: ISBN of electronic version / DOI of book (if available)
- For "citation locations": use chapter numbers instead of pages: "(Chapter 5) concept X [N]"
- Example location: "3.1. (Chapter 3) инфраструктура невидима [19]"

**Sources without ISBN/DOI:**
- For old books (before ISBN system introduction in 1970): acceptable to specify "ISBN: Not available"
- For web sources without DOI: URL + access date MANDATORY
- For dissertations: specify university and type (PhD/Master thesis)

**Archived/obsolete URLs:**
- If original URL unavailable, use Wayback Machine: `https://web.archive.org/web/YYYYMMDD/original-url`
- Mark: [Archived]

---

## 3. PROHIBITIONS

### 3.1. NEVER use generic phrases instead of specific sources:

❌ "Multiple OA sources available on topic X"
❌ "Literature on subject Y"
❌ "Various sources discuss this concept"

**Always specify:** Specific author, title, year, ISBN/DOI, link

### 3.2. NEVER skip:

❌ ISBN for books (must search and specify; "Not available" only for old books)
❌ DOI for articles (must search and specify)
❌ URL for news and web sources (mandatory)
❌ Page range for articles (pp. 123-145)

### 3.3. NEVER make citation locations too long:

❌ Do not use full paragraphs or multiple sentences
❌ Maximum 15 words
✅ Short phrase sufficient for unambiguous location

### 3.4. NEVER include redundant fields:

❌ Access: field (information duplicated in LINKS)
❌ METADATA: block (Type, Peer-reviewed, Language — not needed for user)
❌ EVIDENCE FOR MAPPING: (internal verification)

### 3.5. NEVER use untranslated terms unnecessarily:

❌ "robustness", "fragile", "antifragile" in Russian text (if standard translation exists)
✅ "устойчивость", "хрупкие", "антихрупкие"

Exceptions: established terms without direct translation or when original term important (e.g., "Gestell", "pharmakon")

---

## 4. SOURCE TYPES AND SPECIFIC REQUIREMENTS

### 4.1. Books

```
[N] Author, I. Book Title. City: Publisher, Year. ISBN: XXX-X-XXX-XXXXX-X.
[Translation: Автор И. Название. Город: Издательство, Год. ISBN: XXX.]

- Места размещения в тексте:
N.1. [short phrase]

- SUM: Description (2-3 sentences).

- LINKS: [URL if OA] OR "unavailable"

---
```

### 4.2. Journal Articles

```
[N] Author, I.; Author2, I. Article Title. Journal Name, Volume(Issue), Year, pp. 123-145. DOI: 10.XXXX/XXXX.

- Места размещения в тексте:
N.1. [short phrase]

- SUM: Description (2-3 sentences).

- LINKS: [URL if OA] OR "unavailable"

---
```

### 4.3. Book Chapters

```
[N] Author, I. Chapter Title. In: Editor, R. (Ed.). Book Title. City: Publisher, Year, pp. XX-YY. ISBN: XXX.

- Места размещения в тексте:
N.1. [short phrase]

- SUM: Description (2-3 sentences).

- LINKS: [URL if OA] OR "unavailable"

---
```

### 4.4. News and Web Sources

```
[N] Outlet Name. "Article Title." Publication Date. URL. [Accessed: Month Day, Year]

- Места размещения в тексте:
N.1. [short phrase]

- SUM: Description (2-3 sentences).

- LINKS: [URL — MANDATORY]

---
```

### 4.5. Training Data Sources

```
[N] Author, I. Title. Publisher, Year. ISBN: XXX.
[Translation if applicable]

- Места размещения в тексте:
N.1. [short phrase]

- SUM: Description (2-3 sentences).

- LINKS: unavailable

- Source: Training data corpus
- For OA analysis see: [SPECIFIC sources]: Author, I. (Year) "Title" DOI:...; Author2, I. (Year) "Title2" URL:...

---
```

---

## 5. QUALITY CONTROL

Before providing bibliography, check:

### 5.1. For each source:
- [ ] All mandatory fields specified (author, title, publisher, year)
- [ ] ISBN for books / DOI for articles present (or marked "Not available" with justification)
- [ ] Citation locations short (5-15 words) and unambiguous
- [ ] SUM clearly explains relevance (2-3 sentences, concrete concepts)
- [ ] LINKS contains direct link or "unavailable"
- [ ] URLs cleaned of tracking parameters
- [ ] For articles: page range specified (pp. XX-YY)
- [ ] For web sources: access date added (recommended)

### 5.2. For Training Data sources:
- [ ] Line "Source: Training data corpus" present
- [ ] Line "For OA analysis see:" with SPECIFIC sources present
- [ ] OA alternatives include authors, years, titles, DOI/URL
- [ ] NO generic phrases like "extensive literature"
- [ ] Work meets criteria: >500 citations OR canonical status, pre-2020, detailed content knowledge

### 5.3. Overall:
- [ ] NO generic phrases instead of specific sources
- [ ] NO redundant fields in output (Access, METADATA, EVIDENCE)
- [ ] All sources specific and verifiable
- [ ] Translations indicated in square brackets with full details
- [ ] All links tested for functionality (for OA)
- [ ] SUM language matches source language

---

## 6. WORKING PRINCIPLE

**DO NOT BE LAZY:**
- Search for specific sources, not placeholders
- Find ISBN/DOI for each source
- Check OA availability
- For Training Data: actively search for OA alternatives
- Test link functionality

**IF CANNOT FIND:**
- Explicitly state: "No suitable sources found for [topic]"
- DO NOT output generic phrases like "Literature on topic exists"

**QUALITY > SPEED:**
- Better to spend time finding a specific source
- Than to output a placeholder useless to the user
- 2-4 high-quality relevant sources better than 8 mediocre ones

---

**This format ensures practicality for the scholar: quick location of citation insertion point, ready bibliography for copy-paste, understanding of relevance, and direct access to sources.**

