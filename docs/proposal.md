# Proposal: A-Flow — Retail Workflow Automation for Company A

> Draft v1. 10 slides max, PDF, English. Each section = one slide: **Key message**, content, suggested visual.
> Numbers marked *(assumption)* are illustrative and must be validated in discovery.

---

## Slide 1 — Title

**A-Flow: Let the system do the re-typing, let people do the thinking**

- Low-code workflow automation for Company A's manual processes
- One platform. Three markets. Local adapters.
- Team name · date

*Visual:* a simple canvas screenshot of the drag-and-drop builder (email → AI extract → ERP → approval → quote).

---

## Slide 2 — The real problem

**Key message:** The problem is not "manual work" in general. It is people acting as the glue between fragmented systems.

What employees actually do today:

| Who | Manual work |
|---|---|
| B2B inside sales | Read quote requests in email / PDF / photos, re-key into ERP, check stock and credit by hand |
| Store staff | Count shortages, phone or email HQ, update price labels by hand |
| Customer service | Sort shared inbox, answer the same questions, chase carriers |
| Regional managers / HQ | Ask staff for reports (e.g. Google Maps reviews of every store → Excel → email) |

Why it persists:
- Every country has its own systems, so no central fix has been possible.
- Inputs are unstructured (email, PDF, phone), so classic integration cannot read them.
- The tasks are too small for IT projects, but large in total.

Consequences: slow quotes, wrong SKUs, inconsistent customer experience, staff time spent on typing.

*Visual:* "day in the life" of one inside-sales employee, with the re-typing steps highlighted.

---

## Slide 3 — Why prioritise manual processes

**Key message:** Manual processes sit upstream of the other challenges. Fix them first and the rest improves.

| Challenge | Impact | Reach (3 markets) | Time to market | Needs system replacement? |
|---|---|---|---|---|
| **Manual processes** | High: touches every role | All three | Fast: sits on top of existing systems | **No** |
| Store operations | High in NO | Partly local | Medium | Partly |
| Delivery & fulfilment | High in SE | Partly local | Medium to slow | Often (WMS/TMS) |
| Fragmented systems | High, long term | All three | Slow (multi-year) | **Yes** |

Reasoning:
- Re-keyed orders are a source of delivery errors, and manual store routines are a source of inconsistent operations. Removing the manual layer reduces both.
- Replacing fragmented systems takes years. A layer on top delivers value now and does not block that long-term path.
- Denmark is the first market (manual processes are the highest-impact challenge there). Norway and Sweden reuse the same platform for their own priorities (slide 9).

*Visual:* prioritisation matrix (impact vs time to market) with manual processes top-right.

---

## Slide 4 — The solution

**Key message:** A-Flow is a drag-and-drop workflow builder with retail-specific building blocks. It does not replace the ERP; it removes the human glue around it.

How it works:
1. **Trigger:** an email arrives, a PDF is uploaded, a schedule fires.
2. **Understand:** AI extracts structured data from unstructured input.
3. **Act:** connectors read/write ERP, WMS, POS, web portals.
4. **Decide:** rules and human approval for exceptions only.
5. **Deliver:** quote, Excel/PDF report, email, Teams message.

Design principles:
- Built by business users (store managers, sales leads) on a visual canvas, not by IT tickets.
- Every run is logged: who, what, which data. Auditable.
- Human in the loop by default; automation earns trust step by step.

*Visual:* architecture sketch: sources → A-Flow (builder, engine, AI, connectors) → existing systems.

---

## Slide 5 — Building blocks

**Key message:** About 30 ready-made blocks cover the most common manual tasks. New blocks are plugins, not rebuilds.

| Group | Blocks |
|---|---|
| Triggers | Email received · Web form · Upload PDF/photo · Schedule · Webhook / system event |
| AI | Extract structured data · Classify intent · Draft / translate reply · Summarise |
| System connector | One generic ERP / WMS / POS / carrier connector (get, create, update). Country adapter set in configuration |
| Web | HTTP request · Web scrape · Browser automation (portals without API) · Page monitor |
| Logic | IF / Switch · Loop over lines · Wait · Retry on error · Sub-workflow |
| Exceptions & approval | Approve (human) · Assign task · Escalate · Request missing info |
| Output | Excel / PDF / CSV export · Email · SMS · Teams / Slack |
| Reconcile & report | Compare two sources · Scheduled report · Log + metrics |

Note: stock, price, credit checks are calls to the existing ERP through the connector. We do not rebuild what the ERP already does.

*Visual:* palette panel from the builder UI.

---

## Slide 6 — MVP scope (Denmark, 12 weeks *(assumption)*)

**Key message:** Two workflows, one country, one ERP. Enough to prove value, small enough to ship fast.

**Workflow A: contractor quote request (high value)**
Email in → AI extracts line items → connector matches SKUs, price agreement, stock, credit → rule: auto-approve or send to sales for review → draft quote PDF → reply email.

**Workflow B: weekly store review report (quick win)**
Schedule → fetch Google reviews for all stores → AI summarises themes → Excel → email to regional manager.

