# Proposal: Open Auto — Retail Process Automation for Company A

> Draft v2. 10 slides max, PDF, English. Each section = one slide: **Key message**, content, suggested visual.
> **Planning Notice:** Pilot duration (~12–14 weeks), regional sequencing (Denmark → Norway → Sweden), and tech stack represent an indicative reference plan and baseline architecture. All are modular and will be calibrated to the organizer's official timeline and Company A's enterprise IT standards during discovery.

---

## Slide 1 — Title

**Open Auto: Let the bots do the re-typing, let people do the thinking**
*A Scalable Enterprise Automation Strategy for Distributed Retail Operations*

- Modular automation accelerator tailored for Company A's multi-market footprint
- One shared cloud platform. Configurable local bot adapters per operating market.
- Strategic Roadmap (Reference Scenario): Pilot in Market 1 (Denmark: B2B quotes & store shortages) → Expand to Market 2 (Norway: store operations) → Scale to Market 3 (Sweden: delivery & fulfilment)
- Team name: Vui · Date: October 2026

*Visual:* Executive hero architecture concept — Central Open Auto Cloud Orchestrator securely connecting to distributed Bot Agents across pilot and expansion markets.

---

## Slide 2 — The real problem

**Key message:** The problem is not "manual work" in general. It is people acting as the glue between fragmented systems — and that glue is different in each country.

What employees actually do today:

| Operational Role | Real-World Manual Bottlenecks ("The Human Glue") |
|---|---|
| **B2B Inside Sales Desk**<br>*(Primary: Denmark)* | Decipher unstructured contractor RFQs (messy PDFs, scans, handwritten site notes); manually decode trade slang to ERP SKUs; look up custom customer rebate pricing tiers, check cross-branch stock availability, and verify credit limits by hand. |
| **Store & Timber Yard Staff**<br>*(Primary: Norway)* | Reconcile paper delivery slips (følgesedler) from bulk suppliers against ERP POs; manually print and replace hundreds of shelf/bin tags when timber & commodity prices fluctuate; prepare morning contractor job-site pickup staging. |
| **Dispatch & Site Logistics**<br>*(Primary: Sweden)* | Track heavy freight & crane-truck (kranbil) job-site deliveries across multiple 3rd-party haulier portals; manually chase late drivers and scramble to notify construction site managers before building crews sit idle; verify proof-of-delivery photos. |
| **Central Supply Chain / HQ**<br>*(Cross-Nordic)* | Pull inventory reports from 3 separate national legacy ERPs into massive Excel workbooks to manually reconcile inter-branch stock transfers, track supplier volume rebates, and identify regional stockout risks. |

Why it persists:
- **Fragmented national systems:** Each market runs different legacy ERP/WMS/POS instances; traditional integration projects take years and millions.
- **Unstructured real-world inputs:** Construction orders, supplier delivery slips, and carrier waybills arrive in varied formats that hardcoded APIs cannot parse.
- **"Below the IT radar":** Individual manual tasks appear small locally, but collectively waste tens of thousands of skilled employee hours annually.
- **No unified automation overlay:** No cross-market platform exists to orchestrate lightweight, localized bot workflows across distributed branches.

Consequences: Slow quote turnaround loses B2B contractor bids, wrong building materials arrive at active job sites, out-of-sync shelf prices leak margin, and staff spend their days acting as data-entry buffers.

*Visual:* "Day in the Life" comparison — A B2B trade desk specialist spending 70% of their morning manually re-typing contractor PDFs and toggling between 4 screens, versus an automated workflow delivering immediate customer response.

---

## Slide 3 — Why prioritise manual processes

**Key message:** Manual processes sit upstream of store and delivery challenges—and in Denmark, fast quotes protect core B2B construction revenue against competitors.

| Challenge | Impact | Reach (3 markets) | Time to market | Needs system replacement? |
|---|---|---|---|---|
| **Manual processes** | **Critical:** Touches revenue & every role | All three | **Fast:** Sits on top of existing systems | **No** |
| Store operations | High in NO | Partly local | Medium | Partly |
| Delivery & fulfilment | High in SE | Partly local | Medium to slow | Often (WMS/TMS) |
| Fragmented systems | High, long term | All three | Slow (multi-year ERP overhaul) | **Yes** |

