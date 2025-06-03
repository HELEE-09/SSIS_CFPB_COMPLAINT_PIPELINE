# SSIS_CFPB_COMPLAINT_PIPELINE

🔗 Download CSV Data (CFPB Complaints)

## 📌 Project Overview
This project involves building a robust **ETL pipeline in SQL Server Integration Services (SSIS)** for integrating data from multiple sources. While working with a complex Data Flow Task, the following error occurred:


This error indicated metadata corruption or mismatches in the internal column tracking system (lineage IDs).

---

## 🧩 Root Cause
SSIS uses **lineage IDs** to track the flow of data columns across components. These IDs can break due to:
- Component or column deletions.
- Manual edits or corrupted package files.
- Improper copy-pasting between tasks.
- Incorrect expressions or data type mismatches.

---

## 🛠️ Fix Summary

We resolved the issue using the following steps:

### 1. Rebuilt the Data Flow Task
- Deleted the broken **Data Flow Task**.
- Re-added **sources, transformations**, and **destinations** manually.
- Ensured **proper column mappings** across components.

### 2. Validated Expressions
- Reviewed all expressions in Derived Column and Conditional Split.
- Ensured correct **data type conversions** to avoid `"Input string was not in a correct format"` errors.

### 3. Cleared Cache & Recompiled
- Rebuilt the SSIS project.
- Cleared Visual Studio cache (`.suo` files).
- Restarted Visual Studio for fresh metadata load.

### 4. Tested Each Component
- Used the **Advanced Editor** to inspect input/output columns.
- Verified metadata lineage to ensure consistent column tracking.

---

## ✅ Final Outcome
After applying the above fixes:
- The Data Flow Task executed successfully.
- All columns processed correctly.
- No runtime errors related to lineage IDs or input formatting.


---

## 🧠 Lessons Learned
- Always **check downstream components** when editing upstream column definitions.
- Avoid **manual editing** of .dtsx files unless absolutely necessary.
- Regularly **validate and test expressions** and data type conversions.

---

## 👤 Maintainer
**Helee Rao**  
B.Tech Final Year Student – Data Engineering | Vadodara  

