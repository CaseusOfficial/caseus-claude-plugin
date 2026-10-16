---
name: property-report
description: Builds an overview of a property, building or company in Caseus. Use when the user asks for a fastighetsrapport, status for a property or bolag, vakanser, uthyrningsgrad, costs, net operating income, or "hur går det för ...".
---

# Property or company overview

1. Follow caseus-basics: orient with `system_get_context` if not already done.
2. Identify the target with `info_find_property` or the company list from the context. Ask if the name matches several.
3. Collect, in this order, and skip what the user did not ask for:
   - Rentals and vacancies: `info_get_property_overview`, `info_get_rental_overview`, `info_list_units`.
   - Upcoming move-outs: `info_get_agreement_termination` or terminations in the rental overview.
   - Finances: `info_get_financial_overview`, `info_get_cost_overview`, `info_get_recurring_cost_summary`.
   - Arrears: `info_get_arrears_summary` for that company.
   - Open fault reports and upcoming maintenance: `info_list_fault_reports`, `info_list_upcoming_care`.
4. Present: 3-5 headline numbers first (units, occupancy, monthly rent, arrears, open faults), then one table per area, then up to three things that need attention.
5. If the user wants something to keep or share, offer to build it as a document or dashboard.

State the period and data date for every number. Do not estimate figures that a tool did not return.
