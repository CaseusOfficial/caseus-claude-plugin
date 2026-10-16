---
name: invoice-attest
description: Reviews supplier invoices waiting for approval in Caseus. Use when the user asks about attestkön, leverantörsfakturor, "vad ska jag attestera", outstanding supplier invoices, or wants a specific supplier invoice checked.
---

# Supplier invoice attest review

1. Follow caseus-basics: orient with `system_get_context` if not already done.
2. Pull the queue with `info_get_attest_queue`. For outstanding but already approved invoices, use `info_list_outstanding_supplier_invoices`.
3. For each invoice, check with `info_get_supplier_invoice` and, when needed, `info_read_invoice_file`:
   - Amount against the supplier's recent history (`info_get_supplier_cost_detail`). Flag jumps over about 20 percent.
   - Duplicates: same supplier, same amount or invoice number in the last 90 days.
   - Right company and property (kostnadsställe).
   - Due date: flag anything due within 5 days or already overdue.
   - Recurring costs: compare with `info_list_recurring_costs` when the supplier is on a contract.
4. Sort into three groups: looks fine, needs a question, do not approve yet. One line each with the reason.

Never approve or reject invoices yourself. The user attests in Caseus. Output: the three groups as a table with links.
