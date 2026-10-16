# Mogi

Mogi finds jobs that match what you want and applies to them in your name, automatically.
This plugin connects Claude to your own Mogi account, so you can run your job search in
conversation.

## What it adds to Claude

- **The Mogi connector**, a remote MCP server at `https://jobagent-api.mobiusengine.ai/mcp`.
  It acts only on the signed-in user's own Mogi account.
- **Eight skills** that teach Claude the common workflows:
  - Get started: an overview of the account and what is waiting.
  - Setup: finish setting up Mogi in chat, from resume upload to going live.
  - Review jobs: see the jobs Mogi found and approve or pass on them.
  - Job searches: create, change, widen or remove saved searches.
  - Resumes: upload, edit with AI, go back a version and choose the default resume.
  - Resume rebuild: answer ten questions about your work, then review and approve the rebuilt resume.
  - Settings: auto-approve, resume customization (Heavy, Light or My own), the cover letter, application answers, email preferences, pause or resume.
  - Progress: applications submitted, interviews, questions on a job, support messages and job emails.

## Use it

1. Install the plugin, then open its **Connectors** tab and connect Mogi.
2. Sign in with the Google account you use for Mogi and click **Allow**. You choose which
   permissions to give.
3. Ask, for example: "Show me the new jobs waiting for my approval", "Make my search remote
   only and skip Director roles" or "How many applications went out this week?"

## Data

The plugin talks only to `jobagent-api.mobiusengine.ai`, and only about the signed-in user's
own account. Changes (approving jobs, editing searches, settings) need the "Make changes"
permission, and job emails need "Read job emails"; both can be turned off when connecting.
Reading email never sends, replies to or changes mail, and one-time codes and sign-in links are
removed. The plugin cannot delete the account or send email. Disconnect any time from
**Use in ChatGPT** in the Mogi app's left menu. The plugin runs no local code.

Privacy policy: https://mobiusengine.ai/privacy · Terms: https://jobagent.mobiusengine.ai/terms ·
Support: https://jobagent.mobiusengine.ai/support
