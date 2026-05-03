---
layout: project
title: Nutcracker Bending Design
---

# Automated Nutcracker Design — HW4 Update

## Overview

A simple lever nutcracker redesigned to replace manual grip force with a PA-MC1 micro linear actuator. The handles are modeled as flexible beams and designed to keep elastic deflection under 2% of handle length.

---

## Design Parameters

| Parameter | Value |
|---|---|
| Handle length (L) | 150 mm |
| Nut contact position (a) | 30 mm from pivot |
| Nut cracking force required | 300 N |
| Mechanical advantage (L/a) | 5 |
| Required actuator input force | 60 N |
| Max allowable deflection | 3 mm (2% of 150 mm) |

---

## Actuator Selection

**Selected: PA-MC1 IP65 Micro Linear Actuator**

| Spec | Value |
|---|---|
| Voltage | 12 VDC |
| Force output | 8–39 lbs (35–174 N) |
| Stroke | 0.5–8 inch |
| Price | $67.99 USD |

**Justification:** At maximum output (39 lbs = 174 N), the actuator exceeds the required 60 N input force with margin. A 0.5 inch stroke is sufficient for the nut cracking displacement. The compact micro form factor fits the handle geometry.

---

## Part a) Location of Maximum Deflection

### Assumptions
- Each handle is modeled as a simply supported beam
- Actuator applies a point load at x = L = 150 mm
- Nut reaction applies a point load at x = a = 30 mm
- Only transverse force components are considered
- Uniform cross section, linear elastic material

### Analysis

The handle sees three forces:
- Upward pivot reaction at x = 0
- Downward nut force (300 N) at x = 30 mm
- Downward actuator force (60 N) at x = 150 mm

The nut force dominates. Using the standard simply supported beam formula with point load at position a, the location of maximum deflection is:

x_max = a(2L + a) / 3(L + a) = 30(330) / 3(180) = 18.3 mm from pivot

**Maximum deflection occurs at approximately x = 18 mm from the pivot.**

---

## Part b) Beam Cross-Section Design

### Required Moment of Inertia

Using the point load deflection formula with F = 300 N, a = 0.03 m, L = 0.15 m, δ_max = 0.003 m:

δ = Fa²(L−a)² / 3EIL ≤ 0.003 m

EI ≥ 300(0.03)²(0.12)² / 3(0.003)(0.15) = 2880 N·m²

I ≥ 2880 / (69 × 10⁹) = 41,700 mm⁴

### Material

**Aluminum 6061** — E = 69 GPa, high strength-to-weight ratio, easy to machine.

### Cross-Section

**Hollow rectangle** — maximizes I per unit mass (most mass-efficient for bending).

| Dimension | Value |
|---|---|
| Outer width (b) | 20 mm |
| Outer height (h) | 40 mm |
| Wall thickness (t) | 2 mm |

I = (bh³/12) − ((b−2t)(h−2t)³/12) = (20×40³)/12 − (16×36³)/12 = 44,459 mm⁴ ≥ 41,700 ✓

**Cross-section area:** 20×40 − 16×36 = **224 mm²**
vs. solid rectangle: 800 mm² — **72% mass reduction** while meeting deflection limit.

---

## Part c) Final Design Summary

![Nutcracker Design Drawing](/sp26-portfolio-Reece122/assets/images/nutcrackerdrawing-1.png)

| Component | Specification |
|---|---|
| Handle length | 150 mm |
| Material | Aluminum 6061 |
| Cross-section | Hollow rectangle, 20 mm × 40 mm, 2 mm wall |
| Actuator | PA-MC1, 39 lb setting, 0.5 inch stroke |
| Actuator position | x = 150 mm (end of handle) |
| Nut contact position | x = 30 mm from pivot |
| Max deflection | ~3 mm = 2% of handle length ✓ |

---

## References

- [Progressive Automations — PA-MC1 Linear Actuator](https://www.progressiveautomations.com/collections/linear-actuators)
- Appendix E, Case 4 & 6 (textbook beam deflection tables)
