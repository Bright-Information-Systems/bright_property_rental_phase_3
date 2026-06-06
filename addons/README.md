# Addons Directory

**Bright Information Systems W.L.L** · Qatar Property Phase 3

---

## Purpose

This directory will contain all **custom Odoo modules** for Qatar Property rental management.

Each module extends Odoo official `industry_real_estate` — no modules exist here yet.

---

## Planned modules

| Folder (future) | Module | Status |
|-----------------|--------|--------|
| `qatar_property_base/` | Core Qatar fields and property register | **Not created** |
| `qatar_property_reservation/` | Unit reservation workflow | **Not created** |
| `qatar_property_pdc/` | Post-dated cheque lifecycle | **Not created** |
| `qatar_property_rent_schedule/` | Rent installment schedules | **Not created** |
| `qatar_property_reports/` | Arabic/English reports | **Not created** |
| `qatar_property_portal/` | Tenant/owner portal | **Not created** |
| `qatar_property_kahramaa/` | Kahramaa utility tracking | **Not created** |
| `qatar_property_maintenance/` | Maintenance requests (optional) | **Not created** |

---

## When modules are created

1. Roadmap reviewed and approved ([CUSTOM_MODULE_ROADMAP.md](../CUSTOM_MODULE_ROADMAP.md))
2. First milestone: **scaffold only** for `qatar_property_base`
3. Standard Odoo module layout:

```
addons/qatar_property_base/
├── __init__.py
├── __manifest__.py
├── models/
├── views/
├── security/
├── data/
├── demo/
└── report/
```

---

## Addons path configuration

When development starts, add this directory to Odoo `addons_path`:

```
...,/path/to/projects/qatar_property_phase3_custom_addons/addons
```

The `industry_real_estate` package remains on a separate path (local OEEL copy, not committed).

---

**No Odoo module code has been created yet.**
