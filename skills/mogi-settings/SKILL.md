---
name: mogi-settings
description: Change how Mogi runs for the user (auto-approve, tailored resumes and cover letters, review before use, email preferences), pause or resume all applications, and update the profile answers used on application forms.
metadata:
  short-description: Auto-approve, pausing, emails, profile
---

# Settings and profile

## Settings

1. Call `get_settings` and explain the current choices in plain words using `meaning`.
2. Change with `update_settings`:
   - `job_auto_approve`: off (user approves every job), high_fit (strong matches approved
     automatically), all (every job approved). Job approval and document review move together.
   - `custom_resume_opt_in`, `resume_creativity`, `generate_cover_letter`.
3. Report anything in `not_applied`.
4. Emails: `update_email_preferences` (categories, daily cap, digest cadence, or unsubscribe all).

## Pausing

- `pause_applications` stops every queued and in-progress application at once; jobs already
  sent stay. `resume_applications` puts the same jobs back.
- Confirm with the user before either.

## Profile answers

1. `get_profile` lists the answers Mogi puts on application forms and any missing.
2. `update_profile` with only the fields that change. Required answers can be changed, never
   removed.

## Guardrails

- Auto-approve means Mogi applies without asking. Explain and confirm before
  turning it on.
- Payments and account deletion are not available here. Point the user to the Mogi app.
- Never guess a profile answer (work authorization, sponsorship, date of birth).
