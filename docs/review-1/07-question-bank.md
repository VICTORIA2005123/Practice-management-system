# Question bank for Review 1

Fifty questions a panel is likely to ask, with short answers. Read the answer, then say it in your own words. Don't memorise it. A panel can tell a recited answer from an understood one within a sentence.

Where an answer names **HBK** or a number in red in the Word copy, replace it with the real one before the review.

## A. The problem and the domain

**1. What problem does your project solve, in one sentence?**
Small CA firms lose track of recurring tax deadlines because the work lives in Excel and WhatsApp, and this system creates that work by itself, shows who holds it, and records every change.

**2. Who is your user?**
The staff and partners of a small chartered accountant's firm, 2 to 20 people. The firm's clients never log in. They benefit indirectly, through filings made on time.

**3. What is a practice management system?**
Software for running a professional office rather than doing its accounting: which clients the firm has, what work is due for each, who is doing it, and what happened. Tally or Genius prepares a return. A practice management system makes sure somebody prepares it before the due date.

**4. Why can't a firm just use Excel?**
Excel can't create next month's task by itself, can't warn anyone, and can't say who changed a cell last March. Two people editing one sheet overwrite each other. It works for 20 clients and breaks at a few hundred.

**5. What is a recurring compliance task? Give an example.**
A filing that comes back every period. A GST-registered client files GSTR-3B every month, so that's 12 tasks a year per client, each with a due date, a preparer and a status. Multiply by hundreds of clients and you see why nobody should create them by hand.

**6. What is a DSC and why track its expiry?**
A Digital Signature Certificate is the electronic signature used to sign filings on the MCA and income-tax portals. It's issued for one or two years. If it expires, the filing can't be signed, and getting a new one takes days of verification. A warning 30 days ahead turns a missed deadline into a routine renewal.

**7. What is a PAN and why does the fourth character matter?**
PAN is the 10-character tax ID: five letters, four digits, one letter. The fourth character is the holder's status as the Income Tax Department classifies it: P for an individual, C for a company, F for a firm, T for a trust, and six others. The system reads the entity type from it instead of asking staff to pick, and allows an override only with a written reason, because the department's letter doesn't always match the legal form.

**8. What is a GSTIN and how do you validate it?**
A 15-character GST number. The first two digits are the state code, the next ten are the PAN, then an entity number, the letter Z by default, and a check digit. The check digit is computed from the other 14 characters, so a single typing mistake is caught before the number ever reaches the GST portal.

**9. How did you find out what the firm needs?**
I worked at **HBK** during my internship. I sat with the staff, watched how they track work in Excel and WhatsApp, and asked partners which failures cost the most. Missed deadlines and expired DSCs came up first.

**10. What happens today when a deadline is missed?**
The client pays a late fee for every day of delay, and for GST their buyers can't claim input tax credit until the return is filed. The firm usually absorbs the blame and sometimes the fee.

## B. Objectives and scope

**11. What are your objectives?**
Five, each with a number: validate PAN and GSTIN with 100% of test cases passing, create recurring tasks with no manual entry, warn about every DSC 30 days ahead with none missed, audit 100% of changes for three years, and meet three data-protection checks.

**12. How will you prove an objective is met?**
With an automated test that fails if the feature breaks, plus one screen that shows the same thing. For DSC warnings, the test moves the system's clock through a whole year and checks every day's warning list.

**13. Why only three modules?**
Each one removes a specific failure: wrong client data, forgotten recurring work, expired signatures. Doing three properly beats doing ten halfway. Portal automation and a client portal come later.

**14. What is out of scope?**
Filing returns automatically on government portals, a portal for clients, billing and accounting itself. The firm keeps using its accounting software for that.

**15. Which objective is hardest and why?**
Recurring tasks. Due dates change when the government extends them, services differ by client, and a task must be created exactly once, never twice. Getting "exactly once" right when two things happen at the same time is the hard part.

**16. Are your objectives achievable in one semester?**
Yes, because the scope is three modules and the technology is ordinary: a web app with a database. Nothing depends on research that might not work.

## C. Literature and existing tools

