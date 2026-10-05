# 📊 AI-Allowed Assessment Readiness Index (A3I)

**Author:** Javier Jimenez
**Email:** javierji@buffalo.edu
**Research lead:** Sam Abramovich, University at Buffalo
**Date created:** August 2026
**Last updated:** October 2026 (resource inventory v0.3)
**Status:** 🚧 Phase 2 — Data reconnaissance (Texas STAAR pilot). Resource inventory v0.3 complete; 4 of 15 pilot records still open (see [Quality assurance](#-quality-assurance)).

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
| 📗 `A3I_Record_Keeper_ver0.3.xlsx` | The current resource inventory for released Texas STAAR materials. Tabs: **Record_Keeper** (the inventory), **Data_Dictionary** (every field's definition and allowed values), **Instructions** (entry rules), **Update_Notes** (change log and old-to-new ID map). |
| 📗 `A3I_Record_Keeper_ver0.2.xlsx` | Previous version, kept unchanged for reference. |
| 🧩 `Things_that_didnt_fit_v0.3.docx` | Cases the inventory structure had trouble representing during the pilot, and what we propose to do about each one. |
| 🔍 `Item_Source_Trace_G3_Math_2026.md` | Small test of where each piece of five Grade 3 Math items can be found, to prepare for item acquisition. |
| 📄 `raw_questions.csv` | Template for logging individual assessment items once extraction begins (question text, answer choices A-D, correct answer, reference text). Header only; no items extracted yet. |
| 📘 `A3I_Javier_Onboarding_Packet_Draft_v1_1.docx` | Project overview, vocabulary/glossary, first-assignment brief, 100-hour fall work plan, working norms, and the draft technical architecture/data flow. Read this first. |
| 🔗 `A3I_URL_Reference_PG.docx` | Authoritative TEA source links identified at the start of the pilot (STAAR Grade 3 RLA). The Record Keeper is now the maintained list of sources. |
| 🗂️ `Converted_Data/` | _Not started yet._ Will hold the canonical, machine-readable item schema once the extraction layer (Phase 4) is built. |

## 🗃️ How the resource inventory works

The fall pilot covers Texas STAAR in three contexts: **Grade 3 RLA**, **Grade 3 Mathematics** and **Algebra I** (15 resources).

### One resource per row
Each row in `Record_Keeper` is one authoritative resource: a document, file, web page or test interface. Every field describes **that resource only**. A single test usually has several rows (test, answer key, rationales, scoring guide, blueprint).

### Inclusion rule
A resource is included if it is published by the state agency or its official test vendor, and it describes, scores or delivers the assessment for an in-scope subject and grade or course. Open questions about Spanish versions and student reference materials are in *Things That Did Not Fit*.

### Field conventions
* 🔑 **Resource_ID** is our own ID (`TX-0001`, `TX-0002` ...), assigned once and never reused. Any ID the agency or platform assigns (e.g. Cambium's `testId`) goes in **Source_Assigned_ID**.
* 📦 **Content fields** describe what is *inside this resource*, never what exists elsewhere for the same test:
  * `Contains_Correct_Answer_Info`: does it state correct answers?
  * `Contains_Item_Rationale`: does it explain why answers are right or wrong?
  * `Contains_Standards_Reference`: does it name the TEKS standard for individual items? (Standards listed only by reporting category, as in blueprints, count as N.)
  * `Contains_Scoring_Criteria`: does it give rubric or scoring criteria for written responses?

  Each takes Y / N / Unknown.
* 📝 **Item_Text_Coverage** (None / Partial / Full / Unknown) records how much item content the resource reproduces *as students see it*. Explanations or paraphrases of an item don't count, even if they quote a phrase. Partial means some items are reproduced in full and others not at all, and the notes say which.
* 📋 **Resource_Type**, **Subject**, **Access_Format**, **Technical_Barrier_Type** and **QA_Status** use dropdowns. The allowed values are listed in the Data_Dictionary (there is no separate Controlled_Vocabularies tab as of v0.3). Rubric (generic scoring criteria) and Scoring Guide (one administration's scored sample responses) are separate types.
* ✍️ Titles are copied exactly as printed. Dates use `YYYY-MM-DD`.

### Resources that cover several grades or years
They get **one row**, never duplicates.
* **Grade_Scope** is text: a single grade (`3`), a hyphenated range (`3-5`), or `N/A` for course-based tests. Course-based tests also fill **Course** (e.g. `Algebra I`).
* **Test_Year_Scope** is `YYYY` for a resource made for one administration, `YYYY-YYYY` or `YYYY-present` for one that stays in effect (the rubrics and blueprints are `2022-present`), or `Unknown`. A value ending in `present` should be read together with **Retrieval_Date**.
* To filter by grade or year in code, split the range on the hyphen.

### Recording uncertainty
Values are never guessed. When something can't be confirmed from the source, the field is set to `Unknown` (or left blank where there is no Unknown option), and **Notes_Unresolved_Questions** explains why. **Technical_Barrier_Type** must agree with the notes. Problems with the structure itself go in *Things That Did Not Fit*.

### ✅ Quality assurance
Every row has a **QA_Status**:
* **Not Reviewed**: entered, but not yet checked against the source.
* **Reviewed**: the source was reopened and every field was checked against it.
* **Needs Resolution**: a problem was found that needs discussion. It is described in the notes.

Current pilot status: **11 Reviewed**, **1 Needs Resolution** (Algebra I rationales: 49 items vs. 50 in the answer key, and an unexplained "updated" file), **3 Not Reviewed** (the online practice tests, which still need checking in a browser). The 2026-10-04 QA pass was done with help from Claude, an AI assistant, reading each PDF (see Update_Notes).

## 🔗 How this connects to item acquisition
The inventory is the map for Phases 3–4. It shows which resource supplies which piece of an item (prompt, options, figures, correct answer, points, standard, rationale, scoring) and which pieces exist only in the online test.

The first trace (`Item_Source_Trace_G3_Math_2026.md`) found:
* The downloadable PDFs are enough to rebuild technology-enhanced items (multiple select, drag and drop): the answer-key appendix reproduces them in full.
* Multiple-choice question text, answer choices and figures appear only in the online test, so the online interface has to be one of the acquisition sources.
* `raw_questions.csv` assumes answer choices A-D. It will need to be extended for multi-select, drag-and-drop and constructed-response items before extraction begins.

## 🛠️ Built with

* 🐍 Python (version TBD)
* 🔢 NumPy (version TBD)
* 🐼 Pandas (version TBD)
* _Environment/dependencies list to be finalized during Phase 1 (Orientation) — see Installation below._

## ⚙️ Installation

The project is still in the data-reconnaissance phase (no extraction/acquisition code yet), so for now:

1. 📥 Clone the repository.
2. 📂 Navigate to the project directory.
3. 📖 Open `A3I_Javier_Onboarding_Packet_Draft_v1_1.docx` first for project context, then `A3I_Record_Keeper_ver0.3.xlsx` for the current source inventory.

A `requirements.txt` and environment setup steps will be added here once the acquisition pipeline (Phase 3) begins.

## 📖 Usage

* ✅ Log every official STAAR resource you find in `A3I_Record_Keeper_ver0.3.xlsx`, one row per resource, following the rules on the **Instructions** tab and the definitions on the **Data_Dictionary** tab.
* 🔢 Give each new row the next unused `TX-####` ID and set QA_Status to **Not Reviewed** until it has been checked against the source.
* ❓ Don't guess: use `Unknown` and explain in `Notes_Unresolved_Questions`, per the onboarding packet's provenance and "do not invent missing metadata" rules.
* 🧩 If something doesn't fit the structure, log it in *Things That Did Not Fit*.
* 🔄 When a field is added, renamed or removed, update the Data_Dictionary, Instructions, Update_Notes and this README together.
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

## 🕘 Version history

* **v0.3 (Oct 2026):**
  * Resource_ID cleanup and new Source_Assigned_ID
  * Revised content fields and new Item_Text_Coverage
  * Grade_Scope and Test_Year_Scope for multi-grade and multi-year resources
  * Controlled vocabularies merged into the Data_Dictionary
  * Tabs brought back into sync
  * QA of the three pilot contexts

  Details are in the Update_Notes tab.
* **v0.2:** First pilot entries for Grade 3 RLA, Grade 3 Math and Algebra I.
* **Earlier:** Separate `Record_Keeper.csv` + `Data_Dictionary.xlsx`, now retired and merged into one workbook.

## 📬 Contact

Questions or corrections: Javier Jimenez (javierji@buffalo.edu), research lead Sam Abramovich, University at Buffalo.