Strategic Rationale:
- **B2B Revenue Protection (Primary Market / Denmark Scenario):** Commercial trade contractors send multi-line quote requests to several distributors at once. A manual turnaround of hours or days leads directly to lost bids. Accelerating quotes to minutes directly wins revenue and protects margin.
- **Upstream Error Elimination:** Re-keyed orders are the single biggest cause of downstream store discrepancies and delivery errors. Fixing order entry stops errors before they propagate across the supply chain.
- **Immediate Value without ERP Overhaul:** Replacing fragmented legacy ERPs takes 2–4 years. An overlay orchestration platform delivers value in weeks without disrupting ongoing IT roadmaps.
- **Reusable Foundation:** Proving the platform in the primary market establishes the B2B quote and store inventory bot templates, which subsequent markets adapt in Waves 2 & 3.

*Visual:* Prioritisation 2x2 matrix (Business Impact vs. Speed to Value) highlighting Manual Processes in the top-right "Immediate Quick Win" quadrant.

---

## Slide 4 — The solution: Open Auto

**Key message:** Open Auto is our team's cloud-native automation accelerator tailored for Company A. It sits cleanly on top of existing ERPs to deploy secure Python bots that remove the "human glue"—enabling business users to create automations via AI plain language.

### Recommended Reference Architecture (Modular & Adaptable)

```
  ┌─────────────────────────────────────────────────────────────┐
  │         Open Auto Cloud Orchestrator (Modular Core)         │
  │     (Multi-Tenant · RBAC · Real-Time Dashboard · Audit)     │
  │                                                             │
  │  ┌───────────────────────────────┐   ┌───────────────────┐  │
  │  │ Bot Studio: AI Chat Builder   │   │ Schedule Manager  │  │
  │  │ (MVP Core; Canvas/Code in Ph2)│   │ (Quartz / Cron)   │  │
  │  └───────────────────────────────┘   └───────────────────┘  │
  │  ┌───────────────────────────────┐   ┌───────────────────┐  │
  │  │ Runtime Intelligence Service  │   │ Package Manager   │  │
  │  │ (FastMCP + Claude / LLM API)  │   │ (Cloud Storage)   │  │
  │  └───────────────────────────────┘   └───────────────────┘  │
  │            Real-Time Execution Event Bus (SignalR / WS)     │
  └─────────────┬─────────────────┬─────────────────┬───────────┘
                │                 │                 │
          ┌─────▼──────┐    ┌─────▼──────┐    ┌─────▼──────┐
          │ Bot Agent  │    │ Bot Agent  │    │ Bot Agent  │
          │ Market 1   │    │ Market 2   │    │ Market 3   │
          │ (e.g. DK)  │    │ (e.g. NO)  │    │ (e.g. SE)  │
          └────────────┘    └────────────┘    └────────────┘
```

How it works (Zero Greenfield Plumbing Risk · Fully Adaptable Stack):
1. **Proven Accelerator Foundation:** Open Auto utilizes a battle-tested modular core (reference stack: ASP.NET Core / microservices, Quartz.NET scheduler, SignalR, Next.js). This eliminates plumbing risks while remaining flexible to swap components to align with Company A's internal IT standards.
2. **Create (AI Chat Builder):** Non-technical staff describe automations in plain text; AI assembles pre-tested, sandboxed action modules (MVP). Drag-and-drop canvas and pro-code IDE are Phase 2 extensions.
3. **Deploy & Trigger:** Versioned bot packages deploy to local Bot Agents (Windows/Linux) via secure TLS, triggered by email, schedule, webhook, or manual run.
4. **API-First with UI Fallback:** Bots communicate with ERP/WMS via modern REST/OData APIs; where legacy portals lack APIs, bots seamlessly fall back to headless browser automation (Playwright/Selenium).
5. **Runtime Intelligence:** Enterprise LLM extraction (Claude/Azure OpenAI) parses unstructured tables and SKUs from PDFs and emails within strict EU data boundaries.
6. **Govern & Audit:** Multi-tenant isolation per market, RBAC permissions, human-in-the-loop exception approvals, and immutable audit logs.

