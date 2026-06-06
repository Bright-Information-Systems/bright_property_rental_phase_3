# Custom Module Roadmap — Qatar Property Phase 3

**Bright Information Systems W.L.L** · Extends `industry_real_estate`  
**Status:** Planning only — no module code yet

---

## Delivery order

Modules are delivered in dependency order. Each module must pass UAT before the next begins.

```
industry_real_estate (Odoo official)
    └── qatar_property_base          ← START HERE
            ├── qatar_property_reservation
            ├── qatar_property_pdc
            ├── qatar_property_kahramaa
            ├── qatar_property_rent_schedule
            ├── qatar_property_reports
            ├── qatar_property_portal
            └── qatar_property_maintenance (optional)
```

---

## 1. `qatar_property_base`

**Purpose:** Core Qatar extension layer on official property models.

| Capability | Detail |
|------------|--------|
| Property master data | Qatar district, zone, RERA ref, Baladiya ref, plot number |
| Utility reference | Kahramaa meter reference on unit (base field; full tracking in `qatar_property_kahramaa`) |
| Partner roles | Owner, sponsor, guarantor, tenant role enhancements |
| Property register | Qatar statutory property register (list/report foundation) |
| Model extension | `x_buildings`, `account.analytic.account`, `res.partner`, `sale.order` |

**Depends on:**

- `industry_real_estate`
- `base`
- `contacts`
- `account`
- `sale` / `sale_subscription` (per actual industry module dependency chain)

**Estimated duration:** 4–6 weeks  
**UAT prefix:** UC-QPB-*

---

## 2. `qatar_property_reservation`

**Purpose:** Unit reservation and hold workflow before contract.

| Capability | Detail |
|------------|--------|
| Unit hold | Reserve a property unit for a prospect/tenant |
| Expiry | Automatic or manual reservation expiry |
| Deposits | Reservation deposit tracking |
| Conversion | Convert confirmed reservation → subscription contract |

**Depends on:** `qatar_property_base`

**Estimated duration:** 2–3 weeks  
**UAT prefix:** UC-QPR-*

---

## 3. `qatar_property_pdc`

**Purpose:** Post-dated cheque (PDC) lifecycle management.

| Capability | Detail |
|------------|--------|
| Cheque states | Received, deposited, cleared, bounced, replaced, cancelled |
| Linkage | Tenant, contract, invoice, property unit |
| Accounting | **No direct posting override** unless explicitly approved |

**Depends on:**

- `qatar_property_base`
- `account`

**Estimated duration:** 3–4 weeks  
**UAT prefix:** UC-QPD-*

---

## 4. `qatar_property_rent_schedule`

**Purpose:** Structured rent billing beyond default subscription lines.

| Capability | Detail |
|------------|--------|
| Installments | Rent installment schedule per contract |
| Billing plan | Contract-level billing plan definition |
| Escalation | Annual or periodic rent escalation rules |
| Renewal | Renewal tracking and schedule regeneration |
| Invoice link | Schedule lines linked to invoices/subscriptions |

**Depends on:**

- `qatar_property_base`
- `qatar_property_pdc` (if cheque linkage required for installments)

**Estimated duration:** 3–4 weeks  
**UAT prefix:** UC-QRS-*

---

## 5. `qatar_property_reports`

**Purpose:** Qatar business and regulatory documents.

| Capability | Detail |
|------------|--------|
| Lease documents | Arabic/English lease PDFs |
| Statements | Tenant statement, owner statement |
| Registers | Property register report |
| Summaries | Contract summary, PDC report |

**Depends on:**

- `qatar_property_base`
- `qatar_property_pdc`
- `qatar_property_rent_schedule`

**Estimated duration:** 3–4 weeks  
**UAT prefix:** UC-QRP-*

---

## 6. `qatar_property_portal`

**Purpose:** Tenant and owner self-service portal.

| Capability | Detail |
|------------|--------|
| Visibility | Contracts, invoices, payments, documents |
| Requests | Submit service/lease requests |
| Downloads | Statements and lease documents |

**Depends on:**

- `qatar_property_base`
- `portal`
- `website`

**Estimated duration:** 3–4 weeks  
**UAT prefix:** UC-QPO-*

---

## 7. `qatar_property_kahramaa`

**Purpose:** Kahramaa utility meter and reading management.

| Capability | Detail |
|------------|--------|
| Meter tracking | Kahramaa meter IDs linked to units |
| Readings | Utility reading history |
| Move events | Move-in / move-out utility records |
| Documents | Utility bills and reference attachments |

**Depends on:** `qatar_property_base`

**Estimated duration:** 2–3 weeks  
**UAT prefix:** UC-QKH-*

---

## 8. `qatar_property_maintenance` *(optional, later)*

**Purpose:** Maintenance request workflow linked to property operations.

| Capability | Detail |
|------------|--------|
| Requests | Maintenance linked to property/unit/tenant |
| Assignment | Technician assignment |
| Workflow | Open → in progress → resolved → closed |
| Portal | Request submission via `qatar_property_portal` |

**Depends on:**

- `qatar_property_base`
- `helpdesk` or `project` (final decision pending)

**Estimated duration:** 2–3 weeks  
**UAT prefix:** UC-QMN-*

---

## Module sizing principles

| Rule | Rationale |
|------|-----------|
| One business domain per module | Independent install, test, and deploy |
| Extend, don't replace | Inherit `industry_real_estate` models |
| Security per module | `ir.model.access.csv` + record rules |
| Demo data per module | Sandbox-ready test records |
| Playwright UAT per module | Client screenshot evidence |

---

## Git repository strategy

| Option | Recommendation |
|--------|----------------|
| Single repo for all addons | Preferred — `addons/` contains all `qatar_property_*` modules |
| Phase 2 repo | Documentation/UAT only — do not mix custom code there |
| Phase 3 workspace | Local development; push to dedicated repo when scaffold begins |

---

**Bright Information Systems W.L.L** · June 2026
