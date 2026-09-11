# RCA of Recurrent Main-Shaft Rear Bearing Failure — SG G132, Northeast Brazil
## Plan v2 (Draft)

**Status:** Pre-bid planning draft. No contract, no budget assigned.
**Component:** Main-shaft rear (gearbox-side) bearing, 231/630 spherical roller bearing (SRB).
**Fleet:** Siemens Gamesa G132 (geared + DFIG), ~10–12 rpm rotor, Northeast Brazil.

---

## 0. Revision history
- v0.1: Initial plan (OpenFAST → Abaqus assumed as core).
- v1 (Amendment 01): Added crack-initiated failure pathway (no visible grease alteration).
- v1 (Amendment 02): Added 4-point arrangement and axial-freedom consideration.
- v2: Configuration locked from OEM manual. Rear 231/630 confirmed as **locating/axially fixed** (thrust carrier), failing; front 230/900 **non-locating**, reportedly clean. **Thrust-driven downwind-row overload is now the primary hypothesis.**

---

## 1. Problem statement
The main-shaft **rear (gearbox-side) 231/630 SRB** fails across the G132 fleet at approximately **every 1.5 years**, versus a design life target far longer. Failures are **fleet-wide and similar**, indicating a common-mode cause. Observed damage spans **two pathways**:
- **Pathway 1 (surface-initiated):** micropitting → macropitting → spalling → catastrophic.
- **Pathway 2 (crack-initiated):** a crack develops **with no visible alteration of the grease**, potentially progressing to catastrophic failure.

A bearing-manufacturer countermeasure (grease regime changed from OEM **12 months / 5000 g** to **6 months / 10 000 g**, using Klüberplex BEM 41-141) was applied **after** failures began and did not resolve them.

## 2. Objective and scope
**Objective:** determine *why the rear bearing fails far more often than expected* and recommend the *most cost-effective corrective action*.

**In scope:** rotor → main shaft → rear locating bearing load path; thrust and combined loading; lubrication; site/design basis; operational duty; installation/alignment; material evidence; corrective options.
**Out of scope (unless it emerges):** gearbox-internal and generator bearings; blades/tower/pitch/yaw; electrical drivetrain integrity (screened only as a bearing-current contributor).

This is a **Root Cause Analysis (RCA)**, not a design/verification study. OpenFAST, Abaqus and similar tools are supporting instruments, not the deliverable.

## 3. Asset and component configuration (locked)
| Position | Bearing | Series role | Axial role | Status |
|---|---|---|---|---|
| Front (rotor side) | **230/900** (bore 900 mm) | 230 — radial-oriented, lower axial capacity | **Non-locating** (axially free) | Reportedly undamaged |
| Rear (gearbox side) | **231/630** (bore 630 mm) | 231 — wider series, higher axial capacity | **Locating / axially fixed (thrust carrier)** | **Failing** |

- Drivetrain topology: **four-point suspension** (two main bearings + gearbox torque arms).
- Both bearings are **spherical roller bearings (SRB)**, **sealed variants**, with **heat treatment (specification not disclosed)**.
- Rotor speed ~**10–12 rpm** (very low; marginal lubricant film).

**Key consequence:** the failing rear bearing is the **locating bearing that reacts rotor thrust**, placing it in the documented failure syndrome for symmetric SRBs under high thrust.

## 4. Known facts and available data
| Item | Status |
|---|---|
| Rear bearing | 231/630 SRB, locating, sealed; failing |
| Front bearing | 230/900 SRB, non-locating; reportedly clean |
| Failure modes | micropitting/macropitting/spalling/catastrophic, and crack without grease alteration |
| Reliability | ~1.5 years, fleet-wide, NE Brazil |
| Lubrication | Klüberplex BEM 41-141; OEM 12 mo / 5000 g; changed to 6 mo / 10 000 g post-onset |
| SCADA | 10-min: temperatures, wind speed/direction, pitch, electrical, nacelle vibration; **no accelerometer** |
| Bearing temperature | Historical data not available |
| Grease samples | Collected; lab results pending; inconsistent visual residue |
| Photos | Exist; not yet released |
| OEM docs | Load certificate, drivetrain drawings, grease spec stated as obtainable |
| Site wind | **Met-mast data expected** (Brazilian regulated-market requirement) |
| LiDAR / strain gauges | None |
| IEC class / load certificate | Not yet retrieved |
| Heat treatment spec | Not shared |

## 5. Design basis and the site-suitability question
Leading common-mode hypothesis: the **site exceeds the turbine's certified design envelope** ("not tropicalized"), raising the thrust/fatigue loading beyond what the bearing was sized for. Testing requires both sides:
- **Design side:** certified **IEC 61400-1 class** (Type Certificate) + **OEM load certificate** (design thrust/radial/moment and governing DLCs).
- **Site side:** **met-mast** turbulence intensity, gust, shear, veer, air density vs. class assumptions.

