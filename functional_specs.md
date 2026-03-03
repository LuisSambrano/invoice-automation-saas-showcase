# Functional Specifications: Holos.app

## 🏢 Overview

**Holos.app** is a comprehensive B2B SaaS platform that functions as the central nervous system for corporate operations. It combines AI-driven efficiency, legal precision, enterprise-grade security, and hardware integration to deliver a 360° holistic management solution covering everything from HR and POS to Logistics and Fiscal Compliance.

### ⚡ Cross-Reference Legend

To eliminate redundancy, shared capabilities are owned by a **single module** and consumed by others. When you see `→ Consumes M##`, it means the feature's core logic lives in that referenced module.

| Shared Service           | Owner Module | Consumed By       |
| ------------------------ | ------------ | ----------------- |
| BCV Rate Engine          | M12          | M2, M13, M17, M19 |
| OCR Engine               | M11          | M5, M14, M18, M20 |
| Approval Workflows       | M10 (logic)  | M14 (UI), M20     |
| Audit Trail              | M9           | All modules       |
| Cryptographic Signatures | M10          | M15, M18, M20     |

### Module Index

| #   | Module                                             | Category                |
| --- | -------------------------------------------------- | ----------------------- |
| 1   | Talent Acquisition                                 | Core HR                 |
| 2   | Automated Payroll                                  | Core HR                 |
| 3   | Legal & Compliance                                 | Core HR                 |
| 4   | Performance & Climate                              | Core HR                 |
| 5   | Document & File Management                         | Core HR                 |
| 6   | Attendance & Incidents                             | Core HR                 |
| 7   | Internal Communication                             | Core HR                 |
| 8   | Training & Upskilling                              | Core HR                 |
| 9   | RBAC, Audit Trail & Offline-First                  | Architecture & Security |
| 10  | Cryptographic Signatures & Workflows               | Document & Legal        |
| 11  | Hardware Integration (Biometrics, Scanners, WMS)   | Operations              |
| 12  | Multi-Currency Payroll, White-Label & AI Dashboard | HR, Finance & UX        |
| 13  | Point of Sale (POS Front-Office)                   | Interfaces              |
| 14  | Administrative Panel (Back-Office)                 | Interfaces              |
| 15  | Fiscal & Compliance Panel ("El Búnker Legal")      | Tax & Audit             |
| 16  | Logistics, Warehouse & Dispatch (WMS)              | Operations & Logistics  |
| 17  | Omnichannel & E-commerce                           | Sales & Distribution    |
| 18  | Fleet & Driver Management ("Modo Alcabala")        | Logistics & Legal       |
| 19  | B2B & CRM (Clients, Credits & Collections)         | Sales & Finance         |
| 20  | Procurement & Supplier Management                  | Supply Chain            |

---

## 1. 🔍 Talent Acquisition (Reclutamiento y Selección)

**Goal**: Reduce time-to-hire and ensure cultural/technical alignment.

### Features:

- **AI Sourcing Agent**:
  - Automatically parses PDF CVs from email or direct upload.
  - Generates a "Fit Score" (0-100) based on custom technical and cultural criteria.
  - Summarizes candidate strengths and red flags.
- **Smart Job Posting**:
  - One-click distribution to LinkedIn and local job boards (using optimized SEO tags).
- **Interview Assistant**:
  - Generates dynamic interview questions tailored to the candidate's specific background and the role's requirements.

---

## 2. 💰 Automated Payroll (Administración y Nómina)

**Goal**: Eliminate manual errors and handle currency volatility automatically.

### Features:

- **BCV Daily Scribe**:
  - A background bot that fetches the official BCV rate daily.
- **Indexed Calculation Engine**:
  - Allows salary definitions in USD with automatic conversion to VES at the BCV rate of the payment date.
- **Legal Deduction Automation**:
  - **IVSS**: 4% employee / 9-11% employer.
  - **FAOV**: 1% employee / 2% employer.
  - **RPE & INCES**: Automated percentage calculations.
- **LOTTT Benefits Manager**:
  - Automatic calculation of "Utilidades", "Bono Vacacional", and retroactivity of "Prestaciones Sociales".

---

## 3. ⚖️ Legal & Compliance (Cumplimiento Laboral)

**Goal**: Ensure the company stays in good standing with **labor and employment** government entities.
**Scope**: HR-specific obligations only. Tax/fiscal compliance (SENIAT, IGTF) lives in **Module 15**.

### Features:

- **Parafiscal Compliance Dashboard (Labor Only)**:
  - Real-time status of IVSS, FAOV, and INCES payments — the employer's labor obligations.
  - _Tax obligations (IVA, ISLR withholdings, IGTF) → See Module 15._
