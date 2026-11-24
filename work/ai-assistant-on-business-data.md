# Letting staff ask an AI assistant about the business, safely

**The business:** the same East Texas manufacturer ([ERP write-up](erp-and-quickbooks.md)).

## The problem

The office wanted to ask plain questions: who owes us the most and how late, what did this customer order this year, what does this product actually cost per board foot. The answers were in the ERP but sat behind reports, or behind me. An early experiment that pointed an AI assistant straight at the database proved the idea, and also showed the risk. It could read anything, nobody could tell who had asked what, and it would invent its own math for figures the ERP calculates a specific way.

## What I built

A custom connector (an MCP server) that staff add to Claude like any other app:

- **Each person signs in as themselves.** Every question runs as a real ERP user, and the audit log records who asked what.
- **Read-only by default.** It reads through a database role that can't change anything. It can make exactly two writes: adding a note to a record, and *proposing* a price change. A proposal is queued for a manager to approve in the ERP and is never applied directly.
- **The same numbers staff see.** Balances, aging, customer stats and pricing rates come from tools that use the ERP's own formulas, so the assistant can't make up its own version of "what's overdue."
- **Every answer links back.** Each record the assistant cites comes with a link to its screen in the ERP, so anyone can check it with one click.

## What changed

- Questions that used to wait for a report, or for me, get answered in a chat in seconds, with links to check them.
- Price changes the assistant suggests land as proposals a manager approves or rejects in the ERP.
- Owners can see who used it and for what.

## The pattern

The same shape works for any small business with its data in one place: give the assistant a narrow, audited door instead of the keys, use the system's own formulas for anything that matters, and send every change through a person.
