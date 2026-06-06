# UAT Strategy — Qatar Property Phase 3

**Bright Information Systems W.L.L** · Playwright-driven acceptance testing

---

## Principles

| Principle | Detail |
|-----------|--------|
| **Screenshot evidence** | Every workflow step captured as PNG for client review |
| **Automate where possible** | Playwright for install, menu, CRUD, and business flows |
| **Regression always** | Official `industry_real_estate` workflow must still pass after each module |
| **Isolated sandbox** | Dedicated DB per development phase — never touch Phase 1 UAT DB |
| **Per-module suites** | One spec file per addon under `tests/playwright/` |

---

## Minimum tests per module

Every custom module must pass **at least 5** Playwright test cases before merge:

| # | Test | Description | Screenshot |
|---|------|-------------|------------|
| 1 | **Install test** | Module installs via RPC or UI without error | `01_module_installed.png` |
| 2 | **Menu access test** | All module menus open without traceback | `02_menu_<name>.png` |
| 3 | **Create record test** | Create primary model record via UI | `03_create_<model>.png` |
| 4 | **Edit record test** | Open and verify custom fields on form | `04_edit_<model>.png` |
| 5 | **Main business flow test** | End-to-end workflow for module purpose | `05_flow_<scenario>.png` |
| 6 | **Regression test** | Re-run industry workflow (building → unit → contract → invoice) | `06_regression_industry.png` |

Test 6 is **mandatory** for every module that touches shared models.

---

## Test naming convention

```
tests/playwright/tests/
├── qatar_property_base_uat.spec.js
├── qatar_property_reservation_uat.spec.js
├── qatar_property_pdc_uat.spec.js
├── qatar_property_rent_schedule_uat.spec.js
├── qatar_property_reports_uat.spec.js
├── qatar_property_portal_uat.spec.js
├── qatar_property_kahramaa_uat.spec.js
└── industry_regression.spec.js          ← shared regression suite
```

Use case IDs: `UC-QPB-001`, `UC-QPR-001`, `UC-QPD-001`, etc.

---

## Screenshot storage

```
docs/screenshots/
├── qatar_property_base/
├── qatar_property_reservation/
├── qatar_property_pdc/
├── qatar_property_rent_schedule/
├── qatar_property_reports/
├── qatar_property_portal/
├── qatar_property_kahramaa/
└── regression/
```

Screenshots are committed to the repository and referenced in module README / use-case docs.

---

## Sandbox databases

| Database | Purpose | Port (planned) |
|----------|---------|----------------|
| `qatar_property_phase1_demo` | Phase 1 historical — **do not touch** | 9019 |
| `qatar_property_industry_uat` | Phase 2 official workflow evidence — **read only** | 9020 |
| `qatar_property_phase3_dev` | Phase 3 custom addon development | 9021 *(create at M1)* |

---

## Regression test — official industry workflow

After installing any custom module, re-validate:

| Step | Action | Model |
|------|--------|-------|
| 1 | Open Properties app | — |
| 2 | Verify buildings exist | `x_buildings` |
| 3 | Verify property units exist | `account.analytic.account` |
| 4 | Open rental contract | `sale.order` |
| 5 | Verify invoice link | `account.move` |
| 6 | Open availability gantt | `sale.order` gantt |

Baseline: Phase 2 UAT spec — `bright_property_rental_phase_2/tests/playwright/tests/industry_real_estate_uat.spec.js`

---

## Module-specific flow tests

### `qatar_property_base`

- Create building with Qatar district, zone, RERA, Baladiya
- Create unit with plot number, register number, Kahramaa ref
- Assign owner/sponsor/guarantor/tenant roles on partner
- Generate property register report

### `qatar_property_reservation`

- Reserve Shop G-01 for prospect
- Record reservation deposit
- Convert reservation → subscription S0000X

### `qatar_property_pdc`

- Register PDC received for tenant
- Mark deposited → cleared
- Simulate bounce → replacement

### `qatar_property_rent_schedule`

- Create 12-month schedule on contract
- Apply escalation rule
- Link schedule line to invoice

### `qatar_property_reports`

- Print Arabic lease PDF
- Print tenant statement
- Print property register

### `qatar_property_portal`

- Login as portal tenant
- View contracts and invoices
- Download statement

### `qatar_property_kahramaa`

- Link meter to unit
- Record move-in reading
- Record move-out reading

---

## Pass / fail criteria

| Result | Criteria |
|--------|----------|
| **PASS** | All minimum tests green; screenshots captured; regression PASS |
| **PARTIAL** | Main flow works; minor UI or non-blocking issue documented |
| **FAIL** | Install error, broken industry regression, or missing core workflow |

Client sign-off required for **PASS** before module merge.

---

## CI integration (future)

| Stage | Tool |
|-------|------|
| Lint | `pylint` / `flake8` on `addons/` |
| Install | Odoo `-i module` on clean DB |
| UAT | `npx playwright test` against sandbox |
| Screenshots | Artefact upload on CI failure |

---

## Reference

- Phase 2 UAT: [USE_CASES_INDUSTRY_REAL_ESTATE_UAT.md](https://github.com/Bright-Information-Systems/bright_property_rental_phase_2/blob/feature/industry-real-estate-workflow-uat/docs/USE_CASES_INDUSTRY_REAL_ESTATE_UAT.md)
- Development rules: [DEVELOPMENT_RULES.md](../DEVELOPMENT_RULES.md)

---

**Bright Information Systems W.L.L** · June 2026
