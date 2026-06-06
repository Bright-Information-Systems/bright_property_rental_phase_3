# Requirements Traceability Matrix

**Bright Information Systems W.L.L** · Qatar Property Phase 3  
Maps business requirements to planned custom modules.

---

## Traceability table

| ID | Business requirement | Target module | Industry model used | Phase | Status |
|----|---------------------|---------------|---------------------|-------|--------|
| BR-01 | Qatar property master data (district, zone, RERA, Baladiya, plot) | `qatar_property_base` | `x_buildings`, `account.analytic.account` | Phase 3.1 | Planned |
| BR-02 | Buildings registry | `qatar_property_base` | `x_buildings` (extend) | Phase 3.1 | Planned |
| BR-03 | Property units registry | `qatar_property_base` | `account.analytic.account` (extend) | Phase 3.1 | Planned |
| BR-04 | Owner role on partner | `qatar_property_base` | `res.partner` | Phase 3.1 | Planned |
| BR-05 | Sponsor role on partner | `qatar_property_base` | `res.partner` | Phase 3.1 | Planned |
| BR-06 | Guarantor role on partner | `qatar_property_base` | `res.partner` | Phase 3.1 | Planned |
| BR-07 | Tenant role enhancement | `qatar_property_base` | `res.partner` | Phase 3.1 | Planned |
| BR-08 | Qatar statutory property register | `qatar_property_base` | Report on `account.analytic.account` | Phase 3.1 | Planned |
| BR-09 | Kahramaa meter reference on unit | `qatar_property_base` | `account.analytic.account` | Phase 3.1 | Planned |
| BR-10 | Unit reservation / hold | `qatar_property_reservation` | New `qatar.property.reservation` | Phase 3.2 | Planned |
| BR-11 | Reservation deposit | `qatar_property_reservation` | Reservation + `account.payment` link | Phase 3.2 | Planned |
| BR-12 | Reservation → contract conversion | `qatar_property_reservation` | `sale.order` subscription | Phase 3.2 | Planned |
| BR-13 | Post-dated cheque received | `qatar_property_pdc` | New `qatar.property.pdc` | Phase 3.3 | Planned |
| BR-14 | PDC deposited / cleared / bounced | `qatar_property_pdc` | PDC state machine | Phase 3.3 | Planned |
| BR-15 | PDC replacement / cancellation | `qatar_property_pdc` | PDC state machine | Phase 3.3 | Planned |
| BR-16 | PDC linked to tenant, contract, invoice, unit | `qatar_property_pdc` | Cross-model links | Phase 3.3 | Planned |
| BR-17 | Rent installment schedule | `qatar_property_rent_schedule` | New `qatar.rent.schedule` | Phase 3.4 | Planned |
| BR-18 | Rent escalation rules | `qatar_property_rent_schedule` | Schedule lines | Phase 3.4 | Planned |
| BR-19 | Contract renewal tracking | `qatar_property_rent_schedule` | `sale.order` + schedule | Phase 3.4 | Planned |
| BR-20 | Schedule line → invoice link | `qatar_property_rent_schedule` | `account.move` | Phase 3.4 | Planned |
| BR-21 | Arabic/English lease PDF | `qatar_property_reports` | QWeb report | Phase 3.5 | Planned |
| BR-22 | Tenant statement report | `qatar_property_reports` | QWeb report | Phase 3.5 | Planned |
| BR-23 | Owner statement report | `qatar_property_reports` | QWeb report | Phase 3.5 | Planned |
| BR-24 | Property register report (PDF) | `qatar_property_reports` | QWeb report | Phase 3.5 | Planned |
| BR-25 | Contract summary report | `qatar_property_reports` | QWeb report | Phase 3.5 | Planned |
| BR-26 | PDC report | `qatar_property_reports` | QWeb report | Phase 3.5 | Planned |
| BR-27 | Tenant portal — view contracts | `qatar_property_portal` | `sale.order` portal | Phase 3.6 | Planned |
| BR-28 | Tenant portal — view invoices/payments | `qatar_property_portal` | `account.move` portal | Phase 3.6 | Planned |
| BR-29 | Tenant portal — download documents | `qatar_property_portal` | Report + attachment | Phase 3.6 | Planned |
| BR-30 | Tenant portal — submit requests | `qatar_property_portal` | Portal form | Phase 3.6 | Planned |
| BR-31 | Kahramaa meter tracking | `qatar_property_kahramaa` | Extend `x_meters` or new model | Phase 3.7 | Planned |
| BR-32 | Utility readings history | `qatar_property_kahramaa` | Reading lines | Phase 3.7 | Planned |
| BR-33 | Move-in / move-out utility records | `qatar_property_kahramaa` | Event records | Phase 3.7 | Planned |
| BR-34 | Maintenance request (optional) | `qatar_property_maintenance` | `helpdesk.ticket` or custom | Phase 3.8 | Optional |

---

## Requirements by module

### `qatar_property_base` — BR-01 to BR-09

Core Qatar property layer. All other modules depend on this.

### `qatar_property_reservation` — BR-10 to BR-12

Pre-contract unit hold workflow.

### `qatar_property_pdc` — BR-13 to BR-16

Cheque lifecycle without accounting override.

### `qatar_property_rent_schedule` — BR-17 to BR-20

Structured billing beyond default subscription.

### `qatar_property_reports` — BR-21 to BR-26

Document and reporting layer.

### `qatar_property_portal` — BR-27 to BR-30

Self-service for tenants and owners.

### `qatar_property_kahramaa` — BR-31 to BR-33

Utility meter and reading management.

### `qatar_property_maintenance` — BR-34 *(optional)*

Maintenance requests linked to property.

---

## Out of scope (Phase 3)

| Item | Reason |
|------|--------|
| Replacing `industry_real_estate` | Extend only — official foundation |
| Phase 1 `sale_renting` migration | Historical reference — new data uses industry workflow |
| Accounting posting override | Requires explicit client approval per module |
| Odoo core / industry source edits | Forbidden — inherit and extend only |

---

## Validation source

| Phase | Evidence |
|-------|----------|
| Phase 1 UAT | `sale_renting` workflow — historical |
| Phase 2 UAT | `industry_real_estate` UC-IRE-001 … 009 — foundation |
| Phase 3 UAT | Per-module Playwright suites — future |

---

**Bright Information Systems W.L.L** · June 2026
