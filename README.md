# Claude Code Global Setup

Personal global configuration for Claude Code. Contains custom rules and instructions that apply across all projects.

## What's included

**`CLAUDE.md`** — Global instructions loaded into every Claude Code session. Covers general preferences, coding standards, and GitHub conventions.

**`rules/`** — Path scoped rules that auto load based on file type:

| File | Scope | Purpose |
|------|-------|---------|
| `conventions.md` | All files | DRY, SRP, and service class conventions |
| `laravel.md` | `**/*.php` | Laravel pre implementation checklist |
| `vue.md` | `**/*.vue` | Vue pre implementation checklist |
| `frontend-styling.md` | `**/*.vue`, `**/*.css`, `**/*.scss` | Branding consistency and design tokens |

## Installation

Clone this repo and symlink (or copy) the files into your `~/.claude/` directory:

```bash
git clone git@github.com:TheAaronLawrence/claude-global-setup.git ~/claude-global-setup

# Symlink CLAUDE.md
ln -sf ~/claude-global-setup/CLAUDE.md ~/.claude/CLAUDE.md

# Symlink rules directory
ln -sf ~/claude-global-setup/rules ~/.claude/rules
```

Or copy them directly:

```bash
cp ~/claude-global-setup/CLAUDE.md ~/.claude/CLAUDE.md
cp -r ~/claude-global-setup/rules ~/.claude/rules
```

## How rules work

Rules in `~/.claude/rules/` are loaded automatically by Claude Code. Rules with `paths` frontmatter only load when Claude touches matching files. Rules without `paths` load on every session.

This means the Laravel checklist only consumes context when you're working on PHP files, and the Vue checklist only loads when working on Vue files.

## Customizing

Edit the files directly and push. If you used symlinks, changes take effect immediately in your next Claude Code session.
