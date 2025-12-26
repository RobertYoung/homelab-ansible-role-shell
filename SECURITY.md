# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.x     | :white_check_mark: |

## Reporting a Vulnerability

If you discover a security vulnerability in this Ansible role, please report it responsibly.

**Do not open a public GitHub issue for security vulnerabilities.**

Instead, please report security issues by emailing: me@iamrobertyoung.co.uk

Include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Any suggested fixes (optional)

You can expect:
- Acknowledgment within 48 hours
- Regular updates on progress
- Credit in the fix (unless you prefer to remain anonymous)

## Security Considerations

This role configures shell environments. When using this role:

- Review the deployed `.zshrc` and `.vimrc` configurations for your security requirements
- Ensure the `shell_user` variable points to the correct user
- Consider file permissions on configuration files