"Tropicalization" also includes thermal, humidity, salt/dust and grid axes, which are screened in parallel.

## 6. Failure modes
Two pathways must be distinguished by physical evidence:
1. **Surface-initiated** (micropitting → macropitting → spalling): driven by mixed/boundary lubrication, sliding, and uneven row loading.
2. **Crack-initiated** (no grease alteration): suggests subsurface/structural initiation (e.g., white etching cracks, subsurface fatigue, ring cracking) and is not excluded by clean grease.

## 7. Working hypotheses
**Primary**
- **H1 — Thrust-driven downwind-row overload:** symmetric 231/630 SRB in the locating position under high axial/radial ratio; downwind row overloaded, upwind row prone to skidding; marginal film at 10–12 rpm → micropitting/spalling. Supported by industry evidence for locating SRB main bearings.

**Secondary**
- **H2 — Site/design mismatch:** actual TI/gust/shear/air-density exceeds certified class → thrust spectrum above design.
- **H3 — Lubrication regime:** correct grease, but contact starvation at low speed; the over-greasing countermeasure on a **sealed** bearing may cause churning, seal rupture and contamination (not the origin, since failures pre-dated it).
- **H4 — Load sharing / misalignment / bedplate flexibility:** alters Fa/Fr and row loading; elastic surroundings can change roller loads substantially.
- **H5 — Material / subsurface:** heat treatment unspecified; subsurface defects/WEC pathway remains open.
- **H6 — Electrical / thermal / contamination:** screened; lower priority for a main bearing but retained.

## 8. Work plan (decision-gated)
**Stage 0 — Mobilization & design basis (2–3 weeks)**
- Confirm component/arrangement and the lube-change timeline vs. failure onset.
- Retrieve Type Certificate, OEM load certificate, met-mast data, grease reports, photos, drawing details (seal/purge, fits, heat treatment).
- Build fleet failure/asset database.
- **Gate G0:** data access secured; design basis established.

**Stage 1 — Data-driven diagnosis (4–6 weeks) — in-house core**
- SCADA analytics: duty, stops/idling, pitch/torque variability, thermal trends (where available).
- Fleet Weibull and the lubrication countermeasure counterfactual (failure rate before vs. after).
- Site screening: met-mast TI/shear/gust/density vs. certified class.
- FTA/FMEA; update hypothesis ranking.
- **Gate G1:** is the load branch strong enough to justify Stage 2? Are physical samples/teardown warranted?

**Stage 2 — Thrust/load & site-suitability assessment (conditional, 6–10 weeks)**
- Extract thrust/radial/moment spectrum from the OEM load certificate; compare site conditions to IEC class.
- Use OpenFAST only if the turbine model is obtainable; otherwise request OEM site-specific reassessment.
- Abaqus for bedplate/housing flexibility and local stress; feed boundary stiffness into the bearing model.
- **Gate G2:** quantified load exceedance / governing load case.

**Stage 3 — Physical failure evidence (conditional, parallel, 4–8 weeks) — subcontract**
- Teardown + SEM/EDX: identify damage location (downwind vs. upwind row; azimuth), surface vs. subsurface initiation, WEC/inclusions/fracture.
- Grease lab: FTIR oxidation, ICP (Fe/Cu/water), particle count, ferrography, consistency.
- **Gate G3:** dominant damage mechanism confirmed.

**Stage 4 — Bearing internal-load, lubrication & life (conditional, 6–10 weeks) — subcontract/partner**
- Bearing internal-load model (Romax/Masta/KISSsoft/BEARINX or MBD) for combined Fa/Fr + moment → two-row distribution, contact stress.
- EHL/film assessment (κ, Λ) at actual speed/temperature; ISO 281 / ISO/TS 16281 life + surface/subsurface criteria.
- Translate Stage 2 loads into predicted life; compare to ~1.5 years.

**Stage 5 — Root-cause synthesis & corrective action (4–6 weeks)**
- Rank surviving causes with evidence and confidence.
- Corrective options: asymmetric SRB / axially-optimized wind SRB retrofit; alignment/bedplate; lubrication strategy and sealing; thrust/control strategy (derating/sector management); monitoring (PT100/CMS).
- Business case, pilot plan, monitoring KPIs, verification.

