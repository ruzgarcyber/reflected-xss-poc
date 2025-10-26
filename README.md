## Reflected XSS PoC

## Description
- Minimal, educational Proof‑of‑Concept for Reflected XSS (Cross‑Site Scripting).
- Only run this in authorized lab / VM / test environments.

## Requirements
- Python 3.8+
- requests library
- pip install requests

## Usage
- python exploit.py --target http://10.10.10.10:8000 --endpoint /search --param q --debug --delay 1

## Common options

- --target : base URL (with scheme)

- --endpoint: vulnerable endpoint path (e.g. /search)

- --param : GET parameter name that reflects input (default: q)

- --payloads : provide custom payloads (space separated)

- --delay : seconds to wait between requests (human-like default: 1)

- --debug : verbose request/response info

## Key features (matching the PoC)
- Human-like behavior: random User-Agent rotation + adjustable delay between requests.
- Readable terminal output: [INFO], [SUCCESS], [ERROR] messages for quick understanding.
- Robust detection: checks direct reflection, HTML‑escaped, URL‑encoded and regex matches.
- Logging: all attempts are appended to results.jsonl (time-stamped JSON lines).
- Payload flexibility: default probes included and you can pass custom payloads.

## Default payloads (escaped for safe display)

- &lt;svg/onload=alert(1)&gt;

- "&gt;&lt;svg/onload=alert(1)&gt;

- &lt;img src=x onerror=alert(1)&gt;

- "&gt;&lt;script&gt;console.log(1)&lt;/script&gt;

**You can pass additional/custom payloads with --payloads.**

Example output (successful run)
[INFO] Target: http://10.10.10.10:8000/search  |  Parameter: q
[SUCCESS] Payload reflected: '<svg/onload=alert(1)>'
          HTTP 200 | URL: http://10.10.10.10:8000/search?q=%3Csvg%2Fonload%3Dalert%281%29%3E
          Snippet: ...Search results for &lt;svg/onload=alert(1)&gt;...
==================================================
[SUMMARY] 1 payload(s) reflected
==================================================

## Safety & notes

- **Only run this PoC in environments you own or have explicit permission to test.**
- **This repository is for education and lab practice only. Do not use for malicious activity.**
- **Inspect results.jsonl before committing or sharing logs (may contain sensitive test output).**
