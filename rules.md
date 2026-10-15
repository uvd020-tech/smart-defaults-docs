---
title: Rules and fields — Smart Defaults
---

# Rules and fields

[← Documentation home](index.md)

## What a rule is

A rule belongs to one **project** and one **issue type**. It holds a list of
fields with the value each one should get. There is at most one rule per
project and issue type pair; saving again replaces it.

The rule is applied when the **Create** dialog is open for that project and
issue type. Smart Defaults only fills the dialog: nothing is created until the
person clicks **Create**, and existing issues are never changed.

## Supported fields

The editor lists the fields that are on the create screen of the chosen issue
type and that the app supports:

| Field | Value you enter |
| --- | --- |
| Summary | Text, up to 255 characters |
| Description | Text, up to 32 767 characters — see [formatting](#description-formatting) |
| Priority | One of the priorities |
| Assignee, Reporter | A person, or the [current user](#current-user) |
| Labels | One or more labels: no spaces, up to 255 characters each |
| Components, Affects versions, Fix versions | One or more of the existing ones |
| Due date | A date, or a [relative date](#dates) |
| Custom fields of these types | Single select, radio buttons, multi select, checkboxes, cascading select, number, single-line text, multi-line text, date picker, date time picker, URL, single user picker, multiple user picker |

Not supported: Forge custom fields, any other field type, and any field that is
not on the create screen of the issue type. A date time value must include a
time zone; the editor adds your browser's offset.

## Replace a value that is already filled

By default a field is filled **only if it is empty**. Turn on **Replace a value
that is already filled** for a field to overwrite what is there. This is needed
for values that Jira sets itself — Priority always starts with a system default
— so the option is on by default for Priority and off for other fields.

A field counts as empty when it has no value, when Assignee is *Automatic*, or
when the description has no text.

## Current user

For people fields (Assignee, Reporter and the user pickers) you can choose
**Current user (who creates the issue)**. The value is stored as `{currentUser}`
and replaced with the person who opens the Create dialog. It works only as the
whole value of a people field, not inside text.

## Dates

For date fields choose a relative date: `{today}`, `{today+7}`, `{today-1}`.
The date is calculated in the browser when the dialog opens, in the person's
local time, and is entered as `YYYY-MM-DD`. The shift is a whole number of days
with up to four digits.

The same tokens work inside text values — Summary, Description and text
fields: `Weekly report {today}` becomes `Weekly report 2026-10-15`.

## Description formatting

In Description and multi-line text fields you can use simple markup, which is
converted to Jira's rich text when the field expects it:

| You type | You get |
| --- | --- |
| `# Heading`, `## Heading`, `### Heading` | Headings |
| `- item` or `* item` | Bulleted list |
| `1. item` | Numbered list |
| `**bold**` | Bold text |
| An empty line | Paragraph break |

## What can prevent a field from being filled

- The field is no longer on the create screen — it is skipped and the other
  fields are still filled.
- A select option, component or version in the rule has been deleted in Jira —
  that value is skipped and the others are still filled. Without this check
  Jira rejects the whole set of values.
- A person hid the field with **Show fields** in the dialog. According to
  Atlassian's documentation, hidden fields are not passed to UI modifications.
- The field already has a value and **Replace a value that is already filled**
  is off.

## Resync

On the **Settings → Apps → Smart Defaults** page, Jira administrators have a
**Resync** button. It deletes the UI modifications the app created in Jira and
creates them again from the saved rules. It repairs a mismatch, for example when
a UI modification was deleted by hand. The rules themselves are kept.

---

[← Documentation home](index.md) · [FAQ →](faq.md)
