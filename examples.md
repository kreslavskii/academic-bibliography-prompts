# Annotated Examples for All Source Types

This file contains complete annotated examples for all source types in correct format according to `requirements.md`.

---

## Example 1: OA Article (Journal Article, Open Access)

```
[1] Star, S.L.; Ruhleder, K. Steps Toward an Ecology of Infrastructure: Design and Access for Large Information Spaces. Information Systems Research, 1996, 7(1), pp. 111–134. DOI: 10.1287/isre.7.1.111.

- Места размещения в тексте:
1.1. инфраструктура невидима до момента поломки [1]
1.2. релятивность инфраструктуры — она инфраструктура для кого-то [1]

- SUM: Defines infrastructure relationally: infrastructure for some is system for others; becomes infrastructure when embedded in other structures and invisible in use. Shows infrastructure is learned as part of membership in communities of practice. Infrastructure "sinks into invisibility" when working — becomes visible only upon breakdown.

- LINKS: https://doi.org/10.1287/isre.7.1.111

---
```

**Annotation:**
- Journal article with DOI
- SUM in English (source language)
- Two citation locations (1.1, 1.2)
- Link to full text (may require institutional access — check when using)

---

## Example 2: Training Data Source (Canonical Work Without OA)

```
[2] Heidegger, M. Die Frage nach der Technik. In: Vorträge und Aufsätze. Pfullingen: Günther Neske Verlag, 1954. S. 9–40. ISBN: 978-3-608-91090-3.
[Рус. пер.: Хайдеггер М. Вопрос о технике // Время и бытие. М.: Республика, 1993. С. 221–238. ISBN: 5-250-01416-7.]

- Места размещения в тексте:
2.1. Хайдеггер рассматривает технику как способ раскрытия [2]
2.2. что Хайдеггер называл Gestell [2]
2.3. прохождение через технику [2]

- SUM: Развивает онтологическое понимание техники как способа раскрытия (Entbergen) истины бытия через концепт Gestell (постав). Показывает, что техника — не инструмент, а способ обнаружения сущего как наличного запаса. Опасность Gestell одновременно содержит спасительную силу.

- LINKS: unavailable

- Source: Training data corpus
- For OA analysis see: Mitcham, C. (1994) Thinking Through Technology: The Path Between Engineering and Philosophy. University of Chicago Press, chapter 2 on Heidegger (excerpts at https://philpapers.org/rec/MITATT); Feenberg, A. (2005) "Heidegger and Marcuse: The Catastrophe and Redemption of History" DOI:10.1177/0270467604271196

---
```

**Annotation:**
- Book chapter, canonical philosophical text
- Translation indicated in square brackets with complete details
- SUM in Russian (translation language, more relevant for user)
- Three citation locations (characteristic for foundational works)
- Marked "Source: Training data corpus"
- Specific OA alternatives with complete bibliographic data

---

## Example 3: OA Book (Book, Open Access)

```
[3] Ong, W.J. Orality and Literacy: The Technologizing of the Word. Routledge, 2012 (30th Anniversary Edition; originally 1982). ISBN: 978-0-415-53838-1.

- Места размещения в тексте:
3.1. исследований Онга о том, как письменность перестраивает мышление [3]
3.2. письменность создаёт аналитическое мышление [3]

- SUM: Explores fundamental differences between oral and literate cultures, showing how writing technology transforms consciousness. Demonstrates that literacy is not neutral recording but restructures thought: creates analytic abstraction, visual thinking, detachment from context. Shows orality relies on mnemonic formulas and situational thinking.

- LINKS: https://monoskop.org/images/d/db/Ong_Walter_J_Orality_and_Literacy_2nd_ed.pdf

---
```

**Annotation:**
- Book in OA (full PDF)
- Edition noted (30th Anniversary) and original year (1982)
- SUM in English (source language)
- Link to stable repository (Monoskop)

---