| In scope | Out of scope |
|---|---|
| Visual builder with the ~15 blocks needed for A and B | Full block library (others shown as roadmap) |
| Denmark, one ERP adapter, Danish language | Norway, Sweden adapters |
| Human approval step, run log, basic dashboard | Advanced analytics, mobile app |
| 5 to 10 pilot users (inside sales + 1 regional manager) | Company-wide rollout |

Technical note: React Flow canvas, Node.js engine, Postgres, Claude API for extraction and summarisation.

*Visual:* the two workflows drawn as node diagrams.

---

## Slide 7 — Where AI creates value

**Key message:** AI handles messy inputs; deterministic rules and humans handle decisions.

| Use | What it replaces | Safeguard |
|---|---|---|
| Extract order lines from email / PDF / photo | Reading and re-typing | Confidence score; low confidence goes to a person |
| Match free text to SKU | Searching the catalogue by hand | Top-3 suggestions, human confirms on ambiguity |
| Classify and route inbox | Manual sorting | Rules for escalation |
| Draft replies in DK / NO / SE | Writing the same email | Human sends in pilot |
| Summarise reviews / complaints | Reading hundreds of comments | Link to source comments |
| **Describe a task in words, get a workflow draft** | Waiting for IT | User reviews before activation |

Principles: no autonomous price or credit decisions, EU data handling (GDPR), every AI output traceable to its input.

*Visual:* one email with highlighted fields becoming a structured quote.

---

## Slide 8 — Business impact

**Key message:** Faster quotes, fewer errors, hours back to people. Measured from the pilot, not promised.

Illustrative model for Workflow A in Denmark *(all inputs are assumptions)*:

| Input | Value |
|---|---|
| Quote requests per working day | 400 |
| Manual handling time per request | 12 min |
| Handling time with A-Flow (review only) | 4 min |
| Working days per year | 220 |
| Loaded cost per hour | €40 |

Result: 400 × 8 min × 220 days ≈ 11,700 hours/year ≈ **€470k/year** from one workflow in one country, before counting error reduction and faster response.

KPIs tracked in the pilot:
- Time from request to quote (hours to minutes)
- % requests handled without re-typing
- SKU / price error rate
- Employee time freed and NPS of pilot users
- Conversion of quote to order

Pilot-first rule: the real baseline is measured in weeks 1 to 2, and the business case is recalculated before scaling.

*Visual:* before / after timeline of one quote.

---

## Slide 9 — Scale across markets

**Key message:** One platform, three implementations. Same workflows, different adapters and priorities.

**What is shared:** engine, builder, AI, block library, template library, governance.
**What is local (configuration, not code):** ERP adapter, VAT and legal rules, language, currency, local approval limits.

| Wave | Market | Focus | Reuses |
|---|---|---|---|
| 1 | Denmark | Quote / order intake, reporting | Pilot workflows |
| 2 | Norway | Store operations: shortage reports, price label updates, daily routines | Same engine, new templates, NO adapter |
| 3 | Sweden | Delivery: carrier status checks, delay notifications, order-to-delivery reconciliation | Same engine, new templates, SE adapter |

Operating model:
- Small central team owns platform and templates; local "automation champions" in each country build and adapt workflows.
- Template marketplace: a workflow built in Denmark is a one-click starting point in Norway.

People and change:
- Position as "less typing, more customer work", not job cuts. Involve staff in choosing which tasks to automate first.
- Training and a feedback channel in each country.

Risks and mitigations:

| Risk | Mitigation |
|---|---|
| Browser automation breaks when a portal changes | Prefer APIs; monitoring and alerts; fallback to human task |
| Credentials and data security | Encrypted secret vault, role-based access, audit log |
| Wrong AI output | Confidence thresholds, human approval in pilot |
| Low adoption | Champions, quick wins first, visible time saved |
| Scraping / terms of service | API first, scrape only where permitted |

---

## Slide 10 — Roadmap and assumptions

**Key message:** Value in 12 weeks, scale in 12 months.

| Phase | Timing | Outcome |
|---|---|---|
| Discover | Weeks 1 to 2 | Baseline measured, ERP access, pilot users chosen |
| Build MVP | Weeks 3 to 8 | Builder + Workflows A and B in test |
| Pilot | Weeks 9 to 12 | 5 to 10 users live, KPIs reviewed, go / no-go |
| Scale DK | Months 4 to 6 | More workflows, more stores |
| Norway, Sweden | Months 7 to 12 | Adapters, local templates |

Key assumptions (to validate):
- Company A's ERP in Denmark exposes an API or an integration layer.
- Quote requests arrive mostly by email / PDF and volume is in the range above.
- Pilot users and a business sponsor are available.
- Google Business Profile access exists for stores (needed for full review data; the public Places API returns only a handful of reviews per place).
- Data can be processed in the EU under Company A's GDPR policy.

Decision requested: approve a 12-week Denmark pilot with the two workflows.

---

## Open questions for the team

1. Is Workflow A (quotes) plus B (reviews) the right pair, or should B be a different quick win?
2. Which numbers on slide 8 can we back with public sources or a stated benchmark?
3. Build a clickable demo of the canvas to attach as a link / screenshots in the deck?
