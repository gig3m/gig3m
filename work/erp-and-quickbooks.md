# Replacing a manufacturer's ERP, and wiring it to QuickBooks

**The business:** a family pallet and lumber manufacturer in East Texas, which I run. Orders, quotes, dispatch, log purchasing, kiln records, invoicing and A/R all live in one internal system.

## The problem

The old system dated from 2017, and the books lived somewhere else. Pallet sales reached QuickBooks once a month as a single journal entry built from a report. QuickBooks showed one lump of "pallet sales" instead of real receivables per customer, so the bookkeeper and the sales office were always reconciling two versions of the truth.

## What I built

**Prism**, a new ERP (Laravel, React, Postgres) that is now the system of record. I built it with AI coding agents (Claude Code) as the main hands, and kept myself in the role of spec writer, reviewer and tester:

- every feature starts as a written plan in the repo, which the agent and I argue over before any code exists
- about 1,600 automated tests, all isolated so they never touch production data
- a review checklist for each change, plus a second agent that reviews the first one's work before anything ships

**QuickBooks sync.** Every invoice, payment and early-pay discount now posts to QuickBooks Online on its own, matched customer by customer. The design rule is *Prism does the math, QuickBooks keeps the books*: the sync only delivers numbers Prism has already decided. Anything it won't send goes on a held list with the reason, so nothing fails silently. The requirements were a written contract signed off by the company's accountant before any code was written.

## What changed

- At the October 2026 cutover, every open invoice posted to the live books with no holds or errors.
- The month-end journal entry is gone. QuickBooks A/R now matches the ERP customer by customer, every day.
- Staff have in-app help written for them (freight, board footage, pricing, tax, aging), not for developers.

## What I'd tell another small business

The win wasn't the AI writing code. It was writing down how the business actually works: the freight rules, the tax rules, which account each product hits. Once that was on paper and agreed with the accountant, the build was the easy part.
