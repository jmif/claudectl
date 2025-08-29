# Claudectl

**Easily switch between multiple [Anthropic](https://www.anthropic.com/) Claude accounts with [Claude Code CLI](https://www.anthropic.com/claude-code).**

Claudectl is a free, open‑source command‑line tool for macOS and Linux that simplifies working with multiple Anthropic Claude accounts by providing an easy interactive menu and clean environment handling via separate profile directories.



##  Why Claudectl?

- **Quickly switch accounts** — launch Claude Code CLI (`claude`) with your chosen account in one command (`claudectl`).
- **Run simultaneous sessions** — have multiple terminals open, each with a different Claude account.
- **No environment pollution** — uses isolated `CLAUDE_CONFIG_DIR` profiles in `~/.claudectl/` per account.
- **Fully customizable** — add/edit account names in a `settings.json` menu-driven workflow.
- **Zero conflicts** — works alongside regular `claude` usage if you prefer.

Perfect for developers, teams, consultants, and anyone juggling personal and project Claude accounts.



##  One‑Line Install

For macOS & Linux:
```bash
sudo /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/anthropics/claudectl/main/install.sh)"
```

Then just run:
```bash
claudectl
```



##  Quick Start

1. Install using the command above.
2. Run `claudectl` — choose or edit your account profiles via the menu.
3. Claudectl launches Claude Code CLI under the selected profile.
4. Claude Code stores session data and login in the account’s profile directory (`~/.claudectl/YourAccountName/`).



##  Configuration

To add or edit account profile names:

1. Run:
   ```bash
   claudectl
   ```
2. Select **Edit settings.json**
3. Update the `"accounts"` array, e.g.:
   ```json
   {
     "accounts": ["Work", "Client-Acme", "Personal", "Side-Projects"]
   }
   ```
4. Save — Claudectl will create profile folders automatically upon next use.



##  How It Works

- **Default (Personal)**: uses standard `claude` behavior with no special config.
- **Custom Account**: sets `CLAUDE_CONFIG_DIR=~/.claudectl/AccountName/` per session.
- Every terminal gets its own isolated Claude profile environment.



##  Requirements

- **Required**: [Claude Code CLI](https://github.com/anthropics/claude-code)
- **Optional**: VS Code or your editor of choice (handy for editing settings).



##  Additional Features

- **CLI parameter pass-through** — arguments you pass to `claudectl` are forwarded to the `claude` command.
- **Safe to uninstall**:  
  Remove `/usr/local/bin/claudectl` and delete `~/.claudectl/`. Your Claude accounts remain unaffected.



##  Contributing

PRs, issues, feedback — all welcome. Claudectl aims to keep multi‑account Claude Code workflows clean, fast, and reliable.



##  License

MIT License — free to use and modify.



**Made for Claude Code CLI users who manage multiple Anthropic Claude accounts across projects, clients, and personal use.**