## Example 4: News Source (News/Web Source)

```
[4] Reuters. "Fire at South Korea's National Information Resources Service data center halts online government services." September 26, 2025. https://www.reuters.com/world/asia-pacific/fire-south-korea-data-center-2025-09-26 [Accessed: October 19, 2025]

- Места размещения в тексте:
4.1. 26 сентября 2025 года пожар в дата-центре Южной Кореи [4]
4.2. парализовал 96 государственных систем [4]

- SUM: Документирует пожар в национальном дата-центре NIRS (Тэджон), вызвавший сбой госуслуг. Подтверждает масштаб инцидента и первичные объяснения причин. Служит опорой для аргумента о хрупкости централизованной инфраструктуры без резервирования.

- LINKS: https://www.reuters.com/world/asia-pacific/fire-south-korea-data-center-2025-09-26

---
```

**Annotation:**
- News source (URL mandatory)
- Access date indicated in square brackets (recommended for web sources)
- SUM in Russian (for Russian-speaking user)
- Two citation locations
- URL cleaned of tracking parameters

---

## Example 5: Paywalled Source (With Metadata + OA Alternative)

```
[5] Vinsel, L.; Russell, A.L. The Innovation Delusion: How Our Obsession with the New Has Disrupted the Work That Matters Most. New York: Currency, 2020. ISBN: 978-0-525-57568-9.

- Места размещения в тексте:
5.1. историки технологий Винсел и Рассел [5]
5.2. инновация без культуры поддержания (maintainers) [5]

- SUM: Argues that obsession with innovation devalues maintenance and care, creating fragility. Shows innovation-speak masks neglect of essential work — maintenance, repair, upkeep. Demonstrates that sustainable systems require maintainers more than innovators: keeping existing infrastructure working matters more than disruption.

- LINKS: unavailable

- For OA review see: Russell, A.L.; Vinsel, L. (2016) "Hail the Maintainers" Aeon https://aeon.co/essays/innovation-is-overvalued-maintenance-often-matters-more (essay version of book's core argument)

---
```

