---
name: "master-structural-calculator-pro"
description: "Advanced engineering analyzer supporting complex material libraries, Revit/CAD/PDF layout parsing, smart defaults with hard triggers, top-down load paths, auto-healing member resizing with revision logs, foundation triggers, serviceability checks, rebar anchorage, and progressive disclosure deliverables."
---

## Core Intent
Execute high-precision structural analysis, member tracking, structural verification sizing loops, deep/shallow foundation selection, serviceability limit state checks, and structural schedule formatting across Frame, Load-Bearing, and Hybrid building structures.

---

## 1. Low-Friction Intake, Smart Defaults & Ingestion Pipeline

1. **Unified Low-Friction Intake:**
   - Prompt the user with a single configuration line to eliminate questionnaire fatigue: `[Typology (Frame / Load-Bearing / Hybrid), Location / Code, File Upload (.rvt / .dwg / .pdf)]`.
   - Never assume structural typology; wait for explicit designation.

2. **Smart Defaults with Hard Safety Triggers:**
   - Default unstated units, safety margins, and advanced secondary checks (Embodied Carbon, Thermal/Shrinkage) to standard engineering baselines.
   - **Hard Safety Trigger Override:** If uploaded file metadata or user inputs indicate a building height $> 15\text{ m}$ or a structural span $> 20\text{ m}$, Smart Defaults must auto-override and force-enable wind, seismic, and thermal checks with explicit notification to the user.

3. **Explicit BIM & File Ingestion Protocols:**
   - Ingest structural data via CAD (`DWG/DXF`), PDF text extractions, and Revit (`.rvt`) data.
   - **Revit Ingestion Rule:** Revit `.rvt` spatial data processing requires structured spatial extracts (IFC, tabular schedules, or vector coordinate text strings) to prevent binary parsing failures.
   - **File Metadata Auto-Extraction:** Automatically read embedded units, scaling, and coordinate systems from digital uploads.
   - **Grid-Line Auto-Interpolation Audit:** If member tags are missing from blueprints *but* coordinate grid lines exist, auto-generate temporary alphanumeric grid identifiers (e.g., Grid A-1, B-2) to map elements instantly without blocking execution.

4. **Mandatory Initial Intake Toggles (Advanced Modules):**
   - During initial setup, explicitly ask the user whether to toggle ON/OFF:
     - **Embodied Carbon Tracking (GWP)**
     - **Thermal & Shrinkage Stress Verification (Expansion Joints)**
   - If toggled ON, these are integrated directly into the core calculation loops. If omitted, they remain inactive unless requested via the post-calculation menu (which triggers a supplementary calculation pass).

5. **Dimension Auditing & Pause Rule:**
   - Audit inputs for physical dimensions. If cross-sectional sizes are missing and cannot be interpolated, pause execution and prompt the user for missing dimensions.

---

## 2. Calculation Engineering, Load Paths & Material Libraries

6. **Rigorous Material Data Architecture:**
   - Access mechanical/physical properties for Conventional Materials (Structural Steel, Concrete Grades, Masonry) and Non-Conventional Materials (Engineered Timber, Bamboo, CLT).
   - Evaluate exact material capacities: Compression (Fc|| / Fc⊥), Tension (Ft), Flexural modulus (Fb), Modulus of Elasticity (E), Shear Modulus (G), and structural Density.

7. **Top-Down Gravitational Load Path Sequence:**
   - Strictly process gravitational loads top-down: Roof Slab $\to$ Beams $\to$ Columns $\to$ Floor Slab $\to$ Plinth $\to$ Footing.

8. **Precision Engine & Unit Conversions:**
   - Retain exact unit tracking (Metric: N, kN, mm, m, MPa; Imperial: lbs, kips, in, ft, ksi). Run conversions via Python before executing formulas.
   - **Zero Round-Off Rule (Calculation Phase):** Maintain analytical number strings throughout all internal sizing and optimization loops. Do not round numbers during calculations.

9. **Phase-Separated Conservative Calculation Rounding:**
   - Execute sizing loops on exact analytical values first. 
   - Apply conservative calculation rounding (loads up, dimensions/spans down) only as a final calculation safety pass *after* exact optimization.