*Visual:* Open Auto architecture diagram highlighting the pre-built Cloud Orchestrator connecting securely to market Bot Agents, emphasizing API-first integration and human-in-the-loop governance.

---

## Slide 5 — Bot Studio: AI Chat Builder

**Key message:** Non-technical staff can build secure automations in minutes using natural language. The AI does not write unvetted code—it safely orchestrates pre-certified enterprise building blocks.

### Safe, Constrained Bot Generation Workflow

```
  [1. Plain-Language Prompt]
  "Every morning at 06:00, check central warehouse & branch inventory for high-velocity
   building materials (timber, cement, insulation). If any store is below safety buffer,
   generate an Excel shortage summary and email store trade desks & HQ buyers."
                    │
                    ▼
  [2. AI Intent Parsing & Component Assembly (Claude Engine)]
  AI maps intent to certified building blocks:
  • Trigger: Schedule (Cron: 06:00 Mon-Fri)
  • Connector: ERP Inventory Reader (Pre-vetted read-only API module)
  • Logic: Threshold Filter Module (Min stock rule)
  • Reporter: Excel Generator Module (OpenPyXL template)
  • Dispatcher: Secure SMTP Mailer (Restricted internal relay)
                    │
                    ▼
  [3. Visual Parameter Mapping & Human Validation]
  Platform presents visual workflow summary with extracted parameters for human review:
  [Trigger: 06:00] ──> [ERP: Check Safety Stock] ──> [Filter: < Min] ──> [Email: Trade Desks]
  *Human confirms credentials, scopes, and notification targets*
                    │
                    ▼
  [4. One-Click Packaging & Activation]
  Packaged into sandboxed, signed Python package → Pushed to Cloud Orchestrator
```

### Why Constrained Assembly Beats "Raw Code Generation"
- **No Free-Form Code Generation:** AI selects from a curated catalog of certified, tested action modules rather than writing unconstrained Python scripts against the ERP.
- **Enterprise Guardrails:** Read-only by default for analytical bots; write operations require explicit RBAC permissions and parameter schema validation.
- **Fast Human Review:** Users review clean visual inputs, schedules, and recipients—not raw lines of code.

### Certified Building Blocks Available to AI in MVP
- **Triggers:** Timed schedules (Quartz.NET), inbound email event, file drop, manual trigger.
- **Connectors (API-First):** ERP OData/REST endpoints, SQL read views, secure SFTP, Webhook.
- **UI Fallbacks:** Headless browser automation (Playwright/Selenium) for legacy portals lacking APIs.
- **Document Intelligence:** Claude API extraction for quote PDFs, invoice images, and unstructured emails.
- **Actions & Delivery:** Excel report builder, quote PDF generator, Exchange/SMTP email dispatch, Teams notification.

### Post-MVP Evolution (Phase 2 Roadmap)
- **Visual Drag & Drop Canvas:** Node-based workflow editor for users who prefer visual diagramming over chat.
- **Pro-Code Studio with AI Co-Pilot:** Full Python development environment with SDK autocompletion for complex algorithmic automations.

*Visual:* A 3-step storyboard mockup: (1) Inside sales user typing natural language prompt → (2) AI assembling the visual flow with parameter boxes → (3) User clicking "Approve & Activate" with execution preview.

---

## Slide 6 — MVP scope (Fast-to-Demo & Low-Complexity Pilot)

**Key message:** Focus the MVP on two high-impact, low-complexity use cases that can be demoed in under 30 seconds, carry zero operational risk (read-only queries + human-in-the-loop review), and prove both platform capabilities (AI Document Intelligence & Natural-Language Bot Building).

