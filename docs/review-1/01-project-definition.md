# Project definition

Project (01CT3801), Department of Information and Communication Technology, Marwadi University.

| Field | Value |
|---|---|
| Student name | |
| Enrolment number | |
| Type of project (IDP/UDP/FDP) | IDP |
| Individual or group | Individual |
| Guide | |
| Co-guide | |

## Title

A Keyboard-First Practice Management System for Small CA Firms with Automated Compliance Workflows

## Problem statement

<!-- HBK and [N clients, M staff] are placeholders. In the .docx they are bold red. -->

A small chartered accountant's firm in India files the same returns for the same clients month after month: GST returns, TDS statements, income-tax returns, ROC filings. **HBK**, the firm this project is built with, handles **[N clients, M staff]**. Today that work is tracked in Excel spreadsheets and WhatsApp messages. Nobody can see at a glance which return is pending, who has it, or what changed and when. Digital signature certificates (DSCs) expire quietly, and a filing then stalls on the due date. A missed date costs the client a late fee for every day of delay and costs the firm its credibility. This project builds a practice management system that creates this recurring work by itself, shows who holds each task, warns before DSCs expire, and records every change in an audit trail.

## Who is affected

- The firm's partners, who answer for every missed deadline.
- Its staff (articled assistants and accountants), who keep track of dozens of due dates in their heads.
- The firm's clients, mostly small businesses and individuals, who pay the late fees.

## Scope for this semester

Three modules, chosen because each one removes a specific failure in the firm's current process.

1. **Client register.** Every client's PAN, GSTIN, contacts and branches in one place. The entity type (individual, firm, company, trust) comes from the fourth character of the PAN, so staff don't pick it by hand.
2. **Recurring compliance tasks.** When a client is engaged for a service, such as monthly GST returns, the system creates each period's task with its due date, assigns it, and tracks it until it is filed. Every change goes into an audit trail kept for three years.
3. **DSC register.** Each client's digital signature certificate, its holder and its expiry date, with a warning well before it lapses.

Out of scope for now, and planned for later reviews: automated filing on the income-tax and GST portals, a client-facing portal, billing.

## Objectives

1. Build a client register that rejects every malformed PAN and GSTIN and derives the entity type from the PAN, passing 100% of a written set of format test cases.
2. Create recurring compliance tasks (monthly GSTR-3B, quarterly TDS, yearly ITR) from a client's services with no manual entry, so that for a test set of clients every due task exists with the correct due date.
3. Warn about every DSC at least 30 days before it expires, with zero missed expiries when the system clock is moved forward in testing.
4. Record 100% of creates, changes and deletes in an audit trail that names who made the change, when, and the old and new values, and keep it for three years.
5. Protect client data as the Digital Personal Data Protection Act, 2023 expects: two-factor sign-in, encrypted storage of portal passwords with every reveal logged, and no real client data on any test deployment.

How each objective is shown once it is done is in [objective evidence](03-objectives-evidence.md).

## Project questions

1. Can a rule-based cascade generate all of a small firm's recurring compliance work without manual entry, and which services resist it?
2. How early must a DSC expiry warning arrive for a firm to renew it without a filing being delayed?
3. What does a small firm need to keep, and for how long, to meet its duties under the DPDP Act 2023 without storing more than it needs?

## Sustainable Development Goals

- **SDG 8, Decent Work and Economic Growth (primary).** Fewer missed deadlines mean fewer penalties for the small businesses the firm serves, and less overtime for its staff in the days before a due date.
- **SDG 9, Industry, Innovation and Infrastructure.** Small professional firms are among the last to move off paper and spreadsheets. This gives one a working digital system.
- **SDG 16, Peace, Justice and Strong Institutions.** Timely, recorded tax compliance and an audit trail of who changed what make the firm more accountable.

The full mapping, with targets and indicators, is in [SDG mapping](05-sdg-mapping.md).

## Technology

TypeScript on Node.js, React for the screens, PostgreSQL for data, automated tests with Vitest and Playwright, deployed on Render.

| Signature | |
|---|---|
| Student | |
| Guide | |
| Co-guide | |
| HoD | |
