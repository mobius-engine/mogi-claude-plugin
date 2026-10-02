---
name: mogi-setup
description: Walk a Mogi user through setup in chat once their account is active: upload a resume, create a job search, add the first jobs, fill the required application answers, then accept the Terms and go live. Use whenever setup is not complete.
metadata:
  short-description: Set up your search and go live
---

# Finish setup

## Workflow

1. Call `get_onboarding_status`. If `plan_active` is false, explain that setup continues once
   the account is active in the Mogi app (`app_url`), and stop. Otherwise follow `next_steps` in order and say how many are left.
2. **Resume.** Ask the user to attach their resume (PDF or Word), then call `upload_resume`.
   Formatting takes a minute or two; check with `list_resumes`. When the status is `ready`,
   share `document_link`, and call `approve_resume` only after the user says it looks right.
3. **Search.** Ask which roles and where (remote, hybrid or on-site; cities or states) and any
   pay floor. Call `preview_new_jobs` once to show a sample. Adjust with the user, then call
   `add_jobs_from_search` with the filters and the ids they liked.
4. **Answers.** For each item in `missing_answers`, ask the user and save with
   `update_profile`. `referral_source` is how they heard about Mogi. Never guess an answer
   (work authorization, sponsorship, phone).
5. **Go live.** Show the user `terms_text` and every acknowledgment from
   `get_onboarding_status`, word for word (plus the AI disclosures if they want tailored resumes
   or cover letters), and ask:
   - whether they approve each job themselves (`job_auto_approve` off) or let Mogi approve
     strong matches (`high_fit`) or every match (`all`);
   - whether they want a tailored resume (default yes) and a cover letter (default no) for
     each job.
   Then ask them to type their initials. Call `complete_onboarding` with
   `user_agreed_to_terms` true only after they explicitly agree.
6. Confirm Mogi is live and offer to review the first jobs (mogi-review-jobs).

## Guardrails

- Going live signs the Terms. Never set `user_agreed_to_terms` without the user's explicit yes
  in this conversation, and never type their initials for them.
- One question at a time; keep each message short.
- Use only facts the user gave.
