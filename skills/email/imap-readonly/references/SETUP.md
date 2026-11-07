# Setup

This skill only reads mail through Himalaya. You configure the account once,
and the agent never sees your password.

## 1. Install Himalaya v2

Linux / macOS / WSL, as a regular user:

```bash
curl -sSL https://raw.githubusercontent.com/pimalaya/himalaya/master/install.sh | PREFIX=~/.local sh
himalaya --version   # should print 2.x
```

On Windows, download the binary from
https://github.com/pimalaya/himalaya/releases and put it on your `PATH`.

## 2. Configure the account

Copy `config.example.toml` to `~/.config/himalaya/config.toml` (or point the
`HIMALAYA_CONFIG` environment variable at it) and fill in your server and
address. You get the IMAP server name from your mail provider.

Do not configure SMTP. Without an SMTP section the account cannot send mail
at all.

## 3. Store the password outside the config

```bash
printf '%s' 'your-mailbox-password' > ~/.config/himalaya/.password
chmod 600 ~/.config/himalaya/.password
```

Or use a password manager instead: `password.command = "pass show mail/work"`.

## 4. Test it

```bash
himalaya account check
himalaya envelope list
```

## 5. Install the skill in Hermes

Linux / WSL:

```bash
mkdir -p ~/.hermes/skills/email
cp -r imap-readonly ~/.hermes/skills/email/
```

Native Windows Hermes (Git Bash):

```bash
mkdir -p "$LOCALAPPDATA/hermes/skills/email"
cp -r imap-readonly "$LOCALAPPDATA/hermes/skills/email/"
```

## How "read-only" works, honestly

The read-only behaviour comes from the skill's instructions. The agent is
told which commands it may run and that it must never pass `--seen`. Nothing
technical stops an agent with shell access from running `himalaya message
delete`. Leaving SMTP out of the config does block sending at the technical
level, but deleting, moving and flagging go through IMAP and stay possible.

If you want a hard limit, use a mailbox account with read-only rights (some
servers allow this through shared-folder ACLs), or use Himalaya's MCP server
once it ships in a release. `himalaya mcp` is in Himalaya's master branch at
the time of writing (not in 2.2.1). It exposes only reading tools unless
started with `--allow-write` or `--allow-send`:

```yaml
# ~/.hermes/config.yaml
mcp_servers:
  mail:
    command: "himalaya"
    args: ["mcp"]
```
