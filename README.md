# Master Structural Calculator Pro (V2)

Advanced engineering analyzer supporting complex material libraries, Revit/CAD/PDF layout parsing, smart defaults with hard triggers, top-down load paths, auto-healing member resizing with revision logs, foundation triggers, serviceability checks, rebar anchorage, and progressive disclosure deliverables.

## Core Capabilities

- **Unified Low-Friction Intake:** Single-line configuration (`Typology`, `Location`, `File Upload`) eliminating setup bottlenecks.
- **Smart Defaults & Hard Safety Triggers:** Intelligent zero-prompt fallbacks with automated overrides that force-enable wind, seismic, and thermal checks if building height exceeds 15m or spans exceed 20m.
- **BIM & File Ingestion Protocols:** Structured spatial extract parsing (IFC, schedules, coordinate text) for Revit (`.rvt`) files, CAD blueprints, and PDF extractions, complete with grid-line interpolation.
- **Top-Down Gravitational Load Paths:** Strict calculation hierarchy processing loads downward from roof slabs to footings.
- **Precision & Phase-Separated Rounding:** Exact float calculations during internal optimization loops, followed by a conservative safety pass and practical drafting round-offs to clean multiples of 5 (c/c).
- **Iterative Self-Healing Optimization & Revision Tracking:** Automated resizing loops that fix failing members and slim down over-designed elements, tracked via audit logs (`Rev 01`, `Rev 02`).
- **Advanced Engineering Modules:**
  - Automated shallow vs. deep foundation triggers.
  - Serviceability limit state checks (deflections and crack widths).
  - Rebar anchorage, development lengths ($L_d$), and lap splices.
  - Beam-column joint shear and congestion checks.
- **Localized Code Compliance:** Two-tier tracking against national frameworks (NBC, AISC/ACI, Eurocodes) and local municipal bylaws, complete with an Omitted Parameters Log.
- **Progressive Disclosure & Multi-Format Export:** Post-calculation menus for optional deliverables (BoQ/BoM, Embodied Carbon reports) and exports in PDF, DOCX, DWG, or DXF formats.
