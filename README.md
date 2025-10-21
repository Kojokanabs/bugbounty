# Practical bug bounty

Authentication & Authorization bug-bounty lab write-up demonstrating MFA abuse, credential-stuffing, IDOR, and API token issues. 

# Executive Summary
 
This report documents authentication and authorization weaknesses discovered in a local bug-bounty lab, including an MFA flow that allows cross-user code reuse, credential-stuffing susceptibility, IDORs through predictable IDs, and API token/JSON handling issues. Findings are reproducible locally with PoCs and include remediation recommendations to harden the application.

# Tools & Versions

Tools used to reproduce and test:
- ffuf — fast web fuzzer — v1.5.0+ (any recent)
- Burp Suite — Community or Professional (for intercept/repeater)
- curl — for API requests
- Python 3.8+ — local scripts (num.py)
- SecLists (wordlists) — for username/password lists

Notes:
- Use Burp for interactive MFA manipulation (Proxy / Repeater).
- Adjust ffuf concurrency `-t` to avoid DoS on test targets.

## Repository contents
- `README.md` — this file.
- `REPORT.md` — full vulnerability write-up and remediation (detailed).
- `pocs/` — PoC files and helper scripts:
  - `num.py` — numeric wordlist generator.
  - `auth3_req.txt` — ffuf request template for clusterbomb mode.
  - `sample_num.txt` — small sample numeric list.
