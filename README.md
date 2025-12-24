# homelab-ansible-role-shell

Ansible role for configuring shell environments. Sets up zsh with oh-my-zsh, a custom theme, and vim configuration.

## Requirements

- Ansible >= 2.15
- Target: Ubuntu (focal, jammy, noble) or Debian (bullseye, bookworm)

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `shell_user` | `noxious` | Target user for shell configuration |
| `shell_home_directory` | `/home/{{ shell_user }}` | User's home directory |
| `shell_show_pretty_info` | `true` | Display hostname (figlet) and system info (hyfetch) on shell startup |
| `shell_hostname` | **required** | Hostname to display on shell startup (required if `shell_show_pretty_info` is true) |
| `shell_ohmyzsh_directory` | `{{ shell_home_directory }}/.oh-my-zsh` | Oh-My-Zsh installation directory |

## Tags

Run specific parts of the role using tags:

- `zsh` - Zsh and oh-my-zsh configuration
- `vim` - Vim configuration

## Usage

### Install via requirements.yml

```yaml
- src: git@github.com:RobertYoung/homelab-ansible-role-shell.git
  scm: git
  version: main
  name: shell
```

```bash
ansible-galaxy install -r requirements.yml
```

### Example Playbook

```yaml
- hosts: servers
  roles:
    - role: shell
      vars:
        shell_user: myuser
        shell_hostname: my-server
        shell_show_pretty_info: true
```

### Run specific tasks

```bash
ansible-playbook site.yml --tags "zsh"
ansible-playbook site.yml --tags "vim"
```

## What Gets Installed

### Zsh
- zsh shell with oh-my-zsh framework
- Custom codespaces theme with git status integration
- figlet and hyfetch for system info display

### Vim
- vim editor with dark theme (desert colorscheme)
- Syntax highlighting enabled

## License

MIT
