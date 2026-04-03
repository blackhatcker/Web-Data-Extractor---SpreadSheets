Security Policy
Supported Versions
Version	Supported
1.x	Yes
Reporting a Vulnerability
Please do not report security vulnerabilities through public GitHub issues.

If you discover a security vulnerability, please report it by emailing:

security@lyonfiurex.com

Include in your report:

A description of the vulnerability and its potential impact
Steps to reproduce or a proof-of-concept (if applicable)
The version(s) affected
Any suggested fix (optional)
You will receive an acknowledgment within 48 hours and a status update within 7 business days.

Disclosure Policy
We follow a coordinated disclosure process:

You report the vulnerability privately.
We confirm receipt and begin investigating within 48 hours.
We develop and test a fix.
We release a patched version and notify you.
After the patch is released (or after 90 days, whichever comes first), you may disclose publicly.
Security Considerations for Self-Hosting
When running this application on your own infrastructure:

The API server fetches arbitrary URLs provided by end users. Ensure the server is not exposed to internal network resources (SSRF risk). Consider running it in an isolated network environment or adding an allowlist/denylist of URL patterns.
Rate-limit the /api/extract and /api/extract/preview endpoints to prevent abuse.
The application does not store fetched content — all extraction is performed in-memory per request.
