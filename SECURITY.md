# Security Policy

## Reporting a vulnerability
Please do not report security problems in a public issue.
Use the "Report a vulnerability" button on this repository's
Security tab, or contact <your-username> on GitHub.

I will reply within 3 days.

## Handling secrets in this project
- Secrets live only in a local .env file, which Git ignores.
- .env.example lists the variables needed, with placeholder values.
- Every pull request is scanned for secrets by gitleaks.
