# Phase 3 Domain Integration Plan

## Status

Completed.

Website domain integration is complete and Microsoft 365 email send/receive has been confirmed working.

---

# Goal

Connect `easylearn365.com` to the GitHub Pages website while preserving Microsoft 365 email and business services.

---

# Current Known Setup

Domain provider:
GoDaddy

Business productivity platform:
Microsoft 365

Website hosting:
GitHub Pages

Repository:
`easylearn365.github.io`

Current GitHub Pages URL:
`https://fidayyeen.github.io/easylearn365.github.io/`

Future custom domain:
`easylearn365.com`

---

# Planning Priorities

1. Preserve Microsoft 365 email functionality.
2. Review existing DNS records before making changes.
3. Understand GitHub Pages custom domain requirements.
4. Decide whether to use apex domain, `www`, or both.
5. Plan the DNS change sequence.
6. Enable HTTPS after GitHub Pages recognizes the domain.
7. Document every change.

---

# Information To Collect Before Implementation

- Current GoDaddy DNS records
- Microsoft 365 DNS records currently in use
- GitHub Pages custom domain instructions for this repository
- Whether the site should use `easylearn365.com`, `www.easylearn365.com`, or both
- Current GitHub Pages publishing source
- Whether the repository supports a `CNAME` file

---

# Important Risks

- Incorrect DNS changes could break Microsoft 365 email.
- Changing MX, TXT, SPF, DKIM, DMARC, or Microsoft verification records without review could affect mail flow or security.
- DNS propagation may take time.
- HTTPS may not be immediately available after domain setup.

---

# Recommended Safe Approach

1. Export or screenshot current DNS records.
2. Identify Microsoft 365-related records and mark them as do-not-change.
3. Review GitHub Pages domain requirements.
4. Decide domain format.
5. Add only the required GitHub Pages website records.
6. Configure the custom domain in GitHub Pages.
7. Wait for DNS propagation.
8. Enable HTTPS.
9. Test website access.
10. Test Microsoft 365 email.
11. Document final records and lessons learned.

---

# What Not To Do Yet

- Do not edit DNS records yet.
- Do not remove Microsoft 365 DNS records.
- Do not change MX records.
- Do not change SPF, DKIM, or DMARC records.
- Do not rush HTTPS setup before GitHub Pages detects the domain.

---

# Next Step

Move to Phase 4 – Blog Platform.

Phase 3 Step 1, DNS record review, is complete.

GoDaddy DNS records have been updated and initial DNS verification is complete.

GitHub Pages custom domain verification is successful.

HTTPS has been enforced.

Both website URLs are accessible:

- `https://easylearn365.com`
- `https://www.easylearn365.com`

Microsoft 365 email send and receive has been confirmed working for:

- `sakib@easylearn365.com`
