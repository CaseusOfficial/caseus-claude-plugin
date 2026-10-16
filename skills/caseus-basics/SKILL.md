---
name: caseus-basics
description: Ground rules for any work in Caseus property management data. Use whenever a request touches Caseus records - hyresgäster, uthyrningar, avier, leverantörsfakturor, fastigheter, uppgifter, felanmälningar, e-post or rapporter - or when the user asks "hur gör jag ... i Caseus".
---

# Working in Caseus

## Orient first
- Call `system_get_context` once per conversation. It returns the instance host, the companies (bolag), enabled modules, the record map and the user's scopes.
- If the user has several Caseus connections, pick the one whose host matches what they mention (for example a host in a pasted task link). Ask if unclear.

## Find data
- Prefer the purpose-built `info_*` tools (for example `info_find_renter`, `info_find_property`, `info_get_renter_balance`). They return the right joins and labels.
- Use `data_describe` then `data_sql_query` only when no `info_*` tool fits. Read-only queries only. Filter by company when the user names one.
- For "how do I ... in Caseus" questions, call `manual_search` with Swedish words, then `manual_read`, and answer from the page. Never describe menus or buttons from memory.

## Present results
- Turn every record id into a link with `system_get_record_url` or the record map URL template. Never show a bare id.
- Amounts in SEK, Swedish formatting (1 234 kr). Dates as YYYY-MM-DD.
- Lead with the answer and a short table. State what was not checked.

## Changing data
- Never claim a change was made unless a tool confirmed it.
- For changes, use `actions_describe` to find the right action, then `actions_propose`. A person approves the proposal in Caseus. Say so.
- Draft emails and messages with the draft tools. Do not send email unless the user explicitly asks for that specific message to be sent.
- Tenant data is personal data. Only show what the task needs.