## 9. Tools and software
| Tool | Role | Status |
|---|---|---|
| Python/pandas, Weibull/reliability | SCADA analytics, duty, fleet statistics | **In-house — lead** |
| IEC 61400-1 comparison | Site vs. design class | In-house |
| OpenFAST + TurbSim | Site-specific thrust/load cases | **Conditional** — only if turbine model available |
| Abaqus | Bedplate/housing flexibility, local stress | In-house, conditional |
| Bearing internal-load software (Romax/Masta/KISSsoft/BEARINX or MBD) | Roller loads, two-row split, contact stress | **Subcontract** |
| EHL / ISO 281/16281 + surface/subsurface criteria | Film, life | **Subcontract** |
| Grease/metallurgy lab | Mechanism confirmation | **Subcontract** |
| CBM/vibration | Duty and precursor monitoring | Optional, subcontract |

**Verdict:** the analytical spine is **evidence (data + teardown/grease) plus a bearing internal-load/life step**. OpenFAST and Abaqus are adjuncts. If the OEM load certificate is obtained, OpenFAST's role largely disappears.

## 10. Data request checklist
| Data | Holder | Enables |
|---|---|---|
| Type Certificate / IEC class | Certification body / OEM | Design envelope |
| OEM load certificate + drivetrain drawings | OEM/client (NDA) | Design loads, geometry, fits |
| Met-mast data (TI, shear, gust, veer, density, long term) | Client/developer | Site vs. design |
| SCADA full tags (incl. std/min/max if stored) | Client | Duty, temperature, proxies |
| Grease sample reports | Client/O&M | Lubrication evidence |
| Failed-bearing photos / teardown access | Client/OEM | Mechanism |
| Work orders, replacement history, batch records | Client | Fleet reliability, materials |
| Rear-bearing seal/purge arrangement and exact designation suffix | OEM | Over-greasing/seal interaction |
| Heat-treatment specification | OEM/bearing maker | Subsurface/WEC branch |
| Front 230/900 condition records | Client/O&M | Control comparison |

## 11. Team, roles, and partner model
| Role | Source |
|---|---|
| Program lead / RCA facilitator / data science | **In-house (electrical eng)** |
| Structural FE (bedplate/housing, load cases) | **In-house (civil eng)** |
| Main-bearing / tribology specialist | **Partner** |
| Bearing internal-load + life analysis | **Partner/subcontract** |
| Grease + metallurgy lab | **Subcontract** |
| CBM/vibration | Optional subcontract |
| OEM liaison | In-house + partner |

**Fit assessment:** in-house competently covers SCADA analytics and structural FE. **Bearing/tribology, life analysis and lab work must be partnered.** CFD expertise is not central. The bid should be written as a **partner-supported, data-first RCA**.

## 12. Deliverables
1. Stage 1 diagnostic report (ranked hypotheses + design-basis screen).
2. Data/fault-tree package and evidence register.
3. Load/site-suitability assessment (Stage 2, conditional).
4. Physical-evidence report (Stage 3).
5. Bearing load/life analysis (Stage 4).
6. Final RCA + corrective-action business case + monitoring plan (Stage 5).

## 13. Timeline and indicative effort
- Overall **4–6 months**; Stage 1 standalone in **4–6 weeks**.
- Effort **~8–13 person-months** plus subcontracts (bearing analysis, lab, optional CBM).
- Bid structured as **three priced tiers**: (A) data-driven RCA; (B) + physical/lab; (C) + load simulation and/or field instrumentation.

## 14. Risks, assumptions, exclusions
- **Conflict of interest:** bearing maker recommended the failed countermeasure; maintain independence.
- **OEM data dependency:** load certificate/turbine model may be gated; make access a precondition.
- **Locating/non-locating role** is now confirmed, but **heat treatment and seal/purge details are unknown**.
- **Micropitting / subsurface cracking are partly research-grade:** deliver evidence-ranked causes, not a guaranteed single root cause.
- **No accelerometer / no high-rate data / no bearing temperature:** transient and precursor evidence limited; may require optional measurement.
- **Met-mast is a point measurement:** spatial representativeness must be stated.
- Excludes gearbox/generator and non-drivetrain failure modes.

## 15. Bid positioning
"Independent, data-first RCA — answers from the SCADA and met-mast data the operator already owns within weeks, then targets only the physical and simulation work that matters." Lower cost/risk than simulation-first bids; honest about specialist partnering.

## 16. Open items / decisions needed
1. Accept the **staged/tiered bid structure**.
2. Confirm willingness to **partner/subcontract** bearing + tribology + lab (named partner or us to specify the SoW).
3. Does SCADA retain **std/min/max** tags for wind speed/direction?
4. Obtain **IEC class, OEM load certificate, met-mast data, rear-bearing seal/heat-treatment details, front-bearing condition**.
5. Define file name and version control for this document.
