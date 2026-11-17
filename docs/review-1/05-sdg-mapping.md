# SDG mapping, sustainability and ethics

This project claims three Sustainable Development Goals: SDG 8 as the main one, SDG 9 and SDG 16. Each claim below names a UN target, quotes its text, and says what in this system serves it. A table at the end covers the gap between what a one-firm project can change and what the UN measures.

Target wording is from the UN's SDG pages ([Goal 8](https://sdgs.un.org/goals/goal8), [Goal 9](https://sdgs.un.org/goals/goal9), [Goal 16](https://sdgs.un.org/goals/goal16)).

## An honest limit first

The UN's indicators are national statistics, such as "annual growth rate of real GDP per employed person". One firm using one piece of software will not move India's GDP figures, and claiming it would is the fastest way to lose a panel. So every SDG below has two indicators: the UN's, which says *which direction* the project pushes, and a **project indicator**, which this project can actually measure at **HBK**.

## SDG 8. Decent Work and Economic Growth (primary)

**Target 8.2.** "Achieve higher levels of economic productivity through diversification, technological upgrading and innovation, including through a focus on high-value added and labour-intensive sectors."

**Target 8.3.** "...encourage the formalization and growth of micro-, small- and medium-sized enterprises, including through access to financial services."

**How the project serves it.**
- A CA firm's staff spend hours each month creating the same tasks and chasing the same deadlines. The system creates them by itself, so those hours go to review and advice, which is the higher-value part of the job.
- The firm's clients are mostly micro and small businesses. For them, a late GST return means a late fee for every day of delay, and their buyers can't claim input tax credit on their invoices until they file, so buyers start to avoid them. On-time filing keeps them in the formal tax system and keeps their records clean when they apply for a loan, which is target 8.3's "access to financial services".
- Staff stop working late in the days before a due date, because the deadline was visible weeks earlier. That is the "decent work" half of the goal.

**Project indicators.**
- Filings that missed their due date at HBK, before and after (target: zero caused by the firm).
- Hours a month spent creating and tracking tasks by hand, before and after.
- Late fees paid by HBK's clients for filings the firm handled.

**The tension, stated plainly.** Automation removes clerical work, and clerical work is how some junior staff get hired. My answer is that the system takes over the bookkeeping *of the work*, not the work itself. Somebody still prepares and checks each return. But the question is fair, and I would rather raise it than have the panel find it.

## SDG 9. Industry, Innovation and Infrastructure

**Target 9.3.** "Increase the access of small-scale industrial and other enterprises, in particular in developing countries, to financial services, including affordable credit, and their integration into value chains and markets."

**Target 9.c.** "Significantly increase access to information and communications technology..."

**How the project serves it.**
- Small professional firms are among the last businesses in India to leave Excel and WhatsApp. Large firms buy enterprise software. A 10-person practice usually can't afford it, and the tools it can afford are built for accounting, not for running the office (see the [literature survey](04-literature-survey.md)).
- The system runs in a browser and installs on a phone, so it needs no special hardware. It is built on free, open-source parts (Node.js, React, PostgreSQL), which keeps the cost within reach of a small firm.
- Clients whose filings are current and recorded are easier to integrate into "value chains and markets": a buyer or a bank checking a supplier's GST compliance sees a clean record.

**Project indicators.**
- Share of HBK's recurring work tracked in the system instead of spreadsheets (target: 100% of the three modules' work).
- Running cost per month, compared with commercial practice-management tools.

## SDG 16. Peace, Justice and Strong Institutions

**Target 16.6.** "Develop effective, accountable and transparent institutions at all levels."

**How the project serves it.**
- A CA firm is part of how the tax system works. It sits between the taxpayer and the government. Its records need to show who did what and when.
- The audit trail records every change with the person, the time, and the old and new value, and keeps it for three years. The database writes it, so no screen can skip it. If a client asks "who changed my GSTIN?", the firm has an answer.
- Tax compliance itself feeds public revenue. SDG target 17.1 asks countries to "strengthen domestic resource mobilization... to improve domestic capacity for tax and other revenue collection". On-time, correct filing by thousands of small businesses is how that happens on the ground.

**Project indicators.**
- Share of changes covered by the audit trail (target: 100%, proven by a test).
- Questions about "who changed this" that the firm can answer from the system (target: all of them).

## Summary table

| SDG | Target | What the system does | Project indicator |
|---|---|---|---|
| 8 | 8.2, 8.3 | Creates recurring work automatically, shows deadlines early | Missed filings, hours of manual tracking, clients' late fees |
| 9 | 9.3, 9.c | Affordable browser-based system for a small firm | Share of work moved off spreadsheets, monthly cost |
| 16 | 16.6 (and 17.1) | Audit trail of every change, kept three years | Share of changes audited |

## Ethics and data protection

### What data the system holds

A CA firm holds some of the most sensitive data a person has: PAN, Aadhaar-linked details, bank accounts, income, and the passwords to clients' income-tax and GST portal accounts. If that data leaks, a client can be impersonated on the tax portal.

### The law: Digital Personal Data Protection Act, 2023

The DPDP Act, 2023 is India's personal data law. The DPDP Rules, 2025 were notified in November 2025, and most duties take effect in phases over the 18 months that followed ([PIB release](https://static.pib.gov.in/WriteReadData/specificdocs/documents/2025/nov/doc20251117695301.pdf)). Under the Act, the firm is a **data fiduciary**: it decides why and how client data is processed. Its main duties, and what the system does about each:

| Duty under the Act | What the system does |
|---|---|
| Protect personal data with reasonable security safeguards | Two-factor sign-in for every user. Portal passwords encrypted with a key kept apart from the database. |
| Be able to show what happened to the data | Audit trail of every change. Every reveal of a password is logged with who and when. |
| Keep data only as long as needed | Audit records are kept for three years and then removed by a scheduled job. |
| Collect only what the purpose needs | The client register stores only what filings need. No documents are copied in "just in case". |

Failing to take reasonable security safeguards can bring a penalty of up to Rs 250 crore under the Act's schedule. For a small firm, the bigger risk is losing its clients' trust.

### Ethics of how it is built and tested

- **No real client data outside production.** The staging site is filled with generated, fake clients. Developers and testers never see a real PAN.
- **Least privilege.** A staff member sees a portal password only when they ask to reveal it, and the reveal is logged. Nobody browses passwords.
- **Accessibility.** Every action works from the keyboard, and automated checks (axe-core) look for accessibility faults on every screen. A staff member who can't use a mouse well can still do the job.
- **Honest use of AI tools.** I used AI coding assistants during development, as working engineers now do. Every design decision is written down with its reasons, every feature has tests, and I can explain any part of the system. The decisions and their trade-offs are mine.

### Environmental note

Moving from paper and printouts to a shared system saves some paper. The system also runs on a cloud server that uses electricity. At one firm's scale both effects are small, and I am not claiming an environmental SDG for that reason.
