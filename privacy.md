---
title: Privacy Policy — Smart Defaults
---

# Privacy Policy

**App:** Smart Defaults for Jira Cloud

**Last updated:** 15 October 2026

[← Documentation home](index.md)

## Summary

Smart Defaults is an [Atlassian Forge](https://developer.atlassian.com/platform/forge/)
app. It runs on Atlassian's infrastructure. It has no servers of its own, makes
no requests to other hosts, and sends no data to any third party. What the app
stores stays inside the Forge platform and your Jira site.

The app declares no external permissions in its manifest (no egress), which
makes this verifiable rather than a promise.

## What the app stores

When an administrator saves a rule, the app stores it in Forge storage:

| Data | Why |
| --- | --- |
| Project ID and name, issue type ID and name | To show which rule belongs where |
| For each field in the rule: field ID, field name, type, the default value, and the “replace a value that is already filled” setting | To fill the Create dialog |
| For people fields: the Atlassian account ID (names are looked up in Jira when the editor shows them, not stored) | To fill Assignee, Reporter and user pickers |
| The ID of the Jira UI modification that carries the rule | To update or delete it |
| The time of the last change and the account ID of the person who made it | To show when the rule was updated and to keep a record of who changed it |

Default values are whatever the administrator typed, so they may contain any
text the administrator chose to enter.

The same values are also stored **in your Jira site** as a UI modification
created by the app (its name is `smart-defaults`; it carries the field values and
the project and issue type it applies to). Jira stores it as part of your site.

The app does **not** store passwords, email addresses, payment details, or the
contents of issues.

## What the app reads from Jira

Using the permissions of the person who is using the app:

- the projects visible to the person, the issue types of a project, and the
  fields of the create screen of an issue type (including their allowed
  values);
- the person's own permissions (whether they administer Jira or the project);
- the results of people searches, and the display name of a person for an
  account ID, when you pick people in the editor;
- the project name when a rule is saved.

As the app itself, it reads the list of UI modifications that the app has
created (Jira returns only those).

In the Create dialog the app also reads the create screen's allowed values
(options, components, versions), so that it never inserts a value that has been
deleted.

## What the app writes to Jira

- UI modifications, created, updated and deleted by the app when rules are
  saved, deleted or resynced.
- Field values **inside the Create dialog in the person's browser**. These are
  not saved anywhere until the person clicks Create, and the person can change
  them first.

The app does not create or change issues.

## Logs

- **Forge logs** (operated by Atlassian): when an action fails, the app writes
  its name and the error text; for failed Jira requests this includes the HTTP
  method, the status and the first 300 characters of Jira's response. After
  installation the app logs how many UI modifications it removed and created.
  The app itself does not write rule values or people's names to the logs; the
  error text of Jira is logged as Jira returned it.
- **The person's browser console**: in the Create dialog the app writes one
  line with the result for each field (set, kept, skipped), the ID of the field
  and timings. It stays in the browser and is not sent anywhere.

## Analytics and tracking

The app contains no analytics, no tracking pixels, no advertising and no
third-party scripts. It does not profile users and makes no automated decisions
about them.

## Data retention and deletion

- Deleting a rule removes it from Forge storage and deletes its UI modification
  in Jira.
- Uninstalling the app removes its stored data according to Atlassian's Forge
  storage lifecycle. On a development installation on 15 October 2026 no rules
  were left after uninstalling and installing again.
- To request deletion of data associated with your site, contact us at
  [info@vudia.site](mailto:info@vudia.site).

## Where data is stored

In Forge's storage, operated by Atlassian, and in your Jira site. Hosting
location and residency follow the Atlassian Cloud infrastructure your site runs
on. See the [Atlassian Trust Center](https://www.atlassian.com/trust) for
details.

## Your rights

Since the app processes data on behalf of your organisation, requests for
access, correction or deletion of personal data are best raised with your own
Jira administrator, who controls the site. We will assist administrators with
any such request — contact [info@vudia.site](mailto:info@vudia.site).

## Changes to this policy

Material changes will be published on this page with an updated date above.

## Contact

Vudia — [info@vudia.site](mailto:info@vudia.site)

---

[← FAQ](faq.md) · [Documentation home](index.md) · [Security →](security.md)
