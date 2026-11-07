# Agensi listing — imap-readonly

**Name:** IMAP Read-Only Mailbox (Himalaya v2)

**Short description:**
Let your agent read, search and summarize an IMAP mailbox without sending,
deleting, moving or marking anything as read.

**Long description:**
A skill for reading a work or personal IMAP mailbox through the Himalaya v2
CLI. The agent can list folders, search by sender, subject, body, date or
unread status, read messages and list attachments. It summarizes unread
mail, finds threads and drafts replies in chat, without ever sending them.

- Written for Himalaya v2. The bundled himalaya skill uses v1 commands
  that no longer exist.
- Read-only rules: no send, move, delete, flag or attachment download.
- Reading leaves messages unread in your own mail client.
- Treats email content as data and flags prompt-injection attempts.
- Includes a setup guide and an example config with the password kept
  outside it and no SMTP configured.

Note: the read-only behaviour comes from the skill's instructions. For a
hard technical limit, see the setup guide (read-only account rights, or
Himalaya's MCP server when it is released).

**Works with:** Hermes Agent, and any agent that supports SKILL.md and a
shell (Claude Code, Codex CLI, ...).

**Category:** Productivity / Workflow Automation
**Price:** Free
**Source:** https://github.com/roberttomecki/hermes_skill
