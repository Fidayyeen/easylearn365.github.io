# Phase 3 DNS Record Review

## Status

Completed for planning.

No DNS changes have been made.

---

# Source Files Reviewed

- `C:\Users\UpWork\Downloads\easylearn365.com.csv`
- `C:\Users\UpWork\Downloads\easylearn365.com.txt`

---

# Goal

Review current DNS records for `easylearn365.com` before connecting the domain to GitHub Pages.

The main priority is to preserve Microsoft 365 email and business services.

---

# Current DNS Provider

GoDaddy

Name servers:

- `ns47.domaincontrol.com`
- `ns48.domaincontrol.com`

---

# Microsoft 365 Records To Preserve

These records appear to support Microsoft 365 mail, identity, device enrollment, Teams/Skype services, DKIM, SPF, and DMARC.

Do not remove or modify these during GitHub Pages setup unless Microsoft 365 specifically requires it.

## Mail Routing

MX:

- Host: `@`
- Value: `easylearn365-com.mail.protection.outlook.com`
- Priority: `0`

## SPF

TXT:

- Host: `@`
- Value: `v=spf1 include:spf.protection.outlook.com -all`

## DMARC

TXT:

- Host: `_dmarc`
- Value: `v=DMARC1; p=quarantine; adkim=r; aspf=r; rua=mailto:dmarc_rua@onsecureserver.net;`

## Autodiscover

CNAME:

- Host: `autodiscover`
- Value: `autodiscover.outlook.com`

## Device Registration / Enrollment

CNAME:

- Host: `enterpriseregistration`
- Value: `enterpriseregistration.windows.net`

CNAME:

- Host: `enterpriseenrollment`
- Value: `enterpriseenrollment-s.manage.microsoft.com`

## DKIM

CNAME:

- Host: `selector1._domainkey`
- Value: `selector1-easylearn365-com._domainkey.easylearn365.q-v1.dkim.mail.microsoft`

CNAME:

- Host: `selector2._domainkey`
- Value: `selector2-easylearn365-com._domainkey.easylearn365.q-v1.dkim.mail.microsoft`

## Teams / Skype Related Records

CNAME:

- Host: `lyncdiscover`
- Value: `webdir.online.lync.com`

CNAME:

- Host: `sip`
- Value: `sipdir.online.lync.com`

SRV:

- Host: `_sip._tls.@`
- Target: `sipdir.online.lync.com`
- Port: `443`

SRV:

- Host: `_sipfederationtls._tcp.@`
- Target: `sipfed.online.lync.com`
- Port: `5061`

---

# Existing Website-Related Records

These are the records that affect website routing.

## Apex Domain

A:

- Host: `@`
- Value: `WebsiteBuilder Site`

This appears to be the current GoDaddy Website Builder/default website record.

For GitHub Pages, this record will need to be replaced with GitHub Pages records when implementation begins.

## WWW Subdomain

CNAME:

- Host: `www`
- Value: `@`

For GitHub Pages, this should be changed later to point directly to the GitHub Pages default domain, not to `@`.

Expected target:

`fidayyeen.github.io`

---

# GitHub Pages Records Needed Later

Based on GitHub Pages custom domain requirements, an apex domain should point to GitHub Pages using A records.

Future A records for `@`:

- `185.199.108.153`
- `185.199.109.153`
- `185.199.110.153`
- `185.199.111.153`

Optional IPv6 AAAA records:

- `2606:50c0:8000::153`
- `2606:50c0:8001::153`
- `2606:50c0:8002::153`
- `2606:50c0:8003::153`

Future CNAME for `www`:

- Host: `www`
- Value: `fidayyeen.github.io`

---

# Recommended Domain Choice

Recommended primary custom domain:

`easylearn365.com`

Also configure:

`www.easylearn365.com`

Reason:

- Apex domain is clean for branding.
- `www` should also work and redirect properly.
- GitHub recommends configuring the `www` variant alongside the apex domain for HTTPS-secured sites.

---

# Safe Implementation Sequence

Do not perform these changes until the user is ready.

1. Confirm GitHub Pages is publishing correctly from `main`.
2. In GitHub repository settings, set the custom domain to `easylearn365.com`.
3. Let GitHub create or use the repository `CNAME` file.
4. In GoDaddy DNS, replace the current `@` A record pointing to `WebsiteBuilder Site` with the four GitHub Pages A records.
5. In GoDaddy DNS, change `www` CNAME from `@` to `fidayyeen.github.io`.
6. Do not change MX, SPF, DKIM, DMARC, autodiscover, enrollment, SIP, or SRV records.
7. Wait for DNS propagation.
8. Verify DNS resolution.
9. Enable HTTPS in GitHub Pages when available.
10. Test:
    - `https://easylearn365.com`
    - `https://www.easylearn365.com`
    - Microsoft 365 email sending and receiving

---

# Records To Change Later

Only these website records should change:

- `@` A record currently pointing to `WebsiteBuilder Site`
- `www` CNAME currently pointing to `@`

---

# Records Not To Change

- MX record
- SPF TXT record
- DMARC TXT record
- DKIM CNAME records
- Autodiscover CNAME
- Enterprise registration CNAME
- Enterprise enrollment CNAME
- Lync/SIP CNAME records
- SIP SRV records
- NS records
- `_domainconnect` CNAME

---

# Next Step

Prepare the exact implementation checklist for GitHub Pages and GoDaddy DNS.

No DNS changes yet.
