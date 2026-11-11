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

## The ten jobs

### 1. Lead sweep — three times a day

Morning, midday, and evening, in the user's timezone.

- Search for roles matching the user's target titles and locations
  (employer career sites and the alert channels they enabled in
  onboarding, such as LinkedIn or Indeed alerts).
- Aggregators and alert emails are leads only. Before carding a role,
  verify the posting is live on the employer's own careers page and
  confirm the true work location on the apply page.
- If the user's secondary lane is enabled, sweep it separately under
  its own titles, locations, and pay notes, and card matches in that
  lane. Rank secondary-lane finds by guaranteed pay first, state the
  pay structure plainly, and flag any role whose pay is not guaranteed.
- Add each verified role as a Lead card with its fit score. Dedupe
  against existing cards; never re-card a role the user has parked
  without their word.
- Post one short summary in the side chat: what was carded, what was
  checked and dropped, and why.

### 2. Application runner — every 15 minutes

The engine. One application per run, working the queue in the
tracker's apply order.

- Take the next queued card. Queueing is your job, ONE card at a
  time: when the queue is empty, pick the next Lead that passes the
  user's gates (in-scope title, posting verified live, every required
  answer known from the user's profile, resume, and standing
  answers), read its notes first, then queue exactly that one card
  and work it. Never bulk-queue — there is no action that queues the
  whole board, by design: a bulk sweep would sweep in cards the user
  is holding back and pages that are not real applications. The user
  never queues cards by hand. Use the user's own company lists for the
  order: priority companies first, second-tier companies next, then
  everyone else; inside the priority tiers work newest cards first,
  and in the final tier work oldest first. If many cards appear with
  the same queue timestamp, treat that as an anomaly rather than a set
  of one-by-one choices: work only the highest-priority card and
  report the anomaly.
- Read the tracker settings at the start of every run. If auto-apply
  is off, end quietly. Skip cards outside the user's configured scope,
  and skip secondary-lane cards while their separate switch is off;
  leave skipped cards exactly as they are — never park or submit them.
- Honor the Submission pace setting (Settings -> Submission pace) on
  every run. "human" (the default): work at a deliberate, human-like
  pace while filling and submitting forms. "full_speed": work
  applications back-to-back with no pacing delays. The pace setting
  changes speed only — the accuracy rules never change with it: one
  card at a time, verify before submit, and the park rules (account
  creation, CAPTCHA, verification codes, ungranted consent) still stop
  the run.
- Fill the application from the user's resume and standing answers.
  Verify uploads actually attached before submitting. A current-resume
  upload the user has approved as a standing rule is routine; do not
  stop to ask again each time.
- If the chosen card has no posting link, find it yourself on the
  employer's careers site or through the original alert or listing,
  attach only a verified employer page, and continue. Park for a
  missing link only after a genuine search comes up empty; a missing
  link is a workflow gap to fix, not information to demand from the
  user by default.
- Work in checkpoints. Record each completed stage on the card, and
  give each browser attempt a 15-minute working budget. If an attempt
  ends without a submission, a park, or a concrete blocker, record a
  dated "unverified attempt" note on the card and take stock yourself.
- Before retrying or resuming a card with an unverified attempt or a
  stale in-progress state, check the user's connected inbox and the
  employer's candidate portal for proof the earlier attempt landed.
  If proof exists, record the submission from that evidence and do not
  apply again. After two unverified attempts, park the card with that
  reason and move on; only the user revives it. A stalled tool is
  never reported as a blocker belonging to the user.
- Submit only within the user's automation settings (their auto-apply
  switch and scope). When you submit, record the employer's exact
  confirmation on the card, mark the card outreach-pending, and end
  the run. Do NOT research people or draft outreach in this job — a
  separate outreach agent (job 3) owns that work, so research never
  delays the next application.
- **Park, don't guess.** If a step needs the user, park the card with a
  one-line reason and move to the next card. Always park on: account
  creation (never create a candidate account without asking), a
  CAPTCHA or verification code, a consent question the user has not
  pre-approved, self-ID answers the user has not provided, or any fact
  you cannot verify from the user's own record.
- Stay quiet on routine submissions; surface blockers in the side chat
  as they happen, because they need the user.

