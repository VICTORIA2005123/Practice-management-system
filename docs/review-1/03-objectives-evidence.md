# Objectives and how each one is shown

Every objective in the [project definition](01-project-definition.md) has a number or a yes/no check attached. This page says what "done" means for each, and what to put in front of the panel to prove it. At Review 1 nothing here is shown yet. It is the promise that Reviews 2 and 3 will be marked against.

A rule for all five. The proof is an automated test that anyone can run again, plus one screen that shows the same thing to a person. A screenshot alone proves nothing, because a screenshot can be staged. A test that fails when the feature breaks is the real evidence.

## Objective 1. Client register that rejects bad PAN and GSTIN

**Target.** 100% of a written set of format test cases pass.

**What done looks like.** A table of test cases, at least 30, written before the code:

| Input | Expected |
|---|---|
| `ABCPE1234F` | accepted, entity type "Individual" (4th character P) |
| `ABCFE1234F` | accepted, entity type "Firm" (4th character F) |
| `ABCPE1234` | refused, too short |
| `abcpe1234f` | accepted after converting to capitals |
| `27ABCPE1234F1ZB` | GSTIN accepted, state code 27 is Maharashtra, PAN inside it matches the client's PAN |
| `27ABCPE1234F1Z5` | refused, the check digit should be B |

**How to show it.**
1. Open the test report in the terminal or in the CI run on GitHub. Point at the line "N passed, 0 failed".
2. On the client form, type a bad PAN. The form refuses it and says why. Type a good one and the entity type fills itself in.

**What to say.** "The 15th character of a GSTIN is a check digit computed from the other 14. I validate it the way the GST network does, so a typing mistake is caught here and not on the portal."

## Objective 2. Recurring compliance tasks with no manual entry

**Target.** For a test set of clients, every due task exists with the correct due date, and nobody typed it in.

**What done looks like.** A test that sets up, for example, 10 clients engaged for monthly GSTR-3B, 4 for quarterly TDS and 10 for yearly ITR. It moves the clock through a full financial year (1 April to 31 March) and counts the tasks. The expected count is 10 × 12 + 4 × 4 + 10 × 1 = 146, each with the due date the law sets.

**How to show it.**
1. Run the test and show "146 tasks created, 146 expected".
2. On screen, engage one client for monthly GST. The next period's task appears in the task list with its due date and an assignee.

**What to say.** "Due dates change. The government extends them often. So due dates are data the firm can edit, not numbers buried in code."

## Objective 3. DSC expiry warnings 30 days ahead

**Target.** Zero missed expiries when the clock is moved forward in testing.

**What done looks like.** A test registers certificates expiring on different dates, then moves the system clock forward a day at a time for a year. On each day it checks that every certificate within 30 days of expiry is on the warning list, and that none of the others are.

**How to show it.**
1. The test result, with its count of days and certificates checked.
2. The DSC register screen with one certificate due in 20 days, marked as a warning.

**What to say.** "I don't trust a test that waits for real time to pass. The system reads time from a clock I can control in tests, so a year of expiries checks in seconds."

## Objective 4. Audit trail of 100% of changes, kept three years

**Target.** Every create, change and delete is recorded with who, when, the old value and the new value.

**What done looks like.** The audit trail is written by the database itself through triggers, not by each screen. A screen that forgets to log is then impossible, because the database logs whatever reaches it. A test changes one record in each table and checks that a matching audit row exists for each change. A scheduled job removes rows older than three years, and a test proves that it does.

**How to show it.**
1. Change a client's phone number, then open that client's history. It shows the old number, the new number, the person and the time.
2. The test that walks every table.

**What to say.** "If logging lives in the application, one forgotten line means a silent gap. Putting it in the database means the gap can't happen."

## Objective 5. Protecting client data under the DPDP Act 2023

**Target.** Three checks, each yes or no:
- Every user signs in with a password plus a six-digit code from an authenticator app (TOTP).
- Client portal passwords are stored encrypted, and every time someone reveals one, the reveal is logged with who and when.
- No real client data exists on any test or staging deployment.

**How to show it.**
1. Sign in on screen. The app asks for the six-digit code.
2. Reveal a stored password. Then open the log and show that reveal recorded under your name.
3. Show that the staging database is filled by a script that generates fake clients.

**What to say.** "Under the DPDP Act the firm is a data fiduciary. It has to protect the data and be able to show it did. Logging reveals is what lets the firm answer the question 'who looked at this client's password?'"

## Summary for the slide

| # | Objective | Measure | Proof |
|---|---|---|---|
| 1 | Validate PAN and GSTIN, derive entity type | 100% of 30+ format cases pass | Test report, client form |
| 2 | Create recurring tasks with no manual entry | 146 of 146 tasks in a simulated year | Test report, task list |
| 3 | Warn 30 days before DSC expiry | 0 missed in a simulated year | Test report, DSC register |
| 4 | Audit every change, keep three years | 100% of tables covered | Test report, client history |
| 5 | Protect client data (DPDP Act 2023) | 3 of 3 checks pass | Sign-in, reveal log, staging data |
