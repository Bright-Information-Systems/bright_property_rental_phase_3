# Development Rules — Qatar Property Phase 3

**Bright Information Systems W.L.L** · Mandatory standards for all custom addons

---

## 1. Foundation and extension

| Rule | Detail |
|------|--------|
| **Extend `industry_real_estate`** | All property logic builds on official models (`x_buildings`, `account.analytic.account`, `sale.order`) |
| **Do not duplicate** | Do not recreate building/unit/contract models unless unavoidable and documented |
| **No core edits** | Do not modify Odoo core or `industry_real_estate` source files |
| **Inherit only** | Use `_inherit`, XML view inheritance, and `ir.actions` extensions |

---

## 2. Code location and structure

| Rule | Detail |
|------|--------|
| **All custom code under `addons/`** | One folder per module: `addons/qatar_property_base/`, etc. |
| **Small modules** | One business domain per module; independently installable |
| **Standard layout** | `__manifest__.py`, `models/`, `views/`, `security/`, `data/`, `report/` |
| **Naming** | Prefix all custom models with `qatar.property.*` or `qatar.rent.*` |

---

## 3. Dependencies

| Rule | Detail |
|------|--------|
| **Declare explicitly** | Every `depends` entry in `__manifest__.py` must be justified |
| **Minimal deps** | Only depend on what the module actually uses |
| **No circular deps** | Dependency graph must be acyclic (see MODULE_DEPENDENCY_MAP.md) |
| **Industry first** | `qatar_property_base` must depend on `industry_real_estate` |

---

## 4. Accounting and payments

| Rule | Detail |
|------|--------|
| **No posting override** | Do not override `account.move` posting without explicit client approval |
| **Standard payment flow** | Use Odoo `account.payment` register wizard |
| **PDC is tracking** | `qatar_property_pdc` tracks cheque lifecycle; accounting entries follow approved design only |
| **Document exceptions** | Any accounting customization requires written approval in module design doc |

---

## 5. Security

Every module must include before merge:

- `security/ir.model.access.csv` — groups and CRUD permissions
- Record rules (`security/*.xml`) where multi-company or role-based access applies
- Menu items restricted to appropriate groups
- Portal access rules for `qatar_property_portal`

---

## 6. Data and demo

| Rule | Detail |
|------|--------|
| **Demo data per module** | `demo/` XML with sandbox-ready records |
| **Industry workflow** | Demo data follows `industry_real_estate` flow (buildings → units → contract → invoice) |
| **Phase 1 records** | Historical reference only — do not replicate S00006/S00007 in new demos |
| **Consistent test data** | Reuse Al Rayyan Tower, Shop G-01, Doha Trading LLC naming where applicable |

---

## 7. UAT and evidence

Every module must pass before merge:

| Gate | Requirement |
|------|-------------|
| **Install test** | Module installs cleanly on fresh sandbox DB with `industry_real_estate` |
| **Menu access test** | All menus open without error |
| **CRUD test** | Create, read, update key records |
| **Business flow test** | Main workflow end-to-end |
| **Regression test** | Official industry workflow still works after module install |
| **Playwright suite** | Automated tests in `tests/playwright/` |
| **Screenshots** | Client UAT evidence in `docs/screenshots/<module>/` |

Minimum Playwright tests per module: **5** (install, menu, create, flow, regression).

---

## 8. Versioning and manifests

| Field | Standard |
|-------|----------|
| `version` | `19.0.1.0.0` on first release; semver thereafter |
| `license` | `LGPL-3` (custom modules) |
| `author` | Bright Information Systems W.L.L |
| `category` | Real Estate |

---

## 9. Git and repository

| Rule | Detail |
|------|--------|
| **Phase 2 repo** | Documentation/UAT only — no custom module code |
| **Phase 3 workspace** | Custom addons developed here |
| **Commits** | One module scaffold or feature per logical commit |
| **No secrets** | Never commit `.env`, passwords, or `ODOO_PASSWORD` |

---

## 10. Review gates

| Gate | When | Approver |
|------|------|----------|
| Roadmap review | Before any coding | Client + project lead |
| Module scaffold review | After `__manifest__.py` + empty structure | Project lead |
| UAT review | After Playwright PASS + screenshots | Client |
| Merge to main | After UAT sign-off | Project lead |

**No coding starts until roadmap is reviewed.**  
**First coding milestone = module scaffold only** (`qatar_property_base`).

---

**Bright Information Systems W.L.L** · June 2026