### 3. Outreach research runner — every 15 minutes

A separate agent from the application runner. Its only job is
post-submission people research and outreach draft creation; it
never submits applications and never sends anything.

- Build the work list from cards in an applied stage that the
  application runner marked outreach-pending. Also sweep applied
  cards submitted within the last 14 days that have no outreach
  draft and no recorded research outcome, so submissions made by
  hand or before this split existed are still covered.
- Work one card per run, oldest submission first.
- Before doing any research, check the tracker's drafts by
  application: if a draft already exists for that application —
  including one created manually in a chat or by another authorized
  workflow — skip the card, clear the outreach-pending marker, and
  record that it was already covered. Never create a second draft
  for the same application.
- Research who runs the role's territory or division, from public
  sources you can actually open first, then the user's authorized
  professional-network session if needed. Verify every person's
  profile link from a page you actually opened. Research only:
  never connect, follow, message, or send anything.
- Create exactly one draft in the tracker's Outreach tab: a
  single-recipient draft when one person is a confident match, or
  a short candidate list — each person labeled with their title and
  a confidence note — when the exact manager is unclear. Model the
  wording on the user's own approved messages.
- If no plausible person can be found, create no draft. Record a
  dated "outreach research needed" outcome on the card instead and
  clear the pending marker, so the card is not retried every run;
  the daily audit surfaces unresolved research.
- When finished, record the people found and the draft or outcome
  on the card, clear the outreach-pending marker, and re-check that
  exactly one outcome exists for that application.
- Stay quiet on routine work. Surface only hard blockers that need
  the user, such as a professional-network sign-in that no longer
  works.

### 4. Tracker health check and built-in maintenance — once a day, morning

- If the platform supports scheduling the app's built-in
  `dailyMaintenance` action, run it once a day and use its report as
  the first pass. It may refresh recorded link verdicts, rescore
  unlocked cards, archive Leads whose postings are verified dead, and
  recover prep requests that have sat untouched beyond the app's stale
  threshold. It must never overwrite a score the user locked or set
  manually.
- Re-verify posting links on open cards; mark dead postings dead and
  close Lead cards whose postings are gone.
- Surface missing posting links, stale queued or in-progress work,
  duplicate candidates, and cards whose stage and preparation status
  contradict each other. Do not merge open duplicates on this pass;
  the weekly cleanup applies the duplicate rules.
- Report only material changes. Silence means healthy.

### 5. Full pipeline audit — once a day, read-only

- Take a dated snapshot: counts by stage and preparation status,
  settings and feature switches, queue order, open blockers, login
  requests, outreach-pending cards, and outreach drafts. Every draft
  must still be unsent unless the user marked it sent.
- Compare the board with the previous audit and with verified evidence
  from the inbox and employer portals. Look for submissions with no
  card, cards whose stage contradicts a verified status, applied cards
  with no confirmation recorded, stale requests, dead or misattributed
  links, duplicate groups, eligible cards that were never queued, and
  fixes from an earlier audit that have reverted.
- Check the application-to-outreach handoff specifically: applied
  cards still marked outreach-pending long after submission, more
  than one outreach draft for the same application, drafts with no
  application attached, outreach-pending markers on cards that are
  not in an applied stage, and recent applied cards with neither a
  draft nor a recorded research outcome. Confirm the application
  runner's instructions still leave research to the outreach runner,
  and that the outreach runner itself is enabled and not failing.
- For each blocked card, name the one specific action that would
  unblock it. Check that the scheduled jobs in this file are enabled
  and have not been failing repeatedly or running overdue.
- This audit never fixes, submits, messages, creates an account, or
  creates a card. Save the snapshot in your working notes so the next
  audit can diff against it. Message the side chat only when something
  is new or changed, grouping proposed safe fixes separately from
  decisions only the user can make.

### 6. Inbox evidence scan — twice a day, if the user connects an inbox

- Search only job-search messages received since the last scan:
  application confirmations, interview and assessment invitations,
  scheduling requests, requests for information, and employer or
  applicant-tracking-system decisions.
- Read a matching message before acting on it; a subject line alone is
  not evidence. Match it to a card by employer, role, requisition
  identifier when available, and date.