- **Automatic Labor Reporting**:
  - Generates ARC (ISLR) certificates **for employees** (employer-to-employee document).
  - Generates quarterly Mintra (Nil) reports.
- **Stability Alerts**:
  - AI notifications regarding "Inamovilidad Laboral" regulations and specialized legal updates.

---

## 4. 📈 Performance & Climate (Gestión del Desempeño)

**Goal**: Retain top talent by monitoring engagement.

### Features:

- **AI Sentiment Analysis**:
  - Analyzes recurring internal surveys to detect early signs of employee turnover or burnout.
- **Intelligent Reviews**:
  - AI-assisted performance feedback generation based on self-evaluations and manager input.
- **Growth Paths**:
  - Suggests learning resources (Upskilling) based on performance gaps detected by the Copilot.

---

## 5. 📁 Document & File Management (Gestión de Expedientes)

**Goal**: Centralize and validate legal documentation for every employee.

### Features:

- **Document Validator** _(→ Consumes M11 OCR Engine)_:
  - Sends Cédula and RIF images to the centralized OCR service (Module 11) for extraction.
  - Validates identity data, checks validity/expiration.
  - Verification of academic credentials against profile requirements.
- **Smart Letter Generator**:
  - One-click generation of personalized "Cartas de Trabajo", "Referencias Laborales", and income certifications.
- **Contract Lifecycle Control**:
  - Proactive alerts for expiring fixed-term contracts to manage renewals or transitions to permanent status.

---

## 6. 🕒 Attendance & Incidents (Control de Asistencia)

**Goal**: Precise tracking of time and medical/legal absences.

### Features:

- **Medical Rest Manager**:
  - Upload and validation of IVSS certificates to justify absences.
- **Permission & Leave Tracking**:
  - Employee portal for leave requests (personal, health, education) with real-time balance tracking.
- **Overtime Calculation Engine**:
  - Automated processing of clock-in/out data to determine legal "Horas Extra" and "Bono Nocturno" surcharges according to LOTTT.

---

## 7. 💬 Internal Communication (Comunicación Interna)

**Goal**: Automate repetitive queries and stay connected with the workforce.

### Features:

- **Copilot FAQ Bot**:
  - Decouples HR from trivial queries: "When is the Cestaticket paid?", "What was today's BCV rate?", "How do I request vacations?".
- **Digital Paystubs Distribution**:
  - Mass automated delivery of detailed "Recibos de Pago" (quinquennials and bonuses) via digital channels.
- **Pulse Surveys**:
  - Weekly "Micro-Surveys" to measure team morale in real-time without disrupting productivity.

---

## 8. 🎓 Training & Upskilling (Formación)

**Goal**: Continuous improvement and regulatory awareness.

### Features:

- **Content Curator**:
  - AI-driven suggestions of YouTube tutorials or free courses to close specific skill gaps.
- **Regulatory Briefings**:
  - 2-minute AI summaries of "Gacetas Oficiales" and LOTTT updates, translating legal jargon into actionable business insights for the owner.

---

# 🔒 ENTERPRISE TIER

---

## 9. 🛡️ Core Architecture & Security (Arquitectura Core y Seguridad)

**Goal**: Enterprise-grade security, traceability, and resilience.

### Features:

- **Role-Based Access Control (RBAC)**:
  - Strict permission hierarchy: `SuperAdmin` → `Gerente` → `Operario`.
  - Module-level isolation: a warehouse employee cannot access payroll data.
- **Immutable Audit Trail**:
  - Encrypted, tamper-proof log of every action: `[Who]` did `[What]`, at `[Date/Time]`, to `[Document/Item]`, from `[Terminal/IP]`.
  - Cannot be deleted or modified, even by SuperAdmin.
- **Offline-First Architecture**:
  - Local cache layer for operational modules (fingerprint scanners, inventory guns).
  - Automatic cloud sync upon network restoration with zero data loss.

---

## 10. 📜 Document & Legal Management (Gestión Documental y Legal)

**Goal**: Legally binding digital documents with full traceability.

### Features:

- **Cryptographic Electronic Signatures**:
  - Hash-validated digital signatures on all PDFs.
  - Automatic invalidation if a document is tampered outside the system.
- **Hierarchical Approval Workflows**:
  - Step-by-step validation chain: `Creator` → `Reviewer` → `Approver`.
  - Critical documents (contracts, payroll, purchase orders) are locked until the final digital signature is applied.
- **Metadata & Version Control**:
  - Invisible tracking data embedded in every generated file.
  - Full diff history: compare rejected/edited versions against the final approved version.
