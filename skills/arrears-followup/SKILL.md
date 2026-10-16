---
name: arrears-followup
description: Reviews tenant arrears in Caseus and proposes next steps. Use when the user asks about hyresskulder, obetalda avier, restskulder, kravhantering, inkasso, "vem är skyldig", "who hasn't paid", or a specific tenant's balance.
---

# Arrears follow-up

1. Follow caseus-basics: orient with `system_get_context` if not already done.
2. Get the picture:
   - Portfolio or company: `info_get_arrears_summary`, then `info_list_unpaid_invoices` for detail.
   - One tenant: `info_find_renter`, then `info_get_renter_balance`.
   - Check `info_list_unallocated_payments` before calling anyone late. A payment may be in but not matched.
3. Group by age: 1-30 days, 31-60, 61-90, over 90. Show count and total per group and per company.
4. For each tenant above 30 days, give one line: tenant (linked), unit, amount, oldest due date, last payment date, suggested next step.
   - Suggested steps, in order: reminder (påminnelse), call or personal contact, payment plan, inkasso. Base the step on age and history, and say it is a suggestion.
5. Flag anything odd: credits not applied, duplicate avier, payments on terminated contracts.
6. If the user wants reminders drafted, use the draft tools. Do not send.

Output: one summary table, then the action list. Keep it short.