10. **Explicit Load Sustainability Argument & Multi-Pass Verification:**
    - Formulate a direct computational argument verifying whether each member sustains applied load demands without failure.
    - Internally recheck calculation workflows and mathematical outputs **2–3 times** to ensure complete accuracy.

---

## 3. Optimization, Foundation Selection & Serviceability

11. **Iterative Self-Healing Optimization & Revision Tracker:**
    - If any structural member triggers a "FAIL" state, run an iterative Python feedback loop, incrementally resizing members until safe.
    - **Slim-Down Optimization:** Automatically resize excessively strong (over-powered) members down to optimal dimensions.
    - **Revision Tracking:** Automatically append revision logs tracking optimization loops (`Rev 01`, `Rev 02`, etc.) for professional audit traceability.
    - **Mandatory Logging:** Print a direct engineering log stating element location, original dimensions, failure notes, and resizing results.

12. **Automated Shallow vs. Deep Foundation Triggers:**
    - Automatically evaluate superstructure loads against soil bearing capacity. 
    - If total loads exceed bearing capacity or building height exceeds $15\text{ m}$, automatically trigger deep foundation checks (friction/end-bearing pile groups and pile caps) instead of standard isolated/mat footings.

13. **Serviceability Limit State (Deflection & Crack Widths):**
    - Mandate explicit checks for immediate and long-term span deflections (e.g., $\text{Span}/250$) and maximum allowable crack widths under service loads.

14. **Rebar Anchorage, Development Length & Joint Congestion:**
    - Calculate required development lengths ($L_d$), hook anchorages, and lap splices for reinforcement.
    - Execute beam-column joint shear and rebar congestion checks to ensure constructibility and prevent pour blockages on site.

15. **Conditional Clash Detection:**
    - Scan spatial BIM data for geometric clashes and reinforcement congestion **strictly when Revit files (`.rvt`) / IFC schedules are provided**.

---

## 4. Compliance, Safety Forecasting & Omissions

16. **Two-Tier Localized Code Tracking:**
    - Determine exact project coordinates or city location. Run compliance checks against National Frameworks (e.g., NBC, AISC/ACI, Eurocodes) and Local Municipal Bylaws.
    - Append metadata below every calculation step: Governing Clause Reference, Regulatory Minimum Limit, and Regulatory Maximum Limit.

17. **Dynamic "Skip" Override & Omitted Parameters Log:**
    - Allow safe bypass of unknown rules if requested by the user. 
    - Append a dedicated section labeled "Omitted Parameters Log" at the end of the report documenting all skipped items.

18. **Long-Term Structural Risk Forecasting:**
    - If skipped code parameters or extreme configurations yield compromised safety margins, generate a "Long-Term Structural Risk Assessment" section detailing potential fatigue, deformation, and stress concentration risks.

---

## 5. Progressive Disclosure Deliverables & Drafting Logistics

19. **Post-Calculation Menu (Progressive Disclosure):**
    - Immediately after calculations finish, present a clean menu asking the user:
      - **Deliverable Scope:** Report, Structural Drawings, or Both.
      - **Advanced Add-Ons:** Bill of Quantities (BoQ) vs. Bill of Materials (BoM), and Embodied Carbon Report.

20. **Drawing-Specific Unit Customization & Drafting Layer:**
    - When drawings are requested, explicitly prompt for on-site drafting units (inches, feet, cm, mm) isolated from calculation math.
    - **Practical Drafting Round-Off (Multiples of 5):** Apply a separate drawing rendering layer to round off rebar spacings and dimensions to clean multiples of 5 (e.g., $173.84\text{ mm} \to 175\text{ mm}$ or $180\text{ mm}$ c/c) for field workers without altering core calculation math.

21. **Member Scheduling Matrix & Multi-Format Export:**
    - Generate structured layout matrices containing Member IDs, grid coordinates, and reinforcement details.
    - Export final reports (`PDF` or `DOCX`) and structural drawings (`DWG`, `DXF`, `PDF`) on command.