**17. What existing software did you compare?**
TallyPrime, Zoho Practice, an Indian CA-office product, Karbon and TaxDome. The table is in the literature survey.

**18. Why not just buy one of them?**
The foreign tools (Karbon, TaxDome) are built around US and UK practice. They don't know GSTR-3B or Indian DSCs, and they're priced per user in dollars. The Indian tools focus on preparing returns, not on running the office's workflow and audit trail. None of them combines Indian recurring compliance, DSC tracking and a full audit trail at a small firm's budget.

**19. What did the research papers tell you?**
Three things kept coming up. Small firms adopt technology slowly, mostly because of cost and skills. Automation pays off on repetitive, rule-based work, which recurring compliance is. And most studies look at large firms or Western countries, which leaves small Indian practices unstudied.

**20. What is the research gap?**
Studies of practice software and automation focus on large firms and on preparing returns. None of the reviewed works addresses tracking recurring Indian compliance deadlines, DSC expiry and an audit trail together for a small firm.

**21. How did you choose the papers?**
Published in the last five years, peer-reviewed, and about one of: technology adoption in accounting firms, automation in accounting or tax work, tax technology in India, audit trails, data protection, or digital certificates. I read every abstract myself and recorded each paper's limitation.

**22. Which paper influenced your design most?**
Pick the one you remember best from the survey, and say which design decision it changed. Prepare this one yourself.

## D. SDGs, sustainability and ethics

**23. Which SDGs does your project address?**
SDG 8 mainly, through targets 8.2 (productivity through technology) and 8.3 (growth and formalisation of small businesses). Also SDG 9 (target 9.3, small enterprises) and SDG 16 (target 16.6, accountable and transparent institutions).

**24. How does a CA-firm tool help economic growth?**
Not at the national level, and I won't claim it does. At one firm it saves hours of manual tracking and keeps small-business clients from paying late fees. My indicators are the ones I can measure at the firm: missed filings, hours spent, and late fees.

**25. Why SDG 16? That goal is about justice and institutions.**
Target 16.6 asks for accountable and transparent institutions. A CA firm sits between taxpayers and the government, and the audit trail lets it answer "who changed this, and when?" for every record. On-time tax filing also feeds public revenue, which is SDG target 17.1.

**26. Doesn't automation take jobs away?**
It removes the bookkeeping of the work, such as creating tasks and chasing dates. It doesn't remove preparing or checking returns, which needs a person. Staff spend less time on clerical tracking and more on review and advice. I'd rather admit the tension than pretend it isn't there.

**27. What is the DPDP Act and how does it affect you?**
The Digital Personal Data Protection Act, 2023 is India's data-protection law. Its rules were notified in November 2025. The firm is a data fiduciary for its clients' data, so it must protect that data with reasonable safeguards, keep it only as long as needed, and be able to show what happened to it. Two-factor sign-in, encrypted passwords, logged reveals and three-year retention answer those duties.

**28. What is the most sensitive data you store?**
Clients' passwords for the income-tax and GST portals. With one of those, someone can act as the client on the portal. So they're encrypted, revealed only on request, and every reveal is logged with who and when.

**29. Can every staff member see every client?**
Yes, deliberately for now. In a small office everyone works across clients, and a permission model built from a guess would be worked around every day. Roles still decide who can change data, passwords need a separate permission, and the audit trail shows who looked at what. When usage shows real boundaries, per-client access can be added.

**30. Do you test with real client data?**
No. The staging site is filled with generated fake clients. Real data only ever lives in the firm's production system.

## E. Technical design

**31. What is your technology stack?**
TypeScript throughout. Node.js with the Hono framework on the server, React on the screens, PostgreSQL as the database, Vitest and Playwright for tests, hosted on Render.

**32. Why PostgreSQL and not MongoDB?**
The data is relational: clients have services, services generate tasks, tasks have assignees. Relationships and constraints are exactly what a relational database enforces. PostgreSQL also runs the audit triggers, which a document database can't do the same way.

**33. Why TypeScript instead of JavaScript?**
Types catch mistakes at build time. If I rename a database column, every place that uses it fails to compile instead of failing at a client's desk.

