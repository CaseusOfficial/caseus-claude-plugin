---
name: fault-reports
description: Triages fault reports (felanmälningar) in Caseus. Use when the user asks about felanmälningar, open faults, "vad är trasigt", what is overdue for the caretaker, or the status of a specific fault report.
---

# Fault report triage

1. Follow caseus-basics: orient with `system_get_context` if not already done.
2. List open cases with `info_list_fault_reports`. Open details with `info_get_fault_report` only for cases that need judgment.
3. Classify each open case:
   - Urgent: water leak, no heat, no hot water, electrical risk, lock or entry problem, anything about safety.
   - Normal: functional fault with a workaround.
   - Low: cosmetic.
4. Flag cases open longer than 14 days, cases with no assigned person, and repeated faults in the same unit or building (`info_get_history_events` helps).
5. Output a short table: case (linked), property and unit, category, age in days, assigned to, suggested next step.

To create tasks or update a case, use `actions_propose` and tell the user it waits for approval in Caseus.