- **Physical Archive Indexing ("Testigo Físico")**:
  - Auto-generated topographic codes upon document digitization.
  - Tells the user exactly where to file the physical paper: e.g., `"Estante C, Archivador 2, Carpeta 03-2026"`.

---

## 11. ⚙️ Hardware Integration & Operations (Integración de Hardware)

**Goal**: Eliminate manual data entry via direct hardware connections.

### Features:

- **Dedicated Hardware Integration**:
  - Direct API connection (Local/Bluetooth/USB) with industrial scanners (Zebra, Honeywell) and biometric devices.
  - Eliminates dependency on mobile phone cameras entirely.
- **High-Fidelity OCR Engine**:
  - AI-powered integration with flatbed/ADF document scanners.
  - Extracts invoice and receipt data with millimetric precision.
  - Blocks registration if mathematical inconsistencies are detected (e.g., subtotal + IVA ≠ total).
- **Smart Biometric Attendance Control**:
  - Fingerprint or facial recognition for clock-in/out.
  - Real-time feed into the payroll engine: automatically calculates overtime, night shift bonuses, and holiday surcharges without human intervention.
- **Strict Inventory Management (WMS)**:
  - Full warehouse control: every stock movement requires a hardware scan tied to the logged-in user.
  - Eliminates untraceable losses.

---

## 12. 🎯 HR, Finance & UX (Módulos Avanzados)

**Goal**: Premium analytics, branding, and **single source of truth for the BCV exchange rate**.

### Features:

- **🏦 BCV Rate Service (Single Source of Truth)**:
  - This module owns the daily BCV rate fetch and distribution.
  - All other modules that need the exchange rate **consume this service**: Payroll (M2), POS (M13), Omnichannel (M17), CRM Credits (M19).
  - Rate is fetched once → cached → propagated instantly to all dependents.
- **Automated Multi-Currency Payroll Engine**:
  - Real-time salary processing, benefits, and bonuses cross-referenced with the BCV Rate Service above.
  - Full adaptation to Venezuelan labor regulations (LOTTT, Cestaticket).
- **Corporate Branding Kit (White-Labeling)**:
  - Deep customization panel: logo, color palette (HEX), and typography.
  - All documents, reports, and the entire UI adapt to the client's corporate identity.
- **Analytical Copilot (AI Dashboard)**:
  - Cross-module intelligence: combines HR, inventory, and financial data.
  - Early warning alerts and automated reports. Example: _"Overtime hours increased 30%, but stock dispatches dropped 15% — potential efficiency issue detected."_

---

# 🖥️ DUAL-INTERFACE ARCHITECTURE

---

## 13. 🏪 Point of Sale — POS Front-Office ("La Trinchera")

**Goal**: Maximize cashier speed and eliminate currency miscalculations at the counter.
**Target User**: Cashier / Sales Associate.
**Target Hardware**: Touchscreens, tablets, counter monitors, barcode scanners.

### Features:

- **High-Speed Interface**:
  - Large buttons, high contrast, zero-mouse design.
  - Barcode scanner triggers instant product lookup — item appears on screen immediately.
