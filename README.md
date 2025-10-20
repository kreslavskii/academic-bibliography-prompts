# Scholarly Research Assistant 
Academic bibliography production-grade prompt system for LLM-powered academic bibliography generation.  Three-tier verification (OA/Training/Paywalled), anti-hallucination measures,  4 deployment options. EN instructions, RU user communication

**Date:** October 20, 2025  
**Language:** Instructions in English; user communication in Russian

---

## Table of Contents

- [Overview](#overview)
- [Core Principles](#core-principles)
- [File Structure](#file-structure)
- [Choosing the Right Prompt](#choosing-the-right-prompt)
- [Usage Guidelines](#usage-guidelines)
- [Current Limitations](#current-limitations)
- [Planned Features](#planned-features)
- [Quality Assurance](#quality-assurance)
- [Token Budget](#token-budget)
- [Contributing](#contributing)

---

## Overview

This prompt system enables LLMs to generate high-quality bibliographies with:
- **Three-tier verification:** OA-verified, Training data corpus, Paywalled metadata
- **Citation threshold clarity:** >500 citations applies ONLY to Training Data (Tier 2)
- **Metadata requirements:** Complete bibliographic data (ISBN/DOI/URL)
- **Anti-hallucination measures:** No generic placeholders; specific sources only
- **Deduplication:** Merge by DOI/PMID/Title+Year+FirstAuthor keys
- **Language consistency:** Instructions in English; user communication in Russian

---

## Core Principles

### 1. Source Tiers

**Tier 1 (OA-verified):** Sources with live full-text links
- Verify by accessing and inspecting content
- **Citation count NOT required** (relevance + access + quality primary)

**Tier 2 (Training data corpus):** Canonical works from LLM training
- **>500 citations OR canonical status** (Heidegger, Foucault, Latour, Stiegler, etc.)
- **Pre-2020 publication** (more reliable in training corpus)
- **Model has substantial content knowledge** (3-6 sentences with specific concepts)
- **No sufficient OA available**
- Mark: "Source: Training data corpus" + SPECIFIC OA alternatives

**Tier 3 (Paywalled metadata):** Recent paywalled works (typically 2020-2025)
- Metadata only (based on abstract/preview)
- **Citation count NOT required** (relevance + quality primary)
- Mark: "unavailable" in LINKS

### 2. Citation Threshold Rule

**CRITICAL:** The >500 citations threshold applies **ONLY to Tier 2 (Training Data)**.

- **Tier 1 (OA):** Relevance and quality matter more than citation count
- **Tier 2 (Training):** >500 cites OR canonical status REQUIRED (proxy for training corpus reliability)
- **Tier 3 (Paywalled):** Relevance and quality matter more than citation count

Recent works (2020-2025) naturally have low citation counts — this is expected and acceptable for Tiers 1 and 3.

### 3. Anti-Hallucination Measures

- Never invent DOI/ISBN/URLs/quotes
- Never output generic phrases ("literature available", "multiple sources")
- SPECIFIC OA alternatives (cite ACTUAL works with full citations)
- Mark "Not available" only after exhaustive search

### 4. Language Consistency

**Instructions:** English only (all structural descriptions, commands, requirements)  
**User communication:** Russian only (dialogue, messages, progress updates)  
**Source summaries (SUM):** Original language of the source

---

## File Structure

### Main Prompts (with auxiliary file support)

| File | Length | Dependencies | Use Case |
|---|---|---|---|
| `main.md` | ~12,000 chars | `criteria.md`, `requirements.md`, `examples.md`, `databases.md` | Standard production use with comprehensive guidance |
| `main_short.md` | ~4,400 chars | `criteria.md`, `requirements.md`, `examples.md`, `databases.md` | Token-constrained environments; quick deployment |

### Standalone Prompts (no auxiliary files required)

| File | Length | Dependencies | Use Case |
|---|---|---|---|
| `standalone_full.md` | ~25,000 chars | None | Single-file deployment; no external file loading |
| `standalone_compact.md` | ~6,200 chars | None | Highly token-constrained environments; single-file deployment |

### Auxiliary Files

| File | Length | Purpose |
|---|---|---|
| `criteria.md` | ~6,600 chars | Quality criteria and validation checklist |
| `requirements.md` | ~6,400 chars | Complete output format specification |
| `examples.md` | ~6,700 chars | Annotated examples for all source types |
| `databases.md` | ~6,800 chars | Discipline-specific database recommendations |

### Analysis Documents (for reference)

- `ANALYSIS_v1_v2_comparison.md` — Detailed comparison of v1 vs v2
- `ANALYSIS_external_requirements.md` — Analysis of external requirements (PRISMA/systematic review standards)
- `ANALYSIS_criteria_revision.md` — Revision of citation criteria
- `ИТОГИ_РАБОТЫ.md` — Final report (Russian)

---

## Choosing the Right Prompt

### Use `main.md` if:
- ✅ You need comprehensive guidance with full workflow details
- ✅ You can load auxiliary files
- ✅ Token budget allows ~12K for main + ~15-20K for auxiliary files (~30K total)
- ✅ Standard production environment

### Use `main_short.md` if:
- ✅ You have token constraints but can still load auxiliary files
- ✅ You want faster loading times
- ✅ Token budget: ~4.4K for main + ~15K for auxiliary (~20K total)

### Use `standalone_full.md` if:
- ✅ You cannot load auxiliary files
- ✅ You need a single comprehensive file
- ✅ Generous token budget (~25K characters)
- ✅ Environment doesn't support multiple file loading

### Use `standalone_compact.md` if:
- ✅ Severe token constraints (~6.2K characters)
- ✅ Cannot load auxiliary files
- ✅ Need maximum information density in minimal space
- ✅ Quick testing or minimal deployment environment

---

## Usage Guidelines

### 1. Initial Setup

**For prompts with auxiliary files (`main.md`, `main_short.md`):**
1. Ensure all auxiliary files are accessible: `criteria.md`, `requirements.md`, `examples.md`, `databases.md`
2. Load main prompt first
3. Reference auxiliary files as needed during execution

**For standalone prompts (`standalone_full.md`, `standalone_compact.md`):**
1. Load the single prompt file
2. No additional files needed

### 2. Input Preparation

**Text size considerations:**
- **<50,000 characters (~40 pages):** Process as unified whole (20-40 sources)
- **>50,000 characters:** Model will request segmentation into 5-15K blocks

**User should provide:**
- The text to be bibliographed
- General theme/topic (for large texts: brief description per block)
- Any specific requirements (additional databases, focus areas, etc.)

### 3. Workflow

The model follows this process:

1. **Size analysis** — determine processing strategy
2. **Holistic analysis** — analyze ENTIRE text BEFORE searching (critical)
3. **Adaptive search** — select 2-3 databases per discipline identified
4. **Metadata validation** — verify completeness (currently manual; see [Current Limitations](#current-limitations))
5. **Citation location mapping** — mark WHERE to insert each citation (5-15 word phrases)
6. **Tier-based verification:**
   - Tier 1: Access and inspect full text
   - Tier 2: Verify canonical status + provide specific OA alternatives
   - Tier 3: Metadata only from abstract/preview
7. **Deduplication** — merge by DOI/PMID/Title+Year+FirstAuthor

### 4. Output Format

Each source follows this structure:

```
[N] Author(s). Title. Publisher, Year. ISBN/DOI.
[Translation if applicable: Автор. Название. Издательство, Год. ISBN.]

- Места размещения в тексте:
N.1. [SHORT phrase (5-15 words) where to insert [N]]

- SUM: 2-3 sentences (source's language): what source covers + how supports argument.

- LINKS: [Direct URL if OA] OR "unavailable"

[ONLY if Training data AND no OA:]
- Source: Training data corpus
- For OA analysis see: [SPECIFIC sources: Author (Year) "Title" DOI/URL]

---
```

### 5. Quality Verification

Before accepting output, verify:

- [ ] All tiers correctly marked (OA / Training data corpus / unavailable)
- [ ] Citation count rule applied correctly (>500 only for Tier 2)
- [ ] No generic phrases ("literature available", "multiple sources")
- [ ] All ISBN/DOI present or justified as "Not available"
- [ ] Citation locations SHORT (5-15 words) and CLEAR
- [ ] SUM in source's original language with concrete concepts
- [ ] URLs cleaned (no utm_*, DOI normalized)
- [ ] All major themes/authors/claims from user's text covered
- [ ] No duplicates

---

## Current Limitations

### 1. No JSON/CSV Output Mode

**Status:** ❌ Not implemented

**Current behavior:**
- Output format is human-readable text only
- Structured as markdown with consistent formatting
- Suitable for direct copy-paste into manuscripts

**Why this limitation exists:**
- Primary use case is direct scholar use (human-readable format preferred)
- Text format ensures readability and ease of editing
- Maintains focus on content quality over machine parsing

**Impact:**
- Cannot directly import into reference managers (Zotero, Mendeley, EndNote)
- Requires manual entry or conversion for database integration
- Not suitable for automated processing pipelines

### 2. No API-Based Metadata Validation

**Status:** ⚠️ Partially implemented (manual instructions only)

**Current behavior:**
- Model instructed to verify metadata, but no automated API calls
- DOI/ISBN validation relies on model's knowledge and manual search
- No programmatic confirmation via Crossref/OpenLibrary/WorldCat APIs

**Why this limitation exists:**
- LLMs typically cannot make direct API calls without external tooling
- Prompts provide instructions but cannot enforce API integration
- Implementation depends on deployment environment capabilities

**Impact:**
- Risk of incorrect or outdated metadata
- Cannot programmatically verify DOI/ISBN existence
- Deduplication relies on string matching, not canonical identifiers from registries
- No automatic retrieval of missing metadata fields

### 3. No Automated Deduplication via API

**Status:** ⚠️ Partially implemented (algorithmic only)

**Current behavior:**
- Deduplication by DOI > PMID > Title+Year+FirstAuthor (string matching)
- No API calls to retrieve canonical metadata for comparison
- Relies on model's ability to normalize titles and author names

**Impact:**
- May miss duplicates with slight title/author variations
- Cannot resolve conflicts by querying authoritative registries
- Manual review recommended for final deduplication

---

## Planned Features

### How to Add JSON/CSV Output Mode

**Option 1: Prompt Extension (Simplest)**

Add to main prompt (Section III: Output Format):

```markdown
### Optional: Machine-Readable Output

If user requests JSON output, provide:

{
  "sources": [
    {
      "id": 1,
      "type": "article|book|chapter|news",
      "authors": ["Last, First", "Last2, First2"],
      "title": "Full title",
      "publisher": "Publisher name" OR "journal_name",
      "year": 2020,
      "isbn": "978-X-XXX-XXXXX-X" OR null,
      "doi": "10.XXXX/XXXX" OR null,
      "url": "https://..." OR null,
      "pages": "123-145" OR null,
      "tier": "OA|Training|Paywalled",
      "citation_locations": [
        "Short phrase 1",
        "Short phrase 2"
      ],
      "summary": "2-3 sentences...",
      "source_note": "Training data corpus" OR null,
      "oa_alternatives": [
        "Author (Year) 'Title' DOI:..."
      ] OR []
    }
  ],
  "metadata": {
    "total_sources": 25,
    "oa_verified": 15,
    "training_data": 5,
    "paywalled": 5,
    "databases_used": ["PhilPapers", "arXiv", "Google Scholar"],
    "generation_date": "2025-10-20"
  }
}
```

**Option 2: Post-Processing Script**

Create a Python script to parse text output and convert to JSON:

```python
# parse_bibliography.py
import re
import json

def parse_text_output(text):
    entries = []
    # Parse [N] Author. Title. Publisher, Year. ISBN/DOI.
    # Parse - Места размещения: ...
    # Parse - SUM: ...
    # Parse - LINKS: ...
    # etc.
    return entries

def convert_to_json(entries):
    return json.dumps({"sources": entries}, indent=2)
```

**Option 3: External Tool Integration**

Use a dedicated bibliography parser:
- [anystyle](https://anystyle.io/) — ML-based citation parser
- [cermine](https://github.com/CeON/CERMINE) — content extractor for PDFs
- Custom regex-based parser for consistent format

**Recommendation:** Start with Option 1 (prompt extension) for quick implementation, then add Option 2 (script) for batch processing.

---

### How to Add API-Based Metadata Validation

**Requirements:**
1. LLM with function calling capability (OpenAI GPT-4, Claude with tools, etc.)
2. Access to metadata APIs:
   - Crossref API (DOI validation): https://api.crossref.org/works/{doi}
   - OpenLibrary API (ISBN): https://openlibrary.org/api/books?bibkeys=ISBN:{isbn}
   - WorldCat API (ISBN, alternative)
   - PubMed API (PMID): https://eutils.ncbi.nlm.nih.gov/entrez/eutils/

**Implementation Steps:**

#### Step 1: Define API Functions (for function-calling LLMs)

```json
{
  "name": "validate_doi",
  "description": "Validate DOI via Crossref API and retrieve metadata",
  "parameters": {
    "type": "object",
    "properties": {
      "doi": {"type": "string", "description": "DOI to validate (e.g., 10.1287/isre.7.1.111)"}
    },
    "required": ["doi"]
  }
}

{
  "name": "validate_isbn",
  "description": "Validate ISBN via OpenLibrary API and retrieve metadata",
  "parameters": {
    "type": "object",
    "properties": {
      "isbn": {"type": "string", "description": "ISBN to validate (e.g., 978-0-415-53838-1)"}
    },
    "required": ["isbn"]
  }
}

{
  "name": "deduplicate_sources",
  "description": "Check if two sources are duplicates using API-validated metadata",
  "parameters": {
    "type": "object",
    "properties": {
      "source1": {"type": "object", "description": "First source metadata"},
      "source2": {"type": "object", "description": "Second source metadata"}
    },
    "required": ["source1", "source2"]
  }
}
```

#### Step 2: Add Function Implementations (Python example)

```python
import requests

def validate_doi(doi):
    """Validate DOI via Crossref API"""
    url = f"https://api.crossref.org/works/{doi}"
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()['message']
        return {
            "valid": True,
            "title": data.get('title', [''])[0],
            "authors": [f"{a.get('family', '')}, {a.get('given', '')}" for a in data.get('author', [])],
            "year": data.get('published-print', {}).get('date-parts', [[None]])[0][0],
            "journal": data.get('container-title', [''])[0],
            "doi": doi
        }
    return {"valid": False, "error": "DOI not found"}

def validate_isbn(isbn):
    """Validate ISBN via OpenLibrary API"""
    isbn_clean = isbn.replace('-', '').replace(' ', '')
    url = f"https://openlibrary.org/api/books?bibkeys=ISBN:{isbn_clean}&format=json&jscmd=data"
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()
        if f"ISBN:{isbn_clean}" in data:
            book = data[f"ISBN:{isbn_clean}"]
            return {
                "valid": True,
                "title": book.get('title', ''),
                "authors": [a['name'] for a in book.get('authors', [])],
                "publishers": [p['name'] for p in book.get('publishers', [])],
                "year": book.get('publish_date', ''),
                "isbn": isbn
            }
    return {"valid": False, "error": "ISBN not found"}

def deduplicate_sources(source1, source2):
    """Check if two sources are duplicates"""
    # Priority: DOI > PMID > Title+Year+FirstAuthor
    if source1.get('doi') and source2.get('doi'):
        return source1['doi'] == source2['doi']
    
    if source1.get('pmid') and source2.get('pmid'):
        return source1['pmid'] == source2['pmid']
    
    # Normalize title and first author
    title1 = source1.get('title', '').lower().strip()
    title2 = source2.get('title', '').lower().strip()
    year1 = source1.get('year')
    year2 = source2.get('year')
    author1 = source1.get('authors', [''])[0].split(',')[0].lower() if source1.get('authors') else ''
    author2 = source2.get('authors', [''])[0].split(',')[0].lower() if source2.get('authors') else ''
    
    return (title1 == title2 and year1 == year2 and author1 == author2)
```

#### Step 3: Update Prompt (add to Step 3.5: Metadata Validation)

```markdown
### Step 3.5: Metadata Validation & Deduplication

**For all sources before inclusion:**

1. **DOI validation (if available):**
   - Call `validate_doi(doi)` function
   - If valid: use API-validated metadata (title, authors, year, journal)
   - If invalid: mark "DOI: Not available" and note validation failure
   - If metadata conflicts with found source: note discrepancy; prefer API version

2. **ISBN validation (if available):**
   - Call `validate_isbn(isbn)` function
   - If valid: use API-validated metadata (title, authors, publisher, year)
   - If invalid: mark "ISBN: Not available" and note validation failure
   - If metadata conflicts: note discrepancy; prefer API version

3. **Deduplication (before final output):**
   - For each pair of sources, call `deduplicate_sources(source1, source2)`
   - If duplicate detected: merge entries
     - Retain entry with most complete metadata
     - Combine citation locations ("Also maps to:")
   - Report merged entries to user (optional)

**Validation failure handling:**
- If API unavailable: proceed with manual validation; note limitation in output
- If API returns error: try alternative API (e.g., WorldCat for ISBN if OpenLibrary fails)
- If all APIs fail: mark "Not available" only after exhaustive attempts
```

#### Step 4: Integration with LLM Framework

**For OpenAI GPT-4 (function calling):**

```python
import openai

functions = [
    {
        "name": "validate_doi",
        "description": "Validate DOI via Crossref API",
        "parameters": {
            "type": "object",
            "properties": {
                "doi": {"type": "string"}
            },
            "required": ["doi"]
        }
    },
    # ... other functions
]

response = openai.ChatCompletion.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": open("main.md").read()},
        {"role": "user", "content": "User's text to bibliograph..."}
    ],
    functions=functions,
    function_call="auto"
)

# Handle function calls
if response.choices[0].message.get("function_call"):
    function_name = response.choices[0].message["function_call"]["name"]
    function_args = json.loads(response.choices[0].message["function_call"]["arguments"])
    
    if function_name == "validate_doi":
        result = validate_doi(function_args["doi"])
        # Send result back to model
```

**For Claude (tool use):**

```python
import anthropic

tools = [
    {
        "name": "validate_doi",
        "description": "Validate DOI via Crossref API and retrieve metadata",
        "input_schema": {
            "type": "object",
            "properties": {
                "doi": {"type": "string", "description": "DOI to validate"}
            },
            "required": ["doi"]
        }
    },
    # ... other tools
]

client = anthropic.Anthropic()
response = client.messages.create(
    model="claude-3-sonnet-20240229",
    max_tokens=4096,
    tools=tools,
    messages=[
        {"role": "user", "content": open("main.md").read() + "\n\n" + user_text}
    ]
)

# Handle tool use
for block in response.content:
    if block.type == "tool_use":
        if block.name == "validate_doi":
            result = validate_doi(block.input["doi"])
            # Send result back to model
```

**Recommendation:** Use function calling for real-time validation during generation. This ensures all metadata is verified before inclusion in final output.

---

## Quality Assurance

### Validation Checklist

Before using generated bibliography:

**Source-level checks:**
- [ ] All tiers correctly marked (OA / Training data corpus / unavailable)
- [ ] Citation threshold applied correctly (>500 only for Tier 2)
- [ ] Metadata complete (ISBN for books, DOI+pages for articles, URL for news)
- [ ] Citation locations SHORT (5-15 words) and CLEAR
- [ ] SUM concrete with specific concepts (not vague "important work")
- [ ] URLs cleaned (no tracking parameters)

**Coverage checks:**
- [ ] All major themes from user's text represented
- [ ] All named authors covered
- [ ] All core claims supported by sources
- [ ] No duplicates (same work listed multiple times)

**Format checks:**
- [ ] No generic phrases ("literature available", "multiple sources")
- [ ] No invented metadata (fake DOI/ISBN/URLs)
- [ ] SUM in source's original language
- [ ] Translations in square brackets with complete details

### Testing Scenarios

**Scenario 1: Small interdisciplinary text** (~10K chars, philosophy + CS)
- Expected: 20-30 sources across tiers
- Verify: both disciplines represented, foundational works included

**Scenario 2: Large Russian humanities text** (>50K chars)
- Expected: Request block segmentation
- Verify: Russian databases used (CyberLeninka, eLibrary.ru, philosophy.ru)

**Scenario 3: STEM text with recent literature** (2023-2025)
- Expected: Low citation counts for Tier 1/3
- Verify: Recent works included despite low citations

**Scenario 4: Canonical work inclusion** (text mentioning Heidegger, Foucault)
- Expected: Tier 2 handling with SPECIFIC OA alternatives
- Verify: 3-6 sentences with concrete concepts (not vague descriptions)

---

## Token Budget

### Estimated Token Usage

| Configuration | Characters | Tokens (approx.) | Components |
|---|---|---|---|
| main + auxiliary | ~38,900 | ~9,725 | Full system |
| main_short + auxiliary | ~30,300 | ~7,575 | Compact system |
| standalone_full | ~25,000 | ~6,250 | Self-contained |
| standalone_compact | ~6,200 | ~1,550 | Minimal |

*(Assumes ~4 characters per token average for mixed EN/RU text)*

### Optimization Tips

1. **Use short prompts for simple tasks** — `main_short.md` or `standalone_compact.md` for texts <20K chars
2. **Load auxiliary files selectively** — only load needed files (e.g., skip `examples.md` if model already understands format)
3. **Process large texts in blocks** — for >50K chars, segment into 5-15K blocks and process separately

---

## Contributing

### Reporting Issues

If you encounter problems:

1. **Check analysis documents first:**
   - `ANALYSIS_v1_v2_comparison.md` — structural/architectural questions
   - `ANALYSIS_external_requirements.md` — feature requests
   - `ANALYSIS_criteria_revision.md` — citation criteria questions

2. **Provide minimal reproducible example:**
   - Which prompt version used
   - Input text sample (anonymized if needed)
   - Actual output (highlight issues)
   - Expected output

### Suggesting Improvements

When proposing changes:

1. **Identify which file(s) need updates:**
   - Main prompts: `main.md`, `main_short.md`, `standalone_full.md`, `standalone_compact.md`
   - Auxiliary files: `criteria.md`, `requirements.md`, `examples.md`, `databases.md`

2. **Justify the change:**
   - What problem does it solve?
   - Does it improve accuracy/reproducibility/clarity?
   - Is it aligned with prompt engineering best practices (minimality, specificity)?

3. **Consider propagation:**
   - Updates to auxiliary files benefit `main.md` and `main_short.md` automatically
   - Standalone prompts must be updated manually

### Maintenance Guidelines

**When to update:**

1. **New disciplines:** Add to `databases.md` (table + details)
2. **New source types:** Add examples to `examples.md`, requirements to `requirements.md`
3. **Quality issues:** Update `criteria.md`, propagate to main prompts
4. **API changes:** Update metadata validation instructions

**Update propagation:**

- Auxiliary file updates → automatic for `main.md`, `main_short.md`
- Logic changes → update all four main prompt files manually
- Always maintain consistency across files

---

## License

This prompt system is provided as-is for academic and research use. Please cite appropriately if used in scholarly work.

---

## Version History

- **v1:** Original detailed prompt (~430 lines, single-mode, comprehensive)
- **v2:** Modular compact prompt (~77 lines, multi-mode, auxiliary files)
- **Unified (current):** Best of v1/v2, simplified modes, clarified criteria, metadata validation instructions, simple naming

**Last updated:** October 20, 2025

---

## Contact

For questions about specific prompt behavior, refer to:
- `ANALYSIS_v1_v2_comparison.md` — architectural decisions
- `ANALYSIS_external_requirements.md` — feature rationale
- `ANALYSIS_criteria_revision.md` — citation threshold clarifications
- `ИТОГИ_РАБОТЫ.md` — final report (Russian)

