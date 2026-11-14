# Security Policy

## Protecting secrets and private data

Do not submit API keys, OAuth tokens, passwords, private keys, customer conversations, personal information, or confidential brand material in issues, pull requests, commits, examples, or logs. Use local ignored files or a dedicated secret manager.

## Reporting a vulnerability

Please do not disclose exploitable vulnerabilities in a public issue. Use GitHub's **Report a vulnerability** feature in the repository Security tab when it is enabled. If private vulnerability reporting is unavailable, contact the repository owner through their GitHub profile and request a private reporting channel.

## If a secret is exposed

Revoke or rotate it immediately at the issuing provider. Removing it from the latest commit is not sufficient because Git history and forks may retain copies.
