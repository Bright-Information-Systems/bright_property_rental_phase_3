# Custom Fields Matrix

**Bright Information Systems W.L.L** · Qatar Property Phase 3  
Maps each planned custom field to target model, owning module, and delivery phase.

---

## Field matrix

| Field | Purpose | Target model | Module | Required in phase | Notes |
|-------|---------|--------------|--------|-------------------|-------|
| Qatar District | Geographic district (e.g. Al Rayyan, West Bay) | `x_buildings`, `account.analytic.account` | `qatar_property_base` | Phase 3.1 | Selection or char; align with Qatar municipality list |
| Zone | Sub-district / zone within district | `x_buildings`, `account.analytic.account` | `qatar_property_base` | Phase 3.1 | Optional on building; required on unit |
| RERA Reference | Real Estate Regulatory Authority registration | `x_buildings`, `account.analytic.account` | `qatar_property_base` | Phase 3.1 | Building-level + unit-level refs |
| Baladiya Reference | Municipal (Baladiya) permit reference | `x_buildings` | `qatar_property_base` | Phase 3.1 | Building-level |
| Plot Number | Land registry plot identifier | `account.analytic.account` | `qatar_property_base` | Phase 3.1 | Unit-level; unique per plot |
| Kahramaa Meter Reference | Utility meter ID (Kahramaa) | `account.analytic.account` | `qatar_property_base` | Phase 3.1 | Base reference field; full tracking in `qatar_property_kahramaa` |
| Owner | Property owner partner | `res.partner` (role), link on unit | `qatar_property_base` | Phase 3.1 | Many2one or partner tag/role |
| Sponsor | Lease sponsor (visa/commercial) | `res.partner` (role) | `qatar_property_base` | Phase 3.1 | Common in Qatar commercial leases |
| Guarantor | Financial guarantor | `res.partner` (role) | `qatar_property_base` | Phase 3.1 | Linked to contract |
| Tenant role | Distinct tenant role on partner | `res.partner` (role) | `qatar_property_base` | Phase 3.1 | Extends generic Customer from industry module |
| Property Register Number | Qatar statutory register ID | `account.analytic.account` | `qatar_property_base` | Phase 3.1 | Official portfolio reference |
| Property Status | Available, occupied, reserved, maintenance | `account.analytic.account` | `qatar_property_base` | Phase 3.1 | Computed + manual override; extends `x_invoice_status` |
| Reservation Status | Draft, confirmed, expired, converted | `qatar.property.reservation` *(new)* | `qatar_property_reservation` | Phase 3.2 | New model |
| PDC Status | Received, deposited, cleared, bounced, replaced, cancelled | `qatar.property.pdc` *(new)* | `qatar_property_pdc` | Phase 3.3 | State machine field |
| Rent Schedule Reference | Link to installment schedule | `sale.order` | `qatar_property_rent_schedule` | Phase 3.4 | One2many to `qatar.rent.schedule.line` |

---

## Fields by target model

### `x_buildings` (extend)

| Field | Type (planned) | Module |
|-------|----------------|--------|
| Qatar District | Selection | `qatar_property_base` |
| Zone | Char / Selection | `qatar_property_base` |
| RERA Reference | Char | `qatar_property_base` |
| Baladiya Reference | Char | `qatar_property_base` |

### `account.analytic.account` (extend — property units)

| Field | Type (planned) | Module |
|-------|----------------|--------|
| Qatar District | Selection (related or stored) | `qatar_property_base` |
| Zone | Char | `qatar_property_base` |
| RERA Reference | Char | `qatar_property_base` |
| Plot Number | Char | `qatar_property_base` |
| Kahramaa Meter Reference | Char | `qatar_property_base` |
| Property Register Number | Char | `qatar_property_base` |
| Property Status | Selection | `qatar_property_base` |
| Owner | Many2one `res.partner` | `qatar_property_base` |

### `res.partner` (extend)

| Field | Type (planned) | Module |
|-------|----------------|--------|
| Is Owner | Boolean / role | `qatar_property_base` |
| Is Sponsor | Boolean / role | `qatar_property_base` |
| Is Guarantor | Boolean / role | `qatar_property_base` |
| Is Tenant | Boolean / role | `qatar_property_base` |

### `sale.order` (extend — subscription contracts)

| Field | Type (planned) | Module |
|-------|----------------|--------|
| Guarantor | Many2one `res.partner` | `qatar_property_base` |
| Sponsor | Many2one `res.partner` | `qatar_property_base` |
| Rent Schedule Reference | One2many | `qatar_property_rent_schedule` |

### New models (later modules)

| Model | Key status field | Module |
|-------|------------------|--------|
| `qatar.property.reservation` | Reservation Status | `qatar_property_reservation` |
| `qatar.property.pdc` | PDC Status | `qatar_property_pdc` |
| `qatar.rent.schedule` / `.line` | Schedule line state | `qatar_property_rent_schedule` |
| `qatar.kahramaa.meter` / `.reading` | Reading status | `qatar_property_kahramaa` |

---

## Phase 2 gap confirmation

These fields were confirmed **missing** in Phase 2 UAT (UC-IRE-009):

- Qatar District, Zone, RERA, Baladiya, Plot Number
- Kahramaa meter reference (structured)
- Owner / sponsor / guarantor roles
- Qatar statutory property register

Evidence: [Phase 2 gap screenshot](https://github.com/Bright-Information-Systems/bright_property_rental_phase_2/blob/feature/industry-real-estate-workflow-uat/docs/screenshots/industry_real_estate_uat/10_gap_analysis_shop_g01_fields.png)

---

**Bright Information Systems W.L.L** · June 2026
