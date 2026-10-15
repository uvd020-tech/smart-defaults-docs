---
title: Smart Defaults — Documentation
---

# Smart Defaults

Smart Defaults for Jira Cloud fills fields of the **Create** dialog with values
you choose in advance. You define a rule for a project and an issue type — for
example *Priority = High* and a label for every Bug in one project — and the
dialog opens with those values already in place.

The app is built on [Atlassian Forge](https://developer.atlassian.com/platform/forge/)
and runs on Atlassian infrastructure. It declares no external permissions — see
the [Privacy Policy](privacy.md).

---

## Quick start

1. Open **Settings → Apps → Smart Defaults** (Jira administrators), or
   **Project settings → Apps → Smart Defaults** (project administrators).
2. Click **Add rule**.
3. Choose the project and the issue type. The list shows the supported fields
   that are on the create screen of that issue type.
4. Tick the fields you want to pre-fill and enter their values.
5. Click **Save**.
6. Open **Create** for that project and issue type. The fields are filled in.

Values can appear a few seconds after you pick the issue type. In our tests
(15 October 2026, one Jira site) this took about 5–10 seconds, mostly Jira
loading and applying the rule.

## Who can do what

| You are | You can |
| --- | --- |
| Jira administrator | Open **Settings → Apps → Smart Defaults**, see and edit the rules of every project, use **Resync** |
| Project administrator | Open **Project settings → Apps → Smart Defaults** and manage the rules of that project |
| Anyone who creates issues | Get the defaults in the Create dialog; nothing to configure |

The app checks these permissions on the server for every action on a rule.

## Documentation

| Page | What it covers |
| --- | --- |
| [Rules and fields](rules.md) | Supported fields, values, `{currentUser}` and `{today}`, description formatting, limits |
| [FAQ](faq.md) | Why a default was not applied, sub-tasks, uninstalling |
| [Privacy Policy](privacy.md) | What is stored, read and written |
| [Security Policy](security.md) | Architecture, permissions, vulnerability reporting |
| [Support](support.md) | How to reach us and what to include |
