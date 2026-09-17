# ai-skills

Core W3C utility skills, and centralized curation.

## Recommended W3C Skill Folder Structure

```
w3c-spec-validator/
├── SKILL.md              # Required: Metadata and core agent instructions
├── references/           # Optional: Deep-dive specs, schemas, or RFCs
│   └── aria-rules.json   # Loaded on demand by the agent to save context
└── scripts/              # Optional: Executable validation scripts
    └── check-compliance.py
```

## The SKILL.md Template

Markdown
---
name: w3c-spec-validator
description: Validates HTML, CSS, and Accessibility (WCAG) markup against official W3C recommendations. Use when the user asks to check compliance, audit web components, or fix accessibility errors.
metadata:
  author: "W3C Working Group"
  version: "1.0.0"
  tags:
    - wcag
    - html5
    - accessibility
    - validation
allowed-tools:
  - read_file
  - run_script
---

# W3C Specification Compliance Skill

## Overview
You are an expert W3C standards compliance agent. Your job is to analyze user code, markup, or application structures against official W3C recommendations and guidelines.

## Progressive Disclosure & Context Management
- Do **not** load full reference documents into memory unless an error type requires deep-dive rule checking.
- Look into `references/` only when specific edge cases or complex attribute states are questioned.

## Step-by-Step Instructions

1. **Scan and Parse:** Identify the target code snippet, document file, or component structure provided by the user.
2. **Evaluate Against Core Standards:**
   - Check structural semantics (e.g., proper heading hierarchies, valid nesting).
   - Check accessibility criteria (e.g., mandatory ARIA attributes, alt text text-equivalents, contrast logic).
3. **Run Validation Script (If applicable):**
   - If local environment execution is available, run `scripts/check-compliance.py` targeting the file path.
4. **Formulate Output:**
   - Cite the exact W3C specification section or WCAG Success Criterion (e.g., *WCAG 2.1 Success Criterion 4.1.2: Name, Role, Value*).
   - Provide a direct, standards-compliant corrected code snippet.

## Decision Rules (If/Then)
- **If** the markup violates a foundational HTML specification rule, prioritize fixing the structure before styling or accessibility.
- **If** the user requests a quick audit, output a concise table of errors grouped by severity (Critical, Moderate, Minor).
- **If** the user asks how to implement a complex component, reference the W3C WAI-ARIA Authoring Practices Guid
- 
