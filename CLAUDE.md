# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Ansible role (`shell`) for configuring shell environments on Ubuntu/Debian systems. It sets up zsh with oh-my-zsh, a custom theme, and vim configuration.

## Development Commands

### Linting
```bash
yamllint .                    # Lint all YAML files
ansible-lint                  # Lint Ansible code (currently disabled in CI)
```

### Pre-commit Hooks
```bash
pre-commit install            # Install hooks
pre-commit run --all-files    # Run all hooks manually
```

### Tool Management
Uses `mise` for tool versions (Ansible 13, pipx 1.8). Run `mise install` to set up.

## Role Structure

- `tasks/main.yml` - Entry point, imports zsh and vim tasks with tags
- `tasks/zsh.yml` - Installs zsh, oh-my-zsh, figlet, hyfetch; configures shell
- `tasks/vim.yml` - Installs vim with custom configuration
- `defaults/main.yml` - Default variables
- `templates/.zshrc.j2` - Zsh configuration template
- `files/` - Static files (vimrc, zsh theme)

## Tags

Use tags to run specific parts: `--tags "zsh"` or `--tags "vim"`

## Required Variables

When `shell_show_pretty_info: true` (default), the `shell_hostname` variable must be provided.

## YAML Style

Line length max 120, truthy values must be "true"/"false"/"yes"/"no", 1 space minimum after comments.
