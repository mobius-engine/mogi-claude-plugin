---
name: mogi-resume-rebuild
description: Guide the user through Mogi's required resume rebuild: ten questions about their own work, a rebuilt resume to review, then approval (or, for existing clients, keeping their current resume). Use when get_account shows resume_rebuild required, applications are held, or the user asks to improve their base resume.
metadata:
  short-description: Rebuild the resume Mogi applies with
---

# Resume rebuild

Mogi does not apply for an account until its base resume has been rebuilt and the user has
approved it. Existing clients may keep their current resume instead. `get_account` shows it as
`resume_rebuild` (`applications_held` says whether Mogi is waiting on this).

## Workflow

1. `get_resume_rebuild`. Follow `next`. Status `not_started`: `start_resume_rebuild`. Existing
   clients (`may_keep_current_resume`) get both choices; say what each means before they pick.
2. **Questions** (`questions_ready`). Ask the ten questions one or two at a time, with the
   example Mogi gives. The answers must be the user's own, with their real numbers. Never write
   an answer for them or pad one. "Doesn't apply to me" is fine (`not_applicable`). Save with
   `answer_rebuild_questions`; when all are done, call it with `submit` true. Writing takes a
   minute or two: check `get_resume_rebuild`.
3. **Review** (`draft_ready`). Show the draft and `what_got_stronger`. For a change, use
   `revise_rebuild_draft` (`change` with one instruction; limited per rebuild, see
   `changes_left`) or `back_to_questions`.
4. **Approve.** Only after the user has read the draft and says yes: `approve_rebuilt_resume`
   with `user_approved` true. Approving becomes their default resume and held applications start
   again.
5. **Keep instead** (existing clients only). `get_resume_rebuild` with `show_keep_option`. Show
   the ATS score and the disclaimer word for word, and ask for an explicit yes. Then
   `keep_current_resume` with `user_agreed` true and the `version` that came with it.

## Guardrails

- Approving and keeping are the user's consent. Never set `user_approved` or `user_agreed` for
  them.
- Facts (employers, titles, dates, education) are locked to their resume; do not offer to change
  them here.
