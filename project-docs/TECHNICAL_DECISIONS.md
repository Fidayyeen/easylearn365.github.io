# Technical Decisions

## Purpose

This document records important technical decisions made during the EasyLearn365 project.

The goal is to preserve the reasoning behind decisions so future work does not accidentally undo or duplicate previous efforts.

---

# Hosting

Decision:
GitHub Pages

Reason:

- Free hosting
- Integrates directly with GitHub
- Supports custom domains
- Excellent learning value
- Simple deployment workflow

Status:
Active

---

# Domain

Decision:
easylearn365.com

Provider:
GoDaddy

Status:
Purchased and active

Notes:

- Domain is already owned
- Domain integration with GitHub Pages has not yet been performed
- Custom domain setup will be completed in a later phase

---

# Email Platform

Decision:
Microsoft 365

Status:
Configured separately from website hosting

Purpose:

- Professional email
- Business identity
- Domain-based communication

---

# Version Control

Decision:
Git + GitHub

Reason:

- Industry standard
- Learning objective
- Supports documentation-driven development
- Enables safe experimentation

Status:
Active

---

# Repository

Repository Name:
easylearn365.github.io

Repository Owner:
Fidayyeen

Repository URL:
https://github.com/Fidayyeen/easylearn365.github.io

Status:
Active

---

# Branch Strategy

Primary Branch:
main

Reason:

- GitHub modern standard
- GitHub Pages deployment branch
- Future-proof

Notes:

- Project initially started on master
- Website content was migrated to main
- Future work should be performed on main

---

# Website Type

Decision:
Static Website

Reason:

- Simplicity
- Learning value
- Low maintenance
- No server required

Future Possibilities:

- Jekyll
- Hugo
- Static site generators

Not currently required.

---

# Documentation Strategy

Primary Planning Tool:
Notion

Development Documentation:
project-docs folder

Reason:

- Separate planning from implementation
- Enable AI-assisted development
- Maintain long-term project memory

---

# Development Philosophy

Build → Document → Improve

Priorities:

1. Learning value
2. Simplicity
3. Maintainability
4. Good engineering practices

Avoid unnecessary complexity.