# REN
This is the repo for the exercises used in the 2025 REN Data Sharing Workshop

# ALS Harmonization & OMOP Standards Toolkit  
### *A Unified Guide for Workshops, Exercises, Facilitators & Templates*  
---

# 📘 Table of Contents

1. [Introduction](#introduction)  
2. [Part 1 — Instinctive Harmonization Exercise](#part-1--instinctive-harmonization-exercise)  
3. [Part 2 — OMOP & Vocabulary Harmonization Exercise](#part-2--omop--vocabulary-harmonization-exercise)  
4. [Side-by-Side Mapping Tables](#side-by-side-mapping-tables)  
5. [OMOP Mapping Template (Fillable)](#omop-mapping-template-fillable)  
6. [One-Page OMOP Domain Cheat Sheet](#one-page-omop-domain-cheat-sheet)  
7. [Slide Deck (Markdown Presentation Version)](#slide-deck)  
8. [Full “Harmonizing a Registry to OMOP” Guide](#full-harmonizing-a-registry-to-omop-guide)  
9. [Facilitator Guide (Hidden Notes Included)](#facilitator-guide-hidden-notes-included)  

---

# Introduction

This toolkit contains everything needed to teach and run a **data harmonization workshop** using:

- **Answer ALS**  
- **ALS TDI (ALS Research Collaborative)**  

It demonstrates:

1. How teams naturally (“instinctively”) attempt to harmonize data  
2. Why this produces inconsistent & unscalable results  
3. How OMOP CDM + standard vocabularies fix this  
4. How to design future-proof registries  

All content—exercises, facilitator guides, OMOP templates, and slides—is consolidated into this **single Markdown file** for easy offline use, GitHub viewing, or exporting to PDF.

---

# Part 1 — Instinctive Harmonization Exercise

### Step 1 — Domain Labeling (Intuition-Driven)

In breakouts, label each row with *whatever domain names feel right to you*.

| Domain (your instinct) | Answer ALS Form | ALS TDI Forms |
|------------------------|-----------------|---------------|
|                        | Demographics | General Information 1; Questionnaire |
|                        | Medical History; Neurological Log | Conditions; Injuries; Questionnaire |
|                        | Tracheostomy; Feeding Tube; NIV; DPS | Questionnaire |
|                        | Medications Log | Medications; Supplements |
|                        | Family History | Family History |
|                        | Environmental Questionnaire | Lifestyle; Occupation; Geography |
|                        | ALS History; Diagnosis | Your ALS Experience |
|                        | ALSFRS_R | ALSFRS; Other Data |
|                        | ALS Gene Mutations | Genomic Data |
|                        | Auxiliary Chemistry Labs | Quest Data |
|                        | Mortality | Other Data |

➡️ **Discussion:**  
- What domains did you naturally create?  
- Did your group split or combine differently than others?  
- How many unique domain labels appeared across all groups?

---

### Step 2 — Identify Missing / Extra Domains

#### Answer ALS has data ALS TDI lacks:

- Vital signs  
- Vital capacity  
- Strength testing  
- Reflexes  
- Cognitive/caregiver screen  
- PBA scale  
- Study eligibility  
- Specimen collection (plasma, serum, PBMC, DNA, CSF)

#### ALS TDI has data Answer ALS lacks:

- Clinical trials participation  
- Hospitalizations  
- Accelerometer data  
- Voice data  
- Additional general info set

➡️ **Which missing domains matter for harmonization?**

---

### Step 3 — Mini Interoperability Assessment

Using the worksheet, evaluate **3–4 domains**:

| Domain | Key Fields | Standard Vocabularies? | Shared Definitions? | Harmonization Issues |
|--------|-------------|------------------------|----------------------|----------------------|
|        |             |                        |                      |                      |
|        |             |                        |                      |                      |

---

<!-- hidden facilitator note:
Expected issues: inconsistent ALSFRS naming, ambiguous onset dates, free-text medications, different biospecimen formats.
-->

---

### Step 4 — First-Pass Harmonization (Ad-Hoc)

Before OMOP, participants produce mappings like:

| Harmonized Field | Answer ALS | ALS TDI | Problems |
|------------------|------------|---------|----------|
| ALSFRS_total | ALSFRS_R | ALSFRS | Version mismatch |
| onset_date | Diagnosis details | Your ALS Experience | Different definitions |
| meds_list | Medications Log | Meds + Supplements | Free text |

➡️ **The chaos is intentional. This sets up Part 2.**

---

# Part 2 — OMOP & Vocabulary Harmonization Exercise

Now redo mapping using **OMOP CDM** and **standard vocabularies**.

OMOP gives:

- Shared domain structure  
- Shared vocabulary  
- Shared semantics  

---

### OMOP Domain Primer

| OMOP Table | Concept |
|------------|---------|
| PERSON | Demographics |
| CONDITION_OCCURRENCE | Diagnoses & history |
| DRUG_EXPOSURE | Medications |
| PROCEDURE_OCCURRENCE | Procedures & devices |
| MEASUREMENT | Labs, ALSFRS, vitals |
| OBSERVATION | Environment, PROs |
| SPECIMEN | Biospecimens |
| DEATH | Mortality |

---

### Vocabulary Primer

| Domain | Vocabulary |
|--------|------------|
| Diagnosis | SNOMED |
| Medications | RxNorm |
| Labs | LOINC |
| Phenotypes | HPO |
| Genomics | HGNC/ClinVar |
| Devices | SNOMED |

---

### OMOP-Based Mapping

| OMOP Domain | Answer ALS | ALS TDI |
|-------------|------------|---------|
| PERSON | Demographics | General Info 1 |
| CONDITION_OCCURRENCE | ALS Dx, Medical History | Conditions; Injuries |
| DRUG_EXPOSURE | Medications | Medications; Supplements |
| MEASUREMENT | ALSFRS_R; Labs; Strength | ALSFRS; Quest |
| SPECIMEN | Plasma, Serum, PBMC, DNA, CSF | — |
| OBSERVATION | Environmental Q | Lifestyle; Geography |
| PROCEDURE_OCCURRENCE | Feeding tube, NIV | Procedures in questionnaires |
| DEATH | Mortality | Mortality |

---

### OMOP Harmonized Fields

| OMOP Field | Value | Vocabulary |
|------------|--------|------------|
| condition_concept_id | ALS | SNOMED 86044005 |
| measurement_concept_id | ALSFRS-R | LOINC 89261-2 |
| drug_concept_id | Riluzole | RxNorm 83367 |
| specimen_type_concept_id | Plasma | OMOP Specimen |
| gene_variant | C9orf72 | HGNC |

---

# Side-by-Side Mapping Tables

| Concept       | OMOP                  | Answer ALS        | ALS TDI          |
|---------------|------------------------|--------------------|------------------|
| ALS diagnosis | CONDITION_OCCURRENCE  | Dx details         | Your ALS Experience |
| ALSFRS-R      | MEASUREMENT           | ALSFRS_R           | ALSFRS           |
| Medications   | DRUG_EXPOSURE         | Med Log            | Med + Supp       |
| Labs          | MEASUREMENT           | Chemistry          | Quest            |
| Biospecimens  | SPECIMEN              | Plasma, PBMC       | —                |
| Mortality     | DEATH                 | Mortality          | Other Data       |

---

# OMOP Mapping Template (Fillable)

Use this template during harmonization work to map fields from Answer ALS and ALS TDI into OMOP.

| Source Field | Source Value Example | OMOP Table | OMOP Field | Vocabulary | Concept ID | Notes |
|--------------|----------------------|------------|------------|------------|------------|-------|
| ALSFRS_R_total | 32 | MEASUREMENT | measurement_concept_id | LOINC | 89261-2 | Confirm version |
| Riluzole | “Riluzole” | DRUG_EXPOSURE | drug_concept_id | RxNorm | 83367 | Normalize free-text meds |
| ALS Diagnosis | "ALS" | CONDITION_OCCURRENCE | condition_concept_id | SNOMED | 86044005 | Harmonize onset definitions |
| Vital Capacity | 2.4 L | MEASUREMENT | measurement_concept_id | LOINC | 19849-0 | Units must match |
| PBMC Sample | Y | SPECIMEN | specimen_type_concept_id | OMOP Specimen | — | Add specimen date |

---

# One-Page OMOP Domain Cheat Sheet

### PERSON  
Demographics (birth year, sex, race, person ID)

### CONDITION_OCCURRENCE  
Diagnoses & medical history  
Uses **SNOMED**

### DRUG_EXPOSURE  
Medications & supplements  
Uses **RxNorm**

### MEASUREMENT  
Labs, ALSFRS, vitals, strength  
Uses **LOINC**

### PROCEDURE_OCCURRENCE  
Feeding tube, tracheostomy, NIV  
Uses **SNOMED/CPT**

### OBSERVATION  
Environment, lifestyle, PROs, surveys

### SPECIMEN  
Plasma, serum, PBMC, CSF, DNA

### DEATH  
Mortality, death date, source  

---

# Slide Deck

Below is the slide content formatted for **MkDocs Material** using `::: slides`.

::: slides

## ALS Harmonization  
### Instinct → OMOP

---

## Why OMOP?
- Shared structure  
- Shared vocabularies  
- Shared governance

---

## Instinctive Mapping → Divergence
- Each group creates different domains  
- Different field names  
- No interoperability  

---

## OMOP Mapping → Convergence
Everyone produces:  
- Same domains  
- Same vocabularies  
- Same structure  

---

## ALSFRS Example (OMOP)
- measurement_concept_id = **LOINC 89261-2**  
- value_as_number  
- measurement_date (ISO-8601)

---

## Medications Example (OMOP)
- drug_concept_id = **RxNorm**  
- dose, route, start_date  

---

## Takeaway
**OMOP = Shared Language**  
**Vocabularies = Consistent Meaning**

:::

---

# Full “Harmonizing a Registry to OMOP” Guide

A practical, step-by-step guide for transitioning any registry (ALS, rare epilepsy, etc.) into OMOP CDM.

---

## Step 1 — Inventory Your Data
List every form, field, and variable. Include:
- Definitions
- Units
- Value sets
- Skip logic

---

## Step 2 — Assign OMOP Domains

| Registry Concept | OMOP Table |
|------------------|------------|
| Demographics | PERSON |
| ALS Diagnosis | CONDITION_OCCURRENCE |
| Medications | DRUG_EXPOSURE |
| ALSFRS / Labs | MEASUREMENT |
| Procedures | PROCEDURE_OCCURRENCE |
| PROs | OBSERVATION |
| Specimens | SPECIMEN |
| Mortality | DEATH |

---

## Step 3 — Attach Vocabulary Concepts

Examples:

- ALS → SNOMED **86044005**  
- ALSFRS → LOINC **89261-2**  
- Riluzole → RxNorm **83367**  
- Vital Capacity → LOINC **19849-0**  

---

## Step 4 — Build OMOP Tables

Start with:

- PERSON  
- CONDITION_OCCURRENCE  
- DRUG_EXPOSURE  
- MEASUREMENT  
- OBSERVATION  
- SPECIMEN  
- DEATH  

---

## Step 5 — Identify Gaps

Common issues:

- Free text  
- Missing dates  
- Mixed units  
- Multiple onset definitions  

---

## Step 6 — Validate

Ensure:

- All fields mapped  
- All concepts valid  
- Dates formatted  
- No orphan variables  

---

## Step 7 — Publish Harmonized Dictionary

This becomes your **source of truth**.

---

# Facilitator Guide (Hidden Notes Included)

<!-- facilitator: emphasize difference between instinctive divergence and OMOP convergence -->

## Purpose
Help participants experience:
- Chaos of instinctive mapping  
- Clarity brought by OMOP  

## Timing
- Intro: 5 min  
- Instinct mapping: 15–20 min  
- Debrief: 5 min  
- OMOP mapping: 15–20 min  
- Final discussion: 10 min  

## Expected Participant Insights
- Domain names differ  
- Free text everywhere  
- Missing definitions  
- Difficulty comparing ALSFRS  
- “Wow — OMOP solves these problems”

<!-- facilitator: capture quotes from participants showing “aha moment” -->

