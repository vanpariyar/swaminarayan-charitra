# Swaminarayan Charitra Translation & Post Creation Guidelines

This repository hosts daily Swaminarayan Charitra stories in a trilingual format (Gujarati, Hindi, English) published via Hugo.
Whenever creating, formatting, or translating new Charitra posts, always adhere to the following conventions.

---

## 1. Source Processing & Date Parsing

When given input files such as `આજનું ચરિત્ર-YYYY.docx.md` or similar raw text:
- Identify entry demarcations typically starting with:
  `(?:આજ\s*નું|આજ\s*નુ|આજનો|આજ)\s*ચરિત્ર\s*[:\s\-]+([^\n\r]+)`
- Digits may be in Gujarati (`૦-૯`) or ASCII (`0-9`) with `/` or `-` separators. Normalize all Gujarati digits to standard numbers:
  `૦->0, ૧->1, ૨->2, ૩->3, ૪->4, ૫->5, ૬->6, ૭->7, ૮->8, ૯->9`
- Convert parsed dates into standard ISO format: `YYYY-MM-DD`.
- If multiple charitras exist for the same calendar date, ensure each file has a distinct descriptive slug (e.g. `2020-11-08-gadhpur-lakshmivadi-ladudoshi-tandalja-bhaji.md` vs `2020-11-08-sarangpur-kashtbhanjandev-itihaas-gopalanand-swami.md`).

---

## 2. File Location & Naming

- **Directory**: `content/charitra/`
- **Filename pattern**: `YYYY-MM-DD-<kebab-case-slug>.md`
- **Slug style**: Lowercase English kebab-case highlighting key individuals, villages, and central themes (e.g., `2020-12-31-dangarva-jatanfai-dhan-randhyu-vardan.md`).

---

## 3. Hugo Frontmatter Format

```yaml
---
title: "<Gujarati Title> | <English Transliterated or Translated Title>"
date: YYYY-MM-DDT12:00:00+05:30
# draft: true
author: "Bharat Desai"
description: "<1-2 sentence Gujarati summary>. <1-2 sentence English summary>."
tags: ["<Tag1>", "<Tag2>", "<Tag3>", ...]
categories: ["Charitra"]
series: ["Daily Charitra"]
# aliases: ["migrate-from-jekyl"]
ShowToc: true
TocOpen: true
# weight: 2
---
```

- Always retain `categories: ["Charitra"]` and `series: ["Daily Charitra"]`.
- Include relevant geographical tags, devotee names, and central themes in `tags`.

---

## 4. Markdown Body & Trilingual Section Structure

Every file must follow this exact sequence:

```markdown
<!-- this Content Here will shown id listing page till "more" tag -->
<Opening 1-2 sentence hook in Gujarati>

<!--more-->

## Gujarati
### <Gujarati Title>

<Full Gujarati narrative from the entry:
 - Preserve authentic Saurashtra / Kathiyawadi dialect and vocabulary.
 - Format dialogues in bold (**"..."** or **...**).
 - Clean up raw messenger emojis (e.g. replace 🙇🏻‍♂️🙇🏻‍♂️🙏 with a clean 🙏).
 - Retain original book attributions at the end if present (e.g. '- શ્રીહરિચરિત્ર ચિંતામણિ...').>

[Goto Naviagation:point_down: ](#navigation)

----

## Hindi
### <Hindi Title>

<Complete, rich, devotional, and fluent Hindi retelling:
 - Must cover the full story, not just a brief summary.
 - Faithfully convey all dialogues in bold and emotional/devotional sentiment.
 - Use respectful Satsang vocabulary (e.g., श्रीजी महाराज, अक्षरधाम, महाप्रसादी, भक्तराज).
 - Conclude with 🙏.>

[Goto Naviagation:point_down: ](#navigation)

----

## English
### <English Title>

<Complete, rich, devotional, and fluent English narrative:
 - Must cover the full story, dialogues in bold, and moral/spiritual significance.
 - Retain or naturally contextualize traditional terms (thal, darshan, prasad, Akshardham, etc.).
 - Conclude with 🙏.>

### Navigation:point_down:

- [Gujarati](#gujarati)
- [Hindi](#hindi)
- [English](#english)
```

> **Note on Navigation Anchor**:
> Notice the exact spelling `[Goto Naviagation:point_down: ](#navigation)` used across the site templates.

---

## 5. Parallel Batch Generation (For Large Collections)

When translating large collections (10+ entries):
1. Parse raw entries into a structured JSON list (`id`, `date`, `content`).
2. Divide into batches of 10-12 entries.
3. Spawn parallel worker subagents (type `self`, `Workspace: inherit`) to generate files simultaneously.
4. Always verify the build with `npx hugo --minify` to confirm zero YAML/shortcode errors.
