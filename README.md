# Novamris for AI assistants

Bring your birth chart into the conversation. Explore your placements, today's astrology and the month or year ahead. Compare dates you're considering, with your own chart in view. Novamris supplies the calculations; the assistant you use helps you explore their meaning. Start with your birth date, or connect your existing Novamris account to read its saved chart.

This package contains only connector descriptors and instructions. The application, calculation backend, credentials and customer data are not included.

## What you can ask

- “What stands out in my birth chart?”
- “Help me understand today's astrology.”
- “What is still ahead for me this year?”
- “Compare these two dates I’m considering.”

A birth date is enough for a broad guest reading. An optional historical birthplace and birth time can improve precision. Unknown or approximate times remain uncertain; Novamris does not invent an exact rising sign or houses. Astrology offers reflection, not guaranteed outcomes.

## Connect

Remote MCP endpoint: **https://app.novamris.com/mcp** (Streamable HTTP).

[Setup, capabilities and troubleshooting](https://novamris.com/ai-assistants).

| Client | Setup |
| --- | --- |
| ChatGPT / Codex | Use the directory listing when published, or add the endpoint in developer mode. Directory approval is separate from installing this package. |
| Claude | Add the endpoint as a custom connector. Claude Code also supports `claude mcp add --transport http novamris https://app.novamris.com/mcp`. |
| Gemini CLI | Install this extension repository, or run `gemini mcp add --transport http novamris https://app.novamris.com/mcp`. |
| Cursor | Install this plugin repository or add the endpoint in MCP settings. |
| Other MCP clients | Add the Streamable HTTP endpoint. Guest tools require no account; saved-account tools use OAuth. |

Installation instructions do not mean a marketplace has approved the listing. If a client asks you to connect an account, use Novamris's normal sign-in and review the requested read access. Never paste a password or API key into the assistant.

## Guest readings and saved-account access

Guest calculations use the birth details you explicitly provide. Novamris does not save a guest profile, chart or interpretation. An encrypted chart context is returned to the conversation for follow-ups and accepted for two hours. Its expiry does **not** delete the assistant provider's conversation history. Keep that context private; never put it in a URL.

Connecting an account is optional. It allows the assistant to read only your own saved chart and the timing features included in your account. It cannot read your private events, chats, email or payment details, change records, or make purchases. Disconnect from [Novamris connections](https://app.novamris.com/connections).

The seven tools are `calculate_chart`, `get_profile`, `get_chart`, `get_daily_focus`, `get_timing_month`, `get_timing_year`, and `compare_dates`. They reuse Novamris's calculation engine, timezones and coverage rules. Tool calls do not use Luna message credits; the host assistant provides the conversation.

## Support and privacy

[Novamris](https://novamris.com) · [Support](https://novamris.com/contact) · [Privacy](https://novamris.com/privacy) · [Terms](https://novamris.com/terms)

Published by Rookvell LLC. Connector-source licensing does not grant rights to the Novamris name, logo or other brand assets; see the package's license and notices.

## Package formats

This public repository contains client descriptors only; the Novamris backend and
credentials are not included. ChatGPT/Codex, Claude, Gemini CLI, Cursor and the MCP
Registry descriptors all reference the same hosted Novamris service. They do not
create separate services or transfer account access between clients.

The root `plugin.json`, `mcp.json` and `skills/` use the portable Agent Plugins
layout. The public repository's `mcp.json` contains only portable transport fields.
The separately generated OpenAI submission ZIP adds OpenAI's mixed-auth connection
metadata; OAuth discovery and server-side authorization remain authoritative in
every client. Claude uses `.claude-plugin/plugin.json` and `.mcp.json`; Gemini CLI
uses root `gemini-extension.json`. `server.json` is remote-only MCP Registry
metadata, not a registry submission or proof of a marketplace listing.
