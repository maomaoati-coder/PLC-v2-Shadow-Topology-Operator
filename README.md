<div align="center">

# 🔬 Shadow Topology Operator
## `STO · PLC v2 Extension · PCFS Stack`

**A 4-Dimensional Occlusion-State Encoding Primitive for Photonic Logic Chip Architecture**

---

[![DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.20777359-1B3A6B?style=flat-square&logo=zenodo&logoColor=white)](https://doi.org/10.5281/zenodo.20777359)
[![Prior Art](https://img.shields.io/badge/Prior%20Art-Established-1B3A6B?style=flat-square&logo=zenodo&logoColor=white)](https://doi.org/10.5281/zenodo.20777359)
[![Validation](https://img.shields.io/badge/Validation-6%2F6%20PASS-007A3D?style=flat-square&logo=checkmarx&logoColor=white)](#validation-record)
[![PCFS Layer](https://img.shields.io/badge/PCFS-PLC%20v2%20Layer-2E75B6?style=flat-square)](#pcfs-stack-position)
[![Claims](https://img.shields.io/badge/Claims-6%20Technical%20Claims-6A0DAD?style=flat-square)](#technical-claims)
[![License](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0%20%2F%20MGOVL%20v2.0-orange?style=flat-square)](LICENSE)
[![SHA256](https://img.shields.io/badge/SHA256-ba3a546214b363e4...-lightgrey?style=flat-square&logo=shield&logoColor=white)](#validation-record)
<br/>

*毛广辉 Mao Guang Hui · Independent Inventor · maomaoati@gmail.com*  
*Xinzheng, Zhengzhou, Henan, China · June 2026*

</div>

---

## What Is This?

A single physical shadow event — like a solar eclipse — carries **four independently measurable dimensions** of information. Traditional AND/OR gates discard all of it and output only 1 bit. The **Shadow Topology Operator (STO)** captures all four, producing a 4-dimensional continuous vector per operation.

```
Traditional AND/OR gate   →   output ∈ {0, 1}           →  1 bit / operation
Shadow Topology Operator  →   output ∈ R⁴ ∩ [0, 1]⁴    →  >> 1 bit / operation
```

This is proposed as the **PLC v2** layer of the PCFS (Photonic Computing Full Stack): extending the existing PLC v1 angle-encoding architecture with intensity-envelope topology extraction — on the **same liquid-crystal substrate**, with **no new device types**.

---

## Architecture

```
╔══════════════════════════════════════════════════════════╗
║                   PLC v2  (this work)                   ║
║  ┌──────────────────────────────────────────────────┐   ║
║  │  Layer B · Intensity Envelope  (STO · NEW)       │   ║
║  │  Shadow event  →  4D STV  →  gradient compute    │   ║
║  └──────────────────────────────────────────────────┘   ║
║  ┌──────────────────────────────────────────────────┐   ║
║  │  Layer A · Angle Encoding  (PLC v1 · inherited)  │   ║
║  │  Laser incidence angle  →  Boolean logic         │   ║
║  └──────────────────────────────────────────────────┘   ║
║            Same LC substrate · no new devices           ║
╚══════════════════════════════════════════════════════════╝
                          │
              One physical beam carries both channels
                          │
╔══════════════════════════════════════════════════════════╗
║  STV = ( area_ratio,  edge_gradient,                    ║
║          centroid_offset,  ring_metric )  ∈  [0, 1]⁴   ║
╚══════════════════════════════════════════════════════════╝
```

---

## The 4 STV Dimensions

| Dimension | Symbol | Physical Analog | Range | Key Behaviour |
|-----------|--------|-----------------|-------|---------------|
| Blocked energy fraction | `area_ratio` | Eclipse coverage | [0, 1] | 0 = no shadow · 1 = total darkness |
| Boundary sharpness | `edge_gradient` | Umbra-penumbra edge | [0, 1] | Sharp shadow boundary → high value |
| Centroid displacement | `centroid_offset` | Moon off-axis amount | [0, 1] | Asymmetric block → non-zero |
| Annular shape score | `ring_metric` | Annular eclipse ring | [0, 1] | Bright ring + dark centre → → 1.0 |

---

## Validation Results

Six eclipse archetypes simulated · Python/NumPy · Google Colab · Validation v1.1

| Sc# | Scenario | area_ratio | edge_gradient | centroid_offset | ring_metric | Result |
|:---:|----------|:----------:|:-------------:|:---------------:|:-----------:|:------:|
| 1 | 无遮蔽 · No Obstruction | 0.0000 | 0.0317 | 0.0000 | 0.4014 | ✅ PASS |
| 2 | 日全食 · Total Eclipse | 0.9587 | 0.0005 | 0.0082 | 0.0000 | ✅ PASS |
| 3 | 日偏食 · Partial Eclipse | 0.3080 | 0.0462 | **0.3595** | 0.6002 | ✅ PASS |
| 4 | 日环食 · Annular Eclipse | 0.1404 | 0.0586 | 0.0001 | **1.0000** | ✅ PASS |
| 5 | 偏心环食 · Offset Annular | 0.1347 | 0.0566 | 0.0564 | 0.7092 | ✅ PASS |
| 6 | 双影叠加 · Dual Shadow | 0.3496 | 0.0639 | 0.0002 | 0.6850 | ✅ PASS |

**All 6/6 PASS · Minimum inter-scenario Euclidean distance: `0.2236` (Sc5 ↔ Sc6)**  
All six archetypes are mutually distinguishable in 4D STV space.

> 📌 **Key finding:** Sc4 Annular Eclipse achieves `ring_metric = 1.000` — a natural physical implementation of a **Laplacian edge-detection operator** without any multiply-accumulate unit.

---

## Technical Claims

### Claim 1 *(Independent)* — Shadow Topology Operator: Core Method

A photonic computing method that extracts a four-dimensional Shadow Topology Vector

```
STV = { area_ratio, edge_gradient, centroid_offset, ring_metric } ∈ [0, 1]⁴
```

from a single physical light-occlusion event, such that information content per operation substantially exceeds one binary bit.

---

### Claim 2 — Scenario Distinguishability

*Depends on Claim 1.* Six occlusion archetypes (No Obstruction, Total Eclipse, Partial Eclipse, Annular Eclipse, Offset Annular, Dual Shadow) are mutually distinguishable in the 4D STV space with minimum Euclidean distance ≥ 0.22 (simulated: **0.2236**).

---

### Claim 3 — Laplacian Mapping & Edge-AI Application *(merged from original Claims 3 + 8)*

*Depends on Claim 1.* When `ring_metric > 0.55`, the shadow topology is mathematically equivalent to a **discrete Laplacian edge-detection kernel** — a second-order differential structure with bright boundary and dark centre — realised without any multiply-accumulate unit. This enables multiplication-free photonic edge-AI inference acceleration.

---

### Claim 4 — Asymmetric Occlusion Recognition

*Depends on Claim 1.* The `centroid_offset` dimension separates axisymmetric occlusions (`centroid_offset ≈ 0`, e.g. Scenario 4) from non-axisymmetric occlusions (`centroid_offset > 0`, e.g. Scenarios 3, 5), providing **direction-aware sensing** in a single measurement event.

---

### Claim 5 — Dual-Source Superposition Identification

*Depends on Claim 1.* Dual-source superposed occlusion (Scenario 6) produces a distinct STV signature — validated at `(area_ratio = 0.3496, ring_metric = 0.6850)` — separable from all single-source archetypes, enabling multi-source field identification from one shadow event.

---

### Claim 6 *(Independent)* — PLC v2 Architecture: Dual-Layer Encoding *(merged from original Claims 6 + 7)*

A Photonic Logic Chip v2 (PLC v2) realised on the same liquid-crystal thin-film substrate as PLC v1, comprising:

- **(a) Angle-encoding layer** *(inherited)*: laser incidence angle encodes Boolean logic states for precise discrete computation
- **(b) Intensity-envelope layer** *(new)*: shadow topology vector STV extracted from beam intensity distribution for gradient continuous computation

Both layers share the same physical device without adding new device types, increasing per-unit information density from **1 bit → 4D continuous vector**.

---

## Validation Record

```
Simulation : PLC Shadow Topology Operator (STO) Validation v1.1
Author     : 毛广辉 Mao Guang Hui  maomaoati@gmail.com
GitHub     : github.com/maomaoati-coder
Timestamp  : 2026-06-19T00:33:37.828854Z
Verdict    : ALL PASS  (6/6)
SHA256     : ba3a546214b363e4ba6695fab7b188637e6e75d498a383d37c2a04f8742a6c26
```

> The SHA256 hash is computed from JSON-serialised simulation output including all six STV measurements, pass/fail status, author, and UTC timestamp. It constitutes an immutable prior art timestamp.

---

## PCFS Stack Position

| Layer | Name | Function | DOI |
|-------|------|----------|-----|
| PLC v1 | Photonic Logic Chip | Boolean logic via LC beam angles | [10.5281/zenodo.19801651](https://doi.org/10.5281/zenodo.19801651) |
| PSM | Photonic State Memory | LC angular bistability storage | [10.5281/zenodo.20603456](https://doi.org/10.5281/zenodo.20603456) |
| PEOS | Photonic Emergence OS | OS functions via photonic physics | [10.5281/zenodo.20603667](https://doi.org/10.5281/zenodo.20603667) |
| **PLC v2 / STO** | **This work** | **Intensity-envelope topology extension** | *(Zenodo DOI pending)* |

PLC v2 does not replace PLC v1. Both operate simultaneously on the same LC substrate — angle encodes discrete logic (PLC v1), intensity topology encodes continuous gradient information (STO). Two orthogonal channels, one physical medium.

---

## How to Reproduce

```bash
# Google Colab — Python / NumPy only, no extra installs
# Copy validation code from: plc_sto_validation_v1.html + plc_sto_v1_1_patch.html
# Run all cells in order
# Final output:
#   FINAL RESULT: 6/6 PASS
#   SHA256: ba3a546214b363e4ba6695fab7b188637e6e75d498a383d37c2a04f8742a6c26
```

Key simulation parameters:

| Parameter | Value |
|-----------|-------|
| Grid size | 256 × 256 px |
| Beam waist σ | 40 px |
| Beam centre | (128, 128) |
| Inner zone radius | 0.45 × σ = 18 px |
| Ring zone outer | 1.30 × σ = 52 px |
| edge_gradient norm | 0.35 |
| centroid_offset norm | GRID × 0.12 |

---

## Zenodo Upload Instructions

> Upload the `.docx` paper to [zenodo.org](https://zenodo.org) as a **Technical Note** to obtain a citable DOI.

### Step-by-Step

**1. Create account / log in**
→ `zenodo.org` → Sign in with GitHub (recommended: links to `maomaoati-coder`)

**2. New Upload**
→ Click `+ New Upload` (top right)

**3. Upload file**
→ Drag and drop `plc_v2_sto_prior_art.docx`  
→ Wait for upload to complete

**4. Resource type**
→ Select **Publication** → **Technical note**

**5. Fill in metadata**

| Field | Value |
|-------|-------|
| Title | Shadow Topology Operator (STO): A 4-Dimensional Occlusion-State Encoding Extension for Photonic Logic Chip Architecture (PLC v2) |
| Authors | Mao, Guang Hui |
| Author affiliation | Independent Inventor |
| Author ORCID | *(leave blank or add if registered)* |
| Description | Prior art technical paper for the Shadow Topology Operator (STO), a 4-dimensional occlusion-state encoding primitive extending PLC v1 to PLC v2 within the PCFS (Photonic Computing Full Stack) architecture. Includes 6 merged technical claims and simulation validation SHA256: ba3a546214b363e4ba6695fab7b188637e6e75d498a383d37c2a04f8742a6c26. Validated 6/6 PASS with minimum inter-scenario Euclidean distance 0.2236. |
| Version | 1.0 |
| Language | English |
| Date | 2026-06-19 |

**6. Keywords** *(enter each separately)*
```
photonic computing
shadow topology operator
occlusion state encoding
PLC v2
PCFS
edge AI
Laplacian operator
liquid crystal
prior art
independent inventor
```

**7. License**
→ Select **Creative Commons Attribution Non Commercial No Derivatives 4.0 International**

**8. Related identifiers** *(add prior art chain)*

| Relation | Identifier |
|----------|------------|
| Is supplement to | `10.5281/zenodo.19801651` (PLC v1) |
| Is supplement to | `10.5281/zenodo.20603456` (PSM) |
| Is supplement to | `10.5281/zenodo.20603667` (PEOS) |

**9. Additional notes**
```
Validation simulation: Python/NumPy, Google Colab, 2026-06-19
Validation SHA256: ba3a546214b363e4ba6695fab7b188637e6e75d498a383d37c2a04f8742a6c26
GitHub repository: github.com/maomaoati-coder
```

**10. Publish**
→ Click **Save** → Click **Publish**  
→ DOI will be assigned immediately: `10.5281/zenodo.XXXXXXX`  
→ **Copy the DOI** and update the badge at the top of this README

---

## License

```
Copyright © 2026 毛广辉 Mao Guang Hui

Dual-licensed:
  CC BY-NC-ND 4.0    — Creative Commons Attribution Non-Commercial No-Derivatives
  MGOVL v2.0         — Mao Guang Hui Open Vision License v2.0

Commercial use, reproduction, or modification requires explicit written permission.
Academic citation and non-commercial reference permitted with attribution.
```

---

<div align="center">

*Shadow Topology Operator (STO) · PLC v2 · PCFS Stack*  
*毛广辉 Mao Guang Hui · 2026*  
[![GitHub](https://img.shields.io/badge/GitHub-maomaoati--coder-181717?style=flat-square&logo=github)](https://github.com/maomaoati-coder)

</div>
