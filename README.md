# LEDERG PANZER

**Free defensive security toolkit for Windows 10/11 x64.**

LEDERG PANZER helps administrators and learners review a single domain or IP address that they own or are explicitly authorized to test.

> **Authorization required.** Only assess systems you own or have explicit permission to test. Mass scanning, disruption, exploitation, credential attacks and third-party access are out of scope.

## v0.1.0
- DNS inventory: A, AAAA, MX, NS, TXT, CAA, SPF and DMARC.
- Web configuration review: HTTPS availability, security headers, CORS, Server disclosure and cookie flags.
- TLS certificate validation, issuer and expiry.
- Bounded TCP connect check of 38 common ports on one resolved IP.
- Local SQLite scan history; HTML and JSON reports.
- Russian UI and built-in field guide.
- No account, paid API or Python installation required for the Windows EXE.

## Download
The Windows executable is published in [GitHub Releases](https://github.com/lederg001/lederg-panzer/releases). Download `LEDERG-PANZER.exe`. The build is produced on a Windows runner.

## Run from source
```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```

Tests: `python -m unittest discover -s tests -v`

## Scope guardrails
- One domain or one IP per assessment; URLs, paths, CIDRs, wildcards and target lists are rejected.
- Operator authorization acknowledgement and a second target confirmation are required.
- TCP checks use a fixed 38-port list with bounded concurrency and timeout.
- Web review makes one bounded request to `/`; cross-host redirects are blocked.
- No crawling, fuzzing, exploit payloads, password guessing, stealth, persistence or data extraction.
- Open ports and missing headers are observations, not proof of exploitable vulnerabilities. Validate manually.
- Findings and history remain on the local computer. The app writes an authorization confirmation log.

## Roadmap
1. Signed rule-pack updates and provenance.
2. Import results from Nmap and OWASP ZAP passive/baseline scans.
3. Asset inventory, project workspaces and scan comparisons.
4. SBOM/dependency review.
5. Plugin API with explicit capability and scope enforcement.

## Project
- Repository: https://github.com/lederg001/lederg-panzer
- Maintainer: [@LEDERG_ru](https://t.me/LEDERG_ru)

## License
MIT. See LICENSE.
