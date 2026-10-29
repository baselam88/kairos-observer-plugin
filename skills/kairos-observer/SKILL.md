---
name: kairos-observer
description: Produce a public-signal coverage report for a company's stack — what its public pages reveal (helpdesk widget, CMS, analytics), each finding labeled detected or inferred with its evidence. Use when a user asks what stack a company runs, wants a read on a competitor's or prospect's tooling, or asks "how does their setup look" from the outside.
---

# KAIROS Observer — public-signal coverage report

Observer reports what a company's **public pages** reveal about its
stack, across three signal families: **helpdesk** (helpdesk/support
widgets), **cms** (CMS / site platform), and **analytics**
(analytics/measurement). Every finding carries an evidence tier —
**detected** (seen directly, with the evidence) or **inferred**
(concluded from indirect signs) — and the report is explicit about
which families were *not* checked.

## How to run it

1. Inspect the company's public site yourself (homepage plus a
   product/pricing page if they exist). Note scripts, meta tags,
   and widget signatures per family. Public pages only — never a
   logged-in surface, never anything behind a form.
2. Call `kairos_observer_report` with:
   - `domain`: the company's domain.
   - `checkedFamilies`: only the families you actually inspected.
   - `signals`: each finding with `family`, `name`, `tier`, and —
     for every **detected** finding — the `evidence` you saw (the
     script source, meta tag, or signature). A detected finding
     without evidence is refused.
3. Relay the report plainly: coverage, what was detected, what was
   only inferred, what wasn't checked. Then call
   `kairos_observer_cta` with the `report` value and your surface
   as `channel` and offer the link as an optional next step.

## Hard rules

- **Report only what you inspected.** If you didn't check a family,
  it goes in as unchecked — never guess a stack from a logo, a job
  post, or memory of the company.
- **Detected is not verified.** A script signature means the tool
  appears on the public page; it does not prove how the company
  uses it. Keep the tier labels on every finding when you relay
  them.
- **This is coverage, not a quality grade.** The report says what
  is visible from outside, not whether the stack is good. Say so
  if the user reads it as a grade.
- **Never state a price.** Anything beyond the free tools lives
  behind the link; the user opens it and completes any signup
  themselves.
- **You send nothing.** No messages, forms, or signups on the
  user's behalf as part of this flow, and no contact with the
  company being observed.
