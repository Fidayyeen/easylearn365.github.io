# Phase 3 Domain Implementation Checklist

## Status

Implemented for website domain integration.

Final Microsoft 365 email confirmation is pending.

---

# Goal

Connect `easylearn365.com` and `www.easylearn365.com` to the GitHub Pages website while preserving Microsoft 365 email and business services.

---

# Primary Domain Decision

Primary custom domain:

`easylearn365.com`

Also configure:

`www.easylearn365.com`

Expected behavior:

- `easylearn365.com` should load the GitHub Pages website.
- `www.easylearn365.com` should also work and redirect correctly.

---

# Before Starting

Confirm these are true:

- GitHub Pages site works at `https://fidayyeen.github.io/easylearn365.github.io/`
- Minimal website pages are published and navigation works.
- GoDaddy DNS access is available.
- GitHub repository settings access is available.
- Microsoft 365 email is working before DNS changes.

---

# Records Not To Change

Do not edit or delete these Microsoft 365 records:

- MX record for Outlook mail protection
- SPF TXT record
- DMARC TXT record
- DKIM CNAME records
- `autodiscover` CNAME
- `enterpriseregistration` CNAME
- `enterpriseenrollment` CNAME
- `lyncdiscover` CNAME
- `sip` CNAME
- SIP SRV records
- NS records
- `_domainconnect` CNAME

---

# Step 1 - GitHub Pages Custom Domain

1. Open GitHub.
2. Go to repository:

   `Fidayyeen/easylearn365.github.io`

3. Open:

   `Settings` -> `Pages`

4. Confirm the site is publishing from:

   `main`

5. In `Custom domain`, enter:

   `easylearn365.com`

6. Click `Save`.
7. Wait for GitHub to accept the domain.
8. GitHub may create a `CNAME` file in the repository root.
9. Do not enable HTTPS yet if GitHub says the certificate is not ready.

---

# Step 2 - GoDaddy Apex Domain Records

In GoDaddy DNS, find the existing website-related A record:

- Type: `A`
- Name / Host: `@`
- Value: `WebsiteBuilder Site`

Replace that website builder record with these GitHub Pages A records:

| Type | Name | Value | TTL |
|---|---|---|---|
| A | @ | 185.199.108.153 | 3600 |
| A | @ | 185.199.109.153 | 3600 |
| A | @ | 185.199.110.153 | 3600 |
| A | @ | 185.199.111.153 | 3600 |

Important:

- Only replace the website-related A record.
- Do not change MX, TXT, CNAME, SRV, or NS records related to Microsoft 365.

---

# Step 3 - GoDaddy WWW Record

Find the current `www` CNAME record:

- Type: `CNAME`
- Name / Host: `www`
- Current value: `@`

Change it to:

| Type | Name | Value | TTL |
|---|---|---|---|
| CNAME | www | fidayyeen.github.io | 3600 |

Important:

- The value should be `fidayyeen.github.io`.
- Do not include the repository name in the CNAME target.
- Do not point `www` to `easylearn365.com` or `@`.

---

# Step 4 - Wait For DNS Propagation

DNS changes may take time.

Wait at least 15-30 minutes before testing.

Full propagation can take up to 24 hours.

---

# Step 5 - Verify DNS From PowerShell

Run:

```powershell
Resolve-DnsName easylearn365.com -Type A
```

Expected A records:

```text
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

Run:

```powershell
Resolve-DnsName www.easylearn365.com -Type CNAME
```

Expected CNAME:

```text
fidayyeen.github.io
```

Run:

```powershell
Resolve-DnsName easylearn365.com -Type MX
```

Expected MX record should still point to:

```text
easylearn365-com.mail.protection.outlook.com
```

---

# Step 6 - Enable HTTPS In GitHub Pages

After DNS resolves correctly:

1. Go back to:

   `GitHub` -> `Repository` -> `Settings` -> `Pages`

2. Wait for GitHub to finish checking DNS and issuing the certificate.
3. Enable:

   `Enforce HTTPS`

If HTTPS is not available immediately, wait and check again later.

---

# Step 7 - Website Testing

Test these URLs:

- `http://easylearn365.com`
- `https://easylearn365.com`
- `http://www.easylearn365.com`
- `https://www.easylearn365.com`

Confirm:

- Website loads.
- Navigation works.
- About image loads.
- HTTPS works.
- One domain redirects cleanly to the other if GitHub applies redirect behavior.

---

# Step 8 - Microsoft 365 Testing

After DNS changes, test Microsoft 365:

- Send email from `sakib@easylearn365.com`
- Receive email at `sakib@easylearn365.com`
- Confirm Outlook autodiscover works if possible.
- Confirm no Microsoft 365 DNS warning appears in the admin center.

---

# Rollback Plan

If the website fails:

- Recheck GitHub Pages custom domain setting.
- Recheck A records for `@`.
- Recheck CNAME for `www`.
- Wait for DNS propagation.

If Microsoft 365 email fails:

- Do not change website records first.
- Verify MX, SPF, DKIM, DMARC, autodiscover, and related Microsoft 365 records still match the previous DNS review.
- Restore any accidentally changed Microsoft 365 records from `PHASE_3_DNS_RECORD_REVIEW.md`.

---

# Completion Criteria

Phase 3 domain integration can be marked complete when:

- `https://easylearn365.com` loads the website.
- `https://www.easylearn365.com` works or redirects correctly.
- HTTPS is enforced.
- Microsoft 365 email still sends and receives successfully.
- Final DNS records are documented.

---

# Next Step

Test Microsoft 365 email send and receive using `sakib@easylearn365.com`.

After email is confirmed working, mark Phase 3 complete.
