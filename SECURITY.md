# Security Policy

## Supported Versions

| Version | Supported          |
|---------|--------------------|
| 1.0.x   | :white_check_mark: |
| < 1.0   | :x:                |

## Reporting a Vulnerability

If you discover a security vulnerability in Claw Compactor, please report it responsibly.

### How to Report

1. **Do NOT open a public issue** for security vulnerabilities
2. Send a detailed report to the [OpenClaw Discord](https://discord.com/invite/clawd) via DM to a maintainer
3. Or open a [private security advisory](https://github.com/aeromomo/claw-compactor/security/advisories/new)

### What to Include

- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

### Response Timeline

- **Acknowledgment:** Within 48 hours
- **Assessment:** Within 1 week
- **Fix release:** Within 2 weeks for critical issues

### Scope

Claw Compactor processes local workspace files. Security concerns may include:

- Path traversal in file operations
- Code injection through codebook entries
- Unintended data exposure through compression artifacts
- Engram API key handling

### Safe Harbor

We consider security research conducted in good faith to be authorized. We will not pursue legal action against researchers who follow responsible disclosure.
