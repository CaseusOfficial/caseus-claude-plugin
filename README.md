# Caseus for Claude

Caseus is a Swedish property management system. This plugin lets Claude work directly in your own Caseus instance: look up tenants, rentals and arrears, review supplier invoices waiting for attest, triage fault reports, read tasks and mail, and pull property and financial overviews. Claude links every record it mentions back to the right page in Caseus.

## What you need

- A Caseus account with the **Agenter (MCP)** module turned on.
- Your connection address from Caseus: **Inställningar > Auktoriserade agenter**. It is your own Caseus host followed by `/api/mcp`.
- You sign in to Caseus the first time Claude connects. Claude only sees what your own Caseus user can see.

## Install

**Claude Code.** Add this repository as a marketplace and install the plugin:

```
claude plugin marketplace add CaseusOfficial/caseus-claude-plugin
claude plugin install caseus@caseus --config caseus_mcp_url=https://yourcompany.caseus.se/api/mcp
```

Or run `/plugin install caseus@caseus` inside a session, which asks for the "Caseus connection address" itself. To change the address later, run `/plugin configure caseus@caseus`.

**Claude chat, Cowork and the desktop app.** Install the plugin from the Claude directory, or upload a zip of this repository under Customize > Plugins. Those apps do not ask for plugin settings, so the plugin's own connection is skipped there. Add the Caseus connection once as a [custom connector](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp) with the address from Caseus. The skills then use it.

## Skills

| Skill | Use it for |
| --- | --- |
| caseus-setup | Connecting the plugin to your Caseus instance |
| caseus-basics | How Claude works with Caseus: deployment context, record links, the manual, proposing changes |
| arrears-followup | Hyresskulder and obetalda avier: who owes what, how old, what to do next |
| invoice-attest | Leverantörsfakturor in the attest queue: what to approve, what to question |
| fault-reports | Felanmälningar: open cases, priority, what is overdue |
| property-report | Overview of a property or company: rentals, vacancies, costs, finances |

## What the plugin runs, sends and fetches

- It contains no code. It adds one remote MCP server, the address you enter, which points at your own Caseus host.
- All data Claude reads comes from that Caseus instance, over HTTPS, with your Caseus login.
- Claude does not change data in Caseus on its own. Changes go through Caseus' own proposal flow (actions_propose), which a person approves inside Caseus.
- The plugin sends nothing to any other service.

## Support

Questions: wendt@caseus.se or https://caseus.se.
