---
title: FAQ — Smart Defaults
---

# FAQ

[← Documentation home](index.md)

## A default was not applied. Why?

Check, in this order:

1. There is a rule for **this exact project and issue type**
   (Settings → Apps → Smart Defaults lists them all).
2. The field is on the create screen of that issue type and is not hidden
   with **Show fields**.
3. The field was empty. A field that already has a value is kept unless
   **Replace a value that is already filled** is on for it.
4. The value still exists in Jira. A deleted option, component or version is
   skipped.
5. A few seconds have passed since you picked the issue type — the values can
   appear with a delay.

The details are on [Rules and fields](rules.md#what-can-prevent-a-field-from-being-filled).

## Does it work in team-managed and company-managed projects?

Yes. We tested both kinds on one Jira site on 15 October 2026: the values were
filled in a team-managed project and in a company-managed project.

## Does it change existing issues?

No. Smart Defaults only fills the Create dialog. The issue is created when the
person clicks **Create**, with whatever values the dialog holds at that moment —
the person can change or clear any of them first.

## What about sub-tasks?

You can create a rule for a sub-task type; the editor marks these types with
“(sub-task)”. In the editor we say: sub-tasks get defaults only when Jira opens
the Create dialog for them — from **Create subtask**, when Summary and at least
one other field are required for that issue type. Sub-task types are not offered
in the issue type list of the regular Create dialog (checked on one site on
15 October 2026). We have not tested the **Create subtask** scenario yet.

## Other apps also change the Create dialog. What happens?

According to Atlassian's documentation, up to five apps can apply UI
modifications to the same dialog at the same time; if two of them change the
same field, the one that finishes last wins.

## What happens if I uninstall the app?

The rules saved by the app are removed with its data. We checked this on a
development installation on 15 October 2026: after uninstalling and installing
again there were no rules. Note down the values of the rules you need before
uninstalling.

## What if the license is inactive?

The app shows a banner on its pages. **Add rule** and **Edit** are disabled, so
rules can only be deleted until the license is renewed.

## “Rule is too large” when saving

Jira limits the data stored for one rule to 50 000 characters. Shorten long
Description or text values, or remove fields from the rule.

---

[← Rules and fields](rules.md) · [Documentation home](index.md) · [Privacy Policy →](privacy.md)
