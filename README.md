# Qatar Property — Phase 3 Custom Addons Workspace

**Bright Information Systems W.L.L** · Odoo 19 Enterprise  
**Workspace:** `projects/qatar_property_phase3_custom_addons/`  
**Repository:** https://github.com/Bright-Information-Systems/bright_property_rental_phase_3  
**Date:** June 2026

---

## What this workspace is

This is the **local Phase 3 workspace** for Qatar Property **custom Odoo addons** that extend Odoo's official Property Management package (`industry_real_estate`).

| Aspect | Detail |
|--------|--------|
| **Foundation** | Odoo official `industry_real_estate` v19.0.1.3 |
| **Purpose** | Plan, design, and eventually build Qatar-specific extensions |
| **Custom code location** | `addons/` (modules created here later) |
| **Current state** | **No custom Odoo module code exists yet** |

---

## Relationship to other phases

| Phase | Location | Role |
|-------|----------|------|
| **Phase 1** | [bright_property_rental_phase_1](https://github.com/Bright-Information-Systems/bright_property_rental_phase_1) | Workflow validation using `sale_renting` — historical reference only |
| **Phase 2** | [bright_property_rental_phase_2](https://github.com/Bright-Information-Systems/bright_property_rental_phase_2) | Architecture decision, Playwright UAT, screenshots, user guide |
| **Phase 3** | **This workspace (local)** | Custom addon development planning and future implementation |

Phase 3 is **separate** from the Phase 2 documentation/UAT repository. Phase 2 proves the official workflow; Phase 3 builds the Qatar layer on top of it.

---

## Workspace structure

```
qatar_property_phase3_custom_addons/
├── README.md                      ← This file
├── CUSTOM_MODULE_ROADMAP.md       ← Planned addons and dependencies
├── REQUIREMENTS_TRACEABILITY.md   ← Business requirements → modules
├── DEVELOPMENT_RULES.md           ← Coding and UAT standards
├── docs/
│   ├── PHASE3_PLAN.md
│   ├── MODULE_DEPENDENCY_MAP.md
│   ├── CUSTOM_FIELDS_MATRIX.md
│   ├── UAT_STRATEGY.md
│   └── screenshots/               ← Future UAT evidence
├── addons/
│   └── README.md                  ← Future Odoo modules (empty for now)
└── tests/
    └── playwright/
        └── README.md              ← Future Playwright suites
```

---

## Planned custom modules (summary)

| # | Module | Purpose |
|---|--------|---------|
| 1 | `qatar_property_base` | Qatar fields, partner roles, property register |
| 2 | `qatar_property_reservation` | Unit hold, deposits, convert to contract |
| 3 | `qatar_property_pdc` | Post-dated cheque lifecycle |
| 4 | `qatar_property_rent_schedule` | Installments, escalation, renewals |
| 5 | `qatar_property_reports` | Arabic/English documents and statements |
| 6 | `qatar_property_portal` | Tenant/owner self-service |
| 7 | `qatar_property_kahramaa` | Utility meter tracking |
| 8 | `qatar_property_maintenance` | Maintenance requests (optional, later) |

Full detail: [CUSTOM_MODULE_ROADMAP.md](CUSTOM_MODULE_ROADMAP.md)

---

## Key documents

| Document | Description |
|----------|-------------|
| [CUSTOM_MODULE_ROADMAP.md](CUSTOM_MODULE_ROADMAP.md) | Module purposes, dependencies, delivery order |
| [REQUIREMENTS_TRACEABILITY.md](REQUIREMENTS_TRACEABILITY.md) | Business requirement → module mapping |
| [DEVELOPMENT_RULES.md](DEVELOPMENT_RULES.md) | Extension rules, security, UAT gates |
| [docs/PHASE3_PLAN.md](docs/PHASE3_PLAN.md) | Phase 3 objectives and milestones |
| [docs/MODULE_DEPENDENCY_MAP.md](docs/MODULE_DEPENDENCY_MAP.md) | Dependency diagram |
| [docs/CUSTOM_FIELDS_MATRIX.md](docs/CUSTOM_FIELDS_MATRIX.md) | Field-level design matrix |
| [docs/UAT_STRATEGY.md](docs/UAT_STRATEGY.md) | Playwright and acceptance testing strategy |

---

## Official workflow reference

Custom modules extend this validated flow (from Phase 2 UAT):

```
Properties app → Buildings (x_buildings) → Units (account.analytic.account)
    → Tenant (res.partner) → Subscription (sale.order) → Invoice → Payment
```

Phase 2 evidence: https://github.com/Bright-Information-Systems/bright_property_rental_phase_2/tree/feature/industry-real-estate-workflow-uat

---

## Status

| Item | Status |
|------|--------|
| Roadmap and planning docs | **Created** |
| Custom Odoo modules under `addons/` | **Not created** |
| First coding milestone | Module scaffold for `qatar_property_base` (pending roadmap review) |

---

**Bright Information Systems W.L.L** · June 2026