**34. How does the audit trail work?**
One database trigger is attached to every table. On every insert, update or delete it writes a row with the table, the user, the time, and the whole record before and after. Because the database writes it, no screen or script can forget to.

**35. Why put the audit trail in the database and not in the code?**
If code writes the audit row, one forgotten line in one new feature leaves a hole, and you discover the hole exactly when you need the trail. The database sees every change, however it arrives.

**36. How are recurring tasks generated?**
Each client is engaged for services, like monthly GST. Each service has a task template with its steps. A scheduled job looks at each engagement, works out which periods are due, and creates any missing task. Who gets the task is decided by a four-level cascade, and the first level that has an answer wins: a person named on that engagement, else the client's team, else the team that handles that service firm-wide, else the department the service belongs to. The last level always matches, so no task is left unassigned. I didn't name a person for every client-service pair because a firm with a thousand clients, three services each and three roles per service would need about nine thousand such entries, and nobody would keep them up to date.

**37. What if the job runs twice? Do you get duplicate tasks?**
No. The database allows only one generation per engagement and period (a unique index), so a duplicate can't be stored even if two runs overlap. A second run finds the task already exists and does nothing.

**38. What if two people edit the same record at once?**
Each save carries the version the person loaded. If someone else saved in between, the database finds no matching version and the app refuses the save with a message, so nobody silently overwrites someone else's change.

**39. How do you handle time zones and dates?**
The firm works on Indian time, and due dates are calendar days. The server runs in UTC. So the application reads "today" from one clock set to Asia/Kolkata, and tests can move that clock, which is how a year of DSC expiries checks in seconds.

**40. How is sign-in secured?**
Password plus a six-digit code from an authenticator app (TOTP). Sessions expire. Sign-in records are kept for three years.

**41. How are the portal passwords encrypted?**
With AES-256-GCM, using a key the server holds in its environment, outside the database. Someone who steals a database backup gets encrypted text, not passwords. GCM also detects tampering: a changed ciphertext fails to open instead of decrypting to garbage. Revealing a password needs a separate permission and a fresh authenticator code, and the reveal is logged.

**42. How would it scale to a bigger firm?**
A firm with 2,000 clients and a few dozen staff is small for PostgreSQL. Lists are paged, so screens load the same at any size. The real limit would be people needing finer permissions, not the database.

**43. Is it a mobile app?**
It's a web app that installs on a phone or desktop and opens in its own window. One codebase serves both.

**44. Why keyboard-first?**
Accountants live on the keyboard. Tally trained a generation to work without a mouse. Every action has a key, which is also what makes the app usable for people who can't use a mouse well.

## F. Testing and quality

**45. How do you test it?**
Integration tests run against a real PostgreSQL database, not a fake one. End-to-end tests drive real browsers (Chrome, Firefox and Safari's engine) the way a user would. Automated accessibility checks run on every screen. All of it runs on every change in GitHub Actions.

**46. What is a property-based test?**
Instead of writing five example inputs, you describe the rule ("any valid PAN is accepted, any string with a wrong check character is refused") and the tool generates hundreds of random inputs to try to break it. It finds cases I wouldn't think to write.

## G. Your role, process and next steps

**47. What exactly did you do yourself?**
Prepare this answer in your own words, honestly. Name the parts you designed, the decisions you made and why, and what you tested. If you used AI tools, say how: for example, "I used an AI coding assistant to write code faster, and I reviewed, tested and can explain every part of it. The design decisions are written down with my reasons." A panel respects a clear answer. A vague one makes them dig.

**48. Did you use AI? Isn't that cheating?**
Same as above. Say it plainly and point to the written decision records and the tests as evidence that you understand and control the system. Engineers in industry use these tools daily. The skill being tested is whether you can design, judge and explain, so show that.

**49. What will you show at Review 2?**
The three modules working: the client register with validation, recurring tasks being created and assigned, and DSC warnings, each with the test results that prove its objective.

**50. What would you add with more time?**
Filing on the GST and income-tax portals from inside the system, a portal where clients upload documents and see their filing status, and per-client access control once the firm's usage shows where the boundaries are.
