# Operational Framework: Data Cleansing & Normalization Methodology for 100k+ Incident Sheets

## 1. Executive Summary
Handling transaction and payment dispute records at scale requires a highly disciplined data processing approach. When logging pipelines capture messy end-user data, operational risk teams face fragmented strings, missing merchant identifiers, and mismatched time zone signatures. 

This framework details the algorithmic steps deployed within Microsoft Excel to aggregate, normalize, and audit **100,000+ raw dispute entries**, optimizing internal compliance response speeds and guaranteeing data consistency for regulatory tracking.

---

## 2. Step-by-Step Data Cleansing Pipeline

### Step 1: Structural Integrity & Schema Definition
Raw dispute data extracted from isolated clearing systems is consolidated into a single unified workspace. Initial processing forces explicit schema validation:
* **Unique Key Isolation:** Checking `Dispute_ID` signatures using conditional formatting patterns (`COUNTIF` arrays) to extract and eliminate accidental transmission duplicates.
* **Format Hardening:** Converting chaotic unstructured alphanumeric fields into distinct types: Date/Time stamps (`YYYY-MM-DD HH:MM:SS`), numeric transaction volume baselines (`EUR`), and categorical risk labels.

### Step 2: Complex String Manipulation & Normalization
Merchant descriptors and payment channel nodes often contain systemic noise (e.g., mismatched casing, trailing whitespaces, transaction processing system codes). To prevent aggregation fragmentation, the following formula workflow is executed:
* **Whitespace Pruning:** Deployed `TRIM` and `CLEAN` functions to eliminate hidden non-printable server characters breaking reference lookups.
* **Entity Standardization:** Utilized advanced text isolation formulas via nested `MID`, `SEARCH`, and `LOWER` statements to pull core merchant identifiers out of raw transaction descriptions.

### Step 3: Resolving Missing Metrics & Data Imputation
Incomplete logs can severely skew monthly risk indicators. Blank cells within critical tracking fields are addressed systematically:
* **Missing Value Imputation:** For missing transaction currencies or regional code tags, optimized conditional arrays (`IF`, `ISBLANK`, and `XLOOKUP` matrices) automatically query master client directories to back-fill critical metadata based on matching account histories.
* **Error-Handling Architecture:** Wrapped every active cross-sheet lookup logic layer inside robust `IFERROR` statements, forcing unmapped parameters to resolve into a distinct, actionable categorical alert flag (`"AUDIT_REQUIRED"`), completely preventing broken calculated cells.

---

## 3. Analytical Aggregation & Auditing Framework
Once the dataset reaches a hardened, fully clean state, calculation layers compile high-level operational statistics:
1. **Dynamic Risk Cohorts:** Building optimized Pivot Tables leveraging grouped time hierarchies to track changes in fraud and dispute types across continuous multi-month windows.
2. **Velocity Threshold Tracking:** Applying comprehensive multi-criteria lookup parameters (`INDEX` and `MATCH` / `SUMIFS`) to isolate specific transaction paths exhibiting abnormal dispute volumes, instantly flagging high-risk nodes for executive risk reviews.

---
*Developed by Yegor Litvinov (Risk Data Analyst).*
