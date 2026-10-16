---
name: caseus-setup
description: Connects the Caseus plugin to the user's own Caseus instance. Use when the user installs the plugin, asks how to connect Caseus, gets an authorization or connection error from Caseus tools, or says "koppla Caseus", "anslut till Caseus", "set up Caseus".
---

# Connect Caseus

1. Check whether the Caseus tools respond: call `system_get_context` with `includeRecordTypes: false`.
   - If it returns a deployment, tell the user which instance and how many companies are connected, then stop.
2. If the tool is missing or fails, guide the user:
   - In Caseus, open **Inställningar > Auktoriserade agenter** and copy the connection address. If that page is missing, the user lacks a role that may add agents, or the **Agenter (MCP)** module is off. They should ask their Caseus admin.
   - Where the address goes depends on the app:
     - Claude Code: the plugin setting "Caseus connection address". Run `/plugin configure caseus@caseus` (or the plugin's name as `/plugin` lists it), paste the address, then restart Claude Code.
     - Claude chat, Cowork and the desktop app: these do not use plugin settings. Add a custom connector in Claude's connector settings and paste the address there.
   - Sign in to Caseus when prompted.
3. Call `system_get_context` again to confirm.

Never ask the user for a password or token in chat. Sign-in happens in Caseus' own login page.
