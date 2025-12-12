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