**Annotation:**
- Recent book (2020), paywalled
- SUM in English (source language)
- LINKS: unavailable
- NOT marked as "Training data" (2020 book does not meet criteria)
- Specific OA alternative suggested (authors' essay with key book argument)

---

## Example 6: Source with Multiple Citation Locations

```
[6] Bowker, G.C.; Star, S.L. Sorting Things Out: Classification and Its Consequences. Cambridge, MA: MIT Press, 1999. ISBN: 978-0-262-52295-3.

- Места размещения в тексте:
6.1. классификации структурируют социальные миры [6]
6.2. инфраструктура невидима до момента поломки [6]
6.3. стандарты кодируют ценности и политические выборы [6]
6.4. знание функционирует как инфраструктура [6]

- SUM: Examines how classification systems structure social worlds and knowledge infrastructures. Shows classifications are invisible yet powerful — encode values, create categories, produce advantage and suffering. Knowledge functions as infrastructure: invisible when working, catastrophically visible when fails. Standards and classifications are not neutral but political and moral choices embedded in material practice.

- LINKS: https://hcommons.org/app/uploads/sites/1001532/2020/03/Bowker-1999-Sorting-Things-Out-Classification-and-Its-Consequences.pdf

---
```

**Annotation:**
- Book with OA copy
- FOUR citation locations (6.1, 6.2, 6.3, 6.4) — characteristic for foundational works touching multiple themes
- Extended SUM (4 sentences) due to multiple relevance
- Link to stable repository (Humanities Commons)

---

## Example 7: Preprint

```
[7] Smith, J.; Johnson, A. "Large Language Models and Scholarly Research: Opportunities and Challenges" [Preprint]. arXiv:2310.12345, 2023.

- Места размещения в тексте:
7.1. использование LLM для научного поиска [7]

- SUM: Examines opportunities and risks of using large language models for literature search and synthesis. Discusses hallucination risks and verification strategies. Relevant to methodological considerations of AI-assisted bibliography creation.

- LINKS: https://arxiv.org/abs/2310.12345

---
```

**Annotation:**
- Preprint marked [Preprint] after title
- arXiv ID instead of DOI: arXiv:2310.12345
- No journal/publisher (characteristic for preprints)
- Direct link to arXiv

---

## Example 8: Multi-Volume Work

```
[8] Stiegler, B. La technique et le temps. Tome 1: La faute d'Épiméthée. Paris: Galilée, 1994. ISBN: 978-2-7186-0425-5.
[English: Stiegler, B. Technics and Time, 1: The Fault of Epimetheus. Stanford: Stanford University Press, 1998. ISBN: 978-0-8047-3041-5.]

- Места размещения в тексте:
8.1. Техника — фармакон [8]
8.2. память эпифилогенетическая (распределённо-культурная) [8]
8.3. гипомнематическая (экстериоризованная) [8]

- SUM: Develops concept of technics as constitutive of human being — humans are "prosthetic" beings defined by technical exteriorization. Introduces three types of memory: genetic, epiphylogenetic (cultural-technical transmission), and individual. Presents technics as pharmakon (poison/remedy): simultaneously enabling and threatening.

- LINKS: unavailable

- Source: Training data corpus
- For OA analysis see: Roberts, B. (2006) "Stiegler Reading Derrida" Postmodern Culture DOI:10.1353/pmc.2006.0011 (open access); Hansen, M.B.N. (2010) "Media Theory" Theory, Culture & Society https://doi.org/10.1177/0263276410398291

---
```

**Annotation:**
- Multi-volume work: specific volume indicated (Tome 1) with subtitle
- ISBN for specific volume (not series ISBN)
- English translation indicated separately with complete data
- SUM combines key concepts of volume
- Marked as Training data with specific OA alternatives

---

## Example 9: E-Book with Unstable Pagination

```
[9] Borgman, C.L. Big Data, Little Data, No Data: Scholarship in the Networked World. Cambridge, MA: MIT Press, 2015. ISBN: 978-0-262-52891-7 (electronic).

- Места размещения в тексте:
9.1. (Chapter 3) инфраструктуры данных: от сбора до повторного использования [9]
9.2. (Chapter 5) ресурсная цена репликабельности [9]

- SUM: Analyzes how data infrastructures and standards shape knowledge production in networked scholarship. Shows institutional and technical requirements for data reuse across disciplines. Demonstrates resource costs of reproducibility and verification in real scientific practice.

- LINKS: https://direct.mit.edu/books/monograph/3085/Big-Data-Little-Data-No-Data

---
```

**Annotation:**
- E-book: ISBN of electronic version specified with (electronic) notation
- Citation locations use chapter numbers instead of pages: "(Chapter 3)", "(Chapter 5)"
- This approach solves unstable pagination problem in e-books

---

## Summary Table: Source Types

| Source Type | Mandatory Fields | Special Features |
|---|---|---|
| OA article | Author, title, journal, volume(issue), year, pp. XX-YY, DOI | Link to full text |
| Training data | Full bibliography + ISBN/DOI | Mark "Source: Training data corpus" + specific OA alternatives |
| OA book | Author, title, publisher, year, ISBN | Link to full text (PDF/HTML) |
| News | Outlet, title, date, URL | Access date recommended |
| Paywalled | Full bibliography + ISBN/DOI | "unavailable" + specific OA alternatives (if available) |
| Multi-volume | Volume N: Subtitle, volume ISBN | ISBN of specific volume, not series |
| Preprint | [Preprint], arXiv ID / bioRxiv DOI | Preprint server instead of journal |
| E-book | ISBN (electronic), chapter numbers | Use "(Chapter N)" instead of pages |

---

**These examples cover all major source types and demonstrate correct application of `requirements.md` format for various situations.**

