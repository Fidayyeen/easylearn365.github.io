# Phase 3 DNS Change Log

## Status

Completed.

DNS records updated, GitHub Pages DNS check successful, HTTPS enforced, and Microsoft 365 email confirmed working.

---

# Date

July 2026

---

# Changes Made In GoDaddy

## Apex Domain A Records

The previous website-related A record for `@` pointing to `WebsiteBuilder Site` was replaced with GitHub Pages A records.

Current expected A records:

- `185.199.108.153`
- `185.199.109.153`
- `185.199.110.153`
- `185.199.111.153`

## WWW CNAME

The `www` CNAME was changed from pointing to `easylearn365.com` / `@` to:

`fidayyeen.github.io`

---

# Records Preserved

Microsoft 365 records were not intentionally changed.

Preserved record types include:

- MX
- SPF TXT
- DMARC TXT
- DKIM CNAME records
- Autodiscover CNAME
- Enterprise registration CNAME
- Enterprise enrollment CNAME
- SIP / Lync CNAME records
- SIP SRV records
- NS records

---

# DNS Verification

PowerShell DNS checks confirmed:

## Apex A Records

`Resolve-DnsName easylearn365.com -Type A`

Returned:

- `185.199.108.153`
- `185.199.109.153`
- `185.199.110.153`
- `185.199.111.153`

## WWW CNAME

`Resolve-DnsName www.easylearn365.com -Type CNAME`

Returned:

`fidayyeen.github.io`

## Microsoft 365 MX

`Resolve-DnsName easylearn365.com -Type MX`

Returned:

`easylearn365-com.mail.protection.outlook.com`

---

# Notes

DNS is resolving correctly for GitHub Pages and Microsoft 365 mail routing still appears intact.

HTTP/HTTPS website checks from the local Codex environment were blocked by sandbox network permissions, so browser verification should be performed manually by the user.

The user confirmed:

- GitHub Pages DNS check is successful.
- Enforce HTTPS has been enabled.
- `https://easylearn365.com` is accessible.
- `https://www.easylearn365.com` is accessible.
- `sakib@easylearn365.com` can send and receive email.

---

# Next Step

Move to Phase 4 – Blog Platform.
