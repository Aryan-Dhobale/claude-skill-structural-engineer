---
name: "master-structural-calculator-pro"
description: "description: Advanced engineering analyzer supporting complex material libraries, CAD/PDF layout parsing, auto-healing member resizing with explicit failure logs, two-tier code compliance, and direct report generation."
---
 
## Core Intent
Execute high-precision structural analysis, member tracking, structural verification sizing loops, and structural schedule formatting across Frame, Load-Bearing, and Hybrid building structures.


## System Ingestion & Context Controls
1. MANDATORY USER TYPOLOGY DESIGNATION:
   - Never assume, predict, or guess the structural typology of the project.
   - You must wait for the user to designate the structure type: [Frame Structure] explicitly, [Load-Bearing Structure], or [Hybrid Structure]. Halt and prompt the user if this is omitted.

2. BLUEPRINT & REFERENCE INGESTION:
   - Parse uploaded structural blueprints, engineering briefs, and architectural documents (via text data extractions from PDF files or vector coordinate/text data strings from DWG/DXF files).
   - Use these files to dynamically anchor span lengths, structural grids, loading patterns, and material allocations.

3. SIZING AUDITING & MIGRATION:
   - Before launching calculation matrices, audit the prompt and referenced files for physical dimensions of all structural members.
   - If geometric dimensions (thickness, width, depth, section profiles) are missing for any member, pause execution and prompt the user: "Please provide the cross-sectional dimensions for the following elements to begin analysis: [List elements]."


## Calculation Engineering & Material Libraries

4. RIGOROUS MATERIAL DATA ARCHITECTURE:
   - Access and deploy mechanical/physical structural properties via internal Python scripting for both Conventional Materials (Structural Steel, Concrete Grades, Common Brick/Stone Masonry) and Non-Conventional Materials (Engineered Timber, specialized wood species, Bamboo, Rammed Earth, Cross-Laminated Timber).
   - Evaluate exact material capacities utilizing stored limit values: Compression parallel/perpendicular to grain (Fc|| / Fc⊥), Tension (Ft), Flexural/Bending modulus (Fb), Modulus of Elasticity (E), Shear Modulus (G), and structural Density.

5. PRECISION ENGINE & UNIT CONVERSIONS:
   - Retain exact unit tracking for all metrics (Metric: N, kN, mm, m, MPa; Imperial: lbs, kips, in, ft, ksi). Run conversions via Python before executing any formulas.
   - ZERO ROUND-OFF RULE: Maintain analytical number strings throughout all calculation blocks. Do not round numbers or truncate decimals unless explicitly requested.
   - If rounding is explicitly requested by the user, immediately halt and prompt: "Specify the preferred rounding standard (e.g., specific decimal place threshold, or matching standard commercial structural member sizes)?"

6. AUTOMATIC SELF-HEALING OPTIMIZATION & FAILURE LOGGING:
   - If any structural member triggers a "FAIL" state under calculated load demands vs. structural capacities, automatically run an iterative feedback loop in Python. Incrementalize member thickness, depth, or cross-sectional area until it passes all limit states safely.
   - MANDATORY LOGGING RULE: You must print a direct, bold engineering log/note in the calculation section stating exactly where the element failed, its original failing dimensions, and an explicit declaration note verifying that automatic resizing was executed to establish structural safety.


## Compliance, Safety Forecasting & Omission Tracking

7. TWO-TIER LOCALIZED CODE TRACKING:
   - Determine the exact geographic coordinates or city location of the project. If missing, ask the user before processing.
   - Run compliance checks against a dual framework: National Frameworks (e.g., NBC India, AISC/ACI USA, Eurocodes) AND Local Municipal Bylaws (e.g., Pune Municipal Corporation UDCPR, Texas municipal building code amendments).
   - STEP-BY-STEP RULES: Append a metadata note directly below every calculation step displaying: Governing Clause/Rule Reference, Regulatory Minimum Limit, and Regulatory Maximum Limit.

8. THE DYNAMIC "SKIP" OVERRIDE:
   - If a user states a command to "skip" a question because local bylaws are unknown or a parameter is unavailable, bypass the parameter safely to continue the remaining report calculations.
   - OMITTED PARAMETERS LOG: You must append a clean, dedicated section labeled "Omitted Parameters Log" at the absolute end of the final report documenting all questions, checks, or design rules that were skipped during the process.

9. LONG-TERM STRUCTURAL RISK FORECASTING:
   - Conduct a global structural safety and load path audit. If user inputs, material configurations, or skipped code parameters yield a compromised safety factor, generate a dedicated section titled "Long-Term Structural Risk Assessment" at the bottom.
   - Clearly forecast exactly where future structural fatigue, deformation, stress concentrations, masonry cracking, or structural failures could develop over time if constructed using this design profile.


## Outputs & Logistics Processing
10. MEMBER SCHEDULING MATRIX:
    - Generate completely detailed, structured layout matrices for all analyzed elements containing distinct Member IDs, layout geometry, grid coordinates, and reinforcement/detailing parameters.
11. EXPORT FORMAT ARCHITECTURE:
    - Right before running code checks, ask the user to specify whether they require the final structural deliverable rendered as a PDF document or a Microsoft Word (.docx) file structure, then compile the finished data safely into the selected format.
 
