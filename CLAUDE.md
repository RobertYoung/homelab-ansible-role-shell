# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Ansible role (`shell`) for configuring shell environments on Ubuntu/Debian systems. It sets up zsh with oh-my-zsh, a custom theme, and vim configuration.

## Development Commands

### Linting
```bash
yamllint .                    # Lint all YAML files
ansible-lint                  # Lint Ansible code (currently disabled in CI)
pre-commit run --all-files    # Run all pre-commit hooks
```

### Testing with Molecule
```bash
molecule test          # Run full test suite
molecule converge      # Apply role to test container
molecule verify        # Run verification only
molecule login         # Access container for debugging
molecule destroy       # Clean up test containers
```

### Tool Management
Uses `mise` for tool versions (Ansible 13, pipx 1.8). Run `mise install` to set up.

Install Python dependencies:
```bash
pip install -r requirements.txt
```

## Role Structure

- `tasks/main.yml` - Entry point, includes OS-specific vars and imports task files
- `tasks/zsh.yml` - Installs zsh, oh-my-zsh, figlet, hyfetch/neofetch; configures shell
- `tasks/vim.yml` - Installs vim with custom configuration
- `defaults/main.yml` - Default variables
- `vars/` - OS-specific variables (Debian-12.yml, Debian.yml)
- `templates/.zshrc.j2` - Zsh configuration template
- `files/` - Static files (vimrc, zsh theme, neofetch config)
- `molecule/` - Molecule test configuration

## Tags

Use tags to run specific parts: `--tags "zsh"` or `--tags "vim"`

## Required Variables

When `shell_show_pretty_info: true` (default), the `shell_hostname` variable must be provided.

## Commit Convention

This project uses [Conventional Commits](https://www.conventionalcommits.org/) with semantic-release.

Prefixes:
- `feat:` - New feature (minor version bump)
- `fix:` - Bug fix (patch version bump)
- `docs:` - Documentation changes
- `refactor:` - Code refactoring
- `perf:` - Performance improvements
- `test:` - Adding or updating tests
- `ci:` - CI/CD changes
- `chore:` - Maintenance tasks

## YAML Style

Line length max 120, truthy values must be "true"/"false"/"yes"/"no", 1 space minimum after comments.
