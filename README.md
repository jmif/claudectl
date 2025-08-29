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
sudo /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/jmif/claudectl/main/install.sh)"
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



##  Usage

**Interactive Menu:**
```bash
claudectl                    # Show account selection menu
```

**Direct Profile Launch:**
```bash
claudectl Work               # Launch directly with Work profile
claudectl personal           # Launch with Personal (default) profile
claudectl alternate          # Launch with alternate profile
```

**Pass Arguments to Claude:**
```bash
claudectl Work --help        # Launch Work profile and pass --help to claude
claudectl personal --version # Launch personal profile with --version
```

**Get Help:**
```bash
claudectl --help             # Show usage information
claudectl -h                 # Short help flag
claudectl help               # Alternative help command
```

**Manage CLAUDE.md:**
```bash
claudectl copy-claude-md     # Copy ~/.claude/CLAUDE.md to ~/.claudectl/CLAUDE.md
claudectl edit-claude-md     # Edit the local ~/.claudectl/CLAUDE.md file
```

**Import/Link Global Setup:**
```bash
claudectl import-global Work # Copy global Claude config into Work profile  
claudectl link-global Work   # Create symlinks to global Claude config in Work profile
```

**Notes:**
- Profile names are case-insensitive
- All arguments after the profile name are passed through to `claude`
- Use the interactive menu's "e" option to edit account profiles

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
- **CLAUDE.md Linking**: Each profile directory links to either:
  - `~/.claudectl/CLAUDE.md` (if you've copied it locally with `claudectl copy-claude-md`)
  - `~/.claude/CLAUDE.md` (fallback to global file)

**Managing CLAUDE.md:**
- Use `claudectl copy-claude-md` to create a local copy that all profiles will use
- Use `claudectl edit-claude-md` to edit the local copy
- Local copy takes precedence over the global `~/.claude/CLAUDE.md`
- This allows you to have profile-specific instructions while keeping accounts separate

**Importing/Linking Global Setup:**
- Use `claudectl import-global PROFILE` to copy your entire global Claude configuration into a specific profile
- Use `claudectl link-global PROFILE` to create symlinks to your global Claude configuration in a specific profile
- Import copies all files/directories, link creates symlinks (changes in global affect the profile)
- Both import all settings, session data, and configuration from `~/.claude/`
- Includes confirmation prompt if the profile already has configuration files
- Circular link detection prevents creating invalid configurations



##  Requirements

- **Required**: [Claude Code CLI](https://github.com/anthropics/claude-code)
- **Optional**: VS Code or your editor of choice (handy for editing settings).



##  Additional Features

- **Direct profile launch** — skip the interactive menu by specifying a profile name: `claudectl Work`
- **CLI parameter pass-through** — arguments you pass to `claudectl` are forwarded to the `claude` command.
- **Case-insensitive profiles** — `claudectl work`, `claudectl Work`, and `claudectl WORK` all work the same.
- **Built-in help** — run `claudectl --help` for usage information and available profiles.
- **Local CLAUDE.md management** — copy and edit a local CLAUDE.md that all profiles share.
- **Global setup import/linking** — copy or symlink your existing Claude configuration into any profile.
- **Safe to uninstall**:  
  Remove `/usr/local/bin/claudectl` and delete `~/.claudectl/`. Your Claude accounts remain unaffected.



##  Contributing

PRs, issues, feedback — all welcome. Claudectl aims to keep multi‑account Claude Code workflows clean, fast, and reliable.



##  License

MIT License — free to use and modify.



**Made for Claude Code CLI users who manage multiple Anthropic Claude accounts across projects, clients, and personal use.**