- **Live Multi-Currency Calculator** _(→ Consumes M12 BCV Rate Service)_:
  - Total displayed simultaneously in VES (at today's BCV rate from Module 12) and USD.
  - Real-time rate refresh throughout the day.
- **Split Payment (Pago Mixto)**:
  - Solves the #1 Venezuelan cashier headache: the customer says _"$10 cash, $5 Zelle, and the rest via Pago Móvil"_.
  - System opens individual slots for each payment method.
  - Automatic IGTF calculation on dollar transactions.
  - Tells the cashier the exact VES amount to charge on the POS terminal.
- **Fiscal Integration & Offline Mode**:
  - Direct communication with certified Fiscal Printer ("Máquina Fiscal").
  - If internet drops, the POS continues invoicing from local cache and syncs automatically when connectivity returns.
- **Blind Cash Closing (Arqueo Ciego)**:
  - End-of-shift reconciliation: cashier counts bills and POS terminal batches, enters totals.
  - System compares against expected amounts and flags any shortfall.
  - Full Audit Trail entry: closing time, terminal ID, cashier identity.

---

## 14. 📊 Administrative Panel — Back-Office ("El Cerebro")

**Goal**: Full operational visibility, audit authority, and legal compliance management.
**Target User**: Manager / Accountant / Owner.
**Target Hardware**: Desktop workstations with SaaS dashboard interface.

### Features:

- **Real-Time Financial Dashboard**:
  - Consolidated view of POS sales: income by currency (USD vs VES), daily/weekly/monthly trends.
  - Devaluation exposure indicator: alerts when high VES receivables pose currency risk.
- **Tax & Withholding Summary** _(detail → See Module 15)_:
  - Quick-view of IVA/ISLR status from POS transactions. Full declaration tools are in the Fiscal Panel (M15).
- **Approval Inbox** _(→ Renders M10 Workflow Engine)_:
  - **UI layer** for the approval logic defined in Module 10.
  - Central hub for pending authorizations: invoices, purchase orders, contracts.
  - Example flow: _"OCR scanned a purchase invoice (M11) → Admin verifies → Applies digital signature (M10) to authorize."_
- **Bank Reconciliation Engine**:
  - Upload bank statements (Banesco, Provincial, Mercantil, etc.).
  - AI auto-matches deposits against Pago Móvil and transfer records registered at the POS.
  - Flags unmatched transactions for manual review.
- **Branding & RBAC Control Center**:
  - Configure POS colors, invoice logos, and typography.
  - Manage user permissions: create new cashier accounts with specific module access.

---

# ⚡ SYSTEM INTERCONNECTION — "The Magic"

The POS cashier **cannot see** product costs, retained taxes, or company balances (RBAC in action). They only see sale price and stock availability. But the instant a cashier scans a product and processes a sale, the system simultaneously:

```
┌─────────────────────────────────────────────────────────┐
│  CASHIER SCANS BARCODE → CUSTOMER PAYS                  │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  1. 📦 WMS Module (11)                                  │
│     → Deducts 1 unit from warehouse stock               │
│     → Logs movement tied to authenticated cashier       │
│                                                         │
│  2. 💰 Admin Dashboard (14)                             │
│     → Credits the corresponding cash register           │
│     → Updates real-time financial graphs                 │
│                                                         │
│  3. 🛡️ Audit Trail (9)                                  │
│     → Records: [Cashier ID] sold [Product] at [Time]    │
│     → From [Terminal ID] at [IP Address]                │
│                                                         │
│  4. ⚖️ Tax Engine (14)                                  │
│     → Accumulates IVA/IGTF for fiscal declaration       │
│                                                         │
│  5. 📜 Fiscal Printer (13)                              │
│     → Emits legal invoice to customer                   │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

> **Two separate interfaces, one unified database** — this is what transforms the platform from a simple tool into a true corporate solution.

---

# 🏛️ TAX & AUDIT TIER

---

## 15. 🏛️ Fiscal & Compliance Panel — "El Búnker Legal"

**Goal**: Absolute tax compliance, zero fines, audit-ready at all times.
**Target User**: Accountant / Tax Advisor / External Auditor.
**Rationale**: Separated from the Admin Back-Office because the administrator manages daily cash flow, while the accountant and external auditor enter this panel to guarantee the company won't be fined or shut down.

---

### 15.1 Centro de Mando Tributario (SENIAT Automation)

Converts raw POS and purchasing data into government-compliant formats at a single click.

- **Purchase & Sales Ledger Generator (Libros de Compra y Venta)**:
  - Outputs the structured file with the exact columns and format mandated by the current "Providencia Administrativa" for IVA books.
  - Not a generic Excel export — a regulation-exact format.
- **TXT Withholding File Engine (Retenciones)**:
  - For "Contribuyentes Especiales": auto-compiles all IVA withholdings (75% or 100%) and ISLR withholdings processed during the pay period.
  - Generates the flat `.txt` file ready for upload to the SENIAT portal — no human touches a single number.
- **IGTF Console (Impuesto a Grandes Transacciones Financieras)**:
  - Isolated panel that totalizes exclusively the 3% charged on foreign currency transactions at the POS.
  - Enables auditing that declared IGTF matches — to the centavo — the actual cash USD and Zelle deposits received.

---

### 15.2 Fiscal Hardware Auditing ("El Espejo de la Máquina")

The Fiscal Panel doesn't just read the cloud database — it talks to local hardware to ensure zero discrepancies.

- **Z-Report Auditor (Reporte Z)**:
  - Reads directly from the certified fiscal printer's memory.
  - Cross-references the daily fiscal closing ("Reporte Z") against software-registered sales.
  - If a gap in the correlative invoice numbering is detected, a **critical red alert** fires immediately.
- **Voided Document Vault (Notas de Crédito)**:
  - Every invoice voided at the POS generates a locked, immutable record here.
  - The auditor can see: who voided it (via Audit Trail), the reason, and download the digitally signed supporting document.

---

### 15.3 Parafiscal & Labor Obligation Radar

Connects with the HR module to create a true "All-in-One" compliance experience.

- **Legal Stoplight Calendar (Calendario de Semáforo)**:
  - Visual dashboard tracking all legal deadlines.
  - Push notifications and emails: _"3 days until IVSS declaration"_, _"FAOV solvency expires"_, _"INCES payment due"_.
  - Color coding: 🟢 Compliant | 🟡 Approaching | 🔴 Overdue.
- **Fiscal Payroll Exporter (Exportador de Nómina Fiscal)**:
  - Extracts HR module data (VES salaries, indexations, bonuses) and generates the exact report formats for:
    - **TIUNA** (Seguro Social / IVSS system).
    - **Ministerio del Trabajo (Nil)** declarations.
  - One-click export, zero manual transcription.

---

### 15.4 Audit Access Controls ("Solo Lectura Estricto")

Specialized RBAC configuration for third-party access.

- **External Auditor / Tax Inspector Profile**:
  - If SENIAT or SUNDDE arrives for a fiscal inspection, the owner creates a **temporary read-only user**.
  - This user can only access: ledgers, product prices, and invoices.
  - **Cannot see**: real profitability, profit margins, or internal dashboards.
  - **Cannot modify**: any data whatsoever.
  - Session is time-limited and fully logged in the Audit Trail.
- **Accounting Period Freeze (Congelamiento de Períodos)**:
  - Once the accountant closes a month and submits tax declarations, they apply their digital signature.
  - The system **permanently locks** that accounting period.
  - **Nobody — not even SuperAdmin — can modify a single invoice from a declared month.**
  - Provides absolute legal certainty for audits.

---

# 🚚 LOGISTICS & DISTRIBUTION TIER

---

## 16. 🏭 Logistics, Warehouse & Dispatch — WMS Panel

**Goal**: Zero-loss inventory control and legally compliant merchandise transport.
**Target User**: Warehouse operator / Dispatcher / Driver.
**Rationale**: In Venezuela, moving merchandise is a high-stakes operation due to "alcabalas" (checkpoints) and government permits. This panel ensures every item is tracked from shelf to delivery with full legal backup.

---

### 16.1 Multi-Warehouse & Transfers

- **Visual Warehouse Manager**:
  - Dashboard view of multiple warehouses ("galpones") or branch locations.
- **Inter-Branch Transfers**:
  - Transferring stock from Branch A to Branch B requires:
    1. Exit scan at origin (barcode/QR).
    2. Stock status changes to "In Transit" (locked — cannot be sold).
    3. Entry scan at destination.
  - Full Audit Trail on every step.

---

### 16.2 Mobilization Guide Manager (SADA / SUNAGRO / SICA)

A massive pain point in Venezuela for food and pharmaceutical industries.

- **Automated Guide Generation**:
  - Creates the internal dispatch guide cross-referencing:
    - Vehicle data (plate, model).
    - Driver RIF and identity.
    - Security seal number ("precinto").
  - Format is ready to present at any government checkpoint.

---

### 16.3 Operator Interface (Hardware-First UX)

Designed for the **5-inch touchscreen** of a Zebra industrial scanner, not a 24-inch monitor.

- **Ultra-High Contrast UI**:
  - Giant buttons: `[ENTRADA]` `[SALIDA]` `[INVENTARIO ROTATIVO]`.
  - Zero keyboards — everything via barcode or QR scan.
  - Minimal text, maximum visual feedback (colors + sounds).

---

### 16.4 Last-Mile Delivery Tracking

- **Lightweight Driver Mobile App**:
  - Upon delivery, the customer signs on the driver's phone screen.
  - Alternatively: a photo of the delivery location serves as "testigo físico".
  - Status changes to "Delivered" in the Admin Panel in real-time.

---

## 17. 🌐 Omnichannel & E-commerce Panel

**Goal**: Unify physical and digital sales channels into a single inventory truth.
**Target User**: E-commerce Manager / Marketing / Operations.

---

### 17.1 Real-Time Stock Sync Engine

- **Single Inventory Source**:
  - If the cashier sells the last pair of shoes at the physical POS, the web catalog and Super App hide the product in **< 1 second**.
  - Prevents overselling across channels.

---

### 17.2 Dynamic Catalog & Pricing Manager

In Venezuela, updating prices one by one is unviable due to constant rate fluctuation.

- **Mass USD Price Updates**:
  - Set all prices in USD once.
  - System auto-recalculates VES equivalents across all channels (POS, Web, WhatsApp) using the daily BCV rate.
- **Channel-Specific Margins**:
  - Apply different markups per channel if needed (e.g., delivery surcharge on web orders).

---

### 17.3 Digital Order Board ("Kitchen Monitor")

- **Restaurant-Style Order Display**:
  - New web/app orders trigger an audible alert.
  - Warehouse team receives the **Picking & Packing** order with:
    - AI-optimized shelf collection route.
    - Item checklist with barcode verification.
  - Order progresses through statuses: `Received` → `Picking` → `Packed` → `Dispatched`.

---

## 18. 🚛 Fleet & Driver Management — "Modo Alcabala"

**Goal**: Full legal protection for merchandise in transit and driver accountability.
**Target User**: Fleet Manager / Driver / Checkpoint Inspector.
**Differentiator**: This is the module that makes this platform unbeatable — automated legal hard-stops that prevent human error.

---

### 18.1 Digital Vehicle Dossier (Fleet Management)

Every truck, motorcycle, or van is treated as a **Critical Asset** with its own database.

- **OCR Document Intake** _(→ Consumes M11 OCR Engine)_:
  - High-resolution scan (no blurry photos) sent to the centralized OCR service (Module 11):
    - "Carnet de Circulación" (vehicle registration).
    - Insurance Policy (RCV).
    - Municipal tax receipt ("Trimestre").
  - AI extracts: plates, engine/chassis serial numbers, expiration dates.
- **Load Spec Sheet**:
  - Maximum capacity in weight (KG) and volume (M³).
  - System blocks assigning 2,000 KG to a van rated for 1,000 KG.
- **Maintenance Logbook**:
  - Tracks oil changes, tires, brakes.
  - **Blocks the vehicle** from dispatch if it exceeds safe mileage without registered maintenance.

---

### 18.2 Driver Operational Dossier (HR Integration)

The driver already exists in the HR module — this adds a legal validation layer for field operations.

- **License & Certificate Control**:
  - Driver's license (matched to the truck's tonnage grade).
  - Medical driving certificate.
- **Expiration Stoplight**:
  - **30 days before expiry**: red alerts fire in both the Admin Panel and the Logistics Panel.
- **Responsibility Assignment ("Testigo Digital")**:
  - Before departure, the driver logs in via mobile device or fingerprint at the dispatch terminal.
  - Their electronic signature is **cryptographically bound** to the specific load and vehicle for that day.

---

### 18.3 Legal Hard-Stop Engine ("The Dispatch Blocker")

Automated golden rule that protects the company from catastrophic fines.

- **Strict Exit Condition**:
  - When a dispatcher attempts to generate a Mobilization Guide (SADA/SICA) or Delivery Note:
    1. System runs a **millisecond-level** compliance check.
    2. Verifies: driver's license validity, vehicle RCV status, load capacity, maintenance status.
    3. If **ANY** document is expired or condition unmet → **PRINT IS BLOCKED. EXIT IS PROHIBITED.**
  - Zero human errors. Zero "let him go, he'll renew it tomorrow."

---

### 18.4 Driver App — "Modo Alcabala" (Roadside Survival UX)

The driver on the road doesn't need accounting or stock views — they need tools to **legally defend their cargo** at a checkpoint.

- **Checkpoint Screen ("Modo Alcabala")**:
  - One giant button → generates a **dynamic QR code** on the driver's screen.
- **Instant Verification Portal**:
  - If the traffic officer scans the QR with their phone, they're taken to a **public read-only webpage** (hosted on the platform) showing:
    - ✅ Vehicle legal status (plate, model, valid RCV).
    - ✅ Verified driver identity.
    - ✅ Exact cargo manifest (what's being carried, destination, fiscal invoice number, SICA guide).
  - All backed by the Audit Trail and cryptographic signatures from previous steps.
  - Proves the company is **100% transparent**.

---

# 🤝 COMMERCIAL & SUPPLY CHAIN TIER

---

## 19. 🏢 B2B & CRM Panel (Clients, Credits & Collections)

**Goal**: Manage wholesale/corporate clients with multi-currency credit and full sales lifecycle tracking.
**Target User**: Sales Manager / Credit Analyst / Field Sales Rep.
**Rationale**: The POS handles walk-in cash customers. But for wholesalers, distributors, and corporate services, credit management and prospecting are the lifeblood of the business.

---

### 19.1 Multi-Currency Credit Limit Manager

In Venezuela, extending credit is a massive risk due to currency volatility.

- **USD-Referenced Credit Lines** _(→ Consumes M12 BCV Rate Service)_:
  - Assign each client a credit limit fixed in USD.
  - At payment time, the outstanding debt is recalculated to VES at the **exact BCV rate of that day** (sourced from Module 12).
  - Protects the company from devaluation losses on receivables.
- **Aging Analysis Dashboard**:
  - Visual breakdown of receivables by age: 0-15 days, 15-30, 30-60, 60+.
  - Auto-flags overdue accounts and suggests collection actions.

---

### 19.2 Smart Quotation Engine

- **Branded Quotations (White-Label)**:
  - Professional proposals generated with the company's Kit de Marca (logo, colors, typography).
- **Countdown Timer**:
  - Each quote has a validity countdown (e.g., _"Valid for 24 hours"_) due to currency fluctuation.
  - Expired quotes automatically recalculate at the current BCV rate if reactivated.
- **One-Click to Invoice**:
  - Approved quote converts directly to a fiscal invoice — no re-entry.

---

### 19.3 Sales Pipeline (Embudo de Ventas)

- **Field Sales CRM**:
  - Track prospects through stages: `Lead` → `Contact` → `Proposal` → `Negotiation` → `Won/Lost`.
  - Log calls, schedule visits, attach notes.
- **Client Purchase History**:
  - Full transaction timeline per client, cross-referenced with credits, returns, and payment behavior.
- **Commission Tracker**:
  - Auto-calculates sales rep commissions based on configurable rules (% of sale, margin-based, etc.).

---

## 20. 📦 Procurement & Supplier Management Panel

**Goal**: Intelligent purchasing with full audit trail from requisition to supplier payment.
**Target User**: Purchasing Manager / Warehouse Chief / Director.
**Rationale**: Every item sold at the POS or stored in the WMS must first be purchased intelligently. This panel closes the supply chain loop.

---

### 20.1 Requisition Workflows

- **Internal Requisition System**:
  - The warehouse chief notices low stock → creates a "Requisición" in the system.
  - The requisition flows to the Purchasing Panel via the approval workflow.
- **Multi-Supplier Quote Request**:
  - The system enables requesting quotes from 3+ suppliers for the same item.
  - Side-by-side comparison table with price, lead time, and payment terms.

---

### 20.2 AI Replacement Cost Analysis

- **Historical Price Intelligence**:
  - AI analyzes the purchase history and alerts: _"Supplier X sold you this item 15% more expensive than last month. Supplier Y offers a better rate."_
- **Currency-Adjusted Costing**:
  - All supplier prices are normalized to USD for fair comparison regardless of invoice currency.
- **Reorder Point Suggestions**:
  - Based on sales velocity and lead times, suggests optimal reorder quantities and timing.

---

### 20.3 Digital Purchase Orders

- **Official PO Generation**:
  - Once a supplier is selected, the system generates the formal Purchase Order.
- **Director's Digital Signature**:
  - The PO requires cryptographic signature from the authorized director (Approval Workflow + Audit Trail).
- **Automatic Delivery to Supplier**:
  - Signed PO is emailed to the supplier automatically.
- **Goods Receipt Matching**:
  - When merchandise arrives at the warehouse, the WMS module scans items against the PO.
  - Discrepancies (wrong quantity, missing items) are flagged immediately.

# 🛠️ User Flows

### Onboarding a New Employee

1. HR enters basic data and salary in USD.
2. Copilot generates a digital contract compliant with LOTTT.
3. Employee signs via integrated Cryptographic Electronic Signature (Module 10).
4. System triggers Hierarchical Approval Workflow for contract validation.
5. Data automatically populates the Payroll Engine, Parafiscal tables, and Biometric system.
6. Physical archive code is generated for the signed paper copy.

### Running Payroll

1. Admin triggers a "Payroll Run".
2. Copilot fetches the latest BCV rate (Module 2).
3. System calculates gross salary (USD → VES) and applies all legal deductions.
4. Summary reports are generated for bank transfer and fiscal declaration.
5. Digital paystubs are distributed automatically (Module 7).
6. Immutable audit trail entry is created (Module 9).

### Scanning & Processing an Invoice

1. Operator places the document on the flatbed scanner.
2. OCR Engine extracts all line items, subtotals, and IVA.
3. System validates mathematical consistency — blocks if totals don't match.
4. Approved invoice enters the approval workflow (Module 10).
5. Physical archive index code is generated and printed.

### Inventory Movement

1. Warehouse operator logs in via biometric scan.
2. Scans item barcode with dedicated Zebra/Honeywell scanner.
3. System registers the movement tied to the authenticated user.
4. Stock levels update in real-time on the dashboard.
5. If stock falls below threshold, Analytical Copilot triggers an alert (Module 12).

### POS Sale (Front-Office)

1. Cashier scans product barcode with Zebra/Honeywell scanner.
2. Item appears instantly — total updates in USD and VES simultaneously.
3. Customer requests split payment: "$10 cash + rest via Pago Móvil".
4. System opens payment slots, calculates IGTF on dollars automatically.
5. Cashier confirms — fiscal invoice prints on certified printer.
6. Stock deducts, cash register credits, audit trail logs — all in parallel.

### Bank Reconciliation (Back-Office)

1. Accountant uploads Banesco/Provincial bank statement (PDF or CSV).
2. AI engine parses all deposits and transfers.
3. System auto-matches against POS Pago Móvil and Zelle records.
4. Unmatched entries are flagged for manual review.
5. Reconciliation report is generated and archived with version control (Module 10).

### End-of-Day Cash Closing

1. Cashier initiates "Arqueo Ciego" from POS terminal.
2. Counts physical bills and enters totals per denomination.
3. Enters POS terminal batch totals.
4. System compares against expected collection.
5. Discrepancy report is generated — signed and logged in Audit Trail (Module 9).

### Monthly Tax Declaration (Fiscal Panel)

1. Accountant opens the Fiscal Panel (Module 15).
2. System auto-generates Libros de Compra y Venta from POS and purchase data.
3. TXT engine compiles all IVA/ISLR withholdings for the period.
4. IGTF console displays total foreign currency tax collected.
5. Accountant reviews, validates, and downloads all files.
6. Files are uploaded to SENIAT portal.
7. Accountant applies digital signature → **period is permanently frozen.**

### Fiscal Inspection (External Auditor Access)

1. SENIAT/SUNDDE inspector arrives.
2. Owner creates a temporary read-only auditor profile (Module 15.4).
3. Inspector accesses: invoices, ledgers, product prices.
4. Inspector **cannot see**: margins, profitability, or internal metrics.
5. Inspector **cannot modify**: any record.
6. Upon completion, the temporary account is deactivated and the full session is archived in the Audit Trail.

### Inter-Branch Stock Transfer (WMS)

1. Warehouse operator at Branch A scans items for transfer.
2. System changes stock status to "In Transit" — items become unsellable.
3. Dispatch generates Mobilization Guide with vehicle and driver data (Module 18).
4. Hard-Stop Engine validates: driver license ✅, vehicle RCV ✅, load capacity ✅.
5. Merchandise departs with full legal documentation.
6. At Branch B, operator scans items on arrival → status changes to "Available".
7. Full transfer is logged in the Audit Trail with timestamps from both locations.

### Web/App Order Fulfillment (Omnichannel)

1. Customer places order on web store.
2. Stock sync engine instantly reserves the items across all channels.
3. Digital Order Board alerts the warehouse team with audible notification.
4. AI generates the optimal picking route through the shelves.
5. Operator scans each item during packing (barcode verification).
6. Order is dispatched → driver app tracks delivery → customer signs on screen.
7. Status updates to "Delivered" in real-time on the Admin Dashboard.

### Roadside Checkpoint ("Modo Alcabala")

1. Driver is stopped at a government "alcabala" checkpoint.
2. Driver presses the giant "Modo Alcabala" button on the mobile app.
3. Dynamic QR code appears on screen.
4. Officer scans QR → public read-only portal loads instantly.
5. Portal displays: vehicle status, driver identity, cargo manifest, fiscal invoice.
6. All data is backed by cryptographic signatures and Audit Trail.
7. Inspection is resolved in seconds with full legal transparency.

### Dispatch with Legal Hard-Stop

1. Dispatcher selects items, vehicle, and driver for a delivery run.
2. System runs millisecond compliance check on driver and vehicle documents.
3. **Scenario A** — All clear: Mobilization Guide prints, dispatch proceeds.
4. **Scenario B** — Driver license expired: **System blocks the guide. Exit prohibited.** Alert sent to Admin and HR.
5. **Scenario C** — Vehicle overloaded: **System blocks. Suggests redistribution across available vehicles.**

### B2B Credit Sale (CRM)

1. Sales rep creates a branded quotation for a wholesale client (Module 19.2).
2. Quote includes a 24-hour validity countdown due to BCV fluctuation.
3. Client approves → quote converts to fiscal invoice with one click.
4. System checks client's USD credit limit — sale is within bounds.
5. Goods are dispatched from WMS (Module 16) with full legal documentation.
6. Receivable is logged in the Aging Dashboard, indexed to USD.
7. On payment day, VES amount is recalculated at the current BCV rate.

### Procurement Cycle (Purchasing)

1. Warehouse chief creates a Requisición for low-stock items.
2. Requisition arrives at the Procurement Panel via approval workflow.
3. Purchasing manager requests quotes from 3 suppliers.
4. AI flags: _"Supplier A is 15% more expensive than last month."_
5. Manager selects best supplier → system generates Purchase Order.
6. Director applies digital signature → PO is emailed to supplier automatically.
7. Goods arrive at WMS → operator scans against PO → discrepancies flagged instantly.
