# Playwright UAT — Qatar Property Phase 3

**Bright Information Systems W.L.L**

---

## Purpose

This directory will store **Playwright end-to-end UAT suites** for each Qatar Property custom addon.

Tests follow the strategy defined in [docs/UAT_STRATEGY.md](../../docs/UAT_STRATEGY.md).

---

## Planned structure

```
tests/playwright/
├── README.md                           ← This file
├── package.json                        ← Created when first suite is added
├── playwright.config.js
├── helpers/
│   └── odoo.js                         ← Login, RPC, screenshot helpers
├── tests/
│   ├── qatar_property_base_uat.spec.js
│   ├── qatar_property_reservation_uat.spec.js
│   ├── qatar_property_pdc_uat.spec.js
│   ├── qatar_property_rent_schedule_uat.spec.js
│   ├── qatar_property_reports_uat.spec.js
│   ├── qatar_property_portal_uat.spec.js
│   ├── qatar_property_kahramaa_uat.spec.js
│   └── industry_regression.spec.js
└── run_uat.sh
```

---

## Screenshot output

Screenshots are saved to:

```
docs/screenshots/<module_name>/
```

Example: `docs/screenshots/qatar_property_base/01_module_installed.png`

---

## Reference implementation

Phase 2 Playwright UAT (official `industry_real_estate` workflow):

- Repo: https://github.com/Bright-Information-Systems/bright_property_rental_phase_2
- Spec: `tests/playwright/tests/industry_real_estate_uat.spec.js`
- Sandbox: `qatar_property_industry_uat` @ http://127.0.0.1:9020

Phase 3 development sandbox (planned): `qatar_property_phase3_dev` @ http://127.0.0.1:9021

---

## Running tests (when available)

```bash
cd tests/playwright
export ODOO_URL=http://127.0.0.1:9021
export ODOO_DB=qatar_property_phase3_dev
export ODOO_PASSWORD='<admin password>'
./run_uat.sh
```

---

## Minimum per module

| Test | Required |
|------|----------|
| Install | Yes |
| Menu access | Yes |
| Create record | Yes |
| Main business flow | Yes |
| Industry regression | Yes |

---

**No Playwright suites exist yet. Created when first module scaffold is ready.**
