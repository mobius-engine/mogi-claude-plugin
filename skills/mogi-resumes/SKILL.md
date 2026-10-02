---
name: mogi-resumes
description: Manage the user's Mogi resumes (upload, approve, set default, AI edits, standing tailoring notes) and the tailored resume and cover letter written for each job. Use for anything about resumes or cover letters.
metadata:
  short-description: Upload, approve and edit resumes
---

# Resumes

## Master resumes

1. `list_resumes` shows each resume: status (`processing` while Mogi formats it, `ready` when it
   waits for approval), approved, default, and a `document_link`.
2. **Upload:** ask the user to attach a PDF or Word file and call `upload_resume`. Formatting
   takes a minute or two. Then share `document_link` and call `approve_resume` once they say it
   looks right. An approved resume can be made default with `update_resume` (`make_default`).
3. **Read:** `get_resume` returns the text so you can review it with the user.
4. **Edit:** `edit_resume_with_ai` with plain-words `changes`. Check `get_resume_edit` after a
   minute or two, share the draft link, then `finish_resume_edit` with `save` or `discard`.
5. **Standing notes:** `update_resume` with `tailoring_instructions` (for example "never drop my
   certifications") guides every tailored resume.

## Per-job documents

1. Jobs waiting for document review are in `list_jobs` stage `resume_review`.
2. `get_job_documents` gives the status and links for that job's tailored resume and cover
   letter.
3. `approve_job_document` once the user approves; `request_job_document_changes` with their
   notes otherwise.

## Guardrails

- Approve only after the user has seen the document and said yes.
- Confirm before `delete_resume`. The last resume cannot be deleted.
- Do not rewrite facts: dates, employers, degrees and titles come from the user.
