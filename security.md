---
title: Security Policy — Smart Defaults
---

# Security Policy

**App:** Smart Defaults for Jira Cloud

**Last updated:** 15 October 2026

[← Documentation home](index.md)

This policy describes how Smart Defaults ("the app"), developed and maintained by Vudia, protects your data and manages security risk. It complements our [Privacy Policy](privacy.md).

## 1. Architecture and Hosting

The app is built on **Atlassian Forge** and runs on Atlassian's infrastructure. It has no servers of its own and stores no data outside Atlassian. Its manifest declares no external permissions, so the Forge platform does not allow it to make outbound requests to other hosts, and its code contains none.

Infrastructure-level controls — transport encryption, platform patching, physical security — are provided by Atlassian under its shared responsibility model; see the [Atlassian Trust Center](https://www.atlassian.com/trust). We do not operate any infrastructure of our own.

## 2. Data We Handle

Full detail is in the [Privacy Policy](privacy.md); in summary:

- We store the rules administrators create: project and issue type, the fields with their default values, and the account ID of the person who last changed a rule. They are kept in Forge storage and, as a UI modification, in your Jira site.
- We never store passwords, email addresses, payment details, or issue content.
- The app does not create or change issues. It fills the Create dialog in the person's browser; the issue is created only when the person clicks Create.

## 3. Authentication and Access Control

The app has no login or credential system of its own. Every request is authenticated by the Forge platform using the Jira session of the signed-in person — we never collect, transmit, or store Atlassian usernames, passwords, or API tokens.

Access to rules is checked on the server, for every request:

- listing the rules of all projects and **Resync** require the **Administer Jira** permission;
- listing, reading, saving and deleting the rules of one project require **Administer Jira** or **Administer projects** for that project;
- the lists of projects, issue types, create-screen fields and people are read with the signed-in person's own Jira permissions, so the app never shows a person anything they could not already see in Jira.

Jira allows UI modifications to be managed only by the app itself, so the app creates, updates and deletes them under its own identity, after the permission check above.

The app's requests to Jira are limited to: the person's own permissions, the project list and a project's name, the create-screen metadata of an issue type, people search and lookup, and the app's own UI modifications.

## 4. Declared Scopes

| Scope | Used for |
| --- | --- |
| `read:jira-work` | Permissions check, projects, create-screen metadata, reading the app's UI modifications |
| `read:jira-user` | Searching for people in the rule editor |
| `write:jira-work` | Filling values in the Create dialog |
| `manage:jira-configuration`, `manage:jira-project` | Required by Atlassian: the UI modifications module needs all scopes of its group to be declared |
| `read:app-data:jira`, `write:app-data:jira` | Recommended by Atlassian's documentation for the UI modifications REST API |
| `storage:app` | Forge storage for the rules |

No external or outbound permissions are declared.

## 5. Dependencies and Code

- The source code is kept in a private GitHub repository. **Dependabot** alerts and security updates are enabled on it.
- On 15 October 2026 `npm audit --omit=dev` reported no vulnerabilities in the runtime dependencies of the backend and of both front-end bundles. Build-time tools are not part of the delivered app.

## 6. Vulnerability Management and Incident Response

Vulnerabilities reported to us — whether by Atlassian, a researcher, or a customer — are triaged and fixed within the timeframes of Atlassian's Marketplace policy for cloud apps.

If we identify or are notified of a security incident affecting the app:

1. We investigate and confirm scope and impact.
2. We notify Atlassian within 24 hours via a P1 support ticket, as required of Marketplace partners.
3. We contain and remediate the issue.
4. We notify affected customers directly if their data was affected.
5. We review the incident afterward and adjust our practices if needed.

To report a suspected vulnerability or security incident, email **security@vudia.site**. For general support, use **info@vudia.site**; security reports are prioritized ahead of general support requests.

## 7. Business Continuity

The app has no infrastructure of its own, so its availability depends on Atlassian Forge. There is no customer data outside Forge storage and your Jira site, both operated by Atlassian.

## 8. Third-Party Risk

The only third party in our data flow is **Atlassian**, which hosts and operates Forge, Forge storage and Jira. We do not use any other subprocessor, analytics service, or external API.

## 9. Compliance

We do not hold independent security certifications at this time; as a Forge app we rely on the infrastructure controls of Atlassian's platform.

## 10. Policy Review

This policy is reviewed at least annually, and whenever we make a material change to the app's architecture, data handling, or team.

## Contact

- **Security reports / vulnerability disclosure:** security@vudia.site
- **General support:** info@vudia.site — see [Support](support.md)
- **Privacy questions:** see our [Privacy Policy](privacy.md)

---

[← Privacy Policy](privacy.md) · [Documentation home](index.md) · [Support →](support.md)
