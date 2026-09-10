# 📊 AI-Allowed Assessment Readiness Index (A3I)

**Author:** Javier Jimenez
**Email:** javierji@buffalo.edu
**Research lead:** Sam Abramovich, University at Buffalo
**Date created:** August 2026
**Status:** 🚧 Phase 2 — Data reconnaissance (Texas STAAR pilot)

## 📝 Description

A3I is a research project asking whether state-approved K-12 assessments can already be completed effectively by generative AI. This is **not** a cheat-detection project. It is focused on what current assessment design means now that generative AI is widely available, and on the washback effect this could have on classroom instruction:

```
STATE ASSESSMENT  ->  CURRICULUM & ASSIGNMENTS  ->  STUDENT PRACTICE  ->  LEARNING
```

If a high-stakes assessment rewards a task generative AI can complete easily, the pressure that assessment puts on classrooms may be pushing instruction toward products whose relationship to student learning has changed. A3I aims to provide empirical evidence about the size and structure of that problem, starting with a Texas STAAR pilot before expanding to other states.

## 🎬 Demo

_Screenshots / dashboard preview to be added once the pilot dataset is ready._

## ✨ Features

* 📚 A structured public assessment corpus
* 🤖 An empirical AI benchmark
* 🧩 An explanatory taxonomy
* 📐 The A3I measurement framework
* 🌐 Public-facing outputs (open dataset, reproducible code, dashboard, papers, policy briefs)

## 📁 Project files

| File | What it is |
|---|---|
| 📗 `A3I_Record_Keeper.xlsx` | The source inventory log for released Texas STAAR materials, plus its own Data Dictionary and controlled-vocabulary tabs, all in one workbook. Supersedes the earlier `Record_Keeper.csv` + `Data_Dictionary.xlsx` pair — those are no longer maintained separately. |
| 📄 `raw_questions.csv` | Template for logging individual assessment items once extraction begins (question text, answer choices A-D, correct answer, reference text). Currently a header only — no items extracted yet. |
| 📘 `A3I_Javier_Onboarding_Packet_Draft_v1_1.docx` | Project overview, vocabulary/glossary, first-assignment brief, 100-hour fall work plan, working norms, and the draft technical architecture/data flow. Read this first. |
| 🔗 `A3I_URL_Reference_PG.docx` | Authoritative TEA source links identified so far (STAAR Grade 3 RLA: released test forms, answer key, item rationale, scoring guide/rubrics, blueprint, curriculum standards, and related resources). |
| 🗂️ `Converted_Data/` | _Not started yet._ Will hold the canonical, machine-readable item schema once the extraction layer (Phase 4) is built. |

## 🛠️ Built with

* 🐍 Python (version TBD)
* 🔢 NumPy (version TBD)
* 🐼 Pandas (version TBD)
* _Environment/dependencies list to be finalized during Phase 1 (Orientation) — see Installation below._

## ⚙️ Installation

The project is still in the data-reconnaissance phase (no extraction/acquisition code yet), so for now:

1. 📥 Clone the repository.
2. 📂 Navigate to the project directory.
3. 📖 Open `A3I_Javier_Onboarding_Packet_Draft_v1_1.docx` first for project context, then `A3I_Record_Keeper.xlsx` for the current source inventory.

A `requirements.txt` and environment setup steps will be added here once the acquisition pipeline (Phase 3) begins.

## 📖 Usage

* ✅ Log every official STAAR resource you find in `A3I_Record_Keeper.xlsx` — one row per resource (a released test form, its answer key, its rubric, etc. are separate rows). Field definitions and allowed values are on that workbook's `Data_Dictionary` and `Controlled_Vocabularies` tabs.
* ❓ Leave a field blank and note it in `Notes_Unresolved_Questions` rather than guessing — per the onboarding packet's provenance and "do not invent missing metadata" rules.
* 🔜 Detailed local run instructions will be added once there is code to run (Phase 3+).

## 🗺️ Roadmap

From the 100-hour fall work plan (see the onboarding packet for full detail):

| Phase | Hours | Focus | Deliverable |
|---|---|---|---|
| 1️⃣ Orientation | 8 | A3I basics, Git/GitHub, project conventions | Working environment + project understanding |
| 2️⃣ Data reconnaissance | 12 | Map Texas STAAR RLA/math sources and metadata | Source inventory + reconnaissance reflection |
| 3️⃣ Acquisition pipeline | 20 | Reproducible downloading and source registration | Scripts + source manifest + raw archive conventions |
| 4️⃣ Extraction & schema | 30 | Extract item/stimulus/answer/rubric metadata | Structured Texas dataset + schema documentation |
| 5️⃣ QA & validation | 15 | Errors, duplicates, missing fields, provenance, edge cases | QA report + corrected pipeline/dataset |
| 6️⃣ AI benchmark prototype | 10 | Controlled model-evaluation proof of concept, if ready | Pilot results on a limited clean sample |
| 7️⃣ Documentation & handoff | 5 | Make the work reproducible for another researcher/developer | README, setup notes, issues, next steps |

## 📬 Contact

Questions or corrections: Javier Jimenez (javierji@buffalo.edu), research lead Sam Abramovich, University at Buffalo.
  ## Raw_Data:
  [Download the Documentation](raw_questions.csv)
  
  ## Converted_Data:

  