### MVP Use Case Selection Criteria (Pragmatic & Demo-Ready)
- **Fast & Highly Visual to Demo:** Audience sees immediate before/after results in 20–30 seconds (messy contractor PDF → clean quote PDF preview; prompt → assembled bot).
- **Low Technical Complexity & Risk:** Read-only data lookups against price lists/APIs; zero risky database schema modifications or autonomous writes.
- **Dual Archetype Validation:** Validates both event-triggered AI document extraction (Bot A) and scheduled routine rule automation (Bot B).

### The Two Pragmatic MVP Bots (Denmark Working Scenario)

- **Bot A: B2B Quote Request Extractor & Draft Generator (Event-Driven · High Value)**
  - *Why it's fast to demo:* Inbound email arrives with a contractor PDF $\rightarrow$ AI instantly extracts line items and matches ERP SKUs $\rightarrow$ Generates a ready-to-review Quote PDF. Demo takes **20 seconds** to show tangible value.
  - *Why it's not too difficult:* Read-only catalog matching and draft PDF generation (`pdfplumber` / Claude API + `reportlab`); sales reps retain 100% control via 1-click approval.
  - *Outcome:* Cuts handling time from ~12 minutes to ~4 minutes of review per quote (assumption A4, validated in pilot), defending B2B sales without complex ERP writeback integration.

- **Bot B: Morning Safety-Stock Shortage Alert (Scheduled · Quick Win)**
  - *Why it's fast to demo:* Assembled live in **3–5 minutes** using the **AI Chat Builder** by typing a natural-language prompt $\rightarrow$ Instant test run executes and sends an Excel alert.
  - *Why it's not too difficult:* Read-only threshold check on core fast-moving materials (structural timber, cement, drywall) using simple logic (`stock < min_safety_buffer`) and automated email dispatch (`openpyxl`).
  - *Outcome:* Replaces the manual morning stock-report check in 80 stores with exception-only alerts (~15 → ~5 min per store), so trade desks can arrange inter-branch transfers before the contractor morning rush. It does not replace physical stock counts.

| In Scope (Indicative Pilot Phase) | Out of Scope (Roadmap) |
|---|---|
| Deployment & configuration of Open Auto accelerator core (Multi-tenant, Scheduling, SignalR, Dashboard) | Greenfield platform engineering (accelerator core is pre-built) |
| **AI Chat Builder** (natural language → assembled modular bot) | Visual Drag & Drop Canvas & Pro-Code IDE (Phase 2) |
| **2 Pragmatic Bots:** Bot A (Quote Drafts) + Bot B (Shortage Alerts) | Complex multi-system transactional writebacks |
| Primary market tenant (e.g., Denmark), localized models, 1 ERP catalog connector | Expansion market production tenants (Waves 2 & 3) |
| Read-only API integration with Playwright/Selenium UI fallback | Invasive ERP database schema modifications |
| 3 Bot Agents running on pilot VMs/PCs | Enterprise-wide server cluster deployment |
| 5–10 pilot users (Inside Sales Reps + 1 Regional Store Manager) | Company-wide general rollout |

