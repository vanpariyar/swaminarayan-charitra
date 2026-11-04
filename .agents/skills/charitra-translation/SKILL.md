---
name: charitra-translation
description: >-
  Procedure for parsing, formatting, and generating trilingual (Gujarati, Hindi, English)
  Swaminarayan Charitra markdown posts for Hugo in the swaminarayan-charitra repository.
---

# Charitra Translation & Post Creation Runbook

Use this skill whenever parsing raw Charitra manuscripts or documents (e.g. `આજનું ચરિત્ર-YYYY.docx.md`), extracting daily stories, and generating publish-ready Hugo markdown posts in `content/charitra/`.

## Workflow Steps

### Step 1: Parse the Raw Input File
Raw entries typically begin with header patterns like:
```text
આજનું ચરિત્ર: DD-MM-YYYY
આજ નું ચરિત્ર: DD/MM/YYYY
આજ નુ ચરિત્ર: DD-MM-YYYY
```
Dates may contain Gujarati numerals (`૦-૯`).
Use a quick Python script to parse:
```python
import re, json

guj_to_eng = {"૦":"0", "૧":"1", "૨":"2", "૩":"3", "૪":"4", "૫":"5", "૬":"6", "૭":"7", "૮":"8", "૯":"9"}
def norm_digits(s):
    return "".join(guj_to_eng.get(c, c) for c in s)

# Extract and normalize dates to YYYY-MM-DD
```

### Step 2: Validate Schema & Structure
For every entry:
1. **Filename**: `content/charitra/YYYY-MM-DD-<slug>.md`
   - Kebab-case, lowercase English transliteration of key person, location, or subject.
2. **Frontmatter**:
```yaml
---
title: "<Gujarati Title> | <English Title>"
date: YYYY-MM-DDT12:00:00+05:30
# draft: true
author: "Bharat Desai"
description: "<1-2 sentence Gujarati summary>. <1-2 sentence English summary>."
tags: ["<Location>", "<Devotee/Sadhu>", "<Theme>", ...]
categories: ["Charitra"]
series: ["Daily Charitra"]
# aliases: ["migrate-from-jekyl"]
ShowToc: true
TocOpen: true
# weight: 2
---
```
3. **Excerpt Hook**:
First 1-2 sentences of the Gujarati story followed immediately by `<!--more-->`.
4. **Trilingual Sections**:
   - `## Gujarati` with `### <Gujarati Title>`, dialogue in bold, authentic dialect preserved, ending with `🙏`.
   - `[Goto Naviagation:point_down: ](#navigation)`
   - `----`
   - `## Hindi` with `### <Hindi Title>`, full narrative and dialogue in respectful Satsang Hindi, ending with `🙏`.
   - `[Goto Naviagation:point_down: ](#navigation)`
   - `----`
   - `## English` with `### <English Title>`, complete narrative in fluent devotional English, ending with `🙏`.
   - `### Navigation:point_down:` with links to `#gujarati`, `#hindi`, `#english`.

### Step 3: Scaling with Subagents
For collections of more than 10 entries:
- Split into JSON batch files (`batch_1.json`, `batch_2.json`, etc.) of ~10 items each.
- Launch `self` subagents with `Workspace: inherit` for parallel execution.
- After completion, delete temporary batch files.

### Step 4: Verification
Always run:
```bash
npx hugo --minify
```
Confirm all pages build successfully with 0 warnings or errors.
