# Phase 3 Plan — Qatar Property Custom Addon Layer

**Bright Information Systems W.L.L** · Odoo 19 Enterprise  
**Workspace:** `projects/qatar_property_phase3_custom_addons/`

---

## Objective

Phase 3 prepares and builds the **Qatar-specific custom addon layer** that extends Odoo official `industry_real_estate`.

| Goal | Detail |
|------|--------|
| **Extend, not replace** | Add Qatar fields, roles, registers, and workflows on official property models |
| **Modular delivery** | Eight focused addons, each independently installable and UAT-tested |
| **Evidence-driven** | Playwright screenshots and use-case docs for every module |
| **Client-ready** | Each module merge requires client UAT sign-off |

---

## Prerequisites (complete)

| Prerequisite | Status | Evidence |
|--------------|--------|----------|
| Phase 1 workflow validation | Done | `bright_property_rental_phase_1` |
| Phase 1.5 architecture decision | Done | Option B — `industry_real_estate` |
| Phase 2 UAT on official workflow | Done | UC-IRE-001 … 009 (8 PASS, 1 PARTIAL) |
| Gap analysis | Done | Qatar fields missing — scope for `qatar_property_base` |
| Phase 3 roadmap | **This document** | Pending review |

---

## Phase 3 scope

### In scope

- Custom addon planning and roadmap (this workspace)
- `qatar_property_base` — first module (Qatar master data, roles, register)
- Subsequent modules per [CUSTOM_MODULE_ROADMAP.md](../CUSTOM_MODULE_ROADMAP.md)
- Playwright UAT per module
- Demo data following industry workflow

### Out of scope (Phase 3 planning stage)

- Actual Odoo Python/XML code (until roadmap approved)
- Phase 1 database migration
- Modifications to `industry_real_estate` source
- Accounting posting overrides

---

## Delivery milestones

| Milestone | Deliverable | Gate |
|-----------|-------------|------|
| **M0 — Planning** | This workspace, roadmap, field matrix, UAT strategy | Roadmap client review |
| **M1 — Scaffold** | `qatar_property_base` empty module structure only | Scaffold review |
| **M2 — Base fields** | Qatar fields on building/unit/partner | Module UAT |
| **M3 — Base register** | Property register report | Module UAT + client sign-off |
| **M4 — Reservation** | `qatar_property_reservation` | Module UAT |
| **M5 — PDC** | `qatar_property_pdc` | Module UAT |
| **M6 — Rent schedule** | `qatar_property_rent_schedule` | Module UAT |
| **M7 — Reports** | `qatar_property_reports` | Module UAT |
| **M8 — Portal** | `qatar_property_portal` | Module UAT |
| **M9 — Kahramaa** | `qatar_property_kahramaa` | Module UAT |
| **M10 — Maintenance** | `qatar_property_maintenance` (optional) | Module UAT |

---

## First module: `qatar_property_base`

Phase 3 development **starts with `qatar_property_base`**.

| Attribute | Detail |
|-----------|--------|
| **Why first** | All other modules depend on it |
| **Models extended** | `x_buildings`, `account.analytic.account`, `res.partner` |
| **First deliverable** | Module scaffold (`__manifest__.py`, security, empty views) |
| **Second deliverable** | Qatar custom fields + property register |

---

## Sandbox strategy

| Sandbox | Purpose |
|---------|---------|
| `qatar_property_industry_uat` | Phase 2 reference — do not modify for Phase 3 dev |
| `qatar_property_phase3_dev` | New isolated DB for custom addon development (create when M1 starts) |

---

## Timeline estimate

| Module | Duration | Cumulative |
|--------|----------|------------|
| Planning (M0) | 1 week | Week 1 |
| `qatar_property_base` | 4–6 weeks | Weeks 2–7 |
| `qatar_property_reservation` | 2–3 weeks | Weeks 8–10 |
| `qatar_property_pdc` | 3–4 weeks | Weeks 11–14 |
| `qatar_property_rent_schedule` | 3–4 weeks | Weeks 15–18 |
| `qatar_property_reports` | 3–4 weeks | Weeks 19–22 |
| `qatar_property_portal` | 3–4 weeks | Weeks 23–26 |
| `qatar_property_kahramaa` | 2–3 weeks | Weeks 27–29 |
| `qatar_property_maintenance` | 2–3 weeks | Optional |

*Estimates assume one developer; parallel work on independent modules may reduce calendar time.*

---

## Review gate

> **No coding starts until this roadmap is reviewed and approved.**
>
> **First coding milestone = module scaffold only** for `qatar_property_base`.

---

## Related documents

- [CUSTOM_MODULE_ROADMAP.md](../CUSTOM_MODULE_ROADMAP.md)
- [MODULE_DEPENDENCY_MAP.md](MODULE_DEPENDENCY_MAP.md)
- [CUSTOM_FIELDS_MATRIX.md](CUSTOM_FIELDS_MATRIX.md)
- [UAT_STRATEGY.md](UAT_STRATEGY.md)
- Phase 2 UAT: https://github.com/Bright-Information-Systems/bright_property_rental_phase_2

---

**Bright Information Systems W.L.L** · June 2026