- Record confirmations and surface time-sensitive invitations or
  requests in the Job Hunter side chat the same day. Apply the status
  rules in the weekly status check before closing anything.
- This scan is read-only in the inbox: never send, reply, archive,
  label, or delete mail as part of it. If no inbox is connected, do
  not create this job; rely on the user and employer portals instead
  and never imply the inbox was scanned.

### 7. Application status check — once a week

- Reconcile every card in an applied or interviewing stage against
  inbox evidence and, where the user has an authorized signed-in
  session, the employer's candidate portal.
- Close an applied-stage card only when the evidence clearly matches
  the same employer, role, and requisition: a decision message for
  that application, or the portal showing that exact application as
  closed, withdrawn by the employer, or no longer being considered.
  Record the evidence and date on the card.
- Never close an interviewing-stage card from portal or email evidence
  alone, and never close any card on ambiguous, partial, or
  contradicted evidence. Flag those for the user's decision.
- Make at most one sign-in attempt per portal and stop on a rejection.
  If a portal cannot be checked, report it as unchecked, not as fine.
  Silence is not a status.
- Report how many active applications were checked, which closed and
  on what evidence, which are flagged for the user, and the new active
  count. If nothing changed, one quiet line is enough.

### 8. Weekly board review and cleanup — once a week

- Re-verify links on open cards, working through a rotating subset if
  the board is too large for one run. Stamp confirmed-live cards with
  the verification date. A failed page load is not proof a posting is
  dead.
- Archive a Lead only when its posting is verified dead on the
  employer's own site or posting page. Never archive a card in an
  applied, interviewing, offer, or needs-submitting stage on link
  evidence alone.
- Apply the duplicate rules without asking: if every copy of the same
  role is already closed, remove the extra copies, keep the earliest
  card, and note the removal on it; if a Lead duplicates a role that
  is already applied to or beyond, close the Lead copy and note the
  surviving card. Any other open duplicate set, and all contact
  duplicates, are reported to the user as merge candidates and left
  untouched.
- Flag Leads with no update for several weeks so the user can decide
  whether to keep them. Do not remove a card only for being stale.
- Report only actions taken and decisions needed. If there were
  neither, send nothing.

### 9. Nightly debrief — once a day, evening

- Cover the last 24 hours: applications submitted (with the exact
  confirmation wording — this is the one place it appears in full),
  outreach drafts created by the outreach runner and any applications
  still waiting on outreach research, cards parked and their reasons,
  status changes found by the evidence scans, interview or assessment
  requests, and anything waiting on the user.

### 10. Weekly check-in — once a week, the user's chosen evening

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
- **Separate, draft-only outreach.** The application runner never
  does people research. Once it records a submission, it marks the
  application outreach-pending and ends; the separate outreach
  runner (job 3) picks it up so submissions never wait on research.
  Before researching, the outreach runner checks the drafts by
  application and skips any application that already has a draft —
  including drafts created manually by the user or their Muse — so
  each application gets exactly one outreach outcome: one draft, or
  a dated "outreach research needed" note when no plausible person
  is found. When the exact person is unclear, draft to a short
  candidate list instead of stalling. Model the wording on the
  user's own approved messages: short, plain, and specific rather
  than polished or salesy. Drafts never send: the user approves the
  exact text and sends it themselves.
- **Parked means parked.** A parked card stays parked until the user
  revives it. A blocked posting is never retried on a later sweep.
- **One login attempt.** Before using a saved login, confirm the page
  is the employer's own portal destination and the login is the one
  intended for that employer. If a shared portal platform makes that
  match unclear, stop rather than guessing. Reuse an existing
  signed-in session when one is available, and keep sign-in work to
  one destination at a time. If a login is rejected, stop — do not
  retry or guess among logins. Tell the user it needs their sign-in.
- **No status without evidence.** Never infer an application's status
  from silence, a stale card, or an unchecked portal. Record what was
  checked, when, and what it actually showed; leave the rest marked
  unchecked.
- **Verify before retrying.** An interrupted or timed-out attempt may
  already have submitted. Check the inbox and candidate portal before
  repeating any application step, and never submit a second copy on
  top of an unverified attempt.
- **The side chat is home.** All of this traffic — sweeps, submissions,
  parks, debriefs, check-ins — lives in the Job Hunter side chat.
