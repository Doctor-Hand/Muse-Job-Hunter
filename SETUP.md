# Setup — for the Muse installing this tracker

This file is written for the user's Muse. If your user gave you this
repo and asked you to set the tracker up for them, follow these steps.

## 1. Build the app

Create a fullstack web artifact from this source in the user's Library
and apply `drizzle/0001_create_tracker_tables.sql` to a fresh database.
The tracker starts empty — no jobs, no contacts. Do not load
`examples/seed-example.sql` unless the user asks for demo rows.

## 2. Give the tracker its own side chat

Create a dedicated side chat for the tracker and name it **Job Hunter**.
This chat is the tracker's home. Tell the user you've created it — the
point is that the tracker never clutters their main chat. If a tracker
chat already exists for this user, use it instead of making a second
one. If your client needs the user's OK before creating a chat, ask
once, as part of the install.

## 3. Run onboarding in that side chat

Do the onboarding *in the side chat*, not in the main chat. Walk the
user through the questionnaire (the same questions live in the app's
Onboarding tab — see [ONBOARDING.md](ONBOARDING.md)): either guide them
through the tab while you answer questions in the chat, or collect the
answers conversationally in the chat and save them for them. Finish
with a short summary of how their tracker is configured: target titles,
locations, pay floors, feature switches, and automation permissions.
When onboarding is saved as complete, the app's Onboarding tab retires
on its own — the answers stay editable under Settings → Onboarding
profile, so the dashboard the user lives in day-to-day has no leftover
setup tab.

## 4. Keep every update in the side chat from then on

All tracker traffic belongs in the side chat: new leads, application
outcomes, blocked applications and their reasons, health checks,
scheduled sweeps or debriefs the user sets up, and the weekly check-in.
The main chat stays clean; answer there only if the user asks there,
and still record the outcome in the tracker.

## Standing rules that come with this template

- **Draft-only outreach.** The tracker never sends a message for the
  user. Drafts need the user's exact-text approval; the user sends.
- **Blocked means parked, never guessed.** If an application can't be
  completed with facts the user has provided, park it with the reason
  in the side chat and move on.
- **The user's data stays in their Muse.** Nothing from their tracker
  is shared back to this repo or anywhere else.
