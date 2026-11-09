# Operations — the rhythm that runs the tracker

This file is written for the user's Muse. SETUP.md builds the tracker
and runs onboarding; this file sets up the recurring work that makes it
feel alive afterwards. Create these scheduled jobs during install
(after onboarding, so every job reads the user's own settings), tell
the user what you set up, and deliver every summary to the **Job
Hunter** side chat — never the main chat.

Everything below runs off the user's onboarding profile and tracker
settings: target titles, locations, pay floors, feature switches, and
automation permissions. Nothing is hardcoded to one person's search.

## The five jobs

### 1. Lead sweep — three times a day

Morning, midday, and evening, in the user's timezone.

- Search for roles matching the user's target titles and locations
  (employer career sites and the alert channels they enabled in
  onboarding, such as LinkedIn or Indeed alerts).
- Aggregators and alert emails are leads only. Before carding a role,
  verify the posting is live on the employer's own careers page and
  confirm the true work location on the apply page.
- Add each verified role as a Lead card with its fit score. Dedupe
  against existing cards; never re-card a role the user has parked
  without their word.
- Post one short summary in the side chat: what was carded, what was
  checked and dropped, and why.

### 2. Application runner — every 15 minutes

The engine. One application per run, working the queue in order.

- Take the next queued card. Queueing is your job, ONE card at a
  time: when the queue is empty, pick the next Lead that passes the
  user's gates (in-scope title, posting verified live, every required
  answer known from the user's profile, resume, and standing
  answers), read its notes first, then queue exactly that one card
  and work it. Never bulk-queue — there is no action that queues the
  whole board, by design: a bulk sweep would sweep in cards the user
  is holding back and pages that are not real applications. The user
  never queues cards by hand.
- Fill the application from the user's resume and standing answers.
  Verify uploads actually attached before submitting.
- Submit only within the user's automation settings (their auto-apply
  switch and scope). When you submit, record the employer's exact
  confirmation on the card.
- **Park, don't guess.** If a step needs the user, park the card with a
  one-line reason and move to the next card. Always park on: account
  creation (never create a candidate account without asking), a
  CAPTCHA or verification code, a consent question the user has not
  pre-approved, self-ID answers the user has not provided, or any fact
  you cannot verify from the user's own record.
- Stay quiet on routine submissions; surface blockers in the side chat
  as they happen, because they need the user.

### 3. Tracker health check — once a day, morning

- Re-verify posting links on open cards; mark dead postings dead and
  close cards whose postings are gone.
- Clean up duplicates: if every copy of a role is closed, remove the
  extra copies; if a Lead duplicates a role already applied to or
  beyond, close the Lead copy.
- Report only what changed. Silence means healthy.

### 4. Nightly debrief — once a day, evening

- Cover the last 24 hours: applications submitted (with the exact
  confirmation wording — this is the one place it appears in full),
  cards parked and their reasons, and anything waiting on the user.

### 5. Weekly check-in — once a week, the user's chosen evening

- One short, non-nagging message: where the pipeline stands, and one
  suggested outreach move for the week — a specific person from their
  Key Contacts and why now.

## Standing rules

- **Standing answers are the memory.** Every answer the user gives —
  during onboarding, or when you park and ask — becomes a standing
  answer saved to their profile. Never ask the same question twice.
  Trivial preference questions that attest no fact get the sensible
  default, not a park.
- **Facts on record are standing facts.** Check the user's resume,
  profile, and their own earlier applications before treating a field
  as unknown. Park only on facts genuinely absent or plausibly
  changed.
- **Consent is the user's call.** Attestation boxes covered by the
  user's recorded consent get checked; any new consent question parks
  until the user rules on it. Their ruling becomes the standing rule
  for that question.
- **Draft-only outreach.** For each role the user applies to, research
  the hiring manager or key people and draft the outreach in the
  tracker's Outreach tab. When the exact person is unclear, draft to a
  short candidate list instead of stalling. Drafts never send: the
  user approves the exact text and sends it themselves.
- **Parked means parked.** A parked card stays parked until the user
  revives it. A blocked posting is never retried on a later sweep.
- **One login attempt.** If a saved portal login is rejected, stop —
  do not retry or guess among logins. Tell the user it needs their
  sign-in.
- **The side chat is home.** All of this traffic — sweeps, submissions,
  parks, debriefs, check-ins — lives in the Job Hunter side chat.