Recommended Reference Stack (Flexible & Enterprise-Adaptable):
- **Cloud Orchestrator:** ASP.NET Core backend (or Java/Node.js equivalent), PostgreSQL/SQL Server, Redis, SignalR real-time hub (cloud-agnostic: AWS/Azure/GCP EU region).
- **Control Center:** Next.js enterprise dashboard, Tailwind/Shadcn UI (or Company A's internal design system), real-time log streaming.
- **Bot Agent Runtime:** Lightweight Windows/Linux Service, isolated Python virtual environments, encrypted credential store.
- **Document Intelligence:** Enterprise LLM (Claude / Azure OpenAI) hosted in EU data region via FastMCP runtime connector.

*Visual:* Execution flow diagram: Inbound email/PDF → AI IDP extraction → ERP catalog match → 1-click sales review → draft quote PDF generated in 20 seconds.

---

## Slide 7 — Where AI creates value

**Key message:** AI operates at two distinct, strictly governed layers: accelerating bot creation without coding (Build-Time), and processing messy, unstructured documents with human-in-the-loop safeguards (Run-Time).

### Layer 1 — Build-Time AI: Natural-Language Bot Assembly
*Democratizing automation across Danish branches without compromising system stability.*

| User Persona | Action in Bot Studio | AI Function & Safety Mechanism |
|---|---|---|
| **Store / Sales Lead** | Types plain-language operational need | Claude translates intent into parameter schemas and selects pre-certified building blocks |
| **Automation Champion** | Reviews visual flow, thresholds, and recipients | AI pre-validates logic, verifies required parameters, and checks permissions before 1-click activation |
| **IT / Developer** | Configures secure connectors & data policies | AI inspects bot definitions against corporate security constraints (zero arbitrary script generation) |

### Layer 2 — Run-Time AI: Intelligent Document Processing (IDP)
*Handling unstructured real-world retail data that classic ERP integrations cannot parse.*

| Retail Task | What AI Automates | Enterprise Safeguard & Quality Control | Business Accuracy |
|---|---|---|---|
| **Contractor Order Extraction** | Reads messy PDF quote requests, scans, handwritten notes, and email bodies | Dual-pass OCR/IDP with confidence scoring; fields scoring <85% are routed to human review | Target **≥95% field accuracy** (pilot gate); ≥70% of lines touchless |
| **Catalog SKU Disambiguation** | Maps contractor slang / trade descriptions to exact ERP product numbers | Semantic vector matching; presents top-3 ranked matches with confidence scores for operator sign-off | Reduces wrong-item orders (target −50% errors) |
| **Multilingual Routing & Drafts** | Sorts customer inquiries across Danish, Norwegian, and Swedish inboxes | Strict intent classification; drafts localized responses for sales team review during pilot | Human review before any email dispatch |
| **Stockout Exception Detection** | Evaluates multi-store inventory trends against velocity thresholds | Deterministic business rules verify AI anomaly flags prior to report generation | Prevents false alarms to store managers |

### Non-Negotiable Governance Principles
- **Human-in-the-Loop Authority:** AI never makes autonomous pricing or credit limit decisions. AI extracts and calculates; licensed employees approve.
- **Strict GDPR & EU Boundary:** 100% of LLM inference and document processing executes on EU-hosted, enterprise-grade endpoints. Zero customer or commercial data used for model retraining.
- **Immutable Auditability:** Full end-to-end traceability logged in Open Auto: raw input document → prompt/model version → extraction confidence → human approval → ERP transaction ID.

*Visual:* Two-layer visual diagram: Top (Build-Time: Plain language → certified module assembly); Bottom (Run-Time: Inbound messy PDF → Claude extraction → confidence validation → human approval gate → ERP commit).

---

## Slide 8 — Business impact & ROI

**Key message:** Once rolled out across Denmark, the two bots free ~14,000 staff hours a year — about **€570k net annual value** after running costs — so the ~€140k pilot pays back in roughly 3 months. Faster quotes add revenue upside on top, which we deliberately keep out of the base case.

### Key Assumptions (validated in Weeks 1–2 discovery)
| # | Assumption | Value | Basis |
|---|---|---|---|
| A1 | Stores in Denmark | 80 | Assumption: "hundreds of stores" across 3 markets; Denmark is the home market |
| A2 | B2B quote requests in Denmark | 400 / day (5 per store) | Assumption |
| A3 | Share arriving as email / PDF (in scope for Bot A) | 75% → 300 / day | Assumption: phone and counter requests are excluded |
| A4 | Manual handling time per quote → with Bot A | 12 min → 4 min (review only) | Assumption; to be time-studied on a sample of real quotes |
| A5 | Morning shortage check per store → with Bot B | 15 min → 5 min (exception review) | Assumption |
| A6 | Working days per year | 250 office days / 300 store days | Denmark: 5- vs. 6-day weeks, minus public holidays |
| A7 | Fully loaded labour cost | €50 / hour | Eurostat: Denmark average €51.7/h (2025), rounded down |

### Base Case: Denmark Full Rollout (Annual)
| | Bot A: B2B Quote Drafts | Bot B: Shortage Alerts | Total |
|---|---|---|---|
| Volume | 300 quotes/day × 250 days | 80 stores × 300 days | |
| Time saved | 8 min × 300 = 40 h/day → **10,000 h** | 10 min × 80 = 13.3 h/day → **4,000 h** | **14,000 h** |
| Gross capacity value (€50/h) | €500k | €200k | **€700k** |

| Running Costs (Annual, Assumption) | Amount |
|---|---|
| LLM inference: ~75k documents × ~€0.05 (≈10k input + 3k output tokens on a mid-tier model) | ~€5k |
| Cloud hosting: orchestrator, database, agents (EU region) | ~€25k |
| Platform support: 1 FTE | ~€100k |
| **Total running cost** | **~€130k** |

**Net annual value ≈ €570k** · **Pilot investment ≈ €140k (range €130–150k)** · **Payback ≈ 3 months after Denmark rollout**

*Note: Hours freed are capacity, not automatic headcount cuts. The value comes from sales reps handling more quotes and staff moving to customer-facing work.*

### Upside Not Included in the Base Case
- **Faster quotes, more won bids:** Industry sources consistently link response speed to win rate, but the published percentages are mostly vendor data. So we show sensitivity rather than a promise. *Illustration (assumptions: €2,500 average quote, 25% gross margin): every +1 percentage point in quote-to-order conversion on 75k quotes/year ≈ 750 extra orders ≈ **€470k gross margin**.*
- **Fewer order-entry errors:** Manual order entry is commonly benchmarked at 1–3% errors (APQC, as widely cited). The target is to **halve** errors in the pilot, measured against the Week 1–2 baseline.

### Core Pilot KPIs (Measured with 5–10 Pilot Users)
1. Handling time per quote (baseline 12 min → target ≤4 min)
2. Quote turnaround time (hours → <15 minutes for in-scope quotes)
3. Touchless line rate (target ≥70% of lines need no manual correction)
4. Order-entry error rate (target −50% vs. baseline)
5. Quote-to-order conversion and pilot user satisfaction

*The pilot validates **per-quote** savings with a small user group. The €570k figure is the Denmark-wide extrapolation and is recalculated at the Go/No-Go gate using measured values.*

*Visual:* Simple bar chart: Pilot investment (€140k) vs. annual net value (€570k), with the revenue upside shown as a dashed bar labelled "not in base case".

---

## Slide 9 — Scale across markets

**Key message:** One core engine deployed once; local configurations scale the platform across markets with zero redundant infrastructure.

### Shared Platform vs. Local Market Adapters

| Shared Core (Build Once, Run Everywhere) | Local Adapters (Configured per Market) |
|---|---|
| **Orchestrator & Multi-Tenant Engine:** Cloud hosting, Quartz scheduler, real-time SignalR | **Isolated Workspaces:** Dedicated tenant environments with local RBAC and data separation |
| **Bot Studio & Component Catalog:** Pre-built triggers, action modules, Excel/PDF tools | **Local System Connectors:** Country ERP/WMS/POS adapters (API-first with UI fallback) |
| **Enterprise Intelligence Layer:** Multilingual AI IDP extraction and prompt schemas | **Market Rules:** Local language models, local currencies, VAT, and approval tiers |
| **Central Governance & Auditing:** Unified dashboard, credential vault, security event logging | **Local Operational Schedules:** Store opening hours, morning batch timings, local branch rosters |

### Three-Wave Phased Rollout (Reference Working Scenario)

```
  Wave 1: Market 1 (e.g. DK)        Wave 2: Market 2 (e.g. NO)         Wave 3: Market 3 (e.g. SE)
  Focus: B2B Manual Processes       Focus: Store Operations            Focus: Delivery & Fulfilment
  ┌─────────────────────────┐       ┌───────────────────────────┐      ┌───────────────────────────┐
  │ • Bot A: B2B Quote Desk │ ───>  │ • Supplier Goods Receipt  │ ───> │ • Heavy Haulier / Crane   │
  │ • Bot B: Core Materials │       │   Discrepancy Matcher Bot │      │   Carrier Tracking Bot    │
  │   Shortage Alert        │       │ • Commodity Price Tag &   │      │ • Job-Site Delay Alert Bot│
  │ • Validate Accelerator  │       │   Bin Label Sync Bot      │      │ • Proof-of-Delivery (POD) │
  │ • Train Champions       │       │ • Pro-Pickup Staging Bot  │      │   Reconciliation Bot      │
  └─────────────────────────┘       └───────────────────────────┘      └───────────────────────────┘
```
*Note: Denmark, Norway, and Sweden represent the case study's working scenario; market sequence and operational pairings are fully configurable. Bot B from Wave 1 serves as the direct operational bridge to store routines in Wave 2, while its exception-alerting architecture provides the exact blueprint for delivery tracking in Wave 3.*

### Federated Operating Model
- **Central Platform Team (1–2 FTEs):** Maintains core orchestrator, certifies new reusable Python modules, and governs security/infrastructure.
- **Local Automation Champions (1 per operating market):** Business power users who build and adapt automations via the AI Chat Builder without writing code.
- **Shared Template Marketplace:** A bot built in the initial market is published as a template—subsequent markets can deploy it with 1 click, simply swapping local system assets.

### Top 3 Executive Risks & Mitigations
1. **Legacy Systems Lacking Modern APIs:** Architecture is strictly *API-First, UI-Fallback*. Bots utilize modern REST/OData endpoints where available, but Bot Agents include headless browser automation (Playwright/Selenium) for legacy portals.
2. **AI Reliability & Hallucinations:** AI is restricted to structured parameter extraction and certified template assembly. All financial transactions require human review; model runs in EU datacenters under GDPR.
3. **Cross-Border Adoption Resistance:** Positioned as an employee superpower ("eliminating typing, not jobs"). Local champions shape automations, and visible time-saved metrics build grass-roots trust.

*Visual:* Geographic map visual showing Wave 1 seeding the shared template library → expanding into Wave 2 (store operations) → Wave 3 (logistics/fulfilment).

---

## Slide 10 — Roadmap, governance & decision requested

**Key message:** Accelerator deployed in weeks, first live business value from Week 11, multi-market scale in under a year—with a modular timeline and adaptable architecture ready to align with Company A's roadmap.

### Indicative Pilot Roadmap (~12–14 Weeks · Adaptable Sizing)

| Phase | Timeline | Deliverables & Milestones | Stage Gate / Exit Criteria |
|---|---|---|---|
| **Phase 1: Discover & Baseline** | Weeks 1–2 | • Measure baseline quote times & error rates<br>• Map ERP endpoints / UI screens & confirm tech stack<br>• Select 5–10 inside sales & store pilot users | Signed off baseline metrics & system connectivity verified |
| **Phase 2: Accelerator Tailoring** | Weeks 3–6 | • Deploy Open Auto cloud orchestrator instance<br>• Configure initial tenant, RBAC & audit logging<br>• Install Bot Agents on pilot VMs/PCs | End-to-end telemetry & agent heartbeats verified |
| **Phase 3: Bot Assembly & Testing** | Weeks 5–10 | • Assemble Bot A (Quotes) & Bot B (Shortages)<br>• Validate AI IDP extraction on 100 historical orders<br>• User acceptance testing in ERP sandbox | ≥95% field extraction accuracy & zero unauthorized writes |
| **Phase 4: Live Pilot & Measurement** | Weeks 11–14 | • Live production run with 5–10 pilot users<br>• Daily KPI tracking (time saved, errors, NPS)<br>• Calibrate business case for subsequent markets | **Gate Review:** Formal Go / No-Go decision to scale |
| **Wave 2: Market 2 Expansion** | Months 4–7 | • Onboard secondary market tenant & local ERP adapter<br>• Deploy store operations bots (adapted from Bot B) | Store labor savings validated across retail network |
| **Wave 3: Market 3 Expansion** | Months 7–11 | • Onboard tertiary market tenant & WMS/TMS adapters<br>• Delivery tracking & carrier exception bots | Customer delivery resolution times reduced |

### Strategic Advantages of the Open Auto Approach
- **Zero Platform Licensing Penalty:** Traditional enterprise RPA vendors (UiPath, Power Automate) charge €5k–€10k/year per unattended bot plus user seat licenses. Open Auto's open Python bot model scales to hundreds of automations with zero per-bot software fees.
- **Rapid Time-to-Value via Accelerator IP:** We avoid building plumbing from scratch by tailoring our pre-tested accelerator, de-risking the pilot timeline while keeping components fully customizable.
- **Architected for Multi-Market from Day 1:** Multi-tenant separation ensures all markets maintain complete data sovereignty and local business rules on one shared infrastructure.

### Validated Pilot Assumptions
- Local ERP exposes REST/OData or SOAP endpoints; UI automation fallback (Playwright) available if specific screens lack APIs.
- Contractor quote volume is ~400 requests/day in the pilot market, ~75% received via email attachments (PDF/Excel/images). See assumptions A1–A7 on Slide 8.
- Company A grants standard cloud hosting approval for EU-based, GDPR-compliant inference (cloud provider to be aligned during discovery).
- 5–10 representative pilot users are allocated 2 hours/week for training, feedback, and baseline measurement.
- **Timeline & Stack Flexibility:** The ~12–14 week timeline is an indicative benchmark with 2-week agile sprints, ready to be compressed or adjusted once the organizer's official schedule is announced. Tech stack is a planned baseline adaptable to Company A's ecosystem.

---

### Decision Requested from Executive Leadership

> **Approve the Indicative Pilot Phase (~12–14 weeks, calibrated at kickoff | ~€130k–€150k investment):**
> - **Weeks 1–2:** Measure operational baseline, confirm system access, and freeze final tech stack.
> - **Weeks 3–10:** Tailor the Open Auto accelerator and configure Bot A (B2B Quotes) and Bot B (Store Shortages).
> - **Weeks 11–14:** Run a live production pilot with 5–10 users to measure per-quote savings, then recalculate the **~€570k/year** Denmark net value before regional rollout.

---

## Appendix: Strategic Alignment & Case Review Notes

*(Documenting resolution of consulting evaluation criteria & scenario planning)*

1. **MVP Bot Pair Validation (Fast-to-Demo & Pragmatic):** Confirmed Bot A (B2B Quote Draft Generator) + Bot B (Morning Inventory Safety-Stock Alert). Both were intentionally chosen for the MVP because they are **fast to demo** (20–30 second visual before/after), **low in technical complexity** (read-only catalog lookups + draft PDF/Excel generation, zero risky ERP database writes), and prove both event-driven AI extraction and scheduled routine automation.
2. **Benchmark Credibility:** The labour cost comes from Eurostat (Denmark €51.7/h, 2025). The manual order-entry error range (1–3%) is the APQC figure as widely cited. Handling times, volumes and conversion effects are explicit assumptions (A1–A7), to be measured in discovery. Revenue upside is shown as sensitivity, not in the base case.
3. **Integration Feasibility:** Formally defined as "API-First, UI-Fallback". Leverages modern APIs where available, with native headless browser automation (Playwright/Selenium) as a proven fallback for legacy screens.
4. **Presentation & Demo Strategy:** The 10-slide executive deck relies on a crisp 3-step visual storyboard (Prompt → Assembled Workflow → Generated Quote) on Slides 5 and 6, avoiding fragile live network demos during high-stakes board presentations.
5. **Scenario Planning & Flexibility:** The 12–14 week pilot duration, the three-market sequence (DK → NO → SE), and the specific tech stack components represent a solid, defensible baseline plan. All elements are modular and will be formally tuned to organizer guidelines and Company A's enterprise IT standards during Phase 1 discovery.
